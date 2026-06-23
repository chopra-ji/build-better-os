# platform/runtime/

The execution environment for Build Better OS services.

## Purpose

Runtime defines how services start, run, handle jobs, and shut down. It provides the lifecycle management, job scheduling, and operational primitives that services use to run reliably in production.

## Folder Structure

```
runtime/
└── README.md     ← this file
```

Code will be added during Phase 1 (Platform Core).

**Expected future structure:**
```
runtime/
├── lifecycle/    ← service startup, shutdown, health checks
├── jobs/         ← job queue and background task execution
└── context/      ← request context propagation and tracing
```

## What Belongs Here

- Service startup and graceful shutdown patterns
- Background job definition and execution model
- Job queue integration (the adapter pattern for queue providers)
- Request context: trace IDs, correlation IDs, user context propagation
- Health check and readiness probe infrastructure

## What Does NOT Belong Here

- Business logic (that belongs in services)
- Infrastructure provisioning (that belongs in `infra/`)
- External system clients (those belong in `platform/integrations/`)
- Shared utilities with no runtime concern (those belong in `packages/`)

## Relationships

- Runtime is **used by** every service to manage its execution lifecycle
- Runtime **depends on** `platform/core/` for shared types
- Runtime **is configured by** environment variables and `infra/`
- Jobs defined here are **processed on** infrastructure from `infra/`

## AI-Native Design

The runtime implements the explicit context principle from [ARCHITECTURE.md](../../ARCHITECTURE.md#ai-native-design). Every job and operation carries a context object with:
- Trace ID for end-to-end request correlation
- Origin: what triggered this operation (human action, scheduled job, upstream event)
- Actor identity when applicable

This context propagates through every call and appears in every log entry and event, satisfying the auditability requirement.

## Future Extensions

- Distributed tracing integration
- Job retry and dead-letter queue patterns
- Runtime metrics emission
