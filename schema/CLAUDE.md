# knowledge-base — 운영 규칙 (schema)

이 저장소는 Andrej Karpathy의 패턴을 따르는 개인 *second brain*이다.
원본 자료를 불변으로 보존하면서, 그 위에 LLM이 관리하는 지식 레이어를 쌓는다.

## 1. 3계층 아키텍처

| 계층 | 폴더 | 성격 | 누가 쓰는가 |
| --- | --- | --- | --- |
| **raw** | `raw/` | 불변(immutable) 원본 소스 | 사람만 추가/이동, LLM은 **읽기 전용** |
| **wiki** | `wiki/` | 노트를 가로지르는 개념·연결 페이지 | **LLM이 유지·관리** |
| **schema** | `schema/` | 조직 규칙 (이 파일) | 사람 + LLM 합의 |

핵심 원칙: **raw는 진실의 원천(source of truth), wiki는 그 위에서 파생된 합성물(derived).**
wiki는 언제든 raw로부터 다시 만들어낼 수 있어야 한다. 그 반대는 성립하지 않는다.

## 2. `raw/` — 불변 원본

- **절대 내용을 수정하지 않는다.** 오탈자조차 고치지 않는다. 원본은 원본 그대로 둔다.
- 파일을 지우거나 옮기는 일은 사람이 결정한다. LLM이 멋대로 재배치하지 않는다.
- 새 소스가 들어오면 아래 분류 체계의 알맞은 하위 폴더에 넣는다.

### 현재 분류 (raw 하위 폴더)

```
raw/
├─ news-scrap/          # 일자별 뉴스 스크랩 (중동·에너지 등)
│  └─ 한국경제/          # 한국경제 신문 일일 스크랩
├─ strategic-thinking/  # 거시·지정학 장문 에세이 (1-x, 2-x 시리즈)
├─ startup-innovation/  # 스타트업·VC 실무 자료
├─ stock-market/        # 섹터별 투자 리서치
│  ├─ 00. Macro/
│  ├─ 01. AI_Semiconductor_Robotics/
│  ├─ 02. Cosmetics/
│  ├─ 03. Medical_Pharma/
│  ├─ 04. Energy/
│  ├─ 05. Auto_Ship_Buildings/
│  ├─ 06. Aerospace_Defense/
│  ├─ 07. Staples_Retail/
│  ├─ 08. Entertainment_Leisure/
│  ├─ 09. Finance/
│  │  └─ .../Company Overview/   # 개별 기업 노트 (티커_회사명.md)
└─ concepts-vault/      # 재사용 가능한 개념 정의
   ├─ Accounting/
   ├─ Economics/
   ├─ Geopolitics/  (+ Index/)
   └─ Venture Capital/
```

- 기업 노트 파일명 규칙(기존 관습 유지): `티커_회사명.md` (예: `000660_SK 하이닉스.md`, `NVO_Novo Nordisk.md`).
- 개념 노트 파일명: `한글명 (영문/원어).md` (예: `호르무즈 해협 (Strait of Hormuz).md`).
- `.gdoc` 파일은 Google Docs 원본을 가리키는 포인터다. 로컬에 본문이 없는 소스이므로 raw의 일부로 보존한다.

### raw 노트의 프론트매터 관습 (관찰된 것, 강제 아님)

```yaml
---
type: concept            # concept | report | ...
tags:
- Geopolitics/ME/L3      # 계층형 태그
created: 2026-03-03
edited: 2026-03-31
aliases:
- Strait of Hormuz
---
```

LLM은 이 관습을 **읽어서 활용**하되, raw 파일에 써넣지 않는다.

## 3. `wiki/` — LLM이 관리하는 연결 레이어

목적: 흩어진 raw 노트를 **가로질러** 개념과 맥락을 잇는다. 단순 복사가 아니라 *종합(synthesis)* 이다.

규칙:

1. **모든 주장은 raw로 거슬러 올라갈 수 있어야 한다.** wiki 페이지의 사실 진술에는 출처가 되는 raw 노트를 옵시디언 위키링크 `[[노트 제목]]` 또는 상대경로로 연결한다.
2. wiki는 raw로부터 **재생성 가능**해야 한다. wiki에만 존재하는 1차 사실(원본 데이터)을 만들지 않는다.
3. 페이지 종류:
   - **MOC (Map of Content)**: 한 주제로 들어가는 관문. 관련 raw 노트 묶음 + 짧은 맥락.
   - **개념 연결 페이지**: 여러 섹터/노트에 걸친 개념이 어떻게 연결되는지 서술 (예: 호르무즈 봉쇄 → 유가 → 정유/조선/방산).
   - **인덱스**: 자동/반자동으로 갱신되는 목록.
4. 페이지 상단에 최소 프론트매터를 둔다:
   ```yaml
   ---
   type: moc | synthesis | index
   updated: YYYY-MM-DD
   sources:            # 이 페이지가 종합한 raw 노트들
   - raw/...
   ---
   ```
5. raw가 바뀌면(노트 추가·이동) 관련 wiki 페이지의 링크와 `updated`를 갱신한다. 깨진 링크는 고친다.
6. 새 wiki 페이지는 `wiki/`에 두고 반드시 `wiki/README.md`(허브)에서 링크한다.

## 4. 작업 흐름 (LLM이 호출됐을 때)

1. 요청을 읽고, 관련 raw 노트를 **검색**한다 (제목·태그·본문).
2. raw는 읽기만 한다. 종합·정리·연결이 필요하면 결과를 **wiki에 쓴다**.
3. raw 자료의 구조가 정말로 바뀌어야 한다면(분류 변경 등) 먼저 사람에게 확인한다.
4. 분류 규칙 자체가 바뀌면 이 `schema/CLAUDE.md`를 함께 업데이트한다.

## 5. 제외 대상 (`.gitignore`)

옵시디언/MakeMD의 캐시·작업상태(`.obsidian/`, `.space/`, `*.mdb`), OS·에디터 노이즈, 도구 스크래치는 추적하지 않는다. 이들은 지식이 아니라 도구 상태다.
