---
type: research
date: 2026-09-04
updated: 2026-09-04
tags:
  - ai
  - semiconductor
---

# research-NVDA-GTC 2026 하드웨어 전략

> Constellation Research의 GTC 2026 리뷰 기사 한 건을 정리한 소스 다이제스트다. Larry Dignan,
> "Nvidia GTC 2026: Nvidia's hardware strategy goes beyond GPU in AI inference pivot",
> Constellation Research, 2026-03-16. 검색·열람일 2026-09-04.
> 수치·제품명·인용은 기사에 실린 것을 옮긴 것이며, 회사 공시로 대조하지 않았다.

## 1. 기사의 뼈대

기사는 GTC 2026에서 엔비디아가 **GPU 단품 회사에서 벗어나 CPU·네트워킹·스토리지·추론 전용 프로세서까지
포함한 AI 인프라 스택 전체 공급자로 자기 규정을 바꿨다**고 정리한다. 황 젠슨의 표현을 그대로 인용하면
엔비디아는 "세계 최초의 수직 통합이면서 수평 개방된 회사(the world's first vertically integrated,
but horizontally open company)"다.

## 2. 발표된 제품 — Vera Rubin AI Platform

**연산 (CPU·GPU·전용 프로세서)**

- NVIDIA Vera CPU — 88개 커스텀 "Olympus" 코어, Spatial Multithreading 적용
- NVIDIA Rubin GPU
- NVIDIA Groq 3 LPU — **2025년 12월 그록 인수를 통해 확보한 계열**

**네트워킹·스토리지**

- NVLink 6 Switch
- ConnectX-9 SuperNIC
- BlueField-4 DPU
- Spectrum-6 Ethernet switch

기사는 ConnectX SuperNIC과 Spectrum 이더넷 스위치가 **과거 Mellanox 인수로 확보한 자산의 현재
브랜드**임을 명시한다. 즉 이번 발표의 네트워킹 축은 2020년 인수의 연장선이고, LPU 축은 2025년
인수의 연장선이다.

## 3. 랙 구성 5종 (2026년 하반기 공급 예정)

| 랙 | 구성 | 기사에 제시된 성능 |
|---|---|---|
| Vera Rubin NVL72 | Rubin GPU 72 + Vera CPU 36 | 와트당 추론 처리량 10배 |
| Vera CPU Rack | 액체냉각 CPU 256개 | 강화학습(RL)용 |
| Groq 3 LPX Rack | LPU 프로세서 256개 | **메가와트당 추론 처리량 35배** |
| BlueField-4 STX Storage Rack | 스토리지 | KV 캐시 추론 처리량 5배 |
| Spectrum-6 SPX Ethernet Rack | 이더넷 | 고처리량·저지연 연결 |

## 4. Vera CPU 세부 사양

- 기존 CPU 대비 성능 50% 향상
- 범용 CPU 대비 효율 2배
- 메모리 대역폭 1.2 TB/s (LPDDR5X)
- NVLink-C2C 기반 coherent 대역폭 1.8 TB/s
- 동시 CPU 환경 22,500개 이상 지원

## 5. 황 젠슨 발언 (기사 인용)

- "우리는 플랫폼으로 기술을 이야기할 것이다. 엔비디아에는 플랫폼이 셋 있는데 다들 하나만 이야기한다고
  생각할 것이다. 이제 **AI Factory**라는 새 플랫폼이 생겼다."
- "엔비디아는 세계 최초의 **수직 통합이면서 수평 개방된** 회사다."
- "우리는 그 변곡점에 도달했다. **추론 변곡점이 왔다(The inference inflection has arrived).**"

## 6. 시장 규모와 파트너

- **2027년까지 AI 수요 1조 달러** — 직전 GTC의 데이터센터 전망 대비 2배로 상향
- 신규 칩 7종이 양산 단계
- 하이퍼스케일러 파트너: 알리바바, 바이트댄스, 메타, OCI, CoreWeave, Lambda
- OEM: 델, HPE, 레노버, 슈퍼마이크로, ASUS, QCT
- 생태계 협력사: 구글 클라우드, IBM, 네슬레, NTT Data, AWS, 마이크로소프트 애저

## 7. DSX AI Factory 소프트웨어 모듈 4종

| 모듈 | 역할 |
|---|---|
| DSX Max-Q | 와트당 토큰 성능 최적화 |
| DSX Flex | 전력망 서비스 연계 |
| DSX Exchange | IT·운영기술(OT) 신호 통합 |
| DSX Sim | 디지털 트윈 검증 |

성능 목표로는 토큰 생성 최대 15배 개선, 멀티에이전트 상호작용을 위한 10배 큰 모델 지원이 제시됐다.

## 8. 기사에 실린 애널리스트 코멘트

- **R "Ray" Wang (Constellation 대표)** — 엔비디아가 스택 위로 올라가면서 경쟁 포지션을 강화하는 한편
  **독점 우려를 낳을 위험**이 있으며, 동시에 표준화를 가능하게 한다고 평했다. LPU 확장과
  멀티에이전트 소프트웨어 층 전략을 주목 지점으로 꼽았다.
- **Holger Mueller (Constellation 애널리스트)** — 소버린 AI가 엔비디아 하드웨어 가용성에 종속되는
  문제와, 에이전트 속도에 대한 경쟁 벤치마크의 필요성을 지적했다.

---

출처: Larry Dignan, "Nvidia GTC 2026: Nvidia's hardware strategy goes beyond GPU in AI inference pivot", Constellation Research, 2026-03-16 — https://www.constellationr.com/insights/news/nvidia-gtc-2026-nvidias-hardware-strategy-goes-beyond-gpu-ai-inference-pivot (열람 2026-09-04)
