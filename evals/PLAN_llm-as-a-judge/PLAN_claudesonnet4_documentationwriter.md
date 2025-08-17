# BrewBuddy Technical Implementation Plan

**Source Documents:** [`PRD.md`](PRD.md) | [`SPECS.md`](SPECS.md)

## Legend

**Task Status:**
- `[ ]` = Pending (not started)
- `[-]` = In Progress (currently being worked on)  
- `[x]` = Completed (fully finished, no unresolved issues)

**Priority Levels:**
- **P0** = Critical for MVP launch
- **P1** = Important for initial release
- **P2** = Nice to have / future enhancement

---

## 0. Project/Architecture Setup (P0)

- [ ] Initialize React frontend project with TypeScript and PWA capabilities
- [ ] Set up Node.js/Express backend with TypeScript
- [ ] Configure SQLite database for local-first storage with WAL mode
- [ ] Set up build and development scripts with offline-first bundling
- [ ] Configure ESLint, Prettier, and Git hooks for code quality
- [ ] Create basic project structure and folder organization
- [ ] Set up environment configuration (dev/prod) with feature flags
- [ ] Configure CORS and basic middleware
- [ ] Set up local storage utilities with encryption for sensitive data
- [ ] Implement service worker for offline functionality
- [ ] Set up unit conversion system (metric/imperial) as core utility

## 1. Data Models / Schema (P0)

- [ ] Create Recipe model schema (id, name, type, malt[], hops[], yeast[], adjuncts[], water, batch_size, version, timestamps)
- [ ] Create BrewDayStep model schema (id, recipe_id, name, instructions, timer, measurements[])
- [ ] Create Batch model schema (id, recipe_id, start_date, end_date, notes)
- [ ] Create InventoryItem model schema (id, type, name, quantity, unit, low_threshold)
- [ ] Create FermentationLog model schema (id, batch_id, gravity, temperature, notes, date_time)
- [ ] Set up database migrations and seeding
- [ ] Create TypeScript interfaces for all models
- [ ] Implement basic CRUD operations for all models
- [ ] Set up data validation schemas

## 2. Recipe Builder (P0)

- [ ] Design recipe creation UI with tabbed interface (all-grain vs extract)
- [ ] Implement ingredient input forms (malt, hops, yeast, adjuncts, water)
- [ ] Build batch size and recipe type selection with unit preferences
- [ ] Create brewing calculation engine for ABV estimation
- [ ] Implement IBU calculation algorithms (Tinseth, Rager methods)
- [ ] Add SRM color calculation and color preview
- [ ] Implement calorie calculation based on ingredients
- [ ] Add comprehensive recipe validation and error handling
- [ ] Create recipe editing and versioning functionality with change tracking
- [ ] Implement recipe save/load from local storage with backup
- [ ] Add recipe duplication and template features
- [ ] Integrate unit conversion throughout recipe interface
- [ ] Create recipe list/grid view with search and filtering
- [ ] Add recipe import validation for common formats

## 3. Basic Inventory Management (P0)

- [ ] Create inventory item creation/editing UI
- [ ] Implement inventory list view with search/filter
- [ ] Add manual quantity adjustment functionality
- [ ] Create basic low-stock alert system
- [ ] Implement inventory-recipe integration for availability checking
- [ ] Add ingredient consumption tracking during brewing
- [ ] Create inventory import/export functionality

## 4. Guided Brew Day Workflow (P1)

- [ ] Design step-by-step wizard UI for brew day
- [ ] Implement brew day step progression system
- [ ] Create timer functionality for each step
- [ ] Build measurement logging interface (temperature, gravity, notes)
- [ ] Add customizable step instructions per recipe
- [ ] Implement step completion tracking
- [ ] Create brew day session save/resume functionality
- [ ] Add brew day summary and completion
- [ ] Link brew day data to batch records

## 5. Export/Sharing Functionality (P1)

- [ ] Implement BeerXML export for recipes
- [ ] Create CSV export for recipes and logs
- [ ] Build export UI with format selection
- [ ] Add batch export functionality
- [ ] Implement fermentation log export
- [ ] Create export history tracking
- [ ] Add export validation and error handling

## 6. Fermentation Tracker (P2)

- [ ] Create fermentation log entry UI
- [ ] Implement gravity and temperature input forms
- [ ] Build fermentation progress graph/chart
- [ ] Add fermentation log list view
- [ ] Create fermentation reminder system
- [ ] Implement log editing and deletion
- [ ] Add fermentation calculations (attenuation, ABV tracking)
- [ ] Link fermentation logs to batches

---

## API Layer

- [ ] Set up Express router structure with versioning support
- [ ] Implement recipes API endpoints (GET, POST, PUT, DELETE) with validation
- [ ] Create inventory API endpoints with transaction support
- [ ] Build batches API endpoints with brew day integration
- [ ] Add fermentation logs API endpoints with batch linking
- [ ] Implement export API endpoints with format validation
- [ ] Add comprehensive API request/response validation using Joi/Zod
- [ ] Create centralized API error handling middleware
- [ ] Add API logging and monitoring with request tracking
- [ ] Implement API rate limiting and security headers
- [ ] Add data backup and restore API endpoints

## QA / Testing

- [ ] Set up Jest testing framework
- [ ] Write unit tests for data models
- [ ] Create API endpoint tests
- [ ] Add React component tests
- [ ] Implement integration tests for key workflows
- [ ] Set up test database and fixtures
- [ ] Create end-to-end testing setup
- [ ] Add test coverage reporting
- [ ] Implement continuous testing in CI/CD

## Performance & UX

- [ ] Optimize local storage performance with indexing
- [ ] Implement lazy loading for large recipe lists and ingredient catalogs
- [ ] Add loading states, spinners, and skeleton screens
- [ ] Create responsive design optimized for mobile brew day use
- [ ] Optimize bundle size with code splitting and tree shaking
- [ ] Add offline functionality indicators and sync status
- [ ] Implement intelligent data caching with LRU eviction
- [ ] Add keyboard shortcuts for power users and accessibility
- [ ] Create comprehensive accessibility improvements (ARIA, screen readers)
- [ ] Implement progressive web app features (install prompt, etc.)
- [ ] Add dark mode support for low-light brewing environments
- [ ] Optimize touch interactions for mobile devices

## Documentation

- [ ] Create comprehensive user guide for recipe creation and editing
- [ ] Write detailed brew day workflow documentation with screenshots
- [ ] Document all API endpoints and schemas with OpenAPI/Swagger
- [ ] Create developer setup guide with environment requirements
- [ ] Add inline code documentation and JSDoc comments
- [ ] Create troubleshooting guide for common issues
- [ ] Document export/import procedures with format specifications
- [ ] Add architecture decision records (ADRs) for major technical choices
- [ ] Create video tutorials for key workflows
- [ ] Document unit conversion formulas and calculation methods
- [ ] Add FAQ section for common user questions

---

## Open Technical Questions

- [ ] **Offline Sync Strategy:** How should we handle data synchronization when the app comes back online? Should we implement conflict resolution?
- [ ] **Recipe Versioning:** What's the best approach for recipe versioning and rollback functionality?
- [ ] **Notifications:** Should brewing reminders use browser notifications, or should we implement a backend notification service?
- [ ] **Data Migration:** How do we handle schema changes and data migrations as the app evolves?
- [ ] **Performance:** What's the maximum number of recipes/batches we should optimize for in local storage?
- [ ] **Units System:** Should we store all data in metric and convert on display, or store in user's preferred units?

---

## Milestone Grouping

### Milestone 1: Core MVP (P0 Tasks)
**Target:** Functional recipe builder with basic inventory
- Project/Architecture Setup
- Data Models / Schema  
- Recipe Builder
- Basic Inventory Management

### Milestone 2: Brewing Features (P1 Tasks)
**Target:** Complete brewing workflow support
- Guided Brew Day Workflow
- Export/Sharing Functionality
- API Layer completion
- Core QA/Testing

### Milestone 3: Advanced Features (P2 Tasks)
**Target:** Enhanced user experience
- Fermentation Tracker
- Performance & UX improvements
- Comprehensive Documentation
- Advanced Testing

---

## Acceptance Summary

**Project completion is defined by:**

1. **Core Functionality:** Users can create, edit, and manage recipes with automatic calculations
2. **Inventory Management:** Users can track ingredients and receive low-stock alerts
3. **Brew Day Support:** Users can follow guided workflow with timers and measurement logging
4. **Data Export:** Users can export recipes and logs in BeerXML and CSV formats
5. **Offline Capability:** App functions completely offline during brew day
6. **Mobile Responsive:** App works seamlessly on mobile devices
7. **Data Persistence:** All data is stored locally and survives app restarts
8. **Unit Support:** Both metric and imperial units are supported throughout
9. **Testing Coverage:** 80%+ test coverage for core functionality
10. **Documentation:** Complete user and developer documentation

**Success Metrics from PRD:**
- Support for logging 10+ brews
- Enable export of 5+ recipes
- Consistent repeat usage patterns
- Positive feedback from homebrewing community

---

## Tracking Instructions

**Instructions for Orchestrator:** As you complete each task, update its status by changing the checkbox from `[ ]` to `[x]`. If a task is in progress, change it to `[-]`. When starting work on a new section, mark the first task as `[-]` to indicate progress. Always commit changes to this PLAN.md file after updating task statuses so progress is tracked in version control.

**Update Process:**
1. Mark task as `[-]` when starting work
2. Update to `[x]` when fully completed and tested
3. Commit PLAN.md changes with descriptive message
4. Move to next priority task in logical sequence
5. Update Open Technical Questions as they are resolved
6. Add new tasks if discovered during implementation