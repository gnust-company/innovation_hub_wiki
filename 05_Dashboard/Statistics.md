---
type: atomic-note
category: Dashboard
related: ["MOC_Dashboard", "OKR_Tracking"]
tags: [dashboard, statistics]
updated: 2026-04-28
---

# Statistics

## Các chỉ số thống kê

### User Dashboard
- **Open problems**: Số problem đang open.
- **Active rooms**: Số room active.
- **Live events**: Số event đang active.
- Period-over-period comparison (tuần này vs tuần trước).

### Admin Analytics
- **Tổng users, problems, ideas, rooms, events**.
- **Interaction rate**: Tổng reactions + comments / tổng nội dung.
- **Resolved problems**: Số problem status "solved".
- **Category distribution**: Pie chart problems theo category.
- **Activity over time**: Line chart hoạt động theo ngày.
- **Status breakdown**: Progress bars cho từng status.
- **Top contributors**: Leaderboard theo đóng góp.

## API Endpoints
- `GET /api/v1/dashboard/stats` — Tổng stats
- `GET /api/v1/dashboard/top-contributors` — Leaderboard
- `GET /api/v1/dashboard/activity-over-time` — Chart data
- `GET /api/v1/dashboard/problems-by-category` — Category chart
- `GET /api/v1/dashboard/recent-activity` — Activity feed

## Date Filtering
- Hầu hết endpoints hỗ trợ `date_from` và `date_to` (format YYYY-MM-DD).
- So sánh được theo tuần, tháng, quý.

## Mối liên hệ
- [[05_Dashboard/MOC_Dashboard]] — Tổng quan Dashboard.
- [[05_Dashboard/OKR_Tracking]] — Theo dõi mục tiêu OKR.
