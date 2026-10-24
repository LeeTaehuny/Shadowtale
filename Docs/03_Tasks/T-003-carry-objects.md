---
id: T-003
title: 오브젝트 들기·놓기·회전
status: todo        # todo | in-progress | review | done | blocked
owner:
milestone: M1
priority: P1
depends_on: [T-002]
scope:
  - Assets/_Project/Scripts/Runtime/Carry/
  - Assets/_Project/Prefabs/Props/
  - Assets/_Project/Scenes/Sandbox/T-003_Carry.unity
created: 2026-10-24
updated: 2026-10-24
tags: [task]
---

# 오브젝트 들기·놓기·회전

## 목표
캐릭터가 가까운 오브젝트를 들고 다니다 내려놓고, 들고 있는 동안 회전시킬 수 있게 한다.

## 배경 / 관련 문서
- [[Architecture]]
- [[ADR-0001-shadow-match-method]]

## 완료 조건
- [ ] `Carryable` 컴포넌트 (들 수 있는 오브젝트 표시, 잡는 지점)
- [ ] `CarryController` (가장 가까운 Carryable 감지, 들기/놓기, 회전 입력)
- [ ] 놓을 때 바닥에 안정적으로 내려앉음(물리 튐 없음)
- [ ] Placed / Rotated 이벤트 (C# event) 발생
- [ ] EditMode 테스트: 가장 가까운 대상 선택 로직
- [ ] 문서 갱신

## 에디터 작업 (사용자)
- 테스트 소품(상자, 의자 등 프리미티브) 프리팹 구성

## 학습 포인트
- Physics.OverlapSphereNonAlloc과 GC 할당 회피
- Rigidbody isKinematic 전환
- C# event / Action (Delegate 대응)과 구독 해제

## 작업 기록
