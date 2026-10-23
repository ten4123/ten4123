# ePRIS M3-a 작업기 리서치

## v1 (2026-10-23) 고밀도 업무 UI 크래프트

> 질문: 탑 디자이너와 프로덕트는 **밀도 높은 업무 화면**(긴 테이블, 상태 배지, 일괄 선택, 저장 피드백)을 어떻게 빠르고 정돈되게 만들었나?
> 대상 화면: S1 환자 카드 + 약품 테이블(15~20열, 가로 스크롤) · S2 상단 앱바 + 필터 칩(바텀시트) · S3 하단 조작 영역(선택 n건·저장) · S4 긴급 큐(좌) + 상세(우) · S5 메모 바텀시트. 기기는 세로 태블릿, 터치 전용.
> 기존 조사와 중복을 피했다. `docs/research/a3-b2b-clinical-designers.md`에 있는 Linear 리디자인 **프로세스**, Carbon **배치 액션 바**, Retool 선택 유지, NN/g 4과업, Ashby 단계적 마찰은 다시 쓰지 않고 참조만 한다. 이번 문서는 **시각·인터랙션 크래프트의 구체적인 값과 규칙**에 집중한다.
> 단계: ①문제검증 ②맥락수집 ③레퍼런스 ④발산 ⑤수렴 ⑥구체화 ⑦검증 ⑧학습기록 · 태그: [비주얼] [패턴] [근거] [원칙]

### 0. 조사 방법과 출처 접근성

- 검색어(한·영, 묶음 실행 6회 × 3라운드): Linear redesign density · Stripe dashboard table/badge/bulk · Polaris index table sticky/bulk · Primer data table density · Geist table/status dot · Toss 숫자·테이블·TDS · 배민 사장님 앱 · Airtable/Attio row height · Sonner/Emil undo toast · Material density touch target · Raycast compact · Vercel dashboard redesign · dark mode clinical · Matthew Ström UI density · 당근 SEED 배지.
- **WebFetch 접근성**: 이 환경에서 linear.app, vercel.com, polaris.shopify.com, primer.style, toss.im, buttondown.com, web.archive.org는 DNS 오류 또는 차단으로 열리지 않았다. **raw.githubusercontent.com은 열렸다.** 그래서 GitHub에 원문이 공개된 디자인 시스템 문서(Primer, Polaris, Carbon, Vercel Web Interface Guidelines, Rauno interfaces)는 **원문을 확인했다.** 나머지는 **검색 발췌 기반**이며 신뢰도를 낮췄다.
- 1인칭 작업기가 귀했다. 이번 질문(크래프트 값)에 가장 구체적으로 답한 것은 1인칭 회고보다 **디자인 시스템 원문**이었다. 각 카드에 출처 유형을 적었다.

---

### 1. 작업기·디자인 결정 카드

#### C1. Linear — UI 리디자인(2024)의 밀도·위계·대비 결정
- 출처: [How we redesigned the Linear UI (part II)](https://linear.app/now/how-we-redesigned-the-linear-ui) (Karri Saarinen, 1인칭), [Changelog 2024-03-20](https://linear.app/changelog/2024-03-20-new-linear-ui), 3자 요약 [Plushcap](https://www.plushcap.com/content/linear/blog/linear-how-we-redesigned-the-linear-ui-part-ii)
- 유형: 1인칭 회고 + 체인지로그. **검색 발췌 기반**(원문 열람 실패)
- 핵심 디자인 결정
  - 사이드바·탭·헤더·패널을 다듬어 "reduce visual noise … increase the hierarchy and density of navigation elements".
  - 기반 레이어를 다시 정의해 "hierarchy, balance, and density of all interface elements"를 개선했다.
  - 체인지로그: 기본 다크·라이트 테마의 **대비를 올렸고**, Inbox는 "increased density and better contrast"로 바꿨다.
  - 3자 요약: 테마 생성을 HSL에서 **LCH**로 옮겨 색 간 겉보기 일관성을 맞췄다(원문 미확인, 0.45).
- ePRIS 적용: S1·S2 크롬(앱바, 필터 칩, 환자 카드 헤더)의 **시각 무게를 줄여** 테이블 데이터가 1순위로 보이게 한다. 상태 색 틴트를 만들 때 지각 균일 색공간(LCH/OKLCH)으로 명도를 맞추면 m6 v2 토큰의 "틴트끼리 같은 무게" 조건을 맞추기 쉽다.
- 단계: ⑤수렴 · ⑥구체화 · 태그: [비주얼] [원칙]
- 신뢰도: 0.6 (발췌 문구는 공식 출처. 세부 수치와 LCH는 2차 요약)

#### C2. Matthew Ström — "UI Density" 에세이(2024-05)
- 출처: [matthewstrom.com/writing/ui-density](https://matthewstrom.com/writing/ui-density), 미러 [buttondown](https://buttondown.com/mattstrom/archive/ui-density), 3자 소개 [Gigazine](https://gigazine.net/gsc_news/en/20240526-ui-density). 같은 사람의 사이트에 "Stripe Merchant Dashboard" 프로젝트 페이지가 검색됐다(본문 미열람).
- 유형: 디자이너 1인칭 에세이. **검색 발췌 기반**
- 핵심 디자인 결정
  - 밀도는 "많이 채웠다"는 시각적 인상이 아니다. **사용자가 얻는 가치 ÷ (시간 + 공간)**으로 정의한다(발췌 요약).
  - 같은 점 배열도 묶음(그룹핑)에 따라 더 빽빽하거나 덜 빽빽해 보인다. 시각 밀도에 대한 직관은 믿을 만하지 않다.
  - 속도, 쉬운 사용, 일관성, 예측 가능성, 정보 풍부함을 모두 밀도에 포함한다. Bloomberg Terminal과 Craigslist가 예로 나온다.
- ePRIS 적용: S1 평가 기준으로 쓴다. "한 화면에 몇 행이 보이나"만 보지 말고 **"감사 1건을 끝내는 데 드는 시간"**까지 함께 잰다(M7 관찰 지표 후보). 그룹 간격(환자 카드 사이 간격 > 행 간격)으로 행이 많아도 덜 빽빽하게 읽히게 한다.
- 단계: ①문제검증 · ⑤수렴 · 태그: [원칙]
- 신뢰도: 0.6 (정의 문구는 발췌 요약. temporal density 세부는 미확인)

#### C3. Vercel — 대시보드 리디자인과 배포 목록 재설계
- 출처: [Vercel blog: Dashboard redesign](https://vercel.com/blog/dashboard-redesign), [Changelog: Redesigned deployments list](https://vercel.com/changelog/redesigned-deployments-list)
- 유형: 회사 블로그·체인지로그. **검색 발췌 기반**
- 핵심 디자인 결정
  - 리디자인은 "invaluable feedback from our active customers"를 근거로 했다. 우선순위는 프로덕션·최신 배포 **상태**를 먼저 드러내는 것이었다.
  - 배포 목록: **더 촘촘한 레이아웃**으로 한 화면에 더 많은 배포를 보이게 했다. 환경을 **상태별로 묶었고**, 브랜치·커밋을 훑기 쉽게 정리했다. 모바일 화면도 개선했다.
  - 3자 분석(Blake Crosley): 배포 상태를 탭 파비콘·페이지 제목 등 모든 곳에 보이게 한다(0.35).
- ePRIS 적용: S1 상태별 묶기는 **자동 재정렬이 아니라 필터·요약 칩**으로 가져온다. m6 v2 §7은 "행은 움직이지 않는다"이므로 저장 뒤 행이 다른 그룹으로 옮겨가면 안 된다. S2 필터 칩에 "미처리 n · 확인 필요 n"을 건수와 함께 보여준다.
- 단계: ②맥락수집(고객 피드백) · ⑥구체화 · 태그: [패턴]
- 신뢰도: 0.55

#### C4. Vercel Web Interface Guidelines — 숫자·터치·로딩·상태 규칙
- 출처: [vercel-labs/web-interface-guidelines README](https://github.com/vercel-labs/web-interface-guidelines) (**원문 열람**)
- 유형: Vercel 디자인 엔지니어링 팀이 공개한 체크리스트(1차, 규범 문서)
- 핵심 디자인 결정
  - 숫자: "Use `font-variant-numeric: tabular-nums` or a monospace". 자릿수를 열에 맞춘다.
  - 터치: 보이는 크기가 24px보다 작으면 히트 영역을 24px 이상으로 넓힌다. **모바일은 44px**이다. 체크박스는 라벨과 하나의 히트 영역을 공유한다. "If part of a control looks interactive, it should be interactive."
  - 로딩: 스피너는 **150~300ms 늦게** 띄우고 **최소 300~500ms** 유지해 깜빡임을 막는다. 요청 중에는 제출을 막고, "Saving…"처럼 말줄임 라벨을 쓴다.
  - 상태: "Don't rely on color alone; include text labels." 비동기 결과(토스트)는 polite aria-live로 알린다. "Empty, sparse, dense, & error states"를 모두 디자인한다.
  - 파괴적 액션: "Require confirmation or provide Undo with a safe window."
  - 다크: 다크 테마에서는 `color-scheme: dark`를 지정한다. 호버·활성·포커스 상태는 기본 상태보다 대비가 높아야 한다.
- ePRIS 적용: S1 숫자 열(용량, 횟수, 일수, 시각), S3 저장 버튼 로딩("감사 저장 중…"), S3 토스트, 빈/희소/과밀 상태 설계. **낙관적 업데이트 권고는 채택하지 않는다.** m6 v2 §7이 "서버 응답 뒤에만 그린다"로 정했고, 정확성 원칙에 맞다.
- 단계: ⑥구체화 · 태그: [원칙] [패턴]
- 신뢰도: 0.8 (원문 확인. 다만 웹 일반 가이드이고 의료 맥락의 근거는 아님)

#### C5. Rauno Freiberg — "Web Interface Guidelines"(개인 저장소)
- 출처: [raunofreiberg/interfaces README](https://github.com/raunofreiberg/interfaces) (**원문 열람**)
- 유형: 디자이너 1인칭 규칙 모음(1차)
- 핵심 디자인 결정
  - "Where available, tabular figures should be applied with `font-variant-numeric: tabular-nums`".
  - 호버·**선택 상태에서 글자 굵기를 바꾸지 않는다**. 레이아웃이 밀리기 때문이다.
  - 터치 기기에서 탭할 때 호버 스타일이 번쩍이지 않게 `@media (hover: hover)`로 가둔다.
  - 목록 항목 사이에 **죽은 영역이 없게** 하고, 여백(padding)을 늘려 히트 영역을 메운다.
  - "Animation duration should not be more than 200ms". **목록에서 항목을 추가·삭제하는 것처럼 자주 하는 동작에는 애니메이션을 더하지 않는다.**
  - 성공 피드백은 알림보다 트리거 근처의 임시 인라인 체크로 준다(복사 예시).
- ePRIS 적용: S1 선택 행은 **굵기 변화 없이** 외곽선과 체크로만 표시한다(m6 v2와 일치하는지 점검). 태블릿 웹뷰라면 호버 스타일을 가둔다. 체크 셀과 행 사이 죽은 영역을 없앤다.
- 단계: ⑥구체화 · 태그: [원칙] [비주얼]
- 신뢰도: 0.8

#### C6. GitHub Primer — DataTable
- 출처: [primer/design data-table.mdx](https://github.com/primer/design) (**원문 열람**, raw 경로 `content/components/data-table.mdx`)
- 유형: 디자인 시스템 문서(1차)
- 핵심 디자인 결정
  - 밀도는 Condensed / Normal / Spacious 3단계다. Condensed는 "showing more information in a smaller area", Spacious는 셀 내용이 시각적으로 복잡할 때 쓴다.
  - "Right-align numeric values and use the `tabular-num` font variant when possible."
  - 행 액션은 마지막 열에 두고 헤더가 없어도 된다. 여러 개면 드롭다운으로 묶는다. 자주 쓰는 것은 꺼낼 수 있지만 **"Do not pull out more than 1 action."**
  - 빈 셀은 기본적으로 비워 둔다. **"x"나 "-" 같은 문자를 쓰지 않는다.** 표 전체가 비면 테이블 대신 Blankslate를 보여준다.
  - 로딩은 실제 내용과 최대한 닮은 스켈레톤으로 한다. 750ms 안에 끝나면 로딩을 알리지 않는다.
- ePRIS 적용: S1 숫자 열 오른쪽 정렬과 tnum. 검토자·감사자 칸이 비었을 때 "-"를 넣지 않고 비워 두는지 결정한다(종이 처방전 관습과 충돌할 수 있다 → 약사 확인). 행 단위 메뉴(메모·이력)는 1개만 꺼내고 나머지는 묶는다.
- 단계: ⑥구체화 · 태그: [패턴] [비주얼]
- 신뢰도: 0.85

#### C7. GitHub Primer — Empty states
- 출처: [primer/design ui-patterns/empty-states.mdx](https://github.com/primer/design) (**원문 열람**)
- 핵심 디자인 결정
  - 빈 상태는 "아직 추가 안 함"과 "일시적으로 비어 있음"을 구분한다. 일시적으로 비어 있으면 **왜 비었는지**를 설명한다.
  - 오류에는 장난스러운 그래픽을 쓰지 않는다. 경고 아이콘으로 문제가 생겼다는 것을 분명히 한다.
  - 주 액션은 하나만 둔다. 오류의 액션은 해결 방법이나 도움말로 이어져야 한다. 기술 용어나 알 수 없는 오류 코드는 피한다.
- ePRIS 적용: S1 "필터 결과 0건"(일시적, 필터 해제 액션), S4 "긴급 처방 없음"(일시적, 마지막 갱신 시각), HIS·BESTCare 연동 실패(오류, "다시 시도"와 약제부 내선 안내).
- 단계: ⑥구체화 · 태그: [패턴]
- 신뢰도: 0.8

#### C8. Shopify Polaris — IndexTable
- 출처: [Polaris index-table.mdx](https://github.com/Shopify/polaris) (**원문 열람**, raw 경로 `polaris.shopify.com/content/components/tables/index-table.mdx`), 보조 [PR #8099](https://github.com/Shopify/polaris-react/pull/8099)(sticky와 벌크 바 충돌 수정, 발췌)
- 유형: 디자인 시스템 문서(1차)
- 핵심 디자인 결정
  - 벌크 액션 라벨은 **"verb + noun"** 형식으로 쓴다. 벌크 액션을 숨기면 다중 선택도 사라진다.
  - Shift 범위 선택을 지원한다. **소제목(subheader) 행의 체크박스로 그룹 전체를 선택**할 수 있다.
  - 스크롤해도 보이는 sticky **last** column이 있다. 헤더도 같이 고정된다.
  - 숫자 셀과 숫자 열 제목은 오른쪽 정렬하고 숫자 스타일을 쓴다.
  - 행 `tone`: "Whether the row should visually indicate its status with a background color".
  - 50건을 넘으면 페이지를 나눈다. 일부만 보여주고 있다면 그 사실을 표시한다.
  - PR #8099: 새 벌크 액션 UI가 pointer events를 막아 테이블을 선택할 수 없게 된 버그가 있었다. sticky 영역과 벌크 바가 겹칠 때 생기는 문제다(0.5).
- ePRIS 적용: S1 환자 카드 헤더 체크 = Polaris의 subheader 그룹 선택과 같은 패턴이다(m6 v2 G-12와 맞춤). S3 버튼 라벨 "감사 저장 2"는 동사+명사+건수 형식이라 이미 맞다. S1 좌측 고정 영역과 S3 하단 고정 바가 겹치는 구간에서 **탭이 막히지 않는지 QA 항목**으로 넣는다. "필터로 일부만 표시 중"을 S2에 명시한다.
- 단계: ⑥구체화 · 태그: [패턴]
- 신뢰도: 0.85

#### C9. Shopify Polaris — Badge
- 출처: [Polaris badge.mdx](https://github.com/Shopify/polaris) (**원문 열람**, raw 경로 `polaris.shopify.com/content/components/feedback-indicators/badge.mdx`)
- 핵심 디자인 결정
  - 톤은 6가지다(default, info, success, attention, warning, critical). warning과 critical은 **"it should only be used when absolutely necessary"**.
  - 진행 상태 배지는 Incomplete / **Partially complete** / Complete 3단계다.
  - 표 안에서는 small 배지를 쓴다. 배지는 라벨을 붙인 대상 바로 옆에 둔다.
  - 라벨은 한 단어, 과거형으로 쓴다(Paid, Fulfilled). 기존 라벨 목록에 없을 때만 새 라벨을 만든다.
  - 색이나 아이콘으로 뜻을 전하는 배지에는 스크린리더용 숨김 텍스트를 넣는다.
- ePRIS 적용: K3(빨강은 S-FL-03 전용)를 뒷받침하는 외부 근거다. BID "감 1/2"는 Polaris의 partially complete와 같은 구조이므로 **부분 완료 표지**(반쯤 찬 아이콘 + 텍스트)를 검토한다. 라벨 과거형은 **채택하지 않는다**. "검/감" 약어는 약사가 이미 익숙한 자산이다(conventions §6-5).
- 단계: ⑥구체화 · 태그: [비주얼] [원칙]
- 신뢰도: 0.85

#### C10. IBM Carbon — Data table style(행 높이·타이포)
- 출처: [carbon-website data-table/style.mdx](https://github.com/carbon-design-system/carbon-website) (**원문 열람**). 배치 액션은 a3 B2 참조.
- 핵심 디자인 결정
  - 행 높이는 5단계다. xs 24 / sm 32 / md 40 / lg 48 / xl 64px. xl은 "only recommended if your data is expected to have two lines of content".
  - 열 헤더 행은 "should always match the row size of the table".
  - 툴바 높이는 행 크기와 짝을 이룬다(lg·xl ↔ 48px 툴바, sm·xs ↔ 32px 툴바).
  - 타이포: 열 헤더 14px SemiBold, 행 본문 14px Regular.
- ePRIS 적용: S1 행 높이의 기준 범위다. 터치 기기이므로 **행 자체는 40~48px**, 체크 셀 히트 영역은 44px 이상(m6 v2 A-6)으로 한다. 2줄이 필요한 약품명 행만 예외로 두고 나머지는 1줄과 말줄임으로 처리한다. 헤더 높이는 행과 맞춘다.
- 단계: ⑥구체화 · 태그: [비주얼]
- 신뢰도: 0.85 (수치는 원문. 데스크톱 기준이라 터치에는 보정 필요)

#### C11. Material Design — 밀도와 터치 타깃
- 출처: [Material: Applying density](https://material.io/design/layout/applying-density.html), [Material density on the web (2020)](https://m2.material.io/blog/material-density-web), [Android 접근성: Touch target size](https://support.google.com/accessibility/android/answer/7101858)
- 유형: 가이드라인. **검색 발췌 기반**
- 핵심 디자인 결정
  - 기본 밀도의 터치 타깃은 **48×48dp 이상, 타깃 사이 8dp 이상**이다. iOS 권장은 44×44다.
  - 보이는 크기와 히트 영역은 다르다. 24dp 아이콘을 48dp 타깃 안에 둔다.
  - 압축 밀도는 데이터 테이블과 긴 폼에 맞다. 날짜 선택처럼 작은 입력에는 맞지 않는다.
  - 작은 타깃이 붙어 있어 키우면 겹치는 경우에는 부모가 터치를 대신 받는다(TouchDelegate).
- ePRIS 적용: **밀도는 시각 크기만 줄이고 히트 영역은 줄이지 않는다.** S1 체크 셀(76×44)은 iOS 기준은 맞지만 Android 48dp 기준에는 4dp 모자란다 → 기기 OS 확인. S5 메모 바텀시트와 S2 필터 바텀시트의 입력은 압축하지 않는다.
- 단계: ⑥구체화 · 태그: [원칙]
- 신뢰도: 0.7

#### C12. Emil Kowalski / Sonner — 빈도 기반 모션과 되돌리기 토스트
- 출처: Emil의 원칙은 **2차 요약만** 확인했다([review-animations 스킬](https://mcpservers.org/tr/agent-skills/emilkowalski/review-animations), [emil-design-eng](https://open-design.ai/zh/skills/emil-design-eng/)). Sonner API는 [shadcn/ui Sonner 문서](https://ui.shadcn.com/docs/components/sonner)와 [Sonner README](https://github.com/emilkowalski/sonner)(원문 열람, 설치 내용만 있음)로 확인했다.
- 핵심 디자인 결정
  - (2차) 키보드로 시작한 동작과 **하루 100회 이상 하는 동작에는 애니메이션을 넣지 않는다**. 하루 수십 회는 줄인 모션을 쓰고, 가끔 하는 동작에만 기본 모션을 쓴다.
  - (2차) UI 애니메이션은 300ms 미만으로 하고, ease-in과 scale(0) 등장은 쓰지 않는다.
  - Sonner: `action: { label: "Undo", onClick }`로 토스트에 되돌리기 버튼을 넣는다. `toast.promise`는 loading → success/error 전환을 한 토스트 안에서 처리한다.
  - (3자 가이드) 비파괴 액션 뒤에는 토스트 되돌리기를 쓰고, 파괴적 확인에는 다이얼로그를 쓴다.
- ePRIS 적용: m6 v2 §7의 "선택·체크 0ms, 토스트·확인창 150ms 페이드"를 지지한다. S3 저장은 **promise 토스트 1개**로 처리한다("감사 저장 중… → 감사 저장 10건 [되돌리기]"). 토스트를 여러 개 쌓지 않는다.
- 단계: ⑥구체화 · 태그: [원칙] [패턴]
- 신뢰도: 0.5 (빈도 임계값은 2차 해석. 원 강의 미확인)

#### C13. Stripe — 대시보드·Stripe Apps 패턴
- 출처: [Stripe Connect Dashboard docs](https://docs.stripe.com/docs/connect/dashboard), [Stripe Apps: Full-page apps](https://docs.stripe.com/stripe-apps/patterns/full-page-apps), [Stripe Apps: Filter controls](https://docs.stripe.com/stripe-apps/patterns/filter-controls), [Badge](https://edge-docs.stripe.com/stripe-apps/components/badge)
- 유형: 공식 문서. **검색 발췌 기반**. Stripe 디자이너의 1인칭 테이블 작업기는 찾지 못했다(a3의 공백과 같음).
- 핵심 디자인 결정
  - 상태 배지는 계정 상태(restricted, pending)를 빠르게 보여준다. **호버하면 맥락 정보**가 나오고, **상태 탭**을 누르면 상태별로 묶어 볼 수 있다.
  - 목록 뷰는 정렬 가능한 열, 상태 표시, 클릭 가능한 행을 갖춘 DataTable이다. **배지는 읽기 전용**이고 동작을 일으키지 않는다.
  - 필터는 **속성 하나당 칩 하나**다(상태, 등급 등). 칩을 누르면 메뉴가 열린다.
- ePRIS 적용: S2 필터 칩을 "처리 상태", "오더 상태", "약국" 같이 속성별로 하나씩 둔다. S1 배지는 탭해도 상태를 바꾸지 않는다(읽기 전용). 호버 대신 **배지 탭 → 툴팁**으로 맥락을 보여준다(터치 기기).
- 단계: ⑥구체화 · 태그: [패턴]
- 신뢰도: 0.55

#### C14. Airtable — 그리드 뷰 행 높이 옵션
- 출처: [Airtable support: Grid view](https://support.airtable.com/docs/grid-view), [커뮤니티: Row height](https://community.airtable.com/t/row-height-control-density-of-records-in-grid-view/9563)
- 유형: 제품 문서·커뮤니티. **검색 발췌 기반**
- 핵심 디자인 결정
  - 행 높이는 4단계(Short / Medium / Tall / Extra Tall)이고, **새 뷰의 기본값은 가장 촘촘한 Short**다. 행이 높을수록 줄바꿈 텍스트와 썸네일, 연결 레코드가 더 보인다.
  - 헤더 높이는 조정할 수 없다. 행 높이 일관성을 지키려고 헤더를 줄바꿈하지 않은 것은 의도였다고 한다. 사용자 반발이 있었다.
- ePRIS 적용: 밀도 옵션은 **최대 2단계**(기본/촘촘)로 제한하는 것을 검토한다. 사용자별 저장이다. 헤더 2줄 허용 여부는 긴 열 이름(예: "1회 투여량")이 있을 때 결정한다.
- 단계: ⑥구체화 · 태그: [패턴]
- 신뢰도: 0.55

#### C15. 토스 — 서체의 숫자 설계, TDS ListRow
- 출처: [토스피드: 서체 고민 없이 본질에만 집중할 수 있도록(토스 프로덕트 산스)](https://toss.im/tossfeed/article/beginning-of-tps), [TDS React Native ListRow](https://tossmini-docs.toss.im/tds-react-native/components/list-row/), 3자 [디자인 나침반: 토스증권 PC](https://designcompass.org/2024/07/19/toss-invest-pc/)
- 유형: 회사 1인칭 글(서체), 공식 문서, 3자 리뷰. **검색 발췌 기반**
- 핵심 디자인 결정
  - "본문용 서체의 숫자와 영문은 국문보다 조금 더 작은 크기로 디자인되어 있어요". 그래서 안드로이드·iOS·윈도우·크롬·사파리에서 **세로 메트릭을 테스트**했다.
  - TDS ListRow는 왼쪽(아이콘) / 가운데(contents) / 오른쪽(right) 3영역 구조다. 오른쪽 화살표와 수직 정렬을 설정할 수 있다.
  - (3자) 토스증권 PC는 숫자로 빽빽한 기존 증권 화면과 달리 정보 위계를 정리했다는 평가를 받았다(0.35).
- ePRIS 적용: S1 한글(약품명·용법)과 숫자(용량·시각)가 섞인 셀에서 **숫자가 작아 보이거나 기준선이 어긋나는지** 실제 폰트로 확인한다. S4 긴급 큐 항목을 ListRow 3영역(좌: 처리 표지 / 가운데: 환자·약품 / 우: 경과 시간)으로 구성한다.
- 단계: ⑥구체화 · 태그: [비주얼]
- 신뢰도: 0.5 (테이블 크래프트를 직접 다룬 토스 1인칭 글은 못 찾음)

#### C16. 배민사장님 앱 — 반복 업무용 주문 접수
- 출처: [App Store: 배민사장님](https://apps.apple.com/KR/app/id1042003297), [원티드: 우아한형제들 셀러웹프론트 인터뷰](https://www.wanted.co.kr/events/22_11_s01_b04)
- 유형: 앱 설명(공식), 개발자 인터뷰. **검색 발췌 기반**. 디자이너 1인칭 글은 없음
- 핵심 디자인 결정
  - 새 주문은 **유형별로 다른 알림음**과 푸시로 알린다. **오래된 주문을 목록 위에** 먼저 보여준다. '접수' 버튼과 예상 시간 선택으로 접수가 끝난다.
  - (인터뷰) 사장님들이 모바일 UI에 익숙하지 않아 어려워했다 → 디자이너·기획자가 UI 설계부터 다시 했고, **연령대별 만족도**를 고려했으며 디자인 시스템 작업을 진행했다.
- ePRIS 적용: S4 긴급 큐를 **대기 시간이 긴 순**으로 정렬하고 경과 시간을 표시한다(행 이동 금지 원칙과 충돌하지 않게 큐는 별도 영역). 긴급 처방 도착 알림을 소리로 구분할지는 병원 환경 확인 후 결정한다. ⚑ PM 확인 필요(알림음은 범위 밖일 수 있음).
- 단계: ②맥락수집 · ⑥구체화 · 태그: [패턴]
- 신뢰도: 0.4

#### C17. 의료기기 UI — 다크/저조도 테마
- 출처: [Emergo by UL: Dark mode vs light mode medical device UIs](https://emergobyul.com/news/dark-mode-vs-light-mode-medical-device-uis), [Glance: dark mode accessibility](https://thisisglance.com/learning-centre/can-dark-mode-actually-help-with-app-accessibility)
- 유형: 의료기기 HF 컨설팅사 글, 에이전시 블로그. **검색 발췌 기반**
- 핵심 디자인 결정
  - "The choice of UI theme should be adaptive to these conditions." 밝은 수술실부터 어두운 병실까지 환경이 다르다.
  - 순수 검정(#000) 대신 아주 어두운 회색(#121212 등)을 쓴다.
  - (에이전시) 난시가 있는 사용자는 처음 만든 다크 테마를 어려워했고, 대비와 글자 굵기를 조금 올린 뒤에 나아졌다.
- ePRIS 적용: 약제부 조제실은 보통 밝은 환경이다(**가설**, 맥락 확인 필요). 다크 테마는 이번 범위에서 **뒤로 미루고**, 토큰을 시맨틱 이름으로 유지해 나중에 바꿀 수 있게만 둔다(m6 v2 K4 방식과 같음). 야간 근무 사용 여부를 M7 질문에 넣는다.
- 단계: ②맥락수집 · 태그: [원칙] [근거(약함)]
- 신뢰도: 0.4

---

### 2. 기법 표 (작업 방식 단위)

| 기법 | 한 줄 방법 | 출처 |
|---|---|---|
| 크롬 덜어내기 | 사이드바·헤더·탭의 시각 무게를 낮추고 데이터 영역의 대비를 올린다 | C1 Linear |
| 가치 밀도로 평가 | "보이는 행 수"가 아니라 "가치 ÷ (시간 + 공간)"으로 시안을 비교한다 | C2 Ström |
| 그룹 간격 > 행 간격 | 묶음 사이 여백으로 같은 행 수를 덜 빽빽하게 읽히게 한다 | C2 Ström |
| tnum + 오른쪽 정렬 | 숫자 열은 `tabular-nums`, 오른쪽 정렬, 같은 소수 자릿수 | C4, C5, C6, C8 |
| 선택 시 굵기 고정 | 선택·호버 상태에서 font-weight를 바꾸지 않는다 | C5 Rauno |
| 시각 크기 ≠ 히트 영역 | 밀도는 그림만 줄이고 터치 영역은 44~48 유지 | C4, C11 |
| 빈 셀은 비운다 | "-"/"x" 대신 공백, 표 전체가 비면 이유와 다음 행동 | C6, C7 Primer |
| 행 액션 1개만 노출 | 나머지는 메뉴로 묶는다 | C6 Primer |
| 그룹 헤더 체크 | 소제목 행 체크로 그룹 전체 선택 | C8 Polaris |
| 위험 톤 절제 | warning/critical은 "absolutely necessary"일 때만 | C9 Polaris |
| 부분 완료 배지 | Incomplete / Partial / Complete 3단계 | C9 Polaris |
| 지연 스피너 | 150~300ms 뒤 표시, 최소 300~500ms 유지, "저장 중…" 라벨 | C4 Vercel |
| promise 토스트 | 진행 → 결과 → 되돌리기를 토스트 1개로 | C12 Sonner |
| 빈도 기반 모션 | 하루 100회 이상 하는 동작은 모션 0 | C12 Emil(2차), C5 |
| 속성당 칩 하나 | 필터 칩을 속성별로 나누고 건수를 보인다 | C13 Stripe, C3 Vercel |
| 대기 오래된 순 큐 | 오래 기다린 항목을 위에, 경과 시간 표시 | C16 배민 |

---

### 3. ePRIS에 바로 적용할 디자인 기법 Top 10

| # | 기법 | 적용 화면 | 구체 적용 | 출처 | 신뢰도 |
|---|---|---|---|---|---|
| 1 | 숫자 열에 tabular figures + 오른쪽 정렬 + 소수 자릿수 통일 | S1 약품 테이블(용량·횟수·일수·시각), S3 건수 | `font-variant-numeric: tabular-nums`. 사용 폰트의 tnum 지원 여부와 한글 대비 숫자 크기를 함께 확인한다 | C4·C5·C6·C8·C15 | 0.8 |
| 2 | 행 높이 40~48px + 헤더 높이 일치 + 1줄 말줄임(약품명만 2줄 예외) | S1 | Carbon md/lg 범위. 2줄 행은 약품명이 길 때만 쓴다 | C10·C6 | 0.7 |
| 3 | 시각은 압축하고 히트 영역은 유지(44 이상, 가능하면 48) | S1 체크 셀, S2 칩, S3 버튼 | 체크 셀 76×44 → 기기 OS가 Android면 48로 올리는 것을 검토 | C4·C11 | 0.75 |
| 4 | 선택·상태 변화 때 굵기와 레이아웃을 바꾸지 않는다 | S1 선택 행, 처리 표지 | 외곽선·채움·표지만 바꾼다. 바 슬롯 8px 상시 확보(m6 v2)와 같은 원리 | C5 | 0.8 |
| 5 | 환자 카드 헤더 = 그룹 선택 체크 | S1 | Polaris subheader 선택 패턴. G-12 제외 규칙과 제외 토스트를 함께 쓴다 | C8 | 0.8 |
| 6 | 위험 톤은 하나만, 최소로 | S1 배지, S3 확인창 | 빨강은 S-FL-03 전용(K3)이다. 외부 근거는 Polaris "only when absolutely necessary" | C9 | 0.75 |
| 7 | BID "감 1/2"를 부분 완료 표지로 | S1 처리 표지 | 반쯤 찬 아이콘 + "감 1/2" 텍스트. 색만으로 구분하지 않는다 | C9·C4 | 0.6 |
| 8 | 저장 피드백 = 지연 스피너 + promise 토스트 1개 + 되돌리기 | S3 | 버튼 라벨 "감사 저장 중…"(200ms 뒤 표시) → 토스트 "감사 저장 10건 [되돌리기]" 6초. 토스트를 쌓지 않는다. 낙관적 UI는 쓰지 않는다 | C4·C12 | 0.7 |
| 9 | 빈/희소/과밀/오류 4상태를 따로 디자인 | S1, S4, 연동 실패 | 필터 0건(일시적, "필터 해제"), 긴급 0건(마지막 갱신 시각), 연동 실패(경고 아이콘, "다시 시도", 내선). 빈 셀에 "-" 쓰는지는 약사 확인 | C6·C7·C4 | 0.7 |
| 10 | 필터 칩은 속성당 하나 + 건수, "일부만 표시 중" 명시 | S2 | "처리 상태 ▾ 미처리 12", 필터가 켜져 있으면 테이블 위에 "필터 적용 중 · 38건 중 12건" | C13·C3·C8 | 0.65 |

차순위 후보: 긴급 큐 대기 오래된 순 + 경과 시간(S4, C16, 0.45), 밀도 2단계 사용자 옵션(S1, C14·C6, 0.5), 크롬 무게 낮추기(S2 앱바, C1, 0.55).

---

### 4. 레퍼런스 카드 초안 (M3 이관 후보)

> ID는 m3b의 REF-101~113과 m3c와 겹치지 않도록 **REF-301부터** 임시로 붙였다. M3 통합 때 다시 매긴다.

```yaml
id: REF-301
type: 원칙
title: "숫자 열은 tabular figures + 오른쪽 정렬"
source: "https://github.com/primer/design (content/components/data-table.mdx); https://github.com/vercel-labs/web-interface-guidelines"
designer_or_org: "GitHub Primer, Vercel"
problem_it_solves: "용량·시각 숫자의 자릿수가 행마다 어긋나 비교가 느려진다"
applies_to: [S1]
evidence: "Right-align numeric values and use the tabular-num font variant when possible." (Primer)
why_needed: "약사의 핵심 과업이 행 간 용량 비교다(NN/g 비교 과업). 자릿수가 맞지 않으면 오독 위험이 있다"
cost: "폰트가 tnum을 지원하지 않으면 폰트를 바꾸거나 숫자 전용 폰트를 섞어야 한다. 종이 처방전이 왼쪽 정렬이라면 익숙함 비용이 있다(약사 확인)"
how_to_apply: "숫자만 있는 열은 오른쪽 정렬과 tnum. 숫자+단위 혼합 열(예: 5 mg)은 숫자 부분만 tnum, 정렬은 약사 확인"
confidence: 0.8
```

```yaml
id: REF-302
type: 패턴
title: "그룹(소제목) 행 체크로 그룹 전체 선택"
source: "https://github.com/Shopify/polaris (polaris.shopify.com/content/components/tables/index-table.mdx)"
designer_or_org: "Shopify Polaris"
problem_it_solves: "환자 한 명의 처방 여러 건을 하나씩 체크해야 한다"
applies_to: [S1, S3]
evidence: "Merchants can select a group of rows at once by clicking or Space keypressing a subheader row's checkbox"
why_needed: "하루 수백 건을 환자 단위로 감사한다. 그룹 선택이 없으면 탭 수가 행 수만큼 늘어난다"
cost: "선택 불가 행(D/C·HD 등)을 그룹 선택에서 뺄 규칙과 제외 안내가 필요하다(m6 G-12)"
how_to_apply: "환자 카드 헤더의 체크 = 선택 가능한 행만 선택, 제외 건수는 토스트로 알림"
confidence: 0.8
```

```yaml
id: REF-303
type: 원칙
title: "위험 톤(warning/critical)은 꼭 필요할 때만"
source: "https://github.com/Shopify/polaris (feedback-indicators/badge.mdx)"
designer_or_org: "Shopify Polaris"
problem_it_solves: "빨강·주황이 흔해지면 정말 위험한 신호가 묻힌다"
applies_to: [S1, S3]
evidence: "it should only be used when absolutely necessary"
why_needed: "ePRIS 원칙 1(놓치지 않게)의 최상위 신호(S-FL-03)를 지키는 외부 근거다(K3)"
cost: "파괴적 버튼에 빨강을 쓰지 않는 것이 일반 관습과 다르다(m6 J5, PM 확인 대기)"
how_to_apply: "빨강은 S-FL-03 전용 유지. 나머지 강조는 앰버·보라·텍스트·건수로 낸다"
confidence: 0.75
```

```yaml
id: REF-304
type: 원칙
title: "시각은 압축하되 히트 영역은 유지"
source: "https://github.com/vercel-labs/web-interface-guidelines; https://material.io/design/layout/applying-density.html"
designer_or_org: "Vercel, Google Material"
problem_it_solves: "밀도를 높이면 체크·칩을 잘못 누른다"
applies_to: [S1, S2, S3]
evidence: "If the visual target is smaller than 24px, expand its hit target… On mobile, use 44px" (Vercel) / "at least 48 x 48 dp, with at least 8dp of space" (Material, 검색 발췌)
why_needed: "잘못 누르면 엉뚱한 처방이 선택된다. 정확성이 최우선이다"
cost: "행 높이를 44 아래로 내릴 수 없다. 한 화면 행 수가 줄어든다"
how_to_apply: "행 40~48, 체크 셀 히트 44 이상(Android면 48), 칩 사이 8 이상"
confidence: 0.75
```

```yaml
id: REF-305
type: 패턴
title: "저장 피드백: 지연 스피너 + 결과 토스트 1개 + 되돌리기"
source: "https://github.com/vercel-labs/web-interface-guidelines; https://ui.shadcn.com/docs/components/sonner"
designer_or_org: "Vercel, Emil Kowalski(Sonner)"
problem_it_solves: "저장이 됐는지 확신할 수 없어 다시 누르거나 확인하러 간다"
applies_to: [S3]
evidence: "Require confirmation or provide Undo with a safe window." / 스피너 150–300ms 지연, 300–500ms 최소 표시 (Vercel)
why_needed: "감사 저장은 BESTCare 서명으로 이어진다. 결과와 되돌릴 길이 분명해야 한다"
cost: "되돌리기 = 배치 저장취소 API가 필요하다(G-14). ⚑ PM 확인 필요"
how_to_apply: "버튼 '감사 저장 중…' → 토스트 '감사 저장 10건 · 제외 2건 [되돌리기]' 6초. 서버 응답 뒤에만 행을 바꾼다"
confidence: 0.7
```

```yaml
id: REF-306
type: 패턴
title: "빈 셀·빈 표·오류 상태를 구분해 디자인"
source: "https://github.com/primer/design (data-table.mdx, empty-states.mdx)"
designer_or_org: "GitHub Primer"
problem_it_solves: "빈 화면을 보고 '없는 건지, 안 불러온 건지, 실패한 건지' 알 수 없다"
applies_to: [S1, S4]
evidence: "Show a Blankslate component in place of the table" / 빈 셀에는 "x"나 "-"를 쓰지 않는다
why_needed: "긴급 큐가 비었을 때 '정말 0건'인지 '연동 실패'인지 혼동하면 긴급 처방을 놓친다"
cost: "상태 화면 3~4종 추가. 빈 셀 '-' 관습을 바꾸면 익숙함 비용이 있다(약사 확인)"
how_to_apply: "필터 0건(필터 해제) / 긴급 0건(마지막 갱신 시각) / 연동 실패(경고 아이콘 + 다시 시도 + 내선)"
confidence: 0.75
```

---

### 5. 공백 (찾지 못한 것)

- **Stripe 디자이너의 테이블·배지 1인칭 작업기**: 이번에도 못 찾았다(a3와 같은 공백). Matthew Ström의 Stripe 대시보드 프로젝트 페이지는 검색됐지만 열지 못했다.
- **Linear 모바일(키보드 없는 상황)**: Linear iOS 앱의 리스트·스와이프 설계 글을 찾지 못했다.
- **Geist의 Table·Status Dot 원문**: vercel.com이 열리지 않았고 Geist는 GitHub에 문서가 없다. 3자 복제본만 있어서 쓰지 않았다.
- **Notion, Height, Attio, Retool, Raycast**: 데이터베이스·테이블 뷰 밀도에 관한 디자이너 글을 찾지 못했다. Raycast는 "A fresh look and feel"(compact 모드 언급)만 발췌로 확인했다(0.35, 카드 미작성).
- **국내**: 토스증권·토스 비즈니스·TDS 테이블, 당근 비즈니스·SEED 배지, 우아한형제들 사장님 디자인 시스템 모두 **디자이너 1인칭 글을 찾지 못했다.** 국내 출처는 서체 글(토스), 앱 설명, 개발자 인터뷰에 그친다.
- **스티키 열 + 가로 스크롤 그림자, 그룹 헤더(열 묶음 헤더) 디자인 근거**: Polaris sticky last column 외에 디자인 결정을 설명한 글이 없다.
- **의료 환경 다크 모드의 1차 연구**: 업체 글만 있다.

---

## 오케스트레이터에게

1. **REF ID 범위**: m3b(REF-101~)와 m3c가 겹치지 않도록 REF-301~306으로 임시 부여했다. M3 통합 때 재번호를 매겨야 한다.
2. **m6 v2와 대조할 점 3가지(검증 요청)**
   - 선택 행에서 글자 굵기가 바뀌는 곳이 없는지(C5). 
   - 체크 셀 76×44가 대상 기기 OS 기준(Android 48dp)에 맞는지(C11). 대상 태블릿 OS를 아직 확인하지 못했다.
   - 검토자·감사자 빈 칸 표기("-" 사용 여부, C6). 종이 처방전 관습과 부딪칠 수 있으므로 M7 질문 후보다.
3. **채택하지 않은 외부 권고**: 낙관적 업데이트(Vercel), 배지 라벨 과거형(Polaris). 각각 m6 v2 §7과 "바꿀 것만 바꾸기" 원칙 때문이다.
4. **⚑ PM 확인 필요**: 긴급 처방 알림음(C16), 배치 되돌리기 API(REF-305)는 범위·공수에 영향을 줄 수 있다.
5. **도구 제약**: 이 환경에서 WebFetch는 GitHub raw만 열렸다. 공식 블로그(Linear, Vercel, Stripe, 토스)는 원문을 확인하지 못했다. 원문 확인이 필요하면 브라우저로 직접 열어 인용을 검증해야 한다.

## 요약
- 고밀도 업무 UI의 크래프트는 **숫자 정렬(tnum), 히트 영역 유지, 상태 변화 때 레이아웃 고정, 위험 톤 절제, 저장 피드백 1개 토스트**로 수렴한다. 이 중 5개 규칙은 GitHub 원문(Primer, Polaris, Carbon, Vercel, Rauno)으로 확인했다.
- ePRIS Top 10과 REF-301~306 초안을 만들었다. 대부분 m6 v2 결정(K3, §7)을 뒷받침하고, 새로 점검할 항목은 3개(굵기, 48dp, 빈 셀 표기)다.
- 1인칭 작업기, 특히 Stripe·국내 업무 앱의 테이블 작업기는 여전히 공백이다.

## 신뢰도
- GitHub 원문을 확인한 카드(C4~C10): 0.8~0.85
- 공식 블로그·문서지만 검색 발췌만 본 카드(C1, C3, C11, C13, C14): 0.55~0.7
- 2차 해석이나 간접 출처(C2 일부, C12, C15~C17): 0.4~0.6
- Top 10 전체가 ePRIS에 효과가 있다는 판단: 0.65 (외부 원칙의 적용 판단이고 약사 검증 전이다. **가설**)

## 주의사항
- 디자인 시스템 문서는 데스크톱·마우스 기준이 많다(Carbon 행 높이, Primer 행 액션, Polaris shift 선택). 세로 태블릿 터치에는 보정이 필요하다.
- 외부 관습(빈 셀 비우기, 숫자 오른쪽 정렬, 밀도 옵션)이 종이 처방전의 익숙함과 부딪치면 익숙함을 우선한다. 바꾸기 전에 약사에게 확인한다(conventions §6-5).
- Emil Kowalski의 빈도 임계값(하루 100회)은 2차 해석이다. 그대로 인용하지 말고 "원칙 수준"으로만 쓴다.
- 1인칭 인용 중 원문을 열지 못한 것은 검색 엔진이 요약한 문구일 수 있다. 외부 공유 전에 원문을 확인한다.

## 다음 단계 제안
1. M3: REF-301~306을 `m3-references.md`로 옮기고, m3b·m3c와 함께 ID를 다시 매기고 중복을 정리한다.
2. M6: Top 10의 #1·#2·#3·#8을 v3 스펙(타이포·행 높이·로딩 토스트)에 넣고, 대상 기기 OS와 폰트의 tnum 지원을 확인한다.
3. M7: 약사 질문에 "빈 칸 '-' 표기", "숫자 정렬 방향", "야간 근무 중 사용 여부"를 추가한다.
4. 원문 확보: Linear part II, Matthew Ström 에세이, Vercel 배포 목록 체인지로그를 브라우저로 열어 인용을 검증한다.
