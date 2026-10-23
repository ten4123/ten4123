# A1. SNS 작업기 리서치 (해외) — 톱 프로덕트/UI 디자이너는 실제로 어떻게 일하나

- 모듈: SNS 작업기 리서처 (해외)
- 조사일: 2026-10-23
- 방법: WebSearch만 사용함. 페이지 직접 열람(WebFetch/curl)은 정책상 막혀 있음. 아래 내용은 **검색 결과 스니펫과 검색 엔진 요약에 근거**한다. 원문 전체를 읽은 것은 아니다.
- 신뢰도 기준: 0.8~0.9는 본인 1차 출처이고 스니펫으로 핵심 문장이 확인된 경우, 0.6~0.7은 본인 출처지만 요약을 통해 간접 확인한 경우, 0.4~0.5는 제3자 요약·팟캐스트 쇼노트, 0.3 이하는 정황 근거만 있는 경우.
- 인용 표기: 영어 원문 인용("...")은 검색 결과에서 그 문구가 확인된 경우에만 썼다. 그 외에는 모두 한국어로 의역했다.

---

## 1. 요약 — 공통 패턴

- **"프로세스보다 크래프트·판단"이 지배적인 담론이다.** Linear의 Karri Saarinen은 "craft over process"를 말하고 정해진 단일 프로세스가 없다고 한다. Jenny Wen(Figma→Anthropic)은 "The design process that designers have been taught is basically dead"라고 말한다. Apple 출신 Ken Kocienda는 A/B 테스트 대신 taste와 판단을 말한다. 단계별 방법론보다 **판단력을 빠르게 반복해서 쓰는 것**이 핵심이라는 데 의견이 모인다.
- **발산은 "실물 프로토타입"으로 한다.** Browser Company(Arc/Dia)는 "really, really heavy on prototyping and exploring"이라고 말한다. Rauno Freiberg와 Julius Tarng은 와이어프레임·목업을 건너뛰거나 줄이고 코드로 바로 간다. Brian Lovin(Notion)은 팀 공용 "prototype playground"를 만들었다. 정적 시안 여러 장보다 **만져볼 수 있는 변형 여러 개**를 만드는 쪽으로 기울어 있다.
- **발산의 양 자체를 공개적으로 강조한다.** Jason Yuan은 "Designing 99 'No's for a single 'Yes'"라는 제목의 에피소드에서 쓰지 않은 컨셉 수십 개를 공개했다. Karri는 리디자인 초기에 Figma에서 방법론 없이 자유롭게 탐색했고, "early design needs freedom, later design needs reality"라고 말한다. Dia 팀은 "obvious ideas first"부터 다 해본다.
- **수렴 기준은 "매일 쓰는 감각"과 "스트레스 테스트"다.** Linear는 컨셉 탐색 → 스트레스 테스트 → 동작 정의 → 프로토타입 순으로 진행했다. Kocienda의 Apple은 데모를 반복하며 가장 강한 부분만 남겼다. Rauno는 빠른 스크롤·저전력 같은 극한 상황에서 인터랙션을 테스트한다. Emil Kowalski는 사용 빈도에 따라 애니메이션 여부를 결정한다(가장 자주 쓰는 동작에는 애니메이션 없음).
- **레퍼런스는 "좋은 것을 곁에 두고 왜 좋은지 분해하는" 방식으로 쓴다.** Emil의 "Developing taste"는 좋은 작업을 곁에 두고, 존경받는 사람이 누구를 존경하는지 보고, 왜 좋은지 생각한다. Ridd는 Arc를 쓰면서 스크린샷과 노트로 takeaway를 추출한다. Tobias van Schneider는 산업디자인·건축처럼 다른 분야에서 영감을 받는다. Jordan Singer와 Tobias는 기존 제품(Apple 사이트, 기기)을 분해·역설계하며 배웠다.
- **정성 피드백은 "맥락을 먼저 준 비동기 공유"와 "형식이 있는 크리틱"으로 받는다.** Ridd(Loom 비동기 피드백)는 현재 상태·시작 이유·목표를 먼저 말한다. Figma 디자인팀은 6가지 크리틱 형식을 쓴다. Brian Lovin은 WIP 공유를 주장하며 Campsite를 만들었다. Jenny Wen은 팀이 서로의 작업을 "roast"할 수 있는 분위기를 강조한다.
- **AI 시대의 재정의가 진행 중이다.** Jenny Wen에 따르면 목업 비중이 줄고 있다. Ryo Lu(Cursor)와 Brian Lovin은 디자이너가 코드·에이전트로 직접 만든다. Karri는 "생성된 형태를 해결된 문제로 착각하는 것"을 경계한다. 공통 결론은 **생성은 싸지고 판단(taste·책임)이 비싸진다**는 것이다.

---

## 2. 디자이너별 카드

> 단계 코드: ①문제검증 ②맥락수집 ③레퍼런스 ④발산 ⑤수렴 ⑥구체화 ⑦검증(정성 피드백) ⑧학습기록
> 레퍼런스 4종: 비주얼 / 패턴 / 근거 / 원칙

### 2.1 Karri Saarinen — Linear 공동창업자·CEO (전 Airbnb DLS, Coinbase)
- 출처: [How we redesigned the Linear UI (part Ⅱ)](https://linear.app/now/how-we-redesigned-the-linear-ui) · [karrisaarinen.com 동일 글](https://karrisaarinen.com/posts/how-we-redesigned-the-linear-ui/) · [Design is more than code](https://karrisaarinen.com/posts/design-is-more-than-code/) · [Figma: 10 rules for crafting products](https://www.figma.com/blog/karri-saarinens-10-rules-for-crafting-products-that-stand-out/) · [X 포스트(2026.4)](https://x.com/karrisaarinen/status/2045257582470983691) · [Design Is Search 요약](https://en.ai-creators.tech/media/creative/design-search/) · [sspai 해설(중문)](https://sspai.com/post/104449)
- 핵심 작업 방식
  - 리디자인 초기에는 혼자 Figma를 열고 정해진 방법론 없이 자유롭게 탐색했다. 요약에 따르면 하루 단위로 화면 세트를 만들고 프로토타입으로 연결해 확인했다. 이 세부 내용은 검색 요약 기준이고 원문으로 재확인하지 못했다.
  - 진행 순서는 컨셉 탐색(Figma) → 스트레스 테스트 → 동작(behavior) 정의 → 프로토타입이었다. 처음 본 문제 3개 중 내비게이션은 엔지니어링 리스크가 너무 커서 보류했다(sspai). 즉 리스크를 보고 범위를 줄여 수렴했다.
  - "Design is search": 초기 디자인에는 자유가, 후기 디자인에는 현실(제약)이 필요하다. 그는 디자인이 선형적이지 않으며 컨셉 단계는 글·종이·디자인툴·코드 어디서든 일어난다고 쓴다. 실행이 쉬워졌다고 conceptual/divergent thinking을 평가절하하면 안 된다는 입장이다.
  - AI는 프로토타이핑·탐색에 도움이 된다. 하지만 디자인에는 판단·대화·긴장·시간이 필요하며, "생성된 형태를 해결된 문제로 착각"하는 것이 위험하다고 본다(X, 2026.4). Linear는 단일 프로세스를 따르지 않고 책임을 순환시켜 아이디어를 신선하게 유지한다(Figma 인터뷰).
- 프로세스 매핑: ①④⑤⑥ (+원칙 수준에서 ⑦)
- 레퍼런스 태그: 원칙, 패턴
- 신뢰도: 0.75 (본인 글이 1차 출처. 단 세부 문장은 요약을 거쳐 확인함)

### 2.2 Jenny Wen — Anthropic Claude 디자인 리드 (전 Figma FigJam·Slides 디자인 리드)
- 출처: [Lenny's Podcast: The design process is dead](https://www.lennysnewsletter.com/p/the-design-process-is-dead) · [Hatch 강연 요약(rar.design)](https://rar.design/posts/design-process-is-dead-jenny-wen.md) · [Antoine Buteau 요약](https://www.antoinebuteau.com/lessons-from-jenny-wen/) · [반론 Substack](https://thecursormag.substack.com/p/the-design-process-is-dead-or-is)
- 핵심 작업 방식
  - "The design process that designers have been taught is basically dead." 고전적인 discovery → mock → iterate 순서가 AI 프로토타이핑과 작은 팀 환경에서 무너지고 있다고 본다. 리서치나 전략을 부정하는 것은 아니다(Hatch 강연).
  - 솔루션에서 출발하고, 디테일에 신경 쓰고, 직관을 키우는 것을 강조한다. 긴 리서치 단계가 없으니 빠른 결정을 직관에 의존해야 한다는 논리다.
  - 크래프트는 픽셀을 미는 것에 그치지 않고 매체와 기술 제약을 깊이 이해하는 것이다. 팀이 작업을 "roast"(가차 없이 비평)할 수 있는 환경을 만들면서도 높은 기준을 유지한다.
  - "we might be holding on to taste as a differentiator a little bit too much." AI가 taste에서도 나아지겠지만 출시물에 대한 책임은 사람이 진다. 목업 비중이 60~70%에서 30~40%로 줄었다는 수치는 LinkedIn 2차 인용이라 미확인이다.
- 프로세스 매핑: ④⑤⑥⑦
- 레퍼런스 태그: 원칙
- 신뢰도: 0.6 (본인 팟캐스트·강연이 출처지만 확인은 요약·쇼노트를 통해서만 함)

### 2.3 Rauno Freiberg — Vercel Staff Design Engineer (전 The Browser Company/Arc)
- 출처: [Lovers Magazine 인터뷰](https://spaces.is/loversmagazine/interviews/rauno-freiberg) · [yespress 프로필(2차)](https://yespress.io/rauno-freiberg.md) · [UX Tools: Your UI needs more Walt Disney(2차)](https://www.uxtools.co/blog/your-ui-needs-more-walt-disney) · [27 detalles invisibles(2차, 스페인어)](https://disenandoapps.substack.com/p/27-detalles-invisibles)
- 핵심 작업 방식
  - 코드를 재료로 삼는다. UX Tools 요약에 따르면 와이어프레임·목업을 완전히 건너뛰고 코드로 바로 프로토타입을 만든다(2차 특성화).
  - "robustness"를 강조한다. 빠른 스크롤, 저전력 같은 극한 상황에서 인터랙션이 버티는지 테스트한다.
  - 에세이 "Invisible Details of Interaction Design"(Every.to, 2023)에서 매일 쓰지만 의식하지 않는 인터랙션의 숨은 디테일을 관찰하고 분해한다. 일상의 물리적 행동이 레퍼런스라는 해석이 있지만 2차 해석이다.
- 프로세스 매핑: ③④⑥⑦
- 레퍼런스 태그: 패턴, 원칙
- 신뢰도: 0.45 (본인 원문 문장은 검색으로 확인하지 못함. 모두 2차 요약)

### 2.4 Emil Kowalski — Linear Design Engineer (전 Vercel, Sonner·Vaul·animations.dev 제작자)
- 출처: [Building a toast component](https://emilkowal.ski/ui/building-a-toast-component) · [Developing Taste 독어 재게재](https://zeli.app/de/story/50160135) · [Craftwork digest #4 요약](https://craftwork.design/blog/4) · [emilkowalski/skills 요약(3자)](https://instagit.com/emilkowalski/skills/how-frequency-of-use-should-drive-animation-decisions/)
- 핵심 작업 방식
  - "Developing taste" 요약에 따르면 taste는 타고나는 것이 아니라 훈련된 직관이다. 키우는 방법으로 다음을 든다: Surround yourself with great work / 존경받는 사람들이 누구를 존경하는지 찾기 / "Think about why you like something" / 만들면서 피드백 구하기.
  - Sonner를 만들 때 기능적인 이름을 피하고 '알림' 관련 프랑스어 단어를 찾아 "sonner(울리다)"를 골랐다. API는 react-hot-toast에서 영감을 받았다(렌더링 방식이 매우 유사하다고 본인이 밝힘). 기존 라이브러리를 레퍼런스로 삼고 차별점(hook·context 없이 어디서나 호출)을 설계했다.
  - 사용 빈도에 따라 애니메이션을 결정한다. 하루 100회 이상 쓰는 동작(단축키, 커맨드 팔레트)에는 애니메이션을 넣지 않고, 모달·토스트는 300ms 미만으로 한다. ease-in과 scale(0) 진입은 금지한다. 이 내용은 그의 skills 저장소를 3자가 요약한 것이라 원문 확인이 필요하다.
- 프로세스 매핑: ③⑤⑥⑧
- 레퍼런스 태그: 비주얼, 패턴, 원칙
- 신뢰도: 0.6 (블로그 1차 출처가 있음. 수치 규칙은 3자 요약)

### 2.5 Brian Lovin — Notion 프로덕트 디자이너 (전 GitHub, Campsite 창업, Design Details 공동진행)
- 출처: [How I AI: How Notion designs with AI (Lenny's)](https://www.lennysnewsletter.com/p/this-week-on-how-i-ai-how-notions) · [ChatPRD 정리](https://chatprd.ai/how-i-ai/how-notion-designs-with-ai-brian-lovins-prototype-playground-and-claude-code-workflows) · [Sharing Work in Progress 에피소드](https://play.anghami.com/episode/1102491912) · [Designer Founders 인터뷰](https://designerfounders.substack.com/p/brian-lovin-notion-campsite)
- 핵심 작업 방식
  - code-first prototyping을 한다. 팀 전체가 기능하는 프로토타입을 만들고 공유하고 반복하는 Next.js 기반 "prototype playground"를 구축했다.
  - AI 제품은 Figma 같은 정적 툴로는 제대로 디자인할 수 없다고 본다. Figma 디자인을 프롬프트 하나로 동작하는 코드로 바꾼다.
  - 작업 규칙: "When Claude asks you to do something, teach it to do that thing itself"(반복 작업을 스킬·커맨드로 자산화).
  - WIP(진행 중 작업) 공유가 주는 가치와 두려움을 다뤘다. 이 주제가 WIP 공유 툴 Campsite를 만든 문제의식이다.
- 프로세스 매핑: ④⑥⑦⑧
- 레퍼런스 태그: 패턴
- 신뢰도: 0.6 (본인 출연 팟캐스트. 쇼노트·정리본으로 확인)

### 2.6 Jordan Singer — Diagram 창업자, Figma AI (전 Cash App, Mercury VP Design)
- 출처: [Mercury Founder Features](https://mercury.com/blog/jordan-singer) · [Not Boring Founder's Letter](https://www.notboring.co/p/the-founders-letter-jordan-singer) · [Dive Club: design engineer cowboy](https://dive-club.beehiiv.com/p/design-engineer-cowboy)
- 핵심 작업 방식
  - Apple 웹사이트 같은 것을 역설계(reverse-engineering)하며 디자인과 코드를 독학했다. 좋은 결과물을 분해하는 것이 곧 레퍼런스 학습이었다.
  - "My way of building things is to look for things that could help me"(Mercury). 자기 문제에서 출발해 만든다.
  - 코로나 기간 동안 "lil" 앱 시리즈를 공개적으로 만들며 과정을 공유했다(build in public). 텍스트 프롬프트로 화면을 생성하는 Figma 플러그인 'Designer'처럼, 아이디어를 바로 작동하는 프로토타입으로 만든다.
- 프로세스 매핑: ①③④⑦
- 레퍼런스 태그: 비주얼, 패턴
- 신뢰도: 0.55

### 2.7 Julius Tarng — Toolshop 독립 디자이너 (전 Webflow, Facebook 디자인툴팀 창설)
- 출처: [Dive Club: designing on expert mode](https://dive-club.beehiiv.com/p/designing-expert-mode) · [Toolshop (read.cv)](https://read.cv/teams/toolshop) · [Workspaces #103](https://workspaces.substack.com/p/103-julius-tarng)
- 핵심 작업 방식
  - "I spend way more time sketching stuff out on a notebook than I do in Figma. I can make a scribble and skip the Figma stage to jump directly into code."
  - 루프는 design → build → test → learn → repeat이고, 목업보다 기능하는 프로토타입을 선호한다.
  - 고객과 협업할 때는 1주짜리 trial project로 시작한다. 짧은 기간에 다룰 수 있는 조각부터 검증하는 방식이다.
- 프로세스 매핑: ④⑥⑦
- 레퍼런스 태그: 원칙
- 신뢰도: 0.75 (본인 발언 인용이 확인됨)

### 2.8 Nate Parrott — The Browser Company 창립 디자이너 (Arc), 현 Anthropic
- 출처: [Dive Club: fingerprints](https://dive-club.beehiiv.com/p/fingerprints) · [Inverse: Arc mobile skeuomorphism](https://www.inverse.com/gear/arc-web-browser-mobile-app-skeuomorphism-design)
- 핵심 작업 방식
  - "fingerprints > consistency": 일관성보다 손맛(개성 있는 흔적)을 우선한다(쇼노트 기준).
  - Browser Company의 "culture of prototyping" 안에서 일한다. 동료 Dustin Senos에 따르면 그는 늘 직접 해킹하는 Arc 빌드를 갖고 있었다.
  - 모바일 Arc의 방향을 "skeuomorph-ish"로 잡았다. 물리감, 깊이, 그림자, 3D 작업에 집중했다.
- 프로세스 매핑: ④⑥
- 레퍼런스 태그: 비주얼, 원칙
- 신뢰도: 0.45 (쇼노트·인터뷰 요약 수준)

### 2.9 Dustin Senos — The Browser Company 디자인 총괄 (Dia)
- 출처: [Dive Club: Designing Dia (transcript summary)](https://pod.wave.co/podcast/dive-club--556f9cbd-ac35-4833-98cc-6d19a1ee9091/dustin-senos-designing-dia-the-ai-native-web-browser-c89f532a)
- 핵심 작업 방식
  - 팀은 "really, really heavy on prototyping and exploring, especially early things"다.
  - Arc로는 더 큰 목표에 도달할 수 없다고 판단하자마자 프로토타이핑에 들어갔고, 뻔한 아이디어부터 먼저 소진했다. 예를 들어 가로·세로 전환이 가능한 탭바 같은 것이다.
  - 동료들은 "tried all kinds of different things and let their minds really wander"라고 표현했다. 이 문구는 2차 요약에서만 보이고 정확한 문구는 미확인이다.
- 프로세스 매핑: ①④⑤
- 레퍼런스 태그: 패턴
- 신뢰도: 0.55 (트랜스크립트 요약)

### 2.10 Jason Yuan — Hivemind 창업자 (전 Apple, Mercury OS)
- 출처: [Dive Club 에피소드 목록(Podwise)](https://podwise.ai/podcasts/2291) · [Dive Club episodes](https://mypodcastdata.com/en/podcast/show/dive-club-ridd-1vsj/episodes)
- 핵심 작업 방식
  - 에피소드 제목은 "Designing 99 'No's for a single 'Yes'"다. 쓰지 않은 컨셉, 새로운 아트 디렉션, 브랜드 아이덴티티 수십 개를 화면공유로 공개했다.
  - 목표는 아이디어의 "most true and simple expression"을 찾는 것이다. 대량 발산 후 가장 단순한 표현으로 수렴한다.
- 프로세스 매핑: ④⑤
- 레퍼런스 태그: 비주얼
- 신뢰도: 0.5 (에피소드 설명만 확인함, 원본 미청취)

### 2.11 Ryo Lu — Cursor 디자인 헤드 (전 Notion 창립 디자이너, Asana)
- 출처: [a16z: Cursor AI turns designers to developers](https://a16z.com/podcast/ryo-lu-cursor-ai-turns-designers-to-developers/) · [Antoine Buteau 요약](https://www.antoinebuteau.com/lessons-from-ryo-liu-of-cursor.md)
- 핵심 작업 방식
  - 디자이너는 목업에서 멈추지 말고 코드로 직접 가야 한다고 본다. Cursor로 모호한 아이디어를 상세 스펙으로 바꾸고, 여러 AI 에이전트를 동시에 운용한다.
  - 무엇이 좋은지에 대한 판단(taste)을 사람이 공급하지 않으면 결과물은 generic해진다("AI slop" 회피).
- 프로세스 매핑: ④⑥
- 레퍼런스 태그: 원칙
- 신뢰도: 0.5

### 2.12 Henry Modisett — Perplexity 디자인 헤드 (창립 디자이너)
- 출처: [Dive Club: designing a unicorn](https://dive-club.beehiiv.com/p/designing-unicorn) · [Inside Perplexity's design culture](https://pod.wave.co/podcast/dive-club--556f9cbd-ac35-4833-98cc-6d19a1ee9091/henry-modisett-inside-perplexitys-design-culture)
- 핵심 작업 방식
  - 합류 후 첫 단계로 미니 디자인 시스템을 만들었다. 초기 속도의 핵심은 시스템이었다.
  - "culture of decisiveness"(결정을 내리는 문화)를 만들고 피드백도 다르게 운영한다고 하지만, 구체 방식은 쇼노트상 미확인이다.
  - AI 프로젝트는 기술적으로 될지 모르는 상태에서 시작하는 경우가 많아 반복이 필수라고 본다. 코딩할 수 있는 디자이너를 선호한다.
- 프로세스 매핑: ⑤⑥⑦
- 레퍼런스 태그: 패턴, 원칙
- 신뢰도: 0.45

### 2.13 Ken Kocienda — 전 Apple 소프트웨어 엔지니어/디자이너 (iPhone 키보드), 『Creative Selection』 저자
- 출처: [Sachin Rekhi 리뷰](https://www.sachinrekhi.com/creative-selection-by-ken-kocienda) · [Jarango 독서노트](https://jarango.com/readings/creative-selection/) · [MacRumors](https://forums.macrumors.com/threads/creative-selection-offers-a-behind-the-scenes-look-into-some-key-moments-in-apples-design-history.2135336/)
- 핵심 작업 방식
  - 데모가 중심이다. 최종 승인용이 아니라 초기 진척 공유, 가능성 판단, 근본적인 디자인 결정을 위해 개발 내내 데모를 반복했다.
  - 작은 팀이 "rapid-fire demos"로 빠르게 반복하고, 매 버전에서 가장 강한 부분을 남긴다. 이것이 'creative selection', 즉 선택에 의한 수렴이다.
  - 7요소: inspiration, collaboration, craft, diligence, decisiveness, taste, empathy. taste는 균형을 찾아 통합된 전체를 만드는 판단력이다. iPhone 소프트웨어에는 A/B 테스트를 하지 않고 판단과 접근성 지식에 의존했다.
- 프로세스 매핑: ④⑤⑦
- 레퍼런스 태그: 원칙
- 신뢰도: 0.6 (본인 저서를 다룬 2차 리뷰)

### 2.14 Michael Riddering (Ridd) — Dive Club 호스트, 디자이너 (전 Maven)
- 출처: [Design Tactics #14: async feedback](https://ridd.substack.com/p/design-tactics-14-strategies-for) · [Design Tactics #11: 9 takeaways from Arc](https://ridd.substack.com/p/design-tactics-11-9-design-takeaways) · [Inflight](https://inflight-design.notion.site/Inflight-15fc5217570180a58e26d9234d353f70)
- 핵심 작업 방식
  - 비동기(Loom) 피드백에서는 리뷰어가 생각보다 더 많은 맥락이 필요하다고 가정한다. "People watching your video should immediately know what the current state is, why the work started, and what the goals of the design are." 오래된 스크린샷으로 현재 상태부터 보여준다.
  - 레퍼런스 수집: Arc를 쓰면서 노트를 쓰고 스크린샷을 모아 자기 작업에 적용할 takeaway를 추출했다("go-to source for design inspiration").
  - 비동기 크리틱 툴(Inflight)을 만들었다. 작업을 공유하고 영상으로 설명하면 영상 피드백을 받는 구조다.
- 프로세스 매핑: ③⑦⑧
- 레퍼런스 태그: 비주얼, 패턴
- 신뢰도: 0.75 (본인 뉴스레터 1차 출처)

### 2.15 Noah Levin 외 Figma 디자인팀 — Figma VP Design
- 출처: [From Figma's design team: How to run a design critique](https://www.figma.com/blog/design-critiques-at-figma/) · [Guide for Critique Visitors](https://paper.dropbox.com/doc/Guide-for-Critique-Visitors-g2gEMufFNbzj3HA7psNvb)
- 핵심 작업 방식
  - Figma 디자인팀은 크리틱 형식 6가지를 상황에 따라 골라 쓴다. 목표는 크리틱을 위협적인 자리가 아니라 동기를 주는 자리로 만드는 것이다.
  - 크리틱의 목적은 동료 디자이너에게 피드백과 아이디어를 받아 작업 품질을 올리는 것이다. 외부 방문자용 가이드 문서까지 따로 운영한다.
  - 6가지 형식의 이름은 검색 결과에서 확인하지 못했다. 바이라인(Levin 저자 여부)도 3자 리스트에 근거한다.
- 프로세스 매핑: ⑦
- 레퍼런스 태그: 원칙
- 신뢰도: 0.55

### 2.16 Tobias van Schneider — House of van Schneider, Semplice·mymind 공동창업 (전 Spotify)
- 출처: [Creative Bloq (.net): Tobias van Schneider on taking things apart](https://creativebloq.com/web-design/tobias-van-schneider-taking-things-apart-10134970) · [vanschneider.com 블로그](https://vanschneider.com/blog/author/tvs/page/5/)
- 핵심 작업 방식
  - 영감이 자신을 찾아오게 두되, 그럴 확률이 높은 위치에 자신을 둔다: 새로운 사람, 여행, 낯선 것 시도. 조언은 "force yourself to get lost"다.
  - 산업디자인과 건축 전반에서 큰 영감을 받는다. 즉 다른 분야를 레퍼런스로 쓴다.
  - 어릴 때부터 컴퓨터·TV·주방기기를 분해하고 다시 조립하며 배웠다. 디자인 '규칙'은 rigid rules보다 fundamentals로 보는 게 낫다고 쓴다.
- 프로세스 매핑: ③⑧
- 레퍼런스 태그: 비주얼, 원칙
- 신뢰도: 0.55 (본인 인터뷰지만 일부 문장은 검색 요약을 통해 확인)

### 2.17 Michael Flarup — PixelResort, 앱 아이콘 디자이너, 『The iOS App Icon Book』 저자
- 출처: [ApplyPixels: Designing App Icons](https://applypixels.com/class/designing-app-icons) · [Skillshare 동일 강의](https://www.skillshare.com/en/classes/designing-app-icons/2137389708) · [Adobe 인터뷰(2015)](https://blog.adobe.com/en/publish/2015/07/23/flarup-app-icon) · [Yanko: iOS App Icon Book](https://www.yankodesign.com/?p=348042)
- 핵심 작업 방식
  - 앱 아이콘 작업 흐름은 리서치 → 스케치 → 렌더링이고, 평가 기준 4가지는 scalability, recognizability, consistency, uniqueness다.
  - 인기 앱 아이콘이 해마다 어떻게 바뀌었는지(iteration)와 그 이야기를 책으로 아카이빙했다. 반복 과정 자체를 레퍼런스로 축적한다.
- 프로세스 매핑: ③④⑤⑥⑧
- 레퍼런스 태그: 비주얼, 원칙
- 신뢰도: 0.5 (강의 소개문 수준)

### 2.18 Soleio Cuervo — 전 Facebook(Like 버튼), Dropbox 디자인 리드
- 출처: [Design Buddies: Design lessons from Soleio](https://designbuddies.substack.com/p/design-lessons-from-soleio-the-designer) · [Design MBA: Designing the Facebook Like button](https://nl.player.fm/series/design-mba/designing-the-facebook-like-button)
- 핵심 작업 방식
  - 디자인은 회사가 되고 싶은 모습과 사용자가 경험하는 것 사이의 다리다. 비즈니스 목표를 먼저 이해한다.
  - Like 버튼은 내부에서 'Awesome' 버튼으로 불리며 여러 해 "product purgatory"에 머물렀다. 데이터 분석가의 테스트에서 상호작용이 늘어난 것이 확인되자 출시가 풀렸다. 정성 판단만으로 막힐 때 근거 데이터로 수렴한 사례다.
  - AI는 영향 범위(surface area of impact)를 넓히는 도구로 본다.
- 프로세스 매핑: ①⑤
- 레퍼런스 태그: 근거, 원칙
- 신뢰도: 0.4 (2차 기사·요약)

### 2.19 Julie Zhuo — 전 Facebook 프로덕트 디자인 VP (The Looking Glass)
- 출처: [tilnote 인용(원문: Junior Designers vs. Senior Designers)](https://tilnote.io/en/pages/68ba97691e08f5ca788a84e7) · [scrapbox 독자 노트](https://scrapbox.io/nishio-en/Different%20ways%20to%20explore)
- 핵심 작업 방식
  - 시니어 디자이너는 여러 각도에서 시작하고 한 가지 옵션으로 너무 일찍 좁히지 않는다. 다만 이는 독자 의역이라 원문 문장은 미확인이다.
- 프로세스 매핑: ④
- 레퍼런스 태그: 원칙
- 신뢰도: 0.3

### 2.20 Dann Petty — 프리랜스 웹·앱 디자이너, Epicurrence 주최
- 출처: [Adobe blog 인터뷰(2016)](https://blog.adobe.com/en/publish/2016/12/12/more-freedom-more-opportunity-more-time-to-surf-dann-petty-on-the-freelance-life)
- 핵심 작업 방식
  - 영감은 주로 외부(야외 활동 등)에서 오며, 프로젝트를 타이포그래피와 이미지부터 시작한다.
- 프로세스 매핑: ③⑥
- 레퍼런스 태그: 비주얼
- 신뢰도: 0.45

---

## 3. 바로 써먹을 수 있는 기법 목록

| 기법 | 1줄 사용법 | 출처 |
|---|---|---|
| 자유 탐색 → 현실 제약 2단계 | 초기 1~2주는 방법론 없이 Figma에서 매일 화면 세트를 만들고, 이후 스트레스 테스트와 동작 정의로 전환한다 | Karri Saarinen / Linear 리디자인 |
| 리스크 기반 범위 컷 | 문제 후보 3개를 놓고 엔지니어링 리스크가 큰 것(예: 내비게이션)은 이번 범위에서 명시적으로 뺀다 | Linear (sspai 해설) |
| 99 No 발산 | 하나의 Yes를 위해 아트 디렉션·컨셉을 수십 개 만들고, 가장 "true and simple"한 표현만 남긴다 | Jason Yuan |
| 뻔한 아이디어 먼저 소진 | 새 방향을 정하면 가장 obvious한 아이디어부터 프로토타입으로 만들어 지운다 | Dustin Senos (Dia) |
| 노트 스케치 → 코드 직행 | 종이에 낙서한 다음 Figma 단계를 건너뛰고 코드 프로토타입으로 간다 | Julius Tarng |
| 공용 프로토타입 플레이그라운드 | 팀 공용 Next.js 앱에 모든 프로토타입을 모아 누구나 만들고 공유하고 반복하게 한다 | Brian Lovin (Notion) |
| 반복 요청을 스킬로 | AI가 같은 일을 요구하면 그 일을 스스로 하도록 가르친다(슬래시 커맨드·스킬화) | Brian Lovin |
| 데모 반복 & 최강 부분만 남기기 | 정기적으로 작동하는 데모를 보여주고, 매 라운드에 가장 강한 요소만 다음 버전으로 넘긴다 | Ken Kocienda (Apple) |
| 극한 상황 테스트 | 빠른 스크롤·저전력·느린 네트워크에서 인터랙션이 버티는지 확인한다 | Rauno Freiberg (2차) |
| 사용 빈도별 모션 규칙 | 하루 100회 이상 쓰는 동작은 무애니메이션, 수십 회 쓰는 동작은 300ms 미만, 드문 경험만 풍부하게 | Emil Kowalski (skills, 3자 요약) |
| "왜 좋은가" 분해 노트 | 좋아하는 제품을 쓰면서 스크린샷과 노트로 takeaway를 추출한다 | Ridd (Arc 분석), Emil (Developing taste) |
| 존경받는 사람의 존경 대상 추적 | 존경하는 디자이너가 누구를 레퍼런스로 삼는지 찾아 한 단계 위 소스로 간다 | Emil Kowalski |
| 이름을 다른 언어에서 찾기 | 기능명 대신 관련 외국어 단어(예: 프랑스어)에서 제품·컴포넌트 이름을 찾는다 | Emil Kowalski (Sonner) |
| 비동기 크리틱 맥락 3종 세트 | 영상이나 글 첫머리에 현재 상태·시작 이유·디자인 목표를 먼저 말하고, 옛 스크린샷으로 시작한다 | Ridd Design Tactics #14 |
| 크리틱 형식 메뉴화 | 상황에 따라 6가지 크리틱 형식 중 하나를 골라 진행한다(위협이 아니라 동기 부여가 목표) | Figma 디자인팀 |
| Roast 가능한 팀 문화 | 높은 기준을 유지하면서 서로의 작업을 솔직하게 혹평할 수 있는 장을 만든다 | Jenny Wen |
| 폴리싱 시즌 | 신기능을 멈추고 일정 기간 "someday" 픽스만 처리한다(Linear 2022년에 228개) | [Linear changelog](https://linear.app/changelog/2022-12-01-polishing-season-2022) |
| 다른 분야에서 영감 | 산업디자인·건축·여행·낯선 경험에 의도적으로 노출된다("force yourself to get lost") | Tobias van Schneider |
| 역설계 학습 | 좋은 사이트나 제품을 그대로 재구현해 보면서 구조를 배운다 | Jordan Singer |
| 4기준 평가 | 아이콘·시각요소를 scalability, recognizability, consistency, uniqueness로 채점한다 | Michael Flarup |
| fingerprints > consistency | 일관성보다 손맛이 남는 디테일을 의도적으로 허용한다 | Nate Parrott (Arc) |

---

## 4. 공백·한계

- **원문 미열람**: 모든 내용이 WebSearch 스니펫과 검색 엔진 요약에 근거한다. 원문 문맥, 정확한 인용 범위, 날짜는 원문으로 확인해야 한다. 특히 Rauno, Emil 수치 규칙, Jenny Wen의 목업 비율, Julie Zhuo 의역은 원문 대조가 필요하다.
- **찾지 못한 대상**: Mariana Castilho, Paco Coursey는 프로세스를 다룬 본인 글이나 인터뷰가 검색되지 않았다(동명이인만 나옴). Benji Taylor, Raycast 디자이너, Stripe(Katie Dill, Benjamin De Cock), Airbnb 개별 디자이너, Tuhin Kumar도 쓸 만한 프로세스 서술을 찾지 못했다.
- **X/Twitter 스레드 공백**: X 개별 스레드는 검색 인덱싱이 약하다. Karri의 포스트 1건 외에는 스레드 원문을 확보하지 못했다. 레퍼런스 수집 습관(Are.na, mymind, 스크린샷 폴더 등)은 디자이너가 X에 짧게 남기는 경우가 많은데, 이 영역이 가장 비어 있다.
- **팟캐스트 의존**: Dive Club과 Lenny's 계열은 쇼노트나 AI 요약만 확인했다. 실제 발언 뉘앙스는 트랜스크립트로 확인해야 한다.
- **②맥락수집·⑧학습기록 근거 부족**: 발산·프로토타입·크리틱 이야기는 많지만, 문제 정의와 맥락 수집, 회고와 학습 기록을 구체적으로 서술한 1차 출처는 드물다.
- **편향**: 샘플이 Linear, Browser Company, Figma, Notion 등 "크래프트·디자인 엔지니어링" 계열에 몰려 있다. 엔터프라이즈나 리서치 중심 조직의 방식은 대표하지 않는다.
- **후속 제안**: (1) 접근이 가능해지면 Linear 리디자인 Part I·II, Figma 크리틱 6형식, Emil의 "Developing taste", Rauno의 Every.to 에세이 원문을 확보한다. (2) Dive Club 트랜스크립트(Jason Yuan, Nate Parrott, Julius Tarng)에서 직접 인용을 보강한다.
