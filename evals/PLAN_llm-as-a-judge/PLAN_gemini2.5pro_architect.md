# BrewBuddy Technical Plan

**Source Documents:**
- [Product Requirements Document (PRD)](PRD.md)
- [Technical Specifications (SPECS)](SPECS.md)

---

## Legend

**Task Status:**
- `[ ]` **To Do:** Task has not been started.
- `[-]` **In Progress:** Task is actively being worked on.
- `[x]` **Done:** Task is complete.

**Priority Levels:**
- **P0:** Critical for launch. Must-have.
- **P1:** Important for launch. High-priority.
- **P2:** Nice to have. Can be addressed post-launch.

---

## 0. Project/Architecture Setup (P0)

- `[ ]` Set up frontend project with React.
- `[ ]` Set up backend project with Node.js/Express.
- `[ ]` Configure database (SQLite for local-first approach).
- `[ ]` Establish local storage solution for offline access.

---

## 1. Data Models / Schema (P0)

- `[ ]` Implement Recipe schema.
- `[ ]` Implement BrewDayStep schema.
- `[ ]` Implement FermentationLog schema.
- `[ ]` Implement InventoryItem schema.
- `[ ]` Implement Batch schema.

---

## 2. Feature 1: Recipe Builder (P0)

- `[ ]` Design and implement UI for creating and editing recipes.
- `[ ]` Add UI tabs for all-grain vs. extract recipes.
- `[ ]` Implement automatic calculation for ABV, IBU, and SRM.
- `[ ]` Implement recipe versioning and editing capabilities.

---

## 3. Feature 2: Guided Brew Day Workflow (P1)

- `[ ]` Build a wizard-style UI for step-by-step brew day guidance.
- `[ ]` Implement per-step custom instructions, timers, and measurement logging.
- `[ ]` Allow configuration of brew day steps for each recipe.

---

## 4. Feature 3: Inventory Management (P1)

- `[ ]` Create UI for manual inventory adjustments.
- `[ ]` Implement automatic quantity updates when a brew is started.
- `[ ]` Develop an alert system for low or missing inventory.

---

## 5. Feature 4: Fermentation Tracker (P2)

- `[ ]` Develop UI for entering fermentation readings.
- `[ ]` Display fermentation progress as a graph.
- `[ ]` Implement optional reminders for logging readings.

---

## 6. Feature 5: Export/Sharing (P2)

- `[ ]` Implement export functionality to BeerXML format.
- `[ ]` Implement export functionality to CSV format.
- `[ ]` Create a UI for export actions.

---

## Cross-Cutting Concerns

### API Layer (P1)
- `[ ]` Implement `GET /api/recipes` to list recipes.
- `[ ]` Implement `POST /api/recipes` to create a recipe.
- `[ ]` Implement `PUT /api/recipes/:id` to edit a recipe.
- `[ ]` Implement `GET /api/inventory` to list inventory.
- `[ ]` Implement `POST /api/batches` to start a new batch.
- `[ ]` Implement `POST /api/fermentation-logs` to add a fermentation reading.
- `[ ]` Implement `GET /api/export/:id?format=beerxml|csv` to export recipes and logs.

### QA / Testing (P1)
- `[ ]` Set up a testing framework (e.g., Jest/React Testing Library).
- `[ ]` Write unit tests for all major components and functions.
- `[ ]` Conduct end-to-end testing for all user flows.

### Performance & UX (P2)
- `[ ]` Ensure the application is mobile-friendly and responsive.
- `[ ]` Optimize for fast load times and smooth navigation.
- `[ ]` Ensure all features work offline as expected.

### Documentation (P2)
- `[ ]` Create a `README.md` with setup and usage instructions.
- `[ ]` Add comments to the code where necessary.

---

## Open Technical Questions

- How will offline sync and local storage be handled for multi-device use?
- What is the best approach for recipe versioning and rollback?
- Should reminders/notifications use browser APIs or a backend service?

---

## Milestone Grouping

### Milestone 1: Core Functionality (P0-P1)
- Project/Architecture Setup
- Data Models / Schema
- Feature 1: Recipe Builder
- Feature 2: Guided Brew Day Workflow
- Feature 3: Inventory Management
- API Layer
- QA / Testing

### Milestone 2: Advanced Features (P2)
- Feature 4: Fermentation Tracker
- Feature 5: Export/Sharing
- Performance & UX
- Documentation

---

## Acceptance Summary

The project will be considered complete when:
- All P0 and P1 tasks are completed and tested.
- A user can successfully create a recipe, follow the guided brew day, and track inventory.
- The application is stable and provides a smooth user experience.

---

## Tracking

**Instructions for Orchestrator:** As you complete each task, update its status by changing the checkbox from `[ ]` to `[x]`. If a task is in progress, change it to `[-]`.