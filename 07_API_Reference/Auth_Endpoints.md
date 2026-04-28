---
type: reference
category: API
related: ["MOC_API", "JWT_Flow", "User_Roles"]
tags: [api, auth]
updated: 2026-04-28
---

# Auth Endpoints

Base path: `/api/v1/auth`

## POST /auth/register
Đăng ký user mới.

**Request body:**
```json
{
  "username": "string (required)",
  "password": "string (required)",
  "email": "string? (must contain @)",
  "full_name": "string?",
  "team": "string?"
}
```

**Response:** `200 OK` — `{ access_token, refresh_token, user }`

## POST /auth/login
Đăng nhập.

**Request body:**
```json
{ "username": "string", "password": "string" }
```

**Response:** `200 OK` — `{ access_token, refresh_token, user }`

## GET /auth/me
Lấy thông tin user hiện tại.

**Auth:** Bearer token required.

**Response:** `200 OK` — UserResponseDTO

## POST /auth/refresh
Refresh access token.

**Request body:**
```json
{ "refresh_token": "string" }
```

**Response:** `200 OK` — `{ access_token, refresh_token, user }`

## PUT /auth/password
Đổi mật khẩu.

**Auth:** Bearer token required.

**Request body:**
```json
{ "old_password": "string", "new_password": "string" }
```

**Response:** `200 OK` — `{ "message": "Password updated successfully" }`

## Mối liên hệ
- [[04_Authentication/JWT_Flow]] — Token lifecycle.
- [[04_Authentication/User_Roles]] — Roles.
