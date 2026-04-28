---
type: atomic-note
category: Events
related: ["MOC_Events", "User_Roles"]
tags: [events, faq]
updated: 2026-04-28
---

# FAQ Events

## Tổng quan
Mỗi Event có riêng FAQ section cho câu hỏi thường gặp, hiển thị dạng accordion.

## Tạo FAQ
- **Admin và Team Lead** có thể tạo FAQ.
- Fields: question (bắt buộc), answer (optional, TipTap), sort_order.
- Có thể tạo câu hỏi trước, điền câu trả lời sau.

## Hiển thị
- FAQ hiển thị trong tab FAQ của Event Detail.
- Sắp xếp theo `sort_order`.
- Dạng accordion — click để mở/đóng.

## Chỉnh sửa
- Tác giả hoặc admin có thể sửa/xóa.
- Question và answer đều editable.

## API
- `POST /events/{id}/faqs` — Tạo FAQ
- `GET /events/{id}/faqs` — List FAQs (public)
- `PATCH /events/{id}/faqs/{faq_id}` — Update
- `DELETE /events/{id}/faqs/{faq_id}` — Delete
- Xem [[07_API_Reference/Event_Endpoints]].

## Mối liên hệ
- [[03_Events/MOC_Events]] — Tổng quan Events.
- [[04_Authentication/User_Roles]] — Ai được tạo FAQ.
