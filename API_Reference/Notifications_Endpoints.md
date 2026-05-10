---
type: reference
category: API
related: ["MOC_API", "Architecture/Notification_System"]
tags: [api, notifications]
updated: 2026-05-10
---

# Notifications Endpoints

Base path: `/api/v1/notifications`

Tất cả endpoints yêu cầu JWT Bearer token.

## `GET /notifications` — Danh sách thông báo
- Query: `page` (default 1), `limit` (default 5), `unread_only` (default false)
- Response:
  ```json
  {
    "items": [NotificationObject],
    "total": int,
    "page": int,
    "limit": int,
    "unread_count": int
  }
  ```

## `GET /notifications/unread-count` — Số thông báo chưa đọc
- Dùng cho badge hiển thị số trên icon chuông.
- Response: `{ "count": int }`

## `PATCH /notifications/read-all` — Đánh dấu tất cả đã đọc
- Response: `{ "updated": int }` — số bản ghi đã cập nhật.

## `PATCH /notifications/{id}/read` — Đánh dấu 1 thông báo đã đọc
- Chỉ owner của notification mới thực hiện được.
- Response: `{ "success": true }`

## NotificationObject
```json
{
  "id": "uuid",
  "user_id": "uuid",
  "actor_id": "uuid",
  "actor": {
    "id": "uuid",
    "username": "string",
    "full_name": "string?",
    "avatar_url": "string?"
  },
  "type": "comment_added | reaction_added | vote_added | status_changed | ...",
  "target_id": "uuid",
  "target_type": "problem | idea | event_idea | event_team | ...",
  "target_title": "string",
  "action_detail": "string?",
  "reference_id": "uuid?",
  "is_read": true | false,
  "created_at": "datetime"
}
```

## Mối liên hệ
- [[Architecture/Notification_System]] — Các loại notification và trigger.
- [[API_Reference/MOC_API]] — Full API index.
