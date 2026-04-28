---
type: guide
category: Admin Guide
related: ["MOC_Admin", "User_Roles", "Auth_Endpoints"]
tags: [admin, users]
updated: 2026-04-28
---

# Manage User

## Truy cập
Vào **Admin → Users** (`/admin/users`). Chỉ admin mới truy cập được.

## Danh sách Users
- Xem tất cả users.
- Filter: role, team, search, active status.
- Pagination.

## Sửa User
1. Click vào user trong danh sách.
2. Sửa: email, full_name, team, role (member ↔ admin), is_active.
3. Click "Lưu".

## Deactivate User
- Toggle `is_active` = false.
- User không đăng nhập được nhưng data vẫn giữ.

## Reset Password
1. Click "Reset Password" trên user.
2. Hệ thống tạo password mới.
3. Password mới hiển thị 1 lần — copy cho user.

## API
- `GET /api/v1/users` — List users
- `PATCH /api/v1/users/{id}` — Update user
- `POST /api/v1/users/{id}/reset-password` — Reset password
- `DELETE /api/v1/users/{id}` — Delete user
- Xem [[07_API_Reference/Auth_Endpoints]].

## Mối liên hệ
- [[09_Admin_Guide/MOC_Admin]] — Tổng quan Admin.
- [[04_Authentication/User_Roles]] — Role definitions.
