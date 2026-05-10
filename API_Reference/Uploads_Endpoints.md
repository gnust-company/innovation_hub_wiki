---
type: reference
category: API
related: ["MOC_API", "User_Guide/Quick_Start"]
tags: [api, uploads, storage]
updated: 2026-05-10
---

# Uploads Endpoints

Base path: `/api/v1/uploads`

## `POST /uploads/avatar` — Upload avatar
- Auth: Required.
- Content-Type: `multipart/form-data`
- File restrictions: JPEG, PNG, WebP. Max 10MB.
- Logic: Tự động xóa avatar cũ của user trước khi upload mới.
- Response: `{ "url": "string" }` — URL của avatar mới (có cache-bust timestamp).

## `GET /uploads/file/{object_name}` — Proxy serve file
- Auth: Public (không cần token).
- `object_name` là full path trong MinIO bucket, ví dụ: `users/{uuid}/avatar.jpg`
- Response: File stream với `Cache-Control: public, max-age=31536000, immutable`.
- Mục đích: Tránh expose MinIO port trực tiếp ra ngoài.

## Storage Backend
- **MinIO** (S3-compatible), bucket mặc định: `avatars`.
- File được lưu theo prefix: `users/{user_id}/avatar.{ext}`.

## Mối liên hệ
- [[API_Reference/MOC_API]] — Full API index.
- [[Architecture/FastAPI_Structure]] — Cấu hình MinIO trong backend.
