---
type: atomic-note
category: Chat
related: ["Chat_Overview", "MOC_User_Guide"]
tags: [chat, user-guide]
updated: 2026-05-10
---

# Chat User Guide

Hướng dẫn sử dụng ChatBot trong Innovation Hub.

## Bắt đầu chat

1. Click biểu tượng **Chat** ở sidebar hoặc header.
2. Click **"New Chat"** để tạo session mới.
3. Đặt tên cho session (ví dụ: "Hỏi về Events").
4. Nhập câu hỏi và nhấn Enter.

## Quản lý session

### Xem lịch sử
- Sidebar chat hiển thị danh sách các session của bạn.
- Click vào tên session để xem lại toàn bộ conversation.

### Đổi tên session
- Hover vào session trong sidebar → click **Rename**.
- Nhập tên mới và xác nhận.

### Xóa session
- Hover vào session → click **Delete**.
- Xóa session sẽ xóa toàn bộ lịch sử tin nhắn trong session đó.

## Cách đặt câu hỏi hiệu quả

- **Cụ thể**: "Làm sao để tạo Event?" thay vì "Hướng dẫn đi"
- **Liên quan đến nền tảng**: Agent chỉ có kiến thức về Innovation Hub.
- **Ngôn ngữ**: Có thể hỏi bằng tiếng Việt hoặc tiếng Anh.

## Sources (Nguồn tham chiếu)

Sau mỗi câu trả lời, Agent có thể kèm danh sách **sources** — đây là các trang wiki mà Agent đã đọc để trả lời.
- Sources giúp bạn xác minh thông tin.
- Click vào source nếu muốn đọc chi tiết hơn.

## Lưu ý bảo mật

- **Chỉ bạn xem được** nội dung chat của mình.
- Admin cũng không xem được session của bạn.
- Không chia sẻ thông tin nhạy cảm (mật khẩu, API key) trong chat.

## Troubleshooting

| Vấn đề | Nguyên nhân | Cách xử lý |
|--------|-------------|------------|
| Chat không phản hồi | Agent BE đang khởi động hoặc lỗi | Đợi 30 giây và thử lại. Nếu vẫn lỗi → báo admin. |
| "Not authenticated" | Token hết hạn | Đăng nhập lại. |
| Phản hồi chậm | Network hoặc Agent BE busy | Kiểm tra kết nối mạng. |

Xem thêm: [[Misc/Troubleshooting]].

## Mối liên hệ
- [[06_Chat/Chat_Overview]] — Tổng quan ChatBot.
- [[User_Guide/MOC_User_Guide]] — Index hướng dẫn sử dụng.
