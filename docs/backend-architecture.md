# Backend architecture

## Style

Use a **NestJS modular monolith** with explicit domain boundaries. The goal is fast delivery for the MVP without collapsing the codebase into a featureless monolith.

## Core backend modules

- `auth`
- `users`
- `dashboard`
- `goals`
- `projects`
- `tasks`
- `ideas`
- `notes`
- `documents`
- `search`
- `memory`
- `ai`
- `reviews`
- `notifications`
- `analytics`
- `audit`

## Cross-cutting platform modules

- `database`
- `config`
- `health`
- `logging`
- `events`
- `queue`

## Boundary rules

- Controllers call application services, not Prisma directly.
- Modules own their DTOs, validation, and mapping logic.
- Cross-module access should happen through exported services or domain events.
- Jobs should be triggered by explicit use cases, not hidden side effects.
- Audit and analytics emission should be standardized and reusable.

## Domain responsibilities

### auth

Identity, sessions, OAuth accounts, token lifecycle, and access guards.

### goals / projects / tasks

Strategic planning hierarchy and execution workflows. Projects connect goals to milestones and tasks; tasks handle scheduling, status, dependencies, and review signals.

### notes / documents / search / memory

Knowledge capture, ingestion, indexing, retrieval, and persistence of durable context for AI-assisted workflows.

### ai

Provider abstraction, prompt orchestration, chat endpoints, recommendation generation, and model observability.

### reviews / notifications / analytics

Habit loops, reminders, engagement signals, and execution reporting.

## Suggested NestJS layout

```text
apps/api/src/
  app.module.ts
  common/
  modules/
    auth/
    users/
    dashboard/
    goals/
    projects/
    tasks/
    ideas/
    notes/
    documents/
    search/
    memory/
    ai/
    reviews/
    notifications/
    analytics/
    audit/
```

## Event and job examples

- `document.uploaded` -> extraction job
- `document.processed` -> chunk/embed job
- `review.completed` -> analytics rollup
- `task.completed` -> recommendation refresh
- `notification.scheduled` -> delivery job

## MVP hardening guidance

- central exception mapping
- request validation everywhere
- role-aware authorization guards
- rate limits on auth and AI endpoints
- structured logging and request tracing
