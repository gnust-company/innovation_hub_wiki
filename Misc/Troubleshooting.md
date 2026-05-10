---
type: reference
category: Misc
related: ["MOC_Overview", "Changelog"]
tags: [troubleshooting]
updated: 2026-05-10
---

# Troubleshooting

## Login Issues

### "Not authenticated" (401)
- Token hết hạn → đăng nhập lại.
- Frontend tự refresh, nhưng nếu refresh token cũng hết hạn → login lại.
- Xem [[Authentication/JWT_Flow]].

### "Invalid token"
- Token bị sửa đổi hoặc không hợp lệ.
- Đăng xuất và đăng nhập lại.

## Permission Errors

### "Forbidden" (403)
- Không có quyền thực hiện action.
- Kiểm tra role: [[Authentication/User_Roles]], [[Authentication/Permission_Matrix]].
- Private content: bạn không trong danh sách shared users của resource.

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

## Chat Issues

### Chat không phản hồi hoặc lỗi "Agent unavailable"
- Agent BE container đang chạy không? `docker ps | grep agent`
- Kiểm tra health: `curl http://localhost:8000/health` (Agent BE port)
- `AGENT_BASE_URL` trong backend `.env` phải trỏ đúng đến Agent BE.

### SSE disconnect
- Kiểm tra network giữa Hub BE và Agent BE.
- Nginx config có thể buffer SSE — cần disable buffering cho `/api/chat/stream`.

### "Not authenticated" trong Chat
- Token hết hạn → đăng nhập lại.
- Chat endpoints yêu cầu JWT giống như các endpoints khác.

## Mối liên hệ
- [[Misc/Changelog]] — Phiên bản và thay đổi.
- [[Misc/Glossary]] — Thuật ngữ.
