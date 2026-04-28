---
type: reference
category: API
related: ["MOC_API", "Comment_Threading"]
tags: [api, comments]
updated: 2026-04-28
---

# Comment Endpoints

Base path: `/api/v1/comments`

## Target Types
Comments hỗ trợ 3 target types: `problem`, `idea`, `event_idea`.

## GET /comments
List comments cho target.

**Query params:** `target_id`, `target_type` (problem|idea|event_idea), `page`, `limit`

**Response:** `200 OK` — `{ items, total, page, limit }`

## POST /comments
Tạo comment hoặc reply. Auth required.

**Request body:**
```json
{
  "target_id": "uuid (required)",
  "target_type": "problem|idea|event_idea (required)",
  "content": "string (required)",
  "parent_id": "uuid? (for replies)"
}
```

**Response:** `201 Created` — CommentResponseDTO

## PATCH /comments/{comment_id}
Update comment. Author only.

**Request body:** `{ "content": "string" }`

## DELETE /comments/{comment_id}
Delete comment. Author or admin. `204 No Content`.

## Threading
- Root comments: `parent_id = null`, sorted by created_at desc.
- Replies: `parent_id` set, sorted by created_at asc.
- Xem [[01_Problem_Feed/Comment_Threading]].

## Mối liên hệ
- [[01_Problem_Feed/Comment_Threading]] — Cách threading hoạt động.
