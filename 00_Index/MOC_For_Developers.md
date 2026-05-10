---
type: moc
category: Index
related: ["MOC_Overview", "MOC_For_End_Users", "MOC_Architecture"]
tags: [index, developer]
updated: 2026-05-10
---

# MOC For Developers

Technical documentation cho developers làm việc với Innovation Hub.

## Architecture
- [[Architecture/Clean_Architecture]] — 3-layer separation (Domain → Application → Infrastructure)
- [[Architecture/FastAPI_Structure]] — Backend folder structure và conventions
- [[Architecture/Database_Schema]] — Entity-Relationship, tables, fields
- [[Architecture/API_Contract_Summary]] — Tổng hợp endpoints chính
- [[Architecture/Chat_Integration]] — ChatBot SSE proxy và Agent BE integration

## API Reference
- [[API_Reference/MOC_API]] — Index tất cả API docs
- [[API_Reference/Auth_Endpoints]] — Đăng nhập, đăng ký, JWT
- [[API_Reference/Problem_Endpoints]] — CRUD problems, reactions
- [[API_Reference/Idea_Endpoints]] — CRUD ideas, voting
- [[API_Reference/Event_Endpoints]] — Events, teams, ideas, scoring, awards
- [[API_Reference/Reactions_Endpoints]] — Toggle/delete reactions on problems & ideas

## Authentication & Authorization
- [[Authentication/JWT_Flow]] — Access token + refresh token lifecycle
- [[Authentication/User_Roles]] — member vs admin
- [[Authentication/Permission_Matrix]] — Chi tiết quyền cho từng role

## Key Concepts
- [[Architecture/TipTap_Integration]] — Rich text editor + JSONB storage
- [[Architecture/Privacy_Model]] — Public/Private visibility + shared users
- [[Architecture/Notification_System]] — Triggers, types, delivery

## Development Setup
- Docker Compose: `docker compose up -d --build`
- Backend chạy ở port 8000, Frontend ở port 5173 (dev) hoặc 80 (production)
- MinIO console ở port 9001
- Xem [[Misc/Troubleshooting]] nếu gặp vấn đề
