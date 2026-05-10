---
type: atomic-note
category: Architecture
related: ["MOC_API", "MOC_Architecture", "MOC_For_Developers"]
tags: [architecture, api]
updated: 2026-05-10
---

# API Contract Summary

## Base URL
`/api/v1`

## Endpoint Summary by Module

| Module | Endpoints | Auth |
|--------|-----------|------|
| Auth | 5 (register, login, me, refresh, password) | Mixed |
| Users | 12 (CRUD, stats, reset-password, LLM key mgmt) | Required/Admin |
| Problems | 6 (CRUD + create room) | Mixed |
| Ideas | 7 (CRUD + votes) | Mixed |
| Rooms | 5 (CRUD) | Mixed |
| Comments | 4 (CRUD) | Mixed |
| Reactions | 4 (toggle/delete for problem & idea) | Required |
| Notifications | 4 (list, count, mark read) | Required |
| Dashboard | 7 (stats, charts, feeds) | Required |
| Events | 7 (CRUD + close + assignments) | Mixed/Admin |
| Event Teams | 10 (CRUD + join + leave + assign) | Mixed |
| Event Ideas | 6 (CRUD + from-room) | Mixed |
| Event Scoring | 4 (criteria + scores) | Mixed |
| Event FAQ | 4 (CRUD) | Mixed |
| Event Dashboard | 2 (leaderboards) | Required |
| Event Awards | 6 (CRUD + teams) | Mixed/Admin |
| Uploads | 2 (avatar + file) | Mixed |
| Chat | 7 (sessions CRUD + messages + key-help-url) | Required |

**Total: ~95 logical endpoints**

## Chi tiết
- Xem từng module: [[API_Reference/Auth_Endpoints]], [[API_Reference/Problem_Endpoints]], [[API_Reference/Idea_Endpoints]], [[API_Reference/Event_Endpoints]], [[API_Reference/Chat_Endpoints]].
- Xem đầy đủ: [[API_Reference/MOC_API]].

## Mối liên hệ
- [[API_Reference/MOC_API]] — Full API reference.
- [[Architecture/MOC_Architecture]] — Architecture overview.
