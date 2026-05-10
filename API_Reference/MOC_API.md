---
type: moc
category: API
related: ["MOC_For_Developers", "MOC_Architecture", "API_Contract_Summary"]
tags: [api, index]
updated: 2026-05-10
---

# MOC API

Full API reference cho Innovation Hub. Base path: `/api/v1`.

## Authentication
- [[API_Reference/Auth_Endpoints]] — Register, login, refresh, password change

## Core Resources
- [[API_Reference/Problem_Endpoints]] — CRUD + reactions + create room
- [[API_Reference/Idea_Endpoints]] — CRUD + votes + reactions
- [[API_Reference/Room_Endpoints]] — CRUD + link to problem
- [[API_Reference/Comment_Endpoints]] — CRUD (threaded, polymorphic target)
- [[API_Reference/Reactions_Endpoints]] — Toggle/delete reactions on problems & ideas

## Events
- [[API_Reference/Event_Endpoints]] — Events, teams, ideas, scoring, FAQ, awards, dashboard

## Other
- [[API_Reference/Dashboard_Endpoints]] — Stats, contributors, recent activity, charts
- [[API_Reference/Notifications_Endpoints]] — List, unread count, mark read
- [[API_Reference/Uploads_Endpoints]] — Avatar upload, file proxy
- [[API_Reference/Users_Endpoints]] — Profile, LLM key management, admin CRUD
- [[API_Reference/Chat_Endpoints]] — Chat sessions & messages

## Mối liên hệ
- Tổng hợp nhanh: [[Architecture/API_Contract_Summary]]
- Architecture: [[Architecture/MOC_Architecture]]
