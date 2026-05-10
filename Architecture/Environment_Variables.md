---
type: reference
category: Architecture
related: ["MOC_Architecture", "FastAPI_Structure", "Chat_Integration"]
tags: [architecture, env, configuration]
updated: 2026-05-10
---

# Environment Variables

## Innovation Hub Backend (`innovation_hub/backend/.env`)

| Variable | Required | Default | Mô tả |
|----------|----------|---------|-------|
| `DATABASE_URL` | ✅ | — | PostgreSQL connection string (asyncpg) |
| `JWT_SECRET` | ✅ | — | Secret key cho JWT signing |
| `JWT_ALGORITHM` | ❌ | `HS256` | JWT algorithm |
| `ACCESS_TOKEN_EXPIRE_MINUTES` | ❌ | `30` | Access token lifetime (phút) |
| `REFRESH_TOKEN_EXPIRE_DAYS` | ❌ | `7` | Refresh token lifetime (ngày) |
| `MINIO_ENDPOINT` | ✅ | — | MinIO host (e.g. `minio:9000`) |
| `MINIO_ACCESS_KEY` | ✅ | — | MinIO access key |
| `MINIO_SECRET_KEY` | ✅ | — | MinIO secret key |
| `MINIO_BUCKET_NAME` | ❌ | `avatars` | Default bucket |
| `AGENT_BASE_URL` | ✅ | — | URL đến Agent BE (e.g. `http://agent-be:8000`) |
| `AGENT_API_KEY` | ✅ | — | Shared secret để gọi Agent BE |
| `CORS_ORIGINS` | ❌ | `*` | Allowed CORS origins (comma-separated) |
| `LOG_LEVEL` | ❌ | `INFO` | Logging level |

## Innovation Hub Frontend (`innovation_hub/frontend/.env`)

| Variable | Required | Default | Mô tả |
|----------|----------|---------|-------|
| `VITE_API_BASE_URL` | ✅ | — | Base URL của Hub Backend (e.g. `http://localhost:8000`) |
| `VITE_AGENT_BASE_URL` | ❌ | — | Base URL của Agent BE (nếu FE cần gọi trực tiếp) |

## Agent BE (`innovation_hub_agent/.env`)

| Variable | Required | Default | Mô tả |
|----------|----------|---------|-------|
| `NVIDIA_API_KEY` | ✅ (CLI) | — | NVIDIA NIM API key (cho CLI mode) |
| `WIKI_PATH` | ✅ | — | Absolute path đến `innovation_hub_wiki` vault |
| `AGENT_API_KEY` | ✅ | — | Shared secret cho Hub BE auth. **Service crash nếu thiếu.** |
| `AGENT_ENV` | ❌ | `development` | `production` disables Swagger/ReDoc, enables JSON logging |
| `MODEL_NAME` | ❌ | `moonshotai/kimi-k2.5` | LLM model identifier |
| `NVIDIA_BASE_URL` | ❌ | `https://integrate.api.nvidia.com/v1` | LLM API base URL |
| `MAX_TOOL_CALLS` | ❌ | `10` | Max agent iterations (recursion limit) |
| `MAX_DEPTH` | ❌ | `3` | Max wiki link follow depth |
| `MAX_TOKENS` | ❌ | `4096` | Max response tokens |
| `LLM_MAX_RETRIES` | ❌ | `3` | LLM call retries |
| `TEMPERATURE` | ❌ | `0.0` | Sampling temperature |
| `TOOL_TIMEOUT_SECONDS` | ❌ | `30` | Per-tool timeout |
| `LOG_LEVEL` | ❌ | `INFO` | Logging level |
| `LANGFUSE_PUBLIC_KEY` | ❌ | — | LangFuse tracing (optional) |
| `LANGFUSE_SECRET_KEY` | ❌ | — | LangFuse tracing (optional) |
| `LANGFUSE_HOST` | ❌ | — | LangFuse host URL |
| `AGENT_CORS_ORIGINS` | ❌ | — | Comma-separated CORS allowlist |
| `AGENT_ALLOWED_IPS` | ❌ | — | Comma-separated IP allowlist |

## Docker Compose Ports

| Service | Port | Mô tả |
|---------|------|-------|
| PostgreSQL | `5432` | Database |
| Hub Backend | `8000` | FastAPI API |
| Hub Frontend (dev) | `5173` | Vite dev server |
| Hub Frontend (prod) | `80` | Nginx static serve |
| MinIO API | `9000` | S3-compatible API |
| MinIO Console | `9001` | Web admin UI |
| Agent BE | `8000` | FastAPI Agent (trong container riêng) |

## Mối liên hệ
- [[Architecture/Chat_Integration]] — Cách Hub BE và Agent BE giao tiếp qua `AGENT_BASE_URL` + `AGENT_API_KEY`.
- [[Architecture/FastAPI_Structure]] — Cấu trúc backend sử dụng các biến môi trường này.
- [[Misc/Troubleshooting]] — Nếu setup sai env vars.
