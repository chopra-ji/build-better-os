# Technology Knowledge Domain

The technical infrastructure and tools that power Build Better's operations.

---

## Purpose

This domain documents Build Better's working knowledge of software systems, platforms, infrastructure patterns, and technical tools. It covers both the technology we build on and the technology we evaluate for adoption.

The test for inclusion: does this knowledge help Build Better build, maintain, or scale its systems more effectively? A concept or tool that has no path to application at Build Better belongs in someone's personal notes, not the vault.

---

## Knowledge Standards

A technology entry earns `status: active` when it:

- Documents behavior from direct experience, not documentation alone
- Distinguishes between how a technology is marketed and how it actually behaves under our conditions
- Includes a concrete use case or implementation pattern, not just a description
- Notes version specificity where behavior varies significantly across versions
- Addresses failure modes — every technology has conditions under which it breaks or disappoints
- Has a clear recommendation: adopt, evaluate, avoid, or watch

**What good technology knowledge looks like:** A platform evaluation entry documents the specific workload tested, the performance characteristics observed, the operational overhead required, the cost model at scale, the failure modes encountered, and a verdict with rationale. It gives an engineer enough information to make a decision without having to re-run the evaluation.

---

## Naming Standards

| Entry Type | Convention | Example |
|---|---|---|
| Platform evaluation | `<platform>-evaluation.md` | `vercel-evaluation.md` |
| Tool review | `<tool>-review.md` | `turbo-review.md` |
| Architecture pattern | `<pattern-name>.md` | `event-driven-architecture.md` |
| Concept | `<concept>.md` | `eventual-consistency.md` |
| Integration guide | `<service>-integration.md` | `stripe-integration.md` |

---

## Cross Referencing

- `ai/` — AI-specific tools and platforms used in engineering workflows
- `platform/` — decisions about technology adoption are often recorded as ADRs in `docs/adr/`
- `productivity/` — developer tooling and workflow optimization
- `frameworks/` — architectural decision frameworks

**Note:** When a technology evaluation leads to a formal adoption decision, create an ADR in `docs/adr/` and link to this entry. The knowledge entry is the research; the ADR is the decision.

---

## Metadata

**Required frontmatter for all technology entries:**

```yaml
---
title: ""
domain: technology
type: platform-evaluation | tool-review | architecture-pattern | concept | integration-guide
tags: []
created: ""
updated: ""
status: draft | active | archived
confidence: low | medium | high
tldr: ""
related: []
---
```

**Additional fields by type:**

For `platform-evaluation` and `tool-review`:
```yaml
vendor: ""
version_tested: ""
price_model: free | freemium | paid | enterprise
evaluated_date: ""   # YYYY-MM-DD
verdict: adopt | evaluate | avoid | watch
```

For `architecture-pattern`:
```yaml
origin: ""           # Who popularized or defined this pattern
maturity: emerging | established | foundational
```
