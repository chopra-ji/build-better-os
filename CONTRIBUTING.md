# Contributing to Build Better OS

Thank you for contributing. This document defines how we work together on this project.

---

## Before You Start

- Read [ARCHITECTURE.md](ARCHITECTURE.md) to understand the system design.
- Read [PROJECT_STRUCTURE.md](PROJECT_STRUCTURE.md) to understand where things live.
- For significant changes, open an issue or discussion before writing code.

---

## Branch Strategy

We use **trunk-based development** with short-lived feature branches.

```
main                  → always deployable, protected
  └── feat/...        → new functionality
  └── fix/...         → bug fixes
  └── chore/...       → maintenance, docs, refactors
  └── infra/...       → infrastructure changes
```

Rules:
- Branch from `main`. Merge back to `main`.
- Branches must be short-lived (days, not weeks).
- Do not commit directly to `main`.
- Delete branches after merging.

---

## Commit Conventions

We use [Conventional Commits](https://www.conventionalcommits.org/).

```
<type>(<scope>): <description>

[optional body]

[optional footer]
```

**Types:**
| Type | When to use |
|---|---|
| `feat` | New capability or feature |
| `fix` | Bug fix |
| `docs` | Documentation only |
| `chore` | Maintenance, dependency updates |
| `refactor` | Code restructuring without behavior change |
| `test` | Adding or updating tests |
| `infra` | Infrastructure changes |
| `perf` | Performance improvement |

**Scope** should be the affected module or domain (e.g., `content`, `workflow`, `platform/core`).

**Examples:**
```
feat(content): add draft versioning to content service
fix(workflow): resolve race condition in approval step
docs(platform): clarify integration adapter interface
chore(deps): update dependencies
```

Commit messages must be in the imperative mood: "add", not "added" or "adds".

---

## Pull Requests

- All changes require a pull request.
- PRs must pass CI before merging.
- At least one approving review is required.
- The PR author merges after approval.

**PR title** must follow the same Conventional Commits format as commit messages.

**PR description** must include:
1. What changed and why
2. How to test it
3. Any migration or deployment notes

Use the PR template (`.github/PULL_REQUEST_TEMPLATE.md`).

---

## Code Review

**As a reviewer:**
- Review within one business day.
- Distinguish blocking issues (`BLOCKING:`) from suggestions (`SUGGESTION:`).
- Approve only when you would be comfortable deploying this change.

**As an author:**
- Respond to all comments before requesting re-review.
- Don't resolve comments yourself — the reviewer resolves.

---

## Documentation

Every folder must have a `README.md`. When you add a new directory, add its README before opening a PR.

Significant architectural decisions must be recorded as ADRs in `docs/adr/`. See the [ADR README](docs/adr/README.md) for format.

---

## Testing

- Every service and package must have tests.
- Tests live alongside the code they test, not in a separate top-level directory.
- CI must pass before merging.

---

## Naming Conventions

| Thing | Convention | Example |
|---|---|---|
| Directories | `kebab-case` | `content-service/`, `editorial-workflow/` |
| Service names | `kebab-case` | `content`, `editorial-workflow` |
| Package names | `@build-better/<name>` | `@build-better/core` |
| App names | `kebab-case` | `web`, `admin` |
| Root documents | `UPPER_CASE.md` | `ARCHITECTURE.md`, `SECURITY.md` |
| All other markdown | `kebab-case.md` or `README.md` | `local-setup.md` |
| Commit types | see table above | `feat`, `fix`, `docs`, etc. |
| Branch names | `<type>/short-description` | `feat/content-versioning` |

---

## Asking for Help

Open a GitHub Discussion or reach out in Slack (`#build-better-os`).
