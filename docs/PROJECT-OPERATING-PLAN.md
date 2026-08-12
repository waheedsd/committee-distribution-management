# Committee Distribution Management — Learning & Delivery Operating Plan

## Purpose

This project is both a real charitable-committee product and a structured React learning program. Every task must connect learning to a real product outcome.

## System of record

- GitHub: source of truth for backlog, code, issues, PRs, milestones, and technical documentation.
- ChatGPT: trainer, mentor, Product Manager, solution architect, reviewer, and debugger.
- Google Calendar / Apple Calendar: time commitment and reminders. The calendar entry should point to the GitHub issue and describe the learning + build agenda.
- Google Drive: optional shared committee documents, meeting notes, and non-technical source material.

## Daily task format

Every daily session should contain:

1. Phase and milestone
2. Today's learning objective
3. Why it matters to the product
4. Resource links
5. Visual/UX reference or screenshot when useful
6. Small practice exercise
7. Product implementation task
8. UX consideration
9. Documentation task
10. Test/check steps
11. Definition of done
12. GitHub issue/commit guidance

Default session: 60–120 minutes at 7:00 PM IST.

## Phases

### Phase 0 — Product Discovery & UX
Outcome: a clear V1 product definition, personas, journeys, UX flows, and acceptance criteria.

### Phase 1 — React Foundations
Outcome: understand React mental model, JSX, components, props, state, events, rendering, lists, and effects by building small product UI pieces.

### Phase 2 — Frontend Design System
Outcome: build the application shell and reusable shadcn/ui components with responsive, accessible UX.

### Phase 3 — Forms & Client UX
Outcome: build production-quality forms with React Hook Form + Zod, validation, errors, loading and success states.

### Phase 4 — Backend & Database
Outcome: design generic distribution-domain data and implement NestJS + PostgreSQL + Prisma APIs.

### Phase 5 — React Server State & API Integration
Outcome: connect React to APIs with TanStack Query and understand queries, mutations, caching, invalidation and error handling.

### Phase 6 — Authentication & RBAC
Outcome: implement session/authentication, admin/operator/user access, operator approval and idle logout.

### Phase 7 — Distribution Operations
Outcome: implement token generation, search, queue, allocation, distribution status and history.

### Phase 8 — Payments, Dashboard & Reporting
Outcome: implement QR/payment records, operational dashboard and reports.

### Phase 9 — Testing & Quality
Outcome: unit, integration and E2E tests plus accessibility/security review.

### Phase 10 — Deployment & Operations
Outcome: deploy a low-cost production system with CI/CD, backups, observability and recovery procedures.

## Future product roadmap

After V1 proves the workflow with milk distribution, evaluate grocery, clothing and other committee distributions. Future features should be driven by real committee feedback rather than assumptions.

## UX documentation rule

For each major feature, keep:

- user journey
- wireframe or screenshot/reference
- interaction states
- validation/error states
- accessibility considerations
- acceptance criteria

UX artifacts belong under `docs/ux/` and can later be recreated/refined in Penpot.

## Learning documentation rule

For each important React concept, keep a short note under `docs/learning/` containing:

- concept in plain language
- Node.js/backend analogy where useful
- example from this project
- common mistake
- what I can now explain without help

## Progress rule

A task is not complete just because code works. It is complete when:

- I understand the concept well enough to explain it
- the feature works
- UX states are considered
- tests/checks pass
- documentation is updated
- GitHub issue can be closed

## Calendar agenda convention

Title: `CDM — <Phase>: <Learning/Build topic>`

Description should contain: Goal, Learn, Practice, Build, UX, Docs, Resources, Done When, GitHub issue.
