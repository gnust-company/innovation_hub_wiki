---
type: reference
category: API
related: ["MOC_API", "Auth_Endpoints", "Chat_Integration"]
tags: [api, chat]
updated: 2026-05-10
---

# Chat Endpoints

Base path: `/api/v1/chat` (nằm trong API v1 router, cùng prefix với các module khác).

Tất cả endpoints yêu cầu JWT Bearer token.

## Sessions

### `POST /chat/sessions` — Tạo session
- Body: `{ "title": "string (max 200)" }`
- Response: SessionObject

### `GET /chat/sessions` — Danh sách sessions
- Chỉ trả về sessions của current user, sort theo `updated_at DESC`.
- Response: `SessionObject[]`

### `PATCH /chat/sessions/{id}` — Đổi tên session
- Body: `{ "title": "string (max 200)" }`
- Response: SessionObject

### `DELETE /chat/sessions/{id}` — Xóa session
- Chỉ owner mới xóa được. Cascade xóa messages.
- Status: 204 No Content

## Messages

### `GET /chat/sessions/{id}/messages` — Lịch sử tin nhắn
- Chỉ owner mới xem. Sort `created_at ASC`.
- Response: `MessageObject[]`

### `POST /chat/sessions/{id}/message` — Gửi tin nhắn
- Body: `{ "content": "string" }`
- Logic:
  1. Validate session thuộc current user.
  2. Lưu user message vào DB (`role = "user"`).
  3. Proxy SSE stream đến Agent BE.
  4. Lưu assistant message khi stream hoàn tành (`role = "assistant"`).
- Response: `StreamingResponse` (SSE — Server-Sent Events). Each event: `data: {"type": "token|tool_call|sources|done|error", ...}\n\n`.

### `GET /chat/key-help-url` — URL hướng dẫn lấy LLM API Key
- **Không yêu cầu auth**.
- Trả về URL hướng dẫn user cấu hình LLM API key.
- Response: `{ "url": "string" }`

## Data Models

### SessionObject
```json
{
  "id": "uuid",
  "title": "string",
  "created_at": "datetime",
  "updated_at": "datetime | null"
}
```

### MessageObject
```json
{
  "id": "uuid",
  "role": "user | assistant",
  "content": "string",
  "sources": "JSONB | null",
  "created_at": "datetime"
}
```

> `sources`: Wiki files mà Agent BE đã đọc để trả lời (chỉ có trên assistant messages).

## Mối liên hệ
- [[API_Reference/MOC_API]] — Full API index.
- [[Architecture/Chat_Integration]] — SSE proxy flow và Agent BE integration.
- [[Authentication/Permission_Matrix]] — Chat permissions.
