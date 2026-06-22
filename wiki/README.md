---
type: index
updated: 2026-06-22
---

# wiki — LLM이 관리하는 지식 레이어

`raw/`의 불변 원본 위에서, 노트를 **가로지르는** 개념·맥락·기업 분석을 관리하는 곳.
운영 규칙은 [`../schema/CLAUDE.md`](../schema/CLAUDE.md) 참고.

## 구성

| 폴더 | 내용 |
| --- | --- |
| `cov/` | 개별 기업 분석 노트 (Company Overview). 섹터 인덱스: [cov/README](cov/README.md) |
| `Geopolitics/` | 지정학 개념 노트 |
| `Economics/` | 경제 개념 노트 |
| `Accounting/` | 회계·금융상품 개념 노트 |
| `Venture Capital/` | 스타트업·VC 개념 노트 |
| (루트) | 노트를 가로지르는 종합(synthesis) 페이지 |

> 개념 노트와 기업 노트는 옵시디언 위키링크(파일명 기준)로 연결되므로, 폴더 위치와 무관하게 `[[노트 제목]]`으로 해소된다.

## 종합 페이지 (Synthesis)

- [[중동-에너지-호르무즈]] — 중동 지정학 → 유가 → 한국 산업(정유·조선·방산)으로 이어지는 인과 사슬. `news-scrap`, `strategic-thinking`, `wiki/Geopolitics`, `stock-market`를 가로지름.

## 관련 raw 레이어

- `raw/moc/` — 여러 개념을 묶는 인덱스/지도(Map of Content) 페이지. 예: [[미중 패권 경쟁]], [[중동 분쟁의 역사]]
- `raw/news-scrap/`, `raw/strategic-thinking/`, `raw/startup-innovation/`, `raw/stock-market/<섹터>/` — 불변 원본 소스

## 유지보수 메모

- raw 노트가 추가·이동되면 관련 페이지의 위키링크와 `sources`, `updated`를 갱신한다.
- 깨진 위키링크는 즉시 고친다.
- 새 종합 페이지는 반드시 이 허브에서 링크한다.
