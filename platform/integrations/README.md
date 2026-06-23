# platform/integrations/

Adapters for external systems.

## Purpose

Integrations translate between the internal language of Build Better OS and the APIs, protocols, and conventions of external systems. Each integration is an adapter — it wraps a third-party service behind a stable internal interface so that the rest of the platform can interact with it without depending on its specifics.

## Folder Structure

```
integrations/
└── README.md     ← this file
```

Integrations will be added as external systems are connected.

**Expected future structure:**
```
integrations/
├── cms/              ← content management system adapter
├── storage/          ← file and asset storage adapter
├── email/            ← email delivery adapter
└── analytics/        ← external analytics platform adapter
```

## Shared-Only Rule

**An integration belongs here only if it is used by two or more services.**

If only one service needs a particular external system, the adapter for that system lives inside that service — not here. Move it here only when a second service needs it. Premature centralization creates coupling without benefit.

Examples:
- Email adapter used by both the workflow service and the publishing service → belongs here
- CMS adapter used only by the content service → belongs inside `services/content/`

## What Belongs Here

- Adapter implementations for external systems shared across multiple services
- Client configuration and authentication handling for each shared system
- Transformation logic between external data formats and internal types
- Retry, rate-limiting, and circuit-breaker logic for shared integrations

## What Does NOT Belong Here

- Adapters used by only one service (keep those inside that service)
- Generic HTTP or network utilities (those belong in `packages/`)
- Business logic that uses an integration (that belongs in a service)
- Infrastructure provisioning for external systems (that belongs in `infra/`)

## Adapter Pattern

Each integration must expose an interface defined in `platform/core/` and provide an implementation. Services depend on the interface, not the adapter. This enables:
- Testing with mock implementations
- Swapping external providers without changing service code
- Multiple implementations per interface (e.g., different CMS systems)

## Relationships

- Integrations **implement interfaces** defined in `platform/core/`
- Integrations are **injected into** services at runtime
- Integrations are **configured** via environment and `infra/`

## Future Extensions

- Integration health-check registry
- Shared credential management pattern
- Integration test harness for each adapter
