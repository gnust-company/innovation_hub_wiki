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

## Bản đồ nội dung (MOC Index)

Dưới đây là toàn bộ Map of Content trong vault. Dùng bảng này để xác định nhanh file nào chứa thông tin bạn cần.

### Index & Hướng dẫn
| MOC | Nội dung | Path |
|-----|----------|------|
| MOC Overview | Tổng quan toàn bộ hệ thống | `00_Index/MOC_Overview.md` |
| MOC For Developers | Docs kỹ thuật cho dev | `00_Index/MOC_For_Developers.md` |
| MOC For End Users | Hướng dẫn sử dụng | `00_Index/MOC_For_End_Users.md` |

### Core Features
| MOC | Nội dung | Path |
|-----|----------|------|
| MOC Problem Feed | Đăng vấn đề, thảo luận, reaction, privacy | `01_Problem_Feed/MOC_Problem_Feed.md` |
| MOC Idea Lab | Brainstorm rooms, kanban, voting | `02_Idea_Lab/MOC_Idea_Lab.md` |
| MOC Events | Events, teams, scoring, awards | `03_Events/MOC_Events.md` |
| MOC Dashboard | Statistics, analytics | `05_Dashboard/MOC_Dashboard.md` |

### Kỹ thuật
| MOC | Nội dung | Path |
|-----|----------|------|
| MOC Auth | JWT, roles, permission matrix | `04_Authentication/MOC_Auth.md` |
| MOC Architecture | Clean architecture, DB schema, API | `06_Architecture/MOC_Architecture.md` |
| MOC API | Full API endpoint reference | `07_API_Reference/MOC_API.md` |
| MOC User Guide | Quick start, tìm vấn đề, tham gia event | `08_User_Guide/MOC_User_Guide.md` |
| MOC Admin | Quản lý user, analytics dashboard | `09_Admin_Guide/MOC_Admin.md` |

### Mẹo tìm kiếm nhanh
- **Câu hỏi về tính năng người dùng** → Đọc `MOC_For_End_Users`, rồi follow links
- **Câu hỏi về API/code** → Đọc `MOC_API` hoặc `MOC_Architecture`
- **Câu hỏi về event/competition** → Đọc `MOC_Events`
- **Câu hỏi về phân quyền** → Đọc `MOC_Auth` → `Permission_Matrix`
- **Câu hỏi về vấn đề/ý tưởng** → Đọc `MOC_Problem_Feed` hoặc `MOC_Idea_Lab`

## Thông tin nền tảng
Innovation Hub là nền tảng nội bộ quản lý đổi mới sáng tạo.
- **Tech stack**: React + FastAPI + PostgreSQL + MinIO
- **Roles**: member, admin (team_lead là event-specific)
- **Core flows**: Problem Feed → Idea Lab → Events
- **Privacy**: Public/Private + shared users
- **Rich text**: TipTap editor, JSONB storage
