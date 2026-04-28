---
type: reference
category: API
related: ["MOC_API", "Create_Brainstorm_Room", "Idea_Endpoints"]
tags: [api, rooms]
updated: 2026-04-28
---

# Room Endpoints

Base path: `/api/v1/rooms`

## GET /rooms
List rooms với filters.

**Query params:** `page`, `limit`, `status`, `search`, `problem_id`, `date_from`, `date_to`

**Response:** `200 OK` — `{ items, total, page, limit }`
Each item includes: creator, idea count, participant count.

## POST /rooms
Tạo room (độc lập). Auth required.

**Request body:**
```json
{
  "name": "string (required)",
  "description": "string?",
  "problem_id": "uuid?",
  "visibility": "public|private?",
  "shared_user_ids": ["uuid?"]
}
```

**Response:** `201 Created` — RoomResponseDTO

## GET /rooms/{room_id}
Chi tiết room.

## PATCH /rooms/{room_id}
Update room. Creator or admin.

**Fields:** name, description, status (active/archived), visibility, shared_user_ids

## DELETE /rooms/{room_id}
Delete room. Creator or admin. `204 No Content`.

## Create Room from Problem
`POST /api/v1/problems/{problem_id}/rooms` — Xem [[07_API_Reference/Problem_Endpoints]].

## Mối liên hệ
- [[02_Idea_Lab/Create_Brainstorm_Room]] — User guide.
- [[07_API_Reference/Idea_Endpoints]] — Ideas trong room.
- [[02_Idea_Lab/Room_vs_Problem_Link]] — Problem linkage.
