---
tags: [workflow]
---

# Git 설정

## 초기 1회
```bash
git init
git lfs install
# .gitignore / .gitattributes 는 키트에 포함
```

## 유니티 에디터 설정
- `Edit > Project Settings > Editor`
  - Version Control Mode: **Visible Meta Files**
  - Asset Serialization Mode: **Force Text**

## SmartMerge (씬/프리팹 병합)
`.git/config` 또는 전역 설정에 추가 (경로는 Unity 설치 위치에 맞게):
```ini
[merge]
    tool = unityyamlmerge
[mergetool "unityyamlmerge"]
    trustExitCode = false
    cmd = '<Unity 설치경로>/Editor/Data/Tools/UnityYAMLMerge.exe' merge -p "$BASE" "$REMOTE" "$LOCAL" "$MERGED"
```

## 브랜치 / 커밋
- `main`: 항상 컴파일 되는 상태
- `task/T-XXX-name`: Task별 작업
- 커밋: `[T-XXX] feat|fix|refactor|docs|test: 요약`
