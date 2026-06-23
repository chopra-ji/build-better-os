# Frameworks Knowledge Domain

Mental models, decision tools, and structured thinking systems.

---

## Purpose

A framework is a structured way of seeing. Good frameworks compress decades of hard-won insight into a form that can be applied in minutes. This domain captures the mental models, decision frameworks, and thinking systems that Build Better uses to analyze problems, make decisions, and communicate clearly.

The test for inclusion: does this framework produce a better answer than unstructured thinking on problems Build Better actually faces? If the answer is "sometimes, depending on the problem" — that is worth documenting. Frameworks are tools, and every tool has a purpose and a limit.

---

## Knowledge Standards

A frameworks entry earns `status: active` when it:

- Explains the framework at the level of mechanism, not just structure — why do these specific components work together?
- Documents where the framework was designed to apply and where it breaks down
- Includes a worked example on a real or highly realistic Build Better problem
- Distinguishes between frameworks that produce insights and frameworks that only organize what you already knew
- States any known critiques of the framework from people who have applied it seriously

**What good frameworks knowledge looks like:** An entry on Jobs to Be Done doesn't list the components — it explains the insight behind the framework (people hire products for the progress they're trying to make, not the features they want), shows the specific interview technique for surfacing the job, demonstrates the output, and explains why the framework produces wrong answers when the "job" is actually multiple competing jobs held simultaneously.

---

## Naming Standards

| Entry Type | Convention | Example |
|---|---|---|
| Framework | `<framework-name>.md` | `jobs-to-be-done.md` |
| Mental model | `<model>.md` | `second-order-thinking.md` |
| Decision tool | `<tool>.md` | `eisenhower-matrix.md` |
| Comparison | `<framework1>-vs-<framework2>.md` | `jtbd-vs-persona.md` |

Use the most common name for the framework, not necessarily the creator's preferred term.

---

## Cross Referencing

Frameworks are the connective tissue of the vault. Every framework entry should link to:
- The domain where it is most commonly applied
- Related frameworks that complement or compete with it
- Books that introduce or best explain it (in `books/`)
- Real examples of its application (if documented elsewhere)

---

## Metadata

```yaml
---
title: ""
domain: frameworks
type: framework | mental-model | decision-tool | comparison
tags: []
created: ""
updated: ""
status: draft | active | archived
confidence: low | medium | high
tldr: ""
related: []
creator: ""
origin_year: null
maturity: emerging | established | foundational
best_for: []      # Specific use cases where this framework excels
---
```

**Maturity guide:**
| Value | Meaning |
|---|---|
| `foundational` | Decades of application, widely validated across domains |
| `established` | 10+ years, validated in specific domains, broadly accepted |
| `emerging` | Less than 10 years old or still being refined through application |
