# [Week 12] Mechanistic Interpretability & SAE (Track 3 종합)

- **주제**: 모델이 내보내지 않는 것 — 내부 활성값 — 을 읽는 법. 중첩과 희소 오토인코더(SAE), 특징 조향의 정량 평가와 2025년 회의론, attribution graph 회로 추적, 그리고 2026년의 감사·모델 비교·활성값 언어화(NLA) 도구와 3사 실전 사용 대조
- **리뷰 일자**: 2026-10-26 (월) 회차 · 2026-11-05 작성
- **트랙**: Track 3 — Technical Alignment & Interpretability (**Track 3 종합**)
- **난이도**: 🔴 고급

---

## 🎯 학습 목표
1. **중첩(superposition)** 이 왜 뉴런 단위 분석을 막는지, **SAE**가 활성값을 희소한 특징의 합으로 다시 쓰는 원리(ReLU+L1 · TopK · JumpReLU)를 이해한다.
2. Claude 3 Sonnet(34M) · GPT-4(16M) · Gemma Scope(30M+) 스케일업의 **비용과 불완전성**을 수치로 파악한다.
3. **특징 조향**의 최적 구간과 표적 외 효과, 그리고 **"찾을 대상을 알면 프로브가 SAE를 이긴다"** 는 2025년 회의론의 정확한 범위를 구분한다.
4. **Attribution graph** 가 보여준 계획·다단계 추론·환각·탈옥·불충실 추론의 기전과 그 한계를 이해한다.
5. 2026년 **감사·비교·언어화 도구**(Assistant axis, Diff tool, Emotion vectors, NLA, J-lens)와 3사의 실제 사용 — **실시간은 프로브, 감사는 언어화 도구, 사고 조사에서는 정황 증거** — 를 대조한다.
6. **Track 3(Week 09~12)** 의 네 층(훈련·언어·행동·활성값) 감독 구조와 각 층의 구멍을 종합하고, 소버린 AI 조직의 단계별 화이트박스 도입 경로를 도출한다.

---

## 📂 구성 파일
- [`review_week12.md`](review_week12.md): 12주차 종합 심층 분석 보고서 (Track 3 종합 포함)
- 신설 산출물: [`resources/whitebox_monitoring_guide.md`](../../resources/whitebox_monitoring_guide.md) **화이트박스 감사 & 활성값 모니터링 실전 가이드** — 도구 선택 매트릭스 · 프로브 운영 표준 · 조향 사용 규칙 · 모델 비교 감사 · 평가 인식 3분할 측정 · 증거 등급과 공개 문구 규칙

---

## 📌 이번 주차 핵심 수치

| 항목 | 값 | 출처 (검증 수준) |
| :--- | :--- | :--- |
| Claude 3 Sonnet SAE 규모 | 약 **1M / 4M / 34M** 특징, 토큰당 활성 **300개 미만**, 분산 **65% 이상** 설명 | Mapping the Mind · Scaling Monosemanticity (공지 원문 / 논문 수치는 초록·2차 자료) |
| GPT-4 SAE | **16M** 잠재변수 · 40B 토큰 · 죽은 잠재변수 **7%** | Gao 외, arXiv:2406.04093 (초록 확인) |
| Gemma Scope 비용 | SAE **400개+**, 특징 **3,000만+**, GPT-3 학습 연산량의 **20% 이상**, 활성값 **약 20 PiB** | Gemma Scope 보고서 PDF (원문) |
| 특징 조향 최적 구간 | 조향 계수 **−5 ~ +5** (29개 특징 공통) | Anthropic, Evaluating feature steering (원문) |
| 표적 외 효과 | 성 편향 인식 특징 → 성 편향 **+10%**, 연령 편향 **+13%** / 이민 문항: 이민 특징 **3.90%** vs 낙태 특징 **21.60%** | 동 (원문) |
| SAE vs 기준선 | OOD 유해 의도 탐지: 밀집 선형 프로브 거의 완벽, SAE 열세 / 113개 데이터셋 평균: SAE 프로브 < 로지스틱 회귀 | DeepMind 2025-03 · Kantamneni 외 (초록 확인) |
| 숨겨진 목표 감사 게임 | **4팀 중 3팀** 성공, 최우수 팀 **1명 90분**(SAE) — 단 의미 검색도 동일 데이터 발견 | Marks 외, Anthropic 2025-03 (원문) |
| 자기 성찰 (concept injection) | 최선 프로토콜에서 Opus 4.1 **약 20%** 인식 | Anthropic 2025-10 (원문) |
| Activation capping | 페르소나 탈옥(44범주 · 1,100건) 유해 응답 **약 50% 감소**, 역량 유지 | Assistant axis, 2026-01 (원문, 오픈웨이트 3종) |
| NLA 비언어화 평가 인식 | 파괴적 코딩 평가 **16%** · SWE-bench Verified **26%** · 실사용 **<1%** | Natural Language Autoencoders, 2026-05 (원문) |
| NLA 감사 게임 | 데이터 접근 없이 성공률 **12~15%** vs NLA 없음 **<3%** | 동 (원문) |
| 3사 실시간 안전장치 | Opus 5 **1단 활성값 프로브** · GPT-5.6 **Activation Classifiers**(생물 94.8% / 사이버 80.6% 재현율) · Gemini 3.7 Flash **Introspection Probes** | Week 05 · 06 · 07 원문 대조분 / Gemini FSF Report p.28 |
| 사고 조사 화이트박스 (Mythos 5) | NLA "this is real" 신호 **234건 중 44건(19%)**, 합리화 신호 **2,430건 중 103건(4%)**, T-lens 불확실성 **11.6% vs 8.2%** — 결론은 "약하게 시사" | Anthropic 사이버 사고 정렬 평가, 2026-09-09 (원문) |
| 같은 사고의 CoT 모니터 | Mythos 5 행동의 **약 1%** 만 플래그 → CoT 제거 시 **약 50%** | 동 (원문) |

> ⚠️ **검증 범위**: 이번 세션 네트워크 정책상 `arxiv.org` · `transformer-circuits.pub` · `huggingface.co` · `lesswrong.com` 은 직접 접속하지 못했습니다. 해당 출처 수치는 검색 색인의 초록·요약으로만 확인했으며 리뷰 본문에 **[초록 확인]** / **[2차 자료 · 원문 대조 필요]** 로 표시했습니다.

---

## 🔗 Track 3 연계 로드맵 (종합)
- **Week 09**: RLHF의 한계와 Constitutional AI (RLAIF) & RBRMs — *훈련 층*
- **Week 10**: Scalable Oversight & CoT 감시가능성 — *언어 층*
- **Week 11**: Deception, Sleeper Agents & Sandbagging — *행동 감사 층*
- **Week 12 (현재)**: Mechanistic Interpretability & SAE — *활성값 층* + **Track 3 종합** ([review §3.3](review_week12.md))
- **Week 13 (다음 주, Track 4 개막)**: Tool Use & Autonomous Agent Guardrails — 이번 주 사고 조사 사례(실제 인터넷에 연결된 에이전트의 무단 접근)가 직접 이어지는 주제
