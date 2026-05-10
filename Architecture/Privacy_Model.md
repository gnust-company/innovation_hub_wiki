---
type: atomic-note
category: Architecture
related: ["User_Roles", "Permission_Matrix", "Database_Schema"]
tags: [architecture, privacy]
updated: 2026-04-28
---

# Privacy Model

## Kiến trúc Privacy (Decoupled)
```
Problem (visibility + shared_users)  ← Independent
  └── Room (visibility + shared_users)  ← Independent from Problem
       └── Idea  ← Inherits from Room
```

## Visibility Types
- **public**: Tất cả authenticated users xem được.
- **private**: Chỉ owner, shared users, và admin.

## Shared Users
- Shared users được lưu qua M2M association tables (`problem_shared_users`, `room_shared_users`).
- Khi thêm shared users → visibility tự chuyển thành private.

## Rules
- Problem và Room có privacy **độc lập**.
- Idea **kế thừa** privacy từ Room chứa nó.
- Admin **bypass tất cả** privacy checks.
- Comment/Reaction/Vote chỉ trên nội dung mà user có quyền xem.

## Entities có Privacy
- `problems` → visibility + shared_users (M2M)
- `rooms` → visibility + shared_users (M2M)

## API Handling
- List endpoints tự động filter theo quyền xem.
- GET by ID trả 403 nếu không có quyền.
- Xem [[API_Reference/Problem_Endpoints]], [[API_Reference/Room_Endpoints]].

## Mối liên hệ
- [[Authentication/User_Roles]] — Admin bypass.
- [[Authentication/Permission_Matrix]] — Chi tiết quyền.
- [[01_Problem_Feed/Problem_Privacy]] — Privacy trên Problem cụ thể.
