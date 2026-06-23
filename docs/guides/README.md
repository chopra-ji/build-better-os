# docs/guides/

Step-by-step guides for developers and operators.

## Purpose

Guides are actionable, task-oriented documents: how to set up a local development environment, how to add a new service, how to deploy a release, how to debug a common issue. Guides are for people who need to accomplish something — not for understanding the system.

## Folder Structure

```
guides/
└── README.md     ← this file
```

Guides will be written as development workflows are established.

**Expected future guides:**
```
guides/
├── local-setup.md            ← set up a development environment from scratch
├── adding-a-service.md       ← step-by-step for creating a new domain service
├── writing-an-adr.md         ← how to write and submit an ADR
├── deployment.md             ← how to deploy to staging and production
└── debugging.md              ← common issues and how to diagnose them
```

## What Belongs Here

- Local development environment setup
- Instructions for common development tasks
- Deployment procedures and checklists
- Debugging and troubleshooting guides
- Onboarding guides for new contributors

## What Does NOT Belong Here

- Architecture and design documentation (those belong in `docs/architecture/`)
- Decision records (those belong in `docs/adr/`)
- Reference documentation for APIs or libraries (keep that near the code)

## Guide Format

A good guide:
1. States its goal in one sentence at the top ("After completing this guide, you will have...")
2. Lists prerequisites before the first step
3. Uses numbered steps for procedures
4. Notes where the reader should verify before continuing
5. Ends with a "what to do if this didn't work" section

## Relationships

- Guides **reference** infrastructure from `infra/`
- Guides **reference** scripts from `scripts/`
- Guides **complement** the structural documentation in `docs/architecture/` and `docs/adr/`

## Future Extensions

- Video walkthroughs for complex guides
- Automated local environment setup script (`scripts/setup.sh`)
