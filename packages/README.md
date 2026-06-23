# packages/

Shared internal libraries used across services and applications.

## Purpose

Code that is genuinely reusable across multiple services or apps lives here as named packages. Packages have no knowledge of business domains — they provide utilities, clients, and abstractions that any layer can depend on.

## Folder Structure

```
packages/
└── README.md     ← this file
```

Packages will be extracted here as shared patterns emerge from services.

**Expected future structure:**
```
packages/
├── logger/           ← structured logging utility
├── http-client/      ← shared HTTP client with retry and tracing
├── validation/       ← shared schema validation
└── test-utils/       ← shared test helpers
```

## What Belongs Here

- Utilities with no business domain knowledge
- Shared clients (HTTP, database, queue)
- Shared type definitions used across multiple services
- Test helpers and fixtures
- Configuration readers

## What Does NOT Belong Here

- Business logic (that belongs in `services/`)
- Platform abstractions (those belong in `platform/core/`)
- Application components (those belong in `apps/`)
- Code that is only used by one service or app (keep it local until it is genuinely needed in two places)

## Naming Conventions

- Packages are scoped under `@build-better/<name>`
- Directory names use `kebab-case`
- Example: `packages/logger/` → published as `@build-better/logger`

## Relationships

- Packages are **consumed by** services, apps, and platform code
- Packages have **no internal dependencies** within this repo — they are leaf nodes in the dependency graph
- Packages are **independently versioned**

## Extraction Rule

Do not create a package preemptively. Extract code into `packages/` only when it is already used (or immediately needed) by two or more distinct modules. Premature abstraction creates coordination overhead without value.

## Future Extensions

- Package versioning and publishing workflow
- Shared design tokens or UI primitives (if a design system is adopted)
