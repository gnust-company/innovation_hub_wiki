---
type: atomic-note
category: Events
related: ["MOC_Events", "Team_Formation", "Event_Idea_Submission"]
tags: [events, scoring]
updated: 2026-04-28
---

# Scoring System

## Tổng quan
Hệ thống chấm điểm peer-review giữa các teams trong Event.

## 8 Scoring Criteria
Chia làm 2 groups:

### Problem Group (4 criteria)
1. Clarity of Problem Definition
2. Validity of User Scenarios
3. Measurability of User Expectations
4. Depth of Research

### Solution Group (4 criteria)
1. Innovation & Creativity
2. Feasibility & Implementation Plan
3. Impact & Value
4. Scalability & Sustainability

## Likert Scale (5 levels)
| Level | Label | Points |
|-------|-------|--------|
| 5 | Strongly Agree | 12.5 |
| 4 | Agree | 10.0 |
| 3 | Neutral | 7.5 |
| 2 | Disagree | 5.0 |
| 1 | Strongly Disagree | 2.5 |

**Max total: 8 criteria x 12.5 = 100 points.**

## Circular Review
- Team A review Team B's ideas.
- Team B review Team C's ideas.
- Team C review Team A's ideas.
- Xem [[03_Events/Team_Formation]].

## Criteria tự động seed
- Khi event lần đầu truy cập criteria endpoint.
- Admin có thể tùy chỉnh sau.

## API
- `GET /events/{id}/criteria` — Xem criteria
- `POST /events/{id}/ideas/{idea_id}/scores` — Chấm điểm
- `PUT /events/{id}/ideas/{idea_id}/scores` — Sửa điểm
- Xem [[07_API_Reference/Event_Endpoints]].

## Mối liên hệ
- [[03_Events/Team_Formation]] — Teams chấm điểm lẫn nhau.
- [[03_Events/Event_Idea_Submission]] — Ideas được chấm.
- [[03_Events/Event_Awards]] — Awards dựa trên kết quả scoring.
