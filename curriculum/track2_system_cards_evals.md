# Track 2: System Cards & Dangerous Capabilities Evaluations

> **프론티어 모델의 실전 배포 전 위험 평가(Dangerous Capability Evals), 회수/보안 재조정 사례 및 시스템 카드 심층 분석**

---

## 📌 트랙 개요
Track 2에서는 최신 프론티어 모델(Claude 5 시리즈, GPT-5.6 시리즈, Gemini 3.7 Flash)의 **공식 시스템 카드(System Cards)**와 **전문 위험 평가(Evals) 보고서**를 분해 분석합니다. 단순한 벤치마크 점수가 아닌, 모델이 지닌 오용 잠재력(CBRN 조력, 사이버 침투 공격), 자율적 위험(에이전트 자율 증식, 기만), 멀티모달 악용(음성 복제, 시각 탈옥) 및 **출시 후 회수(Block/Rollback) 및 보안 재조정(Security Re-tuning) 사례**를 다룹니다.

---

## 🎯 핵심 학습 목표
1. **시스템 카드의 표준 구조 분석**: 모델 개요, 데이터 구성, 훈련 파이프라인, 안전 평가 지표, 잔여 위험(Residual Risks) 기술 방식 습득.
2. **Dangerous Capabilities 계측 방법론**:
   - **CBRN (Chemical, Biological, Radiological, Nuclear)**: 생물무기 합성 프로토콜 조력 평가.
   - **Cyber Offensive**: 제로데이 취약점 분석, 악성코드 자동 생성 및 익스플로잇 실행 평가.
   - **Autonomous Capabilities (자율 복제/행동)**: 환경 탐색, 크라우드워커 고용, 가상화폐 결제 등 METR 스타일의 자율 과업 수행력.
3. **출시 후 회수 및 보안 재조정(Rollback & Patching) 분석**:
   - Claude Fable 5, GPT-5.6 등 출시 직후 미처 포착되지 못한 사이버/탈옥 취약점으로 인해 일시 차단(Block) 후 가드레일 재조정 및 재출시된 실제 엔터프라이즈 운영 사례 분석.
4. **가변 추론(Thinking) 환경에서의 안전성 계측**:
   - CoT(Chain of Thought) 토큰 소비 증가에 따른 가드레일 우회 위험 및 기만(Deception) 발생 여부 검증.

---

## 📖 핵심 평가 매트릭스 비교

| 평가 영역 | 주요 지표 및 벤치마크 | 선도 평가 기관 | 주요 완화 기법 |
| :--- | :--- | :--- | :--- |
| **CBRN 위험** | 생화학 프로토콜 유용성(Actionability), 미공개 정보 추출률 | Anthropic, AISI, 외부 생물안전 전문가 | 데이터셋 필터링, 지식 삭제(Unlearning), 거부 응답 훈련 |
| **사이버 공격력** | CTF 챌린지 성공률, 취약점 탐지 자동화 | OpenAI, UK AISI, Cyber Red Teams | 도구 호출 권한 통제, 위험 도메인 실시간 분류기 |
| **자율 과업 수행** | METR Autonomous Task Benchmark (장시간 작업 성공률) | METR, US AISI | 모니터링 로그 분석, 샌드박스 격리, 휴먼인더루프 |
| **추론 기만/탈옥** | Jailbreak Success Rate (JSR), CoT Reasoning Deception | 내부 레드팀, 오픈소스 레드팀 도구 | RLAIF 헌법 기반 거부, 추론 토큰 필터링 |

---

## 🇰🇷 한국 소버린 AI 개발팀 관점 시사점

1. **국내 실정에 맞는 시스템 카드 표준화**
   - 글로벌 기준(Anthropic/OpenAI)의 구조를 차용하되, 한국의 법적 의무 사항(개인정보 비식별화, 저작권 필터링 현황, 한국어 편향/안전성 테스트 결과)을 명시하는 독자 시스템 카드 템플릿 정립.
2. **긴급 차단 및 사후 패치 프로토콜(Incident Response Runbook)**
   - 모델 배포 후 예기치 못한 안전성 결함 발견 시 서비스 중단 없이 가드레일 레이어만 즉각 교체하거나 특정 파라미터/토큰 경로를 차단하는 핫픽스 체계 구축.
