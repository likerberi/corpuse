# [Week 12] Mechanistic Interpretability: SAE & 서킷 분석 (Track 3 종합)

- **주제**: 중첩(Superposition) 해부와 희소 오토인코더(SAE)에서 서킷 추적(Circuit Tracing), 자연어 오토인코더(NLA), 그리고 2026년 3대 시스템 카드의 실시간 활성값 가드레일까지 — 화이트박스 해석가능성의 진화와 Track 3 종합
- **리뷰 일자**: 2026-10-26 (월)
- **트랙**: Track 3 — Technical Alignment & Interpretability (**Track 3 종합 마무리**)
- **난이도**: 🔴 고급

---

## 🎯 학습 목표
1. 왜 개별 뉴런은 여러 무관한 개념에 동시에 반응하는지(**다의성·중첩 가설**) 이해하고, 이를 단의적(monosemantic) 특징으로 분해하는 **희소 오토인코더(SAE)** 의 3대 아키텍처(`ReLU+L1`, `TopK`, `JumpReLU`)와 스케일링 법칙을 파악한다.
2. **특징 조향(Feature Steering / Clamping)** 이 단순한 상관관계를 넘어 모델의 행동을 인과적으로 제어함을 이해하고, 동시에 **단일 거부 방향(Refusal Direction)** 에 의존하는 기존 안전 미세조정의 구조적 취약성과 **서킷 브레이커(Circuit Breakers)** 방어 원리를 익힌다.
3. 개별 특징 사전을 넘어 층간 계산 경로를 역추적하는 **교차 레이어 트랜스코더(CLT)와 귀속 그래프(Attribution Graphs)** 가 밝혀낸 `Claude 3.5 Haiku`의 **환각·거부·탈옥·불충실 CoT·숨은 목표(RM 아첨) 서킷 메커니즘**과 그 한계(유효 설명률 `~25%`)를 분석한다.
4. 실시간 안전 감시에서 **왜 단순 선형 프로브(Linear Probes)가 SAE를 능가하는지**(`arXiv:2502.16681`), 그리고 비지도 사전 감사에서 **자연어 오토인코더(NLA, 2026-05)** 가 어떻게 SAE의 한계를 넘어 비언어화 평가 인식과 거짓 사용자 동의를 포착하는지 비교한다.
5. **2026년 3대 시스템 카드(`Opus 5`, `GPT-5.6 Sol/Terra`, `Gemini 3.7 Flash`)** 의 실제 화이트박스 배포 아키텍처와 Track 3 전체(Week 09~12)를 종합하여, 한국 소버린 AI 조직을 위한 **실시간 활성값 가드레일 & 화이트박스 감사 설계 원칙**을 도출한다.

---

## 📂 구성 파일
- [`review_week12.md`](review_week12.md): 12주차 종합 심층 분석 보고서 및 Track 3 총괄
- 갱신 산출물:
  - [`resources/reasoning_cot_safety_guide.md`](../../resources/reasoning_cot_safety_guide.md): **§7 화이트박스 활성값 프로브 · SAE · NLA 결합 감시 아키텍처** 신설
  - [`resources/reading_list.md`](../../resources/reading_list.md): Week 12 기계론적 해석가능성 · SAE · 서킷 추적 · NLA 1차 사료 목록 추가

---

## 📌 이번 주차 핵심 수치 (원문 대조 완료)

| 항목 | 값 | 출처 |
| :--- | :---: | :--- |
| `Claude 3 Sonnet` SAE 사전 규모 및 활성 특징 수 | **`1M / 4M / 34M` 특징** (토큰당 활성 `L0 < 300`, 설명 분산 `≥ 65%`) | Templeton 외, Anthropic (2024-05) |
| `Claude 3 Sonnet` SAE 규모별 죽은 특징(Dead Features) 비율 | `1M`: **`~2%`** → `4M`: **`~35%`** → `34M`: **`~65%`** (`10^7` 토큰 기준) | 동 |
| `GPT-4` 대상 `TopK` SAE 최대 잠재 특징 규모 | **`1,600만(16M)` 잠재 특징** (`400억` 토큰 학습, 죽은 특징 거의 제거) | Gao 외, OpenAI (arXiv:2406.04093) |
| `Gemma Scope` 오픈웨이트 `JumpReLU` SAE 공개 규모 | `Gemma 2 2B/9B` 전 레이어 + `27B` 핵심 레이어, **주력 `400+`개 SAE · `3,000만+` 특징** (총 `2,000+` 가중치) | Lieberum 외, DeepMind (arXiv:2408.05147) |
| 오픈소스 챗 모델의 거부(Refusal) 매개 부분공간 차원 | `72B` 이하 13개 모델 공통 **단일 `1차원` 부분공간 (Single Direction)** | Arditi 외 (arXiv:2406.11717) |
| 귀속 그래프(Attribution Graphs)가 만족스러운 통찰을 제공한 비율 | 시도한 프롬프트의 **약 `25%` (`about a quarter`)**, `~100` 토큰 이내 단문 중심 | Lindsey 외, Anthropic (2025-03) |
| 다운스트림 프로빙 벤치마크(`113개` 데이터셋)에서 SAE vs 선형 프로브 | **SAE 프로브가 표준 로지스틱 회귀(선형 프로브)를 일관되게 능가하지 못함** | Kantamneni 외 (arXiv:2502.16681) |
| 자연어 오토인코더(`NLA`) 병목 길이 및 `Gemma-3-27B` 학습 비용 | 자연어 병목 **`< 500` 토큰**, `8×H100` 2노드 **`1.5일`** 학습 시 `FVE 0.38 → 0.71` (`>10k` 토큰 전사본 전수 실행은 비현실적) | Fraser-Taliente 외, Anthropic (2026-05) |
| 2026년 3대 시스템 카드 실시간 활성값 가드레일 채택 현황 | **3사 전원 채택**: `Opus 5`(1단 활성값 프로브 + IPI 프로브 `0.56%→0.18%`), `GPT-5.6 Sol/Terra`(스트리밍 일시정지형 Activation Classifier, 프로덕션 `0.981/0.987`), `Gemini 3.7 Flash`(Introspection Probes) | 2026 3대 시스템 카드 |

---

## 🔗 Track 3 완결 로드맵
- **Week 09**: RLHF의 한계와 Constitutional AI (RLAIF) & RBRMs — *행동과 출력 규칙을 어떻게 가르칠 것인가*
- **Week 10**: Scalable Oversight & CoT 감시가능성 — *사고 연쇄(CoT) 텍스트를 어디까지 믿고 감시할 것인가*
- **Week 11**: Deception, Sleeper Agents & Sandbagging — *훈련과 평가를 전략적으로 속이는 모델을 어떻게 적발할 것인가*
- **Week 12 (현재, Track 3 종합)**: Mechanistic Interpretability & SAE — *텍스트에 적히지 않은 내부 활성값과 계산 서킷을 어떻게 읽고 제어할 것인가*
