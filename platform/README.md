# platform/

The core OS layer — shared runtime, abstractions, and external system integrations.

## Purpose

Platform is the "kernel" of Build Better OS. It provides the foundational building blocks that all services are built on: common entity models, event primitives, execution runtime, and adapters for external systems.

Platform code is infrastructure for services — it is not a service itself and does not own business domain logic.

## Folder Structure

```
platform/
├── core/           ← shared abstractions: entities, events, errors, validation
├── integrations/   ← adapters for external systems
├── runtime/        ← execution environment, job management, lifecycle
└── README.md       ← this file
```

## What Belongs Here

- Base entity and value object patterns
- Event primitives and the event emission contract
- Standard error types and error handling patterns
- Shared validation contracts
- The runtime environment that services execute within
- Adapters that translate external APIs into internal interfaces

## What Does NOT Belong Here

- Business logic for any domain (that belongs in `services/`)
- Application-layer code (that belongs in `apps/`)
- Utilities with no architectural concern (those belong in `packages/`)
- Infrastructure provisioning (that belongs in `infra/`)

## Relationships

- Platform **is consumed by** all services in `services/`
- Platform **may use** shared utilities from `packages/`
- Platform **is run on** infrastructure defined in `infra/`
- Platform does **not depend on** apps or services

## Subdirectories

See the README in each subdirectory for detailed documentation:
- [`core/README.md`](core/README.md)
- [`integrations/README.md`](integrations/README.md)
- [`runtime/README.md`](runtime/README.md)

## Future Extensions

- Platform SDK published for internal use
- Developer documentation and examples for platform consumers
- Platform versioning strategy as services mature
