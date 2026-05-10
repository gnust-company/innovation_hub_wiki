---
type: atomic-note
category: Problem Feed
related: ["Create_Problem", "MOC_Problem_Feed", "Idea_Status_Workflow"]
tags: [feature, workflow]
updated: 2026-05-10
---

# Problem Status Workflow

## Trạng thái

| Status | Mô tả |
|--------|-------|
| `open` | Mới đăng, chờ thảo luận |
| `discussing` | Đang có bình luận |
| `brainstorming` | Đã tạo Room brainstorm |
| `solved` | Đã giải quyết (terminal) |
| `closed` | Đã đóng (terminal) |

## Chuyển trạng thái

### Tự động
- `open` → `discussing`: Khi có comment từ người khác (không phải tác giả).
- `open`/`discussing` → `brainstorming`: Khi tạo Room từ Problem.

### Thủ công
- `brainstorming` → `solved`: Tác giả hoặc admin chuyển.
- `brainstorming` → `closed`: Tác giả hoặc admin chuyển.
- `solved` và `closed` là **2 trạng thái terminal ngang hàng** — không thể chuyển đổi qua lại giữa chúng.
- Không thể quay lại từ `solved` hoặc `closed`.

> **Lưu ý quan trọng:** Khi problem ở trạng thái `solved` hoặc `closed`, hệ thống **từ chối tạo brainstorm room mới** (trả về 400 Bad Request).

## Sơ đồ
```
open → discussing → brainstorming → solved
  ↓         ↑              ↑       
  └─────────┘──────────────┘
                              
                         closed
```
- `solved` và `closed` đều là terminal từ `brainstorming` (không phải nối tiếp nhau).

## API
- `PATCH /api/v1/problems/{id}` — Cập nhật status qua field `status`.
- Xem [[API_Reference/Problem_Endpoints]].

## Mối liên hệ
- [[01_Problem_Feed/Create_Problem]] — Problem bắt đầu ở status `open`.
- [[02_Idea_Lab/Create_Brainstorm_Room]] — Tạo Room tự động chuyển sang `brainstorming`.
- [[02_Idea_Lab/Idea_Status_Workflow]] — Workflow tương tự cho Ideas.
