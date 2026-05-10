---
type: meta
category: Review
tags: [review, audit, accuracy]
updated: 2026-05-10
---

# Wiki Review Report — Innovation Hub Wiki

> Ngày review: 2026-05-10
> So sánh với: `innovation_hub` (backend + frontend) và `innovation_hub_agent` (Agent BE)
> Nguồn sự thật chính: `innovation_hub/API_CONTRACT.md` + codebase thực tế

---

## 1. Tóm tắt đánh giá

### Điểm mạnh
- **Cấu trúc Zettelkasten rất tốt** cho RAG — MOCs, atomic notes, wikilinks giúp Agent BE điều hướng hiệu quả.
- **Database Schema** chính xác ~95% — đầy đủ các bảng chính, kiểu dữ liệu, mối quan hệ.
- **API Reference** cấu trúc rõ ràng, gần như đầy đủ các nhóm endpoint chính.
- **Status workflows, Privacy model, Auth/Permission** mô tả chính xác.
- **Chat Integration** mô tả đúng kiến trúc SSE proxy và Agent BE.

### Điểm yếu
- **1 lỗi NGHIÊM TRỌNG** về tên Scoring Criteria — sẽ khiến chatbot trả lờI sai khi được hỏi về event scoring.
- Nhiều điểm **thiếu technical details** (Agent model name, per-request LLM key, frontend architecture, testing, env vars).
- **Một số endpoint bị thiếu** trong API_Reference so với API_CONTRACT.md.
- **Frontend docs gần như không tồn tại** trong wiki (chỉ có User_Guide cơ bản).

---

## 2. Lỗi SAI — Cần sửa ngay

### 🔴 CRITICAL: Scoring Criteria Names sai hoàn toàn
**File:** `03_Events/Scoring_System.md`

Wiki ghi:
| # | Group | Name (SAI) |
|---|-------|------------|
| 1 | problem | Clarity of Problem Definition |
| 2 | problem | Validity of User Scenarios |
| 3 | problem | Measurability of User Expectations |
| 4 | problem | Depth of Research |
| 5 | solution | Innovation & Creativity |
| 6 | solution | Feasibility & Implementation Plan |
| 7 | solution | Impact & Value |
| 8 | solution | Scalability & Sustainability |

**Thực tế trong backend** (`backend/app/application/use_cases/event_scoring/create_criteria.py` + `API_CONTRACT.md`):
| # | Group | Name (ĐÚNG) |
|---|-------|-------------|
| 1 | problem | Unresolved Problem |
| 2 | problem | Root Cause Analysis |
| 3 | problem | Problem Recognition |
| 4 | problem | Gap Evidence |
| 5 | solution | Novelty |
| 6 | solution | Root Cause Resolution |
| 7 | solution | Competitive Advantage |
| 8 | solution | Technical Feasibility |

**Hậu quả:** Chatbot sẽ bịa đặt tên criteria hoàn toàn sai nếu dựa vào wiki. Cần sửa ngay.

---

### 🟡 HIGH: API_Contract_Summary thiếu endpoint / bảng endpoint count không chính xác
**File:** `Architecture/API_Contract_Summary.md`

- Ghi "Total: ~100 endpoints" nhưng thực tế API_CONTRACT.md có >120 endpoint definitions (bao gồm nested resource endpoints).
- Thiếu liệt kê endpoint `/auth/me` (tồn tại trong backend: `auth.py:84` và `users.py:36`).

---

### 🟡 HIGH: API_CONTRACT.md thiếu `GET /auth/me`
**File:** `innovation_hub/API_CONTRACT.md` (không thuộc wiki nhưng là SSOT)

- Section 1 (AUTH) không có `GET /auth/me`, nhưng backend có endpoint này.
- Wiki `Auth_Endpoints.md` có đề cập đúng → Wiki đúng, API_CONTRACT thiếu.

---

### 🟡 MEDIUM: Problem Status Workflow thiếu chi tiết transition
**File:** `01_Problem_Feed/Problem_Status_Workflow.md`

- Wiki ghi: "`open` → `discussing` → `brainstorming` → `solved` / `closed`"
- Thực tế: `solved` và `closed` là **2 trạng thái terminal ngang hàng**, không phải `solved` rồi mới `closed`.
- Thiếu ghi chú: "Khi problem ở `solved` hoặc `closed`, không thể tạo brainstorm room mới".

---

### 🟡 MEDIUM: Team Formation — thiếu constraint quan trọng
**File:** `03_Events/Team_Formation.md`

- Thiếu ghi chú: "User chưa thuộc team nào trong event mới được tạo/join team".
- Thiếu ghi chú: "Không thể tự chấm team của mình (`team_id != target_team_id`)".

---

### 🟢 LOW: OKR Tracking — KR3 định nghĩa mơ hồ
**File:** `05_Dashboard/OKR_Tracking.md`

- "KR3: 20% converted to pilot — Ideas có status 'submitted' hoặc higher"
- "Submitted hoặc higher" không rõ ràng vì `submitted` là terminal status, không có "higher".
- Nên sửa thành: "Ideas có status 'submitted' trong Event hoặc 'submitted' trong Room".

---

## 3. Điểm THIẾU — Cần bổ sung

### 🔴 Thiếu tài liệu Agent BE chi tiết
**Cần tạo file mới hoặc bổ sung:**

| Thông tin thiếu | Vị trí đề xuất | Chi tiết |
|-----------------|----------------|----------|
| Model name (`moonshotai/kimi-k2.5`) | `Architecture/Chat_Integration.md` | Agent BE dùng NVIDIA NIM với model này |
| `X-LLM-API-Key` header | `Architecture/Chat_Integration.md` | Per-request API key, user bring-your-own-key |
| LangFuse monitoring | `Architecture/Chat_Integration.md` | Optional tracing, `LANGFUSE_*` env vars |
| `AGENT_API_KEY` fail-fast | `Architecture/Chat_Integration.md` | Service crash nếu thiếu |
| Path traversal protection | `Architecture/Chat_Integration.md` | `WikiFilesystem._is_safe()` |
| `AGENT_ALLOWED_IPS` / `AGENT_CORS_ORIGINS` | `Architecture/Chat_Integration.md` | Security config |

---

### 🟡 Thiếu Frontend Architecture docs
**Cần tạo folder/file mới:**

| Thông tin thiếu | Vị trí đề xuất |
|-----------------|----------------|
| Tech stack chi tiết (Zustand, React Router, Axios, Recharts, Framer Motion, i18n) | `Architecture/Frontend_Architecture.md` |
| Zustand stores (authStore, chatStore, notificationStore, problemStore, uiStore) | `Architecture/Frontend_Architecture.md` |
| Routing table đầy đủ (`/problems/new`, `/problems/:id/edit`, `/ideas/:id/edit`, `/admin/users`, `/help`, etc.) | `Architecture/Frontend_Architecture.md` hoặc `User_Guide/MOC_User_Guide.md` |
| Component structure (layout, pages, ui, aceternity) | `Architecture/Frontend_Architecture.md` |
| TipTap ResizableImageExtension | `Architecture/TipTap_Integration.md` |

---

### 🟡 Thiếu Environment Variables docs
**Cần tạo file mới:** `Architecture/Environment_Variables.md`

| Dự án | Biến thiếu trong wiki |
|-------|----------------------|
| Hub Backend | `DATABASE_URL`, `JWT_SECRET`, `JWT_ALGORITHM`, `MINIO_*`, `AGENT_BASE_URL`, `AGENT_API_KEY` |
| Hub Frontend | `VITE_API_BASE_URL`, `VITE_AGENT_BASE_URL` |
| Agent BE | `NVIDIA_API_KEY`, `WIKI_PATH`, `AGENT_API_KEY`, `MODEL_NAME`, `NVIDIA_BASE_URL`, `MAX_TOOL_CALLS`, `MAX_DEPTH`, `MAX_TOKENS`, `LLM_MAX_RETRIES`, `TEMPERATURE`, `TOOL_TIMEOUT_SECONDS`, `LOG_LEVEL`, `LANGFUSE_*`, `AGENT_CORS_ORIGINS`, `AGENT_ALLOWED_IPS` |

---

### 🟡 Thiếu Database Constraints & Indexes
**File:** `Architecture/Database_Schema.md`

- Thiếu `UNIQUE(user_id, event_id)` trên `event_team_members`.
- Thiếu `UNIQUE(event_idea_id, scorer_team_id)` trên `event_scores`.
- Thiếu indexes: `chat_sessions(user_id)`, `chat_messages(session_id, created_at)`.
- Thiếu `CHECK(role IN ('user', 'assistant'))` trên `chat_messages`.

---

### 🟡 Thiếu Response Enrichment docs
**Cần bổ sung:** `Architecture/Response_Enrichment.md`

- `ProblemObject` được enrich với: `likes_count`, `dislikes_count`, `insights_count`, `comments_count`, `user_reaction`, `rooms` (list), `room_id` (first room).
- `IdeaObject` được enrich với: `vote_avg`, `vote_count`, `comments_count`, `user_reaction`, `user_vote`.
- `RoomObject` được enrich với: `idea_count`, `participant_count`, `creator`.
- `EventObject` được enrich với: `team_count`, `idea_count`.

---

### 🟢 Thiếu Testing docs
**Cần tạo:** `Misc/Testing.md`

- Backend: pytest, FastAPI TestClient, mocked env vars.
- Frontend: (chưa rõ test setup, cần kiểm tra).
- Agent BE: `FastAPI.TestClient`, `tmp_wiki` fixture, mocked LLM.

---

### 🟢 Thiếu Deployment / Docker docs
**Cần tạo:** `Architecture/Deployment.md`

- Root `docker-compose.yml` orchestrates: PostgreSQL, MinIO, Backend, Frontend (Nginx).
- Agent BE `docker-compose.yml` defines external network `innovation_hub_network`.
- Ports: Backend 8000, Frontend 5173 (dev) / 80 (prod), MinIO 9000/9001, PostgreSQL 5432.

---

### 🟢 Thiếu Notification Polling mechanism
**Cần bổ sung:** `Architecture/Notification_System.md`

- Wiki chỉ nói "Frontend poll endpoint định kỳ".
- Cần bổ sung: Không dùng WebSocket, dùng polling `GET /notifications/unread-count`.

---

### 🟢 Thiếu i18n docs
**Cần tạo:** `Architecture/Internationalization.md`

- Frontend dùng `react-i18next` với 2 ngôn ngữ: EN, VI.
- Settings page cho phép switch language.

---

## 4. Điểm CẦN CẢI THIỆN

### Cấu trúc & Navigation
1. **MOC_User_Guide.md** thiếu nhiều routes quan trọng (`/problems/new`, `/problems/:id/edit`, `/ideas/:id/edit`, `/admin/users`, `/help`).
2. **README.md** của wiki nên thêm liên kết trực tiếp đến `API_Reference/MOC_API` và `Architecture/MOC_Architecture`.
3. Nên có file `Architecture/Frontend_Architecture.md` để cân bằng với `FastAPI_Structure.md`.

### Độ chính xác
4. **Scoring_System.md** cần cập nhật lại criteria names và descriptions theo `create_criteria.py`.
5. **API_Contract_Summary.md** cần cập nhật số endpoint chính xác và thêm `/auth/me`.
6. **Problem_Status_Workflow.md** cần làm rõ `solved` và `closed` là terminal ngang hàng.
7. **Event_Lifecycle.md** nên bổ sung: "Khi event `closed`, tất cả write APIs trả về 403".

### Completeness cho Chatbot
8. **AGENT_GUIDE.md** rất tốt nhưng cần bổ sung:
   - "Nếu câu hỏi về scoring criteria → đọc `03_Events/Scoring_System`" (sau khi sửa).
   - "Nếu câu hỏi về env vars → đọc `Architecture/Environment_Variables`" (khi tạo xong).
9. **Glossary.md** thiếu một số thuật ngữ:
   - `Zustand`, `Recharts`, `Framer Motion`, `Axios`, `react-hook-form`.
   - `SSE` đã có, nhưng thiếu `NVIDIA NIM`, `LangFuse`.

### Cross-references
10. **Architecture/Chat_Integration.md** nên link đến `innovation_hub_agent/docs/AGENT_ARCHITECTURE.md` (file tồn tại trong agent repo).
11. **API_Reference/Event_Endpoints.md** nên có bảng phân quyền chi tiết giống API_CONTRACT Section 23.

---

## 5. So sánh nhanh: Wiki vs Codebase

| Chủ đề | Wiki | Codebase | Kết luận |
|--------|------|----------|----------|
| Tech Stack (BE) | Python 3.11, FastAPI, SQLAlchemy 2.0, PostgreSQL 16 | ✅ Khớp | ✅ Đúng |
| Tech Stack (FE) | React 18, Vite, Tailwind, TipTap | ✅ Khớp (chi tiết hơn trong codebase) | ✅ Đúng |
| Database — bảng | Đầy đủ 17 bảng chính | ✅ Khớp | ✅ Đúng |
| Database — M2M | `problem_shared_users`, `room_shared_users` | ✅ Khớp | ✅ Đúng |
| Auth — JWT lifetime | Access 30 phút, Refresh 7 ngày | ✅ Khớp | ✅ Đúng |
| Auth — Roles | member, admin, team_lead (event-specific) | ✅ Khớp | ✅ Đúng |
| Privacy — Problem/Room | Độc lập, Idea kế thừa Room | ✅ Khớp | ✅ Đúng |
| Problem Status | open → discussing → brainstorming → solved/closed | ✅ Khớp (thiếu chi tiết edge case) | ⚠️ Cần bổ sung |
| Idea Status | draft ↔ refining ↔ reviewing → submitted/closed | ✅ Khớp | ✅ Đúng |
| Event Status | draft → active → closed | ✅ Khớp | ✅ Đúng |
| Reactions | like, dislike, insight | ✅ Khớp | ✅ Đúng |
| Votes | 1-5 stars | ✅ Khớp | ✅ Đúng |
| Scoring — 8 criteria | ❌ **Sai tên** | ✅ 8 criteria cụ thể | 🔴 **Sai** |
| Scoring — Likert Scale | 2.5, 5, 7.5, 10, 12.5 | ✅ Khớp | ✅ Đúng |
| Chat — SSE Proxy | ✅ Mô tả đúng | ✅ Khớp | ✅ Đúng |
| Chat — DB tables | `chat_sessions`, `chat_messages` | ✅ Khớp | ✅ Đúng |
| Agent BE — Model | Không đề cập | `moonshotai/kimi-k2.5` | ⚠️ Thiếu |
| Agent BE — Tools | read_file, list_directory, search_wiki, resolve_wikilink | ✅ Khớp | ✅ Đúng |
| Agent BE — X-LLM-API-Key | Không đề cập | ✅ Có | ⚠️ Thiếu |
| Frontend — Routes | Thiếu ~8 routes | ✅ Đầy đủ trong App.tsx | ⚠️ Thiếu |
| Frontend — i18n | Không đề cập | ✅ react-i18next EN/VI | ⚠️ Thiếu |
| Frontend — Zustand | Không đề cập | ✅ 5 stores | ⚠️ Thiếu |
| MinIO — Bucket | `avatars` | ✅ Khớp | ✅ Đúng |
| Uploads — Avatar | Max 10MB, JPEG/PNG/WebP | ✅ Khớp | ✅ Đúng |
| Notifications — Polling | "Poll endpoint định kỳ" | ✅ Khớp (không WebSocket) | ⚠️ Cần chi tiết hơn |

---

## 6. Khuyến nghị hành động

### Sửa ngay (P0) ✅ ĐÃ XONG
1. [x] Sửa `03_Events/Scoring_System.md` — cập nhật 8 criteria names và descriptions đúng theo backend.
2. [x] Sửa `Architecture/API_Contract_Summary.md` — cập nhật endpoint count (~95 logical endpoints).
3. [x] Sửa `01_Problem_Feed/Problem_Status_Workflow.md` — làm rõ `solved`/`closed` là terminal ngang hàng, thêm ghi chú "không tạo room mới".
4. [x] Thêm `GET /auth/me` vào `innovation_hub/API_CONTRACT.md` (SSOT).

### Bổ sung trong tuần (P1) ✅ ĐÃ XONG
5. [x] Tạo `Architecture/Frontend_Architecture.md` — tech stack, stores, routing, component structure.
6. [x] Tạo `Architecture/Environment_Variables.md` — đầy đủ env vars cho cả 3 dịch vụ + Docker ports.
7. [x] Bổ sung `Architecture/Database_Schema.md` — constraints, indexes, CHECK constraints.
8. [x] Cập nhật `Architecture/MOC_Architecture.md` — link đến 2 file mới.

### Cải thiện dần (P2) ✅ ĐÃ XONG
9. [x] Cập nhật `Misc/Glossary.md` — thêm Zustand, Recharts, Framer Motion, LangFuse, NVIDIA NIM, X-LLM-API-Key.
10. [x] Cập nhật `00_Index/AGENT_GUIDE.md` — bổ sung tips tìm kiếm cho scoring criteria, env vars, frontend.

### Còn lại (có thể làm sau)
11. [ ] Tạo `Architecture/Response_Enrichment.md` — computed fields trên API responses.
12. [ ] Tạo `Misc/Testing.md` — test strategy cho cả 3 dự án.
13. [ ] Tạo `Architecture/Deployment.md` — Docker Compose, ports, network chi tiết.
14. [ ] Tạo `Architecture/Internationalization.md` — i18n setup.
15. [ ] Cập nhật `User_Guide/MOC_User_Guide.md` — bổ sung routes còn thiếu.
16. [ ] Bổ sung `Architecture/Chat_Integration.md` — model name, `X-LLM-API-Key`, LangFuse, security config.

---

## 7. Kết luận

Wiki hiện tại **đủ tốt để chatbot hoạt động cơ bản** cho các câu hỏi về Problem Feed, Idea Lab, Auth, Chat, Privacy. Tuy nhiên, có **1 lỗi nghiêm trọng về Scoring Criteria** sẽ khiến chatbot trả lời sai khi được hỏi về event scoring. Ngoài ra, wiki **thiếu nhiều thông tin technical** về frontend architecture, environment variables, và agent BE config — khiến developer khó tra cứu toàn diện.

**Điểm số đánh giá:**
- **Độ chính xác:** 7.5/10 (trừ điểm lớn vì scoring criteria sai)
- **Độ đầy đủ:** 6/10 (thiếu nhiều technical docs, frontend, testing, deployment)
- **Khả năng hỗ trợ Chatbot:** 7/10 (tốt cho user questions, kém cho technical deep-dives)
- **Khả năng hỗ trợ Developer:** 6/10 (thiếu frontend arch, env vars, deployment)

**Đề xuất:** Ưu tiên sửa scoring criteria, sau đó bổ sung frontend architecture và environment variables.
