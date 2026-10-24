---
id: T-007
title: 그림자 → 2D 그림 전환 연출 (프로토타입)
status: todo        # todo | in-progress | review | done | blocked
owner:
milestone: M1
priority: P2
depends_on: [T-004]
scope:
  - Assets/_Project/Scripts/Runtime/Shadow/ShadowReveal.cs
  - Assets/_Project/Rendering/Shaders/ShadowReveal/
  - Assets/_Project/Scenes/Sandbox/T-007_Reveal.unity
created: 2026-10-24
updated: 2026-10-24
tags: [task]
---

# 그림자 → 2D 그림 전환 연출 (프로토타입)

## 목표
일치한 그림자 자리에 2D 일러스트가 번지듯 나타나는 연출을 만든다 (판정과 분리된 단독 프로토타입).

## 배경 / 관련 문서
- [[Architecture]]

## 완료 조건
- [ ] 벽에 일러스트를 표시하는 방식 결정: URP Decal Projector vs 벽 위 쿼드 (비교 후 DevLog 기록)
- [ ] Shader Graph 디졸브(노이즈 마스크) 전환
- [ ] `ShadowReveal.Play()` 하나로 호출 가능 (Awaitable 또는 코루틴)
- [ ] 문서 갱신

## 에디터 작업 (사용자)
- Shader Graph 편집, 테스트용 일러스트 이미지 임포트

## 학습 포인트
- Shader Graph (Material Editor 대응)
- URP Decal Renderer Feature
- Awaitable (Unity 6+) vs 코루틴

## 작업 기록
