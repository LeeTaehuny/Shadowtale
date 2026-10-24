---
id: T-005
title: 그림자 일치 판정 로직 (Core)
status: todo        # todo | in-progress | review | done | blocked
owner:
milestone: M1
priority: P0
depends_on: [T-001]
scope:
  - Assets/_Project/Scripts/Core/Shadow/
  - Assets/_Project/Tests/EditMode/
created: 2026-10-24
updated: 2026-10-24
tags: [task]
---

# 그림자 일치 판정 로직 (Core)

## 목표
광원 기준 위치·회전·허용 오차로 일치 여부와 근접도(0~1)를 계산하는 순수 C# 판정기를 만든다.

## 배경 / 관련 문서
- [[ADR-0001-shadow-match-method]]

## 완료 조건
- [ ] `ShadowMatchEvaluator`: 입력(현재 위치/회전, 목표, 오차, 대칭 회전 목록) → 결과(일치 여부, 근접도)
- [ ] 평면 오차와 깊이(광원 방향) 오차 분리
- [ ] 대칭 회전 허용 (예: 상자 90도 대칭)
- [ ] EditMode 테스트 10개 이상 (경계값, 대칭, 깊이 오차)
- [ ] 문서 갱신

## 에디터 작업 (사용자)
- 없음 (코드 전용 Task — 에디터 없이 배치모드 테스트 가능)

## 학습 포인트
- asmdef 분리로 순수 로직 테스트
- Quaternion.Angle과 회전 비교 함정
- C# struct(값 타입) 결과 반환

## 작업 기록
