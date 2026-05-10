---
type: atomic-note
category: Chat
related: ["Architecture/Chat_Integration", "Chat_User_Guide", "MOC_Chat"]
tags: [chat, overview]
updated: 2026-05-10
---

# Chat Overview

ChatBot là AI Assistant tích hợp trong Innovation Hub, giúp người dùng tra cứu thông tin và được hỗ trợ bởi kiến thức từ [[00_Index/AGENT_GUIDE|Innovation Hub Wiki]].

## Tính năng chính

### Multi-session Chat
- Mỗi user có thể tạo nhiều chat session.
- Mỗi session có tiêu đề riêng, có thể đổi tên hoặc xóa.
- Lịch sử messages được lưu trong PostgreSQL, chỉ owner mới xem được.

### AI-powered Answers
- Agent đọc nội dung từ wiki vault (Obsidian) để trả lời.
- Hỗ trợ cả tiếng Việt và tiếng Anh.
- Trả lờu dựa trên nội dung wiki — không bịa đặt thông tin.

### Real-time Streaming
- Phản hồi từ AI được stream về frontend qua SSE (Server-Sent Events).
- Hiển thị từng token ngay lập tức thay vì chờ hoàn thành.

## Luồng hoạt động tóm tắt

```
User gửi tin nhắn
  → Hub BE lưu message + lấy full history
    → POST /api/chat/stream đến Agent BE
      → Agent BE dùng LangGraph ReAct đọc wiki files
    ← SSE stream trả về (tokens + sources)
  ← Hub BE lưu assistant message
← FE render câu trả lời + danh sách sources
```

## Bảo mật & Quyền riêng tư
- Session và messages **chỉ thuộc về owner**. Không user nào xem được session của người khác, kể cả Admin.
- Agent BE yêu cầu `X-API-Key` header — internal service, không expose ra ngoài.
- User có thể tự xóa session bất cứ lúc nào (cascade xóa messages).

## Mối liên hệ
- [[Architecture/Chat_Integration]] — Chi tiết kiến trúc SSE proxy và Agent BE.
- [[06_Chat/Chat_User_Guide]] — Hướng dẫn sử dụng.
- [[00_Index/AGENT_GUIDE]] — Cách Agent BE đọc wiki.
