---
type: news-scrap
date: 2026-06-24
updated: 2026-06-24
tags:
  - supply-chain/logistics
  - ai
---

**개요**

Amazon이 풀필먼트 센터 내부에서 인력 배치를 자동으로 재조정하는 새로운 시스템 'Full Facility Load Balancing'(FFLB)을 테스트하고 있다. 기존 자동화가 패키지·화물의 흐름을 최적화하는 데 집중했다면, FFLB는 그 초점을 인력(labor) 자체로 옮긴 시스템이라는 점이 핵심이다. 이 시스템은 약 3분 간격으로 시설 전체의 작업 부하를 재계산해, 어느 공정에 사람이 남고 모자라는지를 판단한 뒤 작업자를 다른 역할로 자동 재배치하도록 설계됐다.

**From packages to labor**

기존 Amazon의 로봇·자동화 투자는 주로 컨베이어, 분류 시스템, 로봇팔 등 물리적 화물 흐름을 다루는 데 집중돼 있었다. FFLB는 결이 다르다. 사람이 어디서 얼마나 필요한지를 알고리즘이 실시간으로 계산하고, 그 결과에 따라 매니저의 판단을 거치지 않고 작업자를 다른 공정으로 이동시킨다. 사내 문서는 이 시스템의 목적을 다음과 같이 설명한다.

> "remove the dependency on manual staffing decisions."

즉, 어느 라인에 몇 명을 배치할지를 매니저가 경험과 직감으로 정하던 방식에서, 알고리즘이 실시간 데이터를 기반으로 정하는 방식으로 전환하려는 시도다.

**'Largest labor automation opportunity'**

사내 자료에 따르면 Amazon은 Container Build(컨테이너에 화물을 적재하는 공정)를 FFLB가 공략할 "가장 큰 단일 인력 자동화 기회"로 지목했다. 시스템은 다음과 같이 동작한다.

> "FFLB dynamically calculates the recommended headcount for different process segments and automatically assigns and balances associates between roles."

이 표현대로, FFLB는 공정 구간별로 권장 인원을 동적으로 산출하고, 그 수치에 따라 작업자를 역할 간에 자동으로 배분·재배치한다. Amazon은 내부적으로 이 시스템이 연간 약 1억 9,300만 달러, 690만 시간의 인건비를 절감할 수 있다고 추산한 것으로 알려졌으나, Amazon 측은 이 구체적 수치를 공식적으로는 인정하지 않고 있다(미확인·논쟁적 수치).

**'No WIP'**

FFLB가 지향하는 운영 상태는 "No WIP"(No Work-In-Progress), 즉 공정 중간에 처리되지 않은 화물이 쌓여 대기하는 상태를 최소화하는 것이다. 사람을 화물이 막히는 지점으로 실시간 재배치함으로써 라인 전체의 흐름을 끊김 없이 유지하려는 목표다. 이는 전통적인 린(Lean) 생산 방식에서 재고·대기를 낭비로 보는 사고와 같은 방향이지만, FFLB는 이를 인적 자원 배치 차원에서 알고리즘으로 자동화한다는 점에서 차이가 있다.

**Deployment plans**

Amazon은 FFLB를 올해 안에 ARS(Amazon Robotics System)를 사용하는 북미 전역의 로보틱스 풀필먼트 센터로 확대 배포할 계획인 것으로 알려졌다. 다만 이 시스템이 매니저의 인력 배치 권한을 알고리즘에 넘기는 구조이다 보니, 현장 도입 과정에서 매니저·작업자 양쪽의 반발과 적응 마찰이 예상된다.

## Key Takeaways

1. FFLB는 약 3분 주기로 시설 전체 인력 배치를 재계산하는 시스템으로, Amazon 자동화의 초점이 '화물'에서 '인력'으로 이동했음을 보여준다. 사내 추산 연간 1억 9,300만 달러·690만 시간 절감액은 Amazon이 공식 확인하지 않은 수치다.
2. Container Build가 "가장 큰 단일 인력 자동화 기회"로 지목됐고, FFLB는 올해 안에 ARS를 쓰는 북미 전역 로보틱스 풀필먼트 센터로 확대될 예정이다.
3. 알고리즘이 매니저의 인력 배치 권한을 대신하는 '알고리즘 관리(algorithmic management)'가 현장 도입 마찰을 일으킬 수 있으며, 이는 Amazon 창고 노동·규제 전반에 대한 더 큰 감시 흐름과 맞물려 있다.

## 추가 조사 (Research)

### 1. FFLB의 3분 주기 재계산과 화물→인력 초점 이동, 미확인 절감액

- 맥락/배경: Amazon은 최근 몇 년간 풀필먼트 센터 자동화를 빠르게 확대해왔다. Amazon 공식 발표에 따르면 2025년 기준 전 세계 운영망에 100만 대 이상의 로봇이 배치돼 있으며, 새로운 AI 기반 로봇 운영체제 'DeepFleet'을 도입해 로봇 이동 효율을 약 10% 개선했다고 밝혔다 [Amazon 공식 블로그 — aboutamazon.com](https://www.aboutamazon.com/news/operations/amazon-million-robots-warehouse-deepfleet). CNBC 역시 이 100만 대 로봇 마일스톤과 DeepFleet 발표를 보도했다 [CNBC](https://www.cnbc.com/2025/10/15/amazon-warehouse-robots-deepfleet.html).
- 원인: 화물 흐름 자동화(분류, 컨베이어, 로봇팔)는 이미 상당 부분 고도화된 반면, 인력 배치는 여전히 매니저의 경험적 판단에 의존하는 영역으로 남아 있었다. FFLB는 이 마지막 비효율 영역을 알고리즘으로 메우려는 시도로 해석된다.
- business impact: 사내 추산 연간 1억 9,300만 달러·690만 시간 절감은 (확인 필요) 사항으로, Amazon이 외부에 공식 인정한 수치가 아니다. 다만 이는 Amazon이 인건비를 핵심 비용 절감 축으로 보고 있음을 시사한다. 같은 맥락에서 뉴욕타임스가 입수한 내부 문서를 인용한 보도들은 Amazon이 자동화를 통해 향후 미국 내 채용을 줄이고 노동비를 절감하려 한다고 전했다 — GeekWire는 해당 NYT 보도를 인용해 Amazon이 자동화로 향후 10년간 약 16만 개 일자리 채용을 회피할 수 있다는 내부 추산을 보도했다고 전했다 [GeekWire](https://www.geekwire.com/2025/amazon-automation-jobs-report/). Interesting Engineering과 Techstrong.ai도 같은 NYT 보도를 인용해 60만 개 일자리, 자동화율 75%, 124억 달러(약 12.6B) 규모의 잠재적 절감 추산을 전했다 [Interesting Engineering](https://interestingengineering.com/), [Techstrong.ai](https://techstrong.ai/) (이 수치들은 NYT의 1차 보도를 재인용한 2차 출처들로, 정확한 액수는 매체별로 다르게 인용되고 있어 **(확인 필요)**로 표시한다).
- supply chain impact: 인력을 화물 흐름에 맞춰 실시간 재배치하는 구조는 결품·병목 발생 시 대응 속도를 높일 수 있다는 점에서 운영 유연성을 높인다. 그러나 동시에 인력 배치 의사결정이 매니저 현장 판단에서 알고리즘 산출값으로 옮겨가면서, 현장 예외 상황(부상, 컨디션, 숙련도 차이 등)에 대한 대응력이 떨어질 위험도 존재한다.

### 2. Container Build 자동화 확대와 ARS 기반 북미 전역 배포 계획

- 맥락/배경: Amazon Robotics System(ARS)을 사용하는 로보틱스 풀필먼트 센터는 이미 분류·운반 단계에서 높은 자동화 수준을 갖추고 있다. Container Build(트레일러/컨테이너 적재) 공정은 상대적으로 사람 의존도가 높게 남아있던 영역이다.
- 원인: 적재 공정은 화물 크기·형태가 다양해 완전 로봇화가 어려운 대신, 인력 배치 최적화로 효율을 끌어올릴 여지가 큰 공정으로 평가된다. 이 때문에 Amazon 내부적으로 "가장 큰 단일 인력 자동화 기회"로 지목된 것으로 보인다.
- business impact: 북미 전역 ARS 기반 시설로의 확대는 Amazon이 이 시스템의 효과를 충분히 검증했다고 판단했음을 시사하며, 성공적으로 안착하면 동종 물류업체들에도 유사한 인력 최적화 알고리즘 도입 압력으로 이어질 수 있다.
- supply chain impact: Container Build 단계의 효율화는 트레일러 적재율과 출고 속도에 직접 영향을 미쳐, 라스트마일 이전 단계의 처리 능력(throughput)을 끌어올릴 수 있다. 다만 확대 속도가 빠를 경우 현장 트레이닝·적응 기간이 충분히 확보되지 않으면 초기 오류율이 높아질 위험이 있다.

### 3. 알고리즘 관리에 대한 매니저 권한 침해와 노동·규제 감시 강화

- 맥락/배경: 알고리즘이 인력 배치·성과 평가까지 관여하는 '알고리즘 관리(algorithmic management)'는 물류·창고업계 전반에서 논쟁거리로 떠올랐다. The Register는 Amazon을 포함한 물류기업들의 알고리즘 관리 방식에 대한 비판적 분석을 보도했다 [The Register](https://www.theregister.com/).
- 원인: 작업 속도·인력 배치 결정권이 매니저에서 알고리즘으로 넘어가면서, 현장 매니저는 재량권 축소를, 작업자는 예측 불가능한 역할 재배치와 작업 강도 강화를 우려하게 된다.
- business impact: 미국 상원 보건교육노동연금위원회(Senate HELP Committee, Bernie Sanders 주도)는 Amazon 창고의 부상률·작업 강도와 관련한 조사 보고서를 발표한 바 있다 [Senate HELP Committee 조사 보고서](https://www.help.senate.gov/) (정확한 보고서 링크는 (확인 필요)). 또한 캘리포니아주는 창고 할당량(quota) 관련 노동법을 시행 중이며, Amazon은 캘리포니아주로부터 약 600만 달러 규모의 벌금을 부과받은 사례가 Bloomberg Law를 통해 보도됐다 [Bloomberg Law](https://news.bloomberglaw.com/) (구체 액수·사건 경위는 **(확인 필요)**). 이러한 규제·소송 리스크는 FFLB 같은 알고리즘 인력관리 시스템의 확대 속도에 제약 요인으로 작용할 수 있다.
- supply chain impact: 노동 분쟁·규제 대응 비용이 늘어나면 자동화 확대의 ROI 계산에 새로운 변수가 추가된다. 동일한 FFLB 관련 보도는 Benzinga에서도 교차 확인됐다 [Benzinga](https://www.benzinga.com/).

### 출처 (Sources)
- [Amazon 공식 블로그 — 100만 로봇·DeepFleet](https://www.aboutamazon.com/news/operations/amazon-million-robots-warehouse-deepfleet)
- [CNBC — Amazon DeepFleet 보도](https://www.cnbc.com/2025/10/15/amazon-warehouse-robots-deepfleet.html)
- [GeekWire — Amazon 자동화·고용 영향 보도](https://www.geekwire.com/2025/amazon-automation-jobs-report/)
- [Interesting Engineering](https://interestingengineering.com/)
- [Techstrong.ai](https://techstrong.ai/)
- [The Register — 알고리즘 관리 비판](https://www.theregister.com/)
- [Senate HELP Committee](https://www.help.senate.gov/)
- [Bloomberg Law](https://news.bloomberglaw.com/)
- [Benzinga](https://www.benzinga.com/)

---
출처: Business Insider (기사 원문 URL 미확인), 2026-06-24
