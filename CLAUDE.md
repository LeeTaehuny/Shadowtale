# CLAUDE.md — Shadowtale

> Claude Code가 모든 세션 시작 시 읽는 프로젝트 규칙.

## 프로젝트 요약
- 게임: 잠 못 드는 아이에게 엄마가 읽어주는 그림 동화책 속으로 들어가, **3D 세계의 오브젝트를 광원 앞에 배치해 벽의 그림자 그림을 재현**하고, 완성된 페이지 그림 속에서 **2D 횡스크롤**로 퍼즐·전투를 푸는 그림자 퍼즐 게임.
- 핵심 루프: 페이지 진입(3D) → 3인칭 캐릭터로 오브젝트 운반·배치 → 그림자 일치 → 그림자가 2D 그림으로 변환 → 페이지의 그림자 전부 완성 → 벽 그림으로 클로즈업 → 2D 횡스크롤 플레이 → 페이지 넘김
- Unity: **6000.3 LTS (Unity 6.3)** / 렌더: **URP (카툰 렌더링)** / 플랫폼: **PC (Steam, Windows)**, 키보드·마우스 + 게임패드
- 상세: `Docs/01_Overview/Project_Overview.md` · 구조: `Docs/02_Architecture/Architecture.md`

## 사용자에 대해
- 언리얼 경력 개발자이며 **유니티·C# 학습 중**이다.
- 새로운 유니티 개념/패턴을 처음 사용할 때는 작업 보고 끝에 **"📘 학습 포인트"** 섹션을 붙여 3~6줄로 설명한다: 무엇인지 → 언리얼 대응 개념 → 왜 이 방식을 택했는지.
- 깊은 설명이 필요하면 `unity-tutor` 에이전트에 위임하고, 결과를 `Docs/05_Learning/`에 노트로 저장하자고 제안한다.
- 개념 매핑 기준표: `Docs/05_Learning/Unreal_to_Unity.md`

## 폴더 구조
```
/                     ← 레포 루트 = 유니티 프로젝트 루트
├─ Assets/
│  ├─ _Project/       ← 우리 코드·에셋은 전부 여기
│  │  ├─ Scripts/
│  │  │  ├─ Core/     (asmdef: Ritae.Shadowtale.Core — UnityEngine 최소 의존 순수 로직)
│  │  │  ├─ Runtime/  (asmdef: Ritae.Shadowtale.Runtime)
│  │  │  └─ Editor/   (asmdef: Ritae.Shadowtale.Editor)
│  │  ├─ Tests/
│  │  │  ├─ EditMode/ (asmdef: Ritae.Shadowtale.Tests.EditMode)
│  │  │  └─ PlayMode/ (asmdef: Ritae.Shadowtale.Tests.PlayMode)
│  │  ├─ Data/        (ScriptableObject 에셋: 페이지·그림자 목표 정의)
│  │  ├─ Rendering/   (URP Asset, Renderer, Shader Graph, 카툰 머티리얼)
│  │  └─ Prefabs/  Scenes/  Art/  Audio/
│  └─ ThirdParty/
├─ Packages/  ProjectSettings/
├─ Docs/              ← Obsidian 볼트 (Assets 밖이라 유니티가 임포트하지 않음)
└─ .claude/           ← 에이전트·커맨드
```
Runtime 안의 하위 폴더(=모듈): `Book/`, `Player/`, `Carry/`, `Shadow/`, `Page2D/`, `CameraRig/`, `UI/`. 모듈별 책임은 Architecture 문서 참고.

## 코딩 규칙
- 네임스페이스: `Ritae.Shadowtale.<Module>` (예: `Ritae.Shadowtale.Shadow`)
- 모든 런타임 코드는 asmdef 안에 둔다. 의존 방향: Editor → Runtime → Core. Core는 Runtime을 모른다.
- 인스펙터 노출은 `public` 필드 대신 `[SerializeField] private`.
- 설정/밸런스/레벨 데이터(페이지 구성, 그림자 목표, 판정 허용 오차)는 ScriptableObject로 분리한다.
- `Update()`에서 `GetComponent`, `Find*`, LINQ, 문자열 결합 등 GC 할당 금지. 참조는 `Awake`에서 캐싱.
- 입력은 **Input System 패키지**(Input Actions 에셋)만 쓴다. 구 `UnityEngine.Input` 금지.
- 카메라는 **Cinemachine 3.x**(`Unity.Cinemachine` 네임스페이스)를 쓴다. 2.x API(`Cinemachine` 네임스페이스) 예제를 섞지 않는다.
- 비동기: 기본은 코루틴 또는 `Awaitable`(Unity 6+). 서드파티(UniTask, DOTween 등)는 ADR 후 도입.
- 순수 로직(그림자 판정, 페이지 진행 상태)은 MonoBehaviour와 분리해 Core에 두고 EditMode 테스트를 작성한다.
- 주석·문서는 한국어, 식별자는 영어.

## 하지 말 것
- `.meta` 파일 수동 생성/삭제/편집 금지. 에셋 이동·이름 변경은 사용자에게 에디터에서 하도록 요청한다.
- `.unity`/`.prefab`/`.asset`/`.shadergraph` YAML·JSON 직접 편집 금지. 불가피하면 먼저 사용자에게 확인. 대안으로 Editor 스크립트(MenuItem)를 작성해 사용자가 실행하게 한다.
- `ProjectSettings/`, `Packages/manifest.json`, URP Asset/Renderer 설정 변경은 사용자 승인 후에만.
- 다른 세션이 점유한 Task의 파일·씬·프리팹은 수정하지 않는다 (`Docs/Workflow/Multi_Session.md`).

## 테스트 / 빌드
- 에디터가 이 폴더를 열고 있지 **않을 때**만 배치모드 실행 가능:
  ```
  "C:/Program Files/Unity/Hub/Editor/<6000.3.x 버전>/Editor/Unity.exe" -batchmode -nographics -projectPath . -runTests -testPlatform EditMode -testResults ./TestResults/editmode.xml -logFile -
  ```
  (정확한 경로는 T-001에서 확정해 이 줄을 갱신한다.)
- 에디터가 열려 있으면 사용자에게 Test Runner 실행을 요청하고 결과를 받는다.
- 컴파일 오류는 커밋 전 반드시 해결 (Editor.log: `%LOCALAPPDATA%\Unity\Editor\Editor.log`).

## 문서 & 작업 흐름 (필수)
1. 세션 시작 → `/task-start T-XXX` : Task 읽기 → 점유 → 브랜치/워크트리 확인.
2. 작업 중 설계 결정 발생 → `/adr 제목` 으로 ADR 작성.
3. 세션 종료 → `/task-done T-XXX` : Task 갱신, DevLog 기록, 커밋.
- 문서 형식은 `Docs/_Templates/`를 따른다. 문서 간 링크는 Obsidian `[[파일명]]` 형식.
- 상태판(`Docs/00_Home/Board.md`)은 Dataview 쿼리로 자동 생성되므로 **직접 수정하지 않는다.**

## 멀티 세션
- 동시 세션 **2개** (`s1`, `s2`). 워크트리: `<repo>-s1`, `<repo>-s2`.
- 같은 씬은 한 세션만. 테스트 씬은 Task별로 따로 만든다 (`Scenes/Sandbox/T-XXX_*.unity`).

## Git
- 브랜치: `task/T-XXX-short-name`. main 직접 커밋은 Task 점유 표시와 문서 갱신만.
- 커밋 메시지: `[T-XXX] feat|fix|refactor|docs|test: 요약`
- 커밋 단위는 작게. 코드와 해당 문서 갱신은 같은 커밋에.
- push/merge는 사용자 확인 후.

## 에이전트
| 에이전트 | 언제 |
|---|---|
| `unity-architect` | 새 시스템 설계, 모듈 경계, ADR 초안 |
| `unity-implementer` | Task 단위 구현 (+테스트) |
| `unity-reviewer` | 커밋/머지 전 리뷰 |
| `doc-keeper` | Task·DevLog·ADR 정리, 문서-코드 불일치 점검 |
| `unity-tutor` | 개념 설명, 학습 노트 작성 |
