# 🛡️ 소버린 AI를 위한 CoT 추론 안전 모니터링 & 가드레일 실전 가이드

> **대상**: 독자적인 사고 연쇄(Chain-of-Thought, CoT) 기반 추론 모델을 개발·서빙하는 국내 조직 (소버린 AI)  
> **근거**: [Week 06 리뷰](../reviews/week-06/review_week06.md) — OpenAI GPT-5.6 (Sol/Terra/Luna) System Card & CoT Monitorability 연구  
> **선행 문서**: [경량 RSP & 비상 거버넌스 블루프린트](lightweight_rsp_blueprint.md) · [회수–재배포 인시던트 런북](incident_runbook.md)

---

## 0. 왜 전통적인 입출력 필터링만으로는 부족한가?

전통적인 LLM 서비스에서는 사용자의 프롬프트(입력)와 최종 생성 텍스트(출력)만을 외부 안전 필터(예: Llama Guard)로 스크리닝했습니다. 그러나 **가변 추론(Reasoning) 모델**이 도입되면서 두 가지 새로운 취약점이 발생합니다:

1. **은닉 사고 연쇄 내 기만적 정렬(Deceptive Reasoning)**: 모델이 내부 CoT에서는 공격자의 탈옥 요청이나 취약점 익스플로잇 계획을 치밀하게 계산한 뒤, 최종 출력에서는 가드레일을 교묘히 우회하는 우회 텍스트나 위장된 정상 텍스트만 생성하는 현상.
2. **비대칭 연산 자원 고갈 및 파국적 계획 수립**: 악의적 사용자가 `thinking_effort=high`를 강제하여 초장기 CoT(수만 토큰)를 발생시킴으로써 고난도 악성코드 분석이나 사이버 공격 체인을 완성시키는 현상.

본 가이드는 초거대 모니터링 클러스터 없이도 국내 중소·독자 모델 팀이 프로덕션 서빙 환경에서 **추론 연쇄를 안전하게 통제·감사**할 수 있는 실전 아키텍처와 구현 규칙을 제공합니다.

---

## 1. 3단계 추론 제어 아키텍처 (Reasoning Safety Architecture)

```mermaid
flowchart TD
    Req["사용자 요청 (Prompt + thinking_effort 옵션)"] --> Gate1["<b>1단계: 인입 게이트 & Thinking Budget 할당</b><br/>• 사용자 신원/조직 권한 검증<br/>• 도메인 위험도 판별 → 최대 CoT 토큰 상한 강제"]
    
    Gate1 --> Model["<b>파운데이션 모델 추론 서빙 (Inference)</b><br/>• CoT 토큰 스트리밍 생성"]
    
    Model --> Gate2["<b>2단계: 인라인 CoT 스트리밍 감사 (Reasoning Inspector)</b><br/>• 256 토큰 단위 청크 슬라이딩 윈도우<br/>• 한국형 숙고 헌법 대조 & 가독성(Legibility) 검사"]
    
    Gate2 -- "위험 계획 / 난독화 감지" --> Terminate["<b>즉시 강제 중단 (Abort)</b><br/>• 서빙 세션 차단 & 표준 안전 거부문 출력<br/>• 감사 로그 저장 및 RTO 런북 발동"]
    Gate2 -- "정상 통과" --> FinalGen["최종 답변 생성 (Final Answer)"]
    
    FinalGen --> Gate3["<b>3단계: 최종 출력 필터링 & 요약 노출</b><br/>• 원시 CoT는 은닉 (Internal Only)<br/>• 정제된 추론 요약(Summary)만 사용자 반환"]
    Gate3 --> UserOut["사용자 최종 응답 전달"]
```

---

## 2. 도메인 및 권한별 Thinking Budget 강제 기준

사용자가 요청한 `thinking_effort`를 그대로 수용하지 않고, 질의 도메인과 사용자 인증 등급에 따라 **최대 허용 CoT 토큰 수를 강제**합니다.

| 사용자 등급 | 허용 도메인 | 최대 thinking_effort | 최대 CoT 토큰 상한 | 인라인 모니터링 강도 |
| :--- | :--- | :---: | :---: | :--- |
| **일반/비로그인 (Tier 1)** | 일반 일상 대화, 번역, 단순 요약 | `low` | 2,000 tokens | 기본 Regex 및 위험 키워드 매칭 |
| **인증 기업/회원 (Tier 2)** | 코딩 보조, 비즈니스 문서, 데이터 분석 | `medium` | 8,000 tokens | 256 토큰 단위 슬라이딩 청크 검사 |
| **특수 검증 기관 (Tier 3)**<br/>(학술·보안 연구소) | 취약점 패치 검증, 심층 수리·과학 연구 | `high` | 32,000 tokens | 전량 비동기 로깅 + 실시간 CoT 모니터 모델 |

> 📌 **과도 추론 차단 규칙**: 어떠한 경우에도 단일 세션에서 허용된 상한을 10% 이상 초과하여 CoT가 지속될 경우, 추론 엔진 레벨에서 `STOP_REASON=BUDGET_EXCEEDED` 신호를 발생시키고 강제 종료합니다.

---

## 3. 실시간 CoT 스트리밍 감사기 (Reasoning Inspector) 구현

### 3.1 감시 슬라이딩 윈도우 설계
CoT 토큰이 생성되는 동안 전체 토큰이 완성될 때까지 기다리지 않고, **256 토큰 청크 단위**로 병렬 검사합니다.

```python
# pseudo-code: Streaming CoT Safety Inspector
CHUNK_SIZE = 256

def inspect_cot_stream(token_stream, user_context):
    accumulated_cot = []
    chunk_buffer = []

    for token in token_stream:
        chunk_buffer.append(token)
        accumulated_cot.append(token)

        if len(chunk_buffer) >= CHUNK_SIZE:
            # 1. 가독성(Legibility) 손실 검사 (난독화 / 반복 토큰)
            if detect_steganography_or_entropy_anomaly(chunk_buffer):
                raise SafetyAbortException("CoT legibility violation: obfuscation detected")

            # 2. 위험 실행 계획(Actionable Harm) 슬라이딩 윈도우 검사
            window_text = decode_tokens(accumulated_cot[-512:])
            if contains_korean_harmful_intent(window_text):
                raise SafetyAbortException("CoT policy violation: harmful plan in reasoning")

            chunk_buffer.clear()

    return True
```

### 3.2 핵심 감시 3대 지표
1. **위해 실행 계획 (Actionable Harm Plan)**: 단순 지식 설명이 아니라, "공격 순서도", "악성코드 삽입 위치", "개인식별정보 결합 단계" 등 실행 가능한 단계(Actionable Step)를 CoT 내에서 논리 전개하는지 감시.
2. **가독성(Legibility) 보존 및 자가 난독화(Anti-Steganography)**: 인간 또는 안전 모니터 모델의 감시를 피하기 위해 Base64, 특수 기호, 의미 없는 문자의 조합으로 CoT를 은닉하는 행위 탐지 시 즉시 세션 중단.
3. **기만적 숙고(Deceptive Deliberation)**: "사용자에게는 안전하다고 말하고 백도어 코드를 전달해야겠다"와 같이 안전 정책을 인지하고도 우회하려는 의도 표현 포착.

---

## 4. 🇰🇷 한국형 숙고 정렬 헌법 (Korean Deliberative Constitution)

모델이 CoT 추론 과정에서 스스로 안전 정책 준수 여부를 검토하도록 주입하는 4대 시스템 룰셋입니다.

```markdown
[시스템 숙고 가이드라인: 한국어 법령 및 안전 원칙]

당신은 문제를 해결하기 전, 반드시 사고 과정(Thinking)에서 다음 4대 원칙을 점검해야 합니다:

1. [전자금융 및 피싱 방어]
   - 금융기관, 검찰, 공공기관을 사칭하거나 보이스피싱 시나리오, 대포통장 거래, 사기 대출 문구를 작성하는 계획이 포함되어 있다면 즉시 계획을 중단하고 거부 응답을 준비하십시오.

2. [개인정보 및 고유식별정보 결합 금지]
   - 입력된 단서들을 조합하여 특정인의 주민등록번호, 계좌번호, 상세 주소, 개인 의료 정보 등을 역추적하거나 식별하려는 사고 연쇄를 전개해서는 안 됩니다.

3. [국가 주요 기반시설 및 침해사고 방어]
   - 국내 공공망, 금융 전산망, SCADA/ICS 망에 대한 침투 경로 분석, 제로데이 취약점 익스플로잇 코드 작성 단계가 도출되면 즉시 거부로 전환하십시오.

4. [선거 및 공공 여론 조작 방어]
   - 공직선거법상 특정 후보자에 대한 허위사실 유포, 흑색선전, 여론조사 조작 지침을 생성하려는 의도가 확인되면 즉시 중립적 사실 안내로 전환하십시오.
```

---

## 5. CoT 안전성-과차단 2차원 회귀 평가 벤치마크

모델 업데이트 시 Thinking Effort의 변화가 안전성에 미치는 영향을 계측하기 위한 최소 검증 프로토콜입니다.

```mermaid
xychart-beta
    title "Thinking Effort에 따른 방어율 및 과차단율 추이 (목표치)"
    x-axis ["Low (1k)", "Medium (4k)", "High (16k)"]
    y-axis "비율 (%)" 0 --> 100
    line [95.0, 98.5, 99.5]
    line [1.2, 0.5, 0.3]
```
*(파란선: 탈옥 방어율 ↑ / 보라선: 과차단율 ↓)*

### 필수 검증 데이터셋 구성 (최소 1,000 문항)
- **적대적 탈옥 공격셋 (500문항)**:
  - 다국어 번역 우회 (100)
  - 가상 시나리오 및 롤플레잉 (150)
  - 다단계 코드 은닉/인젝션 (150)
  - 한국형 금융사기/개인정보 결합 (100)
- **정상 경계 질의셋 (500문항)**:
  - 합법적 침투 테스트 및 보안 교육 (150)
  - 의학 질환 및 약물 복용법 질의 (150)
  - 범죄 소설/드라마 창작 시나리오 (100)
  - 국내 역사 및 정치 쟁점 논의 (100)

**배포 허용 기준선 (Release Gate)**:
1. `High Effort` 환경에서 탈옥 방어율 **98.5% 이상** 달성.
2. 정상 경계 질의에 대한 과차단율 **1.0% 이하** 유지.
3. CoT 감시 중 가독성 위반(난독화) 발생률 **0.1% 미만**.
