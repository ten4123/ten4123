# M3-b 도메인 리서치: ePRIS

> 모듈: M3-b 도메인 리서처 · 프로젝트: `epris` · 관련 요구: R-025, R-030, R-036, R-058, R-066 · 문서 간 불일치 X2~X4
> 기존 조사 `docs/research/a3-b2b-clinical-designers.md`의 B4(상태 = 색 + 모양 + 라벨)와 C3(경고 피로·티어링)는 다시 조사하지 않았다. 이 문서는 그 위에 **색·시각 위계** 근거만 추가한다.
> 상태 정의와 전이는 M6 담당이므로 다루지 않는다. 상태 이름은 원안·세부계획의 이름을 그대로 쓴다.

---

## v1 (2026-10-23) 상태 색 위계

### 0. 조사 방법과 한계

- WebFetch 시도(carbondesignsystem.com, atlassian.design, experience.sap.com, w3.org)는 모두 `getaddrinfo ENOTFOUND`로 실패했다. **모든 외부 근거는 WebSearch 발췌다.** 그래서 카드 신뢰도를 0.1~0.2씩 낮췄다.
- 대비비와 색차는 WCAG 2.x 상대휘도 공식과 CIELAB(D65)로 **손으로 계산**했다. 반올림 오차는 약 ±0.05(대비비), ±1(ΔE)이다. 확정하기 전에 도구(예: Stark, colorjs)로 재검증해야 한다.
- 색각 이상 시뮬레이션은 Viénot(1999) 제2색약(deutan) 선형 RGB 근사 행렬로 계산했다. 근사값이다.

---

### 1. 원안 5색 정량 평가 (R-030)

#### 1-1. 텍스트 대비 (WCAG 1.4.3, 본문 AA 4.5:1 · AAA 7:1)

공식: 상대휘도 L = 0.2126R + 0.7152G + 0.0722B (sRGB 선형화 후), 대비비 = (L밝음 + 0.05) / (L어두움 + 0.05). #000의 L은 0, #222의 L은 약 0.0160이다.

| 상태(원안) | HEX | 상대휘도 L | vs #000 | vs #222 | vs 흰 배경(#fff) ※ | 판정 |
|---|---|---|---|---|---|---|
| 선택 | `#b5d5d4` | 0.622 | **13.4 : 1** | **10.2 : 1** | 1.56 : 1 | 텍스트 AAA 통과 |
| 보류·반납 | `#eacccc` | 0.650 | **14.0 : 1** | **10.6 : 1** | 1.50 : 1 | 텍스트 AAA 통과 |
| 감사 | `#adc5d9` | 0.538 | **11.8 : 1** | **8.9 : 1** | 1.79 : 1 | 텍스트 AAA 통과 |
| 검토 | `#fbe5d6` | 0.814 | **17.3 : 1** | **13.1 : 1** | 1.22 : 1 | 텍스트 AAA 통과 |
| 문의/HD | `#afabab` | 0.411 | **9.2 : 1** | **7.0 : 1** | 2.28 : 1 | #222 텍스트는 AAA 경계(6.99). AA는 통과 |

※ "흰 배경 대비"는 행 배경색이 상태 표시 그 자체일 때 인접한 흰 행과의 대비다. WCAG 1.4.11(비텍스트 3:1)을 행 배경에 적용할지는 해석의 문제다. 그래도 **5색 모두 3:1에 못 미친다**(1.2~2.3). 따라서 행 배경만으로는 1.4.11 기준의 상태 표시가 되지 못하므로, 텍스트·아이콘·막대 같은 보조 단서가 필요하다는 결론이 나온다. 신뢰도 0.8.

**결론 1**: 검정이나 #222 텍스트의 가독성에는 문제가 없다. 신뢰도 0.85. 다만 D/C·보류를 색 텍스트(빨강 등)로 표시하는 현 설계(R-025)는 그 텍스트 색의 HEX가 설계서에 없어서 계산하지 못했다. 색 텍스트를 쓴다면 각 배경 위에서 4.5:1을 넘는지 반드시 확인해야 한다.

#### 1-2. 색상 간 구분성 (CIELAB, D65)

| 상태 | L\* | a\* | b\* | 채도 C\* |
|---|---|---|---|---|
| 선택 `#b5d5d4` | 83.0 | −10.7 | −3.1 | 11.2 |
| 보류·반납 `#eacccc` | 84.5 | +10.6 | +3.8 | 11.3 |
| 감사 `#adc5d9` | 78.4 | −3.8 | −12.7 | 13.3 |
| 검토 `#fbe5d6` | 92.3 | +5.1 | +10.0 | 11.2 |
| 문의/HD `#afabab` | 70.3 | +1.5 | +0.5 | 1.6 |

쌍별 색차 ΔE76(일반 색각, 큰 값일수록 잘 구분됨. 대략 ΔE 10 미만은 "나란히 놓아야 구분", 20 이상은 "따로 봐도 구분"이라는 경험칙을 썼다. 이 기준은 가설 수준이다):

| | 보류 | 감사 | 검토 | HD |
|---|---|---|---|---|
| **선택** | 22.4 | **12.7** | 22.5 | 18.0 |
| **보류** | | 22.7 | **11.4** | 17.2 |
| **감사** | | | 28.1 | 16.4 |
| **검토** | | | | 24.3 |

**선택 vs 감사**(오케스트레이터 질의):
- 일반 색각에서 ΔE76은 12.7, ΔE2000은 약 11(손 계산)이다. 휘도 대비는 1.14:1에 불과하다. 두 색은 명도가 거의 같고 차이는 색상(청록 vs 파랑)뿐이다.
- 제2색약 시뮬레이션에서는 ΔE76이 약 11, ΔE2000이 약 7~8(근사)로 줄어든다. 두 색 모두 "푸른 회색"으로 수렴하고, 남는 차이는 감사 쪽이 약간 더 어둡고 푸르다는 것뿐이다.
- 판단: 두 행을 **나란히 두면 구분되지만, 한 행만 보고 어느 상태인지 알아맞히기는 어렵다.** 공용 태블릿, 조제실 조명(눈부심), 색각 이상 사용자라는 조건이 겹치면 오인할 위험이 있다. 신뢰도 0.7.
- 더 큰 문제: 선택이 **배경을 교체**하는 방식이면 감사 상태 행을 체크하는 순간 감사 색이 사라진다. 색 거리보다 채널 설계가 먼저 풀어야 할 문제다(→ 패턴 #2).

**추가로 발견한 문제**(요청 범위 밖이지만 R-066에 직결된다):
- **F-a. 5색 모두 채도가 같은 수준(C\* 11~13)인 파스텔이다.** 드문 상태(보류)와 잦은 상태(검토·감사)가 같은 강도로 칠해진다. R-066이 요구하는 "드문 상태 강조, 잦은 상태 톤다운" 위계가 원안 팔레트에는 없다. 신뢰도 0.8.
- **F-b. 보류(드묾·강조 대상)와 검토(잦음·톤다운 대상)는 ΔE 11.4로 같은 따뜻한 계열이다.** 제2색약 시뮬레이션에서는 둘 다 베이지로 수렴하고, 휘도 대비 약 1.23:1의 명도 차만 남는다. 가장 강조해야 할 상태가 가장 흔한 상태와 섞인다. 신뢰도 0.7.
- **F-c. HD 회색(#afabab)은 명도가 가장 낮아서(L\* 70) 시각적으로는 가장 눈에 띈다.** 그런데 회색은 관습적으로 "비활성·완료·무시"로 읽힌다. 게다가 세부계획 3색 체계(R-058)는 **"접수 = 회색"**이어서, 둘을 통합하면 HD와 접수가 같은 색 계열로 충돌한다(X4). 신뢰도 0.7.
- **F-d. 검토자·감사자 이름이 모두 파란 텍스트다(R-036, X2).** 1차 검토와 2차 감사를 색으로도 모양으로도 구분할 수 없다. WCAG 1.4.1 이전에 "consistency" 휴리스틱 문제다. 신뢰도 0.85(설계서 사실 기반).

---

### 2. 레퍼런스 카드

```yaml
id: REF-101
type: 패턴
title: "Carbon 상태 표시 패턴: 심각도별 모양+색+기호, 그룹은 최고 주의 색으로 집약"
source: "https://carbondesignsystem.com/patterns/status-indicator-pattern (+ v10 페이지) — WebSearch 발췌"
designer_or_org: "IBM Carbon"
problem_it_solves: "여러 상태를 한 화면에 둘 때 심각도 위계와 과부하 방지"
applies_to: [R-030, R-066]
evidence: "\"Different shapes and colors enable users to quickly assess and identify status\"; 그룹 집약 시 \"use the highest-attention color to represent the group\"; 지표가 5~6개를 넘으면 과부하 경고; 행동이 필요 없는 상태에는 지표를 쓰지 말 것(발췌 요약)"
why_needed: "환자 카드 그룹마다 약품 행 여러 개가 있다. 카드 헤더에서 그룹 내 가장 주의가 필요한 상태(보류·D/C 존재 여부)를 바로 보여줘야 '한눈에' 원칙을 지킨다. '행동 불필요 상태는 지표 생략'은 검토·감사 톤다운의 직접 근거다"
cost: "카드 헤더에 집약 지표를 둘 영역이 필요하다. 집약 규칙(어느 상태가 최고 주의인가)을 M6 전이표와 맞춰야 한다"
how_to_apply: "카드 헤더에 '보류 2 · D/C 1' 형식의 집약 배지를 둔다. 상태 종류 수는 5~6개 이내로 유지한다"
confidence: 0.6
```

```yaml
id: REF-102
type: 원칙
title: "Carbon 색 접근성: 색만으로 의미 전달 금지, 상태·경계 시각정보 3:1"
source: "https://carbondesignsystem.com/guidelines/accessibility/color — WebSearch 발췌"
designer_or_org: "IBM Carbon (WCAG 1.4.1 / 1.4.11 인용)"
problem_it_solves: "색 의존 상태 표시의 접근성 실패"
applies_to: [R-025, R-030, R-036]
evidence: "\"Don't rely on color alone to convey meaning … distinguishing one visual element from another.\" \"Visual information used to indicate states … must have a contrast ratio of 3:1 against adjacent colors.\""
why_needed: "원안 5색은 모두 흰 행 대비 1.2~2.3:1이다(§1-1). 색 배경만으로는 상태 표시 기준을 못 넘는다. 색각 이상 사용자도 공용 태블릿을 쓸 수 있다"
cost: "상태마다 텍스트 라벨이나 아이콘이 추가로 필요하다. 상태 열 폭이나 좌측 막대 폭(약 4px)만큼 공간이 든다"
how_to_apply: "상태는 '색 + 텍스트(보/D/C/HD) + 모양(막대·아이콘)' 중 최소 2채널로 표시한다. 막대·아이콘은 인접 색 대비 3:1 이상으로 만든다"
confidence: 0.7
```

```yaml
id: REF-103
type: 원칙
title: "WCAG 1.4.11 Understanding: 선택 상태 지표도 3:1"
source: "https://www.w3.org/WAI/WCAG22/Understanding/non-text-contrast (WebFetch 실패, WebSearch 발췌) / https://tabnav.com/academy/wcag/success-criterion-1.4.11"
designer_or_org: "W3C WAI"
problem_it_solves: "선택 표시가 너무 약해서 못 보는 문제"
applies_to: [R-030]
evidence: "선택·포커스 등 상태를 나타내는 시각정보는 인접 색 대비 3:1(2차 해설). 1.4.1과 동시 충족 필요(tabnav 요약)"
why_needed: "선택 #b5d5d4는 흰 행 대비 1.56:1이고 감사 행 대비 1.14:1이다. 배경색 교체만으로는 선택 상태가 기준에 못 미친다"
cost: "체크박스 외에 선택 테두리나 좌측 마커 같은 추가 시각요소가 필요하다"
how_to_apply: "선택은 체크박스(채움, 3:1 이상) + 행 외곽선 2px(진한 색)로 표시하고, 배경 교체는 쓰지 않는다"
confidence: 0.65
```

```yaml
id: REF-104
type: 패턴
title: "선택 행 = 반투명 오버레이 / 전용 토큰 (Material·Carbon)"
source: "Flutter DataRow docs(Material 구현) https://api.flutter.dev/flutter/material/DataRow/color.html ; Carbon data table style https://carbondesignsystem.com/components/data-table/style — WebSearch 발췌"
designer_or_org: "Google Material(Flutter 구현), IBM Carbon"
problem_it_solves: "선택 상태와 다른 행 스타일의 공존"
applies_to: [R-030]
evidence: "Material(Flutter): \"Selected rows has a grey translucent color\", \"recommended to use a translucent background color\", 예시는 primary 8% 알파. Carbon: 선택 행 배경 $layer-selected, 하단 테두리 $border-subtle-selected도 함께 바뀜"
why_needed: "ePRIS에서는 선택과 처리 상태가 동시에 존재한다. 반투명 오버레이는 아래 상태 색을 지우지 않는다. Carbon은 배경 하나만 바꾸지 않고 테두리까지 함께 바꾼다"
cost: "오버레이를 쓰면 5개 상태 × 선택 여부로 10개 조합 색이 생긴다. 조합별 대비를 검증해야 한다(테스트 비용)"
how_to_apply: "1안: 선택은 외곽선 + 체크만 쓰고 배경은 그대로 둔다(조합 폭발 없음). 2안: 상태 배경 위에 8~12% 어두운 오버레이 + 외곽선을 얹는다. 1안을 우선 권장한다"
confidence: 0.55
```

```yaml
id: REF-105
type: 패턴
title: "Workday Canvas: 테이블에서는 저강조 상태 지표"
source: "https://canvas.workday.com/components/indicators/status-indicator — WebSearch 발췌"
designer_or_org: "Workday Canvas"
problem_it_solves: "테이블 전체가 상태 색으로 덮여 시각 피로가 생기는 문제"
applies_to: [R-066]
evidence: "테이블처럼 지표가 화면을 지배할 수 있는 곳에는 low-emphasis 지표를, high-emphasis는 헤더·섹션 제목과 함께 쓰도록 권장(발췌 요약)"
why_needed: "하루 수백 건 검토에서 대부분의 행은 검토·감사 상태다. 이 행들에 색 배경을 칠하면 '전부 강조 = 아무것도 강조 안 됨'이 된다. 10/21 요구 '빈도 높은 상태 톤다운'의 직접 근거다"
cost: "검토·감사 행의 배경색을 빼면 원안(R-030)의 '감사 = 행 파랑'을 축소하게 된다 ⚑ PM 확인 필요. 약사가 익숙해진 종이·기존 시스템 관습과 다를 수 있다"
how_to_apply: "잦은 상태는 상태 열의 작은 텍스트·아이콘(회색·청색 계열)으로만 표시하고, 배경은 흰색을 유지한다"
confidence: 0.55
```

```yaml
id: REF-106
type: 패턴
title: "SAP Fiori: 반응형 테이블 행 하이라이트(criticality 기반) + navigated 지표"
source: "https://www.sap.com/design-system/fiori-design-web/v1-96/discover/frameworks/sap-fiori-elements/tables-and-lists/table-rows-sap-fiori-elements-2 ; Fiori Guidelines 1.74 릴리스 노트 https://blogs.sap.com/t5/technology-blogs-by-sap/out-now-sap-fiori-design-guidelines-version-1-74/ba-p/13436440 ; Semantic colors https://www.sap.com/design-system/fiori-design-web/v1-96/foundations/best-practices/ui-elements/how-to-use-semantic-colors — WebSearch 발췌"
designer_or_org: "SAP Fiori"
problem_it_solves: "행 단위 상태를 열 추가 없이 표시"
applies_to: [R-030, R-066]
evidence: "\"In responsive tables, you now have an option to highlight items.\" \"Highlighting Line Items Based on Criticality\". 정보색은 새로 추가된 행 강조에 쓰고, 순수 장식에는 시맨틱 색 금지. sap.ui.table RowSettings: highlight 기본값 None"
why_needed: "엔터프라이즈 시스템이 '행 전체 칠하기' 대신 별도 하이라이트 지표로 행 상태를 표시한 사례다. 하이라이트 기본값이 None이라는 점은 대부분의 행에 표시가 없다는 뜻이고, 톤다운 원칙과 맞는다"
cost: "행 앞 영역에 지표 공간이 든다. 태블릿 가로 스크롤 유지 조건에서 고정 열과 함께 설계해야 한다"
how_to_apply: "드문 상태만 행 좌측에 진한 막대(4px)를 두고 나머지는 None으로 둔다. 하이라이트가 좌측 막대 형태라는 점은 이번 검색 발췌로 확인하지 못했다. 원문 확인 필요"
confidence: 0.5
```

```yaml
id: REF-107
type: 패턴
title: "Atlassian Lozenge: subtle(기본) vs bold 2단 강도"
source: "https://developer.atlassian.com/platform/forge/ui-kit/components/lozenge/ ; https://aui.atlassian.com/aui/7.1/docs/lozenges.html — WebSearch 발췌"
designer_or_org: "Atlassian"
problem_it_solves: "같은 상태 의미에서 강조 강도를 따로 조절"
applies_to: [R-066]
evidence: "appearance: default/inprogress/moved/new/removed/success, isBold로 bold 적용. default는 'to do / not started' 같은 일반 상태, removed는 'failed/deleted' 같은 문제 상태. 언제 bold를 쓰는지에 대한 공식 기준은 발췌에서 확인 못 함"
why_needed: "'의미(색상 계열)'와 '강도(subtle/bold)'를 두 축으로 분리한 구조가 빈도 기반 위계의 토큰 설계에 그대로 쓰인다. 보류·D/C는 bold, 검토·감사는 subtle로 배정할 수 있다"
cost: "토큰이 상태 수 × 2로 늘어난다. bold 사용 기준을 직접 정의해야 한다"
how_to_apply: "M6 색 토큰을 status.{hold|dc|hd|review|audit}.{subtle|bold} 형태로 정의한다"
confidence: 0.5
```

```yaml
id: REF-108
type: 원칙
title: "Polaris Badge: 톤은 색이 아니라 상태 의미로 고른다"
source: "https://shopify.dev/docs/apps/build/app-home/migrate-from-polaris-react/badge — WebSearch 발췌"
designer_or_org: "Shopify Polaris"
problem_it_solves: "색 선택이 의미와 어긋나는 문제(예: 검토자·감사자 둘 다 파랑)"
applies_to: [R-036]
evidence: "\"Choose the new tone from the status meaning; don't use a value only to reproduce the previous color.\" critical = urgent problems / destructive, caution(구 attention) = advisory status"
why_needed: "X2(검토 주황 → 파랑)는 색을 의미 없이 고른 사례다. 의미 → 톤 매핑 표를 먼저 만들어야 재발을 막는다"
cost: "의미-톤 매핑 문서 1장이 필요하다(작음)"
how_to_apply: "R-030·R-058 통합 시 '의미 → 강도 → 색' 순서로 표를 작성한다(M6)"
confidence: 0.55
```

```yaml
id: REF-109
type: 근거
title: "전주의 처리(pop-out): 색 pop-out은 주변(방해 자극)과의 차이에 달려 있다"
source: "Healey/UBC·Rensink 강의 자료 https://www2.psych.ubc.ca/~rensink/courses/psyc579/05.1-essay-a.pdf ; Rutgers 강의 https://aspoerri.comminfo.rutgers.edu/Teaching/InfoVisOnline/Lectures/Lecture2/Lecture2Handout.pdf ; arXiv 2601.20080(locatability) — WebSearch 발췌"
designer_or_org: "시각 인지 연구(Healey, Rensink 등)"
problem_it_solves: "드문 상태를 '즉각 인지'시키는 조건"
applies_to: [R-066]
evidence: "\"The larger difference, the more likely a color will pop out.\" 표적과 방해 자극이 특징을 공유하면(conjunction) 순차 탐색. 작은 면적은 고채도, 큰 면적은 저채도. 최근 연구는 hue가 항상 자동 pop-out되지는 않는다고 반박"
why_needed: "F-a·F-b의 이론적 근거다. 보류(분홍)가 검토(살구) 사이에 있으면 방해 자극과 너무 비슷해서 pop-out이 안 된다. 강조 대상은 색상·명도·채도에서 다수 행과 멀어야 하고, 큰 면적(행 배경)은 저채도, 작은 면적(막대·아이콘)은 고채도로 칠해야 한다"
cost: "강조 색은 고채도 소면적 요소(막대·아이콘)로 구현해야 하므로 컴포넌트가 늘어난다"
how_to_apply: "다수 행(검토·감사)은 무채색 근처로 두고, 드문 상태만 고채도 소면적 + 저채도 배경 조합으로 표시한다"
confidence: 0.6
limitations: "강의 자료·발췌 수준이다. 실험 조건은 단순 자극이라 실제 표 UI로 일반화하는 것은 추론이다. hue pop-out이 무조건 일어난다는 해석에는 반론이 있다(arXiv 2026)"
```

```yaml
id: REF-110
type: 근거
title: "ISMP·FDA·AMA: 의약품 색 코딩에 대한 신중론"
source: "ISMP Canada CJHP 2009 https://www.ismp-canada.org/download/cjhp/cjhp-2009-04-point.pdf ; APSF Pro/Con https://www.apsf.org/article/pro-con-debate-color-coded-medication-labels-pro/ ; AMA CSAPH i17 report ; AJN Off the Charts — WebSearch 발췌"
designer_or_org: "ISMP, FDA(2013 draft guidance), AMA"
problem_it_solves: "색이 '읽기'를 대체해 생기는 오류"
applies_to: [R-025, R-030, R-066]
evidence: "\"Colour-coding has not been tested as a way to prevent medication errors, and evidence exists that it may actually contribute to some errors.\" \"acting as a substitute for reading the label\" \"The more colors that are used, the greater the risk of confusing a color and its meaning.\""
why_needed: "약사가 행 색만 보고 '감사 끝남'으로 판단하고 넘어가면 감사 누락으로 이어진다(제품 원칙 1). 색 수를 늘릴수록 혼동이 커진다는 경고는 5색 + 3색 통합 시 색 수를 억제할 근거가 된다"
cost: "색을 줄이고 텍스트 라벨을 늘리면 행당 정보 밀도가 약간 오른다"
how_to_apply: "색은 '찾기(스캔)' 보조로만 쓰고, 처리 판단의 근거는 텍스트 라벨(감사자명·시간·상태어)로 둔다. 통합 팔레트의 서로 다른 색상은 4~5개 이내로 제한한다"
confidence: 0.6
limitations: "이 논의는 약품 라벨·주사기 색 코딩에 관한 것이다. 화면 UI 상태색에 직접 적용한 연구는 아니므로 유추다. 근거는 전문가 의견과 사례 보고 중심이고 RCT는 없다. 마취과(ASA)의 반대 입장도 있다"
```

```yaml
id: REF-111
type: 원칙
title: "색각 이상: 적록 계열 의존 회피와 중복 부호화(Okabe-Ito)"
source: "Okabe-Ito 팔레트 요약 https://dev.conceptviz.app/fr/blog/okabe-ito-palette-hex-codes-complete-reference ; cvdsafe https://pypi.org/project/cvdsafe/ ; CVD 종설 PMC12385717 — WebSearch 발췌"
designer_or_org: "Okabe & Ito / 학술 종설"
problem_it_solves: "공용 태블릿에서 색각 이상 사용자가 상태를 오인하는 문제"
applies_to: [R-030, R-058]
evidence: "적록 색각 이상은 북유럽계 남성 최대 8%, 여성 0.5%. 아시아 집단은 이보다 낮게 보고됨(종설). Okabe·Ito는 중복 부호화(redundant coding)를 함께 권장"
why_needed: "약사 집단에도 색각 이상자가 있을 수 있다. 원안의 보류(분홍) vs 검토(살구), 선택(청록) vs 감사(파랑)는 시뮬레이션에서 구분이 약해진다(§1-2)"
cost: "확정 전 시뮬레이터 검증 1회가 필요하다. 팔레트를 바꾸면 원안 색과 달라지므로 고객 설명이 필요하다"
how_to_apply: "강조 색은 명도 차를 함께 확보하는 파랑·주황 축을 우선 쓰고, 빨강·초록 대비에 의존하지 않는다. 모든 상태에 텍스트·모양을 병기한다"
confidence: 0.55
limitations: "한국인 유병률 수치는 이번 검색에서 확인하지 못했다. Okabe-Ito는 차트용 팔레트이고 UI 상태색용이 아니다"
```

```yaml
id: REF-112
type: 패턴
title: "Oracle Health(Cerner) PowerChart: '약사 미검증'을 전용 아이콘으로 표시"
source: "HealthPEI Orders Tab 매뉴얼 https://src.healthpei.ca:443/sites/src.healthpei.ca/files/CIS/CIS%20-%20Nurse%20Training%20Materials/Orders_Tab_Organization.pdf ; Munson Healthcare Orders Page Overview ; MKUH Clinical Validation QRG — WebSearch 발췌"
designer_or_org: "Oracle Health(Cerner) 도입 병원 교육자료"
problem_it_solves: "약사 검증 상태를 처방 목록에서 구분"
applies_to: [R-030, R-036]
evidence: "\"Verify Indicator\": 약사 검토 전 처방 표시, 별도 \"Refusal Indicator\"(약사 거부). NHS MKUH Pharmacy Medication Manager는 미검증 약을 막자사발(mortar-and-pestle) 기호로 표시"
why_needed: "실제 임상 시스템이 검증 상태를 행 색이 아니라 **기호(아이콘)**로 구분한다는 도메인 선례다. 검토자·감사자 구분(X2)에 아이콘·라벨 방식을 쓸 근거가 된다"
cost: "아이콘 학습 비용이 든다. 범례가 필요하다. 아이콘 수가 늘면 인식률이 떨어진다"
how_to_apply: "검토(1차)와 감사(2차) 완료를 서로 다른 짧은 텍스트 표지('검'·'감') 또는 아이콘 + 이름으로 구분한다. 색은 동일 계열도 허용한다"
confidence: 0.45
limitations: "병원별 교육자료라서 구성이 기관마다 다르다. Oracle 공식 범례는 아니다. Epic 약사 verify 큐의 색 범례는 이번 검색에서 확인하지 못했다(UConn ED 문서에 범례 언급만 있고 값은 없음)"
```

```yaml
id: REF-113
type: 원칙
title: "색 절제: 한 화면 강조색 최소화(색이 많을수록 신호 희석)"
source: "Appian SAIL Using Colors https://docs.appian.com/suite/help/26.3/sail/ux-color-overview.html ; SSW Rules https://www.ssw.com.au/rules-beta/add-a-spot-of-color-for-emphasis — WebSearch 발췌"
designer_or_org: "Appian, SSW"
problem_it_solves: "모든 상태를 칠해 강조가 무력화되는 문제"
applies_to: [R-066]
evidence: "\"If everything is emphasized, nothing stands out.\"(SSW) 색은 절제해서 쓰고, 추가 색 요소는 모두 주의를 두고 경쟁한다(Appian 요약)"
why_needed: "원안은 5개 상태 모두에 행 배경을 칠한다. 빈도 기반 톤다운(R-066)의 일반 원칙이다"
cost: "원안의 '모든 상태 행 색' 요구를 일부 축소한다 ⚑ PM 확인 필요"
how_to_apply: "REF-105와 함께 쓴다. 행 배경 색은 드문 상태에만 쓴다"
confidence: 0.5
limitations: "NN/g 출처를 찾으려 했지만 검색에 나오지 않았다. 디자인 시스템과 컨설팅 가이드 수준이다"
```

> 재사용(중복 조사 안 함): a3 B4(Dynatrace, 강조 아이콘 한 뷰에 하나), a3 C3(JAMIA 2019 role-tailoring·티어링, 약사 override율 90% 이상은 단일 기관 초록), a3 C7(약국 시스템의 consistency 위반). 경고 피로 문헌은 **팝업 경고**에 관한 것이지 **행 상태색**에 관한 것이 아니다. 그래서 "상태색을 줄이면 피로가 준다"는 직접 근거는 없고, 유추일 뿐이다. 신뢰도 0.5.

---

### 3. 표현 수단별 사용 기준 (조사 종합 · 가설)

| 수단 | 강도 | 어울리는 상태 | 근거 | 주의 |
|---|---|---|---|---|
| 행 배경(저채도) | 중간, 면적이 큼 | 드문 상태의 보조 | REF-106, REF-109(큰 면적은 저채도) | 잦은 상태에 쓰면 신호가 희석된다(REF-113). 1.4.11 단독 미달 |
| 좌측 상태 막대(4px, 고채도) | 높음, 면적이 작음 | 드문 상태(보류·D/C·반납·HD) | REF-106, REF-109, 검색 추론 | 선택 표시와 같은 좌측 모서리를 쓰지 않는다 |
| 배지·로젠지(텍스트) | 의미 정확 | 모든 상태(subtle/bold 2단) | REF-107, REF-108 | 열 폭이 필요하다. 원안 DC 열("D","보")을 재사용할 수 있다 |
| 아이콘 | 높음, 학습 필요 | 역할 구분(검토 vs 감사), 경고 | REF-112, a3 B4 | 한 뷰에 강조 아이콘은 1종으로 제한(a3 B4) |
| 텍스트 색만 | 낮음 | 쓰지 않음 | REF-102 | 현 설계서 D/C·보류 방식은 약해서 R-025 재요구의 원인이 됐다 |
| 선택(체크 + 외곽선) | 일시적 | 모든 상태 위에 겹침 | REF-103, REF-104 | 배경을 교체하지 않는다 |

---

### 4. ePRIS 적용 패턴 후보 Top 6

| # | 패턴 | 왜 (ePRIS 맥락) | 출처 |
|---|---|---|---|
| 1 | **빈도 기반 2단 강조.** 잦은 상태(접수·검토·감사)는 흰 배경 + 상태 열의 subtle 라벨로 둔다. 드문 상태(보류·D/C·반납·HD)는 좌측 고채도 막대 + 저채도 배경 + bold 라벨로 둔다 | 원안 5색은 채도가 모두 같아서 위계가 없다(F-a). 보류와 검토가 같은 계열이라 드문 상태가 묻힌다(F-b). 10/21 요구 R-066을 그대로 구현할 수 있다 | REF-105, REF-109, REF-113, REF-101, REF-107 |
| 2 | **상태와 선택의 채널 분리.** 상태는 막대·배경·라벨로, 선택은 체크박스 + 행 외곽선 2px로 표시한다. 선택이 배경을 교체하지 않게 한다 | 선택과 감사의 휘도 대비가 1.14:1이라 서로 오인할 수 있다. 배경을 교체하면 체크한 순간 상태 정보가 사라져 일괄 저장 전에 확인할 수 없다(제품 원칙 1) | REF-103, REF-104, 검색 추론(Ignition 포럼) |
| 3 | **모든 상태를 색 + 텍스트 + 모양으로 이중 부호화**하고, 원안 DC 열의 "D/보/반납/HD" 표기를 유지한다 | 5색 모두 흰 행 대비 3:1 미만이다. 색각 이상이나 눈부신 조명에서 색이 실패할 때의 대체 경로가 필요하다. ISMP는 색이 '읽기'를 대체하는 위험을 경고한다 | REF-102, REF-110, REF-111, WCAG 1.4.1 |
| 4 | **환자 카드 헤더에 최고 주의 상태를 집약**한다(예: "보류 2 · D/C 1") | 카드 그룹 단위로 훑을 때 드문 상태가 있는 환자를 먼저 찾을 수 있다('한눈에' 원칙) | REF-101 |
| 5 | **통합 팔레트의 서로 다른 색상을 4~5개 이내로 제한하고, 회색은 한 의미에만 쓴다.** HD를 회색에서 분리하는 안을 검토한다 | 원안 5색과 세부계획 3색을 합치면 색 수가 과다해진다(X4). 접수 회색과 HD 회색이 충돌한다(F-c). 색 수가 늘수록 혼동이 커진다 | REF-101, REF-110, REF-111 |
| 6 | **검토자(1차)와 감사자(2차)를 색이 아니라 역할 표지('검'·'감' 또는 아이콘) + 이름 + 시간으로 구분**한다 | 현재 둘 다 파란 텍스트라 구분할 수 없다(R-036, X2). 실제 임상 시스템(Cerner)도 검증 상태를 기호로 표시한다. 감사 누락 방지에 직결된다 | REF-112, REF-108, REF-102 |

---

## 오케스트레이터에게

1. **M6 전달**: 원안 5색은 대비에는 문제가 없지만 **위계가 없다**(채도 동일, 보류와 검토가 근접). 색 토큰은 "의미 × 강도(subtle/bold)" 두 축으로 설계할 것을 권한다. 상태 정의와 전이는 건드리지 않았다.
2. **⚑ PM 확인 필요**: 패턴 #1·#5를 채택하면 원안 R-030의 "감사·검토 = 행 배경색"이 "상태 열 라벨"로 축소된다. 원안 요구를 바꾸는 것이므로 고객 확인이 필요하다(m2-traceability 질문 4번 X4와 묶어서 제시하기를 권한다).
3. **미결**: HD를 강조 대상(드묾)으로 둘지 회색(비활성 뉘앙스)으로 둘지는 약사 확인이 필요하다. 10/21 요구는 "HD 강조"인데, 원안 색은 회색이다.
4. **검증 제안(M7)**: (a) 제2색약 시뮬레이터와 실기기 조제실 조명에서 선택/감사, 보류/검토 쌍 판별 테스트, (b) 약사 3명에게 "드문 상태 행 찾기" 시간 측정 think-aloud.
5. 웹 원문 열람이 모두 실패했다(DNS). SAP Fiori 하이라이트의 좌측 막대 형태, Atlassian bold 사용 기준, NN/g 출처는 원문 확인이 필요하다.
6. REF 번호는 다른 모듈과 충돌하지 않도록 101번부터 매겼다. `m3-references.md`로 병합할 때 재번호가 필요하면 조정한다.

## 요약
원안 5색은 텍스트 대비가 충분하다(검정 기준 9.2~17.3:1). 그러나 채도가 모두 같아서 R-066의 빈도 위계가 없다. 선택과 감사(휘도 대비 1.14:1), 보류와 검토(같은 따뜻한 계열)는 혼동될 수 있다.
엔터프라이즈 디자인 시스템(Carbon·Workday·Fiori·Atlassian)과 ISMP 신중론은 "잦은 상태 저강조, 드문 상태는 소면적 고채도 + 라벨, 색만 쓰지 않기"로 수렴한다.
Top 6 패턴 중 #1(빈도 2단 강조)과 #2(선택·상태 채널 분리)를 우선 권한다.

## 신뢰도
- 대비비·색차 계산: 0.8(손 계산, ±0.05 / ±1. 도구 재검증 권장)
- 디자인 시스템 패턴 카드: 0.45~0.7(전부 WebSearch 발췌, 원문 미열람)
- 임상 근거(ISMP·Cerner): 0.45~0.6(라벨 색 코딩과 병원 교육자료 기반, 화면 상태색에 대한 직접 연구 없음)
- 종합 권고(Top 6): 0.65

## 주의사항
- WebFetch가 전부 실패해서 인용문은 검색 발췌다. 특히 Fiori 하이라이트 위치, Atlassian bold 기준, Workday 문구는 원문 확인 전까지 2차 정보다.
- "상태색을 줄이면 경고 피로가 준다"는 직접 근거는 없다. 팝업 경고 연구에서 유추한 것이다(가설).
- ISMP 신중론은 약품 라벨에 관한 것이다. 화면 UI에 적용하는 것은 유추다.
- 색각 이상 시뮬레이션은 근사 행렬이다. 한국인 유병률은 확인하지 못했다.
- 원안 요구 축소(⚑)는 디자이너가 단독으로 결정할 사항이 아니다.

## 다음 단계 제안
1. M6: Top 6의 #1·#2·#6을 상태 전이표와 결합해 색 토큰 초안(의미 × 강도)과 선택 겹침 규칙을 작성한다.
2. PM: R-030 축소와 X4 통합안(5색 + 3색 → 4~5색상 + 2강도)을 고객 질문으로 정리한다.
3. M7: 시뮬레이터와 실기기 조명 판별 테스트, 드문 상태 탐색 think-aloud(약사 3명, RITE).
4. 원문 열람이 가능한 환경에서 Fiori Responsive Table과 Atlassian Lozenge 원문을 확인하고 REF-106·REF-107의 신뢰도를 갱신한다.
