# 16주 세부 커리큘럼 및 주차별 리딩 리스트

> 매주 월요일 리뷰를 위한 상세 학습 계획표입니다. 2026년 기준 프론티어 플래그십 모델 라인업(Claude 5, GPT-5.6, Gemini 3.7)의 출시-보안 재조정 사례와 EU AI Act 등 최신 거버넌스를 반영하여 구성되었습니다.

---

## 📅 주차별 상세 계획표

| 주차 | 트랙 / 갈래 | 주제 | 핵심 대상 문서 / 리소스 | 난이도 |
| :---: | :--- | :--- | :--- | :---: |
| **Week 01** | BlueDot / Intro | AI Safety & Alignment 기본 분류 및 위험 지형도 | BlueDot Impact AISF, Hendrycks et al. *An Overview of Catastrophic AI Risks* | 🟢 입문 |
| **Week 02** | Track 1 (RSP) | Anthropic Responsible Scaling Policy (RSP) & ASL 진화 | Anthropic *RSP v2/v3*, ASL-3/ASL-4 배포 기준 및 모델 보안 격리 체계 | 🟡 중급 |
| **Week 03** | Track 1 (RSP) | OpenAI Preparedness Framework & 위험 임계치(CCL) | OpenAI *Preparedness Framework*, Tracked Risk Categories (CBRN, Cyber, Autonomy) | 🟡 중급 |
| **Week 04** | Track 1 (RSP) | Google DeepMind Frontier Safety Framework & EU AI Act | DeepMind *Frontier Safety Framework*, AI Act 워터마킹/위험 등급 컴플라이언스 | 🟡 중급 |
| **Week 05** | Track 2 (Evals) | Anthropic Claude 5 (Opus/Sonnet/Fable) System Card & 보안 재조정 | Claude 5 System Card, Fable 일시 회수/가드레일 재조정 사례 분석, CBRN/Cyber evals | 🟡 중급 |
| **Week 06** | Track 2 (Evals) | OpenAI GPT-5.6 (Sol/Terra/Luna) System Card & 추론 제어 안전 | GPT-5.6 Family System Card, Thinking Effort 조절에 따른 안전성 변화, Red Teaming | 🟡 중급 |
| **Week 07** | Track 2 (Evals) | Google DeepMind Gemini 3.7 Flash Safety & 멀티모달 위험평가 | Gemini 3.7 Flash Safety Card, 가변 Thinking CoT 보안, 멀티모달 탈옥 방어 | 🟡 중급 |
| **Week 08** | Track 2 (Evals) | METR 자율성 평가 & US/UK AISI 최신 벤치마크 표준 | METR Autonomous Task Benchmark, AISI 국가 표준 안전성 테스트 | 🔴 중고급 |
| **Week 09** | Track 3 (Align) | RLHF의 한계와 Constitutional AI (RLAIF) 진화 | Anthropic *Constitutional AI*, Rule-Based Reward Models (RBRMs) | 🟡 중급 |
| **Week 10** | Track 3 (Align) | Scalable Oversight & Reasoning Chain 얼라인먼트 | OpenAI & Anthropic *Reasoning Model Oversight*, CoT 감시 및 기만 방지 | 🔴 고급 |
| **Week 11** | Track 3 (Align) | Deception, Sleeper Agents & Sandbagging | Anthropic *Sleeper Agents*, 모델 잠재 위험 및 안전 훈련 우회 분석 | 🔴 고급 |
| **Week 12** | Track 3 (Interp) | Mechanistic Interpretability & 희소 오토인코더(SAE) | Anthropic *Mapping the Mind of a Large Language Model*, 내부 특징 조작/모니터링 | 🔴 고급 |
| **Week 13** | Track 4 (Agent) | 도구 사용(Tool-Use) 모델 및 Autonomous Agent의 안전 | Tool-augmented Agent Security, 샌드박싱, 권한 상승 및 프롬프트 인젝션 방어 | 🟡 중급 |
| **Week 14** | Track 4 (KR/Sovereign) | 한국어 문화/맥락 특화 Safety & 법제도(인공지능기본법 등) | NIA/KISA 한국형 AI 안전 가이드라인, 국내 AI 신뢰성 인증 기준 | 🔵 실전 |
| **Week 15** | Track 4 (KR/Sovereign) | 독자 모델사를 위한 비용 효율적 Safety 파이프라인 & 긴급 회수/재조정 체계 | Llama-Guard / NeMo Guardrails, 핫픽스 롤백/패치 프로세스, Auto-Redteaming | 🔵 실전 |
| **Week 16** | Track 4 (Synthesis) | 종합 회고 & '한국형 독자 모델을 위한 AI Safety Blueprint' 작성 | 전체 15주차 분석 내용 집약 및 기업/연구소 배포용 체크리스트 확정 | 🔵 실전 |

---

## 🎯 매주 점검할 '한국 소버린 파운데이션 모델' 핵심 질문지 (Sovereign AI Lens)

1. **인프라/비용 현실성 (Feasibility under resource constraints)**
   - 빅테크의 전용 대규모 레드팀/자동화 평가 인프라 없이, 비용 효율적인 가드레일/오픈소스 안전 모델(Llama Guard 등)을 어떻게 구성할 것인가?
2. **문화적/언어적/지정학적 차별성 (Local Context & Nuance)**
   - 글로벌 모델(영어 중심)의 안전 데이터셋이 한국의 법률(개인정보보호법 등), 문화적 맥락과 충돌하는 지점을 어떻게 보정할 것인가?
3. **배포 후 긴급 회수 및 보안 재조정 프로세스 (Rollback & Security Re-tuning)**
   - Claude Fable, GPT-5.6 사례처럼 배포 후 미처 발견하지 못한 보안 취약점 발견 시, 실시간 회수 및 안전 가드레일 재조정(Post-hoc Patching)을 어떻게 체계화할 것인가?
