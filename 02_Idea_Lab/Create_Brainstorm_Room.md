---
type: atomic-note
category: Idea Lab
related: ["MOC_Idea_Lab", "Create_Problem", "Room_vs_Problem_Link", "Kanban_Board"]
tags: [user-guide, how-to]
updated: 2026-04-28
---

# Tạo Brainstorm Room

## Điều kiện tiên quyết
- Đã đăng nhập. Xem [[04_Authentication/JWT_Flow]].
- Role: `member`, `admin`.

## Hai cách tạo Room

### 1. Tạo độc lập
1. Vào **Idea Lab** (`/rooms`).
2. Click **"Tạo Room mới"**.
3. Điền: tên, mô tả (optional), privacy.
4. Không bắt buộc gắn Problem.

### 2. Tạo từ Problem (1-click)
1. Vào trang chi tiết Problem (`/problems/{id}`).
2. Click **"Tạo Room"**.
3. Room tự động link với Problem đó.
4. Problem status chuyển sang `brainstorming`. Xem [[01_Problem_Feed/Problem_Status_Workflow]].

## Privacy Room
- Room có privacy **độc lập** với Problem liên quan.
- Room public có thể link với Problem private, và ngược lại.
- Xem [[01_Problem_Feed/Problem_Privacy]] và [[06_Architecture/Privacy_Model]].

## Sau khi tạo
- Room xuất hiện trong Idea Lab.
- Bắt đầu tạo Ideas: xem [[02_Idea_Lab/Kanban_Board]].
- Mọi người có thể vào Room và đóng góp ideas.

## API
- `POST /api/v1/rooms` — Tạo room độc lập
- `POST /api/v1/problems/{id}/rooms` — Tạo room từ problem
- Xem [[07_API_Reference/Room_Endpoints]].

## Mối liên hệ
- [[02_Idea_Lab/Room_vs_Problem_Link]] — Chi tiết mối liên hệ Room-Problem.
- [[01_Problem_Feed/Create_Problem]] — Tạo problem trước khi tạo room.
- [[02_Idea_Lab/MOC_Idea_Lab]] — Tổng quan Idea Lab.
