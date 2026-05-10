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
1. **Unresolved Problem** — Đây là một bài toán chưa có giải pháp hoặc giải pháp chưa triệt để (chưa đáp ứng được nhu cầu ngườI dùng)?
2. **Root Cause Analysis** — Tác giả đã có sự tìm hiểu và phân tích được nguyên nhân gốc rễ của vấn đề/bài toán?
3. **Problem Recognition** — Đây là một bài toán có độ nhận diện cao, được nhắc nhiều trên báo đài hoặc tin tức?
4. **Gap Evidence** — Có bằng chứng về việc bài toán chưa được giải quyết (gap analysis) từ các nguồn uy tín?

### Solution Group (4 criteria)
1. **Novelty** — Ý tưởng của giải pháp thực sự mới lạ và chưa từng xuất hiện trong các giải pháp đã biết (kể cả lĩnh vực khác)?
2. **Root Cause Resolution** — Giải pháp có khả năng giải quyết được vấn đề gốc rễ một cách triệt để và như mong đợi?
3. **Competitive Advantage** — Giải pháp có những điểm khác biệt và ưu thế cạnh tranh so với các giải pháp hiện có trên thị trường?
4. **Technical Feasibility** — Giải pháp khả thi về mặt kỹ thuật, có thể phát triển và triển khai dựa trên các công nghệ hiện tại hoặc tương lai gần?

## Likert Scale (5 levels)
| Level | Label | Points |
|-------|-------|--------|
| 5 | Strongly Agree | 12.5 |
| 4 | Agree | 10.0 |
| 3 | Neutral | 7.5 |
| 2 | Disagree | 5.0 |
| 1 | Strongly Disagree | 2.5 |

**Max total (với defaults): 8 criteria × 12.5 × weight(1.0) = 100 points.**

> **Lưu ý:** Tổng điểm được tính động theo công thức `Σ(score_i × weight_i)`. Nếu admin thay đổi `weight`, `max_score`, hoặc số lượng criteria, tổng điểm tối đa sẽ khác 100.

## Circular Review
- Team A review Team B's ideas.
- Team B review Team C's ideas.
- Team C review Team A's ideas.
- Xem [[03_Events/Team_Formation]].

## Criteria tự động seed
- Khi event lần đầu truy cập criteria endpoint.
- Admin có thể tùy chỉnh sau.

## API
- `GET /api/v1/events/{id}/criteria` — Xem criteria
- `POST /api/v1/events/{id}/ideas/{idea_id}/scores` — Chấm điểm
- `PUT /api/v1/events/{id}/ideas/{idea_id}/scores` — Sửa điểm
- Xem [[API_Reference/Event_Endpoints]].

## Mối liên hệ
- [[03_Events/Team_Formation]] — Teams chấm điểm lẫn nhau.
- [[03_Events/Event_Idea_Submission]] — Ideas được chấm.
- [[03_Events/Event_Awards]] — Awards dựa trên kết quả scoring.
