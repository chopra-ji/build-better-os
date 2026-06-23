# 0001: Monorepo Structure

**Status:** Accepted
**Date:** 2026-06-23
**Deciders:** Engineering Lead

---

## Context

Build Better OS is a new platform that will eventually consist of multiple services, shared libraries, deployable applications, and infrastructure definitions. We need to decide whether to organize this as a single repository (monorepo) or as separate repositories per component (polyrepo).

At this stage, the team is small, the service boundaries are not fully established, and the technology stack has not been finalized. Cross-component changes will be frequent during the foundational phase.

---

## Decision

We will use a **monorepo**. All code that ships as part of Build Better OS lives in this repository.

The repository is organized into top-level directories by concern:
- `apps/` — deployable applications
- `services/` — domain services
- `platform/` — shared OS primitives
- `packages/` — shared libraries
- `infra/` — infrastructure as code

---

## Rationale

**For monorepo:**
- Cross-service changes land in a single atomic commit. No multi-repo PR coordination during early development.
- Shared packages can be imported directly without versioning overhead.
- Unified CI/CD and tooling. One place to configure linting, testing, and deployment.
- Easier to enforce dependency direction rules (apps → services → platform → packages).
- Full context for AI coding assistants — the whole system is visible in one checkout.

**Against polyrepo that we chose not to adopt:**
- Independent deployment velocity is not a current constraint — we have no services yet.
- Separate repo access control is not required at this stage.
- The overhead of cross-repo changes (coordinating PRs, version bumps) is high at our scale.

---

## Alternatives Considered

**Polyrepo (one repo per service)**
Rejected. Too much coordination overhead for a small team building foundational infrastructure. Each cross-cutting change (adding a shared event type, updating a shared dependency) would require multiple PRs across repositories. We can revisit this if individual services need independent release cadences or access control.

**Hybrid (platform as a separate repo, services monorepo)**
Rejected. Adds cross-repo dependency between platform and services without significant benefit at this stage. Service boundaries are still forming and forcing a hard split too early would require disruptive migrations.

---

## Consequences

**Easier:**
- Atomic refactors across service boundaries
- Shared tooling configuration
- Onboarding: one repo to clone

**Harder:**
- Individual services cannot have independent CI pipelines without additional tooling (e.g., Turborepo, Nx, or path-filtered GitHub Actions)
- Repository size will grow over time — requires disciplined boundary enforcement
- Access control is repo-wide, not per-service

**Follow-on decisions required:**
- Monorepo tooling selection (Turborepo, Nx, none) — to be recorded as ADR 0002
- Package versioning strategy for `packages/` — to be recorded when first package is created
