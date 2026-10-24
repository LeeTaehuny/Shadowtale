---
description: Task를 마무리하고 문서·DevLog·커밋을 정리한다
argument-hint: T-XXX
---

Task `$ARGUMENTS` 를 마무리한다.

1. 완료 조건 체크리스트를 하나씩 검증한다. 미완료 항목이 있으면 `status: review` 또는 `in-progress` 유지 여부를 사용자에게 묻는다.
2. `unity-reviewer` 에이전트로 이번 브랜치 diff를 리뷰한다. 🔴 항목이 있으면 먼저 알린다.
3. Task 파일 갱신: 체크리스트, `## 작업 기록`에 요약, 관련 커밋/ADR 링크, `status`, `updated`.
4. `Docs/04_Progress/DevLog/<오늘>_<세션 이름>.md` 에 기록 (없으면 템플릿으로 생성): 한 일, 결정, 문제/해결, 다음 할 일, 📘 오늘 배운 것.
5. 이번 작업에서 새로 쓴 유니티 개념이 있으면 학습 노트로 저장할지 묻는다.
6. 커밋: `[$ARGUMENTS] <type>: <요약>` (코드 + 문서 같은 커밋). merge/push는 사용자 확인 후.
