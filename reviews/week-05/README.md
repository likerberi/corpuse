# [Week 05] Claude Opus 5 System Card & Fable 5 회수–재배포 사례

- **주제**: Anthropic Claude Opus 5 System Card 심층 분석 및 Claude Fable 5 회수(Rollback)–재배포(Redeploy) 실전 사건 사후 분석
- **리뷰 일자**: 2026-09-07 (월)
- **트랙**: Track 2 — System Cards & Frontier Evals
- **난이도**: 🟡 중급

---

## 🎯 학습 목표
1. **System Card의 실제 구조**를 193페이지 원문 기준으로 분해하고, RSP 판정(CB-1 / CB-2 / AI R&D)이 어떤 문장으로 내려지는지 확인한다.
2. **Fable / Mythos 이중 트랙 배포**(동일 베이스 모델 + 세이프가드 차등)라는 새로운 배포 거버넌스 패턴을 이해한다.
3. **Fable 5 회수–재배포 사건**(2026년 6~7월)의 전체 타임라인을 복기하고, 기술적 취약점 · 규제 조치 · 서비스 중단이 어떻게 연쇄했는지 분석한다.
4. 차단율만이 아니라 **과차단율(Over-refusal)** 을 함께 계측하는 평가 규율을 도출하고, 한국어 · 국내 법제 맥락의 빈칸을 식별한다.
5. **세이프가드 레이어를 가중치와 분리**하여 핫스왑 가능하게 만드는 아키텍처 요구사항을 정리한다.

---

## 📂 구성 파일
- [`review_week05.md`](review_week05.md): 5주차 종합 심층 분석 보고서
- 신규 산출물: [`resources/incident_runbook.md`](../../resources/incident_runbook.md) — 회수–재배포 인시던트 런북 (Week 04 Action Item #3 이행)

---

## 📌 이번 주차 핵심 수치 (원문 대조 완료)

| 항목 | 값 | 출처 |
| :--- | :--- | :--- |
| Opus 5 RSP 판정 | CB-1 보유(보수적) / CB-2 미도달 / AI R&D 임계치 미도달 → **ASL-3** | Opus 5 System Card §2 |
| 프롬프트 인젝션 공격 성공률 (코딩, Shade) | Opus 4.8 17.44% → **Opus 5 0.41%** (프로브 적용 시 0.18%) | 동 §5.2.2.1 |
| 단일 턴 무해 응답률 (7개 언어, 한국어 포함) | API 96.34% / claude.ai 98.54% | 동 §4.1.1 |
| 과차단율 | API 0.09% / claude.ai **0.47%** (보고된 모델 중 최저) | 동 §4.1.2 |
| 외부 레드팀 투입 | Trajectory Labs 약 100시간, 10a Labs 약 16시간, Gray Swan 과업당 150회 | 동 §3.5.2 |
| Fable 5 중단 기간 | 2026-06-12 중단 → 2026-07-01 전 세계 재배포 | Redeploying Claude Fable 5 |
