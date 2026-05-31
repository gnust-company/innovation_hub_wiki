---
type: moc
category: Index
related: ["MOC_For_Developers", "MOC_For_End_Users"]
tags: [index, overview]
updated: 2026-05-10
---

# MOC Overview

Innovation Hub là nền tảng nội bộ quản lý đổi mới sáng tạo, số hóa quy trình "Đăng → Thảo luận → Thực thi".

## Tech Stack
- **Frontend**: React 18 + TypeScript + Vite + Tailwind CSS + TipTap rich text + react-markdown
- **Backend**: Python 3.11 + FastAPI + SQLAlchemy 2.0 (async)
- **Database**: PostgreSQL 16
- **Storage**: MinIO (avatars, files)
- **Deployment**: Docker Compose + Nginx

## Core Features

### Cho mọi người
- [[01_Problem_Feed/MOC_Problem_Feed]] — Đăng vấn đề, thảo luận, reaction
- [[02_Idea_Lab/MOC_Idea_Lab]] — Brainstorming rooms, kanban board, star voting
- [[03_Events/MOC_Events]] — Innovation events, team formation, scoring
- [[05_Dashboard/MOC_Dashboard]] — Statistics, analytics, tracking
- [[06_Chat/MOC_Chat]] — AI ChatBot, multi-session chat, wiki-grounded answers

### Hướng dẫn
- [[00_Index/MOC_For_End_Users]] — Hướng dẫn sử dụng cho người dùng
- [[00_Index/MOC_For_Developers]] — Technical docs cho dev

## Khái niệm cốt lõi
- [[01_Problem_Feed/Problem_Status_Workflow]] — open → discussing → brainstorming → solved/closed
- [[02_Idea_Lab/Idea_Status_Workflow]] — draft ↔ refining ↔ reviewing → submitted/closed
