---
description: 새 Task 파일을 템플릿으로 만든다
argument-hint: 작업 설명
---

다음 내용으로 새 Task를 만든다: $ARGUMENTS

1. `Docs/03_Tasks/`에서 가장 큰 T 번호 + 1 로 ID를 정한다.
2. `Docs/_Templates/Task.md` 형식으로 `T-XXX-<짧은영문이름>.md` 생성.
3. 목표, 범위(scope: 수정할 폴더/파일, 씬·프리팹 포함), 완료 조건, 의존 Task를 채운다. 한 세션(2~4시간)에 끝나지 않을 크기면 쪼개서 여러 개 만든다.
4. main에서 즉시 커밋: `[T-XXX] docs: add task` (ID 충돌 방지).
