# BrewBuddy Technical Specifications

## Overview
This document translates the requirements from [`PRD.md`](PRD.md) into actionable technical specifications for BrewBuddy.

## High-Level Architecture
- **Frontend:** React (responsive, mobile-friendly)
- **Backend:** Node.js/Express
- **Database:** SQLite or PostgreSQL (local-first, sync-ready)
- **Storage:** Local storage for offline access

## Feature Breakdown

### 1. Guided Brew Day Workflow
**User Story:** As a homebrewer, I want a step-by-step guide for brew day, with timers and measurement logging.
**Technical Tasks:**
- [ ] Create data model for brew day steps (mashing, boiling, hop additions, cooling, transferring)
- [ ] Build wizard-style UI for step progression
- [ ] Implement per-step custom instructions, timers, and measurement logging (temperature, gravity, notes)
- [ ] Allow configuration of steps per recipe
**Acceptance Criteria:**
- User can progress through steps, set timers, and log measurements
- Data is saved locally and linked to the recipe/batch

### 2. Recipe Builder
**User Story:** As a user, I want to create and edit recipes with all relevant fields and automatic calculations.
**Technical Tasks:**
- [ ] Design recipe schema: malt, hops, yeast, adjuncts, water, batch size
- [ ] UI tabs for all-grain vs. extract recipes
- [ ] Implement auto-calculation for ABV, IBU, SRM, calories
- [ ] Support recipe versioning and editing
**Acceptance Criteria:**
- User can create, edit, and version recipes
- Calculations update automatically, but can be overridden

### 3. Fermentation Tracker
**User Story:** As a brewer, I want to log fermentation readings and view progress as a graph.
**Technical Tasks:**
- [ ] Data model for fermentation logs: gravity, temperature, notes, date/time
- [ ] Link logs to recipes and batches
- [ ] UI for entering readings and displaying graph
- [ ] Optional reminders for logging readings
**Acceptance Criteria:**
- Multiple readings per batch are supported and graphed
- Logs are linked to the correct recipe/batch

### 4. Inventory Management
**User Story:** As a user, I want to track ingredient inventory and get alerts for low/missing items.
**Technical Tasks:**
- [ ] Data model for grains, hops, yeast, adjuncts with quantities
- [ ] Automatic quantity updates when brewing
- [ ] Manual adjustment UI
- [ ] Alert system for low/missing inventory
**Acceptance Criteria:**
- Inventory updates automatically and manually
- Alerts show when ingredients are low/missing

### 5. Export/Sharing
**User Story:** As a user, I want to export recipes and logs in standard formats.
**Technical Tasks:**
- [ ] Implement export to BeerXML and CSV
- [ ] Export includes all recipe details and logs
- [ ] UI for export actions
**Acceptance Criteria:**
- User can export recipes/logs as BeerXML or CSV
- No direct sharing or import required

## Data Models / Schema

- **Recipe:** id, name, type (all-grain/extract), malt[], hops[], yeast[], adjuncts[], water, batch_size, version, created_at, updated_at
- **BrewDayStep:** id, recipe_id, name, instructions, timer, measurements[]
- **FermentationLog:** id, batch_id, gravity, temperature, notes, date_time
- **InventoryItem:** id, type, name, quantity, unit, low_threshold
- **Batch:** id, recipe_id, start_date, end_date, notes

## API Endpoints (if applicable)
- `GET /api/recipes` — List recipes
- `POST /api/recipes` — Create recipe
- `PUT /api/recipes/:id` — Edit recipe
- `GET /api/inventory` — List inventory
- `POST /api/batches` — Start new batch
- `POST /api/fermentation-logs` — Add fermentation reading
- `GET /api/export/:id?format=beerxml|csv` — Export recipe/logs

## Open Technical Questions
- How will offline sync and local storage be handled for multi-device use?
- What is the best approach for recipe versioning and rollback?
- Should reminders/notifications use browser APIs or a backend service?
