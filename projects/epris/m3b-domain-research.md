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

---

## v2 (2026-10-23) 임상·약제 업무 화면의 레이아웃·정보 구조·인터랙션

> 목적: UI 고도화용 도메인 레퍼런스. v1(상태 색)은 다시 다루지 않는다. 화면은 ① 목록(환자 카드 + 약품 테이블 통합 목록), ② 처방전 뷰(환자별 처방전, R-019·R-060), ③ 긴급 큐(좌 목록/우 상세), ④ 필터 바텀시트, ⑤ 하단 조작 영역, ⑥ 메모다.
> 재사용(중복 조사 안 함): a3 B1(NN/g 테이블 4과업), B2·B3(배치 액션 바), A7(필터 변경 시 선택 유지), C3(경고 피로), C5(BCMA 우회), C6(Tall Man 기본), C10(STAT 우선 정렬 특허, 모바일 검증 7.5분 대 38.9분). 아래 카드는 이들을 **보강하거나 반박하는 것만** 넣었다.

### 0. 조사 방법과 한계

- WebFetch 3건(safetyandquality.gov.au, digitalhealth.wh.org.au, online.ecri.org)은 모두 `getaddrinfo ENOTFOUND`로 실패했다(v1과 같은 증상). **모든 외부 근거는 WebSearch 발췌다.** 카드 신뢰도를 v1과 같은 폭(0.1~0.2)으로 낮췄다.
- 벤더 화면(Epic·Oracle Health·athenahealth·CPSI)은 **공식 문서가 아니라 병원 교육자료·도움말 발췌**다. 병원마다 빌드가 달라서 "그 제품은 이렇다"가 아니라 "그런 구성을 쓰는 현장이 있다" 수준으로 읽어야 한다.
- **찾지 못한 것**: Epic Willow 검증 화면의 환자 헤더 구성, Omnicell·Pyxis·Swisslog 소프트웨어 화면, 국내(세브란스·서울아산·삼성서울·분당서울대 BESTCare) 약사용 모바일·태블릿 화면 공개 자료, Dribbble·Behance의 실무 약국 검증 케이스 스터디, NN/g의 바텀시트 글, NHS CUI 원문(현재 폐기 상태). 공백은 §4에 정리했다.

---

### 1. 레퍼런스 카드 (REF-201~)

#### 1-A. 약사 검증 화면 (벤더·현장 자료)

```yaml
id: REF-201
type: 패턴
title: "Epic Willow: 검증 큐(필터는 관리자 또는 약사가 구성) → Verify Orders 활동에서 처방별 검증/거부"
source: "Brainscape RX100 Willow Inpatient Ch.4 플래시카드 https://brainscape.com/flashcards/rx100-willow-inpatient-fundamentals-chap-12958233/packs/21286500 ; AUB FAQ Willow https://servicedesk.aub.edu.lb/TDClient/1398/Portal/KB/Article/66358/FAQ-Willow ; U Iowa Epic support https://epicsupport.sites.uiowa.edu/node/631 — WebSearch 발췌"
designer_or_org: "Epic (병원 교육자료·학습용 플래시카드 경유)"
problem_it_solves: "검증할 처방이 많을 때 약사별로 볼 범위를 나누고, 처방 단위로 판단"
applies_to: [목록, 긴급 큐, 필터, R-004, R-038]
evidence: "검증 큐에는 미검증 처방과 테크니션이 준비해 약사 확인이 필요한 처방이 들어간다. 관리자가 약사에게 맞는 필터를 만들거나 약사가 직접 만든다. Verify Orders 활동은 용량, 예정 투여 시각, 조제 위치, 조제 제품·양을 보여 주고, 약사가 처방마다 검증 또는 거부를 결정한다. AUB FAQ는 검증 전에 투여 지시와 'Note to Pharmacy' 필드를 확인하라고 안내한다(발췌 요약)"
why_needed: "ePRIS도 약국(입원/항암/TPN)·오더 구분·병동·팀별로 볼 범위가 다르다. '저장된 필터 = 개인 큐'라는 구조는 매번 필터를 다시 거는 비용을 없앤다. 처방 비고(Note to Pharmacy에 해당)를 검증 전 확인 대상으로 둔 점은 R-031 '처방 비고 독립 컬럼'의 도메인 근거다"
cost: "저장 필터(개인 뷰)를 만들면 저장·이름 변경·삭제 UI가 늘어난다. 관리자 기본 뷰를 운영할 주체가 필요하다 ⚑ PM 확인 필요(원안 범위 밖일 수 있음)"
how_to_apply: "1차: 로그인 사번별로 마지막 필터를 복원한다(F06 '세션 전환 시 필터 초기화 없음'과 함께 정책을 정한다). 2차(범위 확인 후): 약국별 기본 뷰 2~3개를 프리셋으로 둔다"
confidence: 0.4
limitations: "학습용 플래시카드와 대학 IT 문서다. Epic 공식 문서가 아니고 화면 레이아웃(헤더 구성, 버튼 위치)은 확인하지 못했다"
```

```yaml
id: REF-202
type: 패턴
title: "Oracle Health(Cerner) PharmNet: 처방 행 Action 열에서 Verify 선택 → 'pending' 표지 → 일괄 Submit"
source: "Western Health PharmNet QRG https://digitalhealth.wh.org.au/wp-content/uploads/2023/04/PharmNet-Verifying-a-Medication-Order-Includes-Product-Assignment-and-Future-Orders.pdf ; PharmNet Rejecting https://digitalhealth.wh.org.au/wp-content/uploads/2023/06/PharmNet-Rejecting-a-Medication-Order.pdf ; Northern Light 'Using Pharmacy Patient Monitor' https://hi.northernlighthealth.org/Flyers/Non-Providers/Oncology/Pharmacy/Pharmacy-Flyers/Using-Pharmacy-Patient-Monitor.aspx — WebSearch 발췌(WebFetch 실패)"
designer_or_org: "Oracle Health(Cerner) 도입 병원 교육자료(호주 Western Health, 미국 Northern Light)"
problem_it_solves: "여러 처방을 하나씩 판정한 뒤 한 번에 확정하고, 확정 전 상태를 눈에 보이게 하기"
applies_to: [하단 조작 영역, 목록, R-038, R-026]
evidence: "Pharmacy Medication Manager에서 미검증 처방의 Action 열에서 Verify를 고르고 Apply로 Verify Med Order 창을 연다. 검증·거부한 처방은 제출 전까지 pending 표지가 붙는다. 거부는 MAR에도 표시되어 간호사가 투약 기록 시 경고를 본다(<< 표지). Pharmacy Patient Monitor(PPM)는 약사 조치가 필요한 처방이 있는 **환자 단위** 목록이고, 위치 필터 등으로 맞춤 뷰를 만든다"
why_needed: "ePRIS의 '체크 → 감사 저장'은 같은 2단계(표시 → 확정) 구조다. Cerner는 확정 전 행에 **'아직 저장 안 됨' 표지**를 붙인다. ePRIS는 체크만 하고 저장하지 않은 채 필터를 바꾸거나 화면을 떠나는 상황(감사 누락, 제품 원칙 1)에 그대로 대응한다. 환자 단위 큐(PPM)와 처방 단위 테이블을 나눈 구조는 '환자 카드 + 약품 테이블' 구조의 선례다"
cost: "미저장 표지와 이탈 경고 상태가 하나 늘어난다. 상태 종류가 늘면 v1 REF-101의 5~6개 한도와 충돌하므로 '선택' 채널(체크 + 외곽선)에 합쳐야 한다"
how_to_apply: "하단 조작 영역에 'N건 선택 · 미저장'을 표시한다. 미저장 선택이 있는 채로 필터 변경·뒤로가기·로그아웃을 하면 확인을 받는다. 미저장 표지는 별도 색이 아니라 선택 외곽선의 일부로 표시한다"
confidence: 0.45
limitations: "기관별 QRG다. NHS MKUH는 'Verify를 쓰지 말라'고 안내한다(약국 시스템 구성이 다름). 화면 그림은 보지 못했다"
```

```yaml
id: REF-203
type: 패턴
title: "athenaOne Pharmacy Verification: 위치 필터(부서 → 세부 병동·병실), 미배정 'Overflow' 버킷, 처방 클릭 시 행 확장"
source: "https://help.athenahealth.com/Ohelp/Content/Hospital/H_Pharmacy_Verification_PH.htm ; Medication Preparation https://help.athenahealth.com/Ohelp/Content/Hospital/H_Pharmacy_Medication_Preparation_PH.htm — WebSearch 발췌"
designer_or_org: "athenahealth (벤더 공식 도움말)"
problem_it_solves: "병동 계층이 깊을 때의 필터, 분류되지 않은 처방의 누락, 한 행의 세부 정보 확인"
applies_to: [필터, 목록, R-045, R-069, R-042]
evidence: "좌상단 FILTERS → Filter by Location 창. 부서 체크박스를 고르고 DETAILS로 세부 병동·병실을 고른다. Overflow 필터는 위치가 배정되지 않았거나 자유 텍스트 위치인 환자를 모은다. Unverified Orders에서 약을 누르면 처방의·투여 일정 등 상세가 펼쳐진다. 조제 화면은 검증 상태·조제 상태·예정 시각으로 필터하고 예정 시각·환자·약으로 정렬한다"
why_needed: "10/21 요구는 긴급 병동 필터를 라디오(단일)에서 **중분류 복수 선택**으로 바꾸는 것이다(R-045·R-069). '대분류 체크 + 세부 펼치기'가 그 구조다. 'Overflow(미분류)' 버킷은 분류 체계 밖의 처방이 어떤 필터 조합에서도 보이지 않는 **필터 누락**을 막는다. 23:59:59 경계 누락(R-008)과 같은 계열의 위험이다"
cost: "2단 계층 체크는 바텀시트 높이가 늘어난다. '기타/미분류' 정의를 약제부와 맞춰야 한다"
how_to_apply: "필터 바텀시트의 병동 그룹을 '전체 / 대분류(체크 = 하위 전체) / 펼쳐서 중분류'로 만든다. '기타·미분류'는 기본으로 포함한다. 시트 하단 버튼에 결과 건수를 표시한다('결과 42건 보기')"
confidence: 0.55
limitations: "외래·소규모 병원 대상 제품이다. 기능 서술만 있고 사용성 평가는 없다"
```

```yaml
id: REF-204
type: 패턴
title: "STAT 존재를 큐 진입점 배지에 표시(건수 배지 + '!'), STAT/ASAP을 목록 최상단에"
source: "CPSI(Evident) 2105 Verify Orders Queue https://userareas.cpsi.com/userareas/files/releasenotes/2105_Verify_Orders_Queue.pdf ; Ontada Orders Queue Update https://guide.ontada.com/wp-content/uploads/2025/09/Orders-Queue-Update-–-Ontada-Guide.pdf — WebSearch 발췌"
designer_or_org: "CPSI/Evident, Ontada(iKnowMed)"
problem_it_solves: "다른 화면에서 일하는 중에 긴급 처방이 생겼다는 사실을 알기"
applies_to: [긴급 큐, 목록, R-006, F03]
evidence: "Order Verify 아이콘에 미검증 처방 건수 배지가 붙고, STAT 처방이 있으면 느낌표를 표시한다. 기본 필터는 Admitted이고, 입원 상태 필터를 하나 이상 골라야 처방이 표시된다(CPSI, 간호 검증 큐). Ontada는 STAT/ASAP을 가운데 열 최상단에 두고 나머지는 날짜순으로 둔다"
why_needed: "m2-traceability F03 '정규 작업 중 긴급 알림 없음'의 직접 해법이다. 팝업이 아니라 **진입점 배지**라서 경고 피로(a3 C3)를 키우지 않는다. 'STAT 상단 고정'은 a3 C10(특허)과 같은 방향이어서 근거가 두 개로 늘었다"
cost: "실시간 건수 갱신(폴링·푸시)이 필요하다 ⚑ PM 확인 필요(연동 공수). 배지가 항상 숫자를 보이면 무뎌진다"
how_to_apply: "상단 탭·필터 칩의 '긴급'에 미처리 건수를 표시하고, 기준 시간을 넘긴 건이 있을 때만 강조 형태(아이콘 + 강조색)로 바꾼다. 긴급 큐 목록은 미처리 → 오래된 순을 기본으로 한다"
confidence: 0.45
limitations: "CPSI 자료는 간호 검증 큐이고, 약사 큐가 아니다. 두 제품 모두 사용성 근거는 없다"
```

```yaml
id: REF-205
type: 패턴
title: "Sentri7(Wolters Kluwer): 개입 필요도로 환자 우선순위, 규칙 기반 뷰(예: INR 임계값), PRN 숨기기"
source: "Wolters Kluwer expert insights https://www.wolterskluwer.com/en/expert-insights/harnessing-ehr-data-to-deliver-insights-into-a-pharmacy-tailored-workflows ; Drug Topics https://www.drugtopics.com/view/new-software-streamlines-patient-profile-review ; STM Publishing https://www.stm-publishing.com/?p=8201 — WebSearch 발췌"
designer_or_org: "Wolters Kluwer(PharmacyOneSource)"
problem_it_solves: "임상 우선순위가 높은 환자부터 보기"
applies_to: [목록, 필터]
evidence: "**벤더 주장**: 규칙 로직으로 EHR 데이터를 모아 상세 관리가 필요한 환자를 우선 표시하고, 중증도·치료 영역별로 볼 수 있다. 규칙은 병원 기준으로 조정할 수 있다(예: INR 임계값 미만 제외). PRN 처방을 워크플로에서 숨기는 필터를 추가했다"
why_needed: "ePRIS에서 'PRN·Dr.확인후'(R-044)가 일반 처방과 같은 목록에 섞이면 훑기 부담이 커진다. 'PRN 숨기기'는 그 대응 사례다. 다만 ePRIS는 CDS 규칙 엔진이 범위 밖이므로 **우선순위 자동 산출은 가져오지 않는다**"
cost: "숨김 필터를 쓰면 숨겨진 건수를 보여 줘야 누락이 생기지 않는다(a3 A7과 같은 원리)"
how_to_apply: "필터로 숨긴 처방이 있으면 목록 상단에 'PRN 12건 숨김 · 보기' 줄을 둔다"
confidence: 0.35
limitations: "마케팅 문서다. 화면 확인 없음. 임상 약사 라운딩용이라 조제 감사와 업무가 다르다"
```

```yaml
id: REF-206
type: 근거
title: "TPN 계산 소프트웨어(Abacus): 약사 확인 2회 구조 + 'Summary'로 계산값 대조, 2014 Class I 리콜"
source: "Baxter Abacus 브로셔 https://ushospitalproducts.baxter.com/sites/g/files/ebysai2186/files/2020-06/Abacus%20Software%20Product%20Brochure.pdf ; MDedge 리콜 기사 https://mdedge.com/content/tpn-calculation-software-recalled ; Pharmacy Times 2006 https://www.pharmacytimes.com/view/2006-10-5954 — WebSearch 발췌"
designer_or_org: "Baxter, FDA 리콜 보도"
problem_it_solves: "계산된 조제량이 처방과 맞는지 약사가 확인하기"
applies_to: [처방전 뷰(TPN), 하단 조작 영역]
evidence: "흐름: 처방 입력 → 약사 확인 → 라벨 출력·조제 → 최종 약사 확인. 권한 있는 사용자만 승인한다. 환자 유형별 경고 한계를 설정한다. 2014년 v2.0~3.1 Class I 리콜(전해질 계산량이 기대값의 2배가 되는 오류 등). Baxter는 완료 전 'Summary' 버튼으로 처방과 계산량을 대조하라고 안내했다"
why_needed: "TPN조제 약사가 주 사용자다. 리콜 대응이 '요약 화면에서 처방값과 계산값을 나란히 대조하라'였다는 점은, 감사 저장 직전에 **대조 가능한 요약**이 필요하다는 도메인 근거다. 10/21 요구의 'TPN bag'(재요구) 관련 화면 설계에 쓴다"
cost: "TPN 전용 요약 뷰가 추가된다 ⚑ PM 확인 필요. 계산값 출처(HIS·조제기)를 연동해야 할 수 있다"
how_to_apply: "TPN 처방전 뷰에서 성분 행마다 '처방량 | 계산(조제)량 | 차이'를 같은 행에 둔다. 차이가 있는 행만 강조한다. 데이터가 없으면 이 카드는 보류한다"
confidence: 0.45
limitations: "리콜 사유와 대응은 2차 보도다. 화면 설계 근거가 아니라 사고 대응 사례다. 원인이 계산 로직이므로 UI만으로 막을 수 있는 오류는 아니다"
```

```yaml
id: REF-207
type: 근거
title: "항암 조제 워크플로 소프트웨어(BD Cato 등): 약사 검증 → 단계별 화면 지시 → 중량 확인 → 하드 스톱"
source: "Meren & Waterson, JMIR Hum Factors 2021;8(4):e29180 (PMC8596227) https://humanfactors.jmir.org/2021/4/e29180 ; BD AJHP 재인쇄(MD Anderson) https://www.bd.com/content/dam/bd-assets/na/medication-management-solutions/documents/journal-article/MMS_AJHP_ImpementationEvaluationGravimetricWorkflowInOncologyAmbulatoryCarePharmacy_BR_EN.pdf ; Drug Topics https://drugtopics.com/iv-compounding-software-reduces-risk-med-errors — WebSearch 발췌"
designer_or_org: "BD(벤더), MD Anderson 구현 연구, 영국 구현 연구"
problem_it_solves: "항암 조제의 단계별 오류 차단"
applies_to: [하단 조작 영역, 처방전 뷰(항암)]
evidence: "MD Anderson 2016: 약사 처방 검증, 중량 확인, 작업대의 단계별 화면 지시. 11,874건 중 허용 오차(<4%) 이탈 797건을 최종 백 주입 전에 잡았다. 15,843 dose 중 1,126건(7%)을 소프트웨어가 탐지했다. BD는 오류를 고칠 때까지 진행을 막는 하드 스톱을 쓴다(**벤더 서술**). Meren & Waterson 2021: 처방·조제·투여 소프트웨어 추가로 단계별 탐지가 늘었다고 결론(구현 연구, 대조군 없음)"
why_needed: "ePRIS는 조제 기기 연동이 아니지만, '항암제조제2' 약사의 감사 화면은 이 하류 공정의 **입구**다. 하드 스톱과 소프트 경고의 구분은 하단 조작 영역에서 '저장을 막을지, 확인만 받을지'를 정할 때 참고 기준이 된다"
cost: "하드 스톱을 늘리면 우회 행동이 생긴다(a3 C5). 막을 조건을 약제부가 정해야 한다"
how_to_apply: "막는 조건은 '필수 데이터 누락(예: BSA 없는 항암 처방)'처럼 객관적인 것만 둔다. 나머지는 행 내 경고로 둔다(M6에서 조건 목록화)"
confidence: 0.4
limitations: "BD가 배포한 단일 기관 수치다. 탐지 건수는 '소프트웨어가 없었으면 오류였을 것'을 뜻하지 않는다. 화면 레이아웃 정보는 없다"
```

#### 1-B. 환자 헤더·약물 표기 (가이드·연구)

```yaml
id: REF-208
type: 원칙
title: "호주 ACSQHC '화면 의약품 정보 표시 국가 지침'(2016·2017): 약어 금지, 혼동 이름 Tall Man, 숫자·단위 규칙"
source: "2017판 https://safetyandquality.gov.au/sites/default/files/migrated/National-guidelines-for-on-screen-display-of-medicines-information.pdf ; 2016판 https://www.safetyandquality.gov.au/sites/default/files/migrated/National-guidelines-for-onscreen-display-of-clinical-medicines-information.pdf ; 부분 과업분석·휴리스틱 평가 보고서 2015 — WebSearch 발췌(WebFetch DNS 실패)"
designer_or_org: "Australian Commission on Safety and Quality in Health Care (2017판은 AHMAC 승인)"
problem_it_solves: "화면에서 약 이름·용량·단위를 잘못 읽는 오류"
applies_to: [처방전 뷰, 목록, 긴급 큐 상세]
evidence: "'Do not use abbreviations. Display prescription details in full.' 약 이름과 숫자·단위 측정에 별도 장이 있다. 혼동이 알려진 이름에 국가 Tall Man 목록을 쓴다. 2015 보고서는 처방 요소 순서를 여러 방식으로 시험했다(예: 약명 → 제형 → 경로 → 용량 → 빈도 → 공급량)"
why_needed: "현재 화면 표기 규칙(약어·단위·소수점)을 정한 근거 문서가 ePRIS에 없다. 국가 수준에서 화면 표기만 다룬 지침은 이것이 가장 가깝다(ISMP 전자 지침은 REF-209)"
cost: "약어를 풀어 쓰면 열 폭이 늘어 태블릿 가로 스크롤이 커진다. 약사는 'PO·IV·BID' 같은 약어에 익숙하다. 원칙 3(종이 처방전 용어 유지)과 충돌하므로 **경로·빈도 약어는 유지**하고 숫자·단위 규칙만 가져오는 절충이 현실적이다"
how_to_apply: "M6 표기 규칙 1장: 숫자·단위·소수점 규칙은 채택하고, 경로·빈도 약어는 현행 유지(종이 처방전 기준)로 하되 ISMP 금지 약어(REF-209)만 치환한다"
confidence: 0.5
limitations: "원문을 열지 못했다. 환자 배너 관련 조항 문구와 숫자 규칙 세부 문구는 확인하지 못했다. 호주 지침이라 국내 표기 관행(KIMS 약품명 등)과 다를 수 있다"
```

```yaml
id: REF-209
type: 원칙
title: "ISMP 전자 의약품 정보 지침 + 오류 유발 표기 목록: 후행 0 금지, 선행 0 필수, 숫자와 단위 사이 띄어쓰기, 1,000 이상 쉼표"
source: "ISMP Guidelines for Safe Electronic Communication of Medication Information https://online.ecri.org/hubfs/ISMP/Resources/ISMP_Electronic_Guidelines.pdf ; 오류 유발 표기 표(escholarship 재수록) https://escholarship.org/content/qt75z671jb/table3.htm ; FDA 동물의약품 리터러시(후행·선행 0 사례) https://www.fda.gov/animal-veterinary/animal-health-literacy/all-creatures-great-and-small-properly-medicate-them-all ; NZ HQSC 포스터 https://www.hqsc.govt.nz/assets/Medication-Safety/Alerts-PR/Poster-error-prone-abbreviations-not-to-use.pdf — WebSearch 발췌"
designer_or_org: "ISMP, FDA, NZ HQSC"
problem_it_solves: "10배 용량 오독(5.0 mg → 50 mg, .5 mg → 5 mg, 10mg의 m을 0으로 오독)"
applies_to: [처방전 뷰, 목록(투여량 컬럼, R-021·10/21 '투여량 tooltip → 컬럼'), 긴급 큐 상세]
evidence: "후행 0은 처방·의약품 문서에서 금지('5.0 mg'은 '50 mg'으로 오독). 선행 0은 필수('.5 mg' → '0.5 mg'). 가능하면 더 작은 단위로 바꾼다(0.5 mg → 500 micrograms). 숫자와 단위 사이에 충분한 공간을 둔다. 1,000 이상은 쉼표를 쓴다. ISMP 전자 지침은 일반명을 소문자로 쓰고(Tall Man 제외), 염 표기를 생략하고, 약품명 약어를 피하라고 권한다. ISMP는 금지 약어를 라벨과 조제 시스템을 포함한 모든 커뮤니케이션에 적용한다고 밝힌다"
why_needed: "10/21 요구로 투여량이 툴팁에서 **컬럼**으로 올라온다. 투여량 숫자가 고밀도 표에서 상시 노출되므로 숫자 렌더링 규칙이 필요하다. 소수점 오독은 10배 오류로 이어진다(제품 원칙 1)"
cost: "HIS에서 받은 값을 표시용으로 바꾸면 '원본과 다르다'는 혼란이 생길 수 있다. 변환 규칙은 개발팀·약제부 합의가 필요하다 ⚑ PM 확인 필요. 단위 변환(mg → microgram)은 원본 데이터 변경이라 **가져오지 않는다**"
how_to_apply: "표시 계층에서만 (1) 후행 0 제거, (2) 선행 0 보장, (3) 숫자–단위 사이 공백, (4) 천 단위 쉼표를 적용한다. 투여량 열은 숫자를 오른쪽 정렬하거나 소수점 정렬하고, 탭룰러 숫자(tabular figures)를 쓴다(숫자 정렬은 디자인 추론)"
confidence: 0.6
limitations: "ISMP 원문을 열지 못했고, 띄어쓰기·쉼표 항목은 학술 재수록 표에서 확인했다. 전자 지침의 '화면 잘림(truncation)' 조항은 확인하지 못했다. 효과를 측정한 연구는 없고 사례·전문가 합의 기반이다"
```

```yaml
id: REF-210
type: 원칙
title: "NHS CUI(ISB 1500~1508): 환자 배너(ISB 1505), NHS 번호 표시(ISB 1504), 투약 행 순서 — 현재 '폐기'"
source: "NHS Digital ISB 1500-1508 공지 https://digital.nhs.uk/data-and-information/information-standards/governance/latest-activity/standards-and-collections/isb-1500-1508-common-user-interface ; NHS Data Dictionary 생년월일 https://archive.datadictionary.nhs.uk/DD%20Release%20May%202018/data_dictionary/data_field_notes/d/date_of_birth_(patient_identification)_de.asp@shownav=0.html ; NHS Digital dose-to-text https://simplifier.net/guide/ukcoreimplementationguideformedicines/DosetoTextTranslation — WebSearch 발췌"
designer_or_org: "NHS Connecting for Health / NHS Digital"
problem_it_solves: "환자 식별 정보와 투약 행의 일관된 배치·형식"
applies_to: [목록(환자 카드 헤더), 긴급 큐 상세 헤더, 처방전 뷰]
evidence: "NHS Digital은 CUI 표준(환자 배너 포함)이 'out of date'이며 인터페이스 설계 표준으로 의존하지 말라고 공지하고, 환자 안전 관련 요소는 검토하겠다고 밝혔다. 생년월일 표시는 DD-Mmm-CCYY(CUI 날짜 표준). Dose-to-text 지침: 약명을 굵게, 순서는 약명 → 제형 → 상품명 → 방법·용량·속도·기간·빈도·시점·경로, 단위는 풀어 쓴다(실험적 지침)"
why_needed: "환자 카드 헤더의 식별 정보(이름·등록번호·성별/나이)를 '항상 같은 위치, 같은 형식'으로 두는 원칙의 출처다. **약명 굵게**는 처방 행에서 시선의 닻(anchor)을 주는 저비용 규칙이다"
cost: "폐기된 표준이라 그대로 인용하면 근거가 약하다. 투약 행 순서를 NHS식으로 바꾸면 종이 처방전 열 순서(원칙 3)와 충돌하므로 **순서는 가져오지 않는다**"
how_to_apply: "식별 정보는 카드 헤더 좌측 고정 위치·고정 순서(이름 마스킹 규칙 포함)로 둔다. 약명만 굵게(또는 한 단계 높은 굵기) 하고, 열 순서는 종이 처방전을 유지한다"
confidence: 0.4
limitations: "CUI 원문을 보지 못했다. 성(姓) 대문자, NHS 번호 3-3-4 그룹 같은 세부 규칙은 확인하지 못했다(기억으로 채우지 않음)"
```

```yaml
id: REF-211
type: 근거
title: "환자 사진을 배너에 상시 표시하면 잘못된 환자 처방이 줄었다(관찰 연구) — '수동적 식별 단서'가 팝업 없이 작동"
source: "Salmasian et al., JAMA Netw Open 2020 (PMC7658731) https://pmc.ncbi.nlm.nih.gov/articles/PMC7658731 ; AHRQ 요약 https://digital.ahrq.gov/program-overview/research-stories/displaying-patient-photos-medical-records-reduces-errors-improves ; RCT 등록 NCT03626766 — WebSearch 발췌"
designer_or_org: "Brigham and Women's 등(Salmasian), AHRQ 지원 연구(Adelman)"
problem_it_solves: "목록에서 비슷한 환자를 혼동해 다른 환자 처방을 처리"
applies_to: [목록(환자 카드 헤더), 긴급 큐(좌 목록 → 우 상세 전환)]
evidence: "응급실 약 72,000명, 약 256만 건 처방. 배너에 사진이 있을 때 잘못된 환자 처방 비율이 낮았다(OR 0.72 비보정, 0.57 보정). 저자는 추가 시간 부담과 경고 피로 위험이 없다고 언급했다. 연구 시작 시 사진 보유율은 약 40%였다. 2013 설문에서 사진 표시 기능이 있는 병원 중 실제 사용은 17.6%"
why_needed: "ePRIS는 여러 환자를 한 화면에 쌓는 통합 목록이다(R-019). 국내 응급실 연구(a3 C9)에서도 **환자 선택 단계**가 사용성 문제 1위였다. 이 연구의 요점은 사진 자체보다 '확인 팝업 대신 상시 보이는 식별 단서'다. 긴급 큐에서 좌측 선택이 우측 상세와 같은 환자인지 확인하는 단서 설계에 쓴다"
cost: "사진 연동은 개인정보·연동 공수 문제로 **가져오지 않는다**. 대신 헤더 식별 정보의 시각 강도를 올리면 헤더 높이가 늘어난다"
how_to_apply: "긴급 큐 우측 상세 상단에 좌측 선택 행과 같은 식별 3요소(이름 마스킹·등록번호·병동/병상)를 같은 형식으로 고정한다. 목록에서 환자 카드 경계를 강하게(카드 간 간격 + 헤더 배경) 둔다"
confidence: 0.55
limitations: "관찰(QI) 데이터라 인과를 확정할 수 없다. 응급실 처방의(입력자) 대상이고, 약사 검토자 대상이 아니다. RCT 결과는 이번 검색에서 확인하지 못했다"
```

```yaml
id: REF-212
type: 패턴
title: "Epic Storyboard: 가로 환자 헤더를 좌측 세로 사이드바로 이동, 역할별 내용, 알레르기 '평가 불가'는 빨강"
source: "Premier Health https://premierhealth.com/your-health/articles/premier-pulse/epic-is-updating-its-user-experience-with-storyboard ; UNC Health https://news.unchealthcare.org/2020/01/preview-new-view-for-epic-unc-patient-header-storyboard-in-the-epic-unc-playground ; UF Health https://news-notes.ufhealth.org/2019/09/17/epic-changes-on-the-horizon/ ; Houston Methodist 2021 업데이트 PDF — WebSearch 발췌"
designer_or_org: "Epic (병원 롤아웃 공지 경유)"
problem_it_solves: "와이드스크린에서 환자 맥락 정보를 늘 보이게 하면서 본문 세로 공간을 확보"
applies_to: [긴급 큐 상세, 처방전 뷰, R-020, R-031]
evidence: "헤더 내용을 읽기 쉬운 사이드바로 옮겼다(Premier). 역할마다 다른 뷰를 준다(외래: 지난 방문·케어 갭 / 입원: 새 결과·약·활력징후). UNC는 2020년 1월 헤더를 화면 왼쪽으로 옮겼고, 클릭 감소와 와이드스크린 활용을 이유로 들었다. 알레르기 'Unable to Assess'는 빨강 강조. 체중 표시 위치는 확인하지 못했다"
why_needed: "ePRIS도 약국마다 판단 수치가 다르다(입원: 체중·Scr/CrCl·진단 / 항암: 키·체중·BSA·WBC·ANC / TPN: 별도). '역할별 헤더 내용'은 약국별 카드 헤더 구성의 선례다. 가로 태블릿에서 세로 공간이 부족한 문제(가로 스크롤 테이블)에 '측면 고정 헤더' 대안을 준다"
cost: "목록 화면(여러 환자)에는 맞지 않는다. 한 환자를 보는 화면(긴급 상세·처방전 뷰)에만 해당한다. 사이드바가 테이블 폭을 줄여 가로 스크롤이 늘어난다"
how_to_apply: "처방전 뷰(환자 1명)에서만 '좌측 환자 패널(접기 가능 · 기본 펼침)' 대안을 M4에 넣는다. 패널 내용은 약국별로 다르게 구성한다"
confidence: 0.45
limitations: "병원 공지 수준이고 Epic 공식 디자인 근거가 아니다. 사용성 측정 결과는 없다"
```

```yaml
id: REF-213
type: 패턴
title: "SAP Fiori 동적 페이지 헤더: 접어도 제목과 '핵심 정보'는 남고, 접기/고정(pin) 표시 필수"
source: "Page header usage https://www.sap.com/design-system/fiori-design-web/v1-148/page-types/page-layouts/page-header/usage ; Dynamic page layout https://experience.sap.com/fiori-design-web/v1-74/dynamic-page-layout — WebSearch 발췌"
designer_or_org: "SAP Fiori"
problem_it_solves: "헤더를 접어 공간을 확보할 때 판단에 필요한 정보까지 사라지는 문제"
applies_to: [목록(환자 카드 접기), 처방전 뷰, R-020, F07, N9]
evidence: "핵심 정보(태그·KPI)는 헤더 가운데 영역에 두고 가능한 한 오래 보이게 한다. 헤더가 접히면 header content는 숨지만 제목은 남는다(펼침은 줄바꿈, 접힘은 말줄임). 접기·고정 컨트롤은 header content 하단에 두고, 접을 수 있으면 시각 표시가 필수다. 공간이 부족하면 액션이 제목보다 먼저 오버플로로 간다"
why_needed: "현 설계는 환자 카드를 **접으면 판단 수치가 사라진다**(F07, N9). Fiori는 '접힘 상태에도 남는 최소 집합'을 별도로 정의한다. 체중·CrCl 같은 판단 수치를 접힘 상태에도 남기는 근거다"
cost: "접힘 상태 레이아웃이 하나 더 생긴다. 어떤 수치를 '핵심'으로 둘지 약국별로 약사 확인이 필요하다"
how_to_apply: "환자 카드 접힘 상태 = 식별 3요소 + 약국별 핵심 수치 2~3개(예: 입원 체중·CrCl / 항암 BSA·ANC) + v1의 집약 상태 배지. 전체 접기/펼치기는 목록 상단에 두고 상태를 기억한다"
confidence: 0.55
limitations: "데스크톱 웹 지침이다. 태블릿 카드 목록에 그대로 적용하는 것은 유추다"
```

```yaml
id: REF-214
type: 근거
title: "검증에 필요한 환자 데이터(신기능·체중·검사값)가 바로 보이지 않으면 약사 검토가 느려지고 용량 오류가 남는다"
source: "Goldberg et al. 신기능 기반 용량 조정 프로그램(UMN) https://experts.umn.edu/en/publications/computer-based-program-for-identifying-medication-orders-requirin/ ; JAMIA 2009 반코마이신·아미노글리코시드 표 https://pmc.ncbi.nlm.nih.gov/articles/PMC2605596/table/tbl4 ; CJHP 2011 약사 처방 검토 체크리스트 https://pmc.ncbi.nlm.nih.gov/articles/PMC3130755/table/t1-cjhp-64-3-199 ; Sellier JAMIA 2009 — WebSearch 발췌"
designer_or_org: "학술 연구(미국·캐나다·프랑스)"
problem_it_solves: "용량 판단 근거가 다른 화면에 있어 생기는 지연·누락"
applies_to: [목록(환자 카드 헤더), 처방전 뷰, R-020, R-031]
evidence: "Goldberg: 약국 시스템이 검사 시스템에서 크레아티닌·청소율을 받아 계산하고 조정이 필요한 처방을 알렸다. 저자는 이전에는 '환자 데이터를 바로 볼 수 없어서' 약사가 처방을 빠르게 평가할 수 없었다고 썼다. JAMIA 2009 표: 키·체중 전자 입력률 63% → 96%, 용량 오류 32% → 7%(중재 묶음 효과). CJHP 체크리스트는 검사값(SCr, K), 체중·신기능·간기능 기반 용량을 검토 항목으로 둔다"
why_needed: "R-020(입원 판단 수치)과 R-031(항암 키/체중/BSA, WBC/ANC)이 **카드에 상시 보여야 하는 이유**다. 카드를 접으면 수치가 사라지는 현 설계(F07)의 위험을 뒷받침한다"
cost: "수치가 늘면 카드 헤더가 커진다. 검사 시각(언제 값인지)도 함께 보여야 해서 정보가 더 늘어난다"
how_to_apply: "판단 수치는 '값 + 측정일(상대 시간)'로 표시한다. 기준을 벗어나면 v1의 드문 상태 규칙(소면적 고채도 + 라벨)을 따른다. 수치 기준(정상 범위)은 약제부가 정한다"
confidence: 0.45
limitations: "오래된 연구(1990년대~2009)다. JAMIA 2009 수치는 여러 중재를 묶은 효과라 '표시'만의 효과가 아니다. 2020 JAMIA(27(2):284) 검증 시간 연구는 주 가설이 지지되지 않았다고 발췌됐다"
```

```yaml
id: REF-215
type: 근거
title: "Tall Man 표기의 실제 효과는 불분명하다: 42개 병원 9년 데이터에서 측정 가능한 효과 없음"
source: "Zhong et al. BMJ Qual Saf 2016;25(4):213 https://qualitysafety.bmj.com/content/25/4/213 ; 체계적 문헌고찰 2018 (PMC6061459) https://www.ncbi.nlm.nih.gov/pmc/articles/PMC6061459/ ; Bhat & Gutzwiller(HFES) ; Patient Safety Solutions 2015 — WebSearch 발췌"
designer_or_org: "Zhong 등(미국 소아병원), 체계적 문헌고찰 저자들"
problem_it_solves: "a3 C6(Tall Man 권장)의 근거 수준 갱신"
applies_to: [처방전 뷰, 목록(약품명 열)]
evidence: "42개 소아병원, 2004~2012, 약 160만 건 처방에서 약명 혼동 비율에 측정 가능한 효과 없음. 다만 각 병원이 언제 어떤 쌍에 도입했는지 알 수 없다는 한계(BMJ QS 논평). 2018 고찰 16편 중 13편이 실험실 연구이고 가독성 개선을 보였다. 2020 고찰은 '미미하게 효과적'. Bhat & Gutzwiller: 사용자 배경·약 친숙도·철자 유사성·위치·노출 시간에 따라 다르다"
why_needed: "a3 패턴 #9(Tall Man 적용)의 근거 수준을 정직하게 낮춘다. Tall Man은 **비용이 낮을 때만** 채택할 가치가 있다. 약품명이 KIMS 연동이라 표기를 바꾸는 비용이 높다면 우선순위를 내린다"
cost: "KIMS·HIS 약품명을 화면에서 변환하려면 대조 목록 관리가 필요하다(한글 약품명에는 적용 방식이 불분명)"
how_to_apply: "원내 처방 시스템이 이미 Tall Man을 쓰면 그대로 표시만 한다. 쓰지 않으면 ePRIS가 독자 도입하지 않는다(가설, 약제부 확인)"
confidence: 0.6
limitations: "Zhong은 관찰 연구이고 도입 시점 정보가 없다. 실험실 연구는 실제 업무 환경과 다르다. 한글 약품명에 관한 연구는 찾지 못했다"
```

```yaml
id: REF-216
type: 근거
title: "eMAR 표시 설계: 휴리스틱 평가 60개 문제(일치·오류·가시성 최다), ISMP Canada는 eMAR 표시를 사고 기여 요인으로 판단"
source: "Appl Clin Inform 2011 (DOI 10.4338/ACI-2011-01-RA-0004) https://www.thieme-connect.com/products/all/doi/10.4338/ACI-2011-01-RA-0004 ; ISMP Canada Safety Bulletin 2018 i8 https://www.ismp-canada.org/download/safetyBulletins/2018/ISMPCSB2018-i8-eMAR.pdf ; ACI 2014 노인요양 eMAR ; 체계적 고찰 ACI 2023 (10.1055/s-0043-1761435) — WebSearch 발췌"
designer_or_org: "학술(ACI), ISMP Canada"
problem_it_solves: "투약 목록 화면에서 핵심 요소가 묻히는 문제"
applies_to: [처방전 뷰, 목록, 긴급 큐 상세]
evidence: "평가자 4명, 과업 7개로 상용 eMAR를 평가해 60개 문제, 233개 위반을 찾았다. 일치(match)·오류·가시성 위반이 가장 많았고, 투약과 처방 변경 과업에 심각한 문제가 몰렸다. ISMP Canada: 약명·함량·용량·경로·빈도 같은 핵심 요소가 명확해야 하며, 한 사건에서 eMAR 설계가 중요한 기여 요인이었다. 요양 eMAR 연구는 '정보 배치와 의미'를 설계 과제 5개 중 하나로 꼽았다"
why_needed: "약사 감사 화면도 같은 '투약 행 목록'이다. 핵심 5요소(약명·함량·용량·경로·빈도)를 다른 정보보다 위계 위로 두는 근거다"
cost: "핵심 5요소를 강조하면 나머지 열(발행처·묶음 등)은 상대적으로 흐려진다. 약사가 그 열을 자주 본다면 불편해진다"
how_to_apply: "처방 행에서 핵심 5요소는 본문 색·기본 굵기, 보조 열은 보조 텍스트 색으로 둔다(크롬은 낮추고 데이터는 높이는 a3 #12와 같은 방향). 보조 열 목록은 약사 관찰로 확정한다"
confidence: 0.55
limitations: "간호 투약 기록 대상이다. 약사 감사 화면에 대한 직접 연구는 아니다. ISMP Canada 사례는 단일 사건 분석이다"
```

```yaml
id: REF-217
type: 근거
title: "고밀도 표의 줄무늬(zebra) 효과는 작다. 가로 스크롤·넓은 표에서는 더 클 수 있다(저자 가설)"
source: "Enders, 'Zebra Striping: Does it Really Help?' A List Apart 2008 https://alistapart.com/article/zebrastripingdoesithelp/ ; konigi 비판 https://konigi.com/blog/zebra-striping-does-it-really-help ; Tufte 노트 https://www.edwardtufte.com/notebook/zebra-tables-and-lists/ — WebSearch 발췌"
designer_or_org: "Jessica Enders, Michael Angeles, Edward Tufte"
problem_it_solves: "가로로 긴 표에서 행을 따라가다 다른 행으로 넘어가는 오류"
applies_to: [목록(약품 테이블), 처방전 뷰]
evidence: "참가자 244명, 질문 6개. 줄무늬 표의 정확도·속도가 약간 높았지만 차이는 작았다. 저자: 열 사이 간격이 넓거나 가로 스크롤이 필요하면 효과가 더 클 수 있다. 일부 참가자는 손가락으로 행을 따라갔다고 자발적으로 보고했다. 비판: 테두리와 배경을 함께 쓴 구현이라 비교가 불공정. 대안: 잘 설계된 표는 옅은 가로선만으로 충분하다"
why_needed: "ePRIS 약품 테이블은 가로 스크롤이 있는 넓은 표다(저자가 효과가 더 클 수 있다고 본 조건). 동시에 v1은 **행 배경을 드문 상태 표시에 쓰기로** 했다. 줄무늬 배경을 쓰면 상태 배경과 충돌한다"
cost: "줄무늬를 쓰면 v1 상태 배경과 섞여 '이 회색은 상태인가 줄무늬인가'라는 혼동이 생긴다. 그래서 **줄무늬는 채택하지 않는다**"
how_to_apply: "행 구분은 옅은 가로선(1px)과 충분한 행 높이로 처리한다. 가로 스크롤 시 약품명 열을 고정(sticky)해 행을 따라가는 기준점을 남긴다. 탭한 행은 일시 하이라이트한다(태블릿의 '손가락으로 따라가기' 대체)"
confidence: 0.45
limitations: "단일 온라인 실험이고 동료 심사 여부를 확인하지 못했다. 데스크톱 대상이다"
```

#### 1-C. 태블릿 레이아웃·인터랙션

```yaml
id: REF-218
type: 원칙
title: "목록-상세 / 보조 패널 정준 레이아웃(Material·Android), iPad 사이드바·분할 뷰(Apple HIG)"
source: "Android Canonical layouts https://developer.android.com/develop/ui/compose/layouts/adaptive/canonical-layouts ; Apple HIG Sidebars https://developer-mdn.apple.com/design/human-interface-guidelines/components/navigation-and-search/sidebars — WebSearch 발췌"
designer_or_org: "Google(Material 기반), Apple"
problem_it_solves: "가로 태블릿에서 목록을 잃지 않고 상세를 보는 구조"
applies_to: [긴급 큐, 처방전 뷰]
evidence: "목록-상세: 창을 두 창으로 나누고 목록에서 고르면 상세가 뜬다. 보조 패널은 주 콘텐츠와 관계가 있을 때만 의미가 있다(목록-상세의 상세는 독립적). 확장 폭 가로에서 보조 패널이 잘 맞고, 좁으면 아래나 바텀시트로 옮긴다. 중간 폭은 반반, 확장 폭은 약 70:30(중국어 번역 페이지 수치, 영문 미확인). Apple: 사이드바는 기본으로 숨기지 말 것, 계층은 2단 이하"
why_needed: "긴급 큐는 이미 좌 목록/우 상세 구조다. '상세가 독립적인가(목록-상세) vs 목록 맥락에 붙은 보조 정보인가(보조 패널)'라는 구분으로 우측 폭과 동작을 정할 수 있다. 긴급 300건(R-043)을 훑을 때 좌측 목록 폭을 지키는 근거가 된다"
cost: "좌측 폭을 줄이면 목록 열이 줄어 판단 정보(약명·병동)가 잘린다. 폭 비율은 실기기에서 확인해야 한다"
how_to_apply: "긴급 큐: 좌 목록은 '병동·환자 식별·약명·시각·상태' 5열로 제한하고, 우 상세는 처방전 단위로 둔다. 상세에서 처리(감사 저장)하면 다음 미처리 건으로 자동 이동한다(R의 '긴급 자동 다음'). 이동 후에도 좌측 목록 스크롤 위치를 유지한다"
confidence: 0.6
limitations: "공식 문서의 검색 발췌다. 70:30 비율은 영문 원문에서 확인하지 못했다"
```

```yaml
id: REF-219
type: 패턴
title: "필터 시트: 모바일은 모달 바텀시트, 태블릿·대화면은 '표준(비모달) 사이드 시트'"
source: "Material Side sheets https://material.io/components/sheets-side ; Material Bottom sheets https://material.io/components/sheets-bottom ; MDC Android 1.8.0 https://material.io/blog/android-stable-release-1-8-0 ; SAP Fiori Android Bottom Sheet https://www.sap.com/design-system/fiori-design-android/v26-4/components/system-components/bottom-sheet/usage ; BrightHR Filtering https://ui-docs.bright.hr/docs/design-patterns/Filtering — WebSearch 발췌"
designer_or_org: "Google Material, SAP Fiori for Android, BrightHR"
problem_it_solves: "필터를 바꾸는 동안 결과 목록이 가려지는 문제"
applies_to: [필터, R-004, R-044, R-045, R-069]
evidence: "표준 시트는 주 콘텐츠 작업 중에도 보이고, 모달 시트는 닫아야 아래를 쓸 수 있다. 사이드 시트는 주로 태블릿·데스크톱에 쓰고(베타 지침), 표준·coplanar 사이드 시트는 대화면에 적합하며 작은 화면에는 권하지 않는다(MDC 1.8.0). 필터는 짧고 집중된 과업이라 시트에 맞다. 한 범주의 다중 선택은 값이 7개 이하일 때 바텀시트(BrightHR). SAP는 복잡한 정보에는 바텀시트를 쓰지 말라고 한다"
why_needed: "현 설계는 필터가 바텀시트다. 가로 태블릿에서 모달 바텀시트는 목록을 가려서 '이 조합이면 몇 건인지'를 볼 수 없다. 병동 중분류 복수 선택(R-069)으로 항목이 늘면 7개 한도를 넘는다(SAP·BrightHR 기준으로는 바텀시트가 부적합)"
cost: "사이드 시트로 바꾸면 화면설계서 v1.1 구조가 바뀐다 ⚑ PM 확인 필요. 약사가 이미 본 시안과 다르다. 사이드 시트 표시 중에는 테이블 폭이 줄어든다"
how_to_apply: "안 A(변경 작음): 바텀시트 유지 + 하단 버튼에 결과 건수 표시 + 적용된 필터를 목록 상단 칩으로 노출(a3 #13). 안 B: 가로 모드에서만 우측 표준 사이드 시트로 바꾸고 결과가 실시간으로 갱신된다. M4에서 두 안을 비교한다"
confidence: 0.5
limitations: "사이드 시트 지침은 베타다. NN/g 출처는 찾지 못했다. '7개 한도'는 한 회사 가이드다"
```

```yaml
id: REF-220
type: 근거
title: "태블릿을 잡는 방식은 자세에 따라 다르다. 주요 콘텐츠는 가운데, 보조 액션은 가장자리"
source: "Hoober & Shank, 'Making mLearning Usable: How We Use Mobile Devices' https://www.learningguild.com/research/making-mlearning-usable-how-we-use-mobile-devices ; A List Apart 태블릿 영역 도해 https://alistapart.com/1-9-tablet-zones-jpg/ ; UX Planet 요약 — WebSearch 발췌"
designer_or_org: "Steven Hoober, Patti Shank"
problem_it_solves: "하단 조작 영역과 주요 버튼의 위치"
applies_to: [하단 조작 영역, 메모]
evidence: "태블릿 사용의 88%가 앉은 자세(폰은 19%). 앉으면 한 손으로 하단 1/3을 받치고 다른 손으로 탭한다. 서면 옆면 중간을 잡는다. 태블릿의 엄지 영역은 같은 기기에서도 자세에 따라 달라 일정하지 않다. 주요 콘텐츠는 가운데, 보조 액션은 가장자리, 3차 기능은 메뉴 뒤에 두라는 권고. Hoober는 이후 고전적 thumb zone 모델에서 멀어졌다"
why_needed: "약사가 조제실에서 서서 쓰는지, 책상에 놓고 쓰는지가 하단 조작 영역 배치를 좌우한다. '태블릿 엄지 영역은 일정하지 않다'는 결과는 '하단 = 무조건 편하다'는 가정을 깨는 근거다"
cost: "사용 자세를 관찰해야 한다(M7 관찰 항목 추가)"
how_to_apply: "주요 확정 버튼(감사 저장)은 하단 조작 영역 **우측 끝**에 두고, 파괴적 버튼(반납)은 거리를 둔다. 실제 자세(거치·손에 듦·서서)는 관찰로 확인한 뒤 확정한다(가설)"
confidence: 0.45
limitations: "의료 환경 연구가 아니고 일반 사용자 관찰이다. 태블릿 연구의 세부 수치는 원문을 보지 못했다"
```

```yaml
id: REF-221
type: 근거
title: "검사(체크) 중 중단은 정확도를 떨어뜨린다: 5분 중단 시 정확도 70% 대 90%"
source: "Pharmaceutical Journal 기사(지역약국 약사 103명 실험) https://pharmaceutical-journal.com/article/news/two-thirds-of-pharmacists-miss-at-least-one-of-five-dispensing-errors-hidden-in-test-prescriptions-study-finds ; Pharmacy Daily(Monash 고찰 51편) https://pharmacydaily.com.au/news/impacts-of-dispensing-with-distraction/114946 ; ISMP 'Minimizing distractions and interruptions' https://home.ecri.org/blogs/ismp-alerts-and-articles-library/minimizing-distractions-and-interruptions-during-medication-safety-tasks — WebSearch 발췌"
designer_or_org: "약학 연구(영국 언론 보도), Monash University, ISMP"
problem_it_solves: "업무가 끊긴 뒤 어디까지 확인했는지 잃어버리는 문제"
applies_to: [목록, 하단 조작 영역, 메모, 긴급 큐]
evidence: "약사 103명 중 숨겨진 오류 5개를 모두 찾은 사람은 36명(35%). 검사 중 5분 중단만 정확도를 유의하게 낮췄다(평균 70% 대 중단 없음 90%). Monash 고찰: 조제 중 중단·방해가 오류의 약 1/10에 관여하고, 약사는 시간당 5~20회 중단된다. 해결책은 물리 환경, 워크플로 변경, 약사 직접 접근 제한의 세 범주"
why_needed: "병원 약제부도 전화·문의·긴급 처방으로 자주 끊긴다. 화면이 '어디까지 했는지'를 보존해 주면 재개 비용을 줄일 수 있다. 미저장 선택 보존(REF-202), 필터·스크롤 위치 보존, 진행률(N3 '진행률 표시 없음')의 근거다"
cost: "상태 보존 범위(선택·스크롤·펼침)를 정해야 한다. 공용 태블릿이라 사용자 전환 시 보존 범위를 사번 단위로 나눠야 한다"
how_to_apply: "목록 상단에 '이 필터 기준 감사 n / 전체 N'을 표시한다. 마지막으로 처리한 행에 '여기까지' 표지를 둔다. 앱 복귀 시 스크롤과 미저장 선택을 복원한다"
confidence: 0.5
limitations: "지역약국 조제 검사 실험이고, 병원 처방 감사가 아니다. 원 논문 서지는 확인하지 못했다(언론 보도). 간호 중단 수치(ISMP 12.7%)는 2차 인용이라 넣지 않았다"
```

```yaml
id: REF-222
type: 근거
title: "약사 간 인수인계: 절반 가까이 부정확·불완전, 약 40%는 '조제 소프트웨어가 인계를 지원하지 않는다'"
source: "Chui 연구그룹(UW-Madison) https://pharmacy.wisc.edu/chui-research-group/chui-research/teamwork-communication/ ; J Patient Saf 관련 PMC5659955 https://pmc.ncbi.nlm.nih.gov/articles/PMC5659955 ; 'Quality of handoffs in community pharmacies' https://read.qxmd.com/read/28452917/quality-of-handoffs-in-community-pharmacies — WebSearch 발췌"
designer_or_org: "Michelle Chui 등(위스콘신대 약대)"
problem_it_solves: "미해결 문의·보류가 근무 교대 중에 사라지는 문제"
applies_to: [메모, 목록, R-024, R-038(문의/HD), '인수인계' ◐]
evidence: "지역약국 약사 445명 설문: 인계의 거의 절반이 부정확하거나 불완전했다. 거의 절반은 중단·방해가 많은 환경에서 일어났다. 90% 이상이 인계 교육을 받지 않았고, 약 40%는 조제 소프트웨어가 인계를 충분히 지원하지 않는다고 답했다. 동기식(대면·전화) 인계가 품질이 높았다. 비동기(메모·음성)는 보통 되묻기가 불가능하다"
why_needed: "ePRIS 메모(R-024)는 약품별 자유 텍스트다. 문의/HD·보류처럼 **미해결 상태의 이유**가 메모에만 있으면 다음 근무자가 놓친다. m2-traceability에서 '인수인계'가 ◐(부분)로 남아 있다"
cost: "메모에 '미해결/해결' 상태를 두면 메모가 작업 항목이 되어 상태 모델(M6)과 엮인다. 범위가 커질 수 있다 ⚑ PM 확인 필요"
how_to_apply: "최소안: 보류·문의/HD로 저장할 때 사유 메모를 같은 흐름에서 받는다(빈칸 허용 여부는 약제부 결정). 메모 아이콘은 '있음/없음'에 더해 '미해결 사유 있음'을 구분한다. 목록에 '미해결 메모 n건' 필터를 둔다"
confidence: 0.5
limitations: "미국 한 주(州)의 지역약국 설문이다. 병원 약제부 교대와 구조가 다르다. 초록·요약 수준이다"
```

```yaml
id: REF-223
type: 근거
title: "독립 이중 확인: 항암 처방 2차 약사 검증이 추가 오류를 잡았다. ISMP는 '각자 판단 후 비교'를 요구"
source: "Booth, Kennerly-Shah, Hartman, J Oncol Pharm Pract 2022 (PSNet 요약) https://psnet.ahrq.gov/issue/description-role-pharmacist-independent-double-checks-during-cognitive-order-verification ; ISMP Canada CJHP https://www.ismp-canada.org/download/cjhp0306.pdf ; Patient Safety Solutions 2019 https://www.patientsafetysolutions.com/docs/August_27_2019_Double_Check_on_Double_Checks.htm — WebSearch 발췌"
designer_or_org: "학술(오하이오주립대 등), ISMP, ASCO/ONS"
problem_it_solves: "1차 검토와 2차 감사의 역할 설계"
applies_to: [처방전 뷰(항암), 목록, R-036, R-038]
evidence: "외래 항암 주사 처방 1,645건: 1차 검증에서 30건, 2차에서 10건의 오류를 찾았다(저자: 수정된 오류 33.3% 증가). ISMP: 두 전문가가 각자 평가하고, 각자 끝낸 뒤에만 결론을 비교해야 독립적이다. 간호 설문에서는 이중 확인이 실제로는 '같이 하는 확인'이 되는 경우가 많았다"
why_needed: "ePRIS의 '검토(1차) → 감사(2차)'가 이중 확인 구조다(R-038). 감사 화면이 1차 검토자의 판단(검토 완료 표지·메모)을 **너무 강하게** 보여 주면 2차가 '확인 도장'이 될 수 있다는 가설의 근거다. v1 REF-112·패턴 #6(검토자·감사자 구분)과 이어진다"
cost: "1차 판단을 덜 보이게 하면 원안의 '검토자 이름 표시'(R-036)와 충돌할 수 있다 ⚑ PM 확인 필요. 약사는 1차 메모를 참고해야 한다고 볼 수도 있다"
how_to_apply: "가설 수준으로만 M7 질문에 넣는다: '감사 시 검토자 이름·메모를 먼저 보는가, 처방을 먼저 보는가?' 검토자 표시는 유지하되 처방 행보다 시각 위계를 낮게 둔다(이름은 보조 텍스트)"
confidence: 0.5
limitations: "단일 기관 후향 연구, 외래 항암이다. 화면 설계가 독립성에 미치는 영향을 측정한 연구는 찾지 못했다. 이 연결은 추론이다"
```

```yaml
id: REF-224
type: 근거
title: "모바일 기기 투약 바코드 확인 준수율이 PC보다 높았다(벤더 연구)"
source: "Epic Research https://www.epicresearch.org/articles/improved-barcode-scanning-for-medication-administration-with-mobile-devices-compared-to-standalone-scanners ; Houston Methodist Rover 안내 https://it.houstonmethodist.org/roverRT/ — WebSearch 발췌"
designer_or_org: "Epic Research(벤더 소속 연구)"
problem_it_solves: "스캔을 건너뛰는 우회"
applies_to: [필터(바코드 조회, R-014), 목록]
evidence: "**벤더 연구**: 2021~2024 데이터에서 모바일 기기로 투약을 완료했을 때 BCMA 준수율이 PC보다 일관되게 높았다. Rover는 손목밴드 → 약 스캔 → 오류 시 경고 순서이고, 휴대용 스캐너 일체형 기기를 쓴다"
why_needed: "ePRIS도 라벨 바코드 조회(R-014)가 있고, USB 동글과 가상 키보드를 섞어 쓴다. '스캔 장비가 손 안에 있을 때 스캔을 더 한다'는 결과는 스캔 진입점을 가장 가까운 곳(목록 상단 고정)에 두는 근거가 된다"
cost: "스캔 진입점을 상시 노출하면 상단 영역을 차지한다"
how_to_apply: "목록 상단 검색 필드에 스캔 입력을 상시 받게 하고(포커스 유지), 스캔 실패 시 수동 입력 경로를 같은 자리에 둔다(a3 #10)"
confidence: 0.35
limitations: "벤더 소속 연구이고 간호 투약 대상이다. 화면 설계 정보는 없다"
```

```yaml
id: REF-225
type: 패턴
title: "예외 큐: 문제 처방을 별도 큐로 보낸다(소매 약국 UX 포트폴리오)"
source: "Chris Kiess 포트폴리오(Retail Pharmacy UX) https://chriskiess.net/?p=23944180 — WebSearch 발췌"
designer_or_org: "Chris Kiess(UX 디자이너, 소매 약국 시스템)"
problem_it_solves: "판단 보류 처방이 일반 흐름에 섞여 처리 순서를 방해"
applies_to: [목록, 필터, R-038(문의/HD), 보류]
evidence: "처방에 문제가 있으면(금기, 나이·체중 대비 용량 의문 등) 예외 큐로 보낸다. 관찰·인터뷰·여정 지도로 조사했다(발췌)"
why_needed: "ePRIS의 문의/HD·보류는 '지금 처리 못 하는 처방'이다. 정규 목록에서 이들을 필터 칩 하나로 모아 볼 수 있어야 '놓치지 않게'(원칙 1)를 지킬 수 있다"
cost: "별도 탭이나 화면으로 만들면 탐색 단계가 늘어난다. 필터 칩으로 해결하면 비용이 작다"
how_to_apply: "별도 화면이 아니라 상태 필터 칩 '보류·문의 n'으로 구현한다. 칩 숫자는 0일 때 흐리게 둔다"
confidence: 0.35
limitations: "개인 포트폴리오이고 소매 약국이다. 결과 측정이 없다. 실무 사례이지만 비주얼 확인은 못 했다"
```

---

### 2. 화면별 정보 구조 비교 (조사 종합 · 가설)

| 요소 | 현장 시스템의 공통 구성 | ePRIS 현 설계 | 차이와 함의 |
|---|---|---|---|
| 큐 단위 | 환자 단위 큐(Cerner PPM) + 처방 단위 검증 창(Cerner·Epic·athena) | 환자 카드 + 약품 테이블을 한 목록에 통합 | 통합 목록은 장점(한눈에)이지만 환자 경계 혼동 위험이 있다 → REF-211 |
| 개인 뷰 | 관리자·약사가 큐 필터 저장(Epic, Cerner PPM views) | 필터 매번 선택, 세션 보존 불명(F06) | REF-201 |
| 긴급 진입 | 진입점 배지 + STAT 표지(CPSI), STAT 최상단(Ontada, a3 C10) | 별도 화면 + 오더 필터 2경로, 알림 없음(F03) | REF-204 |
| 확정 방식 | 행별 판정 → pending 표지 → 제출(Cerner) | 체크 → 감사 저장 | 구조는 같다. 미저장 표지가 없다 → REF-202 |
| 환자 판단 수치 | 검증 화면 상단에 키·체중·CrCl(검색 요약, 제품 미특정), 역할별 헤더(Epic Storyboard) | 카드에 있으나 접으면 사라짐(F07) | REF-213, REF-214 |
| 행 상세 | 행 클릭 시 펼침(athena), 별도 검증 창(Cerner) | 툴팁·팝업(R-042) | 태블릿에서는 호버가 없으므로 펼침 또는 우측 패널 |

---

### 3. ePRIS 화면별 적용 후보

| 화면 | # | 패턴 | 왜 (ePRIS 맥락) | 출처 |
|---|---|---|---|---|
| **목록** | L1 | **미저장 선택 표지 + 이탈 확인.** 하단에 'N건 선택 · 미저장'을 두고, 미저장 상태로 필터 변경·뒤로가기·로그아웃을 하면 확인을 받는다 | 체크 → 감사 저장 2단계에서 저장 전 이탈은 곧 감사 누락이다(원칙 1). 중단이 잦은 환경에서 특히 위험하다 | REF-202, REF-221, a3 A7 |
| | L2 | **진행률과 재개 지점.** '이 필터 기준 감사 n/N'과 마지막 처리 행 표지, 복귀 시 스크롤 복원 | 5분 중단만으로 확인 정확도가 90% → 70%로 떨어졌다. N3(진행률 없음)을 해결한다 | REF-221 |
| | L3 | **숨김·미분류 건수 노출.** PRN 숨김이나 미분류 병동이 있으면 'n건 숨김 · 보기'를 표시한다 | 필터 때문에 처방이 안 보이는 누락을 막는다(R-008과 같은 계열) | REF-203, REF-205 |
| **처방전 뷰** | P1 | **용량 숫자 렌더링 규칙**: 후행 0 제거, 선행 0 보장, 숫자–단위 공백, 천 단위 쉼표, 숫자 정렬(tabular) | 투여량이 툴팁에서 컬럼으로 올라와 상시 노출된다(10/21). 소수점 오독은 10배 오류로 이어진다 | REF-209, REF-208 |
| | P2 | **핵심 5요소(약명·함량·용량·경로·빈도) 위계 우선 + 약명 굵게**. 열 순서는 종이 처방전 그대로 유지 | eMAR 연구에서 가시성 위반이 많았다. 열 순서 변경 비용(원칙 3)은 피하면서 위계만 바꾼다 | REF-216, REF-210 |
| | P3 | **줄무늬 대신 옅은 가로선 + 약품명 열 고정(sticky)** | 가로 스크롤 표에서 행 추적이 어렵다. 줄무늬는 v1 상태 배경과 충돌한다 | REF-217 |
| **긴급 큐** | U1 | **좌 목록 5열 제한 + 우 상세 처리 후 자동 다음 + 좌측 스크롤 유지** | 300건 규모(R-043)를 훑으려면 좌 목록을 좁고 일정하게 유지해야 한다. '긴급 자동 다음'(◐)을 완성한다 | REF-218 |
| | U2 | **좌측 선택 행과 우측 상세 헤더의 식별 3요소를 같은 형식으로 고정** | 목록-상세 전환 시 다른 환자를 처리하는 오류를 상시 단서로 막는다(팝업 없이) | REF-211, REF-210 |
| | U3 | **정규 화면에서의 긴급 진입점 배지**(미처리 건수, 기준 시간 초과 시에만 강조) | F03(정규 작업 중 긴급 알림 없음)을 경고 피로 없이 해결한다 ⚑ 실시간 갱신 공수 | REF-204 |
| **필터** | F1 | **병동 2단 계층(대분류 체크 = 하위 전체, 펼쳐서 중분류) + '기타·미분류' 기본 포함** | R-045 → R-069 복수 선택 변경에 대응한다. 분류 밖 처방 누락을 막는다 | REF-203 |
| | F2 | **시트 하단 '결과 n건 보기' + 적용 필터 칩 상시 노출** | 모달 바텀시트가 목록을 가려 결과를 예측할 수 없다. 변경이 작은 안 A | REF-219, a3 #13 |
| | F3 | (M4 비교안) **가로 모드에서 우측 표준 사이드 시트** | 항목이 7개를 넘으면 바텀시트가 부적합하다(SAP·BrightHR) ⚑ 설계 구조 변경 | REF-219 |
| **조작 영역** | A1 | **확정 버튼(감사 저장)은 우측 끝, 파괴적 버튼(반납)은 거리를 두고 확인 강도를 차등** | 태블릿 엄지 영역은 자세에 따라 달라 일정하지 않다. 가역성별 확인은 a3 #6과 같다 | REF-220, a3 #6 |
| | A2 | **저장을 막는 조건(하드 스톱)은 객관적 필수 데이터 누락에만** 쓰고, 나머지는 행 내 경고로 | 하드 스톱이 많으면 우회 행동이 생긴다. 항암·TPN 하류 공정의 입구라서 최소한의 차단은 필요하다 | REF-207, REF-206, a3 C5 |
| | A3 | (TPN) **감사 저장 직전 '처방량 / 계산량 / 차이' 요약**(데이터가 있을 때만) | Abacus 리콜 대응이 '요약에서 대조하라'였다 ⚑ 범위 확인 | REF-206 |
| **메모** | M1 | **보류·문의/HD 저장 흐름에서 사유 메모를 바로 받기** | 미해결 이유가 메모에 없으면 다음 근무자가 놓친다. 인계의 절반 가까이가 부정확했다 | REF-222 |
| | M2 | **메모 아이콘 3단계(없음 / 있음 / 미해결 사유 있음) + '미해결 메모' 필터** | 메모가 많아지면 '있다'만으로는 우선순위를 알 수 없다 ⚑ 상태 모델과 엮임 | REF-222, REF-225 |
| | M3 | 메모·검토자 정보는 처방 행보다 **한 단계 낮은 시각 위계**로(이름은 보조 텍스트) | 2차 감사가 1차 판단을 그대로 따라가는 것을 줄인다(가설) ⚑ R-036 | REF-223 |

---

### 4. 공백 (이번에 찾지 못한 것)

- **국내 자료가 없다**: 분당서울대 BESTCare는 2011년 'Smart BESTCare'(의료진 스마트폰 조회)와 환자용 병상 태블릿만 확인됐다. 세브란스·서울아산·삼성서울은 2000년대 PDA 기사뿐이다. 서울성모병원(2026-04) 음성 간호기록 단말기 보도가 유일한 최신 자료이고, 약사 화면은 아니다. 다음 후보: 한국병원약학회지·대한의료정보학회(JKSMI) 발표, 이지케어텍 제품 자료.
- **Dribbble·Behance 실무 케이스 스터디가 없다**: 검색에서 약국 검증 케이스 스터디는 나오지 않았다. REF-225(포트폴리오) 1건뿐이다. 컨셉 시안은 근거로 쓰지 않는다.
- **Omnicell·Pyxis·Swisslog 소프트웨어 화면**은 조사하지 못했다(이번 배치에서 제외. 자동화 장비 UI라 ePRIS와의 거리도 멀다).
- **Epic Willow 검증 화면의 환자 헤더**(체중·CrCl 위치), **Oracle Health 모바일 약사 앱**은 확인하지 못했다.
- **NN/g 바텀시트·고밀도 표 글**, **ISMP 전자 지침의 잘림(truncation) 조항**, **호주 지침의 환자 식별 조항**은 원문을 열지 못해 비어 있다.

---

## 오케스트레이터에게 (v2)

1. **⚑ PM 확인 필요 묶음**: REF-201(개인 뷰 저장), REF-204(긴급 배지 실시간 갱신), REF-206·A3(TPN 대조 요약), REF-209(용량 표시 변환 규칙, 원본과 다르게 보임), REF-219·F3(필터 사이드 시트로 구조 변경), REF-222·M2(메모 미해결 상태), REF-223·M3(검토자 표시 위계, R-036).
2. **M6 전달**: P1(용량 숫자 렌더링 규칙)과 L1(미저장 표지)은 비용이 작고 안전 효과가 직접적이다. 우선 반영을 권한다. 미저장 표지는 v1의 '선택' 채널(체크 + 외곽선) 안에서 표현해 상태 종류를 늘리지 않는다.
3. **M4 전달**: 필터 안 A(바텀시트 유지 + 결과 건수 + 칩)와 안 B(가로 모드 사이드 시트), 처방전 뷰의 '좌측 환자 패널'(REF-212) 대안을 발산 후보로 넘긴다.
4. **M7 질문 후보**: (a) 태블릿을 어떤 자세로 쓰는가(거치·손·서서), (b) 감사할 때 검토자 메모를 먼저 보는가, (c) 업무가 끊긴 뒤 어디서 다시 시작하는가, (d) 보류·문의 사유를 지금 어디에 남기는가(인계 경로).
5. **a3 갱신 제안**: a3 패턴 #9(Tall Man)는 REF-215로 근거 수준을 낮춰야 한다(대규모 실사용 데이터에서 효과 없음).
6. REF 번호는 201~225를 썼다. m3-references.md로 병합할 때 재번호가 필요하면 조정한다. m3a·m3c 파일은 건드리지 않았다.

## 요약 (v2)
현장 약사 검증 시스템(Epic·Cerner·athena·CPSI)은 '큐 필터 저장 → 처방별 판정 → 미저장 표지 → 일괄 확정', 'STAT 진입점 배지', '위치 필터 + 미분류 버킷'으로 수렴한다. 이 가운데 ePRIS에 없는 것은 미저장 표지, 긴급 배지, 미분류 버킷이다.
표기·근거 쪽에서는 용량 숫자 규칙(ISMP), 접힘 상태에도 남는 핵심 수치(Fiori·신기능 근거), 중단·인계 연구가 목록·메모 설계를 직접 뒷받침한다. Tall Man과 줄무늬는 근거가 약하거나 v1과 충돌해 채택하지 않는다.
화면별 후보 18개 중 P1(용량 렌더링)·L1(미저장 표지)·U2(식별 단서 고정)를 우선 권한다.

## 신뢰도 (v2)
- 벤더 화면 패턴(REF-201~205): 0.35~0.55(병원 교육자료·도움말·마케팅의 검색 발췌, 화면 미확인)
- 표기 원칙(REF-208~210): 0.4~0.6(원문 미열람, CUI는 폐기 상태)
- 임상·사용성 근거(REF-211, 214~217, 221~223): 0.45~0.6(관찰·단일 기관·초록 수준, 약사 감사 화면에 대한 직접 연구는 거의 없음)
- 태블릿 레이아웃 원칙(REF-218~220): 0.45~0.6
- 화면별 적용 후보 종합: 0.6

## 주의사항 (v2)
- WebFetch가 전부 실패해서(DNS) 인용은 모두 검색 발췌다. 벤더 화면 구성은 병원별 빌드 차이가 커서 '선례' 이상으로 쓰면 안 된다.
- 벤더 수치(BD 7% 탐지, Epic Research 준수율, Sentri7 기능)는 **벤더 주장**이다.
- 약사 감사 화면에 대한 직접 연구는 거의 없다. 간호 eMAR, 지역약국, 응급실 처방의 연구를 유추해 쓴 카드가 많다(각 카드 limitations에 표시).
- REF-223(이중 확인 독립성 → 검토자 표시 위계)은 추론이고, R-036 원안 요구와 부딪칠 수 있다. 디자이너가 단독으로 바꾸지 않는다.
- 국내 사례와 실무 케이스 스터디는 찾지 못했다.

## 다음 단계 제안 (v2)
1. M6: P1(용량 렌더링 규칙)과 L1(미저장 표지·이탈 확인)을 스펙에 넣고, 환자 카드 접힘 상태의 '남는 정보 집합'(REF-213)을 약국별로 초안 작성한다.
2. M4: 필터 안 A/B, 긴급 큐 좌측 열 구성(U1), 처방전 뷰 좌측 환자 패널 대안을 발산한다.
3. M7: 위 4개 관찰 질문을 약제부 회의 질문지에 추가한다. 특히 사용 자세와 중단 후 재개 행동은 관찰로만 알 수 있다.
4. PM: ⚑ 7건을 v1 묶음(R-030 축소, X4)과 함께 한 번에 확인한다.
5. 원문 열람이 가능해지면 ACSQHC 2017 지침과 ISMP 전자 지침을 먼저 정독한다(REF-208·209의 신뢰도 갱신).
