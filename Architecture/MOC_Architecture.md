---
type: moc
category: Architecture
related: ["MOC_For_Developers", "Clean_Architecture", "Database_Schema"]
tags: [architecture, index]
updated: 2026-05-10
---

# MOC Architecture

Technical architecture documentation cho Innovation Hub.

## Core Architecture
- [[Architecture/Clean_Architecture]] — 3-layer separation (Domain → Application → Infrastructure)
- [[Architecture/FastAPI_Structure]] — Backend folder structure và routing
- [[Architecture/Frontend_Architecture]] — Frontend tech stack, routing, Zustand stores
- [[Architecture/Database_Schema]] — Entity-Relationship, all tables and fields

## Cross-cutting Concerns
- [[Architecture/TipTap_Integration]] — Rich text editor + JSONB storage pattern
- [[Architecture/Privacy_Model]] — Public/Private visibility + shared users architecture
- [[Architecture/Notification_System]] — Triggers, types, delivery mechanism
- [[Architecture/Environment_Variables]] — Env vars cho cả 3 dịch vụ

## Integration
- [[Architecture/API_Contract_Summary]] — Tổng hợp API endpoints
- [[Architecture/Chat_Integration]] — ChatBot SSE proxy và Agent BE integration
- Xem đầy đủ API docs: [[API_Reference/MOC_API]]

## Mối liên hệ
- Architecture decisions ảnh hưởng mọi feature.
- Xem [[00_Index/MOC_For_Developers]] cho hướng dẫn dev.
