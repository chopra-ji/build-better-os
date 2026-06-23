# Build Better OS — AI Context

This file gives AI coding assistants structured context about this repository. Read it before making any changes.

## What This Project Is

Build Better OS is an internal platform for a media company. It is a monorepo. It is not a consumer product. It handles content creation, editorial workflow, publishing pipelines, and media asset management.

The "OS" means: a platform layer that other tools and workflows are built on, not a single application.

## Repository Map

```
apps/          → end-user applications (thin, no business logic)
services/      → domain services (own their data and rules)
platform/      → shared OS primitives (core, integrations, runtime)
packages/      → shared utilities (no domain knowledge)
knowledge/     → institutional knowledge vault (17 domains)
infra/         → infrastructure as code
docs/          → cross-cutting documentation
scripts/       → developer automation
.github/       → GitHub configuration and CI/CD
```

## Dependency Rule

Code dependencies flow one direction only:

```
apps → services → platform → packages
```

- Nothing imports from `apps/`
- `services/` never imports from `apps/`
- `platform/` never imports from `services/`
- `packages/` imports from nothing in this repo
- `infra/` is a deployment concern, not a code dependency

**Violating this rule requires an ADR.**

## Where Things Belong

| Thing | Where |
|---|---|
| Business logic | `services/<domain>/` |
| Shared abstractions (Entity, Event, Error base types) | `platform/core/` |
| External system adapters used by multiple services | `platform/integrations/` |
| External system adapters used by one service only | inside that service |
| Job execution, lifecycle, context propagation | `platform/runtime/` |
| Shared utility (used by 2+ modules) | `packages/<name>/` |
| Shared utility (used by 1 module) | keep it local, do not extract |
| Infrastructure provisioning | `infra/` |
| Deployable application | `apps/<name>/` |
| CI/CD pipeline definition | `.github/workflows/` |

## Naming Conventions

- Directories: `kebab-case`
- Internal packages: `@build-better/<name>`
- Commits: Conventional Commits (`feat`, `fix`, `docs`, `chore`, `refactor`, `test`, `infra`, `perf`)
- Branches: `feat/...`, `fix/...`, `chore/...`, `infra/...`
- Root documentation: `UPPER_CASE.md`
- All other docs and READMEs: `kebab-case.md` or `README.md`

## Key Constraints

1. Every directory must have a `README.md`. Do not create a directory without one.
2. Significant decisions must be recorded as ADRs in `docs/adr/`. See the format there.
3. Services own their data. No service reads another service's database.
4. Services communicate through events (async) or APIs (sync). Never direct database access.
5. Do not add a package to `packages/` for code used in only one place. Extract only when genuinely shared.
6. All PRs require at least one review. CI must pass.

## AI-Native Design Principles

This system is designed to be observable and callable by AI:

- **Typed contracts at every boundary.** No stringly-typed interfaces. No freeform JSON payloads.
- **Self-describing events.** Events carry their full context — type, origin, actor, timestamp, payload — without requiring external lookup.
- **Explicit operation context.** Every operation carries: trace ID, actor identity, and trigger (human action vs. scheduled job vs. event).
- **Structured errors.** Errors have machine-readable codes and structured metadata, not just messages.
- **Auditable mutations.** Every state change is logged with its full context.

## Knowledge Vault

The vault is at `knowledge/`. It is not code — it is structured markdown content.

**17 domains:** ai, technology, business, marketing, psychology, storytelling, editing, design, fitness, finance, cars, travel, startup, productivity, books, frameworks, quotes

**Every entry requires YAML frontmatter.** The schema is defined in `knowledge/_templates/`. Domain-specific fields are in each domain's `Templates/` folder.

**Entry lifecycle:** `draft` → `active` → `archived`. Never delete. Archive instead.

**Key rules:**
- `status: active` requires a completed `tldr` field — one sentence, no exceptions
- `confidence` must reflect actual verification depth, not wishful thinking
- Every active entry must have at least one `related` link
- Travel entries expire after 24 months without re-verification
- AI entries should be reviewed every 6 months

**Do not create knowledge entries without YAML frontmatter.** Do not create placeholder entries with empty fields and lorem ipsum.

## Technology Stack

Not yet decided. Decisions will be recorded as ADRs in `docs/adr/`. Do not assume a specific language or framework until an ADR says otherwise.

## Documentation Index

- `ARCHITECTURE.md` — system design and layer overview
- `CONTRIBUTING.md` — how to contribute, branch and commit conventions
- `ROADMAP.md` — phased delivery plan
- `PROJECT_STRUCTURE.md` — annotated repo tree
- `docs/adr/` — architecture decision records
- `docs/architecture/` — in-depth design documents
- `docs/guides/` — step-by-step how-to guides
