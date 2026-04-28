---
type: atomic-note
category: Architecture
related: ["Database_Schema", "Clean_Architecture", "FastAPI_Structure"]
tags: [architecture, tiptap]
updated: 2026-04-28
---

# TipTap Integration

## Tổng quan
TipTap là rich text editor dùng trong Innovation Hub cho nhiều nội dung.

## Frontend: Editor
- Dùng TipTap v3.20 ecosystem.
- Hỗ trợ: bold, italic, headings, lists, links, images.
- Image upload có resize extension.

## Backend: Storage
- Nội dung TipTap lưu dạng **JSONB** trong PostgreSQL.
- Fields dùng TipTap: `problems.content`, `ideas.description`, `events.description`, `event_ideas.*` (5 fields), `event_faqs.answer`.

## Rendering
- Custom `TipTapRenderer` component để render JSON → HTML.
- Xử lý images, formatting đúng cách.

## API Pattern
- Request: Gửi TipTap JSON object.
- Response: Trả về TipTap JSON object.
- Frontend editor → JSON → API → JSONB column → API → JSON → Renderer.

## Mối liên hệ
- [[06_Architecture/Database_Schema]] — Các cột JSONB.
- [[06_Architecture/Clean_Architecture]] — Storage pattern.
