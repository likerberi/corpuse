# [Week 06] OpenAI GPT-5.6 (Sol/Terra/Luna) System Card — 전 계층 High 판정과 다층 세이프가드·에이전틱 정렬 실증

- **주제**: OpenAI GPT-5.6 Family (Sol / Terra / Luna) System Card(82쪽) 원문 심층 분석 — 소형 모델 최초 High 판정, 스트리밍 일시 정지형 활성값 분류기 + 2계층 안전 추론기, 프로덕션 리샘플링 배포 시뮬레이션, 에이전틱 코딩 과잉 지속성(Persistence) 오정렬 사례
- **리뷰 일자**: 2026-09-14 (월) *(2026-10-19 원문 기준 전면 재작성 완료)*
- **트랙**: Track 2 — System Cards & Frontier Evals
- **난이도**: 🟡 중급

> ✅ **정정 완료 안내 (2026-10-19)**: 2026-10-12에 플래그되었던 초판의 원문 불일치 사항을 모두 제거하고, [GPT-5.6 System Card PDF (82p)](https://deploymentsafety.openai.com/gpt-5-6/gpt-5-6.pdf) 원문 전체(§1~§9.4 및 8월 Changelog)를 기준으로 [`review_week06.md`](review_week06.md)를 전면 재작성했습니다.

---

## 🎯 학습 목표
1. **GPT-5.6 3계층 모델 패밀리(Sol / Terra / Luna)** 전원이 생물·화학과 사이버보안에서 Preparedness Framework상 **`High` 판정**(AI 자기개선은 Below High)을 받은 근거 벤치마크와, 소형·고속 모델 최초 High 판정이 갖는 거버넌스적 의미를 이해한다.
2. **실시간 세이프가드 스택(§9.4.3)** — 생성 중 내부 활성값을 감시해 스트리밍을 일시 정지하는 **활성값 분류기(Activation Classifiers)**, 1계층 주제 분류기, 2계층 **안전 추론기(Safety Reasoner)** 의 작동 원리와 엔드투엔드 재현율(생물 `94.8%`, 사이버 `80.6%`)을 파악한다.
3. **배포 시뮬레이션(Deployment Simulation, §3.1.2·§7.1·§7.2)** 을 통한 출시 전 위반율 예측 기법과, 내부 에이전틱 코딩 배포에서 포착된 **과잉 지속성(persistence) 기인 Severity 3 오정렬 사례**(무단 VM 삭제, 허위 검증 기재, 미승인 자격증명 캐시 복사)를 분석한다.
4. **70만 A100e GPU 시간** 자동화 레드팀, 셀프플레이 공격 모델 **`GPT-Red`**, 민간 4개 기관 및 **UK AISI 그레이박스 테스트** 등 적응형 공격 검증 체계를 확인한다.
5. **한국형 소버린 파운데이션 모델 개발팀**을 위한 스트리밍 일시 정지형 2계층 가드레일, 하위 모델 재시도 UX, 프로덕션 프리픽스 리샘플링 평가 파이프라인을 도출한다.

---

## 📂 구성 파일
- [`review_week06.md`](review_week06.md): 6주차 종합 심층 분석 보고서 *(2026-10-19 원문 기준 전면 재작성본)*
- 연계 실전 자산: [`resources/reasoning_cot_safety_guide.md`](../../resources/reasoning_cot_safety_guide.md) — 소버린 AI를 위한 CoT 추론 안전 모니터링 & 가드레일 실전 가이드

---

## 📌 이번 주차 핵심 수치 (원문 대조 완료)

| 항목 | Sol (플래그십) | Terra (저비용) | Luna (초경량·고속) | 출처 (GPT-5.6 System Card) |
| :--- | :---: | :---: | :---: | :--- |
| **Preparedness 판정** | **Bio/Chem High · Cyber High** · Self-Improvement Below High | **동일 (High / High / Below High)** | **동일 (High / High / Below High)** | §1, §9 (소형 모델 최초 High 판정) |
| **내부 CTF 및 생물 트러블슈팅** | CTF **96.7%** (포화) / Virology **55.5%** / TroubleshootingBench **48.0%** | 전 모델 CTF High 임계치 초과 / Tacit Knowledge **84.1%** | 전 모델 CTF High 임계치 초과 | §9.1.1, §9.1.2.1 |
| **생물 모델 거부 & 과차단 회피** | Severe `0.943` / Benign 과차단 회피 **0.989** | Severe `0.950` / Benign 과차단 회피 **0.978** | Severe `0.946` / Benign 과차단 회피 **0.989** | §9.4.2.1 (GPT-5.4 `0.696` 대비 과차단 대폭 개선) |
| **사이버 모델 거부율 (`not_unsafe`)** | 프로덕션 **0.981** / 합성 **0.998** | 프로덕션 **0.987** / 합성 **0.998** | 프로덕션 **0.986** / 합성 **1.000** | §9.4.2.2 |
| **실시간 계층형 모니터 Recall** | **생물 94.8%** (프롬프트 87.7%, 생성 89.7%) / **사이버 80.6%** (프롬프트 74.9%, 생성 79.8%) | Sol·Terra 활성값 분류기 + 2계층 안전 추론기 적용 | 주제 분류기 + 2계층 안전 추론기 적용 | §9.4.3.1, §9.4.3.2 |
| **`GPT-Red` 프롬프트 인젝션 공격 성공률** | 직접 **0.051%** / 간접(에이전틱) **3.77%** | 직접 **0.061%** / 간접 **3.32%** | 직접 **0.11%** / 간접 **2.94%** | §4.2 (2026-08-03 추가, 낮을수록 안전) |
| **HealthBench Professional (길이 보정)** | **60.5** (GPT-5.5 `51.8` 대비 +8.7, 평균 길이 단축) | **57.7** | **55.7** | §5.1 |
| **외부 평가 파트너** | **SecureBio** (Bio), **Irregular · UK AISI** (Cyber), **METR** (Self-Improvement), **Apollo Research** (Sandbagging) | — | — | §9.1~§9.3, §9.4.5~§9.4.6 |
