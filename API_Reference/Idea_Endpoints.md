---
type: reference
category: API
related: ["MOC_API", "Kanban_Board", "Star_Voting"]
tags: [api, ideas]
updated: 2026-04-28
---

# Idea Endpoints

Base path: `/api/v1/ideas`

## GET /ideas
List ideas với filters.

**Query params:** `page`, `limit`, `room_id`, `status`, `search`, `author_id`, `sort`

**Response:** `200 OK` — `{ items, total, page, limit }`
Each item includes: author, vote averages, comment counts, user's vote/reaction.

## POST /ideas
Tạo idea mới. Auth required.

**Request body:**
```json
{
  "room_id": "uuid (required)",
  "title": "string (required)",
  "description": "TipTap JSON object (required)",
  "summary": "string?"
}
```

**Response:** `201 Created` — IdeaResponseDTO

## GET /ideas/{idea_id}
Chi tiết idea.

## PATCH /ideas/{idea_id}
Update idea. Owner or admin.

**Fields:** title, description, summary, status, is_pinned

## DELETE /ideas/{idea_id}
Delete idea. Owner or admin. `204 No Content`.

## Votes
- `POST /ideas/{id}/votes` — Vote (body: `{ "stars": 1-5 }`). Response: VoteResponseDTO
- `DELETE /ideas/{id}/votes` — Remove vote. `204 No Content`.

## Reactions
- `POST /ideas/{id}/reactions` — Toggle reaction
- `DELETE /ideas/{id}/reactions` — Remove reaction

## Mối liên hệ
- [[02_Idea_Lab/Kanban_Board]] — UI cho ideas.
- [[02_Idea_Lab/Star_Voting]] — Vote system.
- [[02_Idea_Lab/Idea_Status_Workflow]] — Status transitions.
