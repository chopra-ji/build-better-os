# docs/

All project documentation that does not live alongside code.

## Purpose

This directory is the home for documentation that spans the entire project — architecture decisions, system design deep-dives, and how-to guides. Code-specific documentation lives in README files alongside the code; cross-cutting documentation lives here.

## Folder Structure

```
docs/
├── adr/              ← Architecture Decision Records
├── architecture/     ← System design documents and diagrams
├── guides/           ← How-to guides for developers and operators
└── README.md         ← this file
```

## What Belongs Here

- Architecture Decision Records (ADRs)
- System design documents
- Data flow and sequence diagrams
- Developer environment setup guides
- Operational runbooks
- Onboarding documentation

## What Does NOT Belong Here

- Code-level documentation (that belongs in README files alongside the code)
- The root project documents (README, ARCHITECTURE, CONTRIBUTING, etc. live at the root)
- Inline API documentation (that belongs in the service's own docs or generated from code)

## Subdirectories

| Directory | Purpose |
|---|---|
| [`adr/`](adr/README.md) | Immutable record of significant architectural decisions |
| [`architecture/`](architecture/README.md) | In-depth design documents |
| [`guides/`](guides/README.md) | Step-by-step guides for common tasks |

## Relationships

- Docs **reference** code in `services/`, `platform/`, and `apps/`
- The root `ARCHITECTURE.md` provides the overview; `docs/architecture/` contains the detail
- ADRs **inform** the structure of `platform/`, `services/`, and `infra/`

## Future Extensions

- Automated documentation generation from service interfaces
- Rendered documentation site (e.g., Docusaurus or similar)
- Runbooks for each service
