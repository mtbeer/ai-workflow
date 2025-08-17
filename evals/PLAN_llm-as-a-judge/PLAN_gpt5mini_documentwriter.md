# BrewBuddy Technical Plan (PLAN)

Source documents: [`docs/PRD.md`](docs/PRD.md:1), [`docs/SPECS.md`](docs/SPECS.md:1)

## Legend
- Task statuses: [ ] pending, [-] in progress, [x] completed
- Priority: P0 = must-have for initial release; P1 = important, post-core; P2 = optional / future enhancement
- Format: Tasks grouped by section; each task must include priority and acceptance criteria where applicable

## Summary
This plan breaks the PRD and SPECS into prioritized, actionable tasks and milestones for implementation and orchestration.

## 0. Project / Architecture Setup (P0)
- [ ] Initialize repository structure, CI, linting, and testing scaffold (P0) — acceptance: project builds, tests run locally
- [ ] Choose local-first DB approach and schema migration tooling (SQLite with optional Postgres) (P0)
- [ ] Implement basic backend skeleton: Node.js/Express API with routes listed in [`docs/SPECS.md`](docs/SPECS.md:76) (P0)
- [ ] Implement frontend skeleton: React app, routing, responsive baseline (P0)
- [ ] Offline storage strategy implemented (localStorage/IndexedDB) and sync placeholder (P0)

## 1. Data Models / Schema (P0)
- [ ] Implement Recipe model and migration: fields from [`docs/SPECS.md`](docs/SPECS.md:70) (P0)
- [ ] Implement BrewDayStep model: supports instructions, timer, measurements (P0)
- [ ] Implement Batch and FermentationLog models (P0)
- [ ] Implement InventoryItem model with low_threshold and unit normalization (P0)
- [ ] Unit tests for model validations and basic CRUD (P0)

## 2. Guided Brew Day Workflow (P0)
- [ ] API endpoints to create/start a Batch and to advance BrewDayStep (P0)
- [ ] Frontend wizard UI: step progression, per-step instructions, timers (P0)
- [ ] Per-step measurement logging UI and local persistence (P0)
- [ ] Allow recipe-specific step configuration and saving to recipe versions (P0)
- [ ] Acceptance: user can start a brew, progress steps, set timers, and log measurements locally

## 3. Recipe Builder (P0)
- [ ] Recipe creation/edit UI with tabs for all-grain vs extract (P0)
- [ ] Auto-calculation service for ABV, IBU, SRM, calories with override capability (P0)
- [ ] Recipe versioning API and UI (P0)
- [ ] Acceptance: create/edit/versioning works and calculations update automatically

## 4. Fermentation Tracker (P1)
- [ ] API and model for fermentation logs; link to batch (P1)
- [ ] UI for entering readings and graphing trend lines (P1)
- [ ] Optional reminders for readings (P2)
- [ ] Acceptance: multiple readings per batch are stored and graphed

## 5. Inventory Management (P1)
- [ ] Inventory CRUD API and UI; import initial seed data format (P1)
- [ ] Automatic quantity deduction when batch is started/ingredients used (P1)
- [ ] Manual adjustment UI and reconciliation flow (P1)
- [ ] Low/missing item alert system and UI (P1)
- [ ] Acceptance: inventory updates and alerts function locally

## 6. Export / Sharing (P2)
- [ ] Implement BeerXML and CSV export services (P2)
- [ ] Export UI and file download flow (P2)
- [ ] Acceptance: export includes recipe and logs in requested formats

## Cross-Cutting Concerns
- API Layer (P0)
  - [ ] Implement authentication placeholder (local-only) and standard error handling (P0)
  - [ ] Implement endpoints in [`docs/SPECS.md`](docs/SPECS.md:76-83) with validation and tests (P0)
- QA / Testing (P0)
  - [ ] Unit tests for core services and models (P0)
  - [ ] Integration tests for critical flows: create recipe -> start batch -> complete brew day (P0)
- Performance & UX (P1)
  - [ ] Ensure offline responsiveness and low-latency UI on mobile (P1)
- Documentation (P1)
  - [ ] User-facing docs: guided brew day help and export instructions (P1)
  - [ ] Developer docs: API spec and data model diagrams (P1)

## Open Technical Questions
1. How will offline sync and conflict resolution be implemented for multi-device use? (see [`docs/SPECS.md`](docs/SPECS.md:85-86))
2. What is the desired retention/rollback policy for recipe versioning? (see [`docs/SPECS.md`](docs/SPECS.md:86-87))
3. Should reminders/notifications use browser APIs (service workers) or a backend push service? (see [`docs/SPECS.md`](docs/SPECS.md:87-88))
4. Unit normalization and conversions between metric/imperial — authoritative library or custom logic?

## Milestones
- Milestone 1 — Core (P0)
  - Tasks: Project setup, Data Models, Guided Brew Day, Recipe Builder, basic API endpoints
- Milestone 2 — Tracking & Inventory (P1)
  - Tasks: Fermentation Tracker, Inventory Management, UI polish, unit tests for these flows
- Milestone 3 — Exports & Polish (P2)
  - Tasks: Export/Sharing, reminders (optional), performance tuning, documentation

## Acceptance Summary
- App works offline for a brew day and stores data locally (P0)
- Users can create and version recipes and run guided brew days with timers and measurements (P0)
- Inventory reflects ingredient usage and shows alerts for low/missing items (P1)
- Users can export recipes/logs to BeerXML and CSV (P2)
- Basic unit and integration tests exist for core flows (P0)

## Instructions for Roo Code Orchestrator
- When a task starts: change its checkbox from [ ] to [-] and append a single-line update note directly below the task in PLAN.md:
  - Example: "— [-] In progress by Roo Orchestrator @2025-08-16T14:31:00Z"
- When a task completes: change checkbox to [x], append completion metadata on the same line:
  - Example: "— [x] Completed by Roo Orchestrator @2025-08-16T14:40:00Z — commit: docs/PLAN.md update task status: <task-id>"
- The Orchestrator must create a git commit for every task status change with message: "docs(PLAN): update task status — <section> — <short-task-desc>"
- Keep PLAN.md as the single source of truth; do not create secondary tracking files.
- For subtasks or multi-step tasks, create nested bullet tasks under the main task and follow the same status rules.
- For any blocked task, set status to [-], add a "Blockers:" line with brief explanation and an action item.

## Post-Completion Notes
- After finishing each milestone, update the Milestones section by marking completed tasks and adding a brief release notes summary.
- Record acceptance test run results inline under Acceptance Summary with timestamp and pass/fail.

## Contacts & Ownership
- Project lead: Product — TBD
- Engineering: TBD
- QA: TBD

## Change Log
- 2025-08-16 — Initial PLAN.md created from [`docs/PRD.md`](docs/PRD.md:1) and [`docs/SPECS.md`](docs/SPECS.md:1)