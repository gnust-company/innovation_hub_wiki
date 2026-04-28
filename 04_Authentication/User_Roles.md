---
type: atomic-note
category: Authentication
related: ["Permission_Matrix", "JWT_Flow", "Privacy_Model"]
tags: [auth, roles]
updated: 2026-04-28
---

# User Roles

## System Roles

### Member
- Role mặc định khi đăng ký.
- Quyền:
  - Tạo problems, ideas, rooms, comments, reactions, votes.
  - Tham gia events (tạo/join teams, submit ideas).
  - Xem dashboard cá nhân.
  - Sửa/xóa nội dung của mình.

### Admin
- Quyền đầy đủ:
  - Tất cả quyền của Member.
  - Quản lý users (sửa role, deactivate, reset password).
  - Tạo/quản lý events, scoring criteria, awards.
  - Pin/close problems.
  - Xem mọi nội dung (bypass privacy).
  - Xem analytics dashboard.

### Team Lead (Event-specific)
- Không phải system role — là vai trò trong event team.
- Quyền trong event:
  - Approve/reject join requests.
  - Disband team.
  - Submit ideas cho team.
  - Chấm điểm team khác (nếu được assign).
  - Transfer leadership.
- Xem [[03_Events/Team_Formation]].

## Mối liên hệ
- [[04_Authentication/Permission_Matrix]] — Chi tiết quyền từng role.
- [[06_Architecture/Privacy_Model]] — Admin bypass privacy.
- [[04_Authentication/JWT_Flow]] — Role xác định khi login.
