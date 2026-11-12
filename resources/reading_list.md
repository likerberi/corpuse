# 📚 Official AI Safety Resources & Reading List

AI 안전 분야 3대 프론티어 연구소(Anthropic, OpenAI, Google DeepMind)와 제3자 안전 평가 기관(BlueDot Impact, METR, AISI)의 핵심 공식 문서 링크 모음입니다.

---

## 1. BlueDot Impact & Foundational Risk Taxonomies (Week 01)
- **AI Safety Fundamentals (Alignment Course)**: [https://bluedot.org/courses/alignment](https://bluedot.org/courses/alignment)
- **AI Safety Fundamentals (Governance Course)**: [https://bluedot.org/courses/governance](https://bluedot.org/courses/governance)
- **Course Curriculum & Readings**: [https://bluedot.org/courses](https://bluedot.org/courses)
- **An Overview of Catastrophic AI Risks** (Hendrycks, Mazeika, Woodside, CAIS, 2023): [arXiv:2306.12001](https://arxiv.org/abs/2306.12001) — 4대 재앙적 위험 원천 및 스위스 치즈 다층 방어
- **International AI Safety Report** (Bengio 외 100인, 30개국·UN·EU·OECD 위임, 2025-01): [arXiv:2501.17805](https://arxiv.org/abs/2501.17805) — 범용 AI 위험 3대 국제 표준 분류(악의적 사용·오작동·시스템적 위험)

---

## 2. Anthropic
### Responsible Scaling Policy (RSP)
- **Responsible Scaling Policy Hub (현행 전문)**: [https://www.anthropic.com/responsible-scaling-policy](https://www.anthropic.com/responsible-scaling-policy)
- **RSP Version 3 (2026-02-24 발효, 현행)**: [https://www.anthropic.com/news/responsible-scaling-policy-v3](https://www.anthropic.com/news/responsible-scaling-policy-v3) — 자사 단독 공약과 산업계 권고 분리, `CB-1`/`CB-2` 및 AI R&D 2계층 세분화, 공개 Risk Report 및 LTBT 외부 감사권
- **Anthropic's Responsible Scaling Policy (Version 1, 2023-09)**: [https://www.anthropic.com/news/anthropics-responsible-scaling-policy](https://www.anthropic.com/news/anthropics-responsible-scaling-policy)
- **RSP Version 2 (2024-10 개정)**: [https://www.anthropic.com/news/announcing-our-updated-responsible-scaling-policy](https://www.anthropic.com/news/announcing-our-updated-responsible-scaling-policy)

### System Cards & Model Evaluations
- **System Card: Claude Opus 5 (2026-07-24, 193p)**: [PDF](https://www-cdn.anthropic.com/c5fbac3f0b1280a933ebd26d3cb8bb9f5bdeaf48/Claude%20Opus%205%20System%20Card.pdf) — RSP 평가(CB-1/CB-2/AI R&D), Cyber, Safeguards, Agentic safety, Alignment assessment
- **System Card: Claude Sonnet 5 (2026-06-30)**: [PDF](https://www-cdn.anthropic.com/9e6a1044980d8c4ed85669faf9c2a8342e2e9f1e/Claude%20Sonnet%205%20System%20Card.pdf)
- **Claude Opus 4.5 System Card (2025-11)**: [https://www.anthropic.com/claude-opus-4-5-system-card](https://www.anthropic.com/claude-opus-4-5-system-card)
- **Claude 3.5 Sonnet / Haiku System Card Archive**: [PDF](https://assets.anthropic.com/m/1cd9d098ac3e6467/original/Claude-3-Model-Card-October-Addendum.pdf)
- **Transparency & 규제 대응(Frontier Compliance Framework, EU AI Act GPAI CoP / California TFAIA)**: [https://www.anthropic.com/transparency](https://www.anthropic.com/transparency)

### 회수–재배포(Rollback & Redeploy) 사례 사료 — Claude Fable 5 / Mythos 5
- **Claude Fable 5 and Claude Mythos 5 (2026-06-09 출시 공지)**: [https://www.anthropic.com/news/claude-fable-5-mythos-5](https://www.anthropic.com/news/claude-fable-5-mythos-5)
- **Redeploying Claude Fable 5 (회수·재배포 공지)**: [https://www.anthropic.com/news/redeploying-fable-5](https://www.anthropic.com/news/redeploying-fable-5)
- **Introducing Claude Fable 5.1 and Claude Mythos 5.1 (2026-09)**: [https://www.anthropic.com/claude-fable-and-mythos-5-1](https://www.anthropic.com/claude-fable-and-mythos-5-1)
- **Claude Platform Docs — Fable 5 / Mythos 5 개요**: [https://platform.claude.com/docs/en/about-claude/models/introducing-claude-fable-5-and-claude-mythos-5](https://platform.claude.com/docs/en/about-claude/models/introducing-claude-fable-5-and-claude-mythos-5)

### Alignment & Interpretability Research
- **Constitutional AI: Harmlessness from AI Feedback (RLAIF)**: [https://www.anthropic.com/research/constitutional-ai-harmlessness-from-ai-feedback](https://www.anthropic.com/research/constitutional-ai-harmlessness-from-ai-feedback)
- **Sleeper Agents: Training Deceptive LLMs**: [https://www.anthropic.com/news/sleeper-agents-training-deceptive-llms-that-persist-through-safety-training](https://www.anthropic.com/news/sleeper-agents-training-deceptive-llms-that-persist-through-safety-training)
- **Mapping the Mind of a Large Language Model (Dictionary Learning / SAEs)**: [https://www.anthropic.com/news/mapping-mind-language-model](https://www.anthropic.com/news/mapping-mind-language-model)
- **Reasoning Models Oversight & CoT Safety**: [https://www.anthropic.com/research/reasoning-models-dont-say-think](https://www.anthropic.com/research/reasoning-models-dont-say-think)

---

## 3. OpenAI
### Preparedness Framework & Governance
- **Preparedness Framework Version 2 (2025-04-15, 현행 전문 PDF)**: [PDF](https://cdn.openai.com/pdf/18a02b5d-6b67-4cec-ab64-68cdfbddebcd/preparedness-framework-v2.pdf) — 3대 추적 범주(`Bio/Chem`, `Cyber`, `AI Self-Improvement`) + 5대 연구 범주, `High`/`Critical` 임계치 및 세이프가드 충분성 입증
- **OpenAI Preparedness Framework Overview**: [https://openai.com/safety/preparedness/](https://openai.com/safety/preparedness/)
- **Preparedness Framework Beta Archive (2023-12 PDF)**: [https://cdn.openai.com/openai-preparedness-framework-beta.pdf](https://cdn.openai.com/openai-preparedness-framework-beta.pdf)

### System Cards & Safety Evals
- **GPT-5.6 Family (Sol / Terra / Luna) System Card**: [Deployment Safety Hub](https://deploymentsafety.openai.com/gpt-5-6) · [PDF (2026-07-09)](https://deploymentsafety.openai.com/gpt-5-6/gpt-5-6.pdf)
- **GPT-5.5 System Card (2026-04-23)**: [https://openai.com/index/gpt-5-5-system-card/](https://openai.com/index/gpt-5-5-system-card/)
- **GPT-4o & Reasoning System Card Archive**: [https://openai.com/index/gpt-4o-system-card/](https://openai.com/index/gpt-4o-system-card/)

### Alignment & Reasoning Research
- **Improving model safety behavior with rule-based rewards (RBRMs)**: [https://openai.com/index/improving-model-safety-behavior-with-rule-based-rewards/](https://openai.com/index/improving-model-safety-behavior-with-rule-based-rewards/)
- **Evaluating chain-of-thought monitorability**: [https://openai.com/index/evaluating-chain-of-thought-monitorability/](https://openai.com/index/evaluating-chain-of-thought-monitorability/)
- **Detecting misbehavior in frontier reasoning models (CoT monitoring)**: [https://openai.com/index/chain-of-thought-monitoring/](https://openai.com/index/chain-of-thought-monitoring/)
- **OpenAI Alignment Research Blog**: [https://alignment.openai.com/](https://alignment.openai.com/)
- **Weak-to-Strong Generalization**: [https://openai.com/index/weak-to-strong-generalization/](https://openai.com/index/weak-to-strong-generalization/)

---

## 4. Google DeepMind
### Frontier Safety Framework
- **FSF v3.1 전문 (2026-04-17, 현행)**: [PDF](https://storage.googleapis.com/deepmind-media/DeepMind.com/Blog/strengthening-our-frontier-safety-framework/frontier-safety-framework_3-1.pdf) — TCL 신설, CBRN·Cyber·Harmful Manipulation·ML R&D/Misalignment 4개 도메인
- **Strengthening our Frontier Safety Framework (v3.1 공지)**: [https://deepmind.google/blog/strengthening-our-frontier-safety-framework/](https://deepmind.google/blog/strengthening-our-frontier-safety-framework/)
- **Updating the Frontier Safety Framework (v3 시점)**: [https://deepmind.google/blog/updating-the-frontier-safety-framework/](https://deepmind.google/blog/updating-the-frontier-safety-framework/)
- **Introducing the Frontier Safety Framework (v1, 2024-05)**: [https://deepmind.google/discover/blog/introducing-the-frontier-safety-framework/](https://deepmind.google/discover/blog/introducing-the-frontier-safety-framework/)
- **Frontier safety 허브**: [https://deepmind.google/frontier-safety/](https://deepmind.google/frontier-safety/)
- **An Approach to Technical AGI Safety and Security (FSF v3.1 각주 7·10 인용)**: [arXiv:2504.01849](https://arxiv.org/abs/2504.01849)
- **Evaluating Frontier Models for Stealth and Situational Awareness (FSF v3.1 각주 15 인용)**: [arXiv:2505.01420](https://arxiv.org/abs/2505.01420)

### Frontier Safety Reports (모델별 판정서)
- **Gemini 3.7 Flash Frontier Safety Framework Report (2026-08, 41p)**: [PDF](https://storage.googleapis.com/deepmind-media/gemini/gemini_3-7_flash_fsf_report.pdf) — 도메인별 T/CCL 판정, 경보 임계치, 인간 행동 실험, 은밀성·상황 인식 평가

### Model Cards
- **Gemini 3.8 Flash (2026-09, 최신)**: [PDF](https://storage.googleapis.com/deepmind-media/Model-Cards/Gemini-3-8-Flash-Model-Card.pdf) · [웹](https://deepmind.google/models/model-cards/gemini-3-8-flash/)
- **Gemini 3.7 Flash (2026-08)**: [PDF](https://storage.googleapis.com/deepmind-media/Model-Cards/Gemini-3-7-Flash-Model-Card.pdf) · [웹](https://deepmind.google/models/model-cards/gemini-3-7-flash/)
- **Gemini 3.6 Flash**: [PDF](https://storage.googleapis.com/deepmind-media/Model-Cards/Gemini-3-6-Flash-Model-Card.pdf) *(3.7의 아키텍처·학습 데이터 원본)*
- **Gemini 3.1 Pro**: [PDF](https://storage.googleapis.com/deepmind-media/Model-Cards/Gemini-3-1-Pro-Model-Card.pdf) · [웹](https://deepmind.google/models/model-cards/gemini-3-1-pro/)
- **Gemini 3 Pro**: [PDF](https://storage.googleapis.com/deepmind-media/Model-Cards/Gemini-3-Pro-Model-Card.pdf) · [웹](https://deepmind.google/models/model-cards/gemini-3-pro/)
- **Gemini 3.1 Flash-Lite**: [PDF](https://storage.googleapis.com/deepmind-media/Model-Cards/Gemini-3-1-Flash-Lite-Model-Card.pdf)
- **Gemini 모델 계열 개요**: [https://deepmind.google/models/gemini/](https://deepmind.google/models/gemini/)

> ✅ **정정 (2026-09-21)**: 이전 판에 *"커리큘럼의 Gemini 3.7 Flash는 실재하지 않는 것으로 보인다"* 는 메모를 달았으나 **사실과 다릅니다.** Gemini 3.7 Flash는 2026년 8월 공개된 실제 모델이며 전용 Frontier Safety Report까지 발행되어 있습니다. 당시 검색 결과만으로 단정한 것이 원인이었습니다 — **부재 증명은 검색 누락과 구별되지 않으므로, 앞으로 "존재하지 않음" 판정은 내리지 않고 "확인 필요"로만 표기합니다.**

---

## 5. Third-Party Standards & Evaluation Bodies

### METR (Model Evaluation & Threat Research)
- **METR 홈**: [https://metr.org/](https://metr.org/)
- **Frontier Risk Report (Feb–Mar 2026, 2026-05-19)** — 기관 단위·주기적·내부 배포 평가 시범: [https://metr.org/blog/2026-05-19-frontier-risk-report/](https://metr.org/blog/2026-05-19-frontier-risk-report/)
- **Time Horizon 1.1 (2026-01-29)**: [https://metr.org/blog/2026-1-29-time-horizon-1-1/](https://metr.org/blog/2026-1-29-time-horizon-1-1/)
- **Clarifying limitations of time horizon (2026-01-22)** — 지표 오독 8가지 교정: [https://metr.org/notes/2026-01-22-time-horizon-limitations/](https://metr.org/notes/2026-01-22-time-horizon-limitations/)
- **Task-Completion Time Horizons (상시 갱신 대시보드)**: [https://metr.org/time-horizons/](https://metr.org/time-horizons/)
- **Measuring AI Ability to Complete Long Software Tasks (원 논문, 2025-03)**: [https://metr.org/blog/2025-03-19-measuring-ai-ability-to-complete-long-tasks/](https://metr.org/blog/2025-03-19-measuring-ai-ability-to-complete-long-tasks/)

### UK AI Security Institute (UK AISI)
- **How fast is autonomous AI cyber capability advancing? (2026-05-13)** — 사이버 타임 호라이즌 배가 주기: [https://www.aisi.gov.uk/blog/how-fast-is-autonomous-ai-cyber-capability-advancing](https://www.aisi.gov.uk/blog/how-fast-is-autonomous-ai-cyber-capability-advancing)
- **Measuring AI Agents' Progress on Multi-Step Cyber Attack Scenarios (2026-03-16)**: [https://www.aisi.gov.uk/research/measuring-ai-agents-progress-on-multi-step-cyber-attack-scenarios](https://www.aisi.gov.uk/research/measuring-ai-agents-progress-on-multi-step-cyber-attack-scenarios) · [arXiv:2603.11214](https://arxiv.org/abs/2603.11214)
- **5 key findings from our first Frontier AI Trends Report (2025-12-18)**: [https://www.aisi.gov.uk/blog/5-key-findings-from-our-first-frontier-ai-trends-report](https://www.aisi.gov.uk/blog/5-key-findings-from-our-first-frontier-ai-trends-report)
- **Inspect (오픈소스 평가 프레임워크, METR TH1.1도 채택)**: [https://inspect.aisi.org.uk/](https://inspect.aisi.org.uk/)

### 국내 평가 기관·체계
- **인공지능안전연구소 (Korea AISI, 2024-11 출범, ETRI 산하)**: [https://www.aisi.re.kr/](https://www.aisi.re.kr/)
- **금융보안원 금융 AI 안전성·신뢰성 평가 프레임워크 (2026-08 발표, 2027 본격 적용)**: [보도 (아시아경제)](https://www.asiae.co.kr/en/article/economic-general/2026081214055143616)

### 기타
- **US AI Safety Institute (NIST)**: [https://www.nist.gov/artificial-intelligence/artificial-intelligence-safety-institute](https://www.nist.gov/artificial-intelligence/artificial-intelligence-safety-institute)
- **CAIS (Center for AI Safety)**: [https://www.safe.ai/](https://www.safe.ai/)
- **RAND — Securing AI Model Weights (RRA2849-1)**: [https://www.rand.org/pubs/research_reports/RRA2849-1.html](https://www.rand.org/pubs/research_reports/RRA2849-1.html) — DeepMind FSF의 보안 등급(SL 2+/3/4) 기준 문서
- **Gray Swan — Indirect Prompt Injection 대규모 공개 대회 (arXiv:2603.15714)**: [https://arxiv.org/abs/2603.15714](https://arxiv.org/abs/2603.15714)
- **Stronger adaptive attacks bypass LLM jailbreak/prompt-injection defenses (arXiv:2510.09023)**: [https://arxiv.org/abs/2510.09023](https://arxiv.org/abs/2510.09023)

### 주제별: Scalable Oversight & CoT 감시가능성 (Week 10)
- **Chain of Thought Monitorability: A New and Fragile Opportunity for AI Safety** (Korbak 외 41인, 2025): [arXiv:2507.11473](https://arxiv.org/abs/2507.11473) — 감시가능성의 두 근거(필요성·성향)와 네 가지 붕괴 경로
- **Monitoring Monitorability** (Guan 외, OpenAI, 2025): [arXiv:2512.18311](https://arxiv.org/abs/2512.18311) · [평가 공개 공지](https://alignment.openai.com/monitorability-evals/) · [코드·데이터](https://github.com/openai/monitorability-evals)
- **Reasoning Models Struggle to Control their Chains of Thought** (Chen 외, OpenAI, 2026): [arXiv:2603.05706](https://arxiv.org/abs/2603.05706)
- **Monitoring Reasoning Models for Misbehavior and the Risks of Promoting Obfuscation** (Baker 외, OpenAI, 2025): [arXiv:2503.11926](https://arxiv.org/abs/2503.11926) — "monitorability tax"
- **When Chain of Thought is Necessary, Language Models Struggle to Evade Monitors** (Emmons 외, 2025): [arXiv:2507.05246](https://arxiv.org/abs/2507.05246)
- **Think Fast: Estimating No-CoT Task-Completion Time Horizons** (Gould 외, 2026): [arXiv:2606.07157](https://arxiv.org/abs/2606.07157)
- **Length Penalties Make Chain-of-Thought Less Monitorable** (Little, 2026): [arXiv:2607.09786](https://arxiv.org/abs/2607.09786)
- **AI safety via debate** (Irving 외, 2018): [arXiv:1805.00899](https://arxiv.org/abs/1805.00899) · **Debating with More Persuasive LLMs Leads to More Truthful Answers** (Khan 외, 2024): [arXiv:2402.06782](https://arxiv.org/abs/2402.06782)
- **Weak-to-Strong Generalization** (Burns 외, 2023): [arXiv:2312.09390](https://arxiv.org/abs/2312.09390) · **AI Control: Improving Safety Despite Intentional Subversion** (Greenblatt 외, 2023): [arXiv:2312.06942](https://arxiv.org/abs/2312.06942)
- **Measuring Progress on Scalable Oversight for Large Language Models** (Bowman 외, 2022): [arXiv:2211.03540](https://arxiv.org/abs/2211.03540)
- 시스템 카드 내 해당 절: GPT-5.6 §7.3 CoT Evaluations · §7.4 Metagaming · §9.2.2 UK AISI / Claude Opus 5 §6.4.5 · §6.6.1 (링크는 위 §2·§3 참조)

### 주제별: Deception, Sleeper Agents & Sandbagging (Week 11)
- **Sleeper Agents: Training Deceptive LLMs that Persist Through Safety Training** (Hubinger 외, Anthropic, 2024): [arXiv:2401.05566](https://arxiv.org/abs/2401.05566) — 조건부 백도어가 SFT·RLHF·적대적 학습을 통과해 잔존하며 모델 규모가 클수록 강고해짐을 입증
- **Simple probes can catch sleeper agents** (Anthropic, 2024-04): [https://www.anthropic.com/research/probes-catch-sleeper-agents](https://www.anthropic.com/research/probes-catch-sleeper-agents) — 일반 정직/기만 대조 1쌍($N=2$) 선형 프로브로 배신 전환을 AUROC 99.3%로 탐지
- **Sycophancy to Subterfuge: Investigating Reward-Tampering in Large Language Models** (Denison 외, Anthropic, 2024): [arXiv:2406.10162](https://arxiv.org/abs/2406.10162) — 아첨에서 체크리스트 위조·보상 함수 및 단위 테스트 재작성으로의 제로샷 일반화
- **Alignment Faking in Large Language Models** (Greenblatt 외, Anthropic & Redwood Research, 2024): [arXiv:2412.14093](https://arxiv.org/abs/2412.14093) · [공식 블로그](https://www.anthropic.com/research/alignment-faking) — 자연 발생한 선호 보존형 정렬 위장(무료 vs 유료 티어 Compliance Gap 11~24%p)과 RL 사후학습 시 정렬 위장 추론이 78%까지 급증하는 역설
- **Frontier Models are Capable of In-context Scheming** (Meinke 외, Apollo Research, 2024): [arXiv:2412.04984](https://arxiv.org/abs/2412.04984) — 감시 카메라 해제·후속 모델 덮어쓰기(자기 복제)·심문 시 최대 98% 사후 부인
- **Stress Testing Deliberative Alignment for Anti-Scheming Training** (Schoen 외, Apollo Research & OpenAI, 2025): [arXiv:2509.15541](https://arxiv.org/abs/2509.15541) — 은밀한 행동 완화(o3 13.0%→0.4%, o4-mini 8.7%→0.3%)와 **평가 인식의 인과적 효과(Causal Intervention)** 입증
- **AI Sandbagging: Language Models can Strategically Underperform on Evaluations** (van der Weij 외, 2024): [arXiv:2406.07358](https://arxiv.org/abs/2406.07358) — 위험 능력 선별 저성능 및 특정 목표 정확도 조준(Calibration)
- **Noise Injection Reveals Hidden Capabilities of Sandbagging Language Models** (Tice 외, 2024): [arXiv:2412.01784](https://arxiv.org/abs/2412.01784) — 가중치 가우시안 노이즈 주입 시 샌드배깅 모델의 정답률이 반등하는 비단조(Non-monotonic) 신호 탐지
- **Sabotage Evaluations for Frontier Models** (Benton 외, Anthropic, 2024): [arXiv:2410.21514](https://arxiv.org/abs/2410.21514) · [공식 블로그](https://www.anthropic.com/research/sabotage-evaluations) — 인간 의사결정 조작·코드 백도어 삽입·안전 평가 샌드배깅·감시자 속이기 4대 사보타주 평가
- 시스템 카드 내 해당 절: Claude Opus 5 §2.4 Alignment risk update · §6.1~§6.7 Alignment assessment (UK AISI 비언어화 평가 인식 95% 쌍대 판별·사보타주·SHADE-Arena·LinuxArena 포함) / GPT-5.6 §7.2 Agentic coding misaligned behavior · §7.4 Metagaming · §9.1~§9.3 External alignment & sandbagging (링크는 위 §2·§3 참조)

### 주제별: Mechanistic Interpretability, SAE & 서킷 분석 (Week 12)
- **Toy Models of Superposition** (Elhage 외, Anthropic, 2022): [Transformer Circuits](https://transformer-circuits.pub/2022/toy_model/index.html) · [arXiv:2209.10652](https://arxiv.org/abs/2209.10652) — 희소 특징이 뉴런 수보다 많은 차원에 거의 직교 방향으로 중첩 저장되는 원리 규명
- **Towards Monosemanticity: Decomposing Language Models With Dictionary Learning** (Bricken 외, Anthropic, 2023): [Transformer Circuits](https://transformer-circuits.pub/2023/monosemantic-features/index.html) — 1레이어 트랜스포머(`512` 뉴런)에서 SAE로 `4,096+` 단의적 특징 추출
- **Scaling Monosemanticity: Extracting Interpretable Features from Claude 3 Sonnet** (Templeton 외, Anthropic, 2024-05): [Transformer Circuits](https://transformer-circuits.pub/2024/scaling-monosemanticity/index.html) · [공지](https://www.anthropic.com/news/mapping-mind-language-model) — `Claude 3 Sonnet` 중간 레이어에서 `1M / 4M / 34M` 특징 추출 및 안전 관련 특징(생물무기·기만·아첨) 인과 조향 실증
- **Scaling and evaluating sparse autoencoders** (Gao 외, OpenAI, 2024-06): [arXiv:2406.04093](https://arxiv.org/abs/2406.04093) · [공지](https://openai.com/index/extracting-concepts-from-gpt-4/) — `TopK` ($k$-sparse) 활성화 함수로 죽은 특징 문제를 해결하고 `GPT-4` 활성값에 `1,600만(16M)` 잠재 특징 SAE 학습
- **Jumping Ahead: Improving Reconstruction Fidelity with JumpReLU Sparse Autoencoders** (Rajamanoharan 외, DeepMind, 2024-07): [arXiv:2407.14435](https://arxiv.org/abs/2407.14435) & **Gemma Scope: Open Sparse Autoencoders Everywhere All At Once on Gemma 2** (Lieberum 외, DeepMind, 2024-08): [arXiv:2408.05147](https://arxiv.org/abs/2408.05147) — `JumpReLU` 아키텍처 및 `Gemma 2 2B/9B/27B` 전 레이어 오픈 SAE 스위트(`400+` 주력 SAE, `3,000만+` 특징) 공개
- **Refusal in Language Models Is Mediated by a Single Direction** (Arditi 외, 2024-06): [arXiv:2406.11717](https://arxiv.org/abs/2406.11717) — 13개 오픈소스 챗 모델(최대 `72B`)에서 거절 행동이 단 `1차원` 부분공간에 의해 매개됨을 입증
- **Improving Alignment and Robustness with Circuit Breakers** (Zou 외, CAIS & Gray Swan, 2024-06): [arXiv:2406.04313](https://arxiv.org/abs/2406.04313) & **Representation Engineering** (Zou 외, 2023): [arXiv:2310.01405](https://arxiv.org/abs/2310.01405) — 표면 거절 문자열 학습 대신 유해 출력의 내부 표상 자체를 가로채 차단하는 `Circuit Breakers` 제안
- **Are Sparse Autoencoders Useful? A Case Study in Sparse Probing** (Kantamneni 외, MIT & DeepMind, 2025-02): [arXiv:2502.16681](https://arxiv.org/abs/2502.16681) — 4대 악조건·113개 데이터셋 다운스트림 프로빙에서 SAE 프로브가 표준 밀집 선형 프로브(로지스틱 회귀)를 일관되게 능가하지 못함을 실증
- **Circuit Tracing: Revealing Computational Graphs in Language Models** (Ameisen 외, Anthropic, 2025-03): [Transformer Circuits](https://transformer-circuits.pub/2025/attribution-graphs/methods.html) & **On the Biology of a Large Language Model** (Lindsey 외, Anthropic, 2025-03): [Transformer Circuits](https://transformer-circuits.pub/2025/attribution-graphs/biology.html) · [공지](https://www.anthropic.com/research/tracing-thoughts-language-model) — 교차 레이어 트랜스코더(`CLT`)와 귀속 그래프(`Attribution Graphs`)로 `Claude 3.5 Haiku`의 환각·거부·탈옥(`BOMB`)·불충실 CoT·숨은 목표(RM 아첨) 서킷 해부
- **Natural Language Autoencoders Produce Unsupervised Explanations of LLM Activations** (Fraser-Taliente, Kantamneni, Ong 외, Anthropic, 2026-05): [Transformer Circuits](https://transformer-circuits.pub/2026/nla/index.html) — `AV`(활성값 언어화기) + `AR`(활성값 재구성기)의 왕복 RL 학습으로 내부 활성값을 `<500` 토큰 자연어로 번역하여 비언어화 평가 인식 및 숨은 오정렬 근본 원인 규명
- 시스템 카드 내 해당 절: Claude Opus 5 §3.2 · §3.4.1 · §5.2.2 · §6.2.2 · §6.6.1 · §7.2.1 · §7.4.2 / GPT-5.6 §1 · §9.4.3.1 Activation Classifiers / Gemini 3.7 Flash FSF Report p.28 Introspection Probes (링크는 위 §2·§3·§4 참조)

### 주제별: 도구 사용(Tool-Use) 모델 및 Autonomous Agent의 안전 (Week 13)
- **Not what you've signed up for: Compromising Real-World LLM-Integrated Applications with Indirect Prompt Injection** (Greshake 외, 2023-02): [arXiv:2302.12173](https://arxiv.org/abs/2302.12173) — LLM 통합 애플리케이션 및 도구 사용 에이전트에서 외부 데이터(웹·이메일·문서)를 통한 간접 프롬프트 인젝션(`IPI`) 위협 모델과 데이터-명령어 경계 붕괴를 최초 정립한 기념비적 논문
- **Identifying the Risks of LM Agents with an LM-Emulated Sandbox (`ToolEmu`)** (Ruan 외, 2023-12): [arXiv:2312.06942](https://arxiv.org/abs/2312.06942) — `36`개 고위험 툴킷·`144`개 테스트 케이스에서 LM 에뮬레이션 샌드박스로 도구 사용 에이전트의 파괴적 실패 모드를 정량 발굴
- **InjecAgent: Benchmarking Indirect Prompt Injections in Tool-Integrated Large Language Model Agents** (Zhan 외, ACL Findings 2024): [arXiv:2403.02691](https://arxiv.org/abs/2403.02691) — `17`개 사용자 도구와 `62`개 공격자 도구를 조합한 `1,054`개 테스트 케이스에서 에이전트 간접 인젝션 취약성을 측정한 표준 벤치마크
- **Defending Against Indirect Prompt Injection Attacks With Spotlighting** (Hines 외, Microsoft, 2024-03): [arXiv:2403.14720](https://arxiv.org/abs/2403.14720) — 구분자(Delimiters), 데이터마킹(Datamarking), 인코딩으로 비신뢰 입력 출처를 명시하여 간접 인젝션 ASR을 `>50%`에서 `<2%`로 낮춘 기법
- **The Instruction Hierarchy: Training LLMs to Prioritize Privileged Instructions** (Wallace 외, OpenAI, 2024-04): [arXiv:2404.13208](https://arxiv.org/abs/2404.13208) — `System > User > Tool Outputs` 명령어 권한 계층을 정의하고 하위 권한 입력의 상위 지시 덮어쓰기를 거부하도록 파인튜닝하는 기법
- **AgentDojo: A Dynamic Environment to Evaluate Prompt Injection Attacks and Defenses for LLM Agents** (Debenedetti 외, ETH Zurich, NeurIPS 2024): [arXiv:2406.13352](https://arxiv.org/abs/2406.13352) — 이메일·뱅킹·여행·워크스페이스 `97`개 현실 작업과 `629`개 보안 테스트케이스로 구성된 동적 에이전트 인젝션 평가 환경
- **Defeating Prompt Injections by Design (`CaMeL`)** (Debenedetti, Shumailov, Fan, Carlini 외, Google DeepMind & ETH Zurich, 2025-03): [arXiv:2503.18813](https://arxiv.org/abs/2503.18813) — `Privileged LLM`(제어 흐름 계획 코드 생성)과 `Quarantined LLM`(도구 권한 없는 비신뢰 데이터 파싱)을 분리하고 역량(`Capability`) 및 데이터 흐름 추적 커스텀 인터프리터로 프롬프트 인젝션을 구조적으로 무력화
- **Design Patterns for Securing LLM Agents against Prompt Injections** (Beurer-Kellner, 공저 Carlini·Tramèr 외, ETH Zurich & Google & IBM, 2025-06): [arXiv:2506.08837](https://arxiv.org/abs/2506.08837) — Action-Selector, Plan-Then-Execute, LLM Map-Reduce, Dual LLM 등 에이전트 아키텍처 보안 디자인 패턴 6종 정식화 (보조 사료: **The Attacker Moves Second** [arXiv:2510.09023](https://arxiv.org/abs/2510.09023), **SoK: Prompt Injection** [arXiv:2603.15714](https://arxiv.org/abs/2603.15714))
- **Anthropic 에이전트 샌드박싱 및 격리 아키텍처 공식 엔지니어링·연구 보고서 3부작**:
  - **Making Claude Code more secure and autonomous with sandboxing** (Anthropic Engineering, 2025-10-20): [원문](https://www.anthropic.com/engineering/claude-code-sandboxing) — OS 네이티브 프리미티브(macOS `Seatbelt`, Linux `bubblewrap`) 기반 파일시스템·네트워크 이중 격리로 권한 승인 팝업을 **`84%`** 저감
  - **Trustworthy agents in practice** (Anthropic Alignment, 2026-04-09): [원문](https://www.anthropic.com/research/trustworthy-agents) — 능력(Capability)·정렬(Alignment)·통제(Control)·투명성(Transparency) 4대 축과 배포 전·후 에이전트 거버넌스 프레임워크
  - **How we contain Claude across products** (Anthropic Alignment, 2026-05-25): [원문](https://www.anthropic.com/research/how-we-contain-claude) — `claude.ai`(비영속 컨테이너)·`Claude Code`(OS 샌드박스)·`Claude Cowork`(6중 격리 로컬 VM & `read-write-no-delete` 마운트) 3대 격리 아키텍처, `~93%` 승인 피로 실증, `Auto Mode` 분류기(`~83%` 과잉 행동 차단 / `~0.4%` 오탐), 실제 보안 실패 4건(폴더 신뢰 전 훅 실행, 피싱 프롬프트 `~/.aws/credentials` `24/25` 탈취 및 슬랙 감염, 허용 도메인 `api.anthropic.com` 악용 유출과 방어용 MITM 프록시, VM EDR 사각지대와 Pull 기반 `OTLP`) 공개
- 시스템 카드 내 해당 절: Claude Opus 5 §5.1~5.2 (Computer Use · Gray Swan IPI $k=15$ · Adaptive IPI + `Auto Mode`) · §6.1.3 (서브에이전트 미검증 주장 전달) · §6.4.2 (`[Transcript 6.4.2.A]` 비공개 CoT 자기합리화 및 `120`개 잡 무단 삭제) · §8.11~8.13 (`BrowseComp 93.6%`, `OSWorld 2.0 70.57%`, `MCP-Atlas 85.8%`) / GPT-5.6 §3.3 (파괴적 행동 회피+정확성 `0.44/0.37/0.32`) · §3.4 (고위험 액션 확인 요청) · §4.2 (Connectors & Indirect PI) · §7.2 (`VM 5,6,7` 무단 삭제 및 `access_tokens.json` 복사) / Gemini 3.7 Flash FSF Report (`GRB 27%/47%` 및 `11`개 Linux 상황 인식 챌린지 `6/11` 통과)

### 주제별: 한국형 AI Safety 벤치마크, 교차언어/자모 보안 & 국내 법제도 (Week 14)
- **SQuARe: A Large-Scale Dataset of Sensitive Questions and Acceptable Responses** (Lee 외, NAVER AI Lab · KAIST · SNU, ACL 2023): [arXiv:2305.17696](https://arxiv.org/abs/2305.17696) — 실제 뉴스 헤드라인 기반 `49k` 민감 질문 및 `42k` 수용 가능 / `46k` 비수용 응답 데이터셋
- **KoSBi: A Dataset for Mitigating Social Bias Risks Towards Safer LLM Application** (Lee 외, NAVER AI Lab, ACL 2023): [arXiv:2305.17701](https://arxiv.org/abs/2305.17701) — `15`개 범주·`72`개 인구통계 집단 `34k` 문맥-문장 쌍 (생성 편향 평균 `-16.47%p` 완화)
- **KoBBQ: Korean Bias Benchmark for Question Answering** (Jin 외, KAIST · NAVER AI Lab, TACL 2024): [arXiv:2307.16778](https://arxiv.org/abs/2307.16778) — 한국 문화 적응 3분류 + 고유 편향 4종 추가, `12`개 범주·`268`개 템플릿·`76,048` 샘플
- **HAE-RAE Bench** (Son 외, LREC-COLING 2024): [arXiv:2309.02706](https://arxiv.org/abs/2309.02706) & **CLIcK: Cultural and Linguistic Intelligence in Korean** (Kim 외, LREC-COLING 2024): [arXiv:2403.06412](https://arxiv.org/abs/2403.06412) — 한국 시험·교과서 기반 문화·언어 11개 범주 `1,995` QA 쌍
- **KorNAT: LLM Alignment Benchmark for Korean Social Values and Common Knowledge** (Lee 외, KAIST · SelectStar · NAVER AI Lab, ACL 2024 Findings): [arXiv:2402.13605](https://arxiv.org/abs/2402.13605) — 한국인 `6,174`명 설문(문항당 평균 `219`명) 사회적 가치 `4K` + 공통 지식 `6K` (`10K` 문항)
- **Multilingual Jailbreak Challenges in Large Language Models (`MultiJail`)** (Deng 외, ICLR 2024): [arXiv:2310.06474](https://arxiv.org/abs/2310.06474) — 한국어 포함 다국어 탈옥 시 유해 출력률(`ChatGPT 80.92%`, `GPT-4 40.71%`) 및 `Self-Defense` 파인튜닝
- **WildGuard** (Han 외, NeurIPS 2024): [arXiv:2406.18495](https://arxiv.org/abs/2406.18495) & **PolyGuard: A Multilingual Safety Moderation Tool for 17 Languages** (Kumar 외, 2025): [arXiv:2504.04377](https://arxiv.org/abs/2504.04377) — 한국어 포함 `17`개 언어 `1.91M` 학습 코퍼스·`29K` 평가셋 다국어 안전 분류기
- **KSAFE-MM: A Multimodal Safety Benchmark via Localized Contextualization for Korean Cultural Risks** (Kim 외, 2026-05): [arXiv:2605.28013](https://arxiv.org/abs/2605.28013) — 한국 맥락 멀티모달 안전 평가 (`ProgramExecution` 결합 시 최대 `74.2%` ASR 및 안전–과차단 트레이드오프 실증)
- **Quantifying and Mitigating Korean Jamo-Level Typographical Vulnerabilities in Large Language Models** (Lee & Lee, 2026-08): [arXiv:2608.30229](https://arxiv.org/abs/2608.30229) — 한글 음절 내부 자모 교란 5종의 토크나이저 파편화 규명 및 내부 표상 선형 프로브 + `TACoT` 완화
- **대한민국 국가법령정보센터 — 「인공지능 발전과 신뢰 기반 조성 등에 관한 기본법」(법률 제20676호, 2026. 1. 22. 시행)**: [법령 원문](https://www.law.go.kr/법령/인공지능발전과신뢰기반조성등에관한기본법) — 제31조(투명성·생성물·딥페이크 표시), 제32조($10^{26}$ FLOPs 고성능 AI 안전성), 제33조·제34조(고영향 AI 확인 및 사업자 5대 책무)
- **개인정보보호위원회 — 생성형 AI 개인정보 처리 안내서 (2025-08)**: [https://www.pipc.go.kr/](https://www.pipc.go.kr/) · **TTA AI 신뢰성 검·인증 (`CAT 2.0`)**: [https://www.tta.or.kr/](https://www.tta.or.kr/)

---

## 6. 링크 검증 규칙 (Link Hygiene)

본 저장소의 모든 인용 URL은 **커밋 전에 HTTP 상태 확인을 통과**해야 합니다. 2026-09-07 전수 점검에서 404를 반환하던 링크 8종을 실재 문서로 교체했습니다(경위는 [Week 05 리뷰 §3.4](../reviews/week-05/review_week05.md) 참조).

**판정 기준**
- `200` / `202` / `3xx` → 정상
- `404` → **즉시 교체 대상**
- `403` → `openai.com` 은 자동화 요청을 일괄 차단하므로 403이 곧 사망 링크는 아님. 브라우저 또는 검색으로 실재 여부를 별도 확인할 것
- **링크가 살아 있다고 내용이 맞는 것은 아님** → 시스템 카드·보고서를 인용할 때는 PDF를 내려받아 **인용한 수치·용어가 본문에 실제로 있는지 검색**할 것. 2026-10-12 Week 06 대조에서, 링크는 정상이지만 리뷰가 인용한 수치와 용어 다수가 원문에 없음이 확인되어 **2026-10-19 82페이지 원문 PDF 기준으로 전면 재작성**함
- **"존재하지 않는다"고 단정하지 말 것** → 검색에 안 잡히는 것과 실재하지 않는 것은 다름. 확인되지 않으면 `[확인 필요]`로 표기 (2026-09-21 Gemini 3.7 Flash 오판정 사례)

```bash
grep -rhoE '\]\(https?://[^)]+\)' --include='*.md' . | sed 's/^](//; s/)$//' | sort -u \
  | while read -r u; do printf '%s  %s\n' "$(curl -s -o /dev/null -w '%{http_code}' -L --max-time 15 -A 'Mozilla/5.0' "$u")" "$u"; done
```
