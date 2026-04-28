---
type: atomic-note
category: Problem Feed
related: ["Reactions", "MOC_Problem_Feed", "Notification_System"]
tags: [feature, comments]
updated: 2026-04-28
---

# Comment Threading

## Tổng quan
Hệ thống comment hỗ trợ **threaded comments** (bình luận phân cấp) trên Problems, Ideas, và Event Ideas.

## Cách hoạt động

### Root Comments
- Comment trực tiếp trên target (problem, idea, event_idea).
- Sắp xếp theo thời gian giảm dần (mới nhất trước).

### Replies (Thread)
- Reply vào một comment đã có bằng `parent_id`.
- Replies sắp xếp theo thời gian tăng dần (cũ nhất trước).
- Không giới hạn depth (nhưng UI chỉ hiển thị 1 level).

### Target Types
Comment có thể gắn vào 3 loại target:
- `problem` — Comment trên problem.
- `idea` — Comment trên idea trong Room.
- `event_idea` — Comment trên idea trong Event.

## Quyền
- Ai cũng có thể comment trên target mà họ xem được.
- Chỉ tác giả mới sửa/xóa comment của mình (admin cũng được).

## API
- `POST /api/v1/comments` — Tạo comment/reply
- `GET /api/v1/comments?target_id=X&target_type=problem` — List comments
- Xem thêm: [[07_API_Reference/Comment_Endpoints]]

## Mối liên hệ
- Comment trigger [[06_Architecture/Notification_System]] cho tác giả target và những người đã tương tác.
- Comment trên Problem tự động chuyển status sang "discussing": [[01_Problem_Feed/Problem_Status_Workflow]].
- Kết hợp với [[01_Problem_Feed/Reactions]] để tương tác đa dạng.
