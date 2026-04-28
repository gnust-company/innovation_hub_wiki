---
type: atomic-note
category: Idea Lab
related: ["Idea_Status_Workflow", "Star_Voting", "MOC_Idea_Lab"]
tags: [feature, kanban]
updated: 2026-04-28
---

# Kanban Board

## Tổng quan
Kanban Board là view chính trong Room, hiển thị ideas theo status với **drag-and-drop**.

## 5 Cột (Columns)
| Column | Status | Mô tả |
|--------|--------|-------|
| Draft | `draft` | Ý tưởng mới tạo |
| Refining | `refining` | Đang tinh chỉnh |
| Reviewing | `reviewing` | Đang xem xét |
| Submitted | `submitted` | Đã nộp (terminal) |
| Closed | `closed` | Đã đóng (terminal) |

## Tương tác
- **Drag & Drop**: Kéo idea giữa các cột để thay đổi status.
- **Optimistic Update**: UI cập nhật ngay, API call chạy ngầm.
- **Pin**: Ghim idea quan trọng lên đầu.

## Tạo Idea mới
- Click nút trong cột Draft.
- Điền: tiêu đề, nội dung (TipTap rich text), tóm tắt.
- Idea xuất hiện ngay trên board.

## Board vs List View
- **Board view**: Kanban board (mặc định).
- List view đã bị loại bỏ — chỉ giữ Board view.

## API
- `POST /api/v1/ideas` — Tạo idea
- `PATCH /api/v1/ideas/{id}` — Cập nhật status (drag-drop)
- Xem [[07_API_Reference/Idea_Endpoints]].

## Mối liên hệ
- [[02_Idea_Lab/Idea_Status_Workflow]] — Chi tiết chuyển trạng thái.
- [[02_Idea_Lab/Star_Voting]] — Bình chọn sao cho ideas.
- [[02_Idea_Lab/Create_Brainstorm_Room]] — Tạo room chứa board.
