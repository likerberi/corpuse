# 16주 세부 커리큘럼 및 주차별 리딩 리스트

> 매주 월요일 리뷰를 위한 상세 학습 계획표입니다. 각 주차는 **[1] 핵심 개념**, **[2] 공식 리소스**, **[3] 한국 파운데이션 모델 개발팀을 위한 관전 포인트**로 구성됩니다.

---

## 📅 주차별 상세 계획표

| 주차 | 트랙 / 갈래 | 주제 | 핵심 대상 문서 / 리소스 | 난이도 |
| :---: | :--- | :--- | :--- | :---: |
| **Week 01** | BlueDot / Intro | AI Safety & Alignment 기본 분류 및 위험 지형도 | BlueDot Impact AISF Week 1~2, Hendrycks et al. *An Overview of Catastrophic AI Risks* | 🟢 입문 |
| **Week 02** | Track 1 (RSP) | Anthropic Responsible Scaling Policy (RSP) v1/v2 & ASL | Anthropic *Responsible Scaling Policy*, ASL-2/ASL-3 Deployment Standards | 🟡 중급 |
| **Week 03** | Track 1 (RSP) | OpenAI Preparedness Framework & 위험 임계치(CCL) | OpenAI *Preparedness Framework (Beta & Updated)*, Tracked Risk Categories | 🟡 중급 |
| **Week 04** | Track 1 (RSP) | Google DeepMind Frontier Safety Framework | DeepMind *Frontier Safety Framework*, Critical Capability Levels (CCLs) | 🟡 중급 |
| **Week 05** | Track 2 (Evals) | Anthropic Claude 3 / 3.5 System Card & 위험평가 | Anthropic *Claude 3 / 3.5 Sonnet System Card*, CBRN & Cyber evaluations | 🟡 중급 |
| **Week 06** | Track 2 (Evals) | OpenAI GPT-4 / GPT-4o System Card & Red Teaming | OpenAI *GPT-4o System Card*, Red Teaming Network, Unauthorized Voice Risk | 🟡 중급 |
| **Week 07** | Track 2 (Evals) | Google DeepMind Gemini 1.5 / 2.0 Safety & 멀티모달 위험 | Google *Gemini 1.5 System Card & Safety Evals*, Multimodal Red Teaming | 🟡 중급 |
| **Week 08** | Track 2 (Evals) | METR 자율성 평가 & US/UK AISI 벤치마크 표준 | METR *Evaluating Autonomous Replication & Acquisition*, UK AISI Benchmark | 🔴 중고급 |
| **Week 09** | Track 3 (Align) | RLHF의 한계와 Constitutional AI (RLAIF) | Anthropic *Constitutional AI: Harmlessness from AI Feedback*, BlueDot Week 4 | 🟡 중급 |
| **Week 10** | Track 3 (Align) | Scalable Oversight & Weak-to-Strong Generalization | OpenAI *Weak-to-Strong Generalization*, Anthropic *AI Written Critiques* | 🔴 고급 |
| **Week 11** | Track 3 (Align) | Deception, Sleeper Agents & Sandbagging | Anthropic *Sleeper Agents: Training Deceptive LLMs that Persist Through Safety Training* | 🔴 고급 |
| **Week 12** | Track 3 (Interp) | Mechanistic Interpretability & 희소 오토인코더(SAE) | Anthropic *Mapping the Mind of a Large Language Model (Golden Gate Claude)* | 🔴 고급 |
| **Week 13** | Track 4 (Agent) | 도구 사용(Tool-Use) 모델 및 Autonomous Agent의 안전 | OWASP Top 10 for LLM Applications, Tool-augmented Agent Security | 🟡 중급 |
| **Week 14** | Track 4 (KR/Sovereign) | 한국어 문화/맥락 특화 Safety & 법제도(인공지능기본법 등) | NIA/KISA 한국형 AI 안전 가이드라인, 국내 AI 모델 윤리/안전성 보고서 | 🔵 실전 |
| **Week 15** | Track 4 (KR/Sovereign) | 독자 파운데이션 모델을 위한 비용 효율적 Safety 파이프라인 | Open-source Guardrails (Llama-Guard, NeMo Guardrails, Auto-Redteaming) | 🔵 실전 |
| **Week 16** | Track 4 (Synthesis) | 종합 회고 & '한국형 독자 모델을 위한 AI Safety Blueprint' 작성 | 전체 15주차 분석 내용 집약 및 기업/연구소 배포용 체크리스트 확정 | 🔵 실전 |

---

## 🎯 매주 점검할 '한국 소버린 파운데이션 모델' 질문지 (Lens for Sovereign AI)

매주 문서를 읽을 때 아래 세 가지 질문을 항상 던집니다:

1. **인프라/비용 현실성 (Feasibility under resource constraints)**
   - 프론티어 빅테크(앤트로픽, 오픈AI 등)는 수천억 원 규모의 컴퓨팅과 전담 레드팀을 투입한다.
   - 우리는 1/10, 1/100의 리소스로 이 위험(예: 탈옥, 편향, 환각, 사이버 공격 악용)을 어떻게 효율적으로 방어할 것인가?
2. **문화적/언어적/지정학적 차별성 (Local Context & Nuance)**
   - 서구권 중심의 Safe Dataset / Constitutional Rules(헌법)이 한국의 사회적 가치관, 법적 책임(개인정보보호법, 선거법, 명예훼손 등)과 어떻게 충돌하거나 부합하는가?
   - 한국어 토큰 환경에서 탈옥(Jailbreak) 및 유해 프롬프트(Harmful Prompts)는 어떻게 다르게 동작하는가?
3. **독자 모델의 비즈니스 생존과 신뢰도 (Trust & Enterprise Readiness)**
   - 글로벌 빅테크 API를 쓰지 않고 우리 독자 모델을 쓰는 B2B/B2G 고객들에게 어떤 안전 인증/시스템 카드를 제공해야 설득력을 갖출 수 있는가?
