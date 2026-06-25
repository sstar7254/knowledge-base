---
type: report
source: 다수 (아래 본문 인라인 URL)
date: 2026-06-24
tags:
  - Sector/AI
  - Sector/Semiconductor
status: inbox
---

# 반도체 밸류체인 분류와 주요 상장기업 참고자료

> 반도체 산업의 표준 분류(밸류체인 단계)와 단계별 주요 상장기업(미국·한국)의 주력 사업을 정리한
> 소스 다이제스트. 검색일 2026-06-24. 분류 개념 자체는 기존 raw 노트 [[반도체 산업]]에도 정리돼 있다.
> 시점에 따라 순위·시총은 변하므로 사실 진술의 시점은 본문에 명기한다.

## 1. 표준 분류 (밸류체인 단계)

반도체 산업은 설계 → 제조 → 후공정(조립·테스트)의 가치사슬과, 이를 떠받치는 EDA/IP·장비·소재
지원 산업으로 나뉜다. 사업모델 기준 핵심 분류는 다음과 같다. [TMT IB Guide](https://ibinterviewquestions.com/guides/tmt-investment-banking/semiconductor-value-chain), [Interface EU - global semiconductor value chain](https://www.interface-eu.org/storage/archive/files/the_global_semiconductor_value_chain.pdf), [SIA ecosystem](https://www.semiconductors.org/ecosystem/)

- **Fabless(팹리스)**: 설계만 하고 제조는 파운드리에 위탁. (Nvidia, AMD, Qualcomm 등)
- **Foundry(파운드리)**: 설계 없이 위탁 제조 전담. (TSMC, GlobalFoundries 등)
- **IDM(종합반도체)**: 설계+제조(자체 fab) 모두 수행. (Intel, Micron, TI 등)
- **OSAT(후공정 외주)**: 파운드리·IDM이 위탁한 패키징·테스트 전담.
- **EDA/IP**: 칩 설계 SW(EDA)와 설계자산(IP) 라이선스 제공.
- **장비(Equipment, WFE)**: 노광·증착·식각·검사 등 제조 장비.
- **소재(Materials)**: 포토레지스트·식각액·전구체·고순도 가스 등.
- (보조) **디자인하우스**: 팹리스 설계를 파운드리 공정에 맞게 재설계, 팹리스–파운드리 연결.

## 2. Fabless (팹리스) — 미국 상장 중심

2026년 기준 AI 가속기 수요가 팹리스 지형을 주도. [BlackRidge Top fabless 2026](https://www.blackridgeresearch.com/blog/list-of-top-global-fabless-semiconductor-companies), [statranker Top 100 2026](https://statranker.org/economy/top-100-semiconductor-companies-by-revenue-2026/)

- **Nvidia (NVDA)**: AI 학습·추론용 GPU/가속기 1위. AI 반도체 사이클의 핵심.
- **AMD (AMD)**: CPU(Ryzen/EPYC)·GPU로 고성능 컴퓨팅에서 Nvidia·Intel과 경쟁.
- **Qualcomm (QCOM)**: 모바일 AP(Snapdragon)·통신 모뎀 강자.
- **Broadcom (AVGO)**: 네트워크 칩·맞춤형 AI ASIC·인프라 SW. (커버리지 있음)
- **Marvell (MRVL)**: 데이터센터용 맞춤형 실리콘·광통신·스토리지 컨트롤러.

## 3. IDM (종합반도체) — 미국·한국

[NerdWallet best semiconductor stocks 2026](https://www.nerdwallet.com/investing/learn/best-semiconductor-stocks), [Congress.gov R46581](https://www.congress.gov/crs-product/R46581)

- **Intel (INTC)**: PC·서버 CPU 설계·제조, 파운드리(Intel Foundry) 병행.
- **Samsung Electronics (005930)**: 메모리·시스템반도체·파운드리를 아우르는 종합. 메모리 1위.
- **SK하이닉스 (000660)**: 메모리(DRAM·NAND), HBM 시장 선도. (커버리지 있음)
- **Micron (MU)**: 미국 유일 메모리 IDM, HBM 경쟁 참여.
- **Texas Instruments (TXN)**: 아날로그·임베디드 1위(8만+ 제품군).
- **Analog Devices (ADI)**: 고성능 아날로그·믹스드시그널. (FY2Q26 매출 $3.62B [SEC 8-K](https://www.sec.gov/Archives/edgar/data/0000006281/000000628126000050/adi2q26exhibit991earnings.htm))

## 4. Foundry (파운드리)

2026년 1분기 점유율: Samsung 6.5%, SMIC 5.1%, UMC 3.9%, GlobalFoundries 3.3% 등 (TSMC 압도적 1위).
[Tom's Hardware - SMIC pure-play](https://www.tomshardware.com/tech-industry/blacklisted-china-chipmaker-smic-becomes-the-worlds-second-largest-pure-play-foundry-by-revenue-outsells-globalfoundries-and-others), [Semiecosystem - TSMC Q1'26](https://marklapedus.substack.com/p/tsmc-gains-foundry-share-in-q1-26)

- **TSMC (TSM)**: 세계 최대 순수 파운드리, 첨단 노드 사실상 독점.
- **GlobalFoundries (GFS)**: 성숙·특화 공정(차량·산업·RF) 중심.
- **UMC (UMC)**: 메인스트림 로직·특화 공정.
- **DB하이텍 (000990)**: 한국 대표 8인치 특화(아날로그·전력반도체) 파운드리. ⚠️(시점별 사업 비중은 공시 확인 필요)
- (중국) **SMIC (0981.HK)**: 중국 최대 파운드리, 성숙 노드 확장.

## 5. EDA / IP

Synopsys·Cadence·Siemens EDA 3사가 시장의 ~85% 과점. [heygotrade SNPS vs CDNS](https://www.heygotrade.com/en/blog/synopsys-vs-cadence-snps-vs-cdns-eda-duopoly-ai-chip-boom/), [Wikipedia: Synopsys](https://en.wikipedia.org/wiki/Synopsys)

- **Synopsys (SNPS)**: EDA 1위. 2025.7 Ansys($35B) 인수로 실리콘~시스템 확장.
- **Cadence (CDNS)**: EDA 2위, 커스텀/디지털 구현 툴.
- **Arm (ARM)**: CPU 명령어셋·코어 IP 라이선스(모바일·서버).
- (한국) **오픈엣지테크놀로지 (394280)**: AI 반도체용 IP(메모리 인터페이스·NPU) 공급.

## 6. 장비 (Equipment)

5대 장비사(ASML·AMAT·Lam·KLA·Tokyo Electron)가 시장의 56~66% 차지. [PatentPC - top equipment](https://patentpc.com/blog/top-chip-making-equipment-companies-asml-applied-materials-and-lam-research-market-data)

- **Applied Materials (AMAT)**: 증착 등 전공정 장비 종합 1위.
- **Lam Research (LRCX)**: 식각·증착(3D NAND·FinFET) 특화.
- **KLA (KLAC)**: 검사·계측(공정제어·수율) 1위.
- (네덜란드) **ASML**: EUV 노광 100% 독점.
- (한국) **한미반도체 (042700)**: HBM용 TC본더(국내 점유율 70%+). [한경](https://www.hankyung.com/article/2026022391801)
- (한국) **원익IPS (240810)**: 증착(CVD/ALD) 등 전공정·디스플레이 장비.
- (한국) **주성엔지니어링 (036930)**: ALD 등 전공정 장비.
- (한국) **HPSP (403870)**: 고압수소어닐링(HPA) 장비 사실상 글로벌 독점.
- (한국) **이오테크닉스 (039030)**: 레이저 응용 장비(마킹·어닐링).
- (한국) **피에스케이 (319660)**: 드라이 스트립 등 패키징·전공정 장비.

## 7. 소재 (Materials)

[stockstalker 반도체 소재](https://stockstalker.co.kr/semiconductor-materials/), [나무위키: 동진쎄미켐](https://namu.wiki/w/%EB%8F%99%EC%A7%84%EC%8E%84%EB%AF%B8%EC%BC%90)

- **동진쎄미켐 (005290)**: 국내 최초 포토레지스트(KrF·ArF·EUV)·CMP 슬러리. 3D NAND용 KrF PR 세계 1위.
- **솔브레인 (357780)**: 식각액·세정액·CMP 슬러리·전구체.
- **한솔케미칼 (014680)**: 과산화수소(세정)·High-K 전구체.
- (미국) **Entegris / DuPont**: 고순도 소재·CMP·특수화학 ⚠️(미국 상장).
- (한국) **엘티씨 (170920)**: 반도체·디스플레이 공정용 박리액 등 화학소재. (커버리지 있음)

## 8. OSAT (후공정 조립·테스트) 및 후공정 부품

한국 OSAT 글로벌 점유율 ~4.3%(5위). [디지털투데이 - HBM 효과 OSAT](https://www.digitaltoday.co.kr/news/articleView.html?idxno=528364), [디일렉 - OSAT 점유율](https://www.thelec.kr/news/articleView.html?idxno=28972)

- **하나마이크론 (067310)**: 패키징·실리콘 재료, 베트남 증설.
- **SFA반도체 (036540)**: 메모리 패키징·테스트(BUMP~TEST 일관).
- **두산테스나 (131970)**: 시스템반도체 웨이퍼 테스트 전문.
- **LB세미콘 (061970)**: DDI 등 시스템반도체 패키징·테스트. (커버리지 있음)
- **네패스 (033640)**: 팬아웃(FO-WLP/PLP) 첨단 패키징.

후공정 **부품**(테스트 소켓·프로브카드) — Final 테스트 소켓은 국내 기업이 지배. [한경 - ISC HBM 소켓](https://www.hankyung.com/article/202412222464i), [디일렉 - 티에스이](https://www.thelec.kr/news/articleView.html?idxno=8322)

- **리노공업 (058470)**: 테스트 핀·소켓(릴레이 소켓) 세계 강자. (커버리지 있음)
- **ISC (095340)**: 실리콘러버 소켓 세계 1위, HBM 테스트 소켓.
- **티에스이 (131290)**: 테스트 소켓·프로브카드.
