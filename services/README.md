# services/

Domain-specific backend services.

## Purpose

Each subdirectory is a bounded domain service that owns its data, enforces its business rules, and exposes a well-defined interface. Services are the primary location for business logic in Build Better OS.

## Folder Structure

```
services/
└── README.md     ← this file
```

Services will be added as they are defined.

**Expected future structure:**
```
services/
├── content/          ← content lifecycle management
├── workflow/         ← editorial workflow engine
├── publishing/       ← channel distribution and scheduling
├── analytics/        ← event collection and reporting
└── assets/           ← media file management
```

## What Belongs Here

- Business logic for a named domain
- Data access and persistence for that domain
- Domain events emitted by that service
- API or interface exposed by that service
- Tests for that service's behavior

## What Does NOT Belong Here

- Shared utilities (those belong in `packages/`)
- Platform primitives (those belong in `platform/`)
- Application-layer orchestration (that belongs in `apps/`)
- Cross-service workflows (those are modeled by the workflow service or as platform-level orchestrations)

## Service Boundaries

Each service must:
1. Own its own data store. No service reads another service's database directly.
2. Communicate with other services through defined interfaces (events or APIs).
3. Have a `README.md` describing its domain, interface, and events.

## Relationships

- Services **build on** platform primitives from `platform/`
- Services **import** shared utilities from `packages/`
- Services are **consumed by** apps in `apps/`
- Services are **deployed** via `infra/`

## Future Extensions

- Each service will have its own deployment configuration
- Services may expose gRPC, REST, or event-based interfaces depending on their nature
- Service-to-service communication patterns will be standardized in `platform/core/`
