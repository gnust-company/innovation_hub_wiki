---
type: guide
category: User Guide
related: ["Quick_Start", "Auth_Endpoints", "MOC_User_Guide"]
tags: [user-guide, how-to]
updated: 2026-04-28
---

# Change Password

## Các bước
1. Vào **Settings** (`/settings`).
2. Tìm section "Đổi mật khẩu".
3. Nhập:
   - **Mật khẩu hiện tại**
   - **Mật khẩu mới**
   - **Xác nhận mật khẩu mới**
4. Click "Đổi mật khẩu".

## Lưu ý
- Mật khẩu mới phải khác mật khẩu cũ.
- Sau khi đổi, không cần đăng nhập lại (token vẫn valid).

## Admin Reset Password
- Admin có thể reset password cho user khác qua admin panel.
- Hệ thống tạo password mới tự động.
- Xem [[09_Admin_Guide/Manage_User]].

## API
- `PUT /api/v1/auth/password` — Đổi password.
- `POST /api/v1/users/{id}/reset-password` — Admin reset (admin only).
- Xem [[07_API_Reference/Auth_Endpoints]].

## Mối liên hệ
- [[08_User_Guide/Quick_Start]] — Bắt đầu sử dụng.
- [[09_Admin_Guide/Manage_User]] — Admin quản lý users.
