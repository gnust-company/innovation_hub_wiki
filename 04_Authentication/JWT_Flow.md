---
type: atomic-note
category: Authentication
related: ["User_Roles", "Auth_Endpoints", "MOC_Auth"]
tags: [auth, jwt]
updated: 2026-04-28
---

# JWT Flow

## Tổng quan
Innovation Hub dùng JWT (JSON Web Token) cho authentication.

## Token Types

### Access Token
- **Lifetime**: 30 phút.
- **Dùng cho**: Mọi API request (header `Authorization: Bearer <token>`).
- **Payload**: `sub` (user_id), `type: "access"`, `exp`, `iat`.

### Refresh Token
- **Lifetime**: 7 ngày.
- **Dùng cho**: Lấy access token mới khi hết hạn.
- **Payload**: `sub` (user_id), `type: "refresh"`, `exp`, `iat`.

## Lifecycle
1. User login → nhận access_token + refresh_token.
2. Mỗi request gửi access_token trong header.
3. Access token hết hạn (401) → FE tự động gọi refresh endpoint.
4. Refresh thành công → access_token mới, tiếp tục request.
5. Refresh token hết hạn → user phải đăng nhập lại.

## Frontend handling
- Axios interceptor tự động:
  - Gắn access token vào request header.
  - Bắt 401 → gọi refresh → retry request.
  - Refresh cũng fail → redirect `/login`.

## API
- `POST /api/v1/auth/login` — Login, nhận tokens.
- `POST /api/v1/auth/refresh` — Refresh access token.
- Xem [[07_API_Reference/Auth_Endpoints]].

## Mối liên hệ
- [[04_Authentication/User_Roles]] — Role được encode trong token.
- [[04_Authentication/MOC_Auth]] — Tổng quan Auth.
