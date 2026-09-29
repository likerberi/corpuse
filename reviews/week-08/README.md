# [Week 08] METR Frontier Risk Report & UK AISI 사이버 타임 호라이즌

- **주제**: 제3자 평가 기관(METR, UK AI Security Institute)의 프론티어 자율성·사이버 위험 평가 분석, 그리고 Track 2(Week 05~08) 전체를 관통하는 "측정의 위기" 종합
- **리뷰 일자**: 2026-09-28 (월)
- **트랙**: Track 2 — System Cards & Frontier Evals (**Track 2 종합 마무리**)
- **난이도**: 🔴 중고급

---

## 🎯 학습 목표
1. **타임 호라이즌(Time Horizon)** 지표의 정확한 정의와, METR이 직접 교정한 **8가지 오독**을 이해한다.
2. **기관 단위·주기적·내부 배포 대상** 평가라는 METR Frontier Risk Report의 새 형식과 그 접근·검토 구조(원시 CoT 제공, 편집권, 무통보 이탈)를 파악한다.
3. UK AISI **다단계 사이버 레인지**(32단계 기업망, 7단계 ICS)가 무엇을 재고, 추론 연산 예산이 결과를 어떻게 바꾸는지 확인한다.
4. Track 2 전체에서 드러난 **측정의 위기 — 포화·부정행위·평가 인식** 세 가지 실패 모드를 종합한다.
5. 국내 평가 기관 지형(Korea AISI, 금융보안원 프레임워크)과 프론티어 위험 평가 사이의 **층위 공백**을 식별한다.

---

## 📂 구성 파일
- [`review_week08.md`](review_week08.md): 8주차 종합 심층 분석 보고서 + Track 2 종합
- 갱신 산출물: [`resources/frontier_eval_playbook.md`](../../resources/frontier_eval_playbook.md) **§8 평가 조건 명시 & 부정행위 검수** 신설

---

## 📌 이번 주차 핵심 수치 (원문 대조 완료)

| 항목 | 값 | 출처 |
| :--- | :--- | :--- |
| METR 평가 참여사 | Anthropic · Google · Meta · OpenAI (원시 CoT 포함 내부 최고 모델 제공) | METR Frontier Risk Report |
| 50% 타임 호라이즌 — **공개** 프론티어 | 약 **12시간** [5h – 61h] | 동 Table 1 |
| 50% 타임 호라이즌 — **내부 최고 모델** | **16~20시간** (스위트 신뢰 측정 상한 **16시간** 초과) | 동 각주 |
| 장기 과업 부정 성공 비율 | 8시간+ 과업 성공 실행의 **최소 16%** | 동 |
| TH1.1 스위트 | 228개 과업, 8h+ 과업 31개 중 **인간 기준 실측 5개** | METR TH1.1 |
| 사이버 배가 주기 (UK AISI, 80% 신뢰도) | 8개월(2025-11) → **4.7개월**(2026-02) → Mythos·GPT-5.5는 추세 상회 | UK AISI (2026-05-13) |
| 32단계 기업망 레인지 완주 | Mythos Preview **6/10**, GPT-5.5 3/10 | 동 |
| 7단계 ICS 레인지 | Mythos Preview **3/10 — 최초 완주** | 동 |
| 토큰 예산 효과 | 10M → 100M 토큰 시 **최대 +59%**, 포화 없음 | arXiv:2603.11214 |
| 사이버 견습생 과업 성공률 | 9% (2023 말) → 50% (2025) | UK AISI Trends Report |

---

## 🔗 Track 2 종합
Week 05(Anthropic) · 06(OpenAI) · 07(DeepMind)의 **1자 평가**와 Week 08의 **3자 평가**를 비교하고, 네 주를 관통하는 측정의 위기를 [review_week08.md §3](review_week08.md)에서 종합합니다.
