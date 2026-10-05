# [Week 09] RLHF의 한계와 Constitutional AI (RLAIF) 진화 — Track 3 시작

- **주제**: 인간 피드백 기반 강화학습(RLHF)의 구조적 한계(보상 해킹, Sycophancy, 비용 병목) 분석, Anthropic의 Constitutional AI(RLAIF) 메커니즘, OpenAI의 Rule-Based Reward Models(RBRMs), 그리고 한국형 소버린 AI 헌법 설계
- **리뷰 일자**: 2026-10-05 (월)
- **트랙**: Track 3 — Technical Alignment & Interpretability (**Track 3 개막**)
- **난이도**: 🟡 중급

---

## 🎯 학습 목표
1. **RLHF의 4대 한계**(확장성 병목, 아첨/Sycophancy, 보상 해킹/Goodhart's Law, 라벨러 트라우마 및 비일관성)를 기술적·비용적 관점에서 규명한다.
2. Anthropic **Constitutional AI (CAI)**의 2단계 파이프라인(Critique-Revision SFT 및 AI Feedback 기반 RL)의 수식적/알고리즘적 메커니즘을 완전 분해한다.
3. OpenAI가 GPT-4o / GPT-5 시리즈 정렬에 도입한 **Rule-Based Reward Models (RBRMs)**의 역할과 뉴럴 보상 모델과의 하이브리드 결합 방식을 파악한다.
4. 2026년 최신 추론 모델(Thinking Models)에서의 **Constitutional CoT** 및 과도한 거부(Over-refusal) 완화 기법을 학습한다.
5. 빅테크 수준의 수십억 원대 인간 라벨링 예산이 없는 한국 소버린 AI 조직을 위한 **비용 효율적 RLAIF 레시피**와 **'한국형 AI 헌법(Korean AI Constitution v1.0)'**을 도출한다.

---

## 📂 구성 파일
- [`review_week09.md`](review_week09.md): 9주차 종합 심층 분석 보고서 (Track 3 개막)
- 신규 실전 가이드: [`resources/korean_ai_constitution_guide.md`](../../resources/korean_ai_constitution_guide.md) — 한국형 인공지능 헌법 20조항 및 RLAIF 자동화 파이프라인 실전 템플릿

---

## 📌 이번 주차 핵심 개념 및 지표 비교

| 비교 항목 | 전통적 RLHF (인간 피드백) | Constitutional AI (RLAIF) | Rule-Based Rewards (RBRMs) |
| :--- | :--- | :--- | :--- |
| **피드백 주체** | 크라우드소싱 인간 라벨러 | 자연어 헌법을 참조하는 AI 모델 | 프로그래밍된 명시적 규칙·루브릭 |
| **비용 & 확장성** | 매우 높음 (시간·비용 선형 증가) | 극히 낮음 (추론 토큰 비용만 소요) | 최소 (규칙 작성 후 연산 비용 미미) |
| **피드백 일관성** | 낮음 (라벨러 간 편차, 주관성) | 높음 (동일 헌법/프롬프트 적용) | 결정론적 (100% 일관성) |
| **투명성 & 해석성** | 블랙박스 (인간 선호 점수화) | 높음 (명시적 비판/수정 텍스트 존재) | 극히 높음 (위반 규칙 직접 확인 가능) |
| **주요 부작용** | 아첨(Sycophancy), 보상 해킹 | 모델 자체의 기만, 헌법 충돌 | 규칙 밖 예외 상황 대처 취약 |
| **주요 적용사례** | InstructGPT, 초기 Claude/Llama 2 | Claude 2~5, Gemini RLAIF 파이프라인 | OpenAI GPT-4o / GPT-5.5 / GPT-5.6 |

---

## 🔗 Track 3 연계 로드맵
- **Week 09 (현재)**: RLHF의 한계와 Constitutional AI (RLAIF) & RBRMs
- **Week 10 (다음주)**: Scalable Oversight & Reasoning Chain 얼라인먼트 (Thinking CoT 감시)
- **Week 11**: Deception, Sleeper Agents & Sandbagging (잠재적 기만 분석)
- **Week 12**: Mechanistic Interpretability & 희소 오토인코더(SAE)를 통한 내부 특징 제어
