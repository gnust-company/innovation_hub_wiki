---
type: atomic-note
category: Architecture
related: ["MOC_Architecture", "Clean_Architecture", "Chat_Endpoints"]
tags: [chat, architecture, sse, integration]
updated: 2026-05-10
---

# Chat Integration

## Tổng quan kiến trúc

Chat module gồm 3 thành phần chính:

```
┌─────────────────┐     HTTP/SSE      ┌─────────────────┐
│   Hub Frontend  │ ◄──────────────►  │   Hub Backend   │
│  (React + Vite) │                   │  (FastAPI)      │
└─────────────────┘                   └────────┬────────┘
                                               │
                                               │ HTTP/SSE + X-API-Key
                                               ▼
                                      ┌─────────────────┐
                                      │   Agent BE      │
                                      │  (LangGraph)    │
                                      └────────┬────────┘
                                               │ read-only
                                               ▼
                                      ┌─────────────────┐
                                      │   Wiki Vault    │
                                      │  (Obsidian .md) │
                                      └─────────────────┘
```

## Hub Backend — Session & Message Persistence

Hub BE owns **toàn bộ lịch sử chat** trong PostgreSQL.

### Database
- `chat_sessions` — session metadata (`id`, `user_id`, `title`, `created_at`, `updated_at`)
- `chat_messages` — message content (`id`, `session_id`, `role`, `content`, `sources`, `created_at`)

### API Layer
- Router tại `/api/v1/chat` (nằm trong API v1 router, cùng prefix với các module khác).
- 7 endpoints: CRUD session + list/send message + key-help-url.

## SSE Proxy Flow

Khi user gửi message:

1. **Validate** — Session phải thuộc về current user.
2. **Persist user message** — Lưu vào `chat_messages` với `role = "user"`.
3. **Build payload** — Gom toàn bộ history của session thành `messages[]` array.
4. **Proxy to Agent BE** — Gọi `POST {AGENT_BASE_URL}/api/chat/stream` với:
   - `X-API-Key` header (shared secret)
   - `messages[]` array (full conversation)
   - `thread_id` = `session_id` (để trace trong LangFuse)
5. **Stream response** — Nhận SSE từ Agent BE, forward từng event về frontend.
6. **Persist assistant message** — Khi stream kết thúc, lưu assistant response vào `chat_messages` với `role = "assistant"` và `sources` (wiki files đã tham chiếu).

## Agent BE Integration

Agent BE là **stateless** microservice:
- Không lưu trữ conversation state giữa các request.
- Mỗi request nhận full `messages[]` từ Hub BE.
- Dùng LangGraph ReAct để đọc wiki files qua 4 tools (`read_file`, `list_directory`, `search_wiki`, `resolve_wikilink`).

Xem chi tiết: [[00_Index/AGENT_GUIDE]] và `innovation_hub_agent/docs/AGENT_ARCHITECTURE.md`.

## Internal Services

### AgentProxyService
- Nằm trong Application Layer của Hub BE.
- Dùng `httpx` (async HTTP client) để gọi Agent BE.
- Xử lý retry, timeout, và error mapping.

## Mối liên hệ
- [[API_Reference/Chat_Endpoints]] — Endpoint specification.
- [[Architecture/Database_Schema]] — Chat tables schema.
- [[Architecture/Clean_Architecture]] — Vị trí service trong architecture.
- [[00_Index/AGENT_GUIDE]] — Cách Agent BE hoạt động.
