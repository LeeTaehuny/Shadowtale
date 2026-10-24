---
id: T-002
title: 3인칭 캐릭터 이동과 카메라
status: todo        # todo | in-progress | review | done | blocked
owner:
milestone: M1
priority: P1
depends_on: [T-001]
scope:
  - Assets/_Project/Scripts/Runtime/Player/
  - Assets/_Project/Scripts/Runtime/CameraRig/
  - Assets/_Project/Data/Input/
  - Assets/_Project/Prefabs/Player/
  - Assets/_Project/Scenes/Sandbox/T-002_Move.unity
created: 2026-10-24
updated: 2026-10-24
tags: [task]
---

# 3인칭 캐릭터 이동과 카메라

## 목표
Input System과 CharacterController로 3인칭 캐릭터를 움직이고 Cinemachine 3 카메라가 따라가게 한다.

## 배경 / 관련 문서
- [[Architecture]]

## 완료 조건
- [ ] Input Actions 에셋 (Move, Look, Jump, Interact, Rotate) 키보드·마우스 + 게임패드 바인딩
- [ ] 카메라 기준 이동, 경사·계단 처리(CharacterController)
- [ ] CinemachineCamera + Orbital Follow로 3인칭 카메라
- [ ] Player 프리팹, 테스트 씬
- [ ] 문서 갱신

## 에디터 작업 (사용자)
- 테스트 씬 구성, 캡슐 캐릭터 프리팹 만들기, 카메라 오브젝트 배치

## 학습 포인트
- Input System: Action / Binding / PlayerInput (Enhanced Input IA·IMC 대응)
- CharacterController vs Rigidbody (Character Movement Component 대응)
- Cinemachine 3 (Spring Arm + Camera 대응)

## 작업 기록
