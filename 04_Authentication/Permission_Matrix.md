---
type: atomic-note
category: Authentication
related: ["User_Roles", "Privacy_Model", "MOC_Auth"]
tags: [auth, permissions]
updated: 2026-04-28
---

# Permission Matrix

## Problem Feed
| Action | Member | Admin |
|--------|--------|-------|
| Xem problems (public) | ✅ | ✅ |
| Xem problems (private của người khác) | ❌ | ✅ |
| Tạo problem | ✅ | ✅ |
| Sửa problem | Chỉ của mình | ✅ (mọi problem) |
| Xóa problem | Chỉ của mình | ✅ |
| Thay đổi status | Chỉ của mình | ✅ |

## Idea Lab
| Action | Member | Admin |
|--------|--------|-------|
| Tạo room | ✅ | ✅ |
| Sửa/xóa room | Chỉ của mình | ✅ |
| Tạo idea trong room | ✅ | ✅ |
| Sửa/xóa idea | Chỉ của mình | ✅ |
| Vote/Reaction | ✅ | ✅ |

## Events
| Action | Member | Admin |
|--------|--------|-------|
| Tạo event | ❌ | ✅ |
| Update/close event | ❌ | ✅ |
| Tạo team | ✅ | ✅ |
| Join team | ✅ | ✅ |
| Submit idea | ✅ (team member) | ✅ |
| Chấm điểm | ✅ (team lead, nếu assign) | ✅ |
| Tạo award | ❌ | ✅ |
| Tạo FAQ | ❌ | ✅ (team lead cũng được) |

## User Management
| Action | Member | Admin |
|--------|--------|-------|
| Xem profile mình | ✅ | ✅ |
| Sửa profile mình | ✅ | ✅ |
| Xem danh sách users | ❌ | ✅ |
| Sửa role user | ❌ | ✅ |
| Deactivate user | ❌ | ✅ |
| Reset password user | ❌ | ✅ |

## Mối liên hệ
- [[04_Authentication/User_Roles]] — Định nghĩa roles.
- [[06_Architecture/Privacy_Model]] — Quyền xem nội dung private.
