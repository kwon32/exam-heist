# Workflow: Claude Code + Codex

사용자는 **Claude Code 터미널 하나**로만 소통한다. Claude가 리드, Codex는 Claude Code의 공식 Codex 플러그인(`openai/codex-plugin-cc`)으로 호출된다.

## 역할
| 누구 | 역할 |
|---|---|
| 사용자 | 방향 결정, 플레이테스트, 승인 |
| Claude Code | 설계, 작업 분해, 핵심 코드, 리뷰·통합, 테스트 |
| Codex | 위임받은 범위가 명확한 작업 구현, 교차 리뷰 |

## 규칙
1. **1 작업 = 1 브랜치 = 1 worktree = 1 에이전트.** 같은 파일을 동시에 수정하지 않는다.
2. 작업은 **파일/모듈 경계**로 나눈다 (예: `src/minigames/listening/*`는 Codex).
3. Codex 위임: worktree 생성 후 플러그인 스크립트에 `task --cwd <worktree> --write --background` 로 실행. 진행은 `/codex:status`, 결과는 `/codex:result`.
4. 교차 리뷰: Claude 작업 → `/codex:review`, Codex 작업 → Claude 리뷰. 이 레포에서는 stop-time review gate 활성화.
5. 같은 base 커밋에서 시작 → 각자 테스트 → 의존 순서대로 하나씩 merge → worktree 정리.
6. 파괴적 git 명령(reset --hard, force push 등)은 사용자 승인 후에만.
7. 마일스톤마다 사용자 플레이테스트.
