---
type: moc
category: Index
related: ["MOC_Overview", "MOC_For_End_Users", "MOC_Architecture"]
tags: [index, developer]
updated: 2026-04-28
---

# MOC For Developers

Technical documentation cho developers làm việc với Innovation Hub.

## Architecture
- [[06_Architecture/Clean_Architecture]] — 3-layer separation (Domain → Application → Infrastructure)
- [[06_Architecture/FastAPI_Structure]] — Backend folder structure và conventions
- [[06_Architecture/Database_Schema]] — Entity-Relationship, tables, fields
- [[06_Architecture/API_Contract_Summary]] — Tổng hợp endpoints chính

## API Reference
- [[07_API_Reference/MOC_API]] — Index tất cả API docs
- [[07_API_Reference/Auth_Endpoints]] — Đăng nhập, đăng ký, JWT
- [[07_API_Reference/Problem_Endpoints]] — CRUD problems, reactions
- [[07_API_Reference/Idea_Endpoints]] — CRUD ideas, voting
- [[07_API_Reference/Event_Endpoints]] — Events, teams, ideas, scoring, awards

## Authentication & Authorization
- [[04_Authentication/JWT_Flow]] — Access token + refresh token lifecycle
- [[04_Authentication/User_Roles]] — member vs admin
- [[04_Authentication/Permission_Matrix]] — Chi tiết quyền cho từng role

## Key Concepts
- [[06_Architecture/TipTap_Integration]] — Rich text editor + JSONB storage
- [[06_Architecture/Privacy_Model]] — Public/Private visibility + shared users
- [[06_Architecture/Notification_System]] — Triggers, types, delivery

## Development Setup
- Docker Compose: `docker compose up -d --build`
- Backend chạy ở port 8000, Frontend ở port 5173 (dev) hoặc 80 (production)
- MinIO console ở port 9001
- Xem [[99_Misc/Troubleshooting]] nếu gặp vấn đề
