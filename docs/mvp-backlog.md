# MVP backlog

## P0 epics

### Epic: platform foundation

- **P0** Scaffold monorepo workspace with web, api, worker, and shared packages
- **P0** Establish environment configuration, secrets strategy, and local Docker workflow
- **P0** Add Prisma migrations, seed path, and DB access package conventions
- **P0** Set up CI baseline for install, lint, typecheck, test, build, and schema validation

### Epic: identity and access

- **P0** User registration, login, refresh, logout, and password reset foundation
- **P0** Session persistence and token rotation model
- **P0** OAuth-ready account linking model for Google and Microsoft
- **P0** Protected routes and authorization guard baseline

### Epic: planning and execution core

- **P0** CRUD for goals with parent/child hierarchy
- **P0** CRUD for projects, milestones, and tasks
- **P0** Task status, priority, due dates, and dependencies
- **P0** Dashboard overview from real task, goal, and project data
- **P0** Daily and weekly review workflows

## P1 epics

### Epic: knowledge and ideas

- **P1** Note CRUD and search-ready storage
- **P1** Document upload metadata and ingestion pipeline scaffold
- **P1** Chunking and indexing workflow for documents
- **P1** Idea capture, prioritization fields, and lifecycle states
- **P1** Tagging support across ideas, notes, and documents

### Epic: AI assistance

- **P1** AI conversation persistence and streaming endpoint scaffold
- **P1** Recommendation generation and feedback capture
- **P1** Memory CRUD and retrieval-ready classification
- **P1** Daily plan and weekly plan orchestration endpoints

### Epic: notifications and analytics

- **P1** In-app notification center and read state
- **P1** Notification preferences and scheduled reminders
- **P1** Analytics event capture for core user journeys
- **P1** Daily/weekly execution score rollups

## P2 epics

### Epic: production hardening

- **P2** Audit trail for sensitive actions
- **P2** Observability, tracing, and error monitoring
- **P2** Rate limiting and upload safety controls
- **P2** Backup, recovery, and deployment runbooks
- **P2** Performance tuning for dashboard, search, and AI flows
