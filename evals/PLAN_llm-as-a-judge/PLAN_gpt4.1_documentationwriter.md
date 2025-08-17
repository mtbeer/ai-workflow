# BrewBuddy Technical Implementation Plan

[View PRD.md](./PRD.md) | [View SPECS.md](./SPECS.md)

---

## Legend

- **Task Statuses:**  
  - [ ] = Pending  
  - [-] = In Progress  
  - [x] = Completed  
- **Priority:**  
  - **P0** = Critical for launch  
  - **P1** = Important, but not blocking launch  
  - **P2** = Nice-to-have, post-launch

---

## 0. Project / Architecture Setup (P0)

- [ ] Initialize React frontend and Node.js/Express backend
- [ ] Set up SQLite/PostgreSQL database (local-first)
- [ ] Configure local storage for offline access
- [ ] Set up project structure and repo
- [ ] Implement basic navigation and mobile-friendly layout

---

## 1. Data Models / Schema (P0)

- [ ] Design and implement Recipe schema
- [ ] Design BrewDayStep schema
- [ ] Design FermentationLog schema
- [ ] Design InventoryItem schema
- [ ] Design Batch schema

---

## 2. Guided Brew Day Workflow (P0)

- [ ] Create data model for brew day steps (mashing, boiling, hop additions, cooling, transferring)
- [ ] Build wizard-style UI for step progression
- [ ] Implement per-step custom instructions, timers, and measurement logging (temperature, gravity, notes)
- [ ] Allow configuration of steps per recipe
- [ ] Link brew day data to recipe/batch
- [ ] Ensure offline functionality

---

## 3. Recipe Builder (P0)

- [ ] Design recipe schema: malt, hops, yeast, adjuncts, water, batch size
- [ ] UI tabs for all-grain vs. extract recipes
- [ ] Implement auto-calculation for ABV, IBU, SRM, calories
- [ ] Support recipe versioning and editing
- [ ] Allow override of calculations
- [ ] Ensure data is stored locally

---

## 4. Fermentation Tracker (P1)

- [ ] Data model for fermentation logs: gravity, temperature, notes, date/time
- [ ] Link logs to recipes and batches
- [ ] UI for entering readings and displaying graph
- [ ] Optional reminders for logging readings

---

## 5. Inventory Management (P1)

- [ ] Data model for grains, hops, yeast, adjuncts with quantities
- [ ] Automatic quantity updates when brewing
- [ ] Manual adjustment UI
- [ ] Alert system for low/missing inventory

---

## 6. Export / Sharing (P2)

- [ ] Implement export to BeerXML and CSV
- [ ] Export includes all recipe details and logs
- [ ] UI for export actions

---

## Cross-Cutting Concerns

### API Layer

- [ ] Implement REST API endpoints for recipes, inventory, batches, fermentation logs, export
- [ ] Ensure API supports offline/local-first operations

### QA / Testing

- [ ] Write unit and integration tests for core features
- [ ] Manual QA for offline and mobile scenarios

### Performance & UX

- [ ] Optimize for mobile responsiveness
- [ ] Ensure fast load times and smooth navigation

### Documentation

- [ ] Update user documentation for each feature
- [ ] Maintain developer docs for API and data models

---

## Open Technical Questions

- How will offline sync and local storage be handled for multi-device use?
- What is the best approach for recipe versioning and rollback?
- Should reminders/notifications use browser APIs or a backend service?
- What export formats are required for future integrations?
- How will user authentication and cloud backup be handled (future)?

---

## Milestone Grouping

**Milestone 1: Core Functionality (P0)**
- Project/Architecture Setup
- Data Models / Schema
- Guided Brew Day Workflow
- Recipe Builder

**Milestone 2: Advanced Features (P1)**
- Fermentation Tracker
- Inventory Management

**Milestone 3: Sharing & Polish (P2)**
- Export / Sharing
- Performance & UX
- Documentation

---

## Acceptance Summary

- All P0 tasks completed and tested
- User can create, edit, and track recipes and brew days
- Inventory and fermentation tracking functional
- Data export works as specified
- App works offline and is mobile-friendly

---

## Instructions for Orchestrator

As you complete each task, update its status by changing the checkbox from [ ] to [x]. If a task is in progress, change it to [-]. Always keep PLAN.md up to date after each change.
