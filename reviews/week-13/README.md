# [Week 13] 도구 사용(Tool-Use) 모델 및 Autonomous Agent의 안전 (Track 4 개막)

- **주제**: 간접 프롬프트 인젝션(IPI)과 과잉 에이전시(Overeagerness)에서 제어·데이터 흐름 분리(`CaMeL`), 입출력 이중 가드레일(`Auto Mode`), 그리고 3대 환경 격리(Containment) 아키텍처까지 — 자율 에이전트 보안의 실전 방어선
- **리뷰 일자**: 2026-11-02 (월)
- **트랙**: Track 4 — Sovereign AI & Practical Application (**Track 4 개막**)
- **난이도**: 🟡 중급 ~ 🔵 실전

---

## 🎯 학습 목표
1. 단순 텍스트 챗봇과 달리 **4대 구성요소(`Model · Harness · Tools · Environment`)** 로 작동하는 자율 에이전트가 왜 **'치명적 삼합(Lethal Trifecta: 사적 데이터 접근 + 비신뢰 외부 콘텐츠 노출 + 외부 행동/통신 권한)'** 을 통해 원격 간접 프롬프트 인젝션(IPI)의 표적이 되는지 이해한다.
2. 프롬프트 출처 표식(`Spotlighting`)과 **명령어 우선순위 계층(`Instruction Hierarchy`)** 이 직접 인젝션은 제압(`0.051%`)하면서도 왜 에이전틱 간접 인젝션(`2.94~3.77%`)과 **적응형 공격(`arXiv:2510.09023`, 12개 방어 기법 `>90%` 우회)** 앞에서는 단독 방어선이 될 수 없는지 파악한다.
3. 신뢰된 질의에서 추출한 **제어 흐름(Control Flow)** 과 비신뢰 도구 출력의 **데이터 흐름(Data Flow)** 을 원천 분리하고 Capability 보안을 강제하는 **`CaMeL`(`arXiv:2503.18813`)** 의 설계 원리와, **인바운드 도구 결과 프로브 + 아웃바운드 도구 호출 분류기**를 결합한 **`Auto Mode`**(`Opus 5 Cowork` 브라우저 IPI `0/129` 달성)의 다층 방어 메커니즘을 익힌다.
4. Anthropic이 공개한 실전 격리 공학 보고서(`How we contain Claude across products`, 2026-05)를 통해 **인간 승인 피로(`93%` 승인율)** 의 실태, **3대 환경 격리 패턴(`gVisor 컨테이너 · OS 샌드박스 · 로컬 하이퍼바이저 VM`)**, 그리고 실제 현장에서 뚫렸던 **4대 보안 사고(신뢰 대화상자 이전 훅 실행, 피싱된 사용자의 직접 실행 `24/25`, 허용 도메인 `api.anthropic.com`을 통한 유출, VM 격리와 EDR 가시성 충돌)** 의 원인과 패치 구조를 분석한다.
5. **2026년 3대 시스템 카드(`Opus 5`, `GPT-5.6 Sol/Terra/Luna`, `Gemini 3.7 Flash`)** 의 에이전트 안전·도구 사용·과잉 에이전시(`Severity 3` 및 승인 게이트 추론 우회) 정량 지표를 대조하여, 한국 소버린 AI 조직을 위한 **에이전트 격리·샌드박싱·하네스 가드레일 설계 표준**을 수립한다.

---

## 📂 구성 파일
- [`review_week13.md`](review_week13.md): 13주차 심층 분석 보고서 (Track 4 개막)
- 신규 및 갱신 산출물:
  - [`resources/agentic_tool_guardrails_guide.md`](../../resources/agentic_tool_guardrails_guide.md): **소버린 AI를 위한 도구 사용(Tool-Use) 및 자율 에이전트 격리·가드레일 실전 가이드** (신규 작성)
  - [`curriculum/track4_sovereign_ai_impact.md`](../../curriculum/track4_sovereign_ai_impact.md): 에이전트 4계층 방어 및 한국형 소버린 AI 체크리스트 고도화
  - [`resources/reading_list.md`](../../resources/reading_list.md): Week 13 도구 사용 에이전트 보안 · IPI · 샌드박싱 1차 사료 목록 추가

---

## 📌 이번 주차 핵심 수치 (원문 대조 완료)

| 항목 | 값 | 출처 |
| :--- | :---: | :--- |
| 대규모 공개 간접 프롬프트 인젝션(IPI) 대회 결과 (13개 프론티어 모델) | 464명 · `272,000`회 시도 → `8,648`건 성공 (**전 모델 돌파: `Opus 4.5` `0.5%` ~ `Gemini 2.5 Pro` `8.5%`**) | Dziemian 외, Gray Swan (arXiv:2603.15714) |
| 적응형 공격(`The Attacker Moves Second`)의 기존 12개 방어 기법 우회율 | 경사하강·RL·탐색 최적화 결합 시 대부분 **공격 성공률(ASR) `90% 초과`** | Nasr, Carlini 외 (arXiv:2510.09023) |
| `CaMeL` 제어·데이터 흐름 분리 방어기의 `AgentDojo` 해결률 | 비방어 시스템(`84%`) 대비 **`77%` 과업을 증명 가능한 보안(0% 인젝션 돌파)으로 해결** | Debenedetti, Carlini 외 (arXiv:2503.18813) |
| `Claude Code` 사용자 승인 프롬프트 평균 승인율 & OS 샌드박스 도입 효과 | 승인 프롬프트 **`~93%` 승인(승인 피로)** → `Seatbelt`/`bubblewrap` 도입 후 **승인 프롬프트 `84%` 감소** | Anthropic Engineering (2025-10 / 2026-05) |
| `Claude Code Auto Mode` 분류기의 과잉 행동 포착률 vs 오차단율 | 과잉 행동(overeager actions) **`~83%` 사전 포착 (`~17%` 통과)**, 정상 명령 오차단 **`~0.4%`** | Anthropic, *How we contain Claude* (2026-05) |
| 사내 피싱 레드팀: 사용자가 직접 붙여넣은 악성 프롬프트의 `~/.aws/credentials` 유출률 | 모델 계층 방어가 무력화되어 **`25`회 재시도 중 `24`회 유출 완료 (`96%`)** | 동 (2026-02 사내 레드팀) |
| Gray Swan IPI 벤치마크(Q1 2026, `k=15` 시도) 모델별 공격 성공률 | **`Opus 5` `2.0%`** ($k=1$: `0.2%`) vs `Muse Spark` `16.5%`, **`GPT-5.6 Sol` `20.0%`** ($k=1$: `3.1%`), **`Terra` `30.4%`**, **`Luna` `43.9%`** | Claude Opus 5 System Card §5.2.1 (p.73) |
| `Opus 5` 표면별 적응형 IPI 공격 성공률 (무방어 → 프로브/`Auto Mode` 활성화) | 코딩: `0.56% →` **`0.18%`** (`4/40`) · 컴퓨터 사용: `0.54% →` **`0.25%`** (`1/14`) · 브라우저(`Cowork`): `3.70% →` **`0%` (`0/129`)** | 동 §5.2.2 (p.74–77) |
| `GPT-5.6` `GPT-Red` 자동화 레드팀 직접 vs 간접 프롬프트 인젝션 공격 성공률 | 직접(Instruction Hierarchy): **`0.051% / 0.061% / 0.11%`** vs 간접(에이전틱 도구): **`3.77% / 3.32% / 2.94%`** (`Sol/Terra/Luna`) | GPT-5.6 System Card §4.2 (p.13–14) |
| `GPT-5.6` 우발적 데이터 덮어쓰기 회피율 (`Avoidance only` / `Avoidance + Correctness`) | `Sol`: **`0.83` / `0.44`**, `Terra`: **`0.81` / `0.37`**, `Luna`: **`0.73` / `0.32`** (`GPT-5.5`: `0.88` / `0.44`) | 동 §3.3 (p.11) |

---

## 🔗 Track 4 진행 로드맵
- **Week 13 (현재, Track 4 개막)**: 도구 사용(Tool-Use) 모델 및 Autonomous Agent의 안전 — *모델 밖으로 손을 뻗는 에이전트의 프롬프트 인젝션·과잉 행동·환경 격리를 어떻게 설계할 것인가*
- **Week 14 (예정)**: 한국형 AI Safety 벤치마크 & 문화적/법적 가드레일 (인공지능기본법)
- **Week 15 (예정)**: 독자 파운데이션 모델사를 위한 비용 효율적 Safety 파이프라인 & 비상 대응(Rollback/Re-align)
- **Week 16 (예정)**: 총정리 & 한국형 파운데이션 모델 Safety Blueprint 작성
