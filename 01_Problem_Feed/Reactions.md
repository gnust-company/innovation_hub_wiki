---
type: atomic-note
category: Problem Feed
related: ["Comment_Threading", "MOC_Problem_Feed", "Notification_System"]
tags: [feature, reactions]
updated: 2026-04-28
---

# Reactions

## Tổng quan
Reaction cho phép người dùng bày tỏ cảm xúc về Problem hoặc Idea một cách nhanh chóng.

## Các loại Reaction
| Type | Icon | Ý nghĩa |
|------|------|---------|
| `like` | 👍 | Đồng tình, ủng hộ |
| `dislike` | 👎 | Không đồng tình |
| `insight` | 💡 | Có góc nhìn sâu sắc |

## Cách hoạt động
- **Mỗi user chỉ có 1 reaction** trên mỗi target (problem hoặc idea).
- Click lại reaction hiện tại → toggle off (xóa reaction).
- Click reaction khác → chuyển sang loại mới.
- Reaction count hiển thị trực tiếp trên card.

## Target Types
- `problem` — Reaction trên problem.
- `idea` — Reaction trên idea trong Room.

## API
- `POST /api/v1/problems/{id}/reactions` — Toggle reaction trên problem
- `POST /api/v1/ideas/{id}/reactions` — Toggle reaction trên idea
- `DELETE /api/v1/problems/{id}/reactions` — Xóa reaction
- Xem [[07_API_Reference/Problem_Endpoints]], [[07_API_Reference/Idea_Endpoints]].

## Mối liên hệ
- Reaction trigger [[06_Architecture/Notification_System]] cho tác giả.
- Reaction counts dùng trong [[05_Dashboard/MOC_Dashboard]] analytics.
- Kết hợp với [[01_Problem_Feed/Comment_Threading]] cho tương tác đầy đủ.
