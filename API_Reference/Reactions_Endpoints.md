---
type: reference
category: API
related: ["MOC_API", "Problem_Endpoints", "Idea_Endpoints", "01_Problem_Feed/Reactions"]
tags: [api, reactions]
updated: 2026-05-10
---

# Reactions Endpoints

Reactions API cho phép users thể hiện cảm xúc (like, dislike, insight) trên problems và ideas.

Base path: `/api/v1` (reactions được nested dưới problems và ideas).

## Authentication
Yêu cầu JWT Bearer token.

---

## Problem Reactions

Base: `/api/v1/problems/{problem_id}/reactions`

### `POST /problems/{problem_id}/reactions` — Toggle reaction
- Body: `{ "type": "like" | "dislike" | "insight" }`
- Logic:
  - Nếu user chưa có reaction → tạo mới.
  - Nếu user đã có cùng type → xóa reaction (return `204 No Content`).
  - Nếu user đã có khác type → cập nhật sang type mới.
- Response: `ReactionResponseDTO` hoặc `204 No Content` (nếu toggle off).

### `DELETE /problems/{problem_id}/reactions` — Remove reaction
- Xóa reaction hiện tại của user trên problem.
- Response: `204 No Content`.

---

## Idea Reactions

Base: `/api/v1/ideas/{idea_id}/reactions`

### `POST /ideas/{idea_id}/reactions` — Toggle reaction
- Body: `{ "type": "like" | "dislike" | "insight" }`
- Logic tương tự Problem Reactions.
- Response: `ReactionResponseDTO` hoặc `204 No Content`.

### `DELETE /ideas/{idea_id}/reactions` — Remove reaction
- Xóa reaction hiện tại của user trên idea.
- Response: `204 No Content`.

---

## Data Models

### ReactionResponseDTO
```json
{
  "id": "uuid",
  "target_id": "uuid",
  "target_type": "problem | idea",
  "type": "like | dislike | insight",
  "user_id": "uuid",
  "created_at": "datetime"
}
```

### ReactionCountsDTO
```json
{
  "target_id": "uuid",
  "target_type": "problem | idea",
  "like": 10,
  "dislike": 1,
  "insight": 5,
  "total": 16
}
```

---

## Notifications
- Khi có reaction mới, owner của target nhận notification `reaction_added`.

## Mối liên hệ
- [[API_Reference/Problem_Endpoints]] — Reactions nested dưới problems.
- [[API_Reference/Idea_Endpoints]] — Reactions nested dưới ideas.
- [[01_Problem_Feed/Reactions]] — Giải thích ý nghĩa từng reaction type.
