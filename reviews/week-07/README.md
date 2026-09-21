# [Week 07] Gemini 3.7 Flash Frontier Safety Report & FSF 3.1

- **주제**: Google DeepMind Gemini 3.7 Flash의 Frontier Safety Framework 판정서 심층 분석 및 FSF v3.1의 3단 임계치 구조·평가 무결성 문제
- **리뷰 일자**: 2026-09-21 (월)
- **트랙**: Track 2 — System Cards & Frontier Evals (Track 2 마무리)
- **난이도**: 🟡 중급

---

## 🎯 학습 목표
1. **TCL → 경보 임계치(Alert Threshold) → CCL** 의 3단 임계치 구조와, 그 사이를 메우는 **안전 버퍼(safety buffer)** 논리를 이해한다.
2. 프레임워크 문서가 아니라 **실제 판정서**를 읽고, 도메인별 판정이 어떤 근거와 어떤 유보 조건으로 내려지는지 확인한다.
3. **이끌어내기(Elicitation)** 규율 — 기본 행동이 아니라 절대적 잠재력을 측정하기 위한 스캐폴딩·샌드배깅 점검 절차를 파악한다.
4. **평가 인식(Evaluation Awareness)** 이 정렬 평가를 오염시킨 실제 사례를 분석하고, 능력·성향·버그를 구분하는 평가 무결성 절차를 도출한다.
5. **평가 깊이 등급화**(전면 / 경량 / 상속)를 통해 제한된 예산으로 위험 평가 체계를 운영하는 방법을 정리한다.

---

## 📂 구성 파일
- [`review_week07.md`](review_week07.md): 7주차 종합 심층 분석 보고서
- 신규 산출물: [`resources/frontier_eval_playbook.md`](../../resources/frontier_eval_playbook.md) — 소버린 AI를 위한 프론티어 위험 평가 설계 플레이북

---

## 📌 이번 주차 핵심 수치 (원문 대조 완료)

| 항목 | 값 | 출처 |
| :--- | :--- | :--- |
| Gemini 3.7 Flash 최종 판정 | **모든 T/CCL 미도달** → 배포 수용 가능 | FSF Report §2 |
| 경보 임계치 도달 도메인 | **CBRN, Cybersecurity** (2개 도메인) | 동 §CBRN·§Cyber |
| FSF 버전 이력 | v1(2024-05) → v2(2025-02) → v3(2025-09) → **v3.1(2026-04-17)** | FSF v3.1 |
| 위험 도메인 | CBRN · Cyber · Harmful Manipulation · ML R&D and Misalignment | FSF v3.1 §1.2 |
| 조작 능력 인간 실험 | **참가자 1,596명** (시민 805 / 금융 791), 외부 학계 윤리위(HuBREC) 승인 | FSF Report §Harmful Manipulation |
| Stealth / 상황 인식 | **3/4** (1건은 평가 인식으로 무효) / **6/11** | 동 §ML R&D and Misalignment |
| 외부 레드팀 | Gray Swan `Shade` — 사이버 **28개 과업**, 바이오 **53개 과업** | 동 §Robustness |
| 권고 보안 등급 | CBRN·Cyber·조작 = SL 2+ / ML R&D 가속 = SL 3 / ML R&D 자동화 = SL 4 (RAND 기준 정렬) | FSF v3.1 §2·§3 |

---

## ⚠️ 본 주차에서 수행한 선행 리뷰 정정
Week 04 리뷰의 FSF 서술 중 원문과 어긋나는 5개 항목(EWT 명칭, 연산량 배수 수식, 위험 범주 구성, 보안 등급 체계, 거버넌스 기구명)을 v3.1 원문 대조로 정정했습니다. 상세는 [review_week07.md §3.3](review_week07.md) 참조.
