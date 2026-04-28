---
type: atomic-note
category: Events
related: ["MOC_Events", "Team_Formation", "User_Roles"]
tags: [events, lifecycle]
updated: 2026-04-28
---

# Event Lifecycle

## Trạng thái

| Status | Mô tả | Ai tạo/chuyển |
|--------|-------|---------------|
| `draft` | Đang soạn thảo | Admin |
| `active` | Đang diễn ra | Admin |
| `closed` | Đã kết thúc (terminal) | Admin |

## Chuyển trạng thái
```
draft → active → closed
```
- Chỉ **Admin** mới tạo và chuyển status event.
- Khi close: `closed_at` được set tự động, event trở thành read-only.

## Introduction Type
Event có 2 cách hiển thị giới thiệu (XOR):
- **editor**: Dùng TipTap rich text editor nội bộ.
- **embed**: Nhúng URL bên ngoài (video, website).

## Ngày tháng
- `start_date`, `end_date` (optional).
- Dùng cho filtering và hiển thị.

## API
- `POST /api/v1/events` — Tạo event (admin)
- `PATCH /api/v1/events/{id}` — Update event (admin)
- `PATCH /api/v1/events/{id}/close` — Close event (admin)
- Xem [[07_API_Reference/Event_Endpoints]].

## Mối liên hệ
- [[03_Events/Team_Formation]] — Teams chỉ hoạt động khi event active.
- [[03_Events/Event_Idea_Submission]] — Submit ideas khi event active.
- [[04_Authentication/User_Roles]] — Chỉ admin quản lý events.
