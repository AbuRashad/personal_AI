# Monorepo target structure

## Target layout

```text
apps/
  web/                 # Next.js app-router frontend
  api/                 # NestJS API modular monolith
  worker/              # background jobs and scheduled processing
packages/
  db/                  # Prisma schema, migrations, database client
  ui/                  # shared design system and reusable UI components
  config/              # shared TS, ESLint, Prettier, env, and runtime config
  types/               # shared DTO-adjacent types and contracts
  auth/                # auth helpers, guards, and shared auth utilities
  ai/                  # provider abstraction, prompts, AI client contracts
  analytics/           # event names, schemas, and client helpers
  notifications/       # notification templates and delivery contracts
infrastructure/
  docker/              # local and deployment container assets
  k8s/                 # Kubernetes-ready manifests or Helm charts later
  terraform/           # cloud infrastructure definitions
  scripts/             # deployment/bootstrap scripts when needed
docs/                  # product, engineering, and delivery planning artifacts
```

## Folder responsibilities

### apps/web

- authenticated product UI
- app shell, dashboard, planning, knowledge, reviews, AI workspace
- route groups, layouts, server actions, and API client composition

### apps/api

- REST and streaming APIs
- authorization, orchestration, business rules, and persistence boundaries
- emits jobs/events for async workflows

### apps/worker

- BullMQ or equivalent workers
- ingestion, embeddings, notifications, analytics rollups, scheduled reviews

### packages

Shared packages should stay framework-light where possible so they can be reused by the API, worker, and web app without duplication.

### infrastructure

Keep deployment concerns separate from application code and version them beside the codebase from day one.

## Sequencing recommendation

1. `packages/db`
2. `apps/api`
3. `apps/web`
4. `apps/worker`
5. shared packages and infrastructure assets as implementation demands them
