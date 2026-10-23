# M3-c 화면별 비주얼·패턴 레퍼런스 수집: ePRIS

> 수집 전용 파일이다. 큐레이션·감사(채택/보류/기각)는 다음 웨이브의 M3 통합에서 한다. 아래 카드의 `status`는 모두 **미감사**다.
> 관찰 ID는 `docs/03-project-brief-epris.md`의 O1~O9를 쓴다. M1이 아직 O# 체계를 통합하지 않았으므로 `docs/05-epris-status-review.md`의 N#·F#는 괄호로 함께 적는다.

## v1 (2026-10-23)

### 0. 수집 방법과 한계 (먼저 읽을 것)

- **WebFetch가 모두 실패했다.** sap.com, polaris-react.shopify.com, linear.app, m3.material.io, mobbin.com, carbondesignsystem.com, epicresearch.org는 `getaddrinfo ENOTFOUND`(DNS)로 실패했다. developer.apple.com은 열렸지만 본문이 비어 있었다. 그래서 **모든 카드는 WebSearch 발췌에 기반한다.** 이미지와 실제 화면은 하나도 직접 확인하지 못했다. 신뢰도는 0.65를 넘지 않게 했다.
- **Mobbin·Refero·Page Flows·Godly는 검색 결과에 화면 페이지가 나오지 않았다.** 로그인이나 유료 벽이 있거나 색인이 안 된 것으로 보인다. 따라서 "실제 제품 화면" 요구는 **디자인 시스템 문서 예시와 제품 도움말 문서**로 대신했다. 화면 캡처는 사람이 직접 확인해야 한다. 확인할 검색 경로는 §5에 적었다.
- Dribbble 검색은 약국 대시보드 컨셉 샷만 나왔다(실제 제품이 아님). 기준(실제 제품 우선)에 맞지 않아 카드로 만들지 않았다.
- 텍스트 스케치는 **출처 설명을 바탕으로 내가 재구성한 구조**다. 원본 화면을 옮긴 것이 아니다.

카드 형식: conventions §4에 `screen`, `ref_tags`(4종 중 해당하는 것 전부), `look_at`(참고할 축), `sketch`, `status`를 더했다.

---

### S1 처방 목록 (환자 카드 + 15~20열 가로 스크롤 테이블 + 스티키 열)

```yaml
id: REF-301
type: 패턴
ref_tags: [패턴, 원칙]
screen: S1
title: "SAP Fiori for iOS: Data Table, 스티키 헤더와 스티키 첫 열"
source: "https://www.sap.com/design-system/fiori-design-ios/v25-8/components/data-table/usage"
designer_or_org: "SAP Fiori Design (iOS)"
problem_it_solves: "좁은 폭(compact)에서 다열 테이블을 가로 스크롤로 보여 주면서 행 식별자와 열 이름을 잃지 않게 한다"
applies_to: [O3, O9]
evidence: "검색 발췌: 가로 스크롤 테이블에 스티키 헤더와 스티키 첫 열을 두며 compact·regular 폭 모두 지원한다. compact 폭에서는 가로 스크롤과 스티키 헤더를 권한다."
look_at: "레이아웃(고정 영역/스크롤 영역 경계), 밀도(compact vs regular 행 높이)"
sketch: |
  ┌────────┬──────────────────────────────→
  │ 약품명  │ 용량 │ 용법 │ 일수 │ ... (스크롤)
  ├────────┼──────────────────────────────
  │ (고정)  │                              
  └────────┴──────────────────────────────
  헤더 행은 세로 스크롤에도 고정, 첫 열은 가로 스크롤에도 고정
why_needed: "(초안) 20열을 세로 태블릿에 넣으면 가로 스크롤은 피할 수 없다. 스크롤 중에 약품명이 사라지면 어느 행의 값인지 놓친다(원칙 '놓치지 않게')"
cost: "(초안) 고정 열만큼 스크롤 영역이 줄어든다. 고정 열과 본문의 스크롤 동기화 구현 비용"
how_to_apply: "M3 감사 때 결정"
confidence: 0.5
status: 미감사
```

```yaml
id: REF-302
type: 원칙
ref_tags: [원칙, 패턴]
screen: S1
title: "SAP Fiori for Android: 스티키 첫 열은 화면 폭의 30% 이하"
source: "https://experience.sap.com/fiori-design-android/data-table"
designer_or_org: "SAP Fiori Design (Android)"
problem_it_solves: "고정 열이 너무 넓어 스크롤 영역을 잡아먹는 문제"
applies_to: [O3]
evidence: "검색 발췌: 첫 열은 모바일에서만 선택적으로 스티키이며 화면 폭의 30%로 제한한다."
look_at: "레이아웃(고정 열 폭 상한)"
sketch: |
  |<- ≤30% ->|<------- ≥70% 스크롤 ------->|
why_needed: "(초안) ePRIS 스티키 열 후보가 여럿(약품명·상태·선택 체크)이라 폭 상한이 없으면 고정 영역이 커진다. 수치로 된 상한이 있으면 M4·M6에서 판단하기 쉽다"
cost: "(초안) 약품명이 길면 30% 안에서 줄임 처리가 필요하다. 줄임은 약품 오인 위험이 있다(ISMP 계열 우려, REF-306)"
how_to_apply: "M3 감사 때 결정"
confidence: 0.5
status: 미감사
```

```yaml
id: REF-303
type: 패턴
ref_tags: [패턴, 비주얼]
screen: S1, S3
title: "Shopify Polaris IndexTable: 마지막 열 고정(lastColumnSticky)과 일괄 액션"
source: "https://polaris-react.shopify.com/components/tables/index-table"
designer_or_org: "Shopify Polaris"
problem_it_solves: "가로로 긴 목록에서 행 단위 상태·액션 열을 항상 보이게 하고, 여러 행에 같은 작업을 건다"
applies_to: [O1, O3]
evidence: "검색 발췌: props에 lastColumnSticky가 있고 첫 열 고정 옵션은 없다. bulkActions·promotedBulkActions가 있고, condensed는 490px 미만 화면에서만 권장한다."
look_at: "레이아웃(오른쪽 끝 상태 열 고정), 인터랙션(승격된 일괄 액션 vs 더보기)"
sketch: |
  ┌☐┬약품명┬──── 스크롤 ────┬상태(고정)┐
  │☐│ ...  │                │ 감사 ●   │
why_needed: "(초안) 약사가 가로 스크롤 중에도 행 상태(검토·감사·보류)를 보아야 한다면 상태 열을 오른쪽에 고정하는 대안이 생긴다. 왼쪽 고정만 있는 REF-301과 비교할 축"
cost: "(초안) 양쪽 고정이면 세로 태블릿에서 스크롤 영역이 더 줄어든다. 종이 처방전의 열 순서가 바뀐다(⚑ PM 확인 필요 가능성)"
how_to_apply: "M3 감사 때 결정"
confidence: 0.5
status: 미감사
```

```yaml
id: REF-304
type: 패턴
ref_tags: [패턴, 비주얼]
screen: S1, S5
title: "SAP Fiori Dynamic Page Header: 접혀도 핵심 수치(KPI)는 제목 줄에 남는다"
source: "https://www.sap.com/design-system/fiori-design-web/v1-139/page-types/page-layouts/dynamic-page-layout/usage"
designer_or_org: "SAP Fiori Design (Web)"
problem_it_solves: "헤더를 접어 공간을 확보할 때 판단에 필요한 핵심 정보가 사라지는 문제"
applies_to: [O3, O5]
evidence: "검색 발췌: 헤더 콘텐츠는 접히면 숨겨지지만, 태그·KPI 같은 핵심 정보는 제목 줄 가운데에 두어 가능한 한 오래 보인다. 접힌 상태의 부제는 가장 중요한 정보를 요약하는 데 쓴다."
look_at: "위계(펼침 헤더 vs 접힘 제목 줄), 인터랙션(스크롤 시 스냅)"
sketch: |
  펼침: [환자 더미01 · 병동]          [접기]
        Scr 1.2 | CrCl 45 | BSA 1.6 | 체중 58
        알레르기 · 진단 · 메모 ...
  접힘: [환자 더미01] CrCl 45 · BSA 1.6   [펼치기]
why_needed: "(초안) N9/F07(환자 카드를 접으면 판단 수치가 사라짐)에 직접 대응한다. '접어도 2~3개 수치는 남긴다'는 제안의 외부 선례"
cost: "(초안) 접힘 상태에 남길 수치를 약국별로 정해야 한다(항암=BSA, 입원=CrCl 등). 정의 비용과 약사 합의가 필요"
how_to_apply: "M3 감사 때 결정"
confidence: 0.55
status: 미감사
```

```yaml
id: REF-305
type: 근거
ref_tags: [근거]
screen: S1
title: "가로 스와이프와 OS 가장자리 제스처 충돌, iPad 고정 열 동기화 깨짐"
source: "https://ninjatables.com/sticky-headers-vs-fixed-columns/ ; https://datatables.net/forums/discussion/comment/52508/"
designer_or_org: "Ninja Tables(벤더 블로그), DataTables 포럼"
problem_it_solves: "가로 스크롤 테이블의 터치 기기 위험을 미리 안다"
applies_to: [O3]
evidence: "검색 발췌: 가로 스와이프가 iOS 가장자리 뒤로가기 제스처를 유발할 수 있다. iPad의 탄성 스크롤에서 고정 열과 헤더 동기화가 깨진다는 보고가 있고 확인된 해결책은 없었다."
look_at: "인터랙션(스와이프 시작 영역, 스크롤 동기화)"
sketch: "해당 없음(위험 메모)"
why_needed: "(초안) S1은 가로 스크롤이 전제다. 개발 착수 전 프로토타입에서 확인할 위험 목록에 넣을 근거"
cost: "(초안) 없음(정보성). 다만 벤더 블로그와 포럼 1건이라 근거가 약하다"
how_to_apply: "M3 감사 때 결정"
confidence: 0.35
status: 미감사
```

```yaml
id: REF-306
type: 근거
ref_tags: [근거, 원칙]
screen: S1, S5
title: "ISMP Canada 2018: eMAR 표시 방식이 용량 오류에 기여한 사례"
source: "https://www.ismp-canada.org/download/safetyBulletins/2018/ISMPCSB2018-i8-eMAR.pdf"
designer_or_org: "ISMP Canada"
problem_it_solves: "투약 화면에서 용량·용적 표시가 오독되는 위험"
applies_to: [O3, O5]
evidence: "검색 발췌: 페노바르비탈 6배 용량 사망 사례를 eMAR 표시 문제와 연결하고, 이런 시스템에 인적 요인 원칙이 빠져 있다고 지적한다."
look_at: "타이포(용량·단위 열의 크기와 정렬), 위계"
sketch: "해당 없음(근거)"
why_needed: "(초안) 열을 좁히고 글자를 줄이는 밀도 조정(O3)이 용량 열에도 적용되면 오독 위험이 생긴다. 밀도 조정의 하한선 근거"
cost: "(초안) 용량·단위 열은 줄일 수 없어 다른 열이 더 좁아진다"
how_to_apply: "M3 감사 때 결정"
confidence: 0.45
status: 미감사
```

### S2 상단 앱바 + 필터 칩 → 바텀시트 필터 (날짜·오더·병동 48개 그리드·팀·약품)

```yaml
id: REF-307
type: 근거
ref_tags: [근거]
screen: S2
title: "Baymard #1125: 모바일 필터의 'Apply' 버튼"
source: "https://baymard.com/guidelines/1125-apply-buttons-in-mobile-filtering-interfaces"
designer_or_org: "Baymard Institute"
problem_it_solves: "여러 조건을 고르는 동안 매번 결과가 새로 고쳐져 느려지는 문제"
applies_to: [O4]
evidence: "검색 발췌: 자동 적용 필터는 여러 옵션을 고르려는 사용자를 느리게 할 수 있다(이슈 요약). 권고와 연구 본문은 유료라 읽지 못했다."
look_at: "인터랙션(적용 시점)"
sketch: "해당 없음(근거)"
why_needed: "(초안) N7(시트마다 [조회]를 다시 누름)의 반대 극단(즉시 적용)도 비용이 있다는 근거. 적용 방식 결정의 균형점"
cost: "(초안) 본문 미확인. 이커머스 맥락이라 업무 앱 전이는 가설"
how_to_apply: "M3 감사 때 결정"
confidence: 0.35
status: 미감사
```

```yaml
id: REF-308
type: 원칙
ref_tags: [원칙, 패턴]
screen: S2
title: "NSW Design System Filters: 단일 선택은 즉시, 여러 조건은 일괄 적용"
source: "https://designsystem.nsw.gov.au/components/filters"
designer_or_org: "NSW Government Digital"
problem_it_solves: "필터마다 즉시 적용할지 [적용] 버튼을 둘지 정하는 기준"
applies_to: [O4]
evidence: "검색 발췌: 단일 선택은 즉시 업데이트, 여러 관련 필터를 고를 것으로 예상되면 'Apply filters' 일괄 적용을 권한다."
look_at: "인터랙션(칩 즉시 적용 vs 시트 일괄 적용)"
sketch: |
  앱바 칩: [오늘 ▾][정규 ▾][2동 5개 ▾][팀 ▾]  ← 칩 1개 탭 = 즉시 변경
  시트(병동): 48개 그리드 다중 선택 → [12개 병동 조회]  ← 일괄 적용
why_needed: "(초안) 날짜·오더는 단일 선택, 병동·약품은 다중 선택이다. 한 규칙으로 두 종류를 처리할 수 있다"
cost: "(초안) 칩과 시트의 적용 방식이 달라 학습 비용이 조금 있다"
how_to_apply: "M3 감사 때 결정"
confidence: 0.5
status: 미감사
```

```yaml
id: REF-309
type: 원칙
ref_tags: [원칙]
screen: S2
title: "Maersk Design System: 응답이 1초 넘게 걸리면 일괄 필터"
source: "https://designsystem.maersk.com/guidelines/search-filter-and-sort/filter-patterns/"
designer_or_org: "Maersk"
problem_it_solves: "서버 조회가 느릴 때 즉시 적용 필터가 고통스러워지는 문제"
applies_to: [O4]
evidence: "검색 발췌: 모바일은 페이지 로드가 1초를 넘는 경우가 많아 인터랙티브 필터가 고통스러울 수 있으므로 일괄 필터가 맞다."
look_at: "인터랙션(적용 시점과 응답 시간)"
sketch: "해당 없음"
why_needed: "(초안) ePRIS 조회는 HIS 연동이라 응답 시간이 미확인이다. 응답 시간을 재면 REF-308의 선택을 수치로 정할 수 있다"
cost: "(초안) 응답 시간 측정이 필요하다(개발 협조)"
how_to_apply: "M3 감사 때 결정"
confidence: 0.5
status: 미감사
```

```yaml
id: REF-310
type: 패턴
ref_tags: [패턴]
screen: S2
title: "Linear 저장된 뷰(Personal/Team)"
source: "https://www.temperstack.com/learn/linear/create-custom-views-filters/"
designer_or_org: "Linear (3자 가이드 경유)"
problem_it_solves: "매일 같은 필터 조합을 다시 고르는 반복 비용"
applies_to: [O4]
evidence: "검색 발췌(3자 가이드): 필터 패널 위의 Save view로 저장하고, 개인용/팀용을 고르며, 저장한 뷰는 Views 드롭다운에 나온다. 수정은 Update view."
look_at: "인터랙션(현재 조합 저장 → 이름 → 재호출), 위계(뷰 목록 위치)"
sketch: |
  앱바: [내 근무: 입원 2동 정규 ▾]  [필터 칩들...]
        ▾ 내 프리셋 / 팀 프리셋 / + 현재 조건 저장
why_needed: "(초안) O4·N7('내 근무 프리셋')에 직접 대응한다. 팀 프리셋은 약국별 기본 조합을 관리자가 배포하는 길이 된다"
cost: "(초안) 프리셋 관리 화면과 저장 위치(기기 vs 사용자) 정의가 늘어난다. 공용 태블릿이라 사용자 전환(S7)과 묶여야 한다. 기능 추가라 ⚑ PM 확인 필요"
how_to_apply: "M3 감사 때 결정"
confidence: 0.4
status: 미감사
```

```yaml
id: REF-311
type: 패턴
ref_tags: [패턴, 원칙]
screen: S2
title: "SAP Fiori: 접힌 헤더 부제에 'Filtered By' 요약"
source: "https://www.sap.com/design-system/fiori-design-web/v1-148/page-types/page-layouts/page-header/usage"
designer_or_org: "SAP Fiori Design (Web)"
problem_it_solves: "필터 영역을 접은 뒤에도 지금 어떤 범위를 보고 있는지 알게 한다"
applies_to: [O4]
evidence: "검색 발췌: 목록형 페이지는 헤더에 필터가 있으면 접힌 상태 부제에 'Filtered By' 정보를 보여 줄 수 있다."
look_at: "위계(현재 조회 범위 한 줄 요약)"
sketch: |
  [처방 검토]  10/23 · 정규 · 2동(5) · 항암팀   미감사 12/40
why_needed: "(초안) F04(현재 조회 범위가 안 보임)에 대응한다. 칩이 가로로 넘치면 한 줄 요약이 대안이 된다"
cost: "(초안) 앱바 높이가 늘거나 텍스트가 잘린다"
how_to_apply: "M3 감사 때 결정"
confidence: 0.5
status: 미감사
```

```yaml
id: REF-312
type: 원칙
ref_tags: [원칙]
screen: S2, S6
title: "Material: 태블릿의 바텀시트는 인셋/전폭, 지속 패널은 사이드시트"
source: "https://material.io/components/sheets-bottom ; https://material.io/components/sheets-side"
designer_or_org: "Google Material Design"
problem_it_solves: "태블릿에서 큰 필터(48개 병동 그리드)를 어떤 표면에 담을지"
applies_to: [O3, O4]
evidence: "검색 발췌: 바텀시트는 모바일에서 전폭, 태블릿·데스크톱에서는 인셋 또는 전폭이다. 네 변을 모두 띄우면 스낵바 등과 혼동될 수 있다. 사이드시트는 주로 태블릿·데스크톱용 보조 표면이다(M3 사이드시트는 베타)."
look_at: "레이아웃(시트 폭·높이), 인터랙션(모달 vs 지속)"
sketch: |
  세로 태블릿: 바텀시트 전폭, 높이 ~90%
  ┌──────────────────────────┐
  │ 병동  [1동][2동] 탭       │
  │ □□□□□□ □□□□□□ (8×6 그리드)│
  │ ...                       │
  │ [초기화]   [12개 병동 조회]│
  └──────────────────────────┘
why_needed: "(초안) 48개 그리드는 세로 태블릿에서 반 높이 시트에 들어가지 않는다. 시트 높이 결정의 기준"
cost: "(초안) 전체 높이 시트는 사실상 전체 화면이라, 별도 화면과 차이가 작다"
how_to_apply: "M3 감사 때 결정"
confidence: 0.45
status: 미감사
```

```yaml
id: REF-313
type: 근거
ref_tags: [근거, 패턴]
screen: S2
title: "Airbnb 검색 개편: 자주 쓰는 필터는 위로, 나머지는 'More Filters'"
source: "https://techcrunch.com/?p=906056"
designer_or_org: "Airbnb (TechCrunch 보도)"
problem_it_solves: "필터가 많을 때 사용 빈도로 노출 수준을 나누기"
applies_to: [O4]
evidence: "검색 발췌: 날짜·공간 유형·가격이 가장 많이 쓰이는 필터이고, 덜 쓰이는 것은 'More Filters' 페이지 뒤에 둔다."
look_at: "위계(1차 칩 vs 2차 시트)"
sketch: "앱바 칩 = 고빈도 3개, [필터 +n] = 나머지"
why_needed: "(초안) 5개 시트를 모두 같은 수준으로 노출하는 현재 구조(N7)를 빈도로 나누는 근거. 다만 빈도는 약사에게 확인해야 한다"
cost: "(초안) 2차로 내린 필터는 발견성이 떨어진다"
how_to_apply: "M3 감사 때 결정"
confidence: 0.35
status: 미감사
```

### S3 하단 고정 조작 영역 (선택 n건, 저장취소/문의/검토/감사)

```yaml
id: REF-314
type: 원칙
ref_tags: [원칙, 패턴, 비주얼]
screen: S3
title: "Adobe Spectrum Action Bar: 하단, 선택 수 필수, 액션 5개 이하"
source: "https://spectrum.adobe.com/page/action-bar"
designer_or_org: "Adobe Spectrum"
problem_it_solves: "선택한 항목에 대한 일괄 작업을 어디에 어떤 규칙으로 둘지"
applies_to: [O1, O7, O8]
evidence: "검색 발췌: 항목을 선택하면 뷰포트 하단에 나타난다. 영향 범위를 알 수 있게 선택 수를 반드시 넣는다. 자주 쓰는 액션은 5개 이하, 나머지는 끝의 메뉴로. 모바일 여백 16px, 카운터와 액션 그룹 사이 24px 이상. 표 위에 떠 있을 때는 파란 배경의 강조 변형."
look_at: "레이아웃(카운터-액션 간격), 밀도(액션 수 상한), 위계(강조 변형)"
sketch: |
  ┌──────────────────────────────────────────┐
  │ ✕ 12건 선택      [저장취소][문의][검토][감사]│
  └──────────────────────────────────────────┘
  감사자: 사용자A (S7과 연결)
why_needed: "(초안) 액션이 정확히 4개라 상한 안에 든다. '선택 수 필수'는 일괄 감사 실수(F11)를 막는 최소 장치다. 선택 상태를 행 배경이 아닌 하단 바로 알리면 O1(선택 색과 저장 색 혼동)을 줄일 수 있다"
cost: "(초안) 하단 바가 상시 높이를 차지해 세로 공간이 줄어든다. 강조 변형(파란 배경)을 쓰면 감사 상태 색(파랑)과 겹친다"
how_to_apply: "M3 감사 때 결정"
confidence: 0.6
status: 미감사
```

```yaml
id: REF-315
type: 패턴
ref_tags: [패턴, 비주얼]
screen: S3
title: "IBM Carbon Data Table: 선택 시 나타나는 배치 액션 툴바"
source: "https://carbondesignsystem.com/components/data-table/usage/"
designer_or_org: "IBM Carbon"
problem_it_solves: "테이블 선택 모드 진입·이탈과 전체 선택"
applies_to: [O1, O8]
evidence: "검색 발췌: 행을 선택하면 배치 액션 툴바가 나타난다(v9 문서는 2개 이상일 때라고 해 버전마다 다르다). 취소하거나 선택을 해제하면 나간다. 헤더 체크박스로 전체 선택. 배경은 $background-brand."
look_at: "인터랙션(진입·이탈 조건), 비주얼(브랜드 배경으로 모드 전환 알림)"
sketch: |
  평소:   [검색][필터]                    (툴바)
  선택 시: [3개 선택됨 | 검토 | 감사 | 취소] (툴바가 바뀜, 표 상단)
why_needed: "(초안) 선택 모드를 툴바 전체 색 변화로 알리면 행 색에 '선택'을 쓰지 않아도 된다(O1 대안)"
cost: "(초안) 헤더 체크박스 전체 선택은 F11(전체 선택 위험)과 정면 충돌한다. 가져오면 제한 규칙이 꼭 필요하다"
how_to_apply: "M3 감사 때 결정"
confidence: 0.5
status: 미감사
```

```yaml
id: REF-316
type: 패턴
ref_tags: [패턴]
screen: S3
title: "eBay Playbook Bulk editing: 섹션 상단 고정 바"
source: "https://playbook.ebay.com/design-system/patterns/bulk-editing"
designer_or_org: "eBay Playbook"
problem_it_solves: "일괄 편집 바를 상단에 두는 대안"
applies_to: [O1]
evidence: "검색 발췌: 항목을 하나 이상 고르거나 편집 모드에 들어가면 섹션 상단에 일괄 액션 바가 나타나고, 스크롤해도 상단에 고정된다. 선택기는 'Select all'에서 선택 수로 바뀐다."
look_at: "레이아웃(상단 vs 하단 비교군)"
sketch: "[☐ 전체 | 12개 선택] [액션...]  ← 섹션 상단 고정"
why_needed: "(초안) 하단(REF-314)과 비교할 대조군이다. 태블릿을 카트 위에 두고 쓰는지, 손에 드는지에 따라 엄지 도달 위치가 다르다(O3 관찰 질문과 연결)"
cost: "(초안) 상단에 두면 앱바·필터 칩과 겹쳐 세로 공간을 두 번 쓴다"
how_to_apply: "M3 감사 때 결정"
confidence: 0.45
status: 미감사
```

```yaml
id: REF-317
type: 패턴
ref_tags: [패턴]
screen: S3
title: "Emplifi Soul Bulk-action bar: 액션 후에도 선택이 남으면 바 유지"
source: "https://soul.emplifi.io/latest/components/components/bulk-action-bar/usage-UJL5kHLb"
designer_or_org: "Emplifi Soul DS"
problem_it_solves: "일괄 액션 직후 선택 상태를 어떻게 처리할지"
applies_to: [O1, O8]
evidence: "검색 발췌: 전체 선택하면 'Select all'이 'Clear'로 바뀐다. 일괄 액션이 선택 항목을 해제하지 않으면 바는 활성으로 남는다."
look_at: "인터랙션(액션 후 선택 해제 규칙)"
sketch: "감사 저장 → 선택 자동 해제 → 바 숨김 + 토스트 '12건 감사 저장 [되돌리기]'"
why_needed: "(초안) 저장 후에도 선택이 남으면 '저장된 행을 다시 선택한 상태'가 생겨 O1이 정의하지 않은 조합이 나온다. 해제 규칙을 명시할 근거"
cost: "(초안) 없음에 가깝다(규칙 정의만)"
how_to_apply: "M3 감사 때 결정"
confidence: 0.4
status: 미감사
```

```yaml
id: REF-318
type: 원칙
ref_tags: [원칙]
screen: S3
title: "되돌리기 우선, 확인 대화상자는 되돌릴 수 없거나 범위가 큰 작업에만"
source: "https://developer.gnome.org/hig/patterns/feedback/dialogs.html ; https://uxpsychology.substack.com/p/how-to-design-better-destructive"
designer_or_org: "GNOME HIG, NN/g(2차 인용)"
problem_it_solves: "일괄 감사 저장 같은 고비용 액션의 안전장치 선택"
applies_to: [O8]
evidence: "검색 발췌: GNOME HIG는 파괴적 액션에 확인 대화상자나 되돌리기(토스트)를 둔다. NN/g(2차 인용)는 되돌릴 수 없는 심각한 결과 앞에 확인을 두고, 요청을 다시 말하고 결과를 설명하며 기본 선택을 두지 말라고 한다. 대화상자를 남발하면 숙련자가 읽지 않고 넘긴다."
look_at: "인터랙션(확인 vs 토스트 되돌리기), 문구('감사 저장 12건')"
sketch: |
  ≤N건: 즉시 저장 + 토스트 [되돌리기 5초]
  >N건 또는 D/C·보류 포함: 시트 '12건을 감사 저장합니다. D/C 1건 포함' [취소][12건 감사]
why_needed: "(초안) O8(저장 전 확인 없음)과 F11·F12의 해결 방식을 고를 원칙. 숙련자 대화상자 무시 위험까지 담고 있다"
cost: "(초안) 되돌리기는 서버 측 취소 이력(F17)과 맞물려 개발 비용이 있다. ⚑ PM 확인 필요"
how_to_apply: "M3 감사 때 결정"
confidence: 0.45
status: 미감사
```

### S4 긴급 큐 (좌 목록 / 우 상세 + 다음 환자 자동)

```yaml
id: REF-320
type: 패턴
ref_tags: [패턴, 근거]
screen: S4
title: "Zendesk Play 모드: 제출하면 다음 티켓 자동, 남이 보는 티켓은 건너뜀"
source: "https://www.zendesk.com/blog/play-button/ ; https://support.zendesk.com/hc/es/community/posts/4409515240090"
designer_or_org: "Zendesk"
problem_it_solves: "큐를 한 건씩 빠르게 처리하면서 동시 작업자 간 중복을 막기"
applies_to: [O6]
evidence: "검색 발췌: Play를 누르면 뷰의 첫 티켓이 열리고, 제출하면 다음 티켓이 자동으로 열린다. 다른 상담원이 보고 있는 티켓은 건너뛴다. Enterprise에서는 관리자가 강제할 수 있다. 한계: 미배정만 건너뛰지 않는다."
look_at: "인터랙션(제출 = 다음), 동시성(남이 보는 항목 건너뛰기)"
sketch: |
  ┌ 긴급 큐 (5) ──┬─ 환자 더미03 ────────────┐
  │ ▶ 더미03      │ 처방 상세                 │
  │   더미04 👁B  │                           │
  │   더미05      │        [문의] [감사 후 다음 ▶]│
  └───────────────┴───────────────────────────┘
  👁B = 다른 약사가 보는 중 → 자동 다음에서 건너뜀
why_needed: "(초안) 긴급은 여러 약사가 같은 큐를 본다. '종이는 한 사람만 쥔다'는 안전장치(05 문서)를 디지털로 복구하는 선례"
cost: "(초안) 실시간 '보는 중' 표시는 서버 상태 공유가 필요해 공수가 크다. ⚑ PM 확인 필요"
how_to_apply: "M3 감사 때 결정"
confidence: 0.55
status: 미감사
```

```yaml
id: REF-321
type: 패턴
ref_tags: [패턴]
screen: S4, S5
title: "Gmail 자동 진행(Auto-advance): 처리 후 다음/이전 대화로, 방향 선택"
source: "https://gmail.googleblog.com/2010/10/new-in-labs-auto-advance-to-next.html"
designer_or_org: "Google Gmail"
problem_it_solves: "목록으로 돌아가지 않고 연속 처리"
applies_to: [O6]
evidence: "검색 발췌: 보관·삭제 후 인접 대화로 자동 이동한다. 기본 방향은 더 오래된 대화(최신부터 읽는 사람에게 맞음). 설정에서 켜고 방향을 고른다. 모바일 지원은 출처마다 다르다."
look_at: "인터랙션(다음의 방향 정의), 설정(옵트인)"
sketch: "감사 저장 → 다음 = 목록 정렬 순서상 다음 환자(정렬 기준이 곧 '다음'의 정의)"
why_needed: "(초안) '다음 환자'가 무엇인지(병동순? 접수순? 미감사만?)를 정해야 한다는 점을 드러낸다"
cost: "(초안) 방향·대상 설정을 노출하면 설정 항목이 는다"
how_to_apply: "M3 감사 때 결정"
confidence: 0.5
status: 미감사
```

```yaml
id: REF-322
type: 근거
ref_tags: [근거]
screen: S4, S5
title: "Apple Mail iOS 18.4: 자동 다음 메시지를 끌 수 있는 옵션 추가"
source: "https://9to5mac.com/2025/02/26/apple-mail-iphone-return-to-inbox-after-delete-trash/"
designer_or_org: "Apple (9to5Mac 보도)"
problem_it_solves: "자동 진행이 맞지 않는 사용자의 불편"
applies_to: [O6]
evidence: "검색 발췌: iOS 18.4부터 '삭제 또는 이동 후 동작' 설정이 생겼고, 기본값은 '다음 메시지 보기', 대안은 '메시지 선택 안 함'(목록으로 복귀)이다. iPad 지원은 확인 못 함."
look_at: "인터랙션(자동 진행의 끄기 옵션)"
sketch: "해당 없음"
why_needed: "(초안) 오랫동안 자동 진행만 제공했던 제품이 결국 끄는 옵션을 넣었다. 자동 다음은 모든 사용자에게 맞지 않는다는 간접 근거"
cost: "(초안) 설정 1개 추가"
how_to_apply: "M3 감사 때 결정"
confidence: 0.45
status: 미감사
```

```yaml
id: REF-323
type: 패턴
ref_tags: [패턴, 비주얼]
screen: S4, S3
title: "Toast KDS: 완료(fulfill), 최근 완료 보기, Recall(빨간 RECALLED), All-day 집계"
source: "https://doc.toasttab.com/doc/platformguide/platformKDSOverview.html ; https://support.toasttab.com/article/Item-and-Order-Fulfillment-on-KDS"
designer_or_org: "Toast"
problem_it_solves: "바쁜 현장에서 주문 큐를 처리하고 실수로 넘긴 건을 되살리기"
applies_to: [O2, O6, O8]
evidence: "검색 발췌: 티켓을 두 번 탭하면 완료된다. 오른쪽 위 버튼 4개(All-day, 최근 완료, Recall, 설정). Recall은 가장 최근 완료 티켓을 다시 열고 상단에 빨간 RECALLED를 붙인다. All-day는 품목별 남은 수량을 집계한다. 그리드 열·행 수, 글자 크기, 라이트/다크를 설정할 수 있다."
look_at: "인터랙션(완료/Recall 대칭), 위계(되살린 항목 라벨), 밀도(그리드·글자 크기 설정)"
sketch: |
  [긴급 큐]          [남은 5][최근 완료][↶ 되살리기]
  ┌────┐┌────┐┌────┐
  │더미1││더미2││더미3│  ← 되살린 항목: 상단 '되살림' 라벨
  └────┘└────┘└────┘
why_needed: "(초안) 자동 다음의 위험은 '방금 넘긴 건'을 잃는 것이다. 최근 완료 + Recall은 O8의 한 단계 되돌리기와 같은 구조를 큐 화면에 맞게 보여 준다. All-day 집계는 O2(진행 요약)의 큐 버전"
cost: "(초안) 최근 완료 목록과 되살림 상태가 추가된다(상태 전이표 갱신 필요, m6-spec)"
how_to_apply: "M3 감사 때 결정"
confidence: 0.55
status: 미감사
```

```yaml
id: REF-324
type: 패턴
ref_tags: [패턴]
screen: S4
title: "Linear Triage: 수락/중복/거절 단축키, 거절 시 사유 코멘트"
source: "https://linear.app/docs/triage ; https://linear.app/changelog/2021-06-29-linear-release-and-issue-triage"
designer_or_org: "Linear"
problem_it_solves: "들어온 항목을 몇 개의 고정된 판정으로 빠르게 분류"
applies_to: [O6]
evidence: "검색 발췌: 1=수락, 2=중복, 3=거절, H=스누즈. 거절하면 이유를 코멘트로 남기라는 안내가 뜬다. 추가 정보를 기다리는 동안 인박스에 남겨 둘 수 있다. 모바일 트리아지는 확인 못 함."
look_at: "인터랙션(고정 판정 + 부정 판정에만 사유)"
sketch: "[감사] [검토] [문의…(사유 시트)] [보류…(사유 시트)]"
why_needed: "(초안) 문의·보류(드문 상태)에만 사유를 받고 감사(잦은 상태)는 한 번에 끝내는 비대칭 설계의 선례. F13(보류 사유)과 연결"
cost: "(초안) 사유 입력 시트가 늘어난다(S6 메모 시트와 통합 가능성)"
how_to_apply: "M3 감사 때 결정"
confidence: 0.5
status: 미감사
```

```yaml
id: REF-325
type: 원칙
ref_tags: [원칙]
screen: S4, S5
title: "Apple HIG Sidebars/Split view: 2단 이상은 목록-상세, 하단에 중요 액션 두지 않기"
source: "https://developer.apple.com/design/human-interface-guidelines/sidebars"
designer_or_org: "Apple HIG"
problem_it_solves: "iPad에서 목록-상세 구조와 액션 위치"
applies_to: [O6]
evidence: "검색 발췌: 계층이 2단계를 넘으면 사이드바와 상세 사이에 콘텐츠 목록을 둔 split view를 고려한다. 창을 옮기면 아래쪽이 가려질 수 있어 중요한 정보·액션을 아래쪽에 두지 말라고 한다. compact 환경에서는 사이드바가 공간을 많이 차지한다."
look_at: "레이아웃(세로 compact에서 목록 폭)"
sketch: "세로 태블릿 = compact에 가까움 → 좌 목록은 접이식 또는 상단 가로 스트립"
why_needed: "(초안) 긴급만 가로 분할이고 나머지는 세로라는 N6 혼재를 판단할 원칙. '하단에 중요 액션 금지'는 S3와 충돌하므로 감사 때 반드시 맞대어 볼 것"
cost: "(초안) 원칙이 iPad 멀티윈도우 전제라 전용 태블릿(Android 가능성)에는 약하게 적용된다"
how_to_apply: "M3 감사 때 결정"
confidence: 0.45
status: 미감사
```

### S5 환자 처방전 뷰 (신규 제안: 환자 1명 전체 처방, 판단 수치 상단 고정, 이전/다음)

```yaml
id: REF-326
type: 패턴
ref_tags: [패턴, 원칙]
screen: S5
title: "SAP Fiori Elements: 객체 페이지 이전/다음(Paging buttons)과 'Save and Next'"
source: "https://experience.sap.com/fiori-design-web/v1-104/object-page-header-sap-fiori-elements"
designer_or_org: "SAP Fiori Design"
problem_it_solves: "목록에서 들어간 상세 화면에서 목록으로 돌아가지 않고 이웃 항목으로 이동, 저장과 이동을 한 번에"
applies_to: [O6]
evidence: "검색 발췌: 목록 테이블에 2개 이상 항목이 있을 때 상세 헤더에 이전/다음 버튼이 기본으로 나온다. 푸터의 'Save and Next'는 편집 중 목록을 따라 이동하고, 마지막 항목을 저장하면 목록 리포트로 돌아간다."
look_at: "레이아웃(헤더 오른쪽 ∧∨), 인터랙션(저장+다음, 마지막 항목 처리)"
sketch: |
  ┌ ← 목록   환자 더미01 (3/18)        [∧][∨] ┐
  │ CrCl 45 · BSA 1.6 · 체중 58 (고정)          │
  ├─────────────────────────────────────────────┤
  │ 처방 1 ... 처방 n (세로 스크롤)              │
  ├─────────────────────────────────────────────┤
  │ 미감사 4건          [문의][검토][감사 후 다음]│
  └─────────────────────────────────────────────┘
  마지막 환자 저장 → 목록으로 복귀 + 요약
why_needed: "(초안) S5의 이전/다음과 S4의 자동 다음을 한 규칙(저장+다음, 끝나면 목록)으로 묶을 수 있다. 종이를 '한 장씩 넘기는' 안전장치(05 문서)의 디지털 대응"
cost: "(초안) 신규 화면 추가다. ⚑ PM 확인 필요(계약 범위). '다음'의 정렬 기준 정의 필요(REF-321)"
how_to_apply: "M3 감사 때 결정"
confidence: 0.55
status: 미감사
```

```yaml
id: REF-327
type: 패턴
ref_tags: [패턴, 비주얼]
screen: S5, S1
title: "Epic Haiku/Canto: 한 줄 환자 헤더, 탭하면 요약 리포트"
source: "https://it.houstonmethodist.org/wp-content/uploads/2021/01/Feb-21-2021-ED-RN-Companion.pdf ; https://it.houstonmethodist.org/wp-content/uploads/2021/01/Feb-21-2021-Provider-Solutions-Companion.pdf"
designer_or_org: "Epic (병원 업그레이드 안내 경유)"
problem_it_solves: "작은 화면에서 환자 식별 정보는 한 줄로, 상세는 필요할 때만"
applies_to: [O5]
evidence: "검색 발췌: 환자 헤더가 이름·나이·성별·병실/상태·MRN을 담은 한 줄로 바뀌었다. 헤더를 탭하면 약물·알레르기·인구통계·문제 목록 등의 요약 리포트가 열린다."
look_at: "위계(식별 한 줄 vs 판단 수치), 인터랙션(헤더 탭 = 요약)"
sketch: "[더미01 · 67/M · 52병동 · 0000000] ▸ 탭 → 알레르기·검사·투약 요약 시트"
why_needed: "(초안) 같은 의료 도메인의 실제 제품 선례. 단, Epic은 판단 수치를 한 줄에 넣지 않는다 → ePRIS는 판단 수치를 식별 정보와 다른 줄로 분리해야 하는지 볼 비교 기준"
cost: "(초안) '탭하면 열린다'는 O5(열어야 보이는 정보는 안 본다)와 충돌할 수 있다. 판단 수치에는 쓰면 안 된다는 경계가 필요"
how_to_apply: "M3 감사 때 결정"
confidence: 0.4
status: 미감사
```

```yaml
id: REF-328
type: 패턴
ref_tags: [패턴, 비주얼]
screen: S5, S1
title: "Apple Health Summary: 사용자가 고르는 고정(Pinned) 항목 + 하이라이트"
source: "https://support.apple.com/en-ca/HT203037 ; https://www.macstories.net/stories/health-in-ios-13-a-foundation-for-apples-grand-wellness-ambitions/"
designer_or_org: "Apple Health"
problem_it_solves: "많은 지표 중 지금 볼 몇 개만 위에 고정"
applies_to: [O2, O5]
evidence: "검색 발췌: Summary의 Pinned는 사용자가 고른 카테고리이며 Pinned 옆 Edit로 추가·제거한다. 아래 Highlights는 시간에 따른 비교 그래프를 몇 개만 보여 주고 'Show All Highlights'로 더 본다. iPad는 사이드바에서 Summary로 간다."
look_at: "위계(고정 수치 카드 vs 추세), 비주얼(수치 카드 타이포)"
sketch: |
  [CrCl 45 ▼어제 52] [BSA 1.6] [체중 58]   ← 고정 카드, 변화 화살표
why_needed: "(초안) 판단 수치에 '이전 값 대비 변화'를 붙이는 아이디어의 출처. 약국별로 고정 수치가 다르다는 점(항암 BSA, 입원 CrCl)을 사용자 선택이 아닌 약국 기본값으로 바꿔 쓸 수 있다"
cost: "(초안) 사용자 편집은 공용 태블릿에서 혼란을 준다(가져오면 약국 기본값만). 이전 값 연동은 HIS 데이터 확인 필요"
how_to_apply: "M3 감사 때 결정"
confidence: 0.4
status: 미감사
```

```yaml
id: REF-329
type: 비주얼
ref_tags: [비주얼, 근거]
screen: S5
title: "S7 Airlines 승무원 iPad 재설계, BA·Allegiant 전자 승객 명단"
source: "https://artew.notion.site/iPad-app-redesign-for-Flight-Attendants-Cabin-Crew-Pad-05a9593b17b3410e86e146e056c011c4 ; https://runwaygirlnetwork.com/2014/01/how-a-crm-app-for-crew-tablets-changes-paxex/"
designer_or_org: "Kotelov(포트폴리오), British Airways, Allegiant"
problem_it_solves: "종이 명단(최대 337명, 10kg 이상 서류)을 태블릿으로 옮길 때 무엇을 메인에 둘지"
applies_to: [O3, O5]
evidence: "검색 발췌: S7 사례는 승무원·PO 인터뷰 후 위험 화물 정보를 메인 화면에 보여야 한다고 정리했다. BA는 문 닫힌 뒤 좌석·동반자·등급·식사 요청을 담은 실시간 명단을 받는다."
look_at: "위계(안전 정보는 메인, 서비스 정보는 하위), 종이→태블릿 전환 방식"
sketch: "해당 없음(원본 화면 미확인)"
why_needed: "(초안) '종이가 공짜로 주던 것'을 태블릿으로 옮긴 다른 업무 현장의 비교 사례. 안전 정보 = 메인 원칙이 CDSS 경고(O5)와 같은 구조"
cost: "(초안) 도메인이 달라 화면 자체를 참고하기는 어렵다. 포트폴리오 1건"
how_to_apply: "M3 감사 때 결정"
confidence: 0.3
status: 미감사
```

### S6 메모 바텀시트 · 바코드 스캔 결과 시트

```yaml
id: REF-330
type: 근거
ref_tags: [근거, 패턴]
screen: S6
title: "Epic Rover 바코드 투약(BCMA): 모바일 스캔 준수율이 워크스테이션보다 높음"
source: "https://www.epicresearch.org/articles/improved-barcode-scanning-for-medication-administration-with-mobile-devices-compared-to-standalone-scanners"
designer_or_org: "Epic Research"
problem_it_solves: "환자·약품·사용자를 스캔으로 확인하는 흐름이 실제로 지켜지는가"
applies_to: [O8]
evidence: "검색 발췌: 2021-01~2024-05 컴퓨터 기반 투약 13억 건과 모바일 투약 2.32억 건을 비교했고 모바일의 BCMA 준수율이 일관되게 높았다. 흐름은 손목밴드 스캔 → 약품 스캔이며, 오류(만료·용량·환자 불일치) 시 경고를 띄운다(3자 가이드)."
look_at: "인터랙션(스캔 순서와 불일치 경고)"
sketch: |
  스캔 결과 시트:
  ✓ 라벨 일치: 더미01 · 약품A 500mg      [감사로 표시]
  ✕ 불일치: 스캔=더미02 / 화면=더미01     [다시 스캔]
why_needed: "(초안) 같은 병원 도메인에서 '기기에 붙은 스캔'이 준수율을 높였다는 정량 근거. 라벨 바코드 연동(project.md)을 정당화"
cost: "(초안) Epic 자체 연구라 이해 상충이 있다. 상관관계이며 원문 미열람"
how_to_apply: "M3 감사 때 결정"
confidence: 0.45
status: 미감사
```

```yaml
id: REF-331
type: 패턴
ref_tags: [패턴, 비주얼]
screen: S6
title: "Scandit MatrixScan Count: 스캔 결과 아이콘(성공/판독 불가/있으면 안 됨) + 카운터·진행 바"
source: "https://docs.scandit.com/sdks/ios/matrixscan-count/intro/"
designer_or_org: "Scandit"
problem_it_solves: "여러 개를 연속 스캔할 때 각 결과와 전체 진행을 동시에 알림"
applies_to: [O2]
evidence: "검색 발췌: 스캔한 바코드 위에 성공·판독 불가·있으면 안 되는 항목을 AR 아이콘으로 표시하고, 카운터 배지나 진행 바로 예상 수량 대비 진행을 보여 준다. 구 SDK는 거부된 코드를 다른 색으로 그리고 소리·진동을 내지 않는다."
look_at: "비주얼(3가지 결과 아이콘), 위계(개별 결과 + 전체 카운터)"
sketch: "[스캔 7 / 12]  ✓✓✓✓✓ ? ✕   ← 판독 불가와 '이 목록에 없음'을 구분"
why_needed: "(초안) 스캔 결과가 '일치/불일치' 두 가지가 아니라 '판독 불가', '다른 환자 것'처럼 세 가지 이상임을 보여 준다. 결과 시트 상태 설계의 출발점"
cost: "(초안) AR 오버레이는 ePRIS에 과하다(외장 스캐너 사용). 아이콘 체계만 가져올 후보"
how_to_apply: "M3 감사 때 결정"
confidence: 0.45
status: 미감사
```

```yaml
id: REF-332
type: 근거
ref_tags: [근거, 원칙]
screen: S6
title: "창고 스캐너 앱의 피드백: 인식한 대상 표시, 성공=햅틱·오류=소리, 중복 스캔 방지"
source: "https://studenttheses.uu.nl/handle/20.500.12932/46062 ; https://freelancehunt.com/en/showcase/work/mvp-warehouse-system-for-order-pickers/2043595.html ; https://www.dynamicsmobile.com/insights/new-insight-12"
designer_or_org: "위트레흐트대 논문, 프리랜스 사례, 벤더 가이드"
problem_it_solves: "스캔했는데 무엇이 인식됐는지 모르는 문제, 소란한 환경의 피드백"
applies_to: [O2]
evidence: "검색 발췌: 스캔 후 앱이 인식한 품목·위치를 분명히 보여야 한다. 한 사례는 성공에 햅틱, 오류에 소리를 쓰고 1.5초 디바운스로 중복 스캔을 막았다. 논문은 WMS에서 시각 피드백이 일반적이고 청각 피드백은 비프음에 그친다고 했다. 고대비 색 권장."
look_at: "인터랙션(피드백 채널 분리), 비주얼(인식 대상의 크기)"
sketch: "스캔 → 시트 최상단에 인식한 환자명(더미)+약품명을 가장 크게, 결과 색 띠"
why_needed: "(초안) 약제부는 소음과 조명이 제각각이다. 색 하나에만 의존하지 않는 피드백(O1의 색 의존 문제와 같은 원칙)"
cost: "(초안) 근거가 약하다(논문 1, 사례 1). 병원 내 소리 사용 가능 여부 확인 필요"
how_to_apply: "M3 감사 때 결정"
confidence: 0.35
status: 미감사
```

```yaml
id: REF-333
type: 패턴
ref_tags: [패턴]
screen: S6
title: "Shopify POS 'Unrecognized barcode' 오류와 구체적 해결 안내"
source: "https://help.shopify.com/en/manual/sell-in-person/hardware/barcode-scanners"
designer_or_org: "Shopify POS"
problem_it_solves: "스캔 실패를 사용자가 스스로 해결할 수 있게 함"
applies_to: [O8]
evidence: "검색 발췌: 'Unrecognized barcode' 오류가 나면 상품이 POS에 있는지, 바코드 번호가 관리자 값과 같은지, 앞뒤 0이 붙었는지 확인하라고 안내한다. 오류가 없으면 스캐너를 다시 페어링한다."
look_at: "문구(오류 원인별 다음 행동)"
sketch: "✕ 인식할 수 없는 라벨 → [다시 스캔] [번호 직접 입력] · '조회 범위 밖 처방일 수 있습니다(필터: 2동)'"
why_needed: "(초안) ePRIS에서는 '현재 필터 범위 밖 처방'이 흔한 실패 원인일 수 있다(가설). 원인별 안내 문구 설계의 선례"
cost: "(초안) 실패 원인 분류를 개발과 정의해야 한다"
how_to_apply: "M3 감사 때 결정"
confidence: 0.4
status: 미감사
```

> 메모 바텀시트 자체의 비주얼 레퍼런스는 이번 수집에서 찾지 못했다(빈칸). Apple HIG Sheets 페이지는 열렸지만 본문이 비어 있어 카드로 만들지 않았다. 시트 높이 기준은 REF-312를 참고. 사유 입력과 묶는 방향은 REF-324.

### S7 로그인 · 사용자 전환 (공용 태블릿)

```yaml
id: REF-334
type: 패턴
ref_tags: [패턴, 원칙]
screen: S7
title: "Toast POS: 기기 로그인은 한 번, 사람마다 6~8자리 접근 코드, 권한은 코드를 따른다"
source: "https://support.toasttab.com/en/article/Log-in-to-a-Toast-Product-or-Device ; https://doc.toasttab.com/doc/platformguide/adminToastPosAccessTypes.html"
designer_or_org: "Toast"
problem_it_solves: "공용 기기에서 여러 직원이 빠르게 바꿔 쓰면서 책임·권한을 분리"
applies_to: [O8]
evidence: "검색 발췌: POS 앱 로그인은 기기 단위로 한 사람이 한 번 한다. 이후 직원마다 고유한 6~8자리 POS 접근 코드로 출근·주문·결제한다. 매니저가 기기를 로그인했어도 서버 직원이 자기 코드를 넣으면 매니저 기능은 안 보인다. 같은 매장에서 코드는 중복될 수 없다. 일부 민감 작업에도 코드를 요구한다."
look_at: "인터랙션(기기 인증과 사람 인증 분리), 원칙(권한은 사람 단위)"
sketch: |
  [기기: 약제부 태블릿 3 · HIS 연결됨]
  ┌──────────────┐
  │ 사원증 스캔 또는 │
  │ 사번 PIN ••••  │
  └──────────────┘
  감사 저장 직전: '감사자: 사용자A' (하단 바, S3)
why_needed: "(초안) N4·F16(공용 태블릿 감사자 오기록)에 대한 실제 제품 해법. HIS 로그인(기기)과 감사자 식별(사람)을 분리하는 모델"
cost: "(초안) HIS 로그인 정책과 PIN 정책을 병원 보안팀과 맞춰야 한다. ⚑ PM 확인 필요(연동 범위)"
how_to_apply: "M3 감사 때 결정"
confidence: 0.6
status: 미감사
```

```yaml
id: REF-335
type: 근거
ref_tags: [근거, 패턴]
screen: S7
title: "Square POS: 개인 패스코드·배지로 전환, 공용 패스코드의 위험"
source: "https://squareup.com/help/us/en/article/8395-clock-in-and-out-for-team-members ; https://community.squareup.com/t5/Troubleshooting/Shared-team-passcode-for-restaurant-pos-on-square-register/td-p/735227"
designer_or_org: "Square"
problem_it_solves: "공용 단말에서 개인 식별을 생략하고 싶은 유혹과 그 비용"
applies_to: [O8]
evidence: "검색 발췌: 직원은 개인 4자리 패스코드로 출퇴근하고, 근무 중 직무 전환은 패스코드나 배지로 한다. 자기 이메일로 앱에 로그인한 직원에게는 패스코드를 묻지 않는다. 커뮤니티 답변: 공용 패스코드는 퇴사자도 계속 쓸 수 있다."
look_at: "인터랙션(배지를 PIN의 대안으로)"
sketch: "해당 없음"
why_needed: "(초안) '사번 저장'(현 설계)이 공용 패스코드와 같은 구조라는 점을 보여 주는 근거. 배지 대안의 선례"
cost: "(초안) 커뮤니티 답변은 비공식"
how_to_apply: "M3 감사 때 결정"
confidence: 0.5
status: 미감사
```

```yaml
id: REF-336
type: 패턴
ref_tags: [패턴, 근거]
screen: S7
title: "Imprivata 배지 탭: 탭으로 들어오고 탭으로 나가며 다음 사용자에게 깨끗한 상태"
source: "https://www.imprivata.com/sites/imprivata/files/2026-05/7042-2026_EAM-DS-fast-user-switching.pdf ; https://www.imprivata.com/partners/epic"
designer_or_org: "Imprivata"
problem_it_solves: "병원 공용 단말에서 공용 계정 없이 빠른 사용자 전환"
applies_to: [O8]
evidence: "검색 발췌: 배지 탭으로 세션을 시작하고 같은 탭이나 지문으로 끝낸다. 공용 로그인 없이 각 임상의를 식별하고 다음 사용자에게 깨끗한 상태를 준다. 빠른 로그오프가 잘못된 ID로 기록하는 위험을 줄인다고 주장한다. Epic Rover에도 배지 탭 접근을 제공한다."
look_at: "인터랙션(탭 인/탭 아웃 대칭), 세션 초기화(F06 필터 초기화와 연결)"
sketch: "사원증 스캔 → '사용자B로 전환됨 · 필터 초기화됨' 토스트"
why_needed: "(초안) 병원이 이미 RFID 사원증 인프라를 쓰면 가장 현실적인 경로(가설). N4의 '사원증 바코드 존재 여부 확인 필요'와 직결"
cost: "(초안) 벤더 마케팅 자료. 리더기 하드웨어가 필요할 수 있다(바코드 스캐너로 대체 가능한지 확인 필요)"
how_to_apply: "M3 감사 때 결정"
confidence: 0.45
status: 미감사
```

```yaml
id: REF-337
type: 근거
ref_tags: [근거]
screen: S7
title: "Houston Methodist Rover FAQ: 이전 사용자로 로그인된 채 남아 있을 수 있으니 이름을 확인하라"
source: "https://uatit.houstonmethodist.org/wp-content/uploads/2020/10/Rover-Smartphone-FAQs.final_.5-4-2020_101620.pdf"
designer_or_org: "Houston Methodist (병원 IT 안내)"
problem_it_solves: "공용 기기에서 다른 사람 이름으로 기록하는 실수"
applies_to: [O8]
evidence: "검색 발췌: Rover가 이전 사용자 자격으로 로그인된 채 남아 있을 수 있으므로 기록 전에 올바른 이름이 보이는지 확인하라고 안내한다. 다른 안내는 근무 종료 때 로그아웃해 로그인 화면으로 돌려 두라고 한다."
look_at: "위계(현재 사용자 이름을 기록 직전에 노출)"
sketch: "하단 바 왼쪽: '감사자 사용자A ▾' (탭 → 전환)"
why_needed: "(초안) F16이 가설이 아니라 실제 병원에서 이미 일어나 교육으로 막고 있는 문제라는 근거. 교육 대신 화면으로 막을 이유"
cost: "(초안) 하단 바에 이름이 들어가 공간을 쓴다"
how_to_apply: "M3 감사 때 결정"
confidence: 0.5
status: 미감사
```

```yaml
id: REF-338
type: 원칙
ref_tags: [원칙]
screen: S7
title: "Shared iPad: 사용자 세션은 동시가 아니라 순차, 캐시 사용자 수 상한"
source: "https://kb.filewave.com/books/apple-classroom/page/classroom-shared-ipad-y9h/export/markdown ; https://www.hexnode.com/blogs/wp-json/wp/v2/posts/24201"
designer_or_org: "Apple Shared iPad (MDM 벤더 문서 경유)"
problem_it_solves: "OS 수준 다중 사용자를 쓸지 앱 수준 전환을 쓸지"
applies_to: [O8]
evidence: "검색 발췌: Shared iPad 사용자는 macOS 빠른 사용자 전환처럼 동시가 아니라 공간을 나눠 쓴다. 최대 사용자 수를 넘으면 가장 오래된 계정을 지워 다음 로그인이 느려진다. Managed Apple ID가 필요하다."
look_at: "해당 없음(플랫폼 제약)"
sketch: "해당 없음"
why_needed: "(초안) OS 수준 전환은 느리고 Apple 계정 체계가 필요해 교대가 잦은 약제부에는 맞지 않을 수 있다 → 앱 수준 전환(REF-334) 쪽 근거. 기기가 iPad인지부터 확인 필요"
cost: "(초안) 정보성. 기기 미확정"
how_to_apply: "M3 감사 때 결정"
confidence: 0.35
status: 미감사
```

> REF-319는 쓰지 않았다(토스 TDS 하단 버튼 가이드를 찾지 못해 카드를 만들지 않음). 번호는 비워 둔다.

---

### 1. 화면별 가장 강한 레퍼런스

| 화면 | 가장 강한 레퍼런스 | 이유 | 신뢰도 |
|---|---|---|---|
| S1 처방 목록 | **REF-301 + REF-302** SAP Fiori Data Table | 세로 태블릿 + 다열 + 스티키 헤더·첫 열을 한 컴포넌트로 다루는 유일한 1차 문서다. "고정 열 ≤ 30%"라는 수치 기준이 있어 M4·M6에서 바로 쓸 수 있다 | 0.5 |
| S2 필터 | **REF-308** NSW 필터 규칙(+REF-309 응답 시간 조건) | 칩은 즉시, 다중 선택 시트는 일괄이라는 한 규칙으로 날짜·오더(단일)와 병동·약품(다중)을 모두 정리한다. O4의 반복 비용 자체는 REF-310(저장된 뷰)이 더 직접적이지만 출처가 3자 가이드라 약하다 | 0.5 |
| S3 하단 조작 | **REF-314** Adobe Spectrum Action Bar | 하단 위치·선택 수 필수·액션 5개 이하·간격 수치까지 원칙과 패턴이 함께 있다. ePRIS 액션 4개가 상한 안에 들고, 선택 수 표시가 F11 안전장치가 된다 | 0.6 |
| S4 긴급 큐 | **REF-320** Zendesk Play 모드 | "제출 = 다음"에 더해 "다른 사람이 보는 항목은 건너뜀"이라는 동시성 규칙이 있다. 여러 약사가 같은 긴급 큐를 볼 때 생기는 중복을 막는다. 되돌리기는 REF-323(Toast Recall)으로 보완 | 0.55 |
| S5 처방전 뷰 | **REF-326** SAP Fiori 이전/다음 + Save and Next | 이전/다음, 저장+다음, 마지막 항목 후 목록 복귀까지 한 흐름으로 정의되어 있다. S4 자동 다음과 같은 규칙으로 묶을 수 있다 | 0.55 |
| S6 메모·스캔 | **REF-330** Epic Rover BCMA | 같은 병원 도메인에서 스캔 확인 흐름의 준수율을 정량으로 보인 유일한 자료다. 결과 시트의 비주얼은 REF-331(결과 3종 + 카운터)로 보완 | 0.45 |
| S7 로그인·전환 | **REF-334** Toast POS 접근 코드 모델 | 기기 인증과 사람 인증을 분리하고 권한이 사람을 따른다. 공식 도움말이라 근거가 비교적 확실하다. F16이 실제 문제라는 근거는 REF-337 | 0.6 |

### 2. 매트릭스: 관찰 O# × 레퍼런스 4종

| O# | 비주얼 | 패턴 | 근거 | 원칙 |
|---|---|---|---|---|
| O1 선택·저장 색 혼동 | REF-303, 315 | REF-314, 315, 316, 317 | **빈칸** | REF-314 |
| O2 진행 요약 없음 | REF-323, 328, 331 | REF-323, 331 | REF-332(약) | **빈칸** |
| O3 세로 20열 | REF-301, 303, 304 | REF-301, 303, 304 | REF-305(약), 306 | REF-302, 312 |
| O4 마법사 반복 | **빈칸** | REF-310, 311, 313 | REF-307(본문 미확인), 313(약) | REF-308, 309 |
| O5 툴팁에 숨은 중요 정보 | REF-327 | REF-304, 327, 328 | REF-306 | REF-329(약) |
| O6 목록-상세 + 자동 다음 | REF-323 | REF-320, 321, 323, 324, 326 | REF-320, 322 | REF-325, 326 |
| O7 버튼 색 = 상태 색 | **빈칸** | **빈칸** | **빈칸** | **빈칸** |
| O8 저장 취소·확인 없음 | REF-323 | REF-317, 323, 333, 334 | REF-330, 335, 337 | REF-318, 334 |
| O9 약국별 열 구성 | **빈칸** | **빈칸** | **빈칸** | **빈칸** |

- S7 카드(REF-334~338)는 O8에 넣었지만 실제로는 N4·F16(감사자 오기록)이 주 대상이다. M1이 O#를 통합하면 다시 매핑해야 한다.
- 빈칸: O7과 O9는 이번 수집 범위(화면별 비주얼·패턴)에서 나오지 않았다. O1·O2의 근거, O4의 비주얼도 비어 있다. 상태 색 근거는 m3b(REF-1xx)에 있을 수 있으니 통합 때 확인한다.

### 3. 화면 × 레퍼런스 4종 (수집 분포)

| 화면 | 비주얼 | 패턴 | 근거 | 원칙 | 카드 수 |
|---|---|---|---|---|---|
| S1 | 303, 304 | 301, 302, 303, 304 | 305, 306 | 301, 302, 306 | 6 |
| S2 | **빈칸** | 308, 310, 311, 313 | 307, 313 | 308, 309, 311, 312 | 7 |
| S3 | 314, 315 | 314, 315, 316, 317 | **빈칸** | 314, 318 | 5 |
| S4 | 323 | 320, 321, 323, 324 | 320, 322 | 325 | 6 |
| S5 | 327, 328, 329 | 326, 327, 328 | 329 | 326 | 4 (+304, 306, 321, 322, 325 공유) |
| S6 | 331 | 330, 331, 333 | 330, 332 | 332 | 4 (+312 공유) |
| S7 | **빈칸** | 334, 335, 336 | 335, 336, 337 | 334, 338 | 5 |

**비주얼이 가장 약하다.** 실제 화면을 열지 못했기 때문이다. 요청 목적(UI 고도화)을 생각하면 §5 경로로 사람이 화면을 직접 확인하는 일이 가장 먼저다.

### 4. 감사 때 먼저 볼 충돌

1. **REF-314(하단 액션 바) vs REF-325(HIG: 하단에 중요 액션 두지 않기).** HIG 쪽은 iPad 멀티윈도우 전제라 전용 태블릿에서는 약하다고 보지만, 확인이 필요하다.
2. **REF-315(헤더 전체 선택) vs F11(전체 선택 위험).** 패턴을 그대로 가져오면 안전 원칙과 정면 충돌한다.
3. **REF-327(탭하면 요약) vs O5(열어야 보이는 정보는 안 본다).** 식별 정보에는 맞고 판단 수치에는 맞지 않는다.
4. **REF-303(상태 열 오른쪽 고정)은 종이 열 순서를 바꾼다.** 원칙 3("바꿀 것만 바꾸기")과 충돌하므로 ⚑ PM 확인 필요.
5. **REF-314 강조 변형(파란 배경) vs 감사 상태 색(파랑).** m6-spec v2 토큰과 대조할 것.

### 5. 학습용 메모: 어디서 좋은 레퍼런스가 나왔나 (다음 수집에 재사용)

| 출처 | 이번 수확 | 다음에 쓰는 법 |
|---|---|---|
| **디자인 시스템 문서** (SAP Fiori, Adobe Spectrum, Carbon, Polaris, eBay Playbook) | 가장 좋았다. 업무용·고밀도 패턴에 수치 기준(30%, 액션 5개, 16/24px)이 붙어 있다 | "<패턴명> usage" + 시스템명으로 검색. 업무용 테이블은 **SAP Fiori**가 가장 깊다(iOS·Android·Web 3종) |
| **POS·현장 제품 도움말** (Toast, Square, Shopify POS, Lightspeed) | S3·S4·S7에 실제 제품 동작이 나왔다. 화면은 없지만 상호작용 규칙이 정확하다 | "<제품> help <기능>". 공용 기기·교대·되돌리기 문제는 **POS 도움말**이 가장 가깝다 |
| **병원 IT 안내 PDF** (Houston Methodist 등) | Epic 화면 변화와 현장 실수(이전 사용자 로그인)를 알 수 있었다 | "Epic Rover/Haiku tip sheet pdf" + 기능. Epic 공식 문서는 공개되지 않으므로 이 경로가 유일하다 |
| **업무 큐 제품** (Zendesk, Linear Triage, Gmail, Apple Mail) | S4·S5의 "다음" 규칙과 그에 대한 반발(Apple Mail 옵션 추가)이 나왔다 | 기능명(auto-advance, play mode, triage)으로 검색 |
| **근거 기관** (Baymard, ISMP, Epic Research) | 제목·요약만 얻었다. 본문은 유료이거나 열리지 않았다 | 원문은 브라우저로 직접 열어야 한다 |
| **Mobbin·Refero·Page Flows·Godly·Dribbble** | 이번 환경에서는 **수확 없음**(검색 색인 없음, 로그인 벽). Dribbble은 컨셉 샷만 나옴 | 사람이 로그인해 앱 검색으로 확인. 추천 검색: Mobbin iPad에서 `Toast`, `Square`, `Shopify POS`, `Linear`, `Stripe`; 화면 유형 `Bulk actions`, `Filter`, `Table`, `Login - PIN`. Page Flows에서 `Linear triage`, `Superhuman` |

---

## 오케스트레이터에게

1. **WebFetch가 전부 실패했다(DNS ENOTFOUND).** 모든 카드는 검색 발췌 기반이고 화면 이미지를 하나도 보지 못했다. 비주얼 열이 약하다. 사용자나 디자이너가 Mobbin 등에서 §5 검색어로 화면을 직접 확인해야 비주얼 레퍼런스가 완성된다.
2. **REF 번호**: REF-301~338. REF-319는 비워 두었다.
3. **S7 카드는 O8에 임시 매핑했다.** 실제 대상은 N4·F16이다. M1의 O# 통합 뒤 재매핑해야 한다.
4. ⚑ PM 확인 필요 후보: REF-303(열 순서 변경), 310(프리셋 기능), 318(되돌리기 서버 비용), 320(실시간 '보는 중'), 326(S5 신규 화면), 334(인증 연동).
5. 사실 확인이 필요한 항목: 기기 OS(iPad인지), 사원증 바코드/RFID 여부, HIS 조회 응답 시간(REF-309 판단용), 태블릿을 쥐는 방식(REF-314 vs 316).

## 요약
ePRIS 화면 7개에 대해 업무용 레퍼런스 카드 37개(REF-301~338)를 모았다. 디자인 시스템 문서, POS 도움말, 병원 IT 안내에서 주로 나왔다. 화면별로 가장 강한 레퍼런스는 Fiori Data Table, NSW 필터 규칙, Spectrum Action Bar, Zendesk Play, Fiori 이전/다음, Epic Rover BCMA, Toast 접근 코드다.
원문과 화면 이미지를 하나도 열지 못했다. 그래서 비주얼 열이 가장 약하고 감사는 아직 하지 않았다.

## 신뢰도
- 카드별 0.3~0.6이고 중앙값은 약 0.45다. 모두 검색 발췌 기반이며 원문과 이미지는 미확인이다.
- 가장 높은 카드: REF-314 Spectrum, REF-334 Toast (0.6). 공식 문서이고 여러 발췌가 서로 일치한다.
- 가장 낮은 카드: REF-329 승무원 앱, REF-305 스크롤 위험 (0.3~0.35).
- 텍스트 스케치와 why_needed·cost는 모두 내 초안(가설)이다.

## 주의사항
- 이미지·화면은 복제하지 않았다. 링크와 설명만 있다. 스케치는 출처 구조를 ePRIS에 맞춰 재구성한 것이고 원본 화면이 아니다.
- 수집 전용이다. 채택/보류/기각 판단은 하지 않았다(`status: 미감사`). §4의 충돌 5건은 감사에서 먼저 다뤄야 한다.
- 제품 동작은 버전마다 바뀐다(Carbon 선택 임계값, Gmail 모바일 지원, Apple Mail iPad 여부). 인용할 때는 시점을 함께 적는다.
- 남의 화면을 많이 볼수록 기능이 늘어난다. 카드 37개 중 실제로 채택할 것은 소수여야 한다.

## 다음 단계 제안
1. 사람이 §5 경로로 Mobbin/Page Flows에서 Toast·Square·Shopify POS·Linear 화면을 직접 확인해 비주얼 열을 채운다.
2. M3 통합 웨이브에서 이 파일, m3a, m3b를 합쳐 감사(채택/보류/기각)하고 m3-references.md에 옮긴다. §4 충돌부터 다룬다.
3. 약제부 회의 질문에 추가: 태블릿 쥐는 방식, 사원증 형태, 긴급 큐를 여러 약사가 동시에 보는지(REF-320 필요 여부).
