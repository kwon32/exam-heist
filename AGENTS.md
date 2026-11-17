# AGENTS.md — 모든 AI 에이전트 공통 규칙

## 프로젝트
"합격 작전" — 웹 기반 픽션 시뮬레이션 게임. 먼저 읽을 것: `docs/mission.md`, `docs/game-design.md`, `docs/tech.md`, `docs/workflow.md`.

## 콘텐츠 원칙
- 장비·수치·규칙은 **가상**. 실존 제품명·사양·실제 회피 절차를 코드/문서/데이터에 넣지 않는다.
- 실존 인물(실명·닉네임) 사용 금지.
- 정부 대책은 `docs/research/policies.md`의 공개 보도 수준만 반영.

## 코드 규칙
- TypeScript strict. 게임 로직(`src/core`)은 Phaser에 의존하지 않고 Vitest로 테스트.
- 밸런스 수치는 `src/data`에만 둔다 (하드코딩 금지).
- 커밋은 작고 의미 단위로. 메시지는 영어 conventional commits (`feat:`, `fix:`, `docs:`...).

## 협업 규칙
- 할당받은 파일/폴더 밖은 수정하지 않는다. 필요하면 결과에 제안으로 남긴다.
- 자기 worktree/브랜치에서만 작업. main에 직접 커밋 금지 (Claude 통합 시 제외).
- 작업 끝나면 `npm test` 통과 확인.
