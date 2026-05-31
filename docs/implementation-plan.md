# AbdoOS 3.0 implementation plan

## Delivery approach

Start with a **modular monolith in a monorepo** so the team can move quickly while keeping clear boundaries for future extraction. The first implementation PRs should scaffold the repository, database, API, web app, and worker around the domains defined here.

## Target architecture

- **apps/web**: Next.js app-router frontend for dashboard, planning, knowledge, reviews, and AI chat
- **apps/api**: NestJS API as the primary HTTP and orchestration layer
- **apps/worker**: background job processor for embeddings, document ingestion, reminders, and AI tasks
- **packages/db**: Prisma schema, migrations, and shared DB client configuration
- **shared packages**: UI, config, auth, types, AI, analytics, notifications
- **infrastructure**: Docker, Kubernetes-ready manifests, and Terraform placeholders

## Module boundaries

### Backend modules

- auth
- users
- dashboard
- goals
- projects
- tasks
- ideas
- notes
- documents
- search
- memory
- ai
- reviews
- notifications
- analytics
- audit

Each module should own:

- controllers / resolvers
- service layer
- DTOs and validation
- repository/data access boundaries
- events or jobs it publishes

## API direction

Use REST for CRUD-heavy workflows and streaming endpoints for AI responses.

### Example route groups

- `/auth/*`
- `/dashboard/*`
- `/goals/*`
- `/projects/*`
- `/tasks/*`
- `/ideas/*`
- `/notes/*`
- `/documents/*`
- `/search/*`
- `/ai/*`
- `/reviews/*`
- `/notifications/*`
- `/analytics/*`

## Jobs and async processing

Use the worker app for:

- document text extraction
- chunk generation and embedding requests
- notification scheduling and delivery
- review reminders
- AI summarization and recommendation generation
- analytics rollups and score snapshots

## Data and AI direction

- PostgreSQL is the system of record
- Prisma manages the primary relational model
- document chunks and memory items should be retrieval-ready
- AI requests should store provider, model, and token metadata when possible
- recommendations should be persisted so the product can learn from acceptance or dismissal

## Deployment direction

### Environments

- local
- development
- staging
- production

### Platform expectations

- Docker-first local setup
- CI with install, lint, typecheck, tests, build, and Prisma validation once code is scaffolded
- API, web, and worker deployed independently
- managed Postgres, Redis, object storage, and a vector-capable search layer

## Testing strategy

### Backend

- service unit tests
- module integration tests
- authorization tests
- contract tests around AI adapters and job payloads

### Frontend

- component and hook tests
- route-level integration tests
- E2E coverage for authentication, goals, projects, tasks, ideas, knowledge, and reviews

### Schema and platform

- Prisma validation and migration checks
- smoke tests for document ingestion and AI recommendation pipelines

## Phased delivery

### Phase 0: repository and platform scaffold

- initialize monorepo folders
- bootstrap Next.js, NestJS, worker, and shared package layout
- add Prisma and first migrations
- establish environment conventions and CI baseline

### Phase 1: execution core

- auth, user profile, dashboard shell
- goals, projects, milestones, tasks
- daily and weekly reviews
- basic notifications and analytics events

### Phase 2: knowledge and idea systems

- notes, documents, tagging, search
- idea capture and scoring workflow
- document ingestion and chunking pipeline

### Phase 3: AI-assisted workflows

- AI conversations and recommendation persistence
- memory retrieval
- daily planning and weekly planning endpoints
- recommendation feedback loops

### Phase 4: hardening

- audit coverage, performance tuning, observability, backups, and production readiness checks
