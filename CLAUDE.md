# 디자인 도우미 에이전트 저장소

탑 디자이너(토스, Linear, Airbnb 등)의 작업 프로세스를 바탕으로 만든 **모듈형 디자인 도우미**입니다. 사용자는 이 시스템으로 디자인을 개선하면서 작업 방식 자체를 배웁니다.

- 시작점: `/design-coach` 스킬(M0 코치). 모드를 고르고 모듈 에이전트를 호출하며 Why → Try → Compare → Reflect로 가이드합니다.
- 모듈 에이전트: `.claude/agents/design-*.md` (M1~M8, M3-a, M3-b)
- 공통 규약: `docs/framework/conventions.md` (모든 에이전트가 먼저 읽음)
- 프레임워크 배경: `docs/02-framework-modular.md`, 조사 자료: `docs/01-*.md`, `docs/04-*.md`, `docs/research/`
- 프로젝트 산출물: `projects/<slug>/`

## 규칙
- 주장에는 신뢰도(0.0~1.0)를 붙이고, 가설과 사실을 구분합니다.
- 응답 끝에는 명확한 답변, 신뢰도, 주요 주의사항을 둡니다.
- 환자명 등 실제 개인정보는 산출물에 남기지 않습니다.
