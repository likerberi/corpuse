# [Week 01] AI Safety & Alignment 기본 분류 및 위험 지형도 분석

- **리뷰 일자**: 2026-08-18 (화)
- **트랙/갈래**: Introductory & Governance Overview
- **난이도**: 🟢 입문~중급
- **대상 문서 및 원문 링크**:
  - [BlueDot Impact - AI Safety Fundamentals (AISF)](https://bluedot.org/)
  - [Dan Hendrycks et al. - An Overview of Catastrophic AI Risks (CAIS)](https://arxiv.org/abs/2306.12001)
  - [Anthropic - Responsible Scaling Policy & Claude 5 Overview](https://www-cdn.anthropic.com/c5fbac3f0b1280a933ebd26d3cb8bb9f5bdeaf48/Claude%20Opus%205%20System%20Card.pdf)

---

## 1. 핵심 요약 (Executive Summary)

AI의 역량이 단순 텍스트 완성을 넘어 자율적인 추론, 코딩 및 에이전트 행동으로 진화함에 따라 AI 안전(AI Safety)은 더 이상 단순한 '윤리 가이드라인'이 아닌 **시스템 레벨의 실존적 위험 통제 공학**으로 재정의되었습니다. 본 문서는 BlueDot AISF와 CAIS의 핵심 분류 체계를 통해 AI 위험을 4대 축(악의적 오용, AI 경쟁, 조직적 위험, 통제 불능 AI)으로 체계화하고, 최신 프론티어 모델(Claude 5, GPT-5.6, Gemini 3.7)의 실전 보안 이슈와 결부하여 한국형 소버린 AI의 대응 방향을 제시합니다.

- **핵심 목표**: AI 안전의 4대 재앙적 위험 지형도(Catastrophic Risk Taxonomy)를 확립하고 정렬(Alignment)의 기술적 기초를 이해한다.
- **주요 제안/발견**: 안전은 모델 학습 후 덧붙이는 것이 아니라, 사전 훈련(Pre-training) 데이터 필터링, RLAIF 헌법적 정렬, 추론 시점 가드레일, 그리고 사후 인시던트 패치 체계까지 연결된 전주기 라이프사이클 관리여야 한다.
- **핵심 키워드**: `#CatastrophicRisk` `#AlignmentTaxonomy` `#SovereignSafety` `#RLAIF` `#IncidentResponse`

---

## 2. 세부 내용 분석 (In-depth Technical Analysis)

### 2.1 AI 위험의 4대 분류 체계 (Hendrycks & BlueDot)

```mermaid
mindmap
  root((AI 재앙적 위험))
    악의적 오용 (Malicious Use)
      CBRN 생화학 무기 제조 조력
      자동화된 사이버 침투 및 제로데이 공격
      대규모 맞춤형 여론 조작 및 기만
    AI 경쟁 압력 (AI Race)
      안전 검증 생략 및 조기 배포
      군비 경쟁 및 군사 AI 자율화
    조직적 위험 (Organizational Risks)
      안전 불감증 및 내부 보안 취약
      가중치(Weights) 유출 및 도난
    통제 불능 AI (Rogue AIs)
      목표 왜곡 (Goal Misgeneralization)
      전력 추구 및 자율 복제 (Power-seeking)
      기만적 정렬 (Deceptive Alignment)
```

1. **악의적 오용 (Malicious Use)**
   - 공격자가 고성능 모델을 활용하여 생화학(CBRN) 프로토콜을 합성하거나, 사이버 공격 도구를 무기화하는 위험.
2. **경쟁 압력 (AI Race Dynamics)**
   - 기술 우위를 점하기 위해 안전 평가 기간을 단축하거나 완화 조치를 완화하여 배포하는 구조적 위험.
3. **조직적 위험 (Organizational / Governance Risks)**
   - 안전 부서의 권한 부족, 내부 보안 미비로 인한 모델 가중치 유출, 형식적인 레드팀 운영.
4. **통제 불능 AI (Rogue AIs / Alignment Failure)**
   - 보상 해킹(Reward Hacking), 기만(Deception) 등으로 인해 인간의 실제 의도와 다른 목표를 최적화하며 통제를 벗어나는 위험.

---

## 3. 최근 동향 및 진화 과정 (Context & Recent Evolution)

- **2024년 대비 2026년 프론티어 현황**:
  - 단순 대화형 챗봇에서 **가변 추론(Thinking) 및 자율 도구 실행 에이전트**로 전환됨에 따라 '출력 텍스트 검열'만으로는 안전을 담보할 수 없게 되었습니다.
- **Claude Fable 5 & GPT-5.6의 출시/회수 및 보안 재조정 교훈**:
  - 실제 프론티어 랩에서도 배포 직후 예측하지 못한 보안 홀(사이버 자동화 공격 연계, 프롬프트 인젝션 우회)이 발견되어 **일시 서비스 차단(Block) 후 가드레일 재조정(Security Re-tuning)**을 거쳐 재출시하는 사례가 발생했습니다.
  - 이는 완벽한 사전 검증은 불가능하며, **즉각적인 핫픽스(Hotfix) 및 회수/재조정 런북**이 필수적임을 입증합니다.

---

## 4. 🇰🇷 한국 독자 파운데이션 모델(Sovereign AI) 개발 관점 시사점

> **"세계 최고 수준의 컴퓨팅 파워는 없지만, 독자적인 파운데이션 모델을 안정적으로 서비스해야 하는 입장에서의 실전 적용점"**

### 4.1 리소스 및 인프라 현실성 (Cost & Feasibility)
- 빅테크처럼 수백 명의 전담 레드팀을 상시 가동할 수 없으므로, **3단계 경량 파이프라인**을 구축해야 합니다:
  1. 오픈소스 안전 모델(Llama Guard / ShieldGemma 등)을 인퍼런스 앞단/뒷단에 배치.
  2. 사전 수집된 유해 한국어 프롬프트 셋(Ko-Safety Benchmark)을 이용한 자동화 CI/CD 회귀 테스트.
  3. API 레이어에서의 토큰 이상 패턴 감지 및 즉각적 세션 격리.

### 4.2 한국어 및 로컬 맥락 특수성 (Cultural, Linguistic & Legal Specifics)
- **다국어 번역 우회 (Cross-lingual Jailbreak)**: 영어로 필터링된 유해 지식이 한국어 은어, 방언, 초성체 등으로 질의될 때 필터가 무력화되는 현상 방어.
- **국내 법제도 준수**: 개인정보보호법(주민번호/개인 식별 정보 유출 차단), 인공지능기본법의 고위험 AI 투명성 보고 의무 사전 대비.

### 4.3 우리 팀이 당장 적용할 Action Item (Top 3)
1. **[단기/즉시] 한국형 안전 헌법(Korean Safety Constitution) 초안 작성**: 공공/기업 서비스에 필수적인 거부 규칙 및 응답 원칙 20개 조항 수립.
2. **[중기/학습] 오픈소스 안전 분류기 기반 입출력 가드레일 모듈 구축**: API 게이트웨이에 15ms 이하 지연의 경량 필터 적용.
3. **[배포/운영] 인시던트 대응 런북 및 피처 플래그(Feature Flag) 체계 마련**: 특정 기능/도메인 이상 발현 시 5분 내 우회/차단 가능한 관리자 콘솔 구축.

---

## 5. 논의할 질문 (Discussion Questions)
- Q1. 오픈 가중치(Open-weights) 모델을 배포할 경우, 파인튜닝을 통한 안전 정렬 해제(Safety Unlearning)를 어떻게 방어할 것인가?
- Q2. 한국어 특유의 맥락 의존적 표현(비꼼, 풍자)을 안전 가드레일이 과도하게 거부(Over-refusal)하지 않도록 균형점을 어떻게 잡을 것인가?

---

## 6. 참고 문헌
- Hendrycks, D., et al. (2023). *An Overview of Catastrophic AI Risks*. CAIS.
- Anthropic (2026). *Claude 5 System Architecture and Safety Addendum*.
- OpenAI (2026). *GPT-5.6 Preparedness Framework Report*.
