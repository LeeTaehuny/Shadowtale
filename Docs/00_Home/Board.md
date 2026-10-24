---
tags: [board]
---

# 📋 Task Board
> Dataview 자동 생성. 이 파일은 직접 수정하지 않는다 (병합 충돌 방지).

## 진행 중
```dataview
TABLE owner, milestone, updated FROM "03_Tasks" WHERE status = "in-progress" SORT updated DESC
```

## 리뷰 / 막힘
```dataview
TABLE status, owner FROM "03_Tasks" WHERE status = "review" OR status = "blocked"
```

## 할 일
```dataview
TABLE priority, milestone, depends_on FROM "03_Tasks" WHERE status = "todo" SORT priority ASC
```

## 완료
```dataview
TABLE milestone, updated FROM "03_Tasks" WHERE status = "done" SORT updated DESC LIMIT 20
```
