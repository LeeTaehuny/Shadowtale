---
tags: [workflow]
---

# 멀티 세션 작업 규칙

여러 Claude Code 세션이 동시에 작업할 때 충돌을 막기 위한 규칙.

## 핵심 원칙
1. **1 세션 = 1 Task = 1 브랜치 = 1 워크트리**
2. Task 점유는 Task 파일의 `status`/`owner`를 **main에 커밋**해서 표시한다 (분산 락).
3. 같은 씬(`.unity`)·프리팹(`.prefab`)은 동시에 한 세션만 만진다. → Task의 `scope`에 명시하고 `/task-start`가 겹침을 검사한다.
4. 공유 문서는 **충돌 안 나는 구조**로: Task는 파일 1개씩, DevLog는 `날짜_세션.md`로 세션별 분리, Board는 Dataview 자동 생성.

## 폴더 배치 (예시)
```
D:/Dev/MyGame/           ← main 워크트리: 유니티 에디터 + Obsidian 볼트(Docs/)
D:/Dev/MyGame-s1/        ← 세션 1 워크트리 (task/T-012-...)
D:/Dev/MyGame-s2/        ← 세션 2 워크트리 (task/T-015-...)
```
```bash
git worktree add ../MyGame-s1 -b task/T-012-player-move
git worktree list
git worktree remove ../MyGame-s1     # 머지 후 정리
```

## 유니티 특이사항
- 워크트리마다 별도의 `Library/`가 생기므로 **첫 열기 시 임포트 시간**이 걸린다. 세션 수는 2~3개 권장.
- 같은 프로젝트 경로를 에디터 두 개로 열 수 없다. 워크트리는 경로가 다르므로 가능하지만, 확인이 필요할 때만 연다.
- 코드 전용 Task는 에디터 없이 배치모드 테스트로 검증할 수 있다 (에디터가 그 경로를 열고 있지 않을 때).
- 씬/프리팹 병합은 **UnityYAMLMerge(SmartMerge)** 를 설정해 둔다 → [[Git_Workflow]].

## 세션 이름
- 각 세션 시작 시 "나는 s1이다"처럼 이름을 알려준다. owner와 DevLog 파일명에 쓰인다.

## 흐름
```
main에서 /task-new → 커밋
각 세션: /task-start T-XXX → (main) 점유 커밋 → 워크트리에서 구현
       → /task-done T-XXX → 리뷰 → main에 merge → 워크트리 정리
```

## 충돌 시
- Task 파일 충돌: 나중에 점유한 쪽이 양보 (다른 Task 선택).
- 코드 충돌: merge 전에 `git rebase main` 후 테스트 재실행.
- 씬 충돌: 자동 병합 실패 시 한쪽 변경을 버리고 에디터에서 재작업 (그래서 scope 겹침을 미리 막는다).
