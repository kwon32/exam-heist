# Tech

## 스택 (제안, M1 시작 시 확정)
- **TypeScript + Vite**
- **Phaser 3** — 2D 씬/입력/애니메이션
- 상태 관리: 순수 TS 모듈 (게이지·파이프라인 로직은 Phaser와 분리해 단위 테스트 가능하게)
- 테스트: **Vitest**
- 배포: GitHub Pages (정적 빌드)

## 폴더 구조 (예정)
```
src/
  core/        # 게임 로직 (Phaser 비의존): gauges, pipeline, security, scoring
  data/        # 장비·정책·밸런스 수치 (JSON/TS)
  scenes/      # Phaser 씬: Title, Shop, Exam, PostInvestigation, Ending
  minigames/   # 조준, 리스닝, HUD, 시선 피하기
  ui/
tests/
docs/
```

## 명령어 (M1 이후)
```
npm install
npm run dev     # 개발 서버
npm test        # 단위 테스트
npm run build
```
