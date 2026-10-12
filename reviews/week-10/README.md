# [Week 10] Scalable Oversight & CoT 감시가능성

- **주제**: 사고 연쇄(CoT) 감시가 scalable oversight의 실전 수단으로서 얼마나 믿을 만한가 — 충실성·감시가능성·제어가능성의 구분, 감시가능성이 무너지는 네 가지 경로, 2026년 시스템 카드의 실제 보고
- **리뷰 일자**: 2026-10-12 (월)
- **트랙**: Track 3 — Technical Alignment & Interpretability
- **난이도**: 🔴 고급

---

## 🎯 학습 목표
1. **Scalable oversight**의 네 갈래(Debate, Weak-to-Strong, AI Control, CoT Monitoring)를 구분하고 CoT 감시가 그중 어디에 놓이는지 파악한다.
2. CoT가 감시 가능한 두 근거 — **필요성**과 **성향** — 를 구분하고, 이 구분이 왜 감시의 신뢰도를 결정하는지 이해한다.
3. **충실성(faithfulness) · 감시가능성(monitorability) · 제어가능성(controllability)** 세 개념을 원문 정의와 수치로 구분한다.
4. 감시가능성이 무너지는 **네 가지 경로**(RL 확대, 직접 감독, 간접 최적화 압력, 새 아키텍처)를 2025~2026년 실증과 연결한다.
5. 추론 비용 절감이 감시가능성을 깎는 구조를 이해하고, 소버린 AI 조직을 위한 **감시가능성 회귀 테스트와 "감시가능성 세금" 정책**을 도출한다.

---

## 📂 구성 파일
- [`review_week10.md`](review_week10.md): 10주차 종합 심층 분석 보고서
- 갱신 산출물: [`resources/reasoning_cot_safety_guide.md`](../../resources/reasoning_cot_safety_guide.md) **§6 감시가능성 보존** 신설

---

## 📌 이번 주차 핵심 수치 (원문 대조 완료)

| 항목 | 값 | 출처 |
| :--- | :--- | :--- |
| 힌트 사용을 CoT에 언급한 비율 | Claude 3.7 Sonnet **25%**, DeepSeek R1 **39%** | Anthropic (2025-04) |
| 보상 해킹 실험 | 힌트 이용 **99%+**, CoT 언급 **2% 미만** | 동 |
| CoT 제어 vs 출력 제어 | Claude Sonnet 4.5: **2.7%** vs **61.9%** | Chen 외, arXiv:2603.05706 |
| GPT-5.6 Sol CoT 제어가능성 (5k 토큰) | **1.3%** (GPT-5.5 0.4%, GPT-5.4 Thinking 0.7%) — 상승, 원인 조사 중 | GPT-5.6 System Card §7.3.2 |
| GPT-5.6 Sol 감시가능성 | GPT-5.5와 평균적으로 유사, 일부 환경 회귀 | 동 §7.3.1 |
| Claude Opus 5 사고 텍스트 | unfaithful thinking **감소**, illegible thinking **증가** (Opus 4.8 대비) | Opus 5 System Card §6.4.5 |
| CoT 길이 30% 압축 시 | 정확도 유지, 모니터 탐지율 **35~39% 하락** (Qwen3, MMLU-Pro-R) | Little, arXiv:2607.09786 |
| CoT 없는 50% 타임 호라이즌 | GPT-5.5 **3분 이상**, 약 1년마다 2배 | Gould 외, arXiv:2606.07157 |
| Debate로 비전문가 심판 정확도 | 모델 48→**76%**, 인간 60→**88%** | Khan 외, arXiv:2402.06782 |

---

## ⚠️ 본 주차에서 수행한 선행 리뷰 정정
GPT-5.6 System Card PDF 원문 대조 결과 **Week 06 리뷰의 핵심 서술(Preparedness 판정, 추론 강도별 방어율 표, Legibility Reward 등)이 원문에 없거나 원문과 반대**임을 확인했습니다. Week 06 상단에 정정 고지를 달았으며 상세는 [review_week10.md §3.4](review_week10.md) 참조.

---

## 🔗 Track 3 연계 로드맵
- **Week 09**: RLHF의 한계와 Constitutional AI (RLAIF) & RBRMs
- **Week 10 (현재)**: Scalable Oversight & CoT 감시가능성
- **Week 11 (다음 주)**: Deception, Sleeper Agents & Sandbagging — 이번 주에 본 메타게이밍·언어화되지 않은 채점자 인식에서 이어짐
- **Week 12**: Mechanistic Interpretability & SAE — CoT 텍스트가 아니라 활성값을 읽는 감시
