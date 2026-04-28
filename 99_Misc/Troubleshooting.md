---
type: reference
category: Misc
related: ["MOC_Overview", "Changelog"]
tags: [troubleshooting]
updated: 2026-04-28
---

# Troubleshooting

## Login Issues

### "Not authenticated" (401)
- Token hết hạn → đăng nhập lại.
- Frontend tự refresh, nhưng nếu refresh token cũng hết hạn → login lại.
- Xem [[04_Authentication/JWT_Flow]].

### "Invalid token"
- Token bị sửa đổi hoặc không hợp lệ.
- Đăng xuất và đăng nhập lại.

## Permission Errors

### "Forbidden" (403)
- Không có quyền thực hiện action.
- Kiểm tra role: [[04_Authentication/User_Roles]], [[04_Authentication/Permission_Matrix]].
- Private content: bạn không trong shared_user_ids.

### "Not found" (404)
- Resource không tồn tại hoặc bạn không có quyền xem (trả 404 thay vì 403 để bảo mật).
- Kiểm tra lại ID.

## UI Issues

### Thay đổi không hiển thị ngay
- Đã fix: commit timing đã được optimize. Nếu vẫn gặp → F5.
- Nếu liên tục → báo admin.

### Upload avatar lỗi
- Chỉ hỗ trợ JPEG, PNG, WebP.
- Max 10MB.
- MinIO phải đang chạy.

## Development Issues

### Docker build fail
- `docker compose down && docker compose up -d --build`
- Kiểm tra port conflicts (8000, 5173/80, 5432, 9000/9001).

### Database migration fail
- `alembic upgrade head` trong backend container.
- Kiểm tra connection string.

## Mối liên hệ
- [[99_Misc/Changelog]] — Phiên bản và thay đổi.
- [[99_Misc/Glossary]] — Thuật ngữ.
