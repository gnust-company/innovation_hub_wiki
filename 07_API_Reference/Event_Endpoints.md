---
type: reference
category: API
related: ["MOC_API", "MOC_Events", "Team_Formation"]
tags: [api, events]
updated: 2026-04-28
---

# Event Endpoints

Base path: `/api/v1/events`

## Events CRUD
- `POST /events` — Create (admin). Body: `{ title, description?, introduction_type?, embed_url?, status?, start_date?, end_date? }`
- `GET /events` — List. Query: `status?, page, limit`
- `GET /events/{id}` — Detail
- `PATCH /events/{id}` — Update (admin)
- `PATCH /events/{id}/close` — Close (admin)
- `DELETE /events/{id}` — Delete (admin)

## Teams (`/events/{id}/teams`)
- `POST /events/{id}/teams` — Create team. Body: `{ name, slogan? }`
- `GET /events/{id}/teams` — List teams
- `GET /events/{id}/teams/{team_id}/members` — List members
- `POST /events/{id}/teams/{team_id}/join` — Request join
- `PATCH /events/{id}/teams/{team_id}/members/{user_id}` — Approve/reject. Body: `{ status: "active"|"rejected" }`
- `DELETE /events/{id}/teams/{team_id}` — Disband (leader)
- `DELETE /events/{id}/teams/{team_id}/members/me` — Leave team
- `PATCH /events/{id}/teams/{team_id}/transfer-lead` — Body: `{ new_leader_id }`
- `PATCH /events/{id}/teams/{team_id}/assign-review` — Body: `{ target_team_id? }` (admin)
- `GET /events/{id}/assignments` — View scoring assignments

## Ideas (`/events/{id}/ideas`)
- `POST /events/{id}/ideas` — Manual submit. Body: `{ title, user_problem?, user_scenarios?, user_expectation?, research?, solution }`
- `POST /events/{id}/ideas/from-room` — Import from room. Body: `{ room_id, idea_id }`
- `GET /events/{id}/ideas` — List. Query: `team_id?, sort?, page, limit`
- `GET /events/{id}/ideas/{idea_id}` — Detail
- `PATCH /events/{id}/ideas/{idea_id}` — Update
- `DELETE /events/{id}/ideas/{idea_id}` — Delete

## Scoring
- `GET /events/{id}/criteria` — List criteria
- `POST /events/{id}/ideas/{idea_id}/scores` — Submit score. Body: `{ criteria_scores: {id: score}, criteria_notes? }`
- `PUT /events/{id}/ideas/{idea_id}/scores` — Update score
- `GET /events/{id}/ideas/{idea_id}/scores` — List scores

## FAQ
- `POST /events/{id}/faqs` — Create FAQ
- `GET /events/{id}/faqs` — List FAQs (public)
- `PATCH /events/{id}/faqs/{faq_id}` — Update
- `DELETE /events/{id}/faqs/{faq_id}` — Delete

## Awards
- `POST /events/{id}/awards` — Create award (admin). Body: `{ name, rank_order }`
- `GET /events/{id}/awards` — List awards
- `PATCH /events/{id}/awards/{award_id}` — Update
- `DELETE /events/{id}/awards/{award_id}` — Delete
- `POST /events/{id}/awards/{award_id}/teams` — Add team. Body: `{ team_id }`
- `DELETE /events/{id}/awards/{award_id}/teams/{team_id}` — Remove team

## Dashboard
- `GET /events/{id}/dashboard/ideas` — Idea leaderboard. Query: `team_id?`
- `GET /events/{id}/dashboard/teams` — Team leaderboard

## Mối liên hệ
- [[03_Events/MOC_Events]] — Tổng quan Events feature.
- [[03_Events/Team_Formation]] — Teams guide.
- [[03_Events/Scoring_System]] — Scoring guide.
