# Architecture

This document describes the system architecture of Build Better OS — its structure, principles, and how components relate to each other.

---

## System Overview

Build Better OS is a platform organized into four conceptual layers:

```
┌─────────────────────────────────────────────────────┐
│                      APPS                           │
│          (Web interfaces, API surfaces)             │
├─────────────────────────────────────────────────────┤
│                    SERVICES                         │
│  (Content · Workflow · Publishing · Analytics)      │
├─────────────────────────────────────────────────────┤
│                    PLATFORM                         │
│       (Runtime · Integrations · Core SDK)           │
├─────────────────────────────────────────────────────┤
│                  INFRASTRUCTURE                     │
│       (Compute · Storage · Networking · CI/CD)      │
└─────────────────────────────────────────────────────┘
```

**Code dependencies** flow upward-to-downward only. Infrastructure is not a code dependency — it is a deployment substrate. See [Dependency Rules](#dependency-rules) below.

---

## Layers

### Apps
Deployable, user-facing applications. Each app is a thin shell that composes services to deliver a workflow or interface. Apps do not contain business logic.

### Services
Domain-bounded backend services. Each service owns its data and exposes a well-defined interface. Services communicate asynchronously through events where possible, synchronously through APIs where necessary.

Core service domains:
- **Content** — the lifecycle of a content piece from draft to archive
- **Workflow** — editorial process, approvals, assignments
- **Publishing** — channel-specific distribution and scheduling
- **Analytics** — event collection, aggregation, and reporting
- **Assets** — media files, metadata, transformations

### Platform
The shared runtime and integration layer that services are built on. This is the "kernel" of Build Better OS:

- **Core** — shared abstractions: events, entities, errors, validation
- **Runtime** — execution environment, job scheduling, lifecycle management
- **Integrations** — adapters for external systems shared across two or more services

### Infrastructure
Compute, storage, networking, and CI/CD configuration. Managed as code in `infra/`. This is a deployment concern, not a code dependency.

---

## Dependency Rules

Code imports flow in one direction:

```
apps/ → services/ → platform/ → packages/
```

- `apps/` may import from `services/` and `packages/`
- `services/` may import from `platform/` and `packages/`
- `platform/` may import from `packages/`
- `packages/` has no internal imports
- Nothing imports from `apps/`
- Nothing imports from `infra/` — infrastructure is provisioned, not imported

Violating these rules requires an ADR explaining why.

---

## AI-Native Design

Build Better OS treats AI participation as a first-class architectural concern, not an optional integration. The following principles apply at every layer:

**Typed contracts at every boundary.**
All service interfaces use typed schemas. No freeform JSON payloads, no string-keyed maps, no untyped blobs at service boundaries. Contracts are machine-readable.

**Self-describing events.**
Every significant state change emits a structured event carrying: event type, timestamp, actor identity, trigger origin (human action / scheduled job / upstream event), and typed payload. An AI can understand any event without external documentation.

**Explicit operation context.**
Every operation — HTTP request, background job, event handler — carries a context object with trace ID, actor, and origin. This context propagates through every call and appears in every log entry and event.

**Structured errors.**
Errors carry machine-readable codes and typed metadata alongside human-readable messages. An AI can classify and act on errors without parsing strings.

**Auditable mutations.**
Every state-changing operation is logged with its full context: who triggered it, what the inputs were, what changed, and what the result was. Nothing changes silently.

These principles are the definition of "AI-native" for this system. All other "AI-native" references in this repo point here.

---

## Data Flow

```
External Signal
      │
      ▼
   [App / API]
      │  carries: trace ID, actor, typed request
      ▼
  [Service]  ──── emits typed event ────▶  [Event Stream]
      │             (type, actor, payload)        │
      ▼                                           ▼
 [Platform Core]                          [Other Services]
      │  (shared entity/event types)
      ▼
 [Storage / Integration Adapter]
```

Event contracts are defined in `platform/core/`. All services use these types when emitting events.

---

## Monorepo Strategy

This repository is a monorepo. All code that ships as part of Build Better OS lives here. The decision is recorded in [ADR 0001](docs/adr/0001-monorepo-structure.md).

**Boundaries within the monorepo:**
- `apps/`, `services/`, and `packages/` are independently deployable units
- Each has its own build configuration and dependency manifest
- Shared code lives in `packages/` and is explicitly imported — never by relative path across package boundaries

---

## Architecture Decision Records

All significant architectural decisions are recorded as ADRs in [`docs/adr/`](docs/adr/README.md).

An ADR is created when:
- A technology is adopted or replaced
- A structural boundary is established or changed
- A cross-cutting pattern is standardized
- A decision is consciously rejected (to prevent re-proposing it)

---

## Detailed Design Documents

The root `ARCHITECTURE.md` (this file) is the system map. For in-depth documentation of specific subsystems, see [`docs/architecture/`](docs/architecture/README.md).

**Rule:** if a design decision or explanation requires more than one page, it belongs in `docs/architecture/`, not here.

---

## Technology Decisions

Technology choices have not yet been finalized. Decisions will be recorded in ADRs as they are made. The architecture above is intentionally technology-agnostic at this stage.

See [ROADMAP.md](ROADMAP.md) for when these decisions are expected.
