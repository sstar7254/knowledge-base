# knowledge-base

Andrej Karpathy의 패턴을 따르는 개인 *second brain*. 3계층으로 구성한다.

| 계층 | 폴더 | 성격 |
| --- | --- | --- |
| **raw** | [`raw/`](raw/) | 불변(immutable) 원본 소스 — 사람이 관리, LLM은 읽기 전용 |
| **wiki** | [`wiki/`](wiki/) | 개념 노트, 기업 분석, 종합 페이지 등 커넥션 — LLM이 유지·관리 |
| **schema** | [`schema/`](schema/CLAUDE.md) | 조직 규칙 |

`raw/`는 frontmatter `type`과 1:1 대응하는 5개 폴더로 나뉜다:
[`news/`](raw/news/)(뉴스 스크랩) · [`cov/`](raw/cov/)(기업분석) · [`research/`](raw/research/)(자료 종합) · [`report/`](raw/report/)(단일 자료 요약) · [`note/`](raw/note/)(그 외 — book·strategic·logis 등).
주제 분류는 폴더가 아니라 태그가 담당하며, 전체 카탈로그는 [`wiki/raw-map.md`](wiki/raw-map.md)에 있다.

자세한 운영 규칙은 [`schema/CLAUDE.md`](schema/CLAUDE.md)를 참고한다.
