---
type: index
category: Index
tags: [index, readme]
updated: 2026-04-28
---

# Innovation Hub Wiki

Obsidian Vault — Knowledge base nội bộ cho nền tảng **Innovation Hub**.

## Vault là gì?

Đây là **Zettelkasten vault** chứa toàn bộ tài liệu về Innovation Hub, phục vụ:
- **Developer**: Hiểu architecture, API, database schema
- **End-user**: Hướng dẫn sử dụng các tính năng
- **AI Agent**: Tra cứu thông tin qua wikilinks để trả lời câu hỏi

## Cách sử dụng

1. Bắt đầu từ [[00_Index/MOC_Overview]] để xem tổng quan
2. Nếu bạn là developer → [[00_Index/MOC_For_Developers]]
3. Nếu bạn là end-user → [[00_Index/MOC_For_End_Users]]
4. AI Agent đọc [[00_Index/AGENT_GUIDE]] trước

## Cấu trúc vault

| Folder | Nội dung |
|--------|----------|
| `00_Index` | Entry points, MOC tổng |
| `01_Problem_Feed` | Tính năng Problem Feed |
| `02_Idea_Lab` | Tính năng Idea Lab / Brainstorming |
| `03_Events` | Tính năng Innovation Events |
| `04_Authentication` | Xác thực & phân quyền |
| `05_Dashboard` | Dashboard & Analytics |
| `06_Architecture` | Technical docs cho developers |
| `07_API_Reference` | API endpoint docs |
| `08_User_Guide` | Hướng dẫn end-user |
| `09_Admin_Guide` | Hướng dẫn admin |
| `99_Misc` | Changelog, troubleshooting, glossary |

## Quy tắc Zettelkasten

- Mỗi file là **atomic note** — chỉ nói về 1 concept
- MOC files đóng vai trò mục lục + hub
- Wikilinks `[[Tên_Note]]` để liên kết
- Frontmatter YAML ở đầu mỗi file
