---
type: reference
category: API
related: ["MOC_API", "05_Dashboard/Statistics", "05_Dashboard/OKR_Tracking"]
tags: [api, dashboard, analytics]
updated: 2026-05-10
---

# Dashboard Endpoints

Base path: `/api/v1/dashboard`

Tất cả endpoints yêu cầu JWT Bearer token.

## `GET /dashboard/stats` — Tổng quan thống kê
- Query: `date_from`, `date_to` (YYYY-MM-DD, optional)
- Response:
  ```json
  {
    "total_problems": int,
    "total_ideas": int,
    "total_comments": int,
    "total_rooms": int,
    "interaction_rate": float,
    "resolved_problems": int,
    "problems_by_status": { "open": int, "discussing": int, "brainstorming": int, "solved": int, "closed": int },
    "ideas_by_status": { "draft": int, "refining": int, "reviewing": int, "submitted": int, "closed": int }
  }
  ```
- Privacy: Non-admin chỉ thấy stats của nội dung mình có quyền xem.

## `GET /dashboard/top-contributors` — Leaderboard đóng góp
- Query: `limit` (default 10, max 50), `date_from`, `date_to`
- Response: `[ { "user": UserResponseDTO, "problems_count": int, "ideas_count": int } ]`

## `GET /dashboard/recent-problems` — Problem gần đây
- Query: `limit` (default 5, max 20)
- Response: `ProblemResponseDTO[]` — đã enrich với reactions, comments, room info.

## `GET /dashboard/recent-ideas` — Idea nổi bật gần đây
- Query: `limit` (default 5, max 20)
- Response: `IdeaResponseDTO[]` — sorted by vote_avg → likes → (likes+comments) → created_at.
- Privacy-filtered theo room visibility.

## `GET /dashboard/problems-by-category` — Phân bố theo category
- Query: `date_from`, `date_to`
- Response: `{ "process": int, "technical": int, "people": int, "tools": int, "patent": int }`

## `GET /dashboard/activity-over-time` — Hoạt động theo ngày
- Query: `date_from`, `date_to` (default: 7 ngày gần nhất)
- Response: `[ { "date": "YYYY-MM-DD", "day_name": "Mon", "problems": int, "ideas": int, "comments": int } ]`

## `GET /dashboard/recent-activity` — Feed hoạt động gần đây
- Query: `limit` (default 20, max 50)
- Response: `[ { "id": "string", "type": "problem_created|idea_created|comment_added|...", "actor": {...}, "target_title": "...", "target_id": "...", "target_type": "...", "created_at": "...", "extra": {} } ]`
- Privacy-filtered: non-admin chỉ thấy activity của nội dung public hoặc được share.

## Mối liên hệ
- [[05_Dashboard/Statistics]] — Giải thích ý nghĩa các chỉ số.
- [[API_Reference/MOC_API]] — Full API index.
