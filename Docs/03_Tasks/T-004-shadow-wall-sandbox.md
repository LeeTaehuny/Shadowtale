---
id: T-004
title: 광원·그림자 벽 테스트 씬과 그림자 품질
status: todo        # todo | in-progress | review | done | blocked
owner:
milestone: M1
priority: P1
depends_on: [T-001]
scope:
  - Assets/_Project/Rendering/
  - Assets/_Project/Scripts/Runtime/Shadow/ShadowLight.cs
  - Assets/_Project/Scenes/Sandbox/T-004_ShadowWall.unity
created: 2026-10-24
updated: 2026-10-24
tags: [task]
---

# 광원·그림자 벽 테스트 씬과 그림자 품질

## 목표
광원 하나와 그림자 벽으로 "읽기 쉬운" 그림자가 나오는 URP 설정을 찾고 기준 씬을 만든다.

## 배경 / 관련 문서
- [[ADR-0001-shadow-match-method]]

## 완료 조건
- [ ] Spot / Point / Directional 광원 비교 후 퍼즐용 광원 타입 결정 (DevLog에 기록)
- [ ] URP Asset 그림자 설정 (해상도, Cascade, Bias, Soft Shadow) 튜닝 값 기록
- [ ] `ShadowLight` 컴포넌트: 광원 기준 좌표계 제공 (판정에서 사용)
- [ ] 그림자 벽 머티리얼 (그림자만 잘 보이는 단색)
- [ ] 문서 갱신

## 에디터 작업 (사용자)
- URP Asset / Light 설정을 에디터에서 조정하며 비교 스크린샷

## 학습 포인트
- URP 실시간 그림자 (Shadow Map, Cascade, Depth/Normal Bias)
- 언리얼 Shadow 설정과의 차이

## 작업 기록
