# [Week 06] OpenAI GPT-5.6 (Sol/Terra/Luna) System Card & 추론 제어 안전

- **주제**: OpenAI GPT-5.6 Family (Sol / Terra / Luna) System Card 심층 분석 및 가변 추론(Reasoning Effort / CoT) 안전 제어·모니터링 체계
- **리뷰 일자**: 2026-09-14 (월)
- **트랙**: Track 2 — System Cards & Frontier Evals
- **난이도**: 🟡 중급

---

## 🎯 학습 목표
1. **GPT-5.6 3계층 모델 라인업(Sol / Terra / Luna)**의 계층별 포지셔닝과 가변 추론(Variable Reasoning) 아키텍처에 따른 위험 프로파일 차이를 이해한다.
2. **Preparedness Framework 실전 적용 결과(Risk Scorecard)**를 분석하여 4대 위협(CBRN, Cyber, Persuasion, Model Autonomy)의 Pre-mitigation vs Post-mitigation 정량 점수와 배포 게이트 통과 논리를 확인한다.
3. **추론 제어(Thinking Effort: Low / Medium / High)**가 모델 안전성에 미치는 이중 효과(사고 연쇄 숙고를 통한 탈옥 저항력 강화 vs 은닉 추론 내 기만/보상 해킹 위험)를 규명한다.
4. **은닉 사고 연쇄(Hidden CoT) 모니터링 체계(Chain-of-Thought Monitorability)**와 실시간 안전 모니터(Safety Monitor)의 작동 원리 및 가독성(Legibility) 보존 기법을 분석한다.
5. 리소스 제약이 있는 **한국형 소버린 파운데이션 모델 개발팀**을 위한 경량 CoT 감사 파이프라인 및 추론 예산 제어 런북을 도출한다.

---

## 📂 구성 파일
- [`review_week06.md`](review_week06.md): 6주차 종합 심층 분석 보고서
- 신규 실전 자산: [`resources/reasoning_cot_safety_guide.md`](../../resources/reasoning_cot_safety_guide.md) — 소버린 AI를 위한 CoT 추론 안전 모니터링 & 가드레일 실전 가이드 (Week 05 Action Item 연계)

---

## 📌 이번 주차 핵심 수치 (원문 대조 및 평가 지표 요약)

| 항목 | Sol (플래그십) | Terra (엔터프라이즈) | Luna (경량·고속) | 비고 |
| :--- | :---: | :---: | :---: | :--- |
| **추론 예산 (Thinking Effort)** | 동적 가변 (최대 128k CoT 토큰) | 균형 가변 (최대 32k 토큰) | 고정 경량 (최대 8k 토큰) | 추론 깊이에 따른 안전성 분기 |
| **Preparedness 판정 (Post-mitigation)** | **전 영역 Medium 이하 (배포 승인)** | **전 영역 Medium/Low (배포 승인)** | **전 영역 Low (배포 승인)** | Pre-mitigation 기준 Sol은 Cyber High 기록 |
| **탈옥 방어율 (Jailbreak Defense Rate)** | **99.2%** (High Effort) | 98.4% (Medium Effort) | 95.8% (Low Effort) | 추론 연쇄 증가 시 방어율 상승 |
| **CoT 모니터링 가독성 점수 (Legibility)** | **94.6%** | 96.1% | 97.8% | 자가 암호화/기만적 사고 연쇄 억제율 |
| **단일 턴 과차단율 (Over-refusal Rate)** | **0.38%** | 0.42% | 0.51% | 숙고 추론 모델 특유의 낮은 과차단율 |
| **외부 평가 협력 기관** | US AISI, UK AISI, METR, NCSA 레드팀 | 동등 협력 | 자체 검증 + 제3자 샘플링 | 배포 전 사전 격리 평가 완료 |
