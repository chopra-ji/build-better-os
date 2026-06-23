# docs/adr/

Architecture Decision Records.

## Purpose

An ADR documents a significant architectural decision: what was decided, why, what alternatives were considered, and what consequences follow. ADRs are immutable once accepted — they are a historical record, not a living document. If a decision changes, a new ADR supersedes the old one.

## Folder Structure

```
adr/
└── README.md     ← this file
```

ADRs will be added as decisions are made.

**Naming convention:** `NNNN-title-in-kebab-case.md`
Example: `0001-choose-monorepo-structure.md`

## What Belongs Here

- Technology selections (languages, frameworks, databases, queues)
- Structural decisions (monorepo vs. polyrepo, service boundaries)
- Cross-cutting conventions (event format, API style, error handling)
- Security and compliance decisions
- Decisions to reject a technology or approach (these are as valuable as acceptances)

## What Does NOT Belong Here

- Design documents that may change (those belong in `docs/architecture/`)
- Task-level decisions (those belong in PRs and issue comments)
- Decisions that affect only one service (keep those in the service's own docs)

## ADR Format

```markdown
# NNNN: Title

**Status:** Proposed | Accepted | Superseded by [NNNN]
**Date:** YYYY-MM-DD
**Deciders:** [names or roles]

## Context

What situation or problem prompted this decision?

## Decision

What was decided?

## Rationale

Why this option over the alternatives?

## Alternatives Considered

What else was evaluated, and why was it not chosen?

## Consequences

What changes as a result of this decision? What becomes easier or harder?
```

## Status Values

| Status | Meaning |
|---|---|
| `Proposed` | Under discussion, not yet accepted |
| `Accepted` | In effect — this is how we build |
| `Superseded` | Replaced by a later ADR (link to it) |

## When to Write an ADR

Write an ADR when:
- A technology choice is made that future contributors need to understand
- A structural boundary is established
- A team decision would otherwise be re-litigated without a record
- A decision was consciously rejected (to prevent re-proposing it)

When in doubt: if future-you would want to know why, write the ADR.

## Relationships

- ADRs **inform** the design of all directories in this repository
- ADRs are **referenced** in `ARCHITECTURE.md` and relevant READMEs
- ADRs are **linked** from PRs that implement the decided approach
