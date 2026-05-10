---
type: reference
category: API
related: ["MOC_API", "Auth_Endpoints", "Permission_Matrix"]
tags: [api, users]
updated: 2026-05-10
---

# Users Endpoints

Base path: `/api/v1/users`

Tất cả endpoints yêu cầu JWT Bearer token (trừ khi có ghi chú khác).

## Current User

### `GET /users/me` — Lấy thông tin user hiện tại
- Response: `UserResponseDTO`

### `PATCH /users/me` — Cập nhật profile
- Body: `{ "full_name": "string?", "team": "string?", "avatar_url": "string?" }`
- Response: `UserResponseDTO`

## LLM API Key Management

### `PUT /users/me/llm-api-key` — Lưu & validate API key
- Body: `{ "llm_api_key": "string (8-255 chars)" }`
- Logic: Lưu key vào DB, rồi gọi Agent BE validate.
- Response: `{ "saved": true, "valid": true }` hoặc `{ "saved": true, "valid": false, "reason": "..." }`

### `DELETE /users/me/llm-api-key` — Xóa API key
- Status: `204 No Content`

### `GET /users/me/llm-api-key` — Kiểm tra key đã cấu hình chưa
- Response: `{ "has_key": true | false }`

### `POST /users/me/validate-llm-key` — Validate key hiện tại
- Response: `{ "valid": true }` hoặc `{ "valid": false, "error": "..." }`

## User Management (Admin)

### `GET /users` — Danh sách users (paginated)
- Query: `page`, `limit`, `role`, `team`, `search`, `is_active`
- Response: `UserListResponseDTO`

### `GET /users/{id}` — Xem user theo ID
- Response: `UserResponseDTO`

### `GET /users/{id}/stats` — Thống kê hoạt động user
- Response: `{ "problems_count": int, "ideas_count": int, "comments_count": int, "rooms_count": int }`

### `PATCH /users/{id}` — Admin cập nhật user
- Body: `{ "full_name": "string?", "team": "string?", "role": "member|admin", "is_active": true|false }`
- Yêu cầu: Admin role.
- Response: `UserResponseDTO`

### `DELETE /users/{id}` — Admin xóa user
- Yêu cầu: Admin role. Không thể tự xóa chính mình.
- Status: `204 No Content`

### `POST /users/{id}/reset-password` — Admin reset mật khẩu
- Yêu cầu: Admin role.
- Response: `{ "new_password": "random-string" }`

## Mối liên hệ
- [[API_Reference/MOC_API]] — Full API index.
- [[Authentication/Permission_Matrix]] — Phân quyền chi tiết.
- [[Authentication/User_Roles]] — Vai trò member / admin.
