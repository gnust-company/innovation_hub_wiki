---
type: atomic-note
category: Events
related: ["MOC_Events", "Scoring_System", "Team_Formation"]
tags: [events, awards]
updated: 2026-04-28
---

# Event Awards

## Tổng quan
Awards (giải thưởng) được tạo trong Event để trao cho các teams chiến thắng.

## Tạo Award
- **Admin only**.
- Fields: name (tên giải), rank_order (thứ hạng).
- Ví dụ: "Giải Nhất" (rank 1), "Giải Nhì" (rank 2), "Giải Khuyến Khích" (rank 3).

## Gắn Team vào Award
- Admin chọn award → thêm team(s) chiến thắng.
- Một award có thể có **nhiều teams** (ex-aequo).
- Một team có nhận **nhiều awards**.

## Hiển thị
- Awards hiển thị trong tab Awards của Event Detail.
- Hiển thị tên giải + danh sách teams chiến thắng.

## Workflow gợi ý
1. Tạo event và teams. Xem [[03_Events/Event_Lifecycle]], [[03_Events/Team_Formation]].
2. Teams submit ideas. Xem [[03_Events/Event_Idea_Submission]].
3. Peer review scoring. Xem [[03_Events/Scoring_System]].
4. Admin xem leaderboard → tạo awards → gắn teams.

## API
- `POST /events/{id}/awards` — Tạo award
- `POST /events/{id}/awards/{award_id}/teams` — Gắn team
- `GET /events/{id}/awards` — List awards
- Xem [[07_API_Reference/Event_Endpoints]].

## Mối liên hệ
- [[03_Events/Scoring_System]] — Scores xác định winners.
- [[03_Events/Team_Formation]] — Teams nhận awards.
- [[03_Events/MOC_Events]] — Tổng quan Events.
