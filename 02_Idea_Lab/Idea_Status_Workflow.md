---
type: atomic-note
category: Idea Lab
related: ["Kanban_Board", "MOC_Idea_Lab", "Problem_Status_Workflow"]
tags: [feature, workflow]
updated: 2026-04-28
---

# Idea Status Workflow

## Trạng thái

| Status | Mô tả |
|--------|-------|
| `draft` | Ý tưởng mới tạo, chưa hoàn thiện |
| `refining` | Đang tinh chỉnh nội dung |
| `reviewing` | Đang được xem xét |
| `submitted` | Đã nộp chính thức (terminal) |
| `closed` | Đã đóng (terminal) |

## Chuyển trạng thái

### Tự do (Bi-directional)
`draft` ↔ `refining` ↔ `reviewing`

Ba trạng thái này có thể chuyển qua lại tự do bằng drag-drop trên [[02_Idea_Lab/Kanban_Board]].

### Terminal (Một chiều)
- `draft`/`refining`/`reviewing` → `submitted`: Nộp idea.
- `draft`/`refining`/`reviewing` → `closed`: Đóng idea.
- `submitted` và `closed` **không thể quay lại**.

## Sơ đồ
```
draft ↔ refining ↔ reviewing
  ↓         ↓          ↓
submitted  submitted  submitted
  ↓         ↓          ↓
closed     closed     closed
```

## API
- `PATCH /api/v1/ideas/{id}` — Thay đổi status qua field `status`.
- Xem [[07_API_Reference/Idea_Endpoints]].

## Mối liên hệ
- [[02_Idea_Lab/Kanban_Board]] — Drag-drop để chuyển status.
- [[01_Problem_Feed/Problem_Status_Workflow]] — Workflow tương tự cho Problems.
- [[02_Idea_Lab/MOC_Idea_Lab]] — Tổng quan Idea Lab.
