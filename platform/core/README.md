# platform/core/

Shared abstractions that form the foundation of the Build Better OS type system.

## Purpose

Core defines the primitive building blocks — entity models, event contracts, error types, and validation patterns — that all services use consistently. By standardizing these at the platform level, every service speaks the same language.

## Folder Structure

```
core/
└── README.md     ← this file
```

Code will be added as the platform layer is built in Phase 1.

**Expected future structure:**
```
core/
├── entities/     ← base entity and value object patterns
├── events/       ← event type definitions and emission contracts
├── errors/       ← standard error types and codes
└── validation/   ← shared schema validation primitives
```

## What Belongs Here

- Base `Entity` and `ValueObject` patterns
- `DomainEvent` base type and event emission interfaces
- Standard error types (`NotFoundError`, `ValidationError`, `UnauthorizedError`, etc.)
- Shared validation schemas and validators
- Common type utilities (IDs, timestamps, pagination cursors)

## What Does NOT Belong Here

- Domain-specific entity types (those belong in their respective service)
- Runtime or execution concerns (those belong in `platform/runtime/`)
- External system adapters (those belong in `platform/integrations/`)
- Business logic of any kind

## Relationships

- Core is **imported by** all services and platform subdirectories
- Core has **no internal dependencies** within the platform — it is the base layer
- Core types appear in **service interfaces and event payloads**

## AI-Native Design

Core types implement the AI-native design principles defined in [ARCHITECTURE.md](../../ARCHITECTURE.md#ai-native-design):
- Entities carry a structured `metadata` field for context
- Events are typed and self-describing — no string-keyed payloads
- Error types carry machine-readable codes alongside human-readable messages
- IDs are typed opaque strings, not raw UUIDs

## Future Extensions

- OpenAPI / JSON Schema generation from core types
- Shared event registry for cross-service event documentation
