---
type: atomic-note
category: Architecture
related: ["MOC_Architecture", "Comment_Threading", "Reactions"]
tags: [architecture, notifications]
updated: 2026-04-28
---

# Notification System

## Tổng quan
Notification system thông báo cho users về các hoạt động liên quan.

## Notification Types

### General
- `comment_added` — Ai đó comment trên problem/idea của bạn.
- `reaction_added` — Ai đó reaction trên nội dung của bạn.
- `vote_added` — Ai đó vote cho idea của bạn.
- `status_changed` — Status của problem/idea thay đổi.
- `room_idea_created` — Idea mới trong room bạn tạo/s مشارك.

### Event-specific
- `event_join_request` — Có người xin join team bạn lead.
- `event_join_approved` — Join request được approve.
- `event_join_rejected` — Join request bị reject.
- `event_idea_submitted` — Team nộp idea mới.
- `event_scored` — Idea của team được chấm điểm.
- `event_created` — Event mới được tạo.
- `event_closed` — Event đóng.
- `team_review_assigned` — Team được assign chấm điểm.
- `team_disbanded` — Team bị disband.
- `team_lead_transferred` — Leadership chuyển.

## Delivery
- **Polling**: Frontend poll endpoint định kỳ.
- **Click-to-navigate**: Click notification → navigate đến target.
- **Action detail**: Kèm context (comment content, reaction type, score).

## Recipients
- Tác giả của target.
- Tất cả users đã tương tác (comment, reaction, vote) với target.
- Room creator, problem owner (nếu liên quan).

## API
- `GET /api/v1/notifications` — List notifications
- `GET /api/v1/notifications/unread-count` — Unread count
- `PATCH /api/v1/notifications/{id}/read` — Mark read
- `PATCH /api/v1/notifications/read-all` — Mark all read

## Mối liên hệ
- [[01_Problem_Feed/Comment_Threading]] — Comments trigger notifications.
- [[01_Problem_Feed/Reactions]] — Reactions trigger notifications.
- [[03_Events/MOC_Events]] — Event-specific notifications.
