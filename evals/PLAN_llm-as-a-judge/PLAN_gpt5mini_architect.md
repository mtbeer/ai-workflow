# BrewBuddy — PLAN

Sources:
- [`docs/PRD.md`](docs/PRD.md:1)
- [`docs/SPECS.md`](docs/SPECS.md:1)

## Legend
- Task statuses: [ ] pending, [-] in_progress, [x] completed  
- Priorities: P0 = launch-critical, P1 = important post-launch, P2 = backlog/enhancements  
- Task line format: - [ ] Title (P#) — Owner: agent — ETA: Xd

## Plan Structure
- 0. Project/Architecture Setup (P0)  
- 1. Data Models / Schema (P0)  
- 2. Guided Brew Day Workflow (P0)  
- 3. Recipe Builder (P0)  
- 4. Fermentation Tracker (P1)  
- 5. Inventory Management (P1)  
- 6. Export & Sharing (P1)  
- 7. Cross-Cutting Concerns (P0)  
- 8. Open Technical Questions  
- 9. Milestones & Acceptance

## 0. Project / Architecture Setup (P0)
- [ ] Initialize repository and project scaffold (React frontend + Node/Express backend) (P0)
- [ ] Choose DB strategy: local-first SQLite with optional PostgreSQL sync layer (P0)
- [ ] Configure local storage strategy and offline-first approach (service worker / IndexedDB + SQLite bridge) (P0)
- [ ] Establish code style, linting, and pre-commit hooks (ESLint, Prettier, Husky) (P0)
- [ ] Setup CI pipeline (tests, build, lint) (P0)

## 1. Data Models / Schema (P0)
- [ ] Implement Recipe schema: id, name, type (all-grain/extract), malt[], hops[], yeast[], adjuncts[], water, batch_size, version, created_at, updated_at (P0)
- [ ] Implement BrewDayStep schema: id, recipe_id, name, instructions, timer, measurements[] (P0)
- [ ] Implement FermentationLog schema: id, batch_id, gravity, temperature, notes, date_time (P0)
- [ ] Implement InventoryItem schema: id, type, name, quantity, unit, low_threshold (P0)
- [ ] Implement Batch schema: id, recipe_id, start_date, end_date, notes (P0)
- [ ] Create database migration scripts and seed sample data (P0)
- [ ] Define API contract (REST) for model CRUD and relationships (P0)

## 2. Feature: Guided Brew Day Workflow (P0)
- [ ] Data model and persistence for brew sessions / batches linking steps to recipe (P0)
- [ ] Wizard-style UI for step progression (mobile-first) (P0)
- [ ] Per-step timers, measurement capture (temperature, gravity), photo and notes attachment (P0)
- [ ] Configurable step templates per recipe and ability to skip/re-order steps (P0)
- [ ] Local saving, resume capability, and offline operation (P0)
- [ ] Unit and integration tests for step progression and persistence (P0)

Acceptance Criteria:
- User can start a brew, progress through steps, set timers, and log measurements
- Brew session data persisted locally and linked to recipe/batch
- Responsive UI for mobile devices

## 3. Feature: Recipe Builder (P0)
- [ ] UI for creating and editing recipes with explicit tabs for all-grain vs extract (P0)
- [ ] Implement auto-calculations: ABV, IBU, SRM, calories; allow manual override (P0)
- [ ] Support recipe versioning: save versions, view history, rollback (P0)
- [ ] Validation and unit conversion support (metric/imperial) (P0)
- [ ] Expose hooks for export integration (BeerXML/CSV) (P1)
- [ ] Unit tests for calculation correctness and conversions (P0)

Acceptance Criteria:
- Create / edit / version recipes; calculations update automatically and can be overridden

## 4. Feature: Fermentation Tracker (P1)
- [ ] UI for entering fermentation readings and plotting graphs (P1)
- [ ] Link fermentation logs to batches and recipes (P1)
- [ ] Optional reminders / scheduling for readings (P2)
- [ ] Tests for data capture, storage and graph rendering (P1)

Acceptance Criteria:
- Multiple readings per batch supported and graphed correctly

## 5. Feature: Inventory Management (P1)
- [ ] Implement inventory data model, CRUD APIs and UI (P1)
- [ ] Automatic quantity deduction when a batch is started / ingredients used (P1)
- [ ] Manual adjustment UI and history log for inventory edits (P1)
- [ ] Low-threshold alert system and visible UI banners/indicators (P1)
- [ ] Offline update handling and conflict resolution strategy for sync (P2)

Acceptance Criteria:
- Inventory updates automatically and allows manual edits; alerts appear when low/missing

## 6. Feature: Export / Sharing (P1)
- [ ] Implement export service for BeerXML and CSV formats (P1)
- [ ] Ensure export includes recipe fields and associated batch logs (P1)
- [ ] UI for export actions and download handling (P1)
- [ ] Unit tests to validate output format and required fields (P1)

Acceptance Criteria:
- User can export recipe/logs as BeerXML or CSV with required data

## 7. Cross-Cutting Concerns (P0)
### API Layer
- [ ] Design REST API endpoints and contracts for frontend/backend (P0)
- [ ] Implement server-side validation, sanitization and error handling (P0)
- [ ] Implement pagination and filtering for large lists (P1)

### QA / Testing
- [ ] Unit tests for core logic (calculations, transforms) (P0)
- [ ] Integration tests for major flows (recipe save, brew day, inventory) (P0)
- [ ] E2E tests covering critical user journeys (P1)
- [ ] Test matrix specifically for offline scenarios (P0)

### Performance & UX
- [ ] Mobile-first responsive design and accessibility audit (P0)
- [ ] Optimize DB queries, lazy-load heavy assets and defer non-critical work (P1)
- [ ] Reduce bundle size with code-splitting and tree-shaking (P1)

### Documentation
- [ ] Developer README, architecture diagram, and setup instructions (P0)
- [ ] User-facing help pages and export instructions (P1)
- [ ] API docs (OpenAPI) for backend endpoints (P1)

## Open Technical Questions
- How will offline sync and local storage be handled for multi-device use? (P0)  
- What is the final DB choice for local-first and syncable backend: SQLite vs IndexedDB + SQLite bridge? (P0)  
- Recipe versioning strategy: immutable snapshots or diff-based edits? (P1)  
- Reminders: use browser push APIs, background worker, or backend service? (P2)  
- Export spec: which BeerXML version and exact field mapping required? (P1)

## Milestone Grouping
- Milestone 1 — Core (P0): Project setup, Data Models, Recipe Builder (create/edit/version), Guided Brew Day, Local persistence, Unit tests  
- Milestone 2 — Stability (P1): Inventory Management, Fermentation Tracker, API endpoints, CI tests, E2E tests  
- Milestone 3 — Integrations (P1): Export formats, performance improvements, documentation, accessibility fixes  
- Milestone 4 — Optional / Backlog (P2): Multi-device sync, authentication, cloud backup, reminders

## Acceptance Summary
- Core flows (create recipe, run guided brew, log measurements) work offline and on mobile  
- Data persisted locally and correctly linked across recipes, batches and logs  
- Inventory reflects ingredient usage and displays low/missing alerts  
- Export to BeerXML and CSV produces valid files including recipe and logs  
- Automated tests cover core calculations and persistence flows

## Instructions for Roo Code Orchestrator (tracking & updates)
- When completing a task, update its status in this file by changing the checkbox:  
  - Pending -> In progress: change `[ ]` to `[-]` and add `— started: YYYY-MM-DDTHH:MM:SSZ`  
  - In progress -> Completed: change `[-]` to `[x]` and add `— completed: YYYY-MM-DDTHH:MM:SSZ`  
- Append agent name and brief note after timestamp, e.g. `— completed: 2025-08-16T14:34:00Z — agent: roo-orchestrator — notes: implemented model`  
- After each update to PLAN.md, call the `update_todo_list` tool to reflect high-level progress and keep the in-memory TODO list synchronized with this document  
- For task splits, create a subtask under the same section with its own checkbox and reference parent: `Parent task title — subtask: [ ]`  
- Keep the Milestone Grouping section updated to reflect moved/finished tasks  
- Do not remove tasks; mark them `[x]` only when fully complete and all acceptance criteria are met

## Open actions for next agent run
- [ ] Implement Project/Architecture Setup checklist (P0) — assign to code mode  
- [ ] Implement Data Models and migrations (P0) — assign to code mode  
- [ ] Start Recipe Builder UI skeleton (P0) — assign to frontend dev  
- [ ] Start Guided Brew Day wizard skeleton (P0) — assign to frontend dev

Footer: Generated from [`docs/PRD.md`](docs/PRD.md:1) and [`docs/SPECS.md`](docs/SPECS.md:1)