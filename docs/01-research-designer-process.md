# 01. 탑 디자이너 작업 프로세스 조사·분석 (1차)

> 목적: 디자인 도우미 에이전트 → 프레임워크 → 레퍼런스 수집 에이전트 → 학습 가이드로 이어지는 작업의 **출발점**.
> 범위: 토스, 해외 UI 서비스(Linear, Airbnb, Stripe, Vercel 등), 디자인 원칙. 디자인 시스템 자체(효율화 도구)는 이번 범위에서 제외하고, **아이디어 발상·와이어프레임 디벨롭·문제 해결형(전환율) 디자인**에 집중했습니다.
> 작성일: 2026-10-23 · 상태: 초안. 사용자와 함께 디벨롭할 예정

---

## 0. 조사 방법과 한계

- 웹 검색 결과의 요약·발췌에 의존했습니다. 이 환경에서는 toss.tech·linear.app 원문 페이지를 직접 열 수 없었습니다(네트워크 정책).
- 따라서 **원문 인용이 아닌 2차 요약이 섞여 있습니다.** 각 항목의 신뢰도를 표시했고, 원문 확인이 필요한 항목은 §6에 따로 모았습니다.

---

## 1. 출처별 관찰 (Raw findings)

### 1-1. 토스 (Toss)

| 관찰 | 근거 | 신뢰도 |
|---|---|---|
| **문제 발굴은 관찰에서 시작한다.** 초기 팀은 서울 곳곳에서 하루 종일 사람들을 관찰하고 사흘에 한 번꼴로 모여 논의했다. 그렇게 모은 아이템 100개 중 성공한 것이 간편송금이었고, 첫 버전은 6시간 만에 만든 웹 페이지였다. | [토스는 왜 단순함에 집착할까](https://blog.toss.im/article/importance-simplicity) | 0.8 |
| **한 화면에는 하나의 목적만 둔다(One thing per one page).** 송금 첫 화면은 금액 입력창 하나뿐이다. 팀 안에서도 고민이 많았지만 "다른 선택지가 없는 명쾌함"을 이유로 이 안을 채택했다. | [디자이너 4명 인터뷰](https://toss.im/tossfeed/article/toss-designer-interview), [모티베이션을 디자인하기](https://toss.tech/article/design-motivation) | 0.85 |
| **원칙 기반 리뷰(PP 리뷰)를 한다.** 모든 프로덕트 디자이너가 제품 원칙을 기준으로 서로 피드백한다. UX Writing 팀은 문구 몇 개를 고치는 데서 그치지 않고 화면 전체의 정보 구조를 다듬는 쪽으로 방향을 바꿨다. | [모티베이션을 디자인하기](https://toss.tech/article/design-motivation) | 0.8 |
| **실험 대상은 속도와 임팩트를 함께 따져 고른다.** 토스뱅크 비회원 가입 전환 실험에서 법무 검토가 필요한 동의·신분증 화면은 뒤로 미루고, 빠르게 반복할 수 있으면서 첫 유입에 영향을 주는 인트로 화면부터 개선했다. | [신입 디자이너가 꼭 알아야 할 실험 설계 팁](https://toss.tech/article/45391) | 0.85 |
| **시안을 만들기 전에 과거 실험 기록부터 본다.** 이미 시도했지만 기존 화면을 이기지 못한 안이 많았기 때문이다. 이 글은 "가설을 어떻게 세워야 흔들리지 않을까"를 핵심 고민으로 다룬다. | 위와 같음 | 0.85 |
| **가설은 인터뷰에서 얻고, 결과는 지표로 판단한다.** 대출 심사 로딩 화면에 실제 상품을 보여주는 실험에서 목표 지표인 대출 실행률은 움직이지 않았다. 다만 이탈률과 결과 화면 도달률이 소폭 개선되어 전체 배포로 이어졌다. 지표 변화가 없어 배포하지 못한 사례도 함께 소개한다. | [인터랙션, 꼭 넣어야 해요?](https://toss.tech/article/interaction), [첫 인터랙션 디자이너](https://toss.tech/article/1st_interaction_designer) | 0.75 |
| 디자인 시스템 덕분에 컴포넌트 작업은 줄고, 디자이너가 **인터랙션과 플로우에 집중**하게 되었다. | [TDS 아티클](https://toss.tech/article/toss-design-system), [디자인팀 10문 10답](https://toss.im/tossfeed/article/toss-design-team-qna) | 0.8 |
| Simplicity 컨퍼런스에서 개선 사례를 공개한다. 2025년 시즌 4의 주제는 "Vision-Driven Design"이었다. | [Simplicity 4](https://toss.im/tossfeed/article/simplicity4) | 0.9 |

### 1-2. Linear (Karri Saarinen)

| 관찰 | 근거 | 신뢰도 |
|---|---|---|
| **첫 작업은 문제를 이해하고 검증하는 것이다.** 그다음 "Explore designs"라는 이슈를 만들고 자유롭게 탐색한다. 큰 기능은 피드백을 거치며 여러 방향을 오간다. | [Linear Method](https://linear.app/method/manage-design-projects) | 0.8 |
| **기존 앱을 스크린샷으로 찍고 그 위에 디자인한다.** 디자인 파일은 산출물이 아니라 참고 자료일 뿐이다. 개발이 시작되면 실제 앱이 곧 디자인이 된다. | [Primer on how we design at Linear (X)](https://x.com/karrisaarinen/status/1715085201653805116) | 0.85 |
| **"Design is search."** 디자인은 생산 파이프라인이 아니라 탐색이다. 초반에는 열어두고, 후반에 현실과 맞춘다. 코드는 피드백 수단이지 틀이 아니다. | [Design is search](https://x.com/karrisaarinen/status/1999730838280503775), [Design is more than code](https://karrisaarinen.com/posts/design-is-more-than-code/) | 0.85 |
| 지표나 A/B 테스트보다 사용자 리서치, 고객 피드백, craft에 더 의존한다. | 팟캐스트 요약(2차) | 0.6 |

### 1-3. Airbnb

| 관찰 | 근거 | 신뢰도 |
|---|---|---|
| **스토리보드로 여정 전체를 본다.** 게스트 여정과 호스트 여정을 각각 15컷 정도로 그리고, 어떤 이메일이 여정의 어느 지점에 놓이는지까지 표시한다. | [TechCrunch](https://techcrunch.com/2017/08/07/airbnbs-director-of-experience-design-on-using-stories-to-design/), [O'Reilly](https://oreilly.com/ideas/katie-dill-on-heading-up-experience-design-at-airbnb-2) | 0.75 |
| **11-star experience.** 하나의 경험을 최악부터 비현실적인 최상(11성)까지 극단으로 늘려 상상한다. 그런 다음 6~7성 수준의 현실적인 안으로 되돌아온다. | [UX Collective](https://uxdesign.cc/intentional-play-heres-an-exercise-to-setup-your-next-vision-piece-da643bc548ff) | 0.8 |

### 1-4. 디자인 엔지니어 계열 (Vercel·Rauno Freiberg 등)

| 관찰 | 근거 | 신뢰도 |
|---|---|---|
| 인터랙션은 디자인 툴이 아니라 **코드로 바로 여러 버전을 만들어** 시작한다. 각 버전을 극단까지 밀어붙여 어느 것이 버티는지 본다. | [UX Tools](https://www.uxtools.co/blog/your-ui-needs-more-walt-disney) (2차, 단일 출처) | 0.55 |
| "Invisible details": 평소 의식하지 못하는 인터랙션 디테일을 관찰하고 기록한다. 대표 개념은 fidgetability, 곧 계속 만지고 싶어지는 인터랙션이다. | [designlobster](https://designlobster.substack.com/p/150-fidgetability) | 0.65 |

### 1-5. 프로세스 담론의 변화 (2025~)

| 관찰 | 근거 | 신뢰도 |
|---|---|---|
| **Jenny Wen(전 Figma 디자인 디렉터, 현 Claude 디자인 리드)은 "디자인 프로세스는 죽었다"고 말한다.** 엔지니어가 AI 에이전트로 동작하는 버전을 먼저 만들어 내는 상황에서는 discover→diverge→converge 순서가 깨진다는 것이다. 디자인은 실행 지원과 단기(3~6개월) 비전 제시로 나뉜다고 본다. | [Lenny's Newsletter](https://www.lennysnewsletter.com/p/the-design-process-is-dead) | 0.75 |
| 반론도 있다. 프로세스는 사고방식이고, AI는 실행 속도만 높일 뿐이라는 주장이다. | LinkedIn 반론(2차) | 0.5 |

### 1-6. 전환율·문제 해결형 그래픽의 근거 소스

| 소스 | 성격 | 활용 포인트 | 신뢰도 |
|---|---|---|---|
| [GoodUI](https://goodui.org/patterns/all) | 실제 A/B 테스트를 모아 패턴화했다(140여 개 패턴, 600건 이상 테스트, 자체 집계). | 예: "Multiple Steps" 패턴. 효과 크기는 참고치로만 본다. | 0.7 |
| [Baymard](https://baymard.com/learn/reduce-cart-abandonment) | 체크아웃 UX 대규모 연구 | 이탈 사유의 약 26%가 "과정이 너무 길거나 복잡함"이다. 게스트 체크아웃은 입력 필드 6~8개면 충분하다. | 0.75 |
| [growth.design](https://growth.design/llms.txt) | 행동심리 기반 케이스 스터디 | loss aversion, Zeigarnik 효과, social proof 같은 원리를 화면 단위로 해부한다. | 0.75 |
| [Stripe Checkout](https://stripe.com/blog/stripe-checkout) | 결제 UI 개선 원칙 | "작은 수정이 전환율을 크게 바꾼다." 불필요한 필드 제거, 비용 선공개. | 0.7 (벤더 자료) |

### 1-7. UI 레퍼런스 소스

| 소스 | 강점 |
|---|---|
| Mobbin | 실제 앱의 **플로우** 단위 레퍼런스(모바일·웹). MCP·에이전트 접근은 유료 플랜에서만 된다. |
| Refero | 웹 중심, 시각 검색에 강하고 에이전트용 접근을 지원한다. |
| Page Flows | 사람이 큐레이션한 사용자 여정 녹화본 |
| Godly / Land-book | 웹사이트·랜딩 페이지의 비주얼 영감 |

출처: [Mobbin vs Refero](https://www.lazyweb.com/compare/mobbin-vs-refero), [20 Design Reference Platforms](https://jsdevspace.substack.com/p/20-design-reference-platforms-beyond) (가격·기능은 현재 기준으로 다시 확인해야 함)

### 1-8. 발산·수렴 기법

- **Crazy 8s**(GV Design Sprint): 8분 동안 8개 안을 그린다. 처음 몇 개는 뻔하고, 뒤로 갈수록 독창적인 안이 나온다. 가장 마음에 드는 안을 고른 뒤 그 안이 깔고 있는 **가정**을 적는다.
- **구조화된 크리틱**: 목표를 먼저 밝히고 역할을 나누며, 피드백은 조용히 따로 작성한다. 형식은 "I like / I wish / What if"를 쓴다. ([UX Tigers](https://www.uxtigers.com/post/design-crit))
- **원칙 렌즈**: Apple HIG의 Hierarchy, Harmony, Consistency(2025 Liquid Glass 이후) ([createwithswift](https://www.createwithswift.com/liquid-glass-redefining-design-through-hierarchy-harmony-and-consistency/))

---

## 2. 분석: 공통 패턴 (분해 → 종합)

### 하위 질문별 결론

| # | 하위 질문 | 결론 | 신뢰도 |
|---|---|---|---|
| Q1 | 탑 디자이너는 어디서 시작하는가? | **"문제 검증"이 먼저다.** 토스는 관찰과 퍼널 이탈 구간 분석, Linear는 문제 검증, Airbnb는 여정 스토리보드로 시작한다. 화면부터 그리는 곳은 없었다. | 0.85 |
| Q2 | 아이디어(레퍼런스)는 어디서 얻는가? | ① **자기 조직의 과거 실험 기록**(토스) ② 기존 앱 스크린샷 위에 덧그리기(Linear) ③ 외부 패턴 라이브러리(Mobbin, GoodUI) ④ 일상 인터랙션 관찰(Rauno). **①과 ②가 과소평가되어 있다.** | 0.75 |
| Q3 | 발산은 어떻게 하는가? | 여러 방향을 만들되 극단까지 밀어본다(11-star, Rauno의 absurdity, Crazy 8s). 핵심은 **양을 먼저 확보하고, 뒤로 갈수록 좋은 안이 나온다는 것**이다. | 0.8 |
| Q4 | 수렴(선택)의 기준은? | **명시적인 원칙**이다. 토스의 One thing per page와 PP 리뷰, HIG의 Hierarchy가 여기에 해당한다. 취향이 아니라 원칙으로 리뷰한다. | 0.8 |
| Q5 | 검증은 어떻게 하는가? | 토스는 A/B 테스트와 지표, Linear는 리서치와 craft로 검증한다. **조직 성격에 따라 갈린다.** 공통점은 실패도 기록한다는 것이다. | 0.75 |
| Q6 | 전환율 같은 문제 해결형 그래픽은? | 마찰 줄이기(필드·단계·선택지 축소), 단계 나누기, 심리 원리(손실 회피, 사회적 증거)를 쓴다. 근거는 GoodUI, Baymard, growth.design에서 찾는다. | 0.75 |

### 종합: 1차 프로세스 모델 (초안)

```
 ┌─────────────────────────────────────────────────────────────┐
 │ ① 문제 검증   관찰·퍼널·인터뷰 → "어디서, 왜 막히는가"       │
 │ ② 맥락 수집   과거 실험/기존 화면 스크린샷/제약(법무 등)     │
 │ ③ 레퍼런스    내부 기록 → 외부 패턴(Mobbin) → 근거(GoodUI)   │
 │ ④ 발산        Crazy 8s · 11-star · 스크린샷 위 덧그리기       │
 │ ⑤ 수렴        원칙 렌즈(One thing/page, Hierarchy) + 크리틱  │
 │ ⑥ 구체화      와이어 → 하이파이 → 인터랙션(코드 프로토타입)  │
 │ ⑦ 검증        가설 1문장 + 지표 → A/B 또는 UT                │
 │ ⑧ 학습 기록   성공/실패를 "다음 ②의 재료"로 남김 ──┐         │
 └──────────────────────────────────────────────────────┘ ↺     │
```

**핵심 통찰 3가지**

1. **루프의 연료는 "기록"이다.** 토스는 시안을 만들기 전에 과거 실험부터 본다. 레퍼런스 에이전트는 외부 수집기에 그치지 않고 *내 작업과 실험의 기록*까지 레퍼런스로 다뤄야 한다. (0.8)
2. **레퍼런스는 4종류로 나뉜다.** 비주얼(어떻게 보이나), 패턴(어떻게 동작하나), 근거(효과가 있었나: A/B, 연구), 원칙(왜 맞나). 대부분의 레퍼런스 수집은 비주얼에서 멈춘다. (0.8)
3. **프로세스가 압축되는 흐름(Jenny Wen)을 감안해야 한다.** 단계를 순서대로 다 밟기보다 상황에 맞는 단계를 골라 쓰는 **모듈형 프레임워크**가 현실적이다. (0.7)

---

## 3. 검증 (논리·사실·완전성·편향)

- **사실**: 핵심 주장은 대부분 공식 출처(toss.tech, toss.im, Karri의 글)의 검색 발췌에 기반한다. Rauno의 프로세스와 Linear의 "A/B보다 리서치"는 2차·단일 출처라 신뢰도를 낮췄다.
- **완전성**: 아직 비어 있는 영역이 있다. ① 그래픽·브랜드 디자이너(토스 BX, 일러스트) 프로세스 ② 개인 디자이너의 SNS 스레드형 작업기(X, LinkedIn, 브런치) ③ 국내 다른 탑 팀(당근, 배민, 카카오뱅크) ④ Stripe와 Vercel 디자이너의 1차 글
- **편향**: 생존자 편향이 있다. 공개되는 글은 성공 사례 위주다. 토스가 실패 사례를 공개하는 점은 예외적이고 가치가 높다. 출처도 핀테크와 B2B SaaS에 치우쳐 있다.
- **논리**: "탑 팀이 이렇게 한다"가 "이렇게 하면 좋은 디자인이 나온다"를 뜻하지는 않는다. 프레임워크에는 *왜 이 단계가 필요한지*를 함께 적어야 한다.

## 4. 성찰 (신뢰도 0.8 미만 항목)

- **Q2 레퍼런스 출처(0.75)**: 개인 디자이너의 SNS 작업기를 아직 충분히 수집하지 못했다. 2차 조사에서 브런치, 디자인 뉴스레터, X 스레드를 보강한다.
- **Q5 검증 방식(0.75)**: 조직마다 다르다. 사용자의 상황(트래픽이 있는 서비스인지, A/B 테스트가 가능한지)을 들어야 결정할 수 있다. → §5 질문
- **Q6 전환 사례(0.75)**: 패턴 소스는 확보했지만 **비포·애프터 그래픽 사례 모음**은 아직 없다. 레퍼런스 에이전트의 첫 수집 과제로 둔다.

---

## 5. 함께 디벨롭할 질문 (다음 단계)

1. **대상 프로덕트·도메인**: 지금 개선하려는 서비스나 와이어프레임이 있나요? (앱/웹, B2C/B2B)
2. **당신의 역할과 경험**: 프로덕트 디자이너인가요, 기획자나 개발자가 디자인을 겸하나요? 가이드의 난이도가 여기에 따라 달라집니다.
3. **검증 수단**: 트래픽이 있어 A/B 테스트가 가능한가요, 아니면 UT나 정성 피드백이 중심인가요? 그에 따라 ⑦ 단계가 바뀝니다.
4. **모델 형태**: 위의 ①~⑧ 선형 루프와 상황별 모듈형(예: "와이어 디벨롭 모드", "전환 개선 모드") 중 어느 쪽이 맞나요?
5. **레퍼런스 4종(비주얼·패턴·근거·원칙)**: 이 분류에 동의하나요? 빠진 것이 있나요?
6. **보강 조사 우선순위**: 아래 중 무엇부터 할까요?
   - (a) 개인 디자이너 SNS 작업기
   - (b) 국내 탑 팀(당근, 배민 등)
   - (c) 전환율 비포·애프터 사례
   - (d) 그래픽·BX 디자이너 프로세스

## 6. 원문 확인이 필요한 항목

- toss.tech/article/45391: 가설 수립 방법의 후반부
- toss.tech/article/design-motivation: PP 리뷰의 구체적인 운영 방식
- Karri Saarinen의 Linear 디자인 6단계 원문
- Rauno Freiberg, "Invisible Details of Interaction Design" 원문
