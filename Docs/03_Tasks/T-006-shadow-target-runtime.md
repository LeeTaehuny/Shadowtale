---
id: T-006
title: ShadowTarget 연결과 목표 데이터 SO
status: todo        # todo | in-progress | review | done | blocked
owner:
milestone: M1
priority: P1
depends_on: [T-003, T-004, T-005]
scope:
  - Assets/_Project/Scripts/Runtime/Shadow/
  - Assets/_Project/Data/ShadowTargets/
  - Assets/_Project/Scripts/Editor/
  - Assets/_Project/Scenes/Sandbox/T-006_Match.unity
created: 2026-10-24
updated: 2026-10-24
tags: [task]
---

# ShadowTarget 연결과 목표 데이터 SO

## 목표
Carryable이 놓이거나 회전될 때 ShadowTarget이 판정을 돌려 일치 시 Matched 이벤트를 낸다.

## 배경 / 관련 문서
- [[ADR-0001-shadow-match-method]]
- [[Architecture]]

## 완료 조건
- [ ] `ShadowTargetData` ScriptableObject
- [ ] `ShadowTarget` 컴포넌트: 대상 Carryable 감지, 판정, Matched 이벤트, 근처 스냅 보정
- [ ] 에디터 도구: 씬에 정답 배치를 해두고 MenuItem으로 SO에 캡처
- [ ] PlayMode 테스트: 정답 위치에 놓으면 Matched 발생
- [ ] 문서 갱신

## 에디터 작업 (사용자)
- 정답 배치를 씬에서 잡고 캡처 도구 실행

## 학습 포인트
- ScriptableObject (DataAsset 대응)와 런타임 값 변경 주의
- [MenuItem] 에디터 스크립트 (Editor Utility Widget 대응)

## 작업 기록
