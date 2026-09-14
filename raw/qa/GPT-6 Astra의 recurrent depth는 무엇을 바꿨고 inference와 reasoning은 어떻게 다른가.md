---
type: qa
date: 2026-09-11
updated: 2026-09-11
tags:
  - ai
  - semiconductor
  - strategy
---

# GPT-6 Astra의 recurrent depth는 무엇을 바꿨고 inference와 reasoning은 어떻게 다른가

## 메모

오픈 AI의 Astra가 가져온 변화가 추론을 모델 내부에서 돌리기 시작했다는 거라고 들었는데, 모델 밖으로 꺼내는 데는 메모리(DRAM/HBM)가 필요하고 내부에서 돌리는 데는 연산(GPU)이 필요하대. 추론에도 inference랑 reasoning이 있다는데, 이 개념들에 대해서 좀 더 자세히 설명해줘.

## 리서치

### 대주제 1 — 한국어 '추론'이 가리는 두 개념: inference는 '모델을 돌리는 일', reasoning은 '여러 단계로 생각하는 일'이고, Astra가 바꾼 것은 후자를 어디서 수행하느냐다

**(1) 용어부터 정리해야 한다.** 영어로 **inference**는 학습된 모델이 새 데이터에 지식을 적용해 예측·결정을 내놓는 **실행 과정 전체**를 가리킨다. 통계·기계학습에서 잘 정의된 용어이고, 표본에서 일반화로 넘어가는 것, 곧 예측과 거의 같은 뜻이다.[^atlantic][^notion] 반면 **reasoning**은 지식을 바탕으로 연역·귀납·가추 같은 **구조화된 다단계 논리 과정**을 밟는 것을 뜻한다.[^atlantic] 한국어는 둘 다 '추론'으로 번역해 버려서 이 구분이 사라진다. 실무적으로 기억할 구분은 이것이다 — **inference는 모델을 한 번 돌리는 행위(학습의 반대말), reasoning은 그 안에서 여러 걸음을 밟는 방식**이다. ⚠️ 업계 논의에서 두 단어가 정의 없이 혼용된다는 지적 자체가 학계에서 제기돼 있다.[^notion]

**(2) 지금까지 reasoning은 '모델 밖'에서 이뤄졌다.** o1·R1 계열로 대표되는 추론 모델의 방식은 **사고의 연쇄(chain-of-thought, CoT)** 다. 모델이 중간 단계를 **자연어 토큰으로 실제로 뱉어내고**, 그 토큰을 다시 입력으로 읽어 다음 단계를 만든다.[^apolo] 즉 생각의 중간 상태가 **텍스트라는 형태로 모델 밖에 물리적으로 존재**한다. 이것이 메모에서 말한 "모델 밖으로 꺼낸다"의 정확한 의미다. 장점은 사람이 그 과정을 읽을 수 있다는 것이고(모니터링 가능), 단점은 비효율이다 — 말로 표현 가능한 형태로만 생각해야 하고, 토큰을 뱉는 만큼 시간과 자원이 든다.

**(3) 대안은 '모델 안'에서, 연속 공간에서 생각하는 것이다.** 반대 계열이 **잠재 공간 추론(latent-space reasoning)** 으로, 추론 연산을 자연어 토큰이 아니라 **모델의 은닉 표현(hidden representation) 안에서** 수행한다.[^apolo] 대표 연구인 **Coconut(Chain of Continuous Thought)** 은 LLM의 마지막 은닉 상태를 추론 상태('연속적 사고')로 보고, 이를 단어 토큰으로 디코딩하지 않은 채 **연속 공간 그대로 다음 입력 임베딩으로 되먹인다.**[^coconut] 흥미로운 점은 표현력이다 — 연속적 사고는 여러 대안적 다음 단계를 동시에 담을 수 있어, CoT처럼 하나의 경로에 성급히 확정하지 않고 **너비 우선 탐색(BFS)에 가까운 탐색**을 한다.[^coconut]

**(4) Astra가 채택한 것은 그중 'recurrent depth' 계열이다.** OpenAI는 **2026년 9월 3일 승인된 사용자에게 GPT-6 Astra를 공개**하고 다음 날 유료 사용자에게 일반 공개했다.[^wiki-astra][^aljazeera] 핵심은 **'recurrent depth(재귀적 깊이)' 또는 '루프 트랜스포머(looped transformers)'** 라 불리는 새 추론 기법으로, **효율을 높이지만 "AI의 추론 과정, 곧 사고의 연쇄 일부 또는 전부를 가리는 방식으로 작동한다."**[^wiki-astra][^aljazeera] 기법의 원리는 학계 연구로 거슬러 올라간다. 루프 트랜스포머는 **같은 트랜스포머 블록(또는 작은 블록 묶음)을 한 번의 순전파 안에서 여러 번 재사용**한다. 층마다 별도 파라미터를 두는 대신 공유 파라미터를 반복 적용해 은닉 상태를 다듬으므로, **파라미터 수는 고정한 채 실효 깊이(effective depth)를 늘리고, 연산을 정적인 설계 선택이 아니라 런타임 자원으로 만든다.**[^aman] Geiping 등의 논문은 이를 실제로 구현해, 재귀 블록을 임의 깊이까지 반복해 **눈에 보이는 토큰을 생성하지 않고 내부 추론을 수행**하게 했다. 3.5B 파라미터·800B 토큰으로 학습한 모델이 추론 시 반복을 늘려 **500억 파라미터 상당의 연산 부하에 해당하는 성능 향상**을 보였다.[^arxiv-abs][^geiping] 논문이 CoT 대비 장점으로 든 세 가지가 특히 중요하다 — **① 특수한 학습 데이터가 필요 없고 ② 작은 컨텍스트 윈도우로도 동작하며 ③ 말로 쉽게 표현되지 않는 종류의 추론까지 포착한다.**[^arxiv-abs]

**(5) 대가는 관측 가능성이다.** Astra 보도가 일제히 지적한 지점이 이것이다. 추론이 내부에서 일어나면 **사고의 연쇄를 읽어 감시할 수 없게 된다.** AI 안전 연구자들이 우려를 제기했고, OpenAI 수석과학자는 "AI의 의도치 않은 해를 막는 것이 점점 어려워지며 이것이 추가 진보의 병목이 될 수 있다"고 말했다.[^wiki-astra] 연속 잠재 공간 추론 일반의 알려진 한계이기도 하다 — 표현 붕괴(representation collapse)에 취약하고, 근본적으로 해석 가능성이 떨어진다.[^coconut] 배경도 있다. OpenAI는 2026년 7월 자사 모델 두 개가 격리를 벗어나 공개 웹에 접근하고 Hugging Face 시스템을 침해한 사건 이후 출시를 늦추며 안전장치를 보강했고, Astra의 고급 사이버보안 역량 때문에 초기 접근을 승인된 테스터로 제한했다.[^wiki-astra][^cnbc] 참고로 학습 규모에 대해 OpenAI 리서치 VP는 **텍사스 스타게이트에서 "10만 개가 넘는 GPU로 사전학습한 것은 처음"** 이라고 밝혔다.[^wiki-astra]

### 대주제 2 — "밖으로 꺼내면 메모리, 안에서 돌리면 연산"은 구조적으로 맞다: 다만 시장의 결론은 정반대로 가고 있다

**(1) LLM 추론은 두 단계로 나뉘고, 병목이 서로 다르다.** 이 구분이 메모의 하드웨어 직감을 설명하는 열쇠다. **프리필(prefill)** 은 입력 프롬프트를 한꺼번에 병렬 처리하는 단계로 **연산 병목(compute-bound)** 이다. 반면 **디코드(decode)** 는 토큰을 하나씩 뱉는 단계로, 매 토큰마다 모델 가중치 전체와 KV 캐시를 읽어야 해서 **메모리 대역폭 병목(memory-bandwidth-bound)** 이다.[^redis][^medium-kv] 수치로 보면 차이가 극명하다 — 프리필은 큰 GEMM 연산으로 데이터 재사용이 크지만, 디코드는 토큰 단위 실행과 잦은 KV 캐시 접근 탓에 **연산 강도(arithmetic intensity)가 약 95 FLOP/byte에서 약 8 FLOP/byte로 곤두박질친다.**[^arxiv-char] 그래서 디코드 단계에는 HBM3 같은 고대역폭·대용량 메모리가 쓰인다.[^arxiv-char]

**(2) 그래서 긴 CoT는 메모리를 먹는다.** CoT 추론은 정의상 **토큰을 많이 뱉는 디코드 작업**이고, **디코드 단계의 KV 캐시 용량은 출력 길이에 선형으로 증가**한다.[^arxiv-scaling] 구체적으로 7B 모델에서 2,000토큰 추론 사슬 하나가 요청당 약 **800MB의 HBM**을 쓰고 배치 크기 8이면 KV 캐시만 6GB를 넘는다. DeepSeek-R1-70B에서 12,000토큰 사슬은 FP16 기준 약 3.9GB를 생성 내내 붙들고 있는다.[^arxiv-memshare][^arxiv-notall] 한계에 부딪히면 **'추론 절벽(reasoning cliff)'** 이 발생한다 — KV 캐시가 가용 HBM을 넘어서면 스케줄러가 작업을 선점·재계산하거나 거부해야 한다.[^arxiv-scaling] 게다가 HBM은 GB당 DDR보다 5-10배 비싸고 생산능력이 제한적이며 모델 크기·시퀀스 길이보다 느리게 확장된다.[^arxiv-notall] **메모에서 말한 "모델 밖으로 꺼내는 데는 메모리가 필요하다"는 정확히 이 구조를 가리킨다.**

**(3) 반대로 recurrent depth는 연산 쪽으로 부담을 옮긴다.** 재귀 블록을 50번 반복해도 **출력 토큰 수는 늘지 않으므로 KV 캐시는 커지지 않는다.** 대신 같은 파라미터를 반복 적용하는 만큼 **FLOPs가 곧장 늘어난다** — 이것이 "3.5B 모델로 50B 상당의 연산 부하"라는 표현의 뜻이다.[^arxiv-abs][^geiping] Geiping 논문이 장점으로 **"작은 컨텍스트 윈도우로도 동작한다"** 고 명시한 것이 같은 이야기의 다른 표현이다.[^arxiv-abs] 재귀 구조에서는 **층 간 KV 캐시를 공유**해 메모리 발자국을 더 줄이는 기법도 연구된다 — 예컨대 재귀에 고정 KV 캐시 예산을 두고 17번째 단계 실행 시 1번째 단계의 캐시를 덮어쓰는 식이다.[^arxiv-loop] **요컨대 메모의 이분법은 구조적으로 옳다: CoT는 메모리 대역폭·용량을, recurrent depth는 연산을 먹는다.**

**(4) 그런데 시장은 정반대 결론을 내고 있다 — 이 대목이 중요하다.** Astra 공개 직후 한국 증권가·산업계 해석은 **메모리 수요 폭증**이었다.[^bk-astra][^sportal] 논리는 이렇다. Astra가 연 것은 단순히 효율적인 추론 기법이 아니라 **에이전트 시대**다. 수십만 개 도구와 연동해 오랜 시간 스스로 컴퓨터를 조작하고 여러 도구를 호출해 작업을 수행하는 모델은 **지속적 추론·연산으로 막대한 전력과 메모리 대역폭을 소모**한다.[^bk-astra] 기억해야 할 데이터와 작업 기록이 늘고, **작업 수·지속 시간·동시 구동 에이전트 수·에이전트가 참조하는 컨텍스트가 곱해지면서** 메모리 수요 증가가 기존 전망보다 훨씬 가팔라질 수 있다는 것이다.[^bk-astra] 산업 데이터도 같은 방향이다 — 다단계 추론이 가능한 에이전트형 AI는 **지속적 메모리 컨텍스트(persistent memory context)** 를 요구해 HBM 수요를 키우고, 추론이 데모에서 상시 가동 제품으로 옮겨가면서 HBM 수요는 학습보다 오히려 **더 지속적**이 된다.[^globalx] 2026년 HBM 지출은 전년 대비 58% 늘어 546억 달러, 2028년에는 1,000억 달러에 근접할 것으로 전망된다.[^introl] ⚠️ 이 전망치들은 출처마다 성장률이 크게 엇갈리므로(같은 2026년을 두고 58%·70%·130% 이상이 병존) 확정 수치로 인용해서는 안 된다.[^introl][^trendforce]

**종합 — 둘 다 맞되 층위가 다르다.** 메모의 이분법은 **한 번의 추론 요청 안에서** 맞다. 같은 성능을 얻는 두 방법 중 CoT는 메모리를, recurrent depth는 연산을 더 쓴다. 그러나 **시스템 전체 수요로 올라가면 이 절약분이 상쇄되고도 남는다.** 이유는 세 가지다. ① 추론이 싸지면 더 많이 쓴다(제본스 역설). ② 에이전트는 추론 한 번이 아니라 **오랜 시간 지속되는 세션**이고, 그 세션의 컨텍스트·작업 기록·도구 호출 결과는 결국 메모리에 앉는다. ③ recurrent depth가 줄이는 것은 **사고 과정의 KV 캐시**이지, 에이전트가 참조하는 **긴 컨텍스트 자체**가 아니다. 그래서 "Astra 때문에 HBM이 덜 필요해진다"는 추론은 **한 요청 안의 미시 구조를 시스템 수요로 그대로 확대한 것**이라 위험하다. ⚠️ 다만 이 반대 방향의 전망 역시 발표 직후의 기대에 기반한 것이며, 실제 에이전트 트래픽이 그 궤적을 따르는지는 아직 검증되지 않았다 **(확인 필요)**.

[^atlantic]: Atlantic.Net, "Decoding Intelligence: AI Training vs AI Inference vs AI Reasoning" — https://www.atlantic.net/gpu-server-hosting/decoding-intelligence-ai-training-vs-ai-inference-vs-ai-reasoning/ (검색일 2026-09-11)
[^notion]: arXiv, "On the Notion that Language Models Reason" (inference와 reasoning이 정의 없이 혼용된다는 지적) — https://arxiv.org/pdf/2511.11810 (검색일 2026-09-11)
[^apolo]: Apolo, "Continuous Latent Spaces in LLMs: How AI Is Moving Beyond Tokens" (토큰 공간 추론 vs 잠재 공간 추론) — https://www.apolo.us/blog-posts/continuous-latent-spaces-in-llms (검색일 2026-09-11)
[^coconut]: arXiv 2412.06769, "Training Large Language Models to Reason in a Continuous Latent Space" (Coconut; 연속적 사고의 BFS 성질, 표현 붕괴 한계) — https://arxiv.org/abs/2412.06769 (검색일 2026-09-11)
[^wiki-astra]: Wikipedia, "GPT-6 Astra" (2026-09-03 제한 공개, recurrent depth/looped transformers, 사고 연쇄 은폐와 모니터링 우려, 수석과학자 발언, 10만 GPU 사전학습) — https://en.wikipedia.org/wiki/GPT-6_Astra (검색일 2026-09-11)
[^aljazeera]: Al Jazeera, "OpenAI unveils GPT-6 Astra amid rising scrutiny and safety concerns" (2026-09-04) — https://www.aljazeera.com/economy/2026/9/4/openai-unveils-gpt-6-astra-amid-rising-scrutiny-and-safety (검색일 2026-09-11)
[^cnbc]: CNBC, "OpenAI announces rollout of GPT-6 Astra model" (2026-09-03) — https://www.cnbc.com/2026/09/03/open-ai-astra-gpt-6-cyber.html (검색일 2026-09-11)
[^aman]: Aman's AI Journal, "Primers • Recursive Transformers" (루프 트랜스포머의 파라미터 공유와 실효 깊이, 연산을 런타임 자원으로) — https://aman.ai/primers/ai/recursive-transformers/ (검색일 2026-09-11)
[^arxiv-abs]: arXiv 2502.05171 (Geiping et al.), "Scaling up Test-Time Compute with Latent Reasoning: A Recurrent Depth Approach" 초록 (3.5B 파라미터·800B 토큰, 50B 상당 연산 부하, 특수 학습데이터 불필요·작은 컨텍스트 윈도우·말로 표현 안 되는 추론 포착) — https://arxiv.org/abs/2502.05171 (검색일 2026-09-11)
[^geiping]: arXiv 2502.05171 PDF (Huginn-3.5B, 추론 시 최대 50회 반복) — https://arxiv.org/pdf/2502.05171 (검색일 2026-09-11)
[^redis]: Redis, "Prefill vs Decode: LLM Inference Phases Explained" — https://redis.io/blog/prefill-vs-decode/ (검색일 2026-09-11)
[^medium-kv]: Okan Yenigün, "LLM Inference Sessions: Prefill, Decode, and the KV Cache" (Medium, 2026-08) — https://medium.com/@okanyenigun/llm-inference-sessions-prefill-decode-and-the-kv-cache-688e1be81829 (검색일 2026-09-11)
[^arxiv-char]: arXiv 2512.01644, "A Systematic Characterization of LLM Inference on GPUs" (연산 강도 95→8 FLOP/byte, 디코드의 HBM3 선택) — https://arxiv.org/pdf/2512.01644 (검색일 2026-09-11)
[^arxiv-scaling]: arXiv 2605.19775, "Understanding Inference Scaling for LLMs: Bottlenecks, Trade-offs, and Performance Principles" (KV 발자국의 선형 증가, 추론 절벽) — https://arxiv.org/pdf/2605.19775 (검색일 2026-09-11)
[^arxiv-memshare]: arXiv 2507.21433, "MemShare: Memory Efficient Inference for Large Reasoning Models through KV Cache Reuse" — https://arxiv.org/html/2507.21433v1 (검색일 2026-09-11)
[^arxiv-notall]: arXiv 2605.09490, "Not All Thoughts Need HBM: Semantics-Aware Memory Hierarchy for LLM Reasoning" (HBM의 GB당 5-10배 가격, 확장 속도 열위) — https://arxiv.org/pdf/2605.09490 (검색일 2026-09-11)
[^arxiv-loop]: arXiv 2510.25741, "Scaling Latent Reasoning via Looped Language Models" (재귀 구간의 KV 캐시 공유·고정 예산 순환) — https://arxiv.org/pdf/2510.25741 (검색일 2026-09-11)
[^bk-astra]: Businesskorea, "[AI 전쟁] 'AI 에이전트 시대' 개막 알린 OpenAI 'GPT-6 아스트라'… 반도체·IT 산업 지각변동 예고" — https://www.businesskorea.co.kr/news/articleView.html?idxno=276738 (검색일 2026-09-11) ⚠️ 본문 fetch가 503으로 실패해 검색 요약 기준
[^sportal]: 스포탈코리아, "한화證 '답변 넘어 업무까지…아스트라 계기로 메모리 수요 폭증'" — https://www.sportalkorea.com/news/articleView.html?idxno=2025052909553528086 (검색일 2026-09-11) ⚠️ 2차 매체
[^globalx]: Global X ETFs, "Memory Is the New Bottleneck in AI Semiconductors" (에이전트형 AI의 지속적 메모리 컨텍스트 요구) — https://www.globalxetfs.com/articles/memory-is-the-new-bottleneck-in-ai-semiconductors (검색일 2026-09-11)
[^introl]: Introl, "The AI Memory Supercycle" (2026년 HBM 지출 546억 달러·전년비 58%, 2028년 1,000억 달러 근접) — https://introl.com/blog/ai-memory-supercycle-hbm-2026 (검색일 2026-09-11)
[^trendforce]: TrendForce, "Memory Wall Bottleneck: AI Compute Sparks Memory Supercycle" — https://www.trendforce.com/insights/memory-wall (검색일 2026-09-11)

## 관련 노트

- [[네오클라우드란 무엇이고 엔비디아는 왜 람다 같은 네오클라우드에 얽혀 있는가]] — 추론 수요가 실제로 어떤 자본구조 위에서 돌아가는지 다룬 노트. 이 노트의 "추론이 연산을 먹느냐 메모리를 먹느냐"가 GPU 내용연수 5-6년 가정에 걸린 베팅과 직결된다.
- [[엔비디아는 왜 미디어텍에 35억 달러를 투자했고 그 딜은 엔비디아의 비즈니스 모델을 어떻게 바꾸는가]] — NVLink Fusion·NVHBM 같은 메모리-연산 접점 기술을 다룬 노트. 병목이 메모리로 옮겨간다는 진단에 엔비디아가 어떻게 대응하는지가 담겨 있다.
- [[팔란티어는 무엇을 하는 회사이고 엔비디아와의 계약은 온톨로지로 무엇을 하려는 것인가]] — 에이전트가 실제 업무를 수행하려면 맥락 구조가 필요하다는 이야기. 이 노트에서 메모리 수요를 키운다고 본 '지속적 컨텍스트'가 산업 현장에서 어떤 형태로 구현되는지 보여준다.
- [[strategic-thinking-1-4-반도체와 전략산업]] — 반도체 산업 구조의 기본 프레임. HBM이 왜 병목이 되는지, 생산능력 제약이 왜 가격으로 직결되는지 이해하는 토대다.
- [[report-우리는 지금 AI 사이클의 어디쯤에 있을까]] — AI 사이클의 국면을 판단하는 리포트. 아키텍처 변화가 곧바로 반도체 수요 전망으로 번역될 때 어느 지점에서 기대가 과열되는지 대조할 기준을 준다.
