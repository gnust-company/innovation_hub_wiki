---
type: meta
category: Index
related: ["MOC_Overview", "MOC_For_Developers", "MOC_For_End_Users"]
tags: [meta, conventions, vault]
updated: 2026-05-10
---

# Wiki Conventions

Quy tắc tổ chức và viết note trong Innovation Hub Wiki Vault.

## Vault Structure

Vault được tổ chức theo **folder numbering** cho feature folders và **tên thuần** cho các lĩnh vực khác.

| Loại | Folder | Nội dung |
|------|--------|----------|
| Entry point | `00_Index` | MOCs, system guides, conventions |
| Feature | `01_Problem_Feed` | **User-facing / business logic** notes cho từng tính năng |
| Feature | `02_Idea_Lab` | Brainstorming rooms, kanban, voting |
| Feature | `03_Events` | Innovation events, teams, scoring |
| Feature | `05_Dashboard` | Statistics, analytics |
| Feature | `06_Chat` | AI ChatBot, multi-session chat |
| Cross-cutting | `Authentication` | JWT, roles, permission matrix |
| Cross-cutting | `Architecture` | **Technical docs** — kiến trúc, database, notification |
| Cross-cutting | `API_Reference` | **Endpoint docs** — API contract cho developers |
| Cross-cutting | `User_Guide` | **End-user how-tos** |
| Cross-cutting | `Admin_Guide` | **Admin guides** — quản lý user, analytics |
| Cross-cutting | `Misc` | Changelog, glossary, troubleshooting |

### Quy tắc phân loại

**Feature folders** (`01_Problem_Feed`, `02_Idea_Lab`, `03_Events`, `05_Dashboard`, `06_Chat`...)
- Chứa MOC hub + **atomic notes về business logic và user guide**.
- Ví dụ: `Problem_Status_Workflow.md`, `Kanban_Board.md`, `Chat_User_Guide.md`.
- **KHÔNG** chứa API endpoints hay database schema chi tiết.

**Cross-cutting folders** (`Authentication`, `Architecture`, `API_Reference`, `User_Guide`, `Admin_Guide`, `Misc`)
- Không có số — đây là lĩnh vực, không phải feature.
- `Architecture/`: kiến trúc, database, cross-cutting concerns. Ví dụ: `Clean_Architecture.md`, `Database_Schema.md`, `Chat_Integration.md`.
- `API_Reference/`: endpoint documentation. Ví dụ: `Auth_Endpoints.md`, `Event_Endpoints.md`, `Chat_Endpoints.md`.
- `User_Guide/` và `Admin_Guide/`: hướng dẫn sử dụng.

## Atomic Note Conventions

### Mỗi file chỉ nói về 1 concept
- Nếu concept lớn → chia thành nhiều atomic notes + 1 MOC để liên kết.
- Ví dụ: Events feature có `MOC_Events.md` + `Event_Lifecycle.md` + `Scoring_System.md`...

### YAML Frontmatter
Mọi file đều có frontmatter ở đầu:
```yaml
---
type: atomic-note | moc | reference | meta
category: <folder_name>
related: ["Other_File_Name"]
tags: [tag1, tag2]
updated: YYYY-MM-DD
---
```

### Wikilinks
- Dùng `[[Folder/File_Name]]` để liên kết giữa các note.
- Không dùng extension `.md` trong wikilink.
- MOC files đóng vai trò **hub** — liên kết đến các atomic notes liên quan.

## MOC (Map of Content)

MOC là "mục lục sống" của vault:
- Liệt kê các atomic notes liên quan theo nhóm.
- Dùng bảng markdown để tra cứu nhanh.
- Mỗi feature / lĩnh vực có ít nhất 1 MOC.

## AI Agent — Special Notes

- `00_Index/AGENT_GUIDE.md` là **system prompt** cho AI Agent.
- Agent đọc vault này để trả lời câu hỏi về Innovation Hub.
- Các note nên viết rõ ràng, có cấu trúc, dễ parse.

## Mối liên hệ
- [[00_Index/MOC_Overview]] — Bắt đầu từ đây.
- [[00_Index/MOC_For_Developers]] — Dev entry point.
- [[00_Index/MOC_For_End_Users]] — User entry point.
