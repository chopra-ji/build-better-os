# Build Better OS

> The AI-native operating system for Build Better Media Company.

Build Better OS is the foundational platform that powers how Build Better creates, manages, and distributes content. It is designed from first principles as an AI-native system — meaning AI is not a feature layered on top, but a structural property of how the platform operates.

---

## What is Build Better OS?

Build Better OS is an internal platform that unifies the tools, workflows, and services a modern media company needs to operate at scale:

- **Content operations** — from ideation to publication across channels
- **Editorial workflows** — structured, auditable, and automatable processes
- **Asset management** — a single source of truth for all media assets
- **Publishing pipelines** — reliable distribution to any channel
- **Analytics and signals** — first-party data that informs every decision

The "OS" metaphor is intentional. Like an operating system, Build Better OS provides a platform that higher-level applications and workflows are built on — not a single application itself.

---

## Repository Structure

```
build-better-os/
├── apps/          → Deployable end-user applications
├── docs/          → All project documentation
├── infra/         → Infrastructure as code
├── packages/      → Shared internal libraries
├── platform/      → Core OS layer (runtime, integrations, abstractions)
├── scripts/       → Developer and build automation scripts
└── services/      → Domain-specific backend services
```

See [PROJECT_STRUCTURE.md](PROJECT_STRUCTURE.md) for the full annotated tree.

---

## Key Documents

| Document | Purpose |
|---|---|
| [ARCHITECTURE.md](ARCHITECTURE.md) | System design, principles, and component overview |
| [ROADMAP.md](ROADMAP.md) | Phased delivery plan |
| [CONTRIBUTING.md](CONTRIBUTING.md) | How to contribute to this project |
| [CHANGELOG.md](CHANGELOG.md) | Release history |
| [PROJECT_STRUCTURE.md](PROJECT_STRUCTURE.md) | Annotated repository tree |

---

## Design Principles

1. **AI-native by default.** Every layer of the system is designed to be observed, called, and reasoned about by AI. Structured data over prose. Explicit contracts over implicit conventions.

2. **Workflows over ad-hoc tools.** Operations are repeatable, composable, and auditable. If a human does something more than once, it belongs in a workflow.

3. **Single source of truth.** Assets, metadata, and state live in one place. Everything else is a projection or a cache.

4. **Observable by design.** Every service emits structured events. Every action has a trail.

5. **Modular and bounded.** Services own their domain. Dependencies are explicit. Boundaries are enforced.

---

## Status

This project is in active initialization. See [ROADMAP.md](ROADMAP.md) for current phase and upcoming milestones.
