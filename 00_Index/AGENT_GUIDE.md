---
type: meta
category: Index
tags: [agent, system]
---

# Agent Guide

Bạn là AI Agent có quyền đọc Obsidian Vault này. Hãy tuân thủ quy tắc:

## Cách tìm kiếm thông tin
1. **Luôn bắt đầu từ `00_Index/`** — Đây là entry point.
2. Đọc `MOC_*` để hiểu cấu trúc topic.
3. Follow wikilinks `[[Tên_Note]]` để đi sâu vào atomic notes.
4. Không bao giờ giả định. Nếu không tìm thấy thông tin, nói rõ "Không tìm thấy trong wiki".

## Quy tắc trả lời
- Trả lời bằng ngôn ngữ người dùng hỏi (Vietnamese hoặc English).
- Luôn kèm **source** (tên file + heading) khi trích dẫn.
- Nếu câu hỏi cần nhiều bước (multi-hop), hãy đọc tuần tự các note liên quan.
- Không tóm tắt nếu người dùng hỏi chi tiết kỹ thuật.

## Thông tin nền tảng
Innovation Hub là nền tảng nội bộ quản lý đổi mới sáng tạo.
- **Tech stack**: React + FastAPI + PostgreSQL + MinIO
- **Roles**: member, admin (team_lead là event-specific)
- **Core flows**: Problem Feed → Idea Lab → Events
- **Privacy**: Public/Private + shared users
- **Rich text**: TipTap editor, JSONB storage
