# knowledge-base

Andrej Karpathy의 패턴을 따르는 개인 *second brain*. 3계층으로 구성한다.

| 계층 | 폴더 | 성격 |
| --- | --- | --- |
| **raw** | [`raw/`](raw/) | 불변(immutable) 원본 소스 + 인덱스(MOC) — 사람이 관리, LLM은 읽기 전용 |
| **wiki** | [`wiki/`](wiki/) | 개념 노트 · 기업 분석(cov) · 종합 페이지 — LLM이 유지·관리 |
| **schema** | [`schema/`](schema/CLAUDE.md) | 조직 규칙 |

## 구조

```
raw/
├─ news-scrap/          # 뉴스 스크랩 ((날짜)_(제목).md)
├─ startup-innovation/  # 스타트업·VC 관련 자료
├─ stock-market/        # 섹터별 산업 리서치 (Macro, Energy, Finance ...)
|  ├─ AI_semiconductor_robotics/
|  ├─ aerospace_defense/
|  ├─ auto_ship_buildings/
|  ├─ cosmetics/
|  ├─ energy/
|  ├─ macro/
|  └─ medical_pharma/
└─ strategic-thinking/  # 거시·지정학 에세이

wiki/
├─ wiki-map.md          # 모든 위키를 잇는 허브 인덱스 (도메인별 링크)
├─ cov/                 # 개별 기업 분석 (티커_회사명.md)
├─ geopolitics/         # 주제 별 개념노트
├─ accounting/
└─ moc/                 # 개념을 묶는 인덱스(Map of Content). 노트를 가로지르는 종합 페이지.
```

자세한 운영 규칙은 [`schema/CLAUDE.md`](schema/CLAUDE.md)를 참고한다.
