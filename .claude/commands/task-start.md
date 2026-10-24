---
description: Task를 점유하고 작업 브랜치/워크트리를 준비한다
argument-hint: T-XXX
---

Task `$ARGUMENTS` 작업을 시작한다.

1. `Docs/03_Tasks/`에서 `$ARGUMENTS`로 시작하는 파일을 읽는다. 없으면 멈추고 알린다.
2. frontmatter 확인:
   - `status`가 `in-progress`이고 `owner`가 다른 세션이면 **멈추고** 사용자에게 알린다.
   - `depends_on`의 Task가 `done`이 아니면 경고한다.
3. 다른 `in-progress` Task들의 `scope`와 이번 Task의 `scope`가 겹치는지 검사하고, 겹치면 경고한다.
4. 점유: main 브랜치에서 `status: in-progress`, `owner: <세션 이름>`, `updated: 오늘` 으로 수정 →
   `git commit -m "[$ARGUMENTS] docs: claim task"` (push 여부는 사용자에게 확인).
5. 작업 위치 준비 (`Docs/Workflow/Multi_Session.md` 참고):
   - 현재 위치가 이 Task 전용 워크트리면 `task/$ARGUMENTS-<short>` 브랜치로 체크아웃.
   - 아니면 워크트리 생성 명령을 제안만 하고 실행은 사용자 확인 후.
6. Task의 목표, 범위, 완료 조건, 관련 문서, 예상되는 학습 포인트를 요약해 보여주고 구현 계획(3~7단계)을 제시한다. 사용자 승인 후 구현을 시작한다.
