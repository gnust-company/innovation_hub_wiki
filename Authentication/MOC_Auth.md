---
type: moc
category: Authentication
related: ["MOC_Overview", "User_Roles", "Auth_Endpoints"]
tags: [auth, index]
updated: 2026-04-28
---

# MOC Auth

Authentication & Authorization trong Innovation Hub.

## Các khía cạnh
- [[Authentication/JWT_Flow]] — Access token + Refresh token lifecycle
- [[Authentication/User_Roles]] — Phân quyền: member, admin (team_lead là event-specific)
- [[Authentication/Permission_Matrix]] — Bảng quyền chi tiết cho từng role

## Mối liên hệ
- Auth bảo vệ tất cả API endpoints. Xem [[API_Reference/Auth_Endpoints]].
- Role ảnh hưởng quyền trên mọi feature: [[01_Problem_Feed/MOC_Problem_Feed]], [[02_Idea_Lab/MOC_Idea_Lab]], [[03_Events/MOC_Events]].
- Xem [[Architecture/Privacy_Model]] cho quyền xem nội dung.
