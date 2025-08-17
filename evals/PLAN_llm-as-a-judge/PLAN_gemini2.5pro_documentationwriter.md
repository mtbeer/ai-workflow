# BrewBuddy Technical Plan

**Source Documents:**
- [Product Requirements Document (PRD)](PRD.md)
- [Technical Specifications (SPECS)](SPECS.md)

## Legend

- **Status:**
  - `[ ]` - To Do
  - `[-]` - In Progress
  - `[x]` - Done
- **Priority:**
  - **P0:** Critical for launch.
  - **P1:** Important, but can follow the initial release.
  - **P2:** Nice to have.

---

## 0. Project/Architecture Setup (P0)

- [ ] Initialize React frontend application.
- [ ] Set up Node.js/Express backend server.
- [ ] Choose and configure the database (SQLite or PostgreSQL).
- [ ] Implement local storage for offline access.

## 1. Data Models / Schema (P0)

- [ ] Define and implement the `Recipe` schema.
- [ ] Define and implement the `BrewDayStep` schema.
- [ ] Define and implement the `FermentationLog` schema.
- [ ] Define and implement the `InventoryItem` schema.
- [ ] Define and implement the `Batch` schema.

## 2. Feature 1: Recipe Builder (P0)

- [ ] Design and build the UI for creating and editing recipes.
- [ ] Implement UI tabs for all-grain vs. extract recipes.
- [ ] Implement automatic calculation for ABV, IBU, SRM, and calories.
- [ ] Implement recipe versioning and editing capabilities.

## 3. Feature 2: Guided Brew Day Workflow (P0)

- [ ] Create the data model for brew day steps.
- [ ] Build a wizard-style UI for step-by-step progression.
- [ ] Implement per-step custom instructions, timers, and measurement logging.
- [ ] Allow configuration of steps for each recipe.

## 4. Feature 3: Inventory Management (P1)

- [ ] Create the data model for inventory items.
- [ ] Implement automatic quantity updates when brewing.
- [ ] Build the UI for manual inventory adjustments.
- [ ] Implement an alert system for low or missing inventory.

## 5. Feature 4: Fermentation Tracker (P1)

- [ ] Create the data model for fermentation logs.
- [ ] Link logs to recipes and batches.
- [ ] Build the UI for entering readings and displaying a graph.
- [ ] Implement optional reminders for logging readings.

## 6. Feature 5: Export/Sharing (P2)

- [ ] Implement export functionality to BeerXML and CSV formats.
- [ ] Ensure the export includes all recipe details and logs.
- [ ] Build the UI for export actions.

---

## Cross-Cutting Concerns

### API Layer

- [ ] `GET /api/recipes`
- [ ] `POST /api/recipes`
- [ ] `PUT /api/recipes/:id`
- [ ] `GET /api/inventory`
- [ ] `POST /api/batches`
- [ ] `POST /api/fermentation-logs`
- [ ] `GET /api/export/:id?format=beerxml|csv`

### QA / Testing

- [ ] Set up a testing framework (e.g., Jest, React Testing Library).
- [ ] Write unit tests for all major functions and components.
- [ ] Write integration tests for the API endpoints.

### Performance & UX

- [ ] Ensure the application is responsive and mobile-friendly.
- [ ] Optimize for fast load times.
- [ ] Ensure data is stored and retrieved efficiently from local storage.

### Documentation

- [ ] Add comments to the code where necessary.
- [ ] Create a `README.md` with setup and usage instructions.

---

## Open Technical Questions

- How will offline sync and local storage be handled for multi-device use?
- What is the best approach for recipe versioning and rollback?
- Should reminders/notifications use browser APIs or a backend service?

---

## Milestone Grouping

### Milestone 1: Core Functionality (P0)

- 0. Project/Architecture Setup
- 1. Data Models / Schema
- 2. Feature 1: Recipe Builder
- 3. Feature 2: Guided Brew Day Workflow

### Milestone 2: Advanced Features (P1)

- 4. Feature 3: Inventory Management
- 5. Feature 4: Fermentation Tracker

### Milestone 3: Final Touches (P2)

- 6. Feature 5: Export/Sharing
- Complete all cross-cutting concerns.

---

## Acceptance Summary

The project will be considered complete when:
- All P0 and P1 features are fully implemented and tested.
- The application is stable and performs well on mobile devices.
- The application works offline.
- All success metrics from the PRD are met.

---

## Tracking

**Instructions for Orchestrator:** As you complete each task, update its status by changing the checkbox from `[ ]` to `[x]`. If a task is in progress, change it to `[-]`.