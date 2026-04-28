---
type: atomic-note
category: Problem Feed
related: ["Problem_Privacy", "Comment_Threading", "MOC_Problem_Feed", "Problem_Status_Workflow"]
tags: [user-guide, how-to]
updated: 2026-04-28
---

# Tạo Problem

## Điều kiện tiên quyết
- Người dùng phải đăng nhập (JWT valid). Xem [[04_Authentication/JWT_Flow]].
- Role: `member`, `team_lead`, hoặc `admin`. Xem [[04_Authentication/User_Roles]].

## Các bước thực hiện
1. Vào trang **Problem Feed** (route `/problems`).
2. Click nút **"Đăng vấn đề"** ở góc trên bên phải.
3. Điền form:
   - **Tiêu đề**: Tối đa 200 ký tự, ngắn gọn, mô tả điểm nghẽn.
   - **Tóm tắt**: Ngắn gọn nội dung chính (optional).
   - **Nội dung**: Rich text editor (TipTap), hỗ trợ format, hình ảnh.
   - **Category**: Chọn từ `Process`, `Technical`, `People`, `Tools`, `Patent`.
   - **Privacy**: `public` (toàn bộ) hoặc `private` (chỉ admin + người được share).
4. Click **"Đăng"**. Hệ thống tạo Problem với `status = "open"`.

## Hệ quả
- Problem xuất hiện trên Problem Feed theo thứ tự thời gian giảm dần.
- Người khác có thể comment hoặc reaction ngay lập tức.
- Status tự động chuyển theo tương tác: xem [[01_Problem_Feed/Problem_Status_Workflow]].

## API liên quan
- `POST /api/v1/problems` — Xem chi tiết: [[07_API_Reference/Problem_Endpoints]]
- Body: `{ title, summary?, content, category, visibility?, shared_user_ids? }`

## Mối liên hệ
- Problem có thể tạo [[02_Idea_Lab/Create_Brainstorm_Room]] trực tiếp từ trang chi tiết.
- Xem [[01_Problem_Feed/Problem_Privacy]] để hiểu quyền xem bài đăng.
