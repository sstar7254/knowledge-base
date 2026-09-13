---
type: overview
date: 2025-02-14
updated: 2026-09-13
tags:
  - entertainment
  - ai
---

## AI 데이터 쇼티지 (2025.02.14)

> 출처: [26. Reddit(RDDT)](https://docs.google.com/document/d/1N_9J2vGuYrvMSiZOrSkm1GQurPfc1nvpm1CEQwK1OnY/edit)

### 데이터 홍수 시대, 데이터가 부족하다?

2023년 ChatGPT 등장 이후 AI 모델은 빠르게 성장했고, 그 성장의 필수 요소 중 하나가 데이터다. 그런데 최근 AI 업계에서는 데이터 부족이 임박했다는 예측이 많다. 단어 하나만 검색해도 수백만 개의 자료가 나오는 데이터의 홍수 속에서 정작 AI용 데이터가 모자란다는 역설이다.

리포트가 드는 설명의 출발점은 "Garbage-in, Garbage-out(GIGO)"이다. 좋지 않은 데이터를 넣으면 좋지 않은 결과가 나온다는 뜻으로, 훈련에 방대한 데이터가 필요한 AI에서는 잘못된 데이터를 계속 쓸 경우 품질 저하가 누적된다. Nature에 실린 연구를 주도한 옥스퍼드대 일리아 슈마일로프는 저품질 데이터로 AI를 훈련하는 과정을 '사진을 피사체 삼아 다시 사진 찍는 것'에 비유했다. 찍고 스캔하고 인쇄하는 과정을 반복하면 노이즈가 쌓여 결국 검은 사각형만 남듯, AI에서는 '모델 붕괴(model collapse)'가 나타날 수 있다는 것이다.

따라서 데이터 쇼티지는 데이터 전체가 아니라 학습용 '고품질' 데이터의 부족을 가리킨다. AI 연구기관 에포크(Epoch)에 실린 논문에 따르면 훈련에 필요한 데이터 양은 계속 늘어나는 반면 고품질 데이터는 26년 이전에 소진될 것으로 전망된다.

규모를 토큰으로 환산하면 격차가 분명해진다. 토큰은 인공지능이 글을 이해하고 생성하는 최소 단위인데, 현재 쓰이는 ChatGPT 4에는 약 12조 개가 사용된 것으로 추정된다. 한 단계 더 나아간 ChatGPT 5급 모델에는 최소 60-100조 개가 필요할 것으로 예상되지만, 지금 사용할 수 있는 고품질 언어 토큰을 모두 모아도 10-12조 개가 부족한 것으로 계산된다.

### 점점 커지는 데이터 거래

이 부족을 메우기 위해 AI 기업들은 대규모 데이터 거래에 나서고 있다. OpenAI는 23년 ChatGPT 발표 이후 AP 통신, Le Monde, Financial Times, Wall Street Journal, Time 등 주요 언론·매거진과 데이터 라이선싱 계약을 맺었다.

자체 SNS 플랫폼을 두 개나 보유한 Meta조차 초기에는 자사 플랫폼에서 생성되는 데이터로 모델을 훈련할 수 있다고 말했지만 결국 다양한 라이선싱 계약을 체결했고, Google과 Microsoft 등 빅테크도 데이터 거래에 뛰어들고 있다.

### 데이터 쇼티지의 해결법: 커뮤니티

이 계약 상대 중에는 언론·매거진이 아닌 기업이 하나 섞여 있다. 북미 최대 커뮤니티 레딧(Reddit)이다. 한국에서는 생소하지만, 인스타그램·페이스북·X와 달리 일상이 아니라 '정보 공유'가 활발하게 일어나는 플랫폼이라는 점이 핵심이다.

레딧 안에는 주제별 게시판인 '서브레딧(subreddit)'이 무수히 활성화돼 있고 그 안에서 의견이 오간다. 여기서 미국 밈이 시작되기도 하고, 21년 미국 증시를 뒤흔든 게임스탑 랠리도 r/wallstreetbets에서 출발했을 만큼 영향력이 커졌다. 이에 힘입어 레딧은 24년 3월 뉴욕 거래소 상장에 성공했고, 주당 46달러에 형성된 시초가는 1년가량 지난 현재 330% 상승해 200달러에 다다랐다.

거래 실적도 뒤따랐다. 24년 2월 구글과 연간 6,000만 달러(약 860억 원) 규모의 계약을 맺었고, 24년 5월에는 OpenAI와도 데이터 판매 계약을 체결했다. AI 기업들이 레딧을 찾는 이유는 정보 공유 플랫폼이라는 점만이 아니라, 정보의 품질을 유지하는 장치가 따로 있기 때문이다.

그 장치가 콘텐츠 모더레이터다. 레딧의 일부 유저가 자원해서 사실과 다르거나 관련 없는 정보를 삭제하는 역할을 맡는데, 하루에 2만 명 가까운 모더레이터가 총 466시간을 품질 관리에 쓴다. 덕분에 레딧 데이터는 고품질을 유지할 수 있었다. 여기에 실시간으로 다양한 주제의 의견이 올라오고 이미 서브레딧으로 주제가 세분화돼 있어 데이터 구조화가 간편하다는 점, 실제 사람들이 대화하며 정보를 공유하기 때문에 AI가 사람의 대화 방식을 배우기에 적합하다는 점도 더해진다.

선순환도 작동하고 있다. 24년 구글이 검색 알고리즘을 바꿔 사람이 만들어낸 응답을 최우선 배치하면서 레딧 정보에 접근하는 사람이 늘었고(구글 검색을 통한 로그아웃 트래픽 증가), 트래픽 증가가 더 많은 사용자 콘텐츠 생성으로 이어져 데이터의 가치가 다시 올라가는 구조다.

## Reddit (RDDT) 기업분석 (2025.02.14)

### 기업 개요

레딧은 2005년 스티브 허프먼과 알렉시스 오하니안이 설립한 소셜 뉴스·토론 플랫폼이다. 주요 제품은 사용자들이 주제별로 콘텐츠를 공유하고 토론하는 웹사이트와 모바일 앱이며, '서브레딧'이라 불리는 주제별 커뮤니티가 특징이다. 2024년 매출은 13억 달러로 광고가 92%, 데이터 라이선싱 등 기타 매출이 8%를 차지한다. 사용자 분포는 미국이 전체 일일 활성 사용자(DAU)의 47%이고 인도, 영국, 캐나다가 뒤를 잇는다. 2024년 3월 IPO 당시 첫 거래일 시가총액은 95억 달러였다. 소셜 미디어 광고 시장 점유율은 약 3%이며, 월간 활성 사용자(MAU)는 8억 5천만 명으로 스냅챗·핀터레스트·링크드인을 앞선다.

광고 사업에서는 다목적 광고 플랫폼을 비전으로 삼고 중소기업과 해외 광고주로 확장하며 빠르게 성장하고 있다. 2024년에는 AI 헤드라인 생성기를 출시하고 Memorable AI를 인수해 중견·중소 광고주의 참여를 늘렸다. 최근 도입한 LLM 기반 광고 검토 시스템은 자동 검토 비중을 70% 늘리고 검토 시간을 30분에서 1분으로 줄였다. 앞으로 1년간 레딧 고유의 경험을 더 제공하고 ML 최적화와 광고 스택의 자동화, 업종 다각화를 진행하겠다고 밝혔다. 서브레딧 단위의 타깃 광고가 가능하다는 점도 효율적인 광고 사업의 근거로 제시된다.

24년에는 데이터 라이선싱 사업에 본격 진출했다. 구글·OpenAI와의 계약으로 관련 매출은 23년 1,500만 달러에서 1Q24 2,000만 달러, 2Q24 2,800만 달러, 3Q24 3,300만 달러로 가파르게 늘었다. 연간 일정한 계약금을 수취하고 데이터 취합에 별도 비용이 들지 않아 영업 레버리지를 높일 수 있는 구조다.

주가는 24년 대규모 AI 기업들과의 잇단 데이터 라이선싱 계약과 구글 알고리즘 변경에 따른 트래픽 증가로 상승했고, DeepSeek 이슈 이후 저렴해진 AI의 수혜가 기대되며 25년에도 좋은 흐름을 이어갔다. 다만 2월 12일 4Q24 실적 발표에서 DAU가 컨센서스를 밑돌며 시간외에서 13% 하락했다.

### 4Q24 리뷰

4분기 매출은 4.28억 달러(YoY +71%)로 컨센서스 4.05억 달러를 상회했다. DAU는 1억 170만 명으로 39% 늘었지만 구글 검색 알고리즘 변경의 영향으로 컨센서스를 소폭 밑돌았다. 시장은 구글 알고리즘 변경에 크게 좌우되는 구조를 우려하고 있으나, 회사는 1분기 검색 트래픽이 회복됐다고 밝혔다.

24년 연간 매출은 13억 달러로 10억 달러를 돌파했고 분기 DAU도 1억 명을 넘어섰다. 인터넷 사용자의 40% 이상이 구매 결정에서 레딧의 추천을 영향력 있는 요소로 꼽는데, 이는 전문가 리뷰나 인플루언서 추천, 종합 별점을 앞서는 수치다. AI 기반 검색 도구 Reddit Answers를 출시했고, 올해 안에 하나의 통합 검색 제품으로 만들어 사용자가 레딧을 탐색하고 서브레딧을 찾으며 주관적이고 까다로운 질문에도 답할 수 있게 하겠다는 계획을 밝혔다.

### 연간·분기별 매출 트렌드

매출은 꾸준히 성장해 왔고 24년에 성장률이 크게 뛰었다. 반면 영업손실과 순손실도 크게 늘었는데, 상장 이전 주식 보상과 상장 이후 비용 처리에 따른 일회성 요인으로 판단된다. 영업이익률도 점차 개선되다가 24년 일회성 비용 증가로 급격히 꺾였다.

### 기업 지표

P/E는 OpenAI와의 계약 소식이 있었던 24년 5월 크게 상승했다가 현재는 역사적 평균치에 가까워졌다. META 28.87배, SNAP 30.94배와 비교하면 다소 높은 밸류에이션이다. 잉여현금흐름은 매출 증가에 따라 지속적으로 늘고 있다.

### 주주 환원

레딧은 상장 초기 기업으로 자사주 매입이나 배당 등 주주환원은 진행하지 않고 있다.

## Research

### 데이터 홍수 시대, 데이터가 부족하다?

- **[Data Scarcity: When will AI hit a wall?](https://pieces.app/blog/data-scarcity-when-will-ai-hit-a-wall)**

> There is a huge amount of AI training data on the Internet with more being created every second. It might seem that there would never be data scarcity in AI. However, there is a growing concern about **data scarcity in AI**. The limitations of current sources may create a data shortage for AI model training data, especially as the models become more powerful.
>
> In the AI model training process, an AI uses data from the past to interpret the present and predict the future. Imagine a self-driving car. Its success depends on a vast dataset of traffic scenarios, weather conditions, and pedetrian behaviour. If this data poo dries up, the car’s ability to navigate the ever-changing world will decrease.
>
> This can led to several issues: Reduced accuracy, Limited Generalizability, Complexity of tasks, Stifled Innovation
>
> The reasons for the scarcity of data are multifaceted.
>
> Ex. biases in AI algorithms - due to a data shortage for any group or dataset
>
> As AI is increasingly used in complex domains like healthcare and finance, the need for **more nuanced and specialized data becomes critical**. However, obtaining such data often requires navigating ethical minefiels, especially when dealing with sensitive information and absolute security requirements.
>
> The consequences are far-reaching. AI’s ability to tackle complex problems in healthcare, climate change, and scientific research could be stifled.
>
> The journey towards advanced AI may not focus on ever-increasing amoungs of data. Instead, we might overcome data scarcity **by shifting to using data more intelligently and increasning collaboration between AI and humans in the learning process**.

- **[좋은 걸 먹은 AI가 당연히 일을 더 잘합니다. '이 기업' 주목하세요](https://youtu.be/bzxh9vEEMSs?si=GG_FTnET_kAovbaL)**
    
	토큰: 언어 모델이 텍스트를 이해하고 생성하는 기본 단위. 인공지능이 글을 이해하고 생성하는 최소 단위
    
    고품질 데이터에 대한 수요가 공급을 앞지를 가능성 ‘24년 50% → ‘26년 90%

- **[For Data-Guzzling AI Companies, the Internet Is Too Small](https://www.wsj.com/tech/ai/ai-training-data-synthetic-openai-anthropic-9230f8d8)**

> Some executives and researchers say the industry’s need for **high-quality text data** could outstrip supply within two years, potentially slowing AI’s development.
>
> AI companies are hunting for **untapped information sources**, and rethinking how they train these systems. OpenAI, the maker of ChatGPT, has discussed training its next model, GPT-5, on transcriptions of public YouTube videos, people familiar with the matter said.
>
> Companies also are experimenting with using AI-generated, or synthetic, data as training material—an approach many researchers say could actually cause **crippling malfunctions.**
>
> Data is among several essential AI resources in short supply. [The chips needed](https://www.wsj.com/tech/ai/sam-altman-seeks-trillions-of-dollars-to-reshape-business-of-chips-and-ai-89ab3db0?mod=article_inline) to run what are called large-language models behind ChatGPT, Google’s Gemini and other AI bots also are scarce. And industry leaders worry about a dearth of data centers and the electricity needed to power them.
>
> But Pablo Villalobos, who studies artificial intelligence for research institute Epoch, estimated that GPT-4 was trained on as many as 12 trillion tokens. Based on a computer-science principle called the Chinchilla scaling laws, an AI system like GPT-5 would need 60 trillion to 100 trillion tokens of data if researchers continued to follow the current growth trajectory, Villalobos and other researchers have estimated.
>
> Harnessing all the **high-quality** language and image data available could still leave a shortfall of 10 trillion to 20 trillion tokens or more, Villalobos said. And it isn’t clear how to bridge that gap.
>
> Most of the data available online is useless for AI training because it contains flaws such as sentence fragments or doesn’t add to a model’s knowledge.
>
> **Meta** can mine hundreds of billions of publicly shared images and videos across its networks, including Facebook and Instagram, that are collectively larger than most commonly used data sets. It isn’t clear what percentage of that data would be considered high quality.
>
> → **Meta Eyes Paid Deals With News Publishers for AI Training**

- **[The Data That Powers A.I. Is Disappearing Fast](https://www.nytimes.com/2024/07/19/technology/ai-data-restrictions.html)**

### 점점 커지는 데이터 거래 시장 (Data Marketplace)

- **[Time, OpenAI sign multi-year content deal](https://www.reuters.com/technology/artificial-intelligence/openai-signs-multi-year-content-deal-with-time-magazine-2024-06-27/)**

데이터의 중요성이 높아지면서 데이터 거래 시장 (Data Marketplace) 이 주목을 받고 있습니다. 데이터 거래 시장은 데이터 공유와 협업을 지원하는 온라인 상점으로, 데이터 공급자와 소비자를 연결하여 안전한 환경에서 데이터를 사고 팔 수 있는 기회를 제공합니다.

CB insights

### 데이터 쇼티지의 해결법: 커뮤니티

- **[The Future of Reddit: A Unique Intersection of AI and Community](https://1xmarketing.com/news/en/world-marketing-diary-2407191194/#google_vignette)**

- **[Reddit’s Strategic Play Lands it a $60M Content Licensing Deal Before IPO](https://www.spiceworks.com/tech/artificial-intelligence/news/reddit-ai-training-data-deal/)**

#### 레딧 vs 메타:

레딧: 정보 교류 vs 메타: 일상 공유

Reddit’s Contents Moderator: 21,500명의 Moderator들이 하루 466시간을 모더레이션 작업에 사용 (2019) - volunteer

노동 가치 환산 시 $3.4M (2019년 매출 대비 3%)

⇒ 고품질 데이터

구글의 알고리즘 변화 (human-made contents) → 트래픽 증가 (특히, logout user /via Google) → 유저컨텐츠 증가 → 데이터 가치 상승

Reddit Data Licensing 매출: ‘23 $15M -. 1Q24 $20M → 2Q24 $28M → 3Q24 $32M

⇒ no expense, high leverage

Reddit, 주소비층이 다른 SNS와 중복되지 않음

서브레딧에 타겟 광고

데이터 라이센싱으로 사업 확장 중
