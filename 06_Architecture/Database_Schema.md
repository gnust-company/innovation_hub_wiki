---
type: atomic-note
category: Architecture
related: ["Clean_Architecture", "FastAPI_Structure", "MOC_Architecture"]
tags: [architecture, database]
updated: 2026-04-28
---

# Database Schema

## ERD Overview

### Core Tables

**users**
- id (UUID, PK), username, password_hash, email?, full_name?, role (member/admin), team?, avatar_url?, is_active, created_at, updated_at

**problems**
- id (UUID, PK), title, summary?, content (JSONB/TipTap), category (process/technical/people/tools/patent), status (open/discussing/brainstorming/solved/closed), visibility (public/private), shared_user_ids (JSON array), author_id (FK→users), created_at, updated_at

**rooms**
- id (UUID, PK), name, description?, problem_id? (FK→problems), created_by (FK→users), status (active/archived), visibility (public/private), shared_user_ids (JSON array), created_at, updated_at

**ideas**
- id (UUID, PK), room_id (FK→rooms), title, description (JSONB/TipTap), summary?, status (draft/refining/reviewing/submitted/closed), is_pinned, author_id (FK→users), created_at, updated_at

**comments**
- id (UUID, PK), target_id, target_type (problem/idea/event_idea), content, author_id (FK→users), parent_id? (FK→comments, self-ref), created_at, updated_at

**reactions**
- id (UUID, PK), target_id, target_type (problem/idea), type (like/dislike/insight), user_id (FK→users), created_at

**votes**
- id (UUID, PK), idea_id (FK→ideas), user_id (FK→users), stars (1-5), created_at, updated_at

**notifications**
- id (UUID, PK), user_id, actor_id, type, target_id, target_type, target_title, action_detail?, reference_id?, is_read, created_at, updated_at

### Event Tables

**events**
- id (UUID, PK), title, description? (JSONB/TipTap), introduction_type (editor/embed), embed_url?, status (draft/active/closed), created_by, start_date?, end_date?, created_at, updated_at, closed_at?

**event_teams**
- id (UUID, PK), event_id (FK→events), name, slogan?, leader_id (FK→users), assigned_to_team_id? (FK→event_teams, self-ref), created_at, updated_at

**event_team_members**
- id (UUID, PK), team_id (FK→event_teams), user_id (FK→users), event_id (FK→events), status (pending/active/rejected), joined_at, created_at, updated_at

**event_ideas**
- id (UUID, PK), event_id (FK→events), team_id (FK→event_teams), title, user_problem? (JSONB), user_scenarios? (JSONB), user_expectation? (JSONB), research? (JSONB), solution (JSONB), source_type (manual/linked), source_problem_id?, source_room_id?, source_idea_id?, author_id (FK→users), created_at, updated_at

**event_scoring_criteria**
- id (UUID, PK), event_id (FK→events), group (problem/solution), name, description?, weight, max_score, sort_order, created_at

**event_scores**
- id (UUID, PK), event_idea_id (FK→event_ideas), scorer_team_id (FK→event_teams), criteria_scores (JSONB), criteria_notes? (JSONB), total_score, created_at, updated_at

**event_faqs**
- id (UUID, PK), event_id (FK→events), question, answer? (JSONB/TipTap), created_by (FK→users), sort_order, created_at, updated_at

**event_awards**
- id (UUID, PK), event_id (FK→events), name, rank_order, created_at, updated_at

**event_award_teams**
- id (UUID, PK), award_id (FK→event_awards), team_id (FK→event_teams), created_at, updated_at

## Key Relationships
- Problem → Room (1:N, optional)
- Room → Idea (1:N)
- Idea → Vote (1:N), Idea → Reaction (1:N), Idea → Comment (1:N)
- Problem → Reaction (1:N), Problem → Comment (1:N)
- Event → Team (1:N), Event → EventIdea (1:N), Event → Award (1:N), Event → Criteria (1:N), Event → FAQ (1:N)
- Team → Member (1:N), Team → EventIdea (1:N)
- EventIdea → Score (1:N)
- Award → AwardTeam (1:N)

## Mối liên hệ
- [[06_Architecture/Clean_Architecture]] — Domain entities map to DB tables.
- [[06_Architecture/FastAPI_Structure]] — SQLAlchemy models location.
- [[06_Architecture/MOC_Architecture]] — Tổng quan architecture.
