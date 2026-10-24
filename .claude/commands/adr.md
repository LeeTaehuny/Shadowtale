---
description: 설계 결정을 ADR 문서로 기록한다
argument-hint: 결정 제목
---

"$ARGUMENTS" 에 대한 ADR을 작성한다.

1. `Docs/02_Architecture/ADR/`의 가장 큰 번호 + 1로 `ADR-XXXX-<짧은이름>.md`를 `Docs/_Templates/ADR.md` 형식으로 만든다.
2. 맥락, 고려한 대안(최소 2개, 장단점), 결정, 결과/트레이드오프, **언리얼과 비교**를 채운다. 대화와 코드에서 근거를 찾고, 모르는 부분은 사용자에게 묻는다.
3. 영향받는 Task와 `Architecture.md`에 링크를 추가한다.
