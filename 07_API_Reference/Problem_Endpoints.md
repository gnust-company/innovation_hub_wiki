---
type: reference
category: API
related: ["MOC_API", "Create_Problem", "Room_Endpoints"]
tags: [api, problems]
updated: 2026-04-28
---

# Problem Endpoints

Base path: `/api/v1/problems`

## Authentication
Tất cả endpoints yêu cầu Bearer token (trừ GET list/detail có thể public).
Xem [[07_API_Reference/Auth_Endpoints]].

## GET /problems
List problems với filters.

**Query params:** `page`, `limit`, `category`, `status`, `search`, `author_id`, `is_private`, `sort`, `date_from`, `date_to`

**Response:** `200 OK` — `{ items, total, page, limit }`

## POST /problems
Tạo problem mới. Auth required.

**Request body:**
```json
{
  "title": "string (max 200)",
  "summary": "string?",
  "content": "TipTap JSON object",
  "category": "process|technical|people|tools|patent",
  "visibility": "public|private?",
  "shared_user_ids": ["uuid?"]
}
```

**Response:** `201 Created` — ProblemResponseDTO

## GET /problems/{problem_id}
Chi tiết problem. Response includes author, reaction counts, room linkage, user's reaction.

## PATCH /problems/{problem_id}
Update problem. Owner or admin only.

**Fields:** title, summary, content, category, status, visibility, shared_user_ids

## DELETE /problems/{problem_id}
Delete problem. Owner or admin only. `204 No Content`.

## POST /problems/{problem_id}/rooms
Tạo room từ problem. Xem [[02_Idea_Lab/Create_Brainstorm_Room]].

## Reactions
- `POST /problems/{id}/reactions` — Toggle reaction (body: `{ type: "like|dislike|insight" }`)
- `DELETE /problems/{id}/reactions` — Remove reaction

## Mối liên hệ
- [[01_Problem_Feed/Create_Problem]] — User guide.
- [[07_API_Reference/Room_Endpoints]] — Rooms linked to problems.
