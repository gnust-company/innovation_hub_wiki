---
type: atomic-note
category: Events
related: ["MOC_Events", "Event_Idea_Submission", "Scoring_System", "User_Roles"]
tags: [events, teams]
updated: 2026-04-28
---

# Team Formation

## Tổng quan
Teams là đơn vị tham gia Event. Mỗi team có leader, members, và có thể được assign chấm điểm team khác.

## Tạo Team
- Bất kỳ ai đã đăng nhập đều có thể tạo team trong event active.
- Người tạo tự động trở thành **Team Leader**.
- Fields: name (bắt buộc), slogan (optional).

## Join Team
1. Click **"Join"** trên team card.
2. Status: `pending` — chờ leader duyệt.
3. Leader approve → status `active`.
4. Leader reject → status `rejected`.
- **Mỗi user chỉ được active trong 1 team per event**.

## Leader quyền
- Approve/reject join requests.
- Disband team (xóa toàn bộ).
- Transfer leadership sang member khác.
- Submit ideas cho team. Xem [[03_Events/Event_Idea_Submission]].
- Chấm điểm team khác (nếu được assign). Xem [[03_Events/Scoring_System]].

## Circular Review Assignment
- Admin assign team A review team B, B review C, C review A...
- Qua endpoint: `PATCH /events/{id}/teams/{team_id}/assign-review`.
- Leader của team được assign sẽ chấm ideas của team target.

## API
- `POST /events/{id}/teams` — Tạo team
- `POST /events/{id}/teams/{team_id}/join` — Request join
- `PATCH /events/{id}/teams/{team_id}/members/{user_id}` — Approve/reject
- `DELETE /events/{id}/teams/{team_id}` — Disband
- `PATCH /events/{id}/teams/{team_id}/transfer-lead` — Transfer leader
- Xem [[07_API_Reference/Event_Endpoints]].

## Mối liên hệ
- [[03_Events/MOC_Events]] — Tổng quan Events.
- [[03_Events/Event_Idea_Submission]] — Teams submit ideas.
- [[03_Events/Scoring_System]] — Teams chấm điểm lẫn nhau.
