---
type: atomic-note
category: Architecture
related: ["MOC_API", "MOC_Architecture", "MOC_For_Developers"]
tags: [architecture, api]
updated: 2026-04-28
---

# API Contract Summary

## Base URL
`/api/v1`

## Endpoint Summary by Module

| Module | Endpoints | Auth |
|--------|-----------|------|
| Auth | 5 (register, login, me, refresh, password) | Mixed |
| Users | 8 (CRUD, stats, reset-password) | Required/Admin |
| Problems | 6 (CRUD + create room) | Mixed |
| Ideas | 7 (CRUD + votes) | Mixed |
| Rooms | 5 (CRUD) | Mixed |
| Comments | 4 (CRUD) | Mixed |
| Reactions | 4 (toggle/delete for problem & idea) | Required |
| Notifications | 4 (list, count, mark read) | Required |
| Dashboard | 7 (stats, charts, feeds) | Required |
| Events | 6 (CRUD + close + assignments) | Mixed/Admin |
| Event Teams | 9 (CRUD + join + assign) | Mixed |
| Event Ideas | 6 (CRUD + from-room) | Mixed |
| Event Scoring | 4 (criteria + scores) | Mixed |
| Event FAQ | 4 (CRUD) | Mixed |
| Event Dashboard | 2 (leaderboards) | Required |
| Event Awards | 6 (CRUD + teams) | Mixed/Admin |
| Uploads | 2 (avatar + file) | Mixed |

**Total: ~85 endpoints**

## Chi tiết
- Xem từng module: [[07_API_Reference/Auth_Endpoints]], [[07_API_Reference/Problem_Endpoints]], [[07_API_Reference/Idea_Endpoints]], [[07_API_Reference/Event_Endpoints]].
- Xem đầy đủ: [[07_API_Reference/MOC_API]].

## Mối liên hệ
- [[07_API_Reference/MOC_API]] — Full API reference.
- [[06_Architecture/MOC_Architecture]] — Architecture overview.
