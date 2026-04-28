---
type: guide
category: Admin Guide
related: ["MOC_Admin", "Statistics", "MOC_Dashboard"]
tags: [admin, analytics]
updated: 2026-04-28
---

# Analysis Dashboard

## Truy cập
Vào **Admin → Analytics** (`/admin`). Chỉ admin mới truy cập được.

## Nội dung hiển thị

### Statistics Cards
- Tổng users, problems, ideas, rooms, events.
- Interaction rate (reactions + comments / nội dung).
- Resolved problems count.
- Period-over-period comparison.

### Charts
- **Activity Over Time**: Line chart hoạt động theo ngày.
- **Category Distribution**: Donut chart problems theo category.
- **Status Breakdown**: Progress bars cho từng status.

### Filters
- **Date range**: Chọn khoảng thời gian để phân tích.

### Additional
- **Recent Activity**: Feed hoạt động gần đây (bypass privacy).
- **Top Contributors**: Leaderboard theo đóng góp.

## API
- `GET /api/v1/dashboard/stats` — Stats tổng.
- `GET /api/v1/dashboard/activity-over-time` — Chart data.
- `GET /api/v1/dashboard/problems-by-category` — Category chart.
- Xem [[05_Dashboard/Statistics]].

## Mối liên hệ
- [[05_Dashboard/Statistics]] — Chi tiết metrics.
- [[05_Dashboard/MOC_Dashboard]] — Tổng quan dashboard.
- [[09_Admin_Guide/MOC_Admin]] — Tổng quan Admin.
