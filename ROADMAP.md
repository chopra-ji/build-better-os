# Roadmap

This document tracks the phased delivery of Build Better OS. It is a living document — phases and milestones will be updated as priorities evolve.

---

## Current Phase: Foundation

**Goal:** Establish the project structure, architecture, and conventions that everything else will be built on.

**Milestones:**
- [x] Repository initialized with production-grade structure
- [x] Architecture defined and documented
- [x] Contribution and branching conventions established
- [ ] Technology stack decisions recorded as ADRs
- [ ] CI/CD pipeline configured
- [ ] Local development environment documented
- [ ] First service skeleton established

---

## Phase 1 — Platform Core

**Goal:** Build the foundational platform layer that services will run on.

**Scope:**
- Core entity and event abstractions
- Runtime environment (job execution, lifecycle)
- Base integration adapter pattern
- Shared validation and error handling
- Observability foundation (structured logging, event emission)

**Exit criteria:** A service can be built on the platform layer with consistent patterns for events, errors, and external calls.

---

## Phase 2 — Content Service

**Goal:** The first domain service — managing the lifecycle of content.

**Scope:**
- Content entity model (drafts, versions, metadata)
- Content storage and retrieval
- Basic search and filtering
- Event emission for content lifecycle changes
- API surface for content operations

**Exit criteria:** Content can be created, versioned, retrieved, and archived through a stable API.

---

## Phase 3 — Workflow Service

**Goal:** Structure the editorial process as an explicit, auditable workflow.

**Scope:**
- Workflow definition model
- Step execution and state transitions
- Assignment and notification
- Workflow history and audit trail
- Integration with Content service

**Exit criteria:** A content piece can move through a defined editorial workflow with full auditability.

---

## Phase 4 — Publishing Pipeline

**Goal:** Reliable, channel-aware content distribution.

**Scope:**
- Channel adapter pattern
- Scheduling and queuing
- Publish state tracking
- Rollback and recovery
- Initial channel integrations (TBD)

**Exit criteria:** Content can be scheduled and published to at least one channel with reliable delivery guarantees.

---

## Phase 5 — Web Application

**Goal:** The primary interface for the Build Better OS platform.

**Scope:**
- Core navigation and shell
- Content management interface
- Workflow management interface
- Publishing dashboard

**Exit criteria:** A media team can perform their daily operations through the web application.

---

## Future Phases (Planned)

- **Analytics Service** — first-party event collection and reporting
- **Asset Service** — media file management, transformations, delivery
- **Mobile Application** — field access to content and workflow
- **External Integrations** — CMS, social platforms, distribution networks

---

## What is Not on This Roadmap

- Consumer-facing products (this is an internal platform)
- Anything requiring a decision not yet made (see open ADRs in `docs/adr/`)
