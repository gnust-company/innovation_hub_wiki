---
type: atomic-note
category: Architecture
related: ["FastAPI_Structure", "MOC_Architecture", "Database_Schema"]
tags: [architecture, clean-architecture]
updated: 2026-04-28
---

# Clean Architecture

## 3 Layers

### Domain Layer (`app/domain/`)
- **Entities**: Business objects thuần túy (User, Problem, Room, Idea, Event...).
- **Repositories**: Interface định nghĩa contract (abstract classes).
- **Value Objects**: Enums, immutable types (UserRole, ProblemStatus...).
- **Không phụ thuộc** framework hay infrastructure.

### Application Layer (`app/application/`)
- **Use Cases**: Business logic orchestration (CreateProblemUseCase, UpdateIdeaUseCase...).
- **DTOs**: Data Transfer Objects cho request/response.
- **Services**: JWTService, cross-cutting services.
- **Dependencies injection**: Inject repository interfaces, không dùng concrete implementations.

### Infrastructure Layer (`app/infrastructure/`)
- **Database**: SQLAlchemy models, repository implementations, migrations (Alembic).
- **Web**: FastAPI routes, middleware, dependencies.
- **Security**: Password hashing (bcrypt), JWT handling.
- **Storage**: MinIO client cho file uploads.

## Dependency Rule
```
Infrastructure → Application → Domain
```
- Domain không import gì từ Application hay Infrastructure.
- Application chỉ import từ Domain.
- Infrastructure implement interfaces từ Domain/Application.

## DI Container
- Dùng `dependency-injector` library.
- Container wiring trong `container.py`.
- FastAPI Depends() injection cho endpoints.

## Mối liên hệ
- [[06_Architecture/FastAPI_Structure]] — Chi tiết cấu trúc folders.
- [[06_Architecture/Database_Schema]] — ORM models và schema.
- [[06_Architecture/MOC_Architecture]] — Tổng quan architecture.
