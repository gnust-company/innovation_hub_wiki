---
type: atomic-note
category: Idea Lab
related: ["Create_Brainstorm_Room", "Create_Problem", "Privacy_Model"]
tags: [feature, relationship]
updated: 2026-04-28
---

# Room vs Problem Link

## Mối liên hệ
- Room **có thể** link với 1 Problem (optional).
- Problem chỉ link với **nhiều Room** (1-to-many).

## Tạo link
- **Từ Problem**: Click "Tạo Room" → Room tự động link. Xem [[02_Idea_Lab/Create_Brainstorm_Room]].
- **Khi tạo Room độc lập**: Chọn Problem qua field `problem_id` (optional).

## Hiệu ứng của link
- Khi tạo Room từ Problem:
  - Problem status tự động chuyển sang `brainstorming`.
  - Xem [[01_Problem_Feed/Problem_Status_Workflow]].
- Room hiển thị Problem liên quan ở đầu trang.

## Privacy độc lập
- Problem privacy **KHÔNG** ảnh hưởng Room privacy.
- Problem private → Room vẫn có thể public.
- Room private → Problem vẫn có thể public.
- Xem [[06_Architecture/Privacy_Model]].

## Khi Problem bị xóa
- Room vẫn tồn tại, field `problem_id` thành `null`.

## Mối liên hệ
- [[02_Idea_Lab/Create_Brainstorm_Room]] — Cách tạo room và link.
- [[01_Problem_Feed/Create_Problem]] — Tạo problem trước.
- [[06_Architecture/Privacy_Model]] — Chi tiết privacy model.
