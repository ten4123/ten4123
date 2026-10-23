# A3. B2B·임상 업무 UI 디자이너들의 작업 방식 리서치

> 모듈: 도메인 리서처 (B2B·임상 업무 UI)
> 대상 프로젝트: 병원 약제부 전자처방검토 앱 (태블릿/데스크톱, 밀도 높은 처방 테이블, 행 체크 → 감사 저장/보류/반납, 약사 MEMO, 툴팁, 바코드 스캔)
> 조사 방법: WebSearch(standard)만 사용. 페이지 원문 열람은 불가해서 **검색 결과 발췌와 요약에 근거**했다. 인용문은 검색 발췌에 나온 문구이며, 원문 확인이 필요한 항목은 신뢰도를 낮췄다.
> 작성일: 2026-10-23

---

## 1. 요약 (공통 패턴)

- **현장 관찰을 먼저 한다.** Epic은 디자이너·개발자 전원이 병원 현장을 방문해야 하고, Abridge 디자이너는 의사를 shadowing한다. 프랑스 연구팀(JMIR HF 2025)은 처방분석 도구를 설계하기 전에 병원 약사의 실제 처방 분석 업무부터 체계적으로 관찰했다. 이들 모두 "사용자가 말하는 방식"보다 "실제로 하는 방식"을 근거로 삼는다.
- **테이블은 과업 단위로 설계한다.** NN/g은 테이블 과업을 ①조건으로 찾기 ②비교 ③한 행 보기·편집 ④다건 일괄 처리의 4가지로 나눈다. Stéphanie Walter는 "테이블을 디자인하기 전에 사용자가 그 테이블을 무엇에 쓰는지 리서치하라"고 권한다.
- **일괄 액션에는 정해진 문법이 있다.** Carbon 디자인 시스템 기준으로, 행을 선택하면 테이블 상단에 batch action bar가 나타난다. 전역 액션(필터·설정·내보내기)은 툴바에, 선택 대상 액션은 배치 바에 두어 둘을 분리한다. 되돌릴 수 없는 일괄 액션에는 건수를 명시한 확인 단계를 둔다.
- **밀도를 유지하면서 위계를 세운다.** Linear는 리디자인에서 "시각적 노이즈를 줄이고 hierarchy와 density를 높였다". Bloomberg는 복잡성을 숨기되, 폰트 하나나 버튼 위치 하나를 바꾸는 것도 숙련 사용자에게는 방해가 된다고 보고 변경을 신중히 한다. 숙련 사용자 도구에서는 익숙함 자체가 자산이다.
- **상태는 색만으로 표현하지 않는다.** Dynatrace, WCAG 1.4.1, Skedulo는 모두 색에 모양·아이콘·텍스트 라벨을 함께 쓰라고 한다. Dynatrace는 강조 아이콘을 "한 뷰에 하나"로 제한해 시각적 과부하를 막는다.
- **경고는 적고 역할에 맞아야 한다.** 약사가 받는 CDS 경고의 override율은 90%를 넘는다는 보고가 있다. 체계적 문헌고찰(JAMIA 2019)에서 경고 피로를 가장 효과적으로 줄인 방법은 **역할 맞춤형(role-tailored) 경고**였다. 경고 등급을 나누는 tiering과 저가치 경고 필터링도 권장된다.
- **우회 행동(workaround)이 설계 입력값이다.** 바코드 투약 시스템(BCMA)의 우회 행동 원인은 31가지가 확인됐다(Koppel 2008). 원인은 바코드 훼손, 스캐너 고장, 무선 끊김 같은 현장 요인이 많았다. 스캔 실패 경로를 처음부터 함께 설계해야 한다.
- **검증은 소수 인원으로 빠르게 반복한다.** 대표적인 방법은 RITE(3명 → 수정 → 3명, 문제가 없으면 2명 추가 후 종료), think-aloud, 시선 추적, 그리고 휴리스틱 평가다. 휴리스틱 평가에서는 약국정보시스템이 "일관성"과 "기억보다 인식" 원칙을 가장 많이 위반했다. Walter는 관찰형 피드백 세션과 다이어리 스터디를 병행하고, 결과를 노력 대비 가치로 우선순위화했다.

---

## 2. 작업기·사례 카드

> 단계: ①문제검증 ②맥락수집 ③레퍼런스 ④발산 ⑤수렴 ⑥구체화 ⑦검증(정성 피드백) ⑧학습기록
> 레퍼런스 태그: [비주얼] [패턴] [근거] [원칙]

### A. 제품팀·디자이너 1인칭 작업기

#### A1. Linear — "How we redesigned the Linear UI" (Karri Saarinen, 2부작)
- 출처: [Linear blog: How we redesigned the Linear UI](https://linear.app/blog/how-we-redesigned-the-linear-ui), [Changelog 2024-03-20](https://linear.app/changelog/2024-03-20-new-linear-ui), [Behind the latest design refresh](https://linear.app/blog/behind-the-latest-design-refresh), [Plushcap 요약(2차)](https://www.plushcap.com/content/linear/blog/linear-how-we-redesigned-the-linear-ui-part-ii)
- 핵심 작업 방식
  - 소규모 전담팀이 빠르게 결정했다. 제3자 요약에 따르면 흐름은 Figma 콘셉트 탐색 → stress test → 동작(behavior) 정의 → 프로토타입 → 내부 테스트·피드백 루프였다. 글 도입부에서는 "infinite-loop processes, workshops, or sticky notes"를 생략했다고 밝힌다.
  - 사이드바·탭·헤더·패널을 대상으로 "reduce visual noise … increase the hierarchy and density"를 목표로 했다.
  - 후속 리프레시의 원칙은 "not every element of the interface should carry equal visual weight"였다.
- 단계 매핑: ④발산 → ⑤수렴(stress test) → ⑥구체화(behavior 정의·프로토타입) → ⑦검증(내부 dogfooding)
- 태그: [비주얼] [원칙]
- 신뢰도: 0.7 (공식 블로그 발췌와 2차 요약이 섞여 있음. 세부 단계는 2차 요약 기반)

#### A2. Bloomberg Terminal UX팀 — "How Bloomberg Terminal UX designers conceal complexity"
- 출처: [Tech At Bloomberg](https://www.bloomberg.com/company/stories/how-bloomberg-terminal-ux-designers-conceal-complexity), 반론: [UX Magazine, The impossible Bloomberg makeover (2010)](https://uxmag.com/articles/the-impossible-bloomberg-makeover)
- 핵심 작업 방식
  - "We're hiding complexity"(CTO Shawn Edwards). 혼란과 워크플로 방해를 막는 것이 목적이다.
  - "Even something as simple as a font change or the relocation of a button can be disruptive." 혁신과 익숙함 사이에서 균형을 잡는다.
  - 밀도 높은 화면에서는 "clarifying the information hierarchy challenging"이라고 인정한다.
  - UX팀의 첫 단계는 **표준화**였다. 출시 후 문제를 고치는 working group에서, 개발 초기부터 참여하는 in-house 팀으로 바뀌었다.
- 단계 매핑: ①문제검증, ⑤수렴(표준화), ⑧학습기록(조직 변화)
- 태그: [원칙] [근거(반대 의견 포함)]
- 신뢰도: 0.75 (자사 기사. UX Magazine 비판은 2010년 의견)

#### A3. Epic UX팀 — 현장 방문 의무화
- 출처: [Healthcare IT News: A look inside Epic's EHR design and usability teams](https://healthcareitnews.com/node/528421)
- 핵심 작업 방식
  - "designs with clinicians rather than for them". 사내 임상가, 전문분과 steering committee, 사용자 컨퍼런스의 사용성 랩, 병원 현장 방문을 함께 쓴다.
  - "It's a requirement that everyone goes out into hospitals to see their work in action."(UX director Dana Close)
  - R&D 부사장 Sumit Rana가 ICU에서 4일 밤을 관찰했고, 이후 현장 관찰 프로그램이 공식화됐다.
- 단계 매핑: ②맥락수집, ⑦검증(컨퍼런스 사용성 랩)
- 태그: [원칙]
- 신뢰도: 0.7 (언론 기사. Epic 화면 설계의 세부 근거는 없음)

#### A4. Abridge — 임상가 shadowing + 분석 병행
- 출처: [Abridge Staff Product Designer 채용공고](https://remotejobs.org/remote-jobs/staff-product-designer-abridge), [Abridge blog: Clinician-builder career guide](https://www.abridge.com/blog/clinician-builder-career-guide)
- 핵심 작업 방식
  - "conducting interviews and shadowing sessions with doctors and other clinicians"
  - "combining insights from user feedback and analytics … quickly iterate"
  - "by clinicians, for clinicians"라는 슬로건 아래 임상가 출신 builder를 활용한다.
- 단계 매핑: ②맥락수집, ⑦검증
- 태그: [원칙]
- 신뢰도: 0.5 (채용공고와 자사 홍보 문구. 1인칭 프로세스 글은 미확인)

#### A5. Stéphanie Walter — 사내 엔터프라이즈 툴 리서치와 복잡한 테이블
- 출처: [Condens: UX Research for Internal Enterprise Tools](https://condens.io/blog/ux-research-for-internal-enterprise-tools), [Enterprise UX: essential resources to design complex data tables](https://stephaniewalter.design/blog/essential-resources-design-complex-data-tables/), [UXtweak 팟캐스트](https://www.uxtweak.com/podcast/stephanie-walter-building-trust-in-enterprise-projects/)
- 핵심 작업 방식
  - 10년 넘은 사내 툴을 재구축할 때 **데이터에서 출발**해 고영향 주제를 고르고, 인터뷰와 관찰 세션을 진행했다.
  - "observational feedback sessions, including a mix of usability testing and observational feedback" 방식에 **다이어리 스터디**를 더했다. 직원들은 하고 싶었던 과업, 할 수 없었던 일, 구 툴로 돌아간 순간을 기록했다.
  - 발견 사항은 "effort needed to build and the potential user or business value"로 정렬해 fast track과 big topics로 나눴다.
  - 테이블에 대해서는 "do your user research before designing tables … understand what they use those table for"라고 조언한다. URL, 필터, 키보드 내비게이션 같은 세부도 중요하게 본다(팟캐스트 소개).
- 단계 매핑: ①문제검증(데이터) → ②맥락수집 → ⑦검증(관찰형 피드백·다이어리) → ⑧학습기록(우선순위 백로그)
- 태그: [패턴] [원칙] [레퍼런스 큐레이션]
- 신뢰도: 0.75 (Condens 요약 기사. 4단계 중 뒷부분은 발췌가 잘려 미확인)

#### A6. Datadog — DRUIDS 디자인 시스템
- 출처: [Datadog blog: DRUIDS, the design system that powers Datadog](https://datadoghq.com/blog/engineering/druids-the-design-system-that-powers-datadog), [Figma 고객 사례](https://www.figma.com/customers/how-datadog-built-enterprise-platform-scaling-design-system/)
- 핵심 작업 방식
  - 엔지니어 사용자를 위해 "very dense data understandable"을 과제로 둔다(Figma 사례).
  - DRUIDS의 목표는 "easy to understand, implement, and contribute to"이며, 문서를 공개했다.
  - Design Lab 공고에서는 "hierarchy, density, and attention"을 시각 언어로 다룬다.
- 단계 매핑: ⑥구체화(시스템화)
- 태그: [원칙] [비주얼]
- 신뢰도: 0.55 (밀도 관련 1인칭 상세 글은 찾지 못함)

#### A7. Retool — Table 컴포넌트 재구축
- 출처: [Retool blog: Supercharging the Retool Table](https://retool.com/blog/supercharging-the-retool-table), [Retool changelog](https://docs.retool.com/changelog/weve-supercharged-the-table-component-agHVavZn)
- 핵심 작업 방식
  - 필터링, 정렬, 단일·다중 행 선택, 커스텀 액션 버튼을 기본 기능으로 제공한다.
  - **primary key로 선택 상태를 유지**한다. "maintains state, such as row selection or change sets, through complex filters, sorts, and pagination". 필터를 바꿔도 체크가 유지된다.
- 단계 매핑: ⑥구체화
- 태그: [패턴]
- 신뢰도: 0.65 (엔지니어링·기능 중심 글. 디자인 프로세스 서술은 없음)

### B. 리서치 기관·가이드라인·디자인 시스템

#### B1. NN/g — Data Tables: Four Major User Tasks / Designing Tables for Desktop Apps
- 출처: [NN/g: Data Tables](https://nngroup.com/articles/data-tables), [NN/g video: Designing Tables for Desktop Apps with Lots of Data](https://www.nngroup.com/videos/designing-tables-desktop-apps/)
- 핵심
  - 4대 과업: **조건으로 레코드 찾기 / 비교 / 단일 행 보기·편집·추가 / 다건 일괄 처리**
  - 비교 과업에는 카드보다 테이블이 낫다. 작업기억 부담이 적기 때문이다.
- 단계 매핑: ①문제검증(과업 정의), ③레퍼런스
- 태그: [원칙] [근거]
- 신뢰도: 0.7 (본문 전체가 아니라 요지만 확인)

#### B2. IBM Carbon — Data table (selection & batch actions)
- 출처: [Carbon data table usage](https://carbondesignsystem.com/components/data-table/usage/), [Carbon style](https://carbondesignsystem.com/components/data-table/style), [v10 style](https://v10.carbondesignsystem.com/components/data-table/style)
- 핵심
  - "A batch action toolbar appears when table rows are selected." 바는 테이블 상단에 나타나고, 취소하거나 선택을 해제하면 사라진다.
  - "The table toolbar is reserved for global table actions such as table settings, complex filter, export…". 전역 액션과 선택 대상 액션을 분리한다.
  - 배치 바는 브랜드 배경색이며, 높이는 기본 48px, small 32px이다(v10).
- 단계 매핑: ③레퍼런스, ⑥구체화
- 태그: [패턴] [비주얼]
- 신뢰도: 0.8

#### B3. 기타 배치 액션 레퍼런스 (Agriculture DS, Pega, Ashby)
- 출처: [Australian Agriculture DS: Selectable table with batch actions](https://design-system.agriculture.gov.au/patterns/selectable-table-with-batch-actions), [Pega UI Kit: Actions](https://docs-previous.pega.com/ui-kit-design-documentation/actions), [Ashby: Confirm destructive actions](https://www.ashbyhq.com/product-updates/confirm-destructive-actions)
- 핵심
  - 각 배치 액션은 선택 가능한 모든 행에 적용 가능해야 한다. 작은 버튼을 쓰고, Cancel로 닫는다(Agriculture DS).
  - "If bulk actions cannot be undone, provide a dialog confirming…". 액션이 3개를 넘으면 메뉴로 묶는다(Pega).
  - 건수가 많은 비가역 액션에는 마찰을 단계적으로 높인다. 24건을 넘으면 체크박스와 type-to-confirm을 함께 요구한다(Ashby).
- 단계 매핑: ③레퍼런스, ⑥구체화
- 태그: [패턴]
- 신뢰도: 0.65

#### B4. 상태 표시 — Dynatrace Strato HealthIndicator / WCAG 1.4.1
- 출처: [Dynatrace HealthIndicator usage](https://developer.dynatrace.com/design/components/content/HealthIndicator/usage/), [Skedulo color](https://design-studio.skedulo.com/knowledge/design-system/foundations/color), [WCAG 1.4.1 요약](https://www.disabilityworld.org/toolkit/standards/wcag/1-4-1-use-of-color/)
- 핵심
  - 상태는 색과 모양 또는 아이콘으로 함께 표시한다. shape는 낮은 강도의 보조 신호로 쓰고 **항상 라벨과 함께** 둔다. icon은 핵심 상태용이며 **한 뷰에 하나만** 권장한다(Dynatrace).
  - "never be conveyed using color alone"(Skedulo). 빨강과 초록 조합은 색각이상 사용자에게 문제가 된다.
- 단계 매핑: ⑥구체화
- 태그: [패턴] [원칙]
- 신뢰도: 0.75

#### B5. 엔터프라이즈 테이블 큐레이션 글 (UX Collective, Andrew Coyle, Pencil & Paper)
- 출처: [UX Collective: Designing better tables for enterprise applications](https://uxdesign.cc/designing-better-tables-for-enterprise-applications-f9ef545e9fbd), [Andrew Coyle: Designing tables](https://coyleandrew.medium.com/designing-tables-79a655ca183f), [Pencil & Paper 발췌 미러](https://scour.ing/@emschwartz/p/https://www.pencilandpaper.io/articles/ux-pattern-analysis-enterprise-data-tables), [Pleo Telescope 필터링 리소스](https://telescope.pleo.io/patterns/filtering/filtering.resources)
- 핵심
  - pattern library는 컴포넌트가 "어떻게" 동작하는지는 설명하지만 "언제" 쓰는지는 거의 다루지 않는다. 그래서 시나리오별 선택 기준이 필요하다(UX Collective).
  - Coyle은 엔터프라이즈 SaaS 테이블 기능을 정리했다. 예: fixed header, resizable columns.
  - Pencil & Paper는 "super user … depth of complexity for viewing, filtering, … actions"를 다룬다. 상호작용이 많아질수록 zebra striping은 관리하기 어려워진다고 본다. Pleo DS는 필터 방식별 장단점을 비교한 레퍼런스로 이 글을 인용한다.
- 단계 매핑: ③레퍼런스, ④발산
- 태그: [패턴] [비주얼]
- 신뢰도: 0.55 (대부분 발췌 수준)

### C. 임상·약제 도메인 연구 (근거)

#### C1. 병원 약사의 처방 분석 업무 체계적 관찰 (Butruille et al., JMIR Human Factors 2025)
- 출처: [PMC12048037](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC12048037/), [JMIR HF e65959](https://humanfactors.jmir.org/2025/1/e65959)
- 핵심
  - HFE 3단계 중 "exploration phase"가 중요하지만 문헌에서 자주 간과된다고 지적한다. 그래서 약사의 처방 분석 업무를 **설계 전에 체계적으로 관찰**했다.
  - "Understanding pharmacists' tasks and challenges is vital for creating user-centered solutions."
  - 결과 수치(과업, 시간, 문제점)는 검색 발췌에 없어 확인하지 못했다.
- 단계 매핑: ①문제검증, ②맥락수집
- 태그: [근거] — **본 프로젝트와 도메인이 가장 가깝다. 원문 정독을 권한다.**
- 신뢰도: 0.7 (방법론 프레이밍만 확인)

#### C2. Birmingham Free Clinic 약국 contextual inquiry (RxMAGIC)
- 출처: [JMIR preprint 51921 관련 결과](https://preprints.jmir.org/preprint/51921/accepted) / 검색 요약
- 핵심: 약사 3명을 관찰한 뒤 13개 테마를 도출했고, **약사가 직접 중요도를 순위화**했다. 이를 바탕으로 처방관리·재고 프레임워크를 제안했다.
- 단계 매핑: ②맥락수집 → ⑤수렴(사용자 참여 우선순위화)
- 태그: [근거] [원칙]
- 신뢰도: 0.5 (출처 링크 매칭이 불확실함. 검색 요약 기반)

#### C3. CDS 경고 피로 — 역할 맞춤·티어링
- 출처: [Hussain, Reynolds & Zheng, JAMIA 2019 (PMC6748819)](https://pmc.ncbi.nlm.nih.gov/articles/PMC6748819), [PSNet 요약](https://psnet.ahrq.gov/issue/medication-safety-alert-fatigue-may-be-reduced-interaction-design-and-clinical-role-tailoring), [BMJ Health Informatics 초록 (North York General)](https://informatics.bmj.com/content/29/Suppl_1/A2.2), [PMC9754301](https://pmc.ncbi.nlm.nih.gov/articles/PMC9754301), [Pharmacists' perceptions on DUR alerts (PMC10366836)](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC10366836/)
- 핵심
  - 경고 피로를 줄이는 데 가장 효과적인 개입은 **role tailoring**(처방의와 약사에게 다른 경고 세트를 주는 것)이었다.
  - 약사가 전체 CDS 경고의 절반 이상을 처리한다. 약사 1인당 하루 약 60건이며, override율은 90%를 넘는다. 이 부담을 줄이려고 **customizable filters**를 시도했다(North York).
  - DUR 경고의 낮은 신호 대 잡음비(SNR)가 중요한 경고를 놓치게 만든다.
- 단계 매핑: ①문제검증, ③레퍼런스(근거)
- 태그: [근거]
- 신뢰도: 0.75 (리뷰 결론은 신뢰. 개별 수치는 초록 수준)

#### C4. 처방검토 시스템 경고 등급화 (중국 3차 병원 PPRS)
- 출처: [PMC12220340](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC12220340/)
- 핵심: 경고 수준을 7단계로 나누고 사용자 규칙 3,015개를 운용했다. 도입 후 부적절 처방 비율이 감소했다. 단, 전후 비교라서 UI 효과만 따로 분리할 수는 없다.
- 단계 매핑: ⑥구체화(등급 체계)
- 태그: [근거]
- 신뢰도: 0.6

#### C5. 바코드 투약(BCMA) 우회 행동 (Koppel et al., JAMIA 2008)
- 출처: [JAMIA 15(4):408](https://academic.oup.com/jamia/article/15/4/408/731255), [PMC2442264](https://pmc.ncbi.nlm.nih.gov/articles/PMC2442264), [ScienceDaily](https://www.sciencedaily.com/releases/2008/07/080701083525.htm), [Patient Safety Solutions 2020](https://www.patientsafetysolutions.com/docs/September_2020_More_on_Workarounds.htm)
- 핵심
  - 5개 병원에서 약 30.8만 건의 투약을 분석해 **우회 행동의 원인 31개**를 도출했다. 원인에는 바코드 훼손·누락, 스캐너 오작동, 손목밴드 판독 불가, 무선 끊김 등이 있다.
  - 시스템이 "일상 워크플로와 충돌"할 때 지름길이 생기고, 그 지름길이 안전 위험이 된다.
  - 2020년 네덜란드 관찰 연구에서는 투약 약 6,000건 중 62.7%에 우회 행동이 있었다(2차 인용).
- 단계 매핑: ②맥락수집(우회 행동 관찰), ①문제검증
- 태그: [근거]
- 신뢰도: 0.7 (수치는 2차 요약 기반이므로 원문 확인 권장)

#### C6. Tall Man lettering (ISMP/FDA)
- 출처: [ISMP Look-Alike Tall Man Letters PDF](https://online.ecri.org/hubfs/ISMP/Resources/ISMP_Look-Alike_Tallman_Letters.pdf), [ECRI/ISMP 블로그](https://home.ecri.org/blogs/ismp-resources/look-alike-drug-names-with-recommended-tall-man-mixed-case-letters), [FDA Name Differentiation Project](https://www.fda.gov/drugs/medication-errors-related-cder-regulated-drug-products/name-differentiation-project)
- 핵심
  - 이름이 달라지는 부분을 대문자로 강조한다(예: vinBLAStine / vinCRIStine). 색이나 굵기와 결합할 수 있다.
  - 효과 근거는 엇갈린다. ISMP는 "one among numerous strategies"로 권장한다.
  - 화면(EHR/CPOE)에 적용하는 구체 지침은 이번 검색에서 확인하지 못했다.
- 단계 매핑: ⑥구체화
- 태그: [원칙] [근거(혼재)]
- 신뢰도: 0.7

#### C7. 사용성 평가 방법 — 휴리스틱 / think-aloud / 시선추적 / RITE
- 출처: [이란 국가 약국정보시스템 휴리스틱 평가](https://repository.brieflands.com/items/9b55fa39-51de-481c-ba31-f3db79696db7/full), [e-prescribing 사용자 경험 혼합연구 (PMC7126479)](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC7126479/), [GitLab Handbook: RITE](https://handbook.gitlab.com/handbook/product/ux/ux-research/rite), [DONE-RITE (수술 평가 도구)](https://corescholar.libraries.wright.edu/obgyn/88)
- 핵심
  - 약국정보시스템에서 가장 많이 위반된 휴리스틱은 **"consistency and standards"와 "recognition rather than recall"**이었다.
  - 전자처방 화면의 안전 영향을 탐색하는 방법으로 eye-gaze tracking과 think-aloud가 제안됐다.
  - RITE 진행 방식: 3명 → 수정 → 새로운 3명 → 문제가 없으면 2명 추가 → 총 5명에서 문제가 없으면 종료(GitLab). 임상 변형인 DONE-RITE는 UI 문제는 초심 사용자에게, 도메인 문제는 전문가에게 맡긴다.
- 단계 매핑: ⑦검증(정성 피드백)
- 태그: [원칙] [근거]
- 신뢰도: 0.7 (DONE-RITE는 소규모 포스터 수준이라 0.4)

#### C8. 약사 참여형 설계 사례 (인도네시아 통합 EMR·처방, Mataram 약국모듈, Hvidovre)
- 출처: [UMSIDA preprint 11855](https://archive.umsida.ac.id/index.php/archive/preprint/view/11855), [J-Cosine (Univ. Mataram)](https://jcosine.if.unram.ac.id/index.php/jcosine/article/view/672), [Pharmacy 2023 (PMC10037631)](https://pmc.ncbi.nlm.nih.gov/articles/PMC10037631/)
- 핵심: 관찰, 인터뷰, 포커스그룹, 문서분석을 결합한 participatory design을 썼다. 약국 직원이 포함된 8명이 참여했고, 프로토타입에 **약국 검증(pharmacy verification) 단계**를 넣었다.
- 단계 매핑: ②맥락수집 → ④발산 → ⑦검증
- 태그: [근거]
- 신뢰도: 0.5 (프리프린트, 소규모 표본)

#### C9. 국내 EMR 사용성 (응급실 설문 2022) / 국내 병원 차세대 EMR 기사
- 출처: [응급실 EMR 사용성 문제 연구](https://oak.ulsan.ac.kr/handle/2021.oak/14224), [ETNews: HIS 3.0](https://m.etnews.com/20150407000217), [이투데이: 연세의료원](https://www.etoday.co.kr/news/view/1081598)
- 핵심
  - 국내 응급실 의사 103명과 간호사 97명을 설문한 결과, **환자 선택 단계**에서 사용성 문제가 가장 많았다. 원인은 낮은 가시성과 구분성이었고, 연구는 시각적 개선을 권고했다.
  - 세브란스·서울대·삼성서울 관련 기사는 기술 전환(WPF, AI 통합)이나 "한눈에" 같은 표현 수준이다. **디자이너가 쓴 1인칭 작업기는 찾지 못했다.**
- 단계 매핑: ①문제검증
- 태그: [근거]
- 신뢰도: 0.55

#### C10. 약사 검증 화면 — 우선순위 큐 (특허) / 모바일 검증
- 출처: [US 특허 8682042](https://image-ppubs.uspto.gov/dirsearch-public/print/downloadPdf/8682042), [JAMIA 27(2):284](https://academic.oup.com/jamia/article/27/2/284/5593605)
- 핵심
  - 처방 검토 큐를 **STAT 우선, 그다음 접수 시각 순**으로 자동 정렬한다(특허 설명. 사용성 평가는 아님).
  - 회진 중 모바일로 검증하면 검증까지 걸리는 시간이 줄었다(7.5분 대 38.9분). 다만 작은 키보드와 네트워크 끊김이 문제로 보고됐다(2013 연구, 검색 요약).
- 단계 매핑: ③레퍼런스, ⑥구체화
- 태그: [패턴] [근거]
- 신뢰도: 0.5

---

## 3. 이 프로젝트(약제부 처방검토 앱)에 바로 적용할 수 있는 패턴 후보

| # | 패턴 | 왜 (이 앱 맥락) | 출처 |
|---|---|---|---|
| 1 | **설계 전 약사 업무 관찰(2~3명, 반나절 단위)**: 실제 처방 검토 순서, 필터 조합, 보류·반납 사유, 메모 습관, 바코드 사용 시점을 기록한다 | 약사의 처방분석 업무는 문헌에서도 "탐색 단계"가 간과된다고 지적된다. 체크 → 감사 저장 흐름의 실제 순서를 확보해야 한다 | C1, A3, A4, C2 |
| 2 | **관찰 테마는 약사가 직접 우선순위화**한다 | 디자이너가 짐작으로 정한 우선순위를 막고, 정성 피드백 문화와도 맞는다 | C2, A5 |
| 3 | **테이블 과업을 4가지로 분해해 화면 영역에 매핑**한다: 찾기=필터바(접수약국·오더구분·병동·약품구분·팀), 비교=테이블, 단일 행=MEMO·툴팁·상세 패널, 일괄=감사 저장/보류/반납 | 기능 나열이 아니라 과업 기준으로 레이아웃 근거를 세울 수 있다 | B1, A5 |
| 4 | **전역 툴바와 선택 시 나타나는 배치 액션 바를 분리**한다. 바에는 "N건 선택됨"과 감사 저장/보류/반납, 취소를 둔다 | 필터·내보내기 같은 전역 액션과 행 대상 액션이 섞이면 오조작이 생긴다 | B2, B3 |
| 5 | **필터·정렬·페이지가 바뀌어도 행 선택을 유지**한다(처방번호를 key로 사용). 숨은 선택 건수도 표시한다 | 병동 필터를 바꾸는 사이에 체크가 풀리거나, 보이지 않는 행이 함께 처리되는 사고를 막는다 | A7 |
| 6 | **가역성에 따라 확인 강도를 달리한다.** 감사 저장·보류는 undo 토스트로, 반납처럼 되돌리기 어렵거나 대량인 처리는 건수를 명시한 확인 대화상자로 처리한다(Cancel에 기본 포커스) | 모든 처리에 확인창을 띄우면 클릭 습관이 생긴다. 반대로 대량 반납은 마찰이 필요하다 | B3 |
| 7 | **상태(미검토/감사완료/보류/반납/경고)는 색 + 모양·아이콘 + 텍스트 라벨로 표시**한다. 강조 아이콘은 한 뷰에 한 종류로 제한한다 | 밀도 높은 테이블에서 색만 쓰면 판별이 어렵다. 색각 이상과 태블릿 눈부심 환경에도 대비해야 한다 | B4 |
| 8 | **경고 표시를 등급화하고 약사 역할에 맞춘다.** 고위험만 인터럽트하고 나머지는 행 내 배지·툴팁으로 처리한다. 경고 필터도 제공한다 | 약사의 override율은 90%를 넘고 하루 약 60건을 처리한다. 경고가 테이블을 덮으면 중요한 신호를 놓친다 | C3, C4 |
| 9 | **Look-alike 약품명에 Tall Man 표기**를 적용한다(약품명 열·툴팁) | 밀도 높은 테이블에서는 약품명 오인 위험이 크다. 근거는 혼재하지만 ISMP 권장 전략이다 | C6 |
| 10 | **바코드 스캔 실패 경로를 처음부터 설계**한다. 수동 입력 대체 경로, 스캔 실패 사유 기록, 네트워크 끊김 상태 표시가 필요하다 | BCMA 우회 행동의 원인 다수가 현장 하드웨어와 환경 문제였다. 실패 경로가 없으면 우회 행동이 생긴다 | C5, C10 |
| 11 | **변경 최소화와 익숙함 존중**: 기존 시스템의 열 순서, 단축키, 용어를 지도화한 뒤 바꿀 것만 바꾼다 | 숙련 사용자에게는 버튼 위치 하나도 방해가 된다. "consistency"는 약국 시스템에서 가장 많이 위반된 휴리스틱이다 | A2, C7 |
| 12 | **밀도는 유지하고 시각적 무게에 차등**을 둔다. 크롬(사이드바·헤더)은 낮추고 데이터와 상태를 높인다 | 처방 테이블의 정보량은 줄일 수 없으므로 위계로 해결해야 한다 | A1, A6 |
| 13 | **기억 대신 인식**: 현재 적용된 필터를 칩으로 상시 노출하고, 약품·처방 정보는 툴팁으로 즉시 보여준다 | "recognition rather than recall" 위반이 약국 시스템에서 빈번했다. 응급실 연구에서도 가시성과 구분성이 핵심 문제였다 | C7, C9, B5 |
| 14 | **정성 검증은 RITE 방식**으로 진행한다. 약사 3명 think-aloud → 즉시 수정 → 새로운 3명. 도메인 문제는 숙련 약사, UI 문제는 신규 약사에게 맡긴다 | A/B 테스트를 하지 않는 조건에서 소수 인원으로 빠르게 수렴할 수 있다 | C7 |
| 15 | **출시 후 관찰형 피드백과 다이어리**를 운영한다. "못 한 일, 구 시스템으로 돌아간 순간"을 기록하게 하고, 노력×가치로 fast track과 big topic을 나눈다 | 학습 기록(⑧)과 다음 반복의 백로그를 동시에 만들 수 있다 | A5 |
| 16 | **STAT 우선 + 접수 시각 순 기본 정렬**을 후보로 둔다 | 처방 검토는 긴급도가 첫 번째 축이다. 다만 근거가 특허 수준이므로 관찰로 검증해야 한다 | C10 |

---

## 4. 공백과 한계

- **원문 미열람**: 모든 내용은 검색 발췌와 요약 기반이다. 인용문은 발췌 문구이며, 특히 C1(Butruille 2025)의 결과, Linear 2부작 본문, NN/g 본문, Pencil & Paper 본문은 직접 정독해야 한다.
- **1인칭 작업기가 부족하다**: Stripe Dashboard, Palantir, Oscar Health, One Medical, Airtable은 채용공고나 2차 자료만 나왔다. 디자이너가 직접 쓴 프로세스 글은 찾지 못했다. Retool·Datadog도 기능과 시스템 소개 위주이고 탐색·수렴 과정 서술은 없다.
- **국내 사례가 없다**: 세브란스·서울대병원·삼성서울 EMR의 UX 디자이너 작업기와 국내 약제부 처방검토 화면 사용성 연구는 이번 검색에서 확인하지 못했다. 다음 후보로는 대한병원약사회지, 대한의료정보학회 발표록, 토스·당근·우아한형제들 기술블로그의 어드민 글이 있다.
- **SAP Fiori, Atlassian 상세 지침 미확보**: Fiori의 Semantic Colors·Responsive Table, Atlassian dynamic table의 밀도 관련 지침은 내비게이션 페이지만 잡혔다.
- **ISMP의 화면 표시 지침 미확보**: Tall Man lettering을 CPOE와 약국 소프트웨어 화면에 적용하는 구체 지침, 그리고 BCMA UI 레이아웃 지침은 찾지 못했다.
- **근거 강도의 편차**: 경고 피로 수치(override율 90% 이상, 하루 약 60건)는 단일 기관 초록이다. BCMA 수치는 2차 요약이다. 중국 PPRS는 전후 비교 연구다. C2의 링크 매칭은 불확실하다.
- **임상 환경 특유의 검증 실무**: 근무 중 약사 리크루팅, 검증 중 발견된 안전 이슈 처리 같은 실무 가이드는 찾지 못했다.
