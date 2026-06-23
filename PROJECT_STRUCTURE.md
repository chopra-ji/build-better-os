# Project Structure

Annotated repository tree for Build Better OS. Every directory has a `README.md` with its own detailed documentation.

---

## Full Tree

```
build-better-os/
│
├── .github/                        # GitHub-specific configuration
│   ├── ISSUE_TEMPLATE/             # Issue forms (bug reports, feature requests)
│   ├── PULL_REQUEST_TEMPLATE.md    # Default PR description template
│   └── workflows/                  # GitHub Actions CI/CD pipeline definitions
│
├── apps/                           # Deployable end-user applications
│   └── README.md
│
├── docs/                           # All project documentation
│   ├── adr/                        # Architecture Decision Records
│   ├── architecture/               # System design diagrams and deep-dives
│   ├── guides/                     # How-to guides for developers and operators
│   └── README.md
│
├── infra/                          # Infrastructure as code
│   └── README.md
│
├── packages/                       # Shared internal libraries and utilities
│   └── README.md
│
├── platform/                       # Core OS layer
│   ├── core/                       # Shared abstractions (entities, events, errors)
│   ├── integrations/               # Adapters for external systems
│   ├── runtime/                    # Execution environment and job management
│   └── README.md
│
├── scripts/                        # Developer and build automation scripts
│   └── README.md
│
├── services/                       # Domain-specific backend services
│   └── README.md
│
├── ARCHITECTURE.md                 # System architecture overview
├── CHANGELOG.md                    # Release history
├── CONTRIBUTING.md                 # Contribution guidelines
├── PROJECT_STRUCTURE.md            # This file
├── README.md                       # Project overview and entry point
└── ROADMAP.md                      # Phased delivery plan
```

---

## Directory Ownership

| Directory | Layer | Description |
|---|---|---|
| `apps/` | Application | User-facing, deployable applications |
| `services/` | Service | Domain logic and business rules |
| `platform/` | Platform | Shared OS primitives and integrations |
| `packages/` | Shared | Reusable libraries used across layers |
| `infra/` | Infrastructure | Compute, storage, networking, CI/CD |
| `docs/` | Documentation | All docs that do not belong in code |
| `scripts/` | Tooling | Automation for development and operations |
| `.github/` | Repository | GitHub configuration and workflows |

---

## Dependency Rules

See [ARCHITECTURE.md — Dependency Rules](ARCHITECTURE.md#dependency-rules) for the authoritative dependency direction diagram and rules.

---

## Naming Conventions

See [CONTRIBUTING.md — Naming Conventions](CONTRIBUTING.md#naming-conventions) for the authoritative naming rules.
