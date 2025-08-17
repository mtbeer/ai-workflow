# BrewBuddy Technical Plan

**Source Documents:**  
- [Product Requirements Document (PRD.md)](PRD.md)
- [Technical Specifications (SPECS.md)](SPECS.md)

---

## Legend

- **Task Status:**  
  - [ ] Pending  
  - [-] In Progress  
  - [x] Completed
- **Priority:**  
  - P0: Launch-critical  
  - P1: Important, but not blocking launch  
  - P2: Nice-to-have / future

---

## 0. Project/Architecture Setup (P0)
- [ ] Set up React frontend and Node.js/Express backend
- [ ] Configure SQLite/PostgreSQL for local-first storage
- [ ] Implement local storage for offline access
- [ ] Establish project structure and code conventions

## 1. Data Models / Schema (P0)
- [ ] Design schema for Recipe, BrewDayStep, FermentationLog, InventoryItem, Batch
- [ ] Implement models in backend and sync with frontend
- [ ] Support both all-grain and extract recipes
- [ ] Ensure support for metric and imperial units

## 2. Guided Brew Day Workflow (P0)
- [ ] Design BrewDayStep data model
- [ ] Build wizard-style UI for step progression
- [ ] Implement per-step instructions, timers, measurement logging
- [ ] Link brew day data to recipes/batches
- [ ] Enable configuration of steps per recipe

## 3. Recipe Builder (P0)
- [ ] Design recipe schema (malt, hops, yeast, adjuncts, water, batch size)
- [ ] Create UI tabs for all-grain vs. extract
- [ ] Implement auto-calculation (ABV, IBU, SRM, calories)
- [ ] Support recipe versioning/editing

## 4. QA / Testing (P0)
- [ ] Write unit tests for data models and core logic
- [ ] Implement integration tests for workflows
- [ ] Manual QA for mobile/offline scenarios

## 5. Documentation (P0)
- [ ] Write user guide for core features
- [ ] Document API endpoints and data models
- [ ] Update README with setup and usage

## 6. Fermentation Tracker (P1)
- [ ] Design fermentation log data model
- [ ] Link logs to recipes/batches
- [ ] UI for readings and graph display
- [ ] Implement reminders for readings

## 7. Inventory Management (P1)
- [ ] Data model for inventory items
- [ ] Auto-update quantities when brewing
- [ ] Manual adjustment UI
- [ ] Alert system for low/missing inventory

## 8. Export/Sharing (P1)
- [ ] Export to BeerXML and CSV
- [ ] Export includes all recipe/log details
- [ ] UI for export actions

## 9. API Layer (P1)
- [ ] Define REST endpoints for recipes, inventory, batches, fermentation logs, export
- [ ] Implement backend logic for CRUD and export
- [ ] Ensure local-first and offline support

## 10. Performance & UX (P1)
- [ ] Optimize UI responsiveness for mobile
- [ ] Tune local storage and sync logic
- [ ] Improve navigation and ease of use

---

## 11. Open Technical Questions
- [ ] How will offline sync and local storage be handled for multi-device use?
- [ ] What is the best approach for recipe versioning and rollback?
- [ ] Should reminders/notifications use browser APIs or a backend service?
- [ ] What export formats should be supported long-term?
- [ ] How will user authentication and cloud backup be managed (future)?
- [ ] Any constraints for supporting both metric and imperial units?

---

## 12. Milestone Grouping

**Milestone 1: Core Functionality (P0)**
- Project/Architecture Setup
- Data Models / Schema
- Guided Brew Day Workflow
- Recipe Builder
- QA / Testing
- Documentation

**Milestone 2: Advanced Features (P1)**
- Fermentation Tracker
- Inventory Management
- Export/Sharing
- API Layer
- Performance & UX

**Milestone 3: Open Questions & Future Enhancements (P2)**
- Address open technical questions
- Explore cloud backup, authentication, additional export formats

---

## 13. Acceptance Summary

- All P0 tasks completed and tested
- User can create, edit, and track recipes and brew days
- Inventory and fermentation features functional
- Data export works for BeerXML and CSV
- App is mobile-friendly and works offline
- Documentation and user guide available
- All open technical questions resolved or deferred

---

## 14. Instructions for Orchestrator

- As you complete each task, update its status by changing the checkbox from [ ] to [x].
- If a task is in progress, change it to [-].
- After completing a milestone, mark all its tasks as [x] and note milestone completion.
- For open technical questions, update with answers or decisions as they are resolved.
- Always keep PLAN.md up to date with the latest progress and decisions.
