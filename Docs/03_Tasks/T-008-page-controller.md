---
id: T-008
title: 페이지 진행 상태와 완성 이벤트
status: todo        # todo | in-progress | review | done | blocked
owner:
milestone: M1
priority: P1
depends_on: [T-005]
scope:
  - Assets/_Project/Scripts/Core/Page/
  - Assets/_Project/Scripts/Runtime/Book/PageController.cs
  - Assets/_Project/Data/Pages/
  - Assets/_Project/Tests/EditMode/
created: 2026-10-24
updated: 2026-10-24
tags: [task]
---

# 페이지 진행 상태와 완성 이벤트

## 목표
페이지의 모든 ShadowTarget이 일치하면 PageComplete 이벤트를 내고, 테스트 페이지 1장으로 M1을 완성한다.

## 배경 / 관련 문서
- [[Architecture]]
- [[Project_Overview]]

## 완료 조건
- [ ] `PageProgress` (Core): 목표 목록, 완료 처리, 전체 완료 판정 + EditMode 테스트
- [ ] `PageData` SO, `PageController` (Runtime): ShadowTarget 구독 → ShadowReveal 재생 → 전부 완료 시 PageComplete
- [ ] `Scenes/Pages/Page_Test01.unity`: 오브젝트 2개, 그림자 2개로 M1 완료 기준 충족
- [ ] 문서 갱신

## 에디터 작업 (사용자)
- Page_Test01 씬 조립 (T-002~T-007 프리팹 사용)

## 학습 포인트
- 이벤트 구독/해제 위치 (OnEnable/OnDisable)
- 씬 간 참조 대신 SO 데이터로 연결하는 이유

## 작업 기록
