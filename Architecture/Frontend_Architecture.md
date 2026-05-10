---
type: atomic-note
category: Architecture
related: ["FastAPI_Structure", "MOC_Architecture", "TipTap_Integration"]
tags: [architecture, frontend, react]
updated: 2026-05-10
---

# Frontend Architecture

## Tech Stack

| Công nghệ | Phiên bản | Mục đích |
|-----------|-----------|----------|
| React | 18.2 | UI framework |
| TypeScript | 5.2 | Type safety |
| Vite | 5.1.4 | Build tool & dev server |
| Tailwind CSS | 3.4.1 | Styling (custom "Clay" design system) |
| Zustand | 4.5.2 | State management |
| React Router | v6 | Client-side routing |
| Axios | 1.6.7 | HTTP client (with JWT refresh interceptors) |
| react-hook-form | 7.51 | Form handling |
| Zod | 3.22 | Schema validation |
| TipTap | 3.20 | Rich text editor ecosystem |
| Recharts | 2.12 | Charts & analytics |
| Framer Motion | 11.0 | Animations |
| react-i18next | 16.6 | Internationalization (EN + VI) |
| lucide-react | 0.344 | Icons |

## Folder Structure

```
frontend/src/
├── api/                    # API client modules
│   ├── client.ts          # Axios instance + JWT refresh interceptor
│   ├── auth.ts, problems.ts, rooms.ts, ideas.ts, comments.ts,
│   ├── dashboard.ts, uploads.ts, notifications.ts, users.ts,
│   ├── events.ts, chat.ts, index.ts
├── components/
│   ├── chat/              # Chat panel, messages, sidebar, bubble button
│   ├── common/            # ProblemCard
│   ├── feedback/          # Toast notifications
│   ├── layout/            # MainLayout, Header, Sidebar, AuthGuard
│   ├── notifications/     # NotificationDropdown
│   └── ui/                # Base UI components + TipTap extensions
│       └── aceternity/    # AuroraBackground, ShimmerButton, SpotlightCard, TextGenerateEffect
├── pages/                 # Route-level page components
│   ├── Landing/
│   ├── Login/
│   ├── Register/
│   ├── Home/              # User dashboard
│   ├── Dashboard/         # Admin analytics
│   ├── ProblemFeed/
│   ├── ProblemDetail/
│   ├── IdeaLab/
│   ├── RoomDetail/
│   ├── IdeaDetail/
│   ├── Events/
│   ├── EventDetail/       # Tabs: Introduction, Teams, Ideas, Dashboard, FAQ, Awards
│   ├── Admin/             # AdminUsersPage
│   ├── Settings/          # UserSettingsPage (profile, i18n, password)
│   └── Help/
├── stores/                # Zustand stores
│   ├── authStore.ts       # Auth state, login/register/logout
│   ├── chatStore.ts       # Chat sessions/messages
│   ├── notificationStore.ts
│   ├── problemStore.ts
│   └── uiStore.ts
├── i18n/                  # react-i18next setup
│   ├── index.ts
│   └── locales/           # en.json, vi.json
├── types/                 # TypeScript definitions
├── utils/                 # Constants, helpers, TipTap utilities
└── styles/                # globals.css
```

## Routing Table

| Path | Page | Auth |
|------|------|------|
| `/login`, `/register` | LoginPage, RegisterPage | Public |
| `/` | LandingPage | Public |
| `/dashboard` | UserDashboardPage | Protected |
| `/admin` | Admin DashboardPage | Admin only |
| `/admin/users` | AdminUsersPage | Admin only |
| `/problems` | ProblemFeedPage | Protected |
| `/problems/new` | CreateProblemPage | Protected |
| `/problems/:id` | ProblemDetailPage | Protected |
| `/problems/:id/edit` | EditProblemPage | Owner/Admin |
| `/rooms` | IdeaLabPage | Protected |
| `/rooms/:id` | RoomDetailPage | Protected |
| `/rooms/:roomId/ideas/new` | CreateIdeaPage | Protected |
| `/ideas/:id` | IdeaDetailPage | Protected |
| `/ideas/:id/edit` | EditIdeaPage | Owner/Admin |
| `/events` | EventsPage | Protected |
| `/events/:id` | EventDetailPage | Protected |
| `/events/:id/ideas/:ideaId` | EventDetailPage (idea focus) | Protected |
| `/settings` | UserSettingsPage | Protected |
| `/help` | HelpPage | Protected |

> Protected routes wrapped in `AuthGuard` + `MainLayout`.

## State Management (Zustand)

### authStore
- `user`, `isAuthenticated`, `login()`, `register()`, `logout()`
- Tự động refresh token qua Axios interceptor

### chatStore
- `sessions`, `activeSessionId`, `messages`
- Load history, send message (SSE streaming), rename/delete session

### notificationStore
- `notifications`, `unreadCount`
- Polling (không dùng WebSocket)

### problemStore
- Problem list, filters, sorting

### uiStore
- Sidebar state, theme, toasts

## Key Patterns

### JWT Refresh Interceptor
Axios interceptor trong `client.ts`:
1. Gắn access token vào mọi request.
2. Bắt 401 → gọi `POST /auth/refresh` → retry request.
3. Refresh fail → redirect `/login`.

### TipTap Integration
- Editor: `RichTextEditor` component dùng TipTap v3.20 với image, link, placeholder.
- Renderer: `TipTapRenderer` chuyển JSONB → HTML.
- Image resize: `ResizableImageExtension` custom.
- Storage: JSONB trong PostgreSQL (không lưu HTML).

### i18n
- `react-i18next` với 2 locales: `en`, `vi`.
- Switch language trong Settings page.
- Default: Vietnamese.

## Mối liên hệ
- [[Architecture/FastAPI_Structure]] — Backend counterpart.
- [[Architecture/TipTap_Integration]] — Rich text JSONB pattern.
- [[API_Reference/MOC_API]] — API endpoints FE gọi.
- [[User_Guide/MOC_User_Guide]] — Routes mapping với user flows.
