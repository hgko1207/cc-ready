# CHANGELOG

## 0.6.0 — 2026-11-17

이름을 **team-ai-kit에서 cc-ready로** 바꿨다. 혼자 쓰는 사람에게 팀 전용처럼 보이던 이름을, 키트의 핵심인 "명령 하나로 저장소에 맞는 Claude Code 세팅"에 맞췄다. 동작은 바뀌지 않았다.

- 마켓플레이스 `team-ai-kit` → `cc-ready`, 플러그인 `team-ai` → `cc-ready`, `team-ai-extras` → `cc-ready-extras`. 명령은 `/cc-ready:setup`, `/cc-ready:verify` 등으로 바뀐다.
- 설치: `claude plugin marketplace add hgko1207/cc-ready`, `claude plugin install cc-ready@cc-ready`. 예전 이름으로 설치했다면 `claude plugin uninstall team-ai@team-ai-kit` 뒤 새로 설치한다.
- 팀 설정 파일은 `.claude/cc-ready.json`으로 바뀌었다. 예전 `.claude/team-ai.json`도 계속 읽고 보호한다(새 파일이 있으면 새 파일 우선). 테스트 3개 추가.
- README에 Anthropic과 관계없는 개인 도구라는 안내를 넣었다.

## 0.5.0 — 2026-11-15

출시 직전에 빠뜨리기 쉬운 것을 plan.md에서 챙기게 했다.

- setup이 새로 만드는 plan.md에 `## 출시 전 확인` 목록을 넣는다. 기본은 비밀값과 배포 환경변수 두 줄이고, 저장소 종류에 따라 덧붙인다: 화면 있는 웹·앱(개인정보처리방침과 동의 안내, 아이콘·공유 미리보기 이미지, 404·오류 화면), PWA(실제 PNG 아이콘과 실기기 설치), 스토어 앱(등록 자료, Google Play 12명·14일 테스트). 라이브러리·내부 도구에는 넣지 않는다. 이미 있는 plan.md에는 넣지 않고 보고서에서 제안한다.
- plan-feature가 첫 출시·배포 작업을 계획할 때 이 목록의 남은 줄을 검증 항목에 넣는다.
- 재주입 훅은 바뀌지 않았다. 이 목록이 "다음 작업"에 섞이지 않는 것을 테스트로 확인했다.

## 0.4.1 — 2026-11-15

실제 저장소에 사람이 직접 적용해 본 결과를 반영한 문구 수정. 동작은 바뀌지 않았다.

- setup 보고가 "main에 커밋하면 훅이 막는다"고 틀리게 경고하던 문제를 고쳤다. 보호 브랜치 훅은 강제 push와 브랜치 삭제만 막는다는 사실을 setup 지시에 적고, 문서에 없는 동작을 짐작해 보고하지 않게 했다.
- `.claude/`·`.vscode/` 새 파일을 만들 때의 승인 창은 권한 모드가 Auto면 뜨지 않을 수 있다고 QUICKSTART와 setup 보고에 적었다.

## 0.4.0 — 2026-11-14

Claude Code와 Codex 같은 다른 AI 도구를 같이 쓰는 저장소 지원.

- setup에 AGENTS 방식 추가: 공통 규칙은 `AGENTS.md`, `CLAUDE.md`는 첫 줄 `@AGENTS.md`로 가져온 뒤 Claude 전용 안내만 둔다(공식 문서가 권하는 import 방식, Windows에서도 동작). CLAUDE.md·AGENTS.md가 둘 다 없으면 한 번 묻고, AGENTS.md만 있으면 이 방식을 제안한다.
- 대화 압축 후 재주입 훅이 `reinjectSections`의 섹션을 CLAUDE.md에서 못 찾으면 AGENTS.md에서 찾는다. AGENTS 방식이면 setup이 `검증 명령`, `하지 말 것`을 기본으로 넣는다.
- verify·review-pr·commit·plan-feature·open-pr·update-docs가 CLAUDE.md가 가져온 AGENTS.md도 함께 본다.

## 0.3.0 — 2026-11-10

첫 공개 버전(MIT).

- 기본 플러그인 `team-ai`: `setup`, `plan-feature`, `verify`, `review-pr`, `commit` 스킬과 보호 경로 차단, 위험 명령 차단, 수정 후 포맷, 대화 압축 후 남은 작업 다시 알림 훅.
- 선택 플러그인 `team-ai-extras`: `fix-issue`, `refactor`, `open-pr`, `update-docs` 스킬과 `verifier` 에이전트.
- 스택 규칙 예시 5종, 처음 쓰는 사람용 QUICKSTART, VS Code·Windows 참고 문서, 훅 테스트.
- setup이 마켓플레이스 주인을 기본 `hgko1207`로 채운다. 회사가 사본을 두었으면 그 주인으로 바꾼다.
