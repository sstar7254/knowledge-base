# knowledge-base — 운영 규칙 (schema)

이 저장소는 Andrej Karpathy의 패턴을 따르는 개인 *second brain*이다.
원본 자료를 불변으로 보존하면서, 그 위에 LLM이 관리하는 지식 레이어를 쌓는다.

## 1. 3계층 아키텍처

| 계층 | 폴더 | 성격 | 누가 쓰는가 |
| --- | --- | --- | --- |
| **raw** | `raw/` | 불변(immutable) 원본 소스 | 사람이 추가/이동, LLM은 **읽기 전용** |
| **wiki** | `wiki/` | 개념 노트 · 기업 분석(cov) · 종합 페이지(moc) | **LLM이 유지·관리** |
| **schema** | `schema/` | 조직 규칙 (이 파일) | 사람 + LLM 합의 |

핵심 원칙: **raw는 진실의 원천(source of truth), wiki는 그 위에서 파생된 합성물(derived).**

## 2. `raw/` — 불변 원본

- **원본 소스의 본문은 수정하지 않는다.** 오탈자조차 고치지 않는다.
- 파일을 지우거나 옮기는 일은 사람이 결정한다. LLM이 멋대로 재배치하지 않는다.
- 새 소스는 아래 분류의 알맞은 하위 폴더에 넣는다.

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
```

### raw 명명 규칙

- **news-scrap**: `(날짜)_(제목 또는 키워드).md` 형식. 제목/키워드가 없으면 날짜만 쓴다.
  출처(URL·매체명)는 본문 frontmatter의 `source:` 필드로 보존한다 (폴더로 분류하지 않는다).
- **stock-market 섹터 폴더**: 섹터 번호·점·공백 없이 클린한 이름을 쓴다 (예: `09. Finance` → `Finance`).
  섹터 자체의 산업 리서치만 여기 두고, 개별 기업 노트는 `wiki/cov/`로 보낸다.

### raw 노트의 frontmatter 관습 (관찰된 것)

```yaml
---
type: news-scrap | concept | report | ...
source: https://...        # 출처 URL 또는 매체명
date: YYYY-MM-DD
tags:
- 계층형/태그
---
```

## 3. `wiki/` — LLM이 관리하는 레이어

목적: 흩어진 raw 노트를 **가로질러** 개념·맥락을 잇고, 기업 분석을 한곳에서 관리한다.

```
wiki/
├─ cov/                 # 개별 기업 분석 (티커_회사명.md)
├─ geopolicits/          # 주제 별 개념노트
├─ accounting/
├─ venture-capital/
└─ moc/                 # 개념을 묶는 인덱스(Map of Content). 노트를 가로지르는 종합 페이지
```

규칙:

1. **개념 노트는 `wiki/(하위 분류)` 아래에 둔다** (Geopolitics / Accounting / Venture Capital).
   작성 시 참조한 외부 URL을 확인할 수 있는 경우 `sources` 필드에 명시한다.
   참조한 `raw/` 파일은 반드시 위키링크(`[[노트 제목]]`)로 연결한다.
   하위 분류는 노트의 내용에 따라 가장 밀접한 폴더를 새롭게 생성할 수 있다. 단, 가장 밀접한 하나의 분류에만 포함한다.
3. **기업 분석 노트(cov)는 `wiki/cov/`에 평탄하게 둔다.** 파일명은 `티커_회사명.md`.
   섹터 분류는 `wiki/cov/README.md` 인덱스로 유지한다.
4. **모든 사실 진술은 raw로 거슬러 올라갈 수 있어야 한다.** 출처가 되는 raw 노트를 위키링크로 연결한다.
   위키링크는 파일명 기준으로 해소되므로 폴더 위치와 무관하게 작동한다.
5. **종합(moc) 페이지**는 `wiki/` 루트에 두고 `wiki/README.md` 허브에서 링크한다.
   상단에 최소 frontmatter를 둔다:
   ```yaml
   ---
   type: synthesis | index | concept
   updated: YYYY-MM-DD
   sources:
   - raw/...        # 종합·참조한 raw 노트
   ---
   ```
6. raw가 바뀌면(노트 추가·이동) 관련 wiki 페이지의 링크와 `updated`를 갱신한다. 깨진 링크는 고친다.

## 4. 작업 흐름 (LLM이 호출됐을 때)

1. 요청을 읽고, 관련 raw 노트를 **검색**한다 (제목·태그·본문).
2. raw 원본 본문은 읽기만 한다. 종합·정리·연결이 필요하면 결과를 **wiki에 쓴다**.
3. raw 자료의 구조가 정말로 바뀌어야 한다면(분류 변경 등) 먼저 사람에게 확인한다.
4. 분류 규칙 자체가 바뀌면 이 `schema/CLAUDE.md`를 함께 업데이트한다.

## 5. 제외 대상 (`.gitignore`)

옵시디언/MakeMD의 캐시·작업상태(`.obsidian/`, `.space/`, `*.mdb`), OS·에디터 노이즈, 도구 스크래치는 추적하지 않는다. 이들은 지식이 아니라 도구 상태다.

## 6. 사실 정확성 원칙 (모든 쓰기 작업에 적용)

- 불확실하거나 검증 불가한 내용은 반드시 ⚠️ 를 붙인다.
- 기관명·통계·정책 등 구체적 사실은 웹 검색으로 확인 후 출처를 함께 기재한다.
- 검색으로도 확인이 불충분하면 추정하지 않고 **(확인 필요)** 로 명시한다.
- raw 신규 파일 생성 시: 출처 URL 또는 검색일을 frontmatter에 기록한다.
