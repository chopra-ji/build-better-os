# scripts/

Developer and build automation scripts.

## Purpose

Executable scripts that automate repetitive development, build, and operational tasks. These scripts are for humans (and CI) to run directly — they are not application code and they do not contain business logic.

## Folder Structure

```
scripts/
└── README.md     ← this file
```

Scripts will be added as development workflows are established.

**Expected future structure:**
```
scripts/
├── setup.sh          ← bootstrap local development environment
├── dev.sh            ← start all services in development mode
├── build.sh          ← build all apps and services
└── seed.sh           ← seed local database with development data
```

## What Belongs Here

- Environment setup scripts (install dependencies, configure local env)
- Development server start scripts
- Database migration and seeding scripts for local development
- Build and bundle scripts
- Release automation scripts (changelog generation, version bumping)
- Utility scripts run by CI workflows

## What Does NOT Belong Here

- Application code
- Infrastructure provisioning scripts (those belong in `infra/`)
- GitHub Actions workflow definitions (those belong in `.github/workflows/`)
- Scripts that are part of a service's own operational tooling (keep those in the service directory)

## Conventions

- Scripts must be executable (`chmod +x`)
- Scripts must have a usage comment at the top
- Scripts must fail fast (`set -euo pipefail` for bash scripts)
- Script names use `kebab-case`
- Prefer idempotent scripts — running a setup script twice should be safe

## Relationships

- Scripts are **called by** `.github/workflows/` during CI/CD
- Scripts **operate on** the services and apps in this repository
- Scripts may **interact with** infrastructure defined in `infra/`

## Future Extensions

- Script for generating a new service from a template
- Script for validating that all directories have READMEs
- Script for checking that ADRs are current
