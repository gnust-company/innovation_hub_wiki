---
type: atomic-note
category: Idea Lab
related: ["Kanban_Board", "MOC_Idea_Lab", "Notification_System"]
tags: [feature, voting]
updated: 2026-04-28
---

# Star Voting

## Tổng quan
Hệ thống bình chọn sao (1-5) cho Ideas trong Room.

## Cách hoạt động
- **1 user = 1 vote per idea**: Chỉ được vote 1 lần cho mỗi idea.
- **Stars**: Từ 1 (thấp nhất) đến 5 (cao nhất).
- **Thay đổi vote**: Click lại để chọn số sao khác.
- **Xóa vote**: Có thể xóa vote đã đặt.

## Average Stars
- Hiển thị **điểm trung bình** trên idea card.
- Ví dụ: 4.2/5 từ 15 votes.
- Dùng cho trending ideas trong [[05_Dashboard/MOC_Dashboard]].

## Phân biệt với Reaction
- **Vote (Star)**: Đánh giá chất lượng, có trọng số.
- **Reaction**: Bày tỏ cảm xúc nhanh (like/dislike/insight).
- Idea có cả vote lẫn reaction. Xem [[01_Problem_Feed/Reactions]].

## API
- `POST /api/v1/ideas/{id}/votes` — Vote (body: `{ "stars": 1-5 }`)
- `DELETE /api/v1/ideas/{id}/votes` — Xóa vote
- Xem [[07_API_Reference/Idea_Endpoints]].

## Mối liên hệ
- [[02_Idea_Lab/Kanban_Board]] — Vote hiển thị trên idea cards.
- [[06_Architecture/Notification_System]] — Vote trigger notification cho tác giả idea.
- [[05_Dashboard/MOC_Dashboard]] — Average stars dùng cho analytics.
