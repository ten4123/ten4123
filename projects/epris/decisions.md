# ePRIS 결정 로그 (M8, append-only)

> 상태: 검증 전 / 검증됨 / 번복됨 / **미결정**(합의 필요). 미결정 항목은 결정되는 즉시 갱신한다.
> 근거: `docs/05-epris-status-review.md`

```yaml
id: DEC-001
date: 2026-10-23
status: 미결정
question: "ePRIS는 종이 처방전을 대체하는 검토 도구인가, 처방 목록을 관리하는 감사 도구인가?"
options_considered: [처방전 뷰 중심, 목록 중심, 목록(작업 큐) + 환자 처방전 뷰 하이브리드]
chosen: null
proposal: "하이브리드 (05 문서 4-1)"
owner: PM + 약제부
revisit_if: "약사가 종이에 적는 내용 확인 후"
```

```yaml
id: DEC-002
date: 2026-10-23
status: 미결정
question: "약국·병동 접수 플로우: A안(3단계 위저드, 원안) vs B안(조회 조건 폼, 10/12 내부 개편안)"
note: "10/21 회의록에 결정 기록 없음. 필터 언어로 보아 B안 쪽으로 흐른 듯하나 명시적 합의가 없다"
chosen: null
owner: 다음 회의
```

```yaml
id: DEC-003
date: 2026-10-21
status: 미결정(고객 합의·공수 조정 미확인)
question: "앱 내 스타일러스 펜 그리기 입력을 제공하는가?"
recorded: "회의록: '앱에서 스타일러스 펜 그리기 입력 요구사항은 사업범위 밖임' / 태블릿 기본 기능은 사용 가능"
conflict: "공수산정(HTML 인용): 펜 그리기·필기감 20 M/D가 1차 범위에 배정됨"
owner: PM
revisit_if: "공수산정 원문 확인, 대상 기종 확정"
```

```yaml
id: DEC-004
date: 2026-10-21
status: 검증 전
question: "기본 조회 조건"
chosen: "접수일 기준 Default Toggle ON, 처방일은 필요할 때 추가"
feedback_source: "10/21 회의록"
```

```yaml
id: DEC-005
date: 2026-10-21
status: 검증 전
question: "여러 환자 비교 방식"
chosen: "가로 스크롤 통합 뷰 유지"
feedback_source: "10/21 회의록"
open_issue: "가로 스크롤 시 고정 열(환자·약품명) 정의 필요"
```

```yaml
id: DEC-006
date: 2026-10-21
status: 검증 전
question: "입원조제 투여량 정보 노출 방식"
chosen: "팝업 대신 컬럼에 직접 노출"
feedback_source: "10/21 회의록"
```

## 가이드라인 후보
- (결정이 쌓이면 추가)
