# Workflows

GitHub Actions CI/CD pipeline definitions for Build Better OS.

## Purpose

This directory contains all automated workflow definitions that run on GitHub Actions. Workflows are triggered by git events (push, pull request, tag) and manage the build, test, and deployment lifecycle.

## Folder Structure

```
workflows/
└── README.md     ← this file
```

Workflow files will be added as pipelines are defined.

## What Belongs Here

- CI workflows: lint, test, build, type-check
- CD workflows: deploy to staging, deploy to production
- Utility workflows: dependency updates, release automation, scheduled jobs

## What Does NOT Belong Here

- Application logic
- Infrastructure definitions (those live in `infra/`)
- Scripts that are run locally by developers (those live in `scripts/`)

## Relationships

- Workflows invoke scripts from `scripts/`
- Workflows deploy artifacts from `apps/` and `services/`
- Workflows run against the infrastructure defined in `infra/`

## Future Extensions

- Workflow for automated CHANGELOG generation on release
- Workflow for dependency vulnerability scanning
- Workflow for ADR validation (ensures new directories have READMEs)
- Environment-specific deployment workflows (staging, production)
