---
type: qa
date: 2026-07-22
updated: 2026-07-22
tags:
  - supply-chain
  - retail
  - strategy
---

# 제조업 SCM과 유통업 SCM은 왜 다른 게임이고 산업별 SCM은 어떻게 갈라지는가

## 메모

(아래는 스레드(Threads)에서 캡처한 대화 원문 + 사용자 질문)

**제조업 SCM과 유통업 SCM은 왜 완전히 다른 게임인가**
제조업에서 유통업으로 넘어오면서 가장 먼저 깨달은 것이 있습니다. 발주서 한 장의 의미가 완전히 다르다는 것입니다. (1/3)

제조업 SCM의 특성
1. 수요가 예측 가능하고 사이클이 김
2. 리드타임이 길어도 바이어가 기다려줌
3. SKU가 한번 만들어지면 반복 구매 주기. 로 수요가 발생하고 제품 수명이 김
4. "오더가 오면 만든다"는 구조가 작동 (2/3)

유통업 SCM의 특성
1. 수요가 SNS 하나로 하루 만에 10배가 됨
2. 리테일러는 납기 하루 늦으면 차지백을 때림
3. SKU 수백-수천 개, 제품 수명 1-2년
4. "팔릴 것을 미리 만들어 놓아야" 하는 구조 (3/3)

(댓글, scmcenter) 잘 정리되었어요. 제조업 SCM은 제품 뿐만아니라 원재료까지 관리 해야하는 점과 생산라인 내에 재공(WIP)의 흐름, 외주 관리도 해야해서 SCM구조 관점에서는 더 복잡하지만, FCST부분은 유통업이 더 복잡한것같아요. 제조+유통까지하는 기업은.......ㅜㅜ

---

이 내용에 대해 좀 더 자세히 조사해서 정리해줘. 제조업 SCM과 유통업 SCM, 나아가 산업 별 SCM에 어떤 차이가 있을까?

## 리서치

### 대주제 — 제조업 SCM과 유통업 SCM을 '다른 게임'으로 가르는 근본 축은 무엇이고, 그 축 위에서 산업별 SCM은 어떻게 갈라지는가

메모의 직관("발주서 한 장의 의미가 다르다")은 SCM 학계가 20년 넘게 다뤄온 핵심 명제와 정확히 맞닿아 있다. **한 SCM을 다른 SCM과 구별 짓는 것은 업종 이름이 아니라 '제품의 수요 성격'과 '재고를 어디까지 미리 만들어 두는가(디커플링 포인트)'라는 두 축**이다. 아래는 ① 두 축을 세우는 이론 프레임 → ② 제조업 SCM의 성격 → ③ 유통업 SCM의 성격 → ④ 산업별로 이 축이 어떻게 다르게 세팅되는가 → ⑤ 제조+유통을 겸하는 기업의 딜레마 순으로 정리한다.

**① 두 SCM을 가르는 근본 축 — Fisher의 제품·공급망 정합, 그리고 주문침투점(CODP)**

- **Marshall Fisher의 프레임(HBR, 1997)** 이 출발점이다. 제품을 두 종류로 나눈다 — **기능적 제품(functional)**: 안정적 수요·긴 수명·낮은 마진·적은 다양성. **혁신적 제품(innovative)**: 불확실 수요·짧은 수명·높은 마진·다품종. 그리고 각각에 맞는 공급망이 다르다고 주장했다. 기능적 제품엔 **효율형(efficient) 공급망**(재고·비용 최소화, 높은 가동률), 혁신적 제품엔 **반응형(responsive) 공급망**(여유 버퍼 재고·여유 capacity, 속도·유연성으로 결품·재고 구식화 최소화, 차별화 지연[postponement])을 붙여야 한다. Fisher는 "많은 기업이 시스템·설비에 투자하고도 부진한 이유는 제품에 맞지 않는 공급망을 썼기 때문"이라고 진단했다[^fisher-umbrex][^fisher-hbr]. 메모의 대비는 사실상 **제조업=기능적/효율형, 유통업(패션·소비재)=혁신적/반응형** 구도의 재발견이다.
- **주문침투점(Customer Order Decoupling Point, CODP)** 이 메모의 "오더 오면 만든다 vs 미리 만들어 놓는다"를 정확히 설명한다. CODP는 **공급망에서 제품이 특정 고객 주문과 연결되는 지점**으로, 이 점의 하류(下流)는 실제 주문에 따라, 상류(上流)는 수요 예측에 따라 움직인다[^codp-fabrico][^codp-review]. 위치에 따라 4가지다:
  - **MTS(재고생산·Make-to-Stock)**: 디커플링 포인트가 완제품에 있음 → 고객은 매대에서 바로 구매, 리드타임 ≈ 0. **유통업의 "미리 만들어 놓는다".**
  - **ATO(주문조립·Assemble-to-Order)**: 모듈·반제품을 재고로 두고 주문 시 구성(예: PC).
  - **MTO(주문생산·Make-to-Order)**: 원자재만 두고 주문이 와야 가공. **제조업의 "오더 오면 만든다".**
  - **ETO(주문설계·Engineer-to-Order)**: 주문·사양이 나와야 설계 착수(예: 플랜트·선박).
  - 핵심 트레이드오프: **디커플링 포인트를 하류로 둘수록 고객 리드타임은 짧지만 완제품 재고 리스크가 커지고, 상류로 둘수록 재고는 가볍지만 대기가 길다**[^codp-fabrico]. 이것이 곧 **push(예측·상류) vs pull(주문·하류)** 의 트레이드오프다.
- **채찍효과(Bullwhip Effect)** 는 두 세계 모두를 괴롭히지만 방식이 다르다. Lee·Padmanabhan·Whang(1997, *Management Science*)은 최종 수요는 완만한데 상류로 갈수록 주문 변동이 증폭되는 현상의 4대 원인을 **수요신호 처리, 주문 배치(batching), 가격 변동·판촉, 물량 배분·품귀 게임(shortage gaming)** 으로 정리했다(P&G 기저귀 사례)[^bullwhip-mit][^bullwhip-lee]. 유통업은 하류의 수요 급변이 상류를 때리고, 제조업은 긴 리드타임이 이 증폭을 더 키운다(반도체가 대표적).

**② 제조업 SCM — 상류(원재료·WIP·외주)가 무겁고, 예측 가능한 수요를 긴 리드타임으로 받아내는 게임**

- 메모 요지(예측 가능·긴 사이클·긴 리드타임을 바이어가 기다려줌·반복 구매·긴 제품 수명·"오더 오면 만든다")는 **기능적 제품 + MTO/상류 디커플링**의 특징이다. B2B 특성상 바이어가 리드타임을 감내하므로, 완제품을 미리 쌓기보다 **주문을 받아 생산**하는 편이 합리적이다[^fisher-umbrex][^codp-fabrico].
- 다만 **구조적 복잡성은 제조업이 더 크다**(댓글의 통찰과 일치). 제조업 SCM은 완제품뿐 아니라 **① 원재료·부품 조달, ② 생산라인 내 재공품(WIP) 흐름, ③ 외주(아웃소싱) 관리**까지 동시에 통제해야 한다. 반도체처럼 리드타임이 길수록 WIP·안전재고가 구조적으로 쌓인다[^semi]. 즉 제조업의 난도는 '넓고 깊은 상류 네트워크의 동기화'에 있다.

**③ 유통업 SCM — 하류 수요가 하루 만에 뒤집히고, '예측(FCST)'이 승부처인 게임**

- 메모 요지(SNS로 하루 만에 수요 10배·다품종(SKU 수백~수천)·짧은 제품 수명(1~2년)·"팔릴 것을 미리 만들어 놓는다")는 **혁신적 제품 + MTS/완제품 디커플링**의 특징이다. 완제품을 선(先)비축해야 하므로 **무엇이 얼마나 팔릴지의 예측(수요계획, FCST)이 곧 손익**이다 — 과잉이면 재고 구식화·폐기, 과소면 결품·기회손실[^fisher-umbrex][^grocery].
- "납기 하루 늦으면 차지백"은 실제 유통 규범이다. 월마트의 **OTIF(On-Time In-Full)** 는 납품 정시·정량을 요구하고(대체로 98% 기준, 필수도착일 MABD 창은 신선식품 1일·일반 2일), 미달 시 **미준수 물량 원가의 3%를 인보이스에서 차감(차지백)** 한다. 경고 없이 자동 부과되고 분쟁 인정도 드물다[^otif][^chargeback]. 유통업 SCM의 압력이 '정확·정시'에 쏠려 있음을 보여준다.
- **결론적 대비**: 제조업은 '구조(원재료·WIP·외주)'가 복잡하고, 유통업은 '예측(변동성 큰 하류 수요)'이 복잡하다 — 이는 댓글의 관찰과 정확히 부합한다.

**④ 산업별 SCM — 같은 두 축(수요 성격 × 디커플링 위치)이 산업마다 다르게 세팅된다**

- **패션·어패럴(초(超)반응형)**: 시즌이 극단적으로 짧다. Zara(Inditex)는 수직통합으로 디자인→생산→물류를 통제해 신상품 리드타임을 **약 15일**(럭셔리 평균 6개월 대비)까지 줄이고, 연 **20 시즌**·주 2회 신상 투입을 돌린다. 매장 판매 데이터를 매일 본사로 피드백해 생산을 조정한다 — Fisher의 반응형 공급망의 교과서 사례다[^zara]. SKU 다양성·구식화 리스크가 최고 수준.
- **식품·신선(콜드체인·폐기 최소화)**: 유통기한이 '분기'가 아니라 '일(日)' 단위다. 신선·유제품·육류는 냉장(2–8℃)·냉동(–18℃ 이하) 콜드체인을 끝까지 유지해야 하고, 짧은 유통기한 탓에 **더 잦은 단기 예측**이 필요하다. 날씨·판촉·SNS로 수요가 급변하고, 한 케이스만 더 시켜도 폐기, 덜 시키면 결품이라 예측 오차의 회복 창이 '며칠, 때로는 몇 시간'이다[^grocery].
- **반도체·전자(초장(超長) 리드타임·강한 사이클)**: 리드타임이 **24주~1년 이상**, 산업 사이클이 **3~5년**, fab 한 곳 투자비가 **200억 달러+** 로 한 번 결정하면 비가역적이다. 긴 리드타임 탓에 WIP·안전재고를 많이 쥘 수밖에 없고, 작은 최종 수요 변화가 크게 증폭되는 **채찍효과가 극심**하다(die bank 등 postponement로 완충)[^semi][^semi-cycle].
- **자동차(JIT·다층 공급망)**: 도요타식 **적기생산(JIT)** 과 린 원칙으로 재고를 최소화하되, **Tier 1/2/3 다층 공급망**을 kaizen으로 동기화한다. 수만 개 부품이 맞물려 돌아가므로 한 부품(예: 반도체)만 끊겨도 라인 전체가 멈추는 취약성이 있다[^auto].
- **제약(규제 최우선)**: 비용·효율보다 **규제·품질이 상위 제약조건**이다. GMP/GDP(우수 제조·유통 기준)를 준수해야 하고, 온도 일탈 관리가 필수인 **콜드체인**, 그리고 위·변조 방지를 위한 **일련번호 추적(serialization, 미국 DSCSA 2026년 전면 시행)** 까지 요구된다 — 추적성·규정 준수가 SCM 설계를 지배한다[^pharma].
- **이커머스·옴니채널(분산 풀필먼트·라스트마일)**: 전통 유통이 DC·매장으로 팔레트 단위 대량 배송이라면, 이커머스는 **개별 소포를 소비자에게 직배송**한다. 매장·MFC(마이크로 풀필먼트)를 활용한 분산형 이행(ship-from-store, 픽업)과 실시간 재고 동기화가 핵심이며, **라스트마일이 이행 비용의 50%+** 를 차지해 승부처가 된다[^omni][^lastmile].

**⑤ 제조+유통을 겸하는 기업의 딜레마 — 두 복잡성을 동시에 진다, 해법은 '리게일'과 '연기전략'**

- 댓글의 "제조+유통까지 하는 기업은…ㅜㅜ"이 핵심을 짚는다. 이런 기업은 **제조의 구조 복잡성(원재료·WIP·외주)과 유통의 예측 복잡성(변동성 큰 완제품 수요)을 동시에** 짊어진다.
- 학계의 답은 **리게일(leagile)** 이다. Naylor·Naim·Berry(1999)가 제시한 개념으로, **디커플링 포인트를 기준으로 상류는 린(lean·평준화·낭비 제거), 하류는 애자일(agile·반응·맞춤)** 로 운영해 두 목표를 한 사슬 안에서 절충한다[^leagile]. 실무적으로는 **연기전략(postponement)** — 공통 반제품·모듈은 예측으로 미리(push) 만들어 두고, 최종 차별화는 주문·수요 확정 후(pull) 수행 — 로 구현된다(Fisher가 말한 '차별화 지연', 반도체 die bank가 그 예)[^fisher-umbrex][^semi].
- 요컨대 정답은 하나의 SCM이 아니라 **제품 성격에 SC를 맞추고(Fisher), 디커플링 포인트를 어디에 둘지(CODP)를 산업·품목별로 다르게 세팅**하는 것이다. '다른 게임'이라는 메모의 직관은 옳되, 두 게임은 같은 두 축(수요 성격 × 재고 선(先)투입 지점) 위의 서로 다른 좌표다.

## 관련 노트

- [[news-260623-Built to bend-How AI-first supply chains adapt when disruption hits]] — AI-first 공급망이 계획과 실행을 이어 붕괴 상황에 적응하는 방식을 다룬 노트. 유통업 SCM의 핵심인 '반응성·실시간 수요 대응'을 실제 사례로 보강한다.
- [[news-260623-Kraft Heinz merges procurement and supply chain units]] — 조달과 공급망 조직을 한 부서로 통합한 사례. 제조+유통을 겸하는 기업이 구조 복잡성을 어떻게 관리하는지 보여줘 ⑤ 하이브리드 딜레마와 직결된다.
- [[logis-tech-market-overview]] — 물류테크 시장 지형도. 유통·이커머스 SCM의 실행 레이어(라스트마일·풀필먼트)를 담당하는 스타트업들을 담아, ④의 이커머스 SCM 특성을 구체화한다.
- [[strategic-thinking-2-1-국제 분쟁과 세계 경제]] — 국제 분쟁이 무역·공급망에 미치는 영향을 다룬 강의 노트. 산업별 SCM이 지정학·거시 충격에 서로 다르게 노출되는 상위 맥락을 제공한다.

---

[^fisher-umbrex]: Umbrex, "Efficient vs Responsive Supply Chain Model (Fisher)" — https://umbrex.com/resources/frameworks/supply-chain-frameworks/efficient-vs-responsive-supply-chain-model-fisher/ (2026-07-22)
[^fisher-hbr]: Marshall L. Fisher, "What Is the Right Supply Chain for Your Product?" (Harvard Business Review, 1997) — https://store.hbr.org/product/what-is-the-right-supply-chain-for-your-product/97205 (2026-07-22)
[^codp-fabrico]: Fabrico, "The Decoupling Point: Where Make-to-Stock Meets Make-to-Order" — https://www.fabrico.io/blog/decoupling-point-manufacturing/ (2026-07-22)
[^codp-review]: Taylor & Francis (Int'l Journal of Production Research), "The customer order decoupling point in empirical operations and supply chain management research" — https://www.tandfonline.com/doi/full/10.1080/00207543.2024.2314164 (2026-07-22)
[^bullwhip-mit]: MIT Sloan Management Review, "The Bullwhip Effect in Supply Chains" (Lee, Padmanabhan, Whang) — https://sloanreview.mit.edu/article/the-bullwhip-effect-in-supply-chains/ (2026-07-22)
[^bullwhip-lee]: Lee, Padmanabhan & Whang, "Information Distortion in a Supply Chain: The Bullwhip Effect" (Management Science, 1997) — https://www2.isye.gatech.edu/~jvandeva/Classes/6203/2006/TheBullWhipEffectinSCsLee.pdf (2026-07-22)
[^leagile]: "Significance of Lean, Agile and Leagile Decoupling Point in Supply Chain Management" (Naylor·Naim·Berry, 1999 개념 정리) — https://www.researchgate.net/publication/267779764_Significance_of_Lean_Agile_and_Leagile_Decoupling_Point_in_Supply_Chain_Management (2026-07-22)
[^zara]: SupplyChain360, "The Secrets Behind Zara's Supply Chain Strategy" — https://supplychain360.io/zaras-supply-chain-mastery-an-analysis-of-strategy-and-execution/ (2026-07-22)
[^otif]: Orderful, "Walmart OTIF Requirements: Avoid Fines & Penalties" — https://www.orderful.com/blog/walmart-otif (2026-07-22)
[^chargeback]: 8th & Walton, "Walmart Chargebacks: Everything Suppliers Should Know" — https://www.8thandwalton.com/blog/walmart-chargebacks (2026-07-22)
[^semi]: Supply Chain Management Review, "Lead time economics: What semiconductor supply chains reveal about strategic planning" — https://www.scmr.com/article/lead-time-economics-what-semiconductor-supply-chains-reveal-about-strategic-planning (2026-07-22)
[^semi-cycle]: MacroMicro, "Investing in Semiconductor Stocks: Key Insights in Five Charts" (반도체 사이클·재고) — https://en.macromicro.me/blog/investing-in-semiconductor-stocks-key-insights-in-five-charts (2026-07-22)
[^pharma]: SPARQ360, "Pharma & Life Sciences Logistics: GDP, Cold Chain & Serialization" — https://sparq360.com/pharma-life-sciences-logistics-guide/ (2026-07-22)
[^auto]: Supply Chain Today, "Toyota Supply Chain Management" — https://www.supplychaintoday.com/toyota-supply-chain-management/ (2026-07-22)
[^grocery]: RELEX Solutions, "Managing retail grocery supply chains: The complete guide" — https://www.relexsolutions.com/resources/managing-retail-grocery-supply-chains/ (2026-07-22)
[^omni]: McKinsey, "Retail's need for speed: Unlocking value in omnichannel delivery" — https://www.mckinsey.com/industries/retail/our-insights/retails-need-for-speed-unlocking-value-in-omnichannel-delivery (2026-07-22)
[^lastmile]: OneRail, "An Industry-by-Industry Guide to Last Mile Fulfillment & Delivery" — https://www.onerail.com/an-industry-by-industry-guide-to-last-mile-delivery/ (2026-07-22)
