---
id: T-001
title: 프로젝트 생성 및 기본 셋업
status: todo        # todo | in-progress | review | done | blocked
owner:
milestone: M1
priority: P0
depends_on: []
scope:
  - ProjectSettings/
  - Packages/
  - Assets/_Project/ (폴더·asmdef)
  - Assets/_Project/Rendering/
created: 2026-10-24
updated: 2026-10-24
tags: [task]
---

# 프로젝트 생성 및 기본 셋업

## 목표
Unity 6.3 URP 프로젝트를 만들고 폴더·asmdef·패키지·Git LFS를 준비해 두 세션이 작업을 시작할 수 있게 한다.

## 배경 / 관련 문서
- [[Setup_Checklist]]
- [[Git_Workflow]]

## 완료 조건
- [ ] Unity 6000.3 LTS, Universal 3D 템플릿으로 프로젝트 생성 (레포 루트 = 프로젝트 루트)
- [ ] Visible Meta Files / Force Text 설정 확인
- [ ] Input System, Cinemachine 3.x, Test Framework 패키지 설치
- [ ] CLAUDE.md 폴더 구조대로 폴더와 asmdef 5개 생성, 참조 설정
- [ ] 빈 EditMode 테스트 1개가 Test Runner에서 통과
- [ ] CLAUDE.md의 Unity 실행 경로 갱신
- [ ] Git LFS 설정 후 첫 커밋
- [ ] 문서 갱신

## 에디터 작업 (사용자)
- Unity Hub에서 프로젝트 생성
- Project Settings 설정, Package Manager에서 패키지 설치
- asmdef 생성(Create > Scripting > Assembly Definition) 또는 Claude Code가 만든 MenuItem 실행

## 학습 포인트
- asmdef = 언리얼 Module(.Build.cs)과 비슷한 컴파일 단위
- URP Asset / Renderer Data 구조
- Package Manager와 manifest.json

## 작업 기록
