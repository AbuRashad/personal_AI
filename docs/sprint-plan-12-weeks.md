# 12-week sprint plan

## Assumptions

- Six two-week sprints
- Small product team with full-stack coverage
- Scope stays within MVP boundaries defined in the PRD

## Sprint 1 (Weeks 1-2): repository and platform bootstrap

- scaffold monorepo folders and tooling
- bootstrap Next.js web app, NestJS API, and worker app
- add Prisma package, initial migrations, and local Postgres wiring
- establish CI, env conventions, and Docker-based local development

## Sprint 2 (Weeks 3-4): auth and app shell

- implement user, auth account, and session flows
- add protected app shell and navigation
- deliver login/register/reset foundations
- add shared UI primitives and API client setup

## Sprint 3 (Weeks 5-6): goals, projects, milestones, tasks

- build goals hierarchy APIs and screens
- implement projects and milestones
- implement task CRUD, status, priority, and due dates
- add dashboard overview with execution-focused summaries

## Sprint 4 (Weeks 7-8): reviews, notifications, analytics baseline

- add daily and weekly review flows
- add in-app notifications and preferences
- capture core analytics events
- compute first execution score and trend summaries

## Sprint 5 (Weeks 9-10): ideas, notes, documents, search foundation

- implement idea capture and lifecycle states
- implement notes and document metadata CRUD
- add ingestion queue, chunking pipeline, and indexing scaffold
- expose search entry points for text and semantic retrieval

## Sprint 6 (Weeks 11-12): AI and launch hardening

- add AI conversations, messages, and recommendation persistence
- implement daily-plan and weekly-plan orchestration endpoints
- connect memory retrieval to AI workflows
- complete audit, observability, and release readiness checks

## End-of-MVP outcomes

By the end of week 12, the team should have a functional MVP slice covering auth, planning, reviews, knowledge capture, basic retrieval, and persisted AI-assisted planning flows.
