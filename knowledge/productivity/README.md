# Productivity Knowledge Domain

Systems, workflows, and practices that multiply output without degrading quality.

---

## Purpose

Build Better is a small team with large ambitions. The leverage we generate through systems and workflows is the difference between being overwhelmed and being formidable. This domain captures what we know about working effectively: time management, attention management, tool selection, process design, and the habits that compound over time.

This is not a self-help section. Every entry must justify its inclusion with a specific, transferable practice — not a motivational observation.

---

## Knowledge Standards

A productivity entry earns `status: active` when it:

- Describes a specific, implementable practice — not a general principle
- Specifies the conditions under which it works (type of work, team size, role, cognitive load)
- Includes the failure mode: what happens when you misapply it or use it past its useful context
- Has been validated by at least one person on the team, or by a credible source describing specific results
- Distinguishes between productivity techniques that optimize for output volume and those that optimize for output quality — Build Better cares about both but in different proportions for different work

**What good productivity knowledge looks like:** An entry on weekly reviews documents the specific questions the review answers, the time commitment, the inputs required (calendar, task system, journal), the output format, the failure modes (what causes the habit to break down), and how to adapt it for a week where normal rhythms were disrupted.

---

## Naming Standards

| Entry Type | Convention | Example |
|---|---|---|
| System | `<system>.md` | `weekly-review.md` |
| Technique | `<technique>.md` | `time-blocking.md` |
| Tool review | `<tool>-review.md` | `linear-review.md` |
| Concept | `<concept>.md` | `attention-residue.md` |
| Workflow | `<workflow>.md` | `content-production-workflow.md` |

---

## Cross Referencing

- `psychology/` — cognitive science behind attention, habit formation, willpower depletion, decision fatigue
- `technology/` — tools and software for workflow implementation
- `ai/` — AI tools that augment specific workflows
- `fitness/` — physical practices (sleep, exercise, nutrition) that underpin cognitive performance
- `frameworks/` — decision frameworks that reduce cognitive load

---

## Metadata

```yaml
---
title: ""
domain: productivity
type: system | technique | tool-review | concept | workflow
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

For `system` and `technique`:
```yaml
time_investment: ""    # e.g., "15 min/day" or "2 hr/week"
setup_time: ""         # One-time setup investment
works_best_for: []     # Role types or work types
requires: []           # Tools or preconditions needed
```

For `tool-review`:
```yaml
url: ""
price_model: free | freemium | paid | subscription
platform: []           # web | mac | ios | android | windows | cli
verdict: adopt | evaluate | avoid | watch
```
