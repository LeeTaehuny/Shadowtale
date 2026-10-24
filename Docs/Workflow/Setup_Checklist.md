---
tags: [workflow, setup]
updated: 2026-10-24
---

# 초기 셋업 체크리스트

## 1. 레포 & Git
- [ ] GitHub에 빈 레포 `shadowtale` 생성 (README·.gitignore 없이)
- [ ] 로컬에 클론 → 이 키트(CLAUDE.md, .claude/, Docs/, .gitignore, .gitattributes)를 루트에 복사
- [ ] `git lfs install` (PC당 1회) → 첫 커밋 전에 `.gitattributes`가 들어가 있는지 확인
- [ ] SmartMerge(UnityYAMLMerge) 설정 → [[Git_Workflow]]

## 2. Unity (T-001)
- [ ] Unity Hub에서 **6000.3 LTS** 설치 (모듈: Windows Build Support (IL2CPP), 문서 선택)
- [ ] 템플릿 **Universal 3D**로 프로젝트 생성 → 생성된 내용을 레포 루트로 (레포 루트 = 프로젝트 루트)
- [ ] `Edit > Project Settings > Editor`: Version Control Mode = Visible Meta Files, Asset Serialization Mode = Force Text
- [ ] `Edit > Project Settings > Player > Other Settings`: Active Input Handling = **Input System Package (New)**
- [ ] Package Manager: Input System, Cinemachine (3.x), Test Framework 확인/설치
- [ ] `Edit > Preferences > External Tools`: Rider 또는 Visual Studio 지정 → Regenerate project files
- [ ] (선택) `Project Settings > Editor > Enter Play Mode Settings`: 도메인 리로드 끄기는 static 초기화 규칙을 배운 뒤에

## 3. Obsidian
- [ ] 볼트 열기: 레포의 `Docs/` 폴더
- [ ] 커뮤니티 플러그인: **Dataview**(필수, Board/Home), Templater(선택), Obsidian Git(선택)
- [ ] 설정 > 파일 및 링크: 새 링크 형식 = 최단 경로, 위키 링크 사용
- [ ] Templates 폴더 = `_Templates`

## 4. Claude Code 멀티 세션 (2개)
- [ ] main 워크트리: 유니티 에디터 + Obsidian
- [ ] 세션 워크트리 2개: `git worktree add ../shadowtale-s1 -b task/T-xxx-...` (s1), `../shadowtale-s2` (s2)
- [ ] 각 세션 시작 시 "나는 s1이다"처럼 이름 알려주기 → [[Multi_Session]]

## M1 병렬 진행 추천
T-001은 혼자 먼저 끝낸다(모든 Task의 기반). 그 뒤:

| 순서 | s1 (플레이어 쪽) | s2 (그림자 쪽) |
|---|---|---|
| 1 | T-002 3인칭 이동 | T-005 판정 로직 (코드 전용) |
| 2 | T-003 들기·놓기 | T-004 광원·그림자 벽 |
| 3 | T-009 카툰 스파이크 | T-007 전환 연출 |
| 4 | T-006 ShadowTarget 연결 | T-008 페이지 진행 |

scope가 겹치지 않도록 짝지었다. T-006과 T-008은 앞 단계가 머지된 뒤 시작한다.
