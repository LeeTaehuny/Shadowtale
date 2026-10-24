---
id: T-009
title: 카툰 셰이딩 방식 비교 (스파이크)
status: todo        # todo | in-progress | review | done | blocked
owner:
milestone: M1
priority: P3
depends_on: [T-004]
scope:
  - Assets/_Project/Rendering/Shaders/Toon/
  - Assets/_Project/Rendering/Materials/
  - Assets/_Project/Scenes/Sandbox/T-009_Toon.unity
  - Docs/02_Architecture/ADR/ADR-0002-toon-rendering.md
created: 2026-10-24
updated: 2026-10-24
tags: [task]
---

# 카툰 셰이딩 방식 비교 (스파이크)

## 목표
Shader Graph 커스텀 라이팅과 Unity Toon Shader를 비교해 ADR-0002를 확정한다.

## 배경 / 관련 문서
- [[ADR-0002-toon-rendering]]

## 완료 조건
- [ ] 같은 씬에 A/B 두 방식 머티리얼 적용, 그림자 벽 가독성 비교 스크린샷
- [ ] Shader Graph 툰 셰이더 최소 버전 (램프 + 그림자 감쇠)
- [ ] ADR-0002 status: accepted로 갱신
- [ ] 문서 갱신

## 에디터 작업 (사용자)
- Package Manager로 Toon Shader 설치 시도, Shader Graph 편집

## 학습 포인트
- Shader Graph Custom Function 노드
- URP 메인 라이트/그림자 샘플링 (GetMainLight)

## 작업 기록
