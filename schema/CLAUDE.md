# knowledge-base — 운영 규칙 (schema)

이 저장소는 Andrej Karpathy의 패턴을 따르는 개인 *second brain*이다.
원본 자료를 불변으로 보존하면서, 그 위에 LLM이 관리하는 지식 레이어를 쌓는다.

## 0. Git conventions
- Branch naming: feat/short-description, fix/issue-number (no random name)
- Never commit directly to main

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
- 새 소스는 아래 분류의 알맞은 하위 폴더에 넣는다. 필요하다면 새로운 디렉토리를 생성할 수 있다. 새로운 디렉토리를 생성한 경우 반드시 `CLAUDE.md`와 `README`의 파일 트리를 함께 수정한다.
- LLM은 최초 파일의 생성까지 허용한다. 이때 포함되는 내용은 원본 소스를 보존하는 성격의 사실/자료 요약이다. 반드시 매체/출처/url을 병기한다.

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
├─ logistics-tech-startup/
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
status: inbox | used        # 아래 참고
---
```

**status 필드 로직**: 새 raw 노트는 기본값 `status: inbox`로 둔다(필드를 생략해도 inbox로 간주).
이 raw 노트를 출처로 `/sc-letter` 글을 작성하면, 해당 raw 노트의 `status`를 `used`로 변경한다.

### LLM이 리서치를 raw에 저장할 때 (소스 다이제스트 원칙)

기본은 §1대로 raw는 사람이 추가하는 영역이다. **사람이 명시적으로 "raw에 저장"을 지시한 경우에
한해** LLM이 raw에 파일을 만든다. 이때 다음을 지킨다.

- raw에는 **참고한 기사·자료의 요약(소스 다이제스트)만** 둔다. 항목마다 **매체명·URL·일자**를 병기한다.
- **해석·비교·결론·전략 분석 같은 파생물은 raw에 쓰지 않는다.** 그것은 wiki의 몫이다(§1 derived).
- 주제별 하위 폴더 `raw/<주제>/`를 만든다. 시장·동향 개요는 `_개요...` 또는 `_시장개요 참고자료.md`,
  대상(기업·인물 등)별 자료는 `(대상) 참고자료.md` 형식으로 평탄하게 둔다.
- frontmatter `date`에는 **검색일**을, `source`에는 대표 출처(또는 `다수`)를 기록한다.

## 3. `wiki/` — LLM이 관리하는 레이어

목적: 흩어진 raw 노트를 **가로질러** 개념·맥락을 잇는다.

```
wiki/
├─ wiki-map.md          # 모든 위키를 잇는 허브 인덱스 (도메인별 인덱스 링크)
├─ cov/                 # 개별 기업 분석 (티커_회사명.md)
├─ cross-border/        # 도메인을 가로지르는 종합(synthesis) 노트 (에너지·물질·통화 lens)
├─ geopolitics/         # 주제 별 개념노트
├─ accounting/
├─ logistics/
└─ supply-chain/        # SCM/CPIM 개념노트
```

규칙:

1. **개념 노트는 `wiki/(하위 분류)` 아래에 둔다** (Geopolitics / Accounting / Venture Capital).
   작성 시 참조한 외부 URL을 확인할 수 있는 경우 `sources` 필드에 명시한다.
   참조한 `raw/` 파일은 반드시 위키링크(`[[노트 제목]]`)로 연결한다.
   하위 분류는 노트의 내용에 따라 가장 밀접한 폴더를 새롭게 생성할 수 있다. 단, 가장 밀접한 하나의 분류에만 포함한다.
2. **상장 기업 커버리지(cov)는 `wiki/cov/`에 평탄하게 둔다.** 파일명은 `티커_회사명.md`.
   섹터 분류는 `wiki/cov/README.md` 인덱스로 유지한다.
3. **여러 개별 대상(스타트업·기업·인물 등)의 분석이 한 주제로 묶이면 `wiki/<주제>/` 폴더에 평탄하게
   둔다** (예: `wiki/logistics/`). 파일명은 `대상명 (구분).md`처럼 사람이 식별하기 쉽게 짓고, 각 노트는
   ① 대응하는 raw 소스 다이제스트로 위키링크하고 ② 사실 진술마다 인라인 출처를 병기한다.
   (티커가 있는 상장 기업 커버리지는 cov, 그 외 주제별 분석은 이 규칙을 따른다.)
4. **모든 사실 진술은 raw로 거슬러 올라갈 수 있어야 한다.** 출처가 되는 raw 노트를 위키링크로 연결한다.
   위키링크는 파일명 기준으로 해소되므로 폴더 위치와 무관하게 작동한다.
5. **종합 페이지(map)는 `wiki/(하위 분류)`에 둔다.** 파일명은 **_(prefix 필수)영문 kebab-case**로 짓는다
   (예: `_logistics-tech-startup-map.md`). 한 주제에 대해 **인덱스(목록·링크)와 종합(지형도·분석)을
   별도 파일로 쪼개지 말고 하나의 페이지로 병합**한다(별도 README/개념노트 남발 금지). 상단에 최소
   frontmatter를 둔다:
   ```yaml
   ---
   type: map | index | concept
   updated: YYYY-MM-DD
   ---
   ```
6. raw가 바뀌면(노트 추가·이동) 관련 wiki 페이지의 링크와 `updated`를 갱신한다. 깨진 링크는 고친다.

## 4. 작업 흐름 (/research 스킬 중심)

아래 8단계를 **순서대로 빠짐없이** 따른다. 이 절차가 정본이며, `skills/research/SKILL.md`는 이를 리서치 방법론과 함께 구체화한다.

1. **운영 규칙 로드** — 이 `schema/CLAUDE.md`를 먼저 읽어 구조·명명·쓰기 규칙을 확인한다.
2. **기존 자료 검색** — `raw/`에서 관련 노트를 제목·태그·본문으로 검색한다.
3. **리서치 계획 수립** — 관련 자료가 있으면 그것을 기반으로, 이미 있는 것과 부족한 것을 구분한 계획을 세운다.
4. **리서치 수행** — `skills/research/SKILL.md`의 방법론(`내부 진행 단계`·`핵심 규칙`)에 따라 웹 검색 기반 리서치를 수행한다.
5. **raw 저장** — 획득한 1차 자료는 `raw/`의 알맞은 하위 폴더에 출처 URL·매체명·검색일을 frontmatter에 병기하여 요약·저장한다(§2의 "최초 파일 생성" 규칙). 원본 보존용이며 해석·종합은 넣지 않는다.
6. **wiki 작성** — `raw/` 자료를 근거로 `wiki/`의 가장 밀접한 분류에 노트를 쓴다. 모든 사실 진술은 출처 raw 노트에 위키링크로 연결한다(§3).
7. **map 작성** — 6번에서 wiki 파일을 두 개 이상 작성한 경우, 이를 인덱싱하는 map을 작성한다. 
8. **wiki-map 연결** — 작성한 map(혹은 단일 wiki)를 허브 파일 `wiki/wiki-map.md`에 도메인별로 링크한다.
9. **파일트리 갱신** — 새로 생기거나 이동한 파일·디렉토리 path를 이 `schema/CLAUDE.md`와 `README.md`의 파일 트리에 모두 반영한다.

원칙(모든 단계에 적용):

- raw 원본 본문은 읽기만 한다. 기존 raw 파일의 본문 수정·삭제·이동은 사람이 결정한다(§2).
- raw 자료의 구조가 정말로 바뀌어야 한다면(분류 변경 등) 먼저 사람에게 확인한다.
- 분류 규칙 자체가 바뀌면 이 `schema/CLAUDE.md`를 함께 업데이트한다.

## 5. 제외 대상 (`.gitignore`)

옵시디언/MakeMD의 캐시·작업상태(`.obsidian/`, `.space/`, `*.mdb`), OS·에디터 노이즈, 도구 스크래치는 추적하지 않는다. 이들은 지식이 아니라 도구 상태다.

## 6. 사실 정확성 원칙 (모든 쓰기 작업에 적용)

- 불확실하거나 검증 불가한 내용은 반드시 ⚠️ 를 붙인다.
- 기관명·통계·정책 등 구체적 사실은 웹 검색으로 확인 후 출처를 함께 기재한다.
- 검색으로도 확인이 불충분하면 추정하지 않고 **(확인 필요)** 로 명시한다.
- raw 신규 파일 생성 시: 출처 URL 또는 검색일을 frontmatter에 기록한다.
