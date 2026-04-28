---
type: atomic-note
category: Architecture
related: ["Clean_Architecture", "MOC_Architecture"]
tags: [architecture, fastapi]
updated: 2026-04-28
---

# FastAPI Structure

## Backend Folder Structure
```
backend/
├── app/
│   ├── main.py                    # FastAPI app creation
│   ├── container.py               # DI container
│   ├── domain/                    # Domain layer
│   │   ├── entities/              # Business objects
│   │   ├── repositories/          # Repository interfaces
│   │   └── value_objects/         # Enums, value types
│   ├── application/               # Application layer
│   │   ├── dto/                   # Request/Response DTOs
│   │   ├── services/              # Services (JWT, etc.)
│   │   └── use_cases/             # Business use cases
│   │       ├── problem/
│   │       ├── idea/
│   │       ├── room/
│   │       ├── event*/
│   │       └── ...
│   ├── infrastructure/            # Infrastructure layer
│   │   ├── database/
│   │   │   ├── config.py          # Database connection
│   │   │   ├── models/            # SQLAlchemy ORM models
│   │   │   └── repositories/      # Repository implementations
│   │   ├── security/              # Password hashing
│   │   ├── storage/               # MinIO client
│   │   └── web/
│   │       └── api/
│   │           ├── deps.py        # FastAPI dependencies
│   │           ├── middleware.py   # CORS, etc.
│   │           └── v1/
│   │               ├── router.py  # Route aggregation
│   │               └── endpoints/ # Endpoint handlers
│   └── core/
│       ├── config.py              # App settings
│       └── exceptions.py          # Custom exceptions
├── alembic/                       # Database migrations
├── Dockerfile
└── requirements.txt
```

## Key Patterns
- **Dependencies** (`deps.py`): `get_db_session`, `get_current_user`, repo factories.
- **Router aggregation**: `v1/router.py` gộp tất cả endpoint routers.
- **Async everywhere**: Tất cả DB operations dùng async/await.
- **Repository pattern**: Mỗi entity có interface (Domain) + implementation (Infrastructure).

## Mối liên hệ
- [[06_Architecture/Clean_Architecture]] — 3-layer architecture giải thích.
- [[06_Architecture/Database_Schema]] — Database models detail.
- [[06_Architecture/MOC_Architecture]] — Tổng quan architecture.
