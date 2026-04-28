---
type: atomic-note
category: Problem Feed
related: ["Create_Problem", "Privacy_Model", "User_Roles"]
tags: [feature, privacy]
updated: 2026-04-28
---

# Problem Privacy

## Chế độ hiển thị

Problem có 2 chế độ hiển thị, độc lập với Room liên quan:

### Public (Mặc định)
- Tất cả người dùng đã đăng nhập đều xem được.
- Xuất hiện trên Problem Feed chung.

### Private
- Chỉ những người sau mới xem được:
  - **Tác giả** của problem.
  - **Người được share** (qua `shared_user_ids`).
  - **Admin** (luôn xem được mọi nội dung).
- Khi thêm `shared_user_ids`, visibility tự động chuyển thành `private`.

## Độc lập với Room
- Problem và Room có **privacy settings riêng biệt**.
- Problem private có thể có Room public, và ngược lại.
- Xem thêm: [[06_Architecture/Privacy_Model]].

## Thay đổi privacy
- Khi tạo: chọn Public/Private trong form.
- Khi sửa: PATCH `/api/v1/problems/{id}` với field `visibility` và `shared_user_ids`.
- Xem [[07_API_Reference/Problem_Endpoints]] chi tiết.

## Mối liên hệ
- [[01_Problem_Feed/Create_Problem]] — Cách tạo problem với privacy settings.
- [[04_Authentication/User_Roles]] — Admin luôn bypass privacy.
- [[06_Architecture/Privacy_Model]] — Tổng quan privacy toàn hệ thống.
