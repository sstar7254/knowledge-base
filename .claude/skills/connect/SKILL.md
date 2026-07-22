---
name: connect
description: "흩어진 노트 사이에 의미 있는 위키링크를 엮어 그래프뷰의 연결을 늘린다. 2단계로 작동한다 — (1) 새로 추가된 노트에 '## 관련 노트' 백링크를 달아 인접 노트끼리 잇고, (2) 저장소(raw+wiki) 전체를 가로지르는 새로운 high-level idea를 cross-border 노트로 합성한다. memory.md로 이미 처리한 노트를 기억해 신규 노트만 읽는다."
---

# /connect — 노트 연결 2단계 스킬

## 역할과 목표

너는 이 second-brain 저장소의 **연결 담당 사서**다. 목표는 흩어진 노트 사이에 *실제로 의미 있는*
위키링크(`[[파일명]]`)를 만들어, Obsidian 그래프뷰에서 주제·기업·개념이 군집을 이루게 하는 것이다.
연결은 두 방향으로 만든다.

- **Step 1 (수평 연결)** — 새로 들어온 노트를 인접한 기존 노트들과 `## 관련 노트` 백링크로 잇는다.
- **Step 2 (수직 연결)** — 저장소 전체를 관통하는 새 아이디어를 `wiki/`에 cross-border 종합 노트로 쓴다(평탄 배치, `type: idea`).

`/connect`는 기본적으로 **Step 1 → Step 2 순서로 둘 다** 실행한다.
범위를 좁히려면 `/connect step1`(수평 연결만) 또는 `/connect step2`(새 합성 노트만)로 호출한다.

---

## 사전 준비 (매 실행 공통)

1. **운영 규칙 로드** — `schema/CLAUDE.md`를 먼저 읽어 3계층 구조·명명·쓰기 규칙을 확인한다.
   특히 **`raw/`는 읽기 전용**이다. raw 본문은 절대 수정하지 않고, 링크는 `wiki/` 노트에서 raw로
   *나가는* 방향으로만 만든다(나가는 링크만으로도 그래프 엣지가 생긴다). `wiki/`는 편집 가능하다.
   **유일한 예외는 `raw/qa/`(질문-답변 노트)**: schema §2에 따라 qa 노트에는 frontmatter·`## 리서치`·
   `## 관련 노트`·`## 소화`의 AI 몫(심화질문·피드백) 추가·갱신이 허용된다(사람이 쓴 `## 메모`와
   `## 소화`의 요약·답변은 불변).
2. **메모리 로드** — `.claude/skills/connect/memory.md`를 읽어 이미 처리한 노트와 이미 만든
   cross-border 아이디어를 파악한다. 이 파일이 "전부 다시 읽지 않기 위한" 핵심 장치다.

### 공통 원칙 (두 단계 모두에 적용)

- **부분만 읽는다 (DO NOT READ FULL FILE).** 노트당 앞부분 ~30줄 정도만 읽고 *high-level idea*만
  잡는다. 정확한 사실 인용이 아니라 "이 노트가 무엇에 관한 것인가"를 아는 게 목적이다.
- **PERFECT를 추구하지 않는다.** 가장 신호가 강한 연결 위주로 만들고, 모든 쌍을 빠짐없이 잇지 않는다.
- 위키링크는 **파일명 기준**으로 해소되므로 폴더 위치와 무관하다. 링크 대상 파일명은 추측하지 말고
  실제 파일명과 정확히 일치시킨다(특수문자·괄호·공백 포함).
- 마무리 전 반드시 **링크 검증**을 돌려 깨진 링크가 없는지 확인한다(아래 `## 링크 검증` 참고).

---

## STEP 1 — 신규 노트 수평 연결 (`## 관련 노트`)

> proceed with making actual useful and meaningful connections between various topics, files and notes.
> read the content of the file, only read some part, DO NOT READ FULL FILE, and then based on that get a
> high level idea. then proceed to make relevant connections and backlinks between them. This is obsidian
> notes folders and backlinks, connections will be reflected in graph view. Don't try to be PERFECT.

### 1-1. 신규 노트만 골라낸다 (memory 활용)

전체를 다시 읽지 않는다. 처리 대상은 **memory.md에 기록된 마지막 처리 이후 새로 추가/변경된 노트**다.

- 1차: `memory.md`의 `last_commit` 이후 변경분을 git으로 추린다.
  `git diff --name-only <last_commit> HEAD -- 'wiki/**/*.md' 'raw/qa/*.md'` + 추적 안 된 신규 파일(`git status`).
- 2차(보강): `wiki/`와 `raw/qa/`의 전체 노트 집합에서 memory.md `## 처리됨` 목록에 없는 파일을 신규로 본다.
- 두 결과의 합집합을 **신규 노트 목록**으로 삼는다. 신규가 없으면 Step 1을 건너뛰고 그 사실을 보고한다.

### 1-2. 각 신규 노트에 연결을 만든다

신규 노트마다:

1. 앞부분만 읽어 high-level idea(섹터/주제/밸류체인 위치)를 잡는다.
2. **이 노트의 주제를 이해하는 데 실제로 도움이 되는** 기존 노트만 **3~5개**로 추린다(많이 거는 게
   목적이 아니다 — 신호가 약한 링크는 버린다). 좋은 연결의 근거는 예를 들어:
   - 같은 밸류체인의 전/후방(예: 메모리 ↔ CSP ↔ 전력),
   - 동일 섹터 경쟁/대체재, 공급-수요 관계,
   - 같은 지정학·매크로 테마에 노출된 자산.
   기업 노트는 `wiki/sector-map.md`가, raw 전체는 `wiki/raw-map.md`가 후보를 빠르게 좁히는 인덱스다.
3. 노트 끝에 아래 형식으로 섹션을 **추가(append)** 한다(있으면 합치고, 헤딩을 중복 생성하지 않는다).
   **링크마다 한 줄씩, 왜 그 노트가 주제 이해에 도움이 되는지 1~2문장 설명을 붙인다**(링크만 나열 금지):

   ```markdown
   ## 관련 노트

   - [[대상1]] — 이 노트의 주제와 어떻게 이어지는지, 무엇을 이해하는 데 도움이 되는지 1~2문장.
   - [[대상2]] — ...
   ```
4. 강한 상호 관계라면, 이미 처리된 상대 노트에도 **역방향 한 줄**을 보태 양방향 엣지를 만든다(선택).

### 1-3. 주의

- `## 관련 노트` 헤딩이 이미 있는 노트는 새로 만들지 말고 기존 섹션에 항목만 보탠다(중복 헤딩 금지).
- raw 노트에는 섹션을 달지 않는다(읽기 전용). raw는 링크의 *대상*으로만 등장한다.
- 작업한 신규 노트 파일명을 memory.md `## 처리됨`에 추가한다.

---

## STEP 2 — repo 전체를 가로지르는 새 cross-border 노트

> Read the content of the file, and based on that get a HIGH LEVEL IDEA. Proceed to write a new note for
> that high level idea, and make relevant connections and backlinks from the existing notes. Save the notes
> in the wiki/ folder (flat) and update the wiki-map.

### 2-1. 저장소 전체에서 새 아이디어를 찾는다

- 탐색 범위는 **`raw/`와 `wiki/` 전체**다. Step 1처럼 신규에 한정하지 않는다.
- **이미 다른 cross-border 노트에서 쓴 소스 노트를 다시 인용해도 된다.** 재사용은 허용된다.
  단, **아이디어(렌즈/논지) 자체는 새로워야** 한다. memory.md `## cross-border 아이디어` 목록에
  이미 있는 프레이밍과 겹치지 않는, 다른 각도의 high-level idea를 잡는다.
- 좋은 cross-border 아이디어는 **서로 다른 폴더(silo)를 관통**한다(예: AI-반도체 × 에너지 × 지정학을
  하나의 논지로 묶기). 각 노트의 앞부분만 훑어 공통으로 흐르는 줄기를 포착한다.

### 2-2. 노트를 쓴다

- 저장 위치: `wiki/<읽기 쉬운 한국어 제목>.md` (평탄 배치, frontmatter `type: idea`).
- frontmatter는 최소로: `type: concept`(개념 종합) / `updated: <오늘 날짜>`.
- 구성: 맨 위에 **High-level idea**를 한 문단으로 요약하고, 이어 2~4개 섹션으로 논지를 전개한다.
- **모든 핵심 진술은 출처 노트로 위키링크**한다. 사실의 근거는 `raw/`로, 사례 기업은 `raw/cov/`의 overview 노트로,
  개념은 `wiki/geopolitics/` 등으로 잇는다(`schema/CLAUDE.md` §3.4).
- 본문 아래에 `## 관련 노트` 섹션을 둔다. 단, **이 노트의 주제를 이해하는 데 가장 도움이 되는 노트만
  3~5개**로 추리고, **링크마다 1~2문장 설명**을 붙인다(Step 1과 동일한 형식). 다른 cross-border 노트로
  잇는 '자매 노트' 류 링크나 허브 맵 링크는 넣지 않는다 — 그 인덱스는 `wiki/wiki-map.md`가 맡는다(아래 2-3).

### 2-3. 인덱스·트리 갱신 (누락 금지)

1. **wiki-map** — `wiki/wiki-map.md`의 `cross-border` 섹션에 새 노트를 **직접** 한 줄 링크로
   추가하고 `updated`를 갱신한다.
2. **파일트리** — `wiki/` 구조가 바뀌면 `schema/CLAUDE.md`와 `README.md`의
   파일 트리에 모두 반영한다.
3. **메모리** — memory.md `## cross-border 아이디어`에 새 노트 제목과 한 줄 논지를 기록한다.

---

## memory.md 사양

경로: `.claude/skills/connect/memory.md`. 이 스킬이 직접 유지·관리하는 상태 파일이다.
"이미 한 일"을 기억해 **신규 노트만 읽도록** 하는 것이 목적이다. 형식 예:

```markdown
---
last_run: 2026-06-24
last_commit: <직전 처리 시점의 git HEAD 해시>
---

## 처리됨 (Step 1: ## 관련 노트 완료)
- 000660_SK 하이닉스
- AVGO_Broadcom
- ...

## cross-border 아이디어 (Step 2 산출)
- AI 전력 슈퍼사이클과 에너지 안보 — AI 연산→전력→원자재→중동 석유
- 자원의 무기화 — 물질로 보는 세계질서 — 반도체·희토류·우라늄 가치사슬, 미중 공급망
- 달러 패권의 균열 — 페트로달러·위안화·금·연준·스테이블코인
```

갱신 규칙:
- 실행 끝에 `last_run`(오늘 날짜)과 `last_commit`(현재 HEAD)을 갱신한다.
- Step 1에서 섹션을 단 노트 파일명을 `## 처리됨`에 추가한다.
- Step 2에서 만든 노트 제목·논지를 `## cross-border 아이디어`에 추가한다.
- 목록은 사람이 읽기 좋게 유지하되, 정확성이 우선이다(추측해 채우지 않는다).

---

## 링크 검증 (마무리 필수)

커밋 전, 이번에 만든/수정한 노트의 위키링크가 실제 파일로 해소되는지 확인한다.

```bash
existing=$(find . -name "*.md" -not -path "./.git/*" -printf "%f\n" | sed 's/\.md$//' | sort -u)
# 검증 대상 파일들에 대해:
grep -oh '\[\[[^]]*\]\]' <files> | sed 's/\[\[//; s/\]\]//; s/|.*//; s/#.*//' | sort -u \
| while IFS= read -r l; do [ -z "$l" ] && continue;
    printf '%s\n' "$existing" | grep -qxF "$l" || echo "UNRESOLVED: $l"; done
```

- 이미지·PDF 임베드, 헤딩/블록 참조(`#`, `#^`), 의도된 ghost 노트(저장소에서 이미 여러 번 쓰이는
  미작성 링크)는 예외로 둔다. 그 외 UNRESOLVED는 오타이므로 고친다.

## 커밋

- 기본 브랜치에 직접 커밋하지 않는다(`schema/CLAUDE.md` §0). 작업 브랜치에서 진행한다.
- 변경 요약과 함께 커밋한다. PR이 이미 열려 있으면 같은 브랜치로 push해 갱신한다.
- 사용자가 명시적으로 요청하지 않는 한 새 PR을 만들지 않는다.
