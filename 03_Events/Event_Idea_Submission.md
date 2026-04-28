---
type: atomic-note
category: Events
related: ["MOC_Events", "Team_Formation", "MOC_Idea_Lab", "Scoring_System"]
tags: [events, ideas]
updated: 2026-04-28
---

# Event Idea Submission

## Hai cách nộp Idea

### 1. Manual (Tạo trực tiếp)
- Điền form trong tab Ideas của Event.
- Các fields:
  - **title** (bắt buộc)
  - **user_problem** — Mô tả vấn đề người dùng (TipTap)
  - **user_scenarios** — Tình huống sử dụng (TipTap)
  - **user_expectation** — Kỳ vọng người dùng (TipTap)
  - **research** — Nghiên cứu (TipTap)
  - **solution** — Giải pháp (bắt buộc, TipTap)
- `source_type = "manual"`.

### 2. Import từ Room (Linked)
- Chọn Room → chọn Idea → import.
- `source_type = "linked"`.
- Lưu `source_problem_id`, `source_room_id`, `source_idea_id`.
- Xem [[02_Idea_Lab/Create_Brainstorm_Room]].

## Quyền nộp
- Phải là thành viên **active** của team trong event.
- Idea gắn với team của người nộp.

## Chỉnh sửa
- Tác giả, team lead, hoặc admin có thể edit.
- Chỉ khi event đang active. Xem [[03_Events/Event_Lifecycle]].

## API
- `POST /events/{id}/ideas` — Manual submit
- `POST /events/{id}/ideas/from-room` — Import from room
- `PATCH /events/{id}/ideas/{idea_id}` — Update idea
- Xem [[07_API_Reference/Event_Endpoints]].

## Mối liên hệ
- [[03_Events/MOC_Events]] — Tổng quan Events.
- [[03_Events/Team_Formation]] — Teams submit ideas.
- [[02_Idea_Lab/MOC_Idea_Lab]] — Ideas có thể import từ rooms.
- [[03_Events/Scoring_System]] — Ideas được chấm điểm sau submit.
