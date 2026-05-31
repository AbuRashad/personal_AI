# Frontend architecture

## Style

Use **Next.js App Router** with route groups, shared layouts, server-side data fetching where appropriate, and client components only where interactivity requires them.

## Primary route map

```text
/(marketing)
  /                # optional landing page later
/(auth)
  /login
  /register
/(app)
  /dashboard
  /goals
  /projects
  /projects/[projectId]
  /tasks
  /ideas
  /knowledge
  /knowledge/notes/[noteId]
  /knowledge/documents/[documentId]
  /reviews
  /ai
  /settings
```

## App shell

The authenticated shell should provide:

- left navigation for major domains
- top command/search bar
- optional right-side AI panel on larger screens
- notification entry point
- responsive behavior for tablet and mobile web

## Route ownership

### dashboard

Mission control overview for priorities, due work, recommendations, and recent progress.

### goals / projects / tasks

Execution planning surfaces with list, board, and detail views.

### ideas / knowledge

Fast capture plus structured retrieval and review.

### reviews

Daily and weekly workflows with guided prompts and score summaries.

### ai

Conversation workspace for planning, summarization, and recommendation review.

## UI composition guidance

Create reusable components for:

- KPI cards
- goal trees
- project summary cards
- task lists and kanban columns
- milestone timelines
- idea score cards
- note/document result cards
- AI chat threads and recommendation cards
- review forms and score summaries

## Data-fetching guidance

- use server components for first-load data where practical
- keep mutations behind typed API clients or server actions
- reserve client state for UI concerns such as filters, panels, and optimistic interactions
- design route loaders around module-aligned API boundaries

## Frontend MVP priorities

1. authenticated app shell
2. dashboard
3. goals/projects/tasks flows
4. ideas and knowledge flows
5. reviews
6. AI workspace
