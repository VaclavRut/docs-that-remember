# Development Tasks: [Feature Name]

> **LLM-executable tasks**
>
> This document contains specific, actionable tasks that can be executed by developers (human or AI). Each task should be atomic, testable, and clearly defined.

---

## Overview

**Feature:** [Feature Name]

**Status:** [Not Started | In Progress | Complete]

**Last Updated:** [YYYY-MM-DD]

## Task Breakdown

### Setup & Infrastructure
<!-- Preparation work before feature development -->

- [ ] **TASK-001: Set up development environment**
  - Create feature branch: `feature/[feature-name]`
  - Install required dependencies
  - Configure environment variables
  - **Acceptance:** Branch created, dependencies installed, env vars set
  - **Estimate:** [time estimate]

- [ ] **TASK-002: Create database migrations**
  - Create migration file for [table/schema changes]
  - Add rollback migration
  - Test migration on local database
  - **Acceptance:** Migrations run successfully up and down
  - **Files:** `migrations/[timestamp]_[migration_name].sql`
  - **Estimate:** [time estimate]

### Backend Development

- [ ] **TASK-101: Create data model**
  - Define `[ModelName]` interface/class
  - Add validation rules
  - Write unit tests for model
  - **Acceptance:** Model defined, validated, tests passing
  - **Files:** `src/models/[model-name].ts`
  - **Tests:** `src/models/[model-name].test.ts`
  - **Estimate:** [time estimate]

- [ ] **TASK-102: Implement [ServiceName] service**
  - Create service class/module
  - Implement [method1], [method2], [method3]
  - Add error handling
  - Write unit tests
  - **Acceptance:** Service methods work, error cases handled, tests pass
  - **Files:** `src/services/[service-name].ts`
  - **Tests:** `src/services/[service-name].test.ts`
  - **Dependencies:** TASK-101
  - **Estimate:** [time estimate]

- [ ] **TASK-103: Create API endpoint `POST /api/[resource]`**
  - Define route handler
  - Add request validation
  - Add authentication/authorization
  - Implement business logic
  - Add error handling
  - Write integration tests
  - **Acceptance:** Endpoint returns correct responses, auth works, tests pass
  - **Files:** `src/routes/[resource].ts`
  - **Tests:** `src/routes/[resource].test.ts`
  - **Dependencies:** TASK-102
  - **Estimate:** [time estimate]

- [ ] **TASK-104: Create API endpoint `GET /api/[resource]/:id`**
  - Define route handler
  - Add authentication/authorization
  - Implement retrieval logic
  - Add error handling (404, 403, etc.)
  - Write integration tests
  - **Acceptance:** Endpoint retrieves data correctly, handles errors, tests pass
  - **Files:** `src/routes/[resource].ts`
  - **Tests:** `src/routes/[resource].test.ts`
  - **Dependencies:** TASK-102
  - **Estimate:** [time estimate]

### Frontend Development

- [ ] **TASK-201: Create [ComponentName] component**
  - Create component file
  - Implement UI layout
  - Add prop types/interfaces
  - Add basic styling
  - Write component tests
  - **Acceptance:** Component renders, props work, tests pass
  - **Files:** `src/components/[ComponentName]/index.tsx`
  - **Files:** `src/components/[ComponentName]/styles.css`
  - **Tests:** `src/components/[ComponentName]/[ComponentName].test.tsx`
  - **Estimate:** [time estimate]

- [ ] **TASK-202: Implement [ComponentName] state management**
  - Set up state (useState/Redux/etc)
  - Implement state update functions
  - Add state validation
  - Write state logic tests
  - **Acceptance:** State updates correctly, validation works, tests pass
  - **Files:** `src/components/[ComponentName]/index.tsx`
  - **Dependencies:** TASK-201
  - **Estimate:** [time estimate]

- [ ] **TASK-203: Connect [ComponentName] to API**
  - Create API client functions
  - Implement data fetching
  - Add loading states
  - Add error handling
  - Write integration tests
  - **Acceptance:** Data loads correctly, loading/error states work, tests pass
  - **Files:** `src/api/[resource].ts`
  - **Files:** `src/components/[ComponentName]/index.tsx`
  - **Dependencies:** TASK-103, TASK-104, TASK-202
  - **Estimate:** [time estimate]

- [ ] **TASK-204: Add form validation to [ComponentName]**
  - Implement field validation rules
  - Add validation error messages
  - Add visual error indicators
  - Prevent invalid submissions
  - Write validation tests
  - **Acceptance:** Validation works, errors display, invalid forms blocked, tests pass
  - **Files:** `src/components/[ComponentName]/validation.ts`
  - **Dependencies:** TASK-201
  - **Estimate:** [time estimate]

- [ ] **TASK-205: Style [ComponentName] component**
  - Implement responsive design
  - Add hover/focus states
  - Ensure accessibility (ARIA labels, keyboard nav)
  - Test on multiple screen sizes
  - **Acceptance:** Looks good on all devices, accessible, passes a11y tests
  - **Files:** `src/components/[ComponentName]/styles.css`
  - **Dependencies:** TASK-201
  - **Estimate:** [time estimate]

### Integration & Polish

- [ ] **TASK-301: Integrate [ComponentName] into [ParentComponent]**
  - Import and render component
  - Pass required props
  - Handle component events
  - Update parent state as needed
  - Test integration
  - **Acceptance:** Component works in parent, data flows correctly
  - **Files:** `src/components/[ParentComponent]/index.tsx`
  - **Dependencies:** TASK-203, TASK-205
  - **Estimate:** [time estimate]

- [ ] **TASK-302: Add error boundaries**
  - Create error boundary component
  - Wrap feature in error boundary
  - Add error logging
  - Add user-friendly error UI
  - Test error scenarios
  - **Acceptance:** Errors caught gracefully, logged, user sees helpful message
  - **Files:** `src/components/ErrorBoundary.tsx`
  - **Estimate:** [time estimate]

- [ ] **TASK-303: Implement loading states**
  - Add loading indicators
  - Add skeleton screens
  - Optimize perceived performance
  - **Acceptance:** User sees feedback during loads, no layout shift
  - **Files:** Various component files
  - **Estimate:** [time estimate]

- [ ] **TASK-304: Add analytics tracking**
  - Track key user actions
  - Add custom events
  - Test analytics in dev
  - **Acceptance:** Events fire correctly, data captured
  - **Files:** `src/analytics/[feature-name].ts`
  - **Estimate:** [time estimate]

### Testing

- [ ] **TASK-401: Write E2E tests for happy path**
  - Set up test data
  - Write test for main user flow
  - Verify all steps work end-to-end
  - **Acceptance:** E2E test passes consistently
  - **Files:** `tests/e2e/[feature-name].spec.ts`
  - **Dependencies:** All development tasks
  - **Estimate:** [time estimate]

- [ ] **TASK-402: Write E2E tests for error cases**
  - Test invalid input handling
  - Test network error scenarios
  - Test authorization failures
  - **Acceptance:** Error cases handled correctly in E2E tests
  - **Files:** `tests/e2e/[feature-name]-errors.spec.ts`
  - **Dependencies:** All development tasks
  - **Estimate:** [time estimate]

- [ ] **TASK-403: Performance testing**
  - Test with large datasets
  - Test concurrent users
  - Measure response times
  - Identify bottlenecks
  - **Acceptance:** Meets performance requirements from tech design
  - **Dependencies:** All development tasks
  - **Estimate:** [time estimate]

- [ ] **TASK-404: Accessibility testing**
  - Run automated a11y tests
  - Test with screen reader
  - Test keyboard navigation
  - Fix any issues found
  - **Acceptance:** Passes WCAG 2.1 AA standards
  - **Dependencies:** All frontend tasks
  - **Estimate:** [time estimate]

### Documentation

- [ ] **TASK-501: Update API documentation**
  - Document new endpoints
  - Add request/response examples
  - Document error codes
  - **Acceptance:** API docs are complete and accurate
  - **Files:** `docs/api/[resource].md` or OpenAPI spec
  - **Dependencies:** Backend tasks complete
  - **Estimate:** [time estimate]

- [ ] **TASK-502: Write user guide**
  - Create user-facing documentation
  - Add screenshots/examples
  - Document common issues
  - **Acceptance:** Users can understand how to use feature
  - **Files:** `docs/user-guide/[feature-name].md`
  - **Dependencies:** All development tasks
  - **Estimate:** [time estimate]

- [ ] **TASK-503: Update system map**
  - Add new components to system map
  - Document new data flows
  - Update architecture diagrams
  - **Acceptance:** System map reflects current state
  - **Files:** `docs/00-context/system-map.md`
  - **Dependencies:** All development tasks
  - **Estimate:** [time estimate]

### Deployment

- [ ] **TASK-601: Create feature flag**
  - Add feature flag configuration
  - Wrap feature in flag check
  - Test flag on/off states
  - **Acceptance:** Feature can be toggled without deployment
  - **Files:** `src/config/feature-flags.ts`
  - **Estimate:** [time estimate]

- [ ] **TASK-602: Deploy to staging**
  - Merge to staging branch
  - Run deployment pipeline
  - Verify deployment success
  - Smoke test on staging
  - **Acceptance:** Feature works on staging environment
  - **Dependencies:** All development tasks complete
  - **Estimate:** [time estimate]

- [ ] **TASK-603: Production deployment**
  - Create deployment plan
  - Schedule deployment window
  - Deploy to production
  - Enable feature flag gradually
  - Monitor metrics and errors
  - **Acceptance:** Feature live in production, no critical errors
  - **Dependencies:** TASK-602, all testing complete
  - **Estimate:** [time estimate]

## Task Summary

### By Status
- **Not Started:** [count]
- **In Progress:** [count]
- **Complete:** [count]
- **Blocked:** [count]

### By Category
- **Setup:** [count] tasks
- **Backend:** [count] tasks
- **Frontend:** [count] tasks
- **Integration:** [count] tasks
- **Testing:** [count] tasks
- **Documentation:** [count] tasks
- **Deployment:** [count] tasks

## Blocked Tasks

| Task ID | Blocked By | Issue | Action Needed |
|---------|------------|-------|---------------|
| [TASK-XXX] | [blocker] | [description] | [what needs to happen] |

## Notes for LLM Execution

### Context to Provide
When executing tasks, ensure the LLM has access to:
- Feature specification (feature-spec.md)
- Technical design (tech-design.md)
- Current system map (docs/00-context/system-map.md)
- Relevant existing code

### Execution Guidelines
- Complete tasks in dependency order
- Run tests after each task
- Commit after each completed task
- Update this file with status and notes
- Ask questions if requirements are unclear

### Code Standards
- Follow existing code style in repo
- Add comments for complex logic
- Write self-documenting code
- Include error messages that help debugging
- Ensure all tests pass before marking complete

## Related Documents

- Feature Spec: [link to feature-spec.md]
- Tech Design: [link to tech-design.md]
- Test Plan: [link to test-plan.md]

## Change Log

| Date | Changes | Author |
|------|---------|--------|
| YYYY-MM-DD | Initial task breakdown | [Name] |
| YYYY-MM-DD | Tasks X, Y, Z completed | [Name] |
