---
type: index
date: 2026-07-30
updated: 2026-07-30
tags:
  - supply-chain
  - strategy
---

# cpim-concept-map

최근 추가된 qa 노트 세 편([[제조업 SCM과 유통업 SCM은 왜 다른 게임이고 산업별 SCM은 어떻게 갈라지는가]], [[과재고는 왜 결품보다 조용히 회사를 죽이고 그 재고 리스크는 결국 누가 떠안는가]], [[우버는 왜 배민이 아니라 모회사 딜리버리히어로를 통째로 인수했나]])에서 다룬 개념 가운데 **CPIM 커리큘럼에 실제로 대응하는 것만** 골라 영역별로 묶은 지도다. 스레드에서 출발한 실무 언어(과재고·밀어내기·바이백·DP)가 시험 용어로는 무엇인지 연결하는 것이 목적이며, **대응하지 않는 것은 억지로 끼워 넣지 않고 마지막 절에 따로 적었다.**

## 현행 커리큘럼 구조 (CPIM 9.0)

CPIM은 ASCM(옛 APICS)의 생산·재고관리 자격이다. **2026년 6월 1일부터 버전 9.0이 시행** 중이며(8.0은 2026년 5월 31일 만료), 2024년 2월 1일 Part 1 + Part 2 분리 체제가 폐지되어 **150문항·3.5시간 단일 시험**으로 운영된다[^cpim9-guide][^cpim9-mavens]. 9.0은 8.0의 8개 영역 중 'Plan and Manage Supply'가 내부/외부 공급으로 쪼개지며 **9개 영역**이 됐다[^cpim9-mavens].

| # | 영역 | 비중 |
| --- | --- | --- |
| I | Supply Chain Strategy (공급망 전략) | 12% |
| II | Sales & Operations Planning (S&OP) | 10% |
| III | Demand Management (수요관리) | 12% |
| IV | Internal Supply (내부 공급) | 12% |
| V | External Supply (외부 공급) | 11% |
| VI | Inventory Management (재고관리) | 14% |
| VII | Detailed Schedules (상세 일정계획) | 12% |
| VIII | Distribution (유통) | 8% |
| IX | Quality, Continuous Improvement & Technology | 9% |

(비중 출처[^cpim9-mavens]. ⚠️ 영역 명칭은 자료마다 축약형·정식명이 섞여 쓰이므로 위 표는 통용 표기 기준이다. 확정 문구는 ASCM 공식 ECM을 참조할 것[^ascm-ecm].)

## 영역별 매핑

### I. Supply Chain Strategy — 가장 밀도 높게 겹치는 영역

[[제조업 SCM과 유통업 SCM은 왜 다른 게임이고 산업별 SCM은 어떻게 갈라지는가]]의 골격이 통째로 이 영역이다.

- **제품 특성과 공급망의 정합(Fisher 프레임)** — 기능적 제품 → 효율형(efficient) 공급망 / 혁신적 제품 → 반응형(responsive) 공급망. "업종이 아니라 제품의 수요 성격이 공급망 설계를 결정한다"는 명제 자체가 전략 영역의 출발점이다.
- **주문침투점(CODP)과 제조환경 4분류** — MTS / ATO / MTO / ETO. CPIM에서 디커플링 포인트는 **예측으로 움직이는 상류와 실주문으로 움직이는 하류를 가르는 지점**으로 정의되며, MTS 환경에서는 완제품 재고가 곧 디커플링 포인트가 된다[^cpim-ecm-topics]. 메모의 "오더 오면 만든다(MTO) vs 팔릴 것을 미리 만들어 둔다(MTS)"가 정확히 이 분류다.
- **Push / Pull** — 디커플링 포인트를 하류에 둘수록 고객 리드타임은 짧아지지만 완제품 재고 리스크가 커지는 트레이드오프.
- **연기전략(Postponement)** — 공통 반제품까지는 예측으로 만들고 최종 차별화를 주문 확정 후로 미루는 기법. 과잉재고·진부화·보유비용을 동시에 낮추는 완화책으로 다뤄진다[^postponement-vmi].
- **Lean / Agile / Leagile** — 디커플링 포인트를 경계로 상류는 린, 하류는 애자일로 운영하는 하이브리드.
- **Make-or-Buy·수직통합** — [[우버는 왜 배민이 아니라 모회사 딜리버리히어로를 통째로 인수했나]]에서 우버의 '에셋라이트 오케스트레이터' 전략(직접 만들지 않고 네트워크로 흡수)이 여기 걸치지만, 이 노트의 본체는 M&A·규제라 대응은 얕다(아래 「CPIM 밖」 참조).

### III. Demand Management — DP(Demand Planner)와 예측 편향

[[과재고는 왜 결품보다 조용히 회사를 죽이고 그 재고 리스크는 결국 누가 떠안는가]]의 ⑤절이 이 영역이다.

- **수요계획 담당자(Demand Planner)의 직무** — 다른 모든 기능이 그것에 맞춰 계획을 세우는 **단일 수요 숫자**를 소유하고, 통계 베이스라인 생성 → 인간 판단의 개입 시점 판단 → 부서 간 합의(consensus) 도출 → 예측 정확도 측정의 사이클을 돈다.
- **예측 오차와 편향(bias)** — CPIM은 정확도 지표와 편향 감시를 함께 다룬다. **MAPE**(평균절대백분율오차)로 오차 크기를, **추적 신호(tracking signal)**로 편향의 누적을 감시하며, 추적 신호가 허용 범위(통상 −6에서 +6 사이)를 벗어나면 예측 모델이 더는 유효하지 않다고 본다[^forecast-metrics]. 실무적으로 **양(+)의 편향은 만성적 과소예측 → 결품**을, **음(-)의 편향은 만성적 과대예측 → 과잉재고**를 낳는다[^forecast-metrics] — 노트의 "부실한 예측의 대가는 재고로 지불된다"가 이 대목이다.
- **채찍효과(Bullwhip Effect)** — 최종 수요는 완만한데 상류로 갈수록 주문 변동이 증폭되는 현상. 지표로는 **과잉재고·진부화·재고보유비용**으로 드러나며[^postponement-vmi], 완화책으로 정보 공유·VMI·연기전략이 함께 다뤄진다.

### VI. Inventory Management — 이번 PR에서 가장 실무적으로 겹치는 영역

과재고 노트의 ①·④절 대부분이 여기 대응한다(비중 14%로 9개 영역 중 최대).

- **재고보유비용(carrying cost)** — 자본비용·보관·보험·세금·취급·손모·진부화의 합. CPIM 의사결정 시나리오에서 **보유비용·주문비용·품절비용** 3종이 기본 축이다[^postponement-vmi]. 노트가 인용한 "재고가치의 20-30%" 벤치마크가 이 항목이다.
- **초과·진부화 재고(E&O)** — 과재고가 결품과 달리 즉시 손익에 잡히지 않고 뒤늦게 평가손실로 터지는 구조.
- **안전재고(Safety Stock)** — 수요·리드타임 불확실성을 흡수하는 버퍼. CPIM은 순소요량 계산식(총소요량 + 안전재고 − 현재고)과 안전 리드타임을 함께 다룬다[^cpim-ecm-topics]. **예측이 부실할수록 버퍼를 두껍게 가져가야 하고, 두꺼운 버퍼가 곧 과재고 리스크**라는 노트의 결론이 여기서 나온다.
- **재고 관리 시스템** — 재주문점(ROP), 정기 발주, min-max, two-bin, 칸반 등[^cpim-ecm-topics].
- **리드타임 단축의 의미** — 예측해야 하는 구간을 줄여 안전재고 필요량 자체를 줄이는 접근(= 예측을 잘하는 게 아니라 예측 지평선을 줄이는 것).

### V. External Supply — 공급자 관계와 재고 리스크의 계약적 배분

과재고 노트 ②절(바이백·Distributor 4주체 구조)이 이 영역에 걸린다.

- **VMI(공급자관리재고)** — 공급자가 고객의 재고 데이터를 받아 보충 시점·수량을 직접 결정하는 방식. 가시성을 높여 **채찍효과를 줄이고 보충을 안정화**하는 수단으로 다뤄진다[^postponement-vmi].
- **공급자 계약과 리스크 배분** — 바이백 조항처럼 "안 팔린 재고를 누가 되사는가"를 계약으로 정하는 장치. 노트가 표로 정리한 Manufacturer / Distributor / Buyer / End User의 **"단가 인하 ↔ 리스크 인수" 맞교환**이 이 관점의 사례다.
- 노트의 결론 **"재고는 공급망 어딘가에 반드시 존재한다, 누가 들고 있느냐의 문제"**는 이 영역과 VI(재고관리)를 잇는 다리다.

### VIII. Distribution — 납품 성과와 유통 네트워크

- **납품 성과 지표(OTIF)** — 정시·정량 납품률. 월마트 사례(98% 기준, 미달 시 원가 3% 차감)는 유통 채널이 공급자에게 부과하는 서비스 수준의 실제 형태다.
- **유통망 설계와 라스트마일** — 분산형 이행(ship-from-store·MFC), 라스트마일 비용 비중. 이 주제는 기존 노트 [[라스트마일이 배송비의 53%를 삼키는 이유, 답은 트럭이 아니라 상류에 있다]]에서 DRP·ATP 관점으로 더 깊게 다뤘다.

### IX. Quality, Continuous Improvement & Technology

- **JIT·린 생산** — 도요타식 적기생산과 kaizen, Tier 1/2/3 다층 공급망의 동기화. 재고 최소화의 대가로 한 부품만 끊겨도 라인이 멈추는 취약성까지가 한 세트다.

### II·IV·VII — 이번 PR에서 얕게 스치는 영역

- **II. S&OP** — 과재고 노트의 "영업(판매 실적 보너스) vs 운영(비용 절감 보너스)이 하나의 예측 숫자를 놓고 부딪힌다"가 S&OP가 존재하는 이유 그 자체지만, 노트는 프로세스(수요 리뷰 → 공급 리뷰 → 사전회의 → 경영진 회의)까지는 다루지 않았다.
- **IV. Internal Supply / VII. Detailed Schedules** — 반도체의 긴 리드타임·WIP·안전재고 누적, 제조업의 "원재료 + 재공품(WIP) + 외주 관리" 3중 통제가 여기 걸치지만, MRP·MPS·CRP 같은 핵심 기법은 이번 노트들에 등장하지 않는다. **보강이 가장 필요한 공백**이다.

## CPIM 밖 — 억지로 매핑하지 않은 것

- **채널 스터핑(재고 밀어내기)** — 현상 자체는 재고 리스크 전가지만, 노트가 인용한 판단 기준은 **SEC 회계 부정·경영진 제재**로 회계·거버넌스 영역이다. CPIM의 재고관리가 아니라 재무보고 윤리 쪽이다.
- **콜드체인 규제·일련번호 추적** — GMP/GDP, DSCSA serialization은 제약 규제 준수(GxP) 영역이다. CPIM은 품질경영을 다루지만 이런 산업별 법규 자체는 범위 밖이다.
- **[[우버는 왜 배민이 아니라 모회사 딜리버리히어로를 통째로 인수했나]] 전반** — 공개매수 구조·기업결합 심사·플랫폼 크로스셀은 M&A·경쟁법·플랫폼 전략이다. CPIM과의 접점은 make-or-buy/수직통합 정도이며, 이 노트를 CPIM 학습 자료로 쓰는 것은 무리다.

## 출처

[^cpim9-guide]: OpenExamPrep, "FREE APICS CPIM 2026 Exam Guide: v9.0 Single Exam" — https://open-exam-prep.com/blog/apics-cpim-certified-in-production-and-inventory-management-exam-guide-2026 (2026-07-30)
[^cpim9-mavens]: Supply Chain Mavens, "CPIM 9.0 is here!" — https://www.supplychainmavens.net/cpim9 (2026-07-30)
[^ascm-ecm]: ASCM, "Exam Content Manual, Effective June 1, 2026, Version 9.0" — https://www.ascm.org/globalassets/ascm_website_assets/docs/ecm/ecm-CPIM9.pdf (2026-07-30, ⚠️ 직접 열람은 차단되어 검색 결과 기준으로만 확인)
[^cpim-ecm-topics]: ASCM, "CPIM Exam Content Manual" (MRP·DRP·안전재고·디커플링 포인트·재고 시스템 수록) — https://www.ascm.org/learning-development/certifications-credentials/cpim/ecm/ (2026-07-30)
[^postponement-vmi]: Taylor & Francis, "The moderating role of vendor managed inventory on the bullwhip effect in the COVID-19 pandemic" (채찍효과 지표: 과잉재고·진부화·보유비용 / 연기전략·VMI의 완화 효과) — https://www.tandfonline.com/doi/full/10.1080/23311975.2022.2158604 (2026-07-30)
[^forecast-metrics]: Mathnal Analytics, "Forecast Bias & Errors: 12 Metrics Guide — MAPE, RMSE, Tracking Signal" — https://mathnal.tech/newsletter_forecast_bias_errors.html (2026-07-30)
