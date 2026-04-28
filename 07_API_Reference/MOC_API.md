---
type: moc
category: API
related: ["MOC_For_Developers", "MOC_Architecture", "API_Contract_Summary"]
tags: [api, index]
updated: 2026-04-28
---

# MOC API

Full API reference cho Innovation Hub. Base path: `/api/v1`.

## Authentication
- [[07_API_Reference/Auth_Endpoints]] — Register, login, refresh, password change

## Core Resources
- [[07_API_Reference/Problem_Endpoints]] — CRUD + reactions + create room
- [[07_API_Reference/Idea_Endpoints]] — CRUD + votes + reactions
- [[07_API_Reference/Room_Endpoints]] — CRUD + link to problem
- [[07_API_Reference/Comment_Endpoints]] — CRUD (threaded, polymorphic target)

## Events
- [[07_API_Reference/Event_Endpoints]] — Events, teams, ideas, scoring, FAQ, awards, dashboard

## Other
- Dashboard endpoints: Xem [[05_Dashboard/Statistics]]
- Notification endpoints: Xem [[06_Architecture/Notification_System]]
- Upload endpoints: Xem [[06_Architecture/TipTap_Integration]]

## Mối liên hệ
- Tổng hợp nhanh: [[06_Architecture/API_Contract_Summary]]
- Architecture: [[06_Architecture/MOC_Architecture]]
