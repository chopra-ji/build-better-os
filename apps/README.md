# apps/

Deployable, end-user-facing applications.

## Purpose

Each subdirectory is a self-contained deployable application — a web interface, API gateway, background worker, or other runtime artifact that is shipped and run. Apps are thin layers that compose services and present them to users or external systems.

## Folder Structure

```
apps/
└── README.md     ← this file
```

Applications will be added as they are initialized.

**Expected future structure:**
```
apps/
├── web/          ← primary web application
├── api/          ← public API gateway (if separated from individual services)
└── worker/       ← background job processor
```

## What Belongs Here

- Web frontends (React, Next.js, etc.)
- API gateways and BFF (backend-for-frontend) layers
- Background workers and job processors
- CLI tools intended for end users
- Any deployable artifact that is not a domain service

## What Does NOT Belong Here

- Business logic (that belongs in `services/`)
- Shared libraries (that belongs in `packages/`)
- Platform primitives (that belongs in `platform/`)
- Infrastructure definitions (that belongs in `infra/`)

## Relationships

- Apps **consume** services from `services/`
- Apps **import** shared utilities from `packages/`
- Apps are **deployed** using infrastructure defined in `infra/`
- Apps are **built and tested** by workflows in `.github/workflows/`

## Naming Conventions

Each app directory uses `kebab-case`. The directory name is the canonical name of the application.

## Future Extensions

- Mobile application (`apps/mobile/`)
- Admin application (`apps/admin/`)
- Embeddable widgets (`apps/embed/`)
