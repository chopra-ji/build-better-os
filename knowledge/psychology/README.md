# Psychology Knowledge Domain

Human behavior, cognition, and motivation as they apply to media and business.

---

## Purpose

This domain captures Build Better's working knowledge of psychology — how people think, decide, feel, and behave. For a media company, this is not a soft consideration. It is the operating system beneath everything we make. Every piece of content we create makes an implicit model of how the audience will perceive and respond to it. This domain makes that model explicit.

The focus is applied psychology: principles with direct implications for how we create content, build products, lead teams, and make decisions.

---

## Knowledge Standards

A psychology entry earns `status: active` when it:

- Is grounded in peer-reviewed research, a credible meta-analysis, or a primary source — not a pop-science summary
- States the replication status of findings where known (the replication crisis is real; acknowledge it)
- Distinguishes between a robust finding and a contested one
- Provides the mechanism: not just that people behave a certain way, but why they do
- Has at least one direct application to Build Better's content, product, or operations
- Notes the context in which the finding holds and where it breaks down

**What good psychology knowledge looks like:** An entry on loss aversion documents the original Kahneman/Tversky experiments, the effect size, the known moderators (the effect is stronger in some domains than others), the contested aspects, and three specific ways this shows up in content engagement and editorial decisions at Build Better.

---

## Naming Standards

| Entry Type | Convention | Example |
|---|---|---|
| Cognitive bias | `<bias-name>.md` | `loss-aversion.md` |
| Psychological concept | `<concept>.md` | `intrinsic-motivation.md` |
| Research synthesis | `<topic>-research.md` | `persuasion-research.md` |
| Framework | `<framework>.md` | `self-determination-theory.md` |
| Personality model | `<model>.md` | `big-five-personality.md` |

---

## Cross Referencing

- `marketing/` — behavioral science applied to audience acquisition and content strategy
- `storytelling/` — emotional engagement, narrative transportation, character identification
- `frameworks/` — decision-making frameworks that account for cognitive limitations
- `business/` — behavioral economics, pricing psychology, negotiation
- `editing/` — how reader cognitive load affects editorial decisions

---

## Metadata

```yaml
---
title: ""
domain: psychology
type: concept | bias | research-synthesis | framework | model
tags: []
created: ""
updated: ""
status: draft | active | archived
confidence: low | medium | high
tldr: ""
related: []
origin: ""
field: ""          # cognitive psychology | social psychology | behavioral economics | etc.
---
```

**Additional fields for research-based entries:**
```yaml
primary_researcher: ""   # Who produced the foundational research
replication_status: ""   # replicated | contested | failed-replication | unknown
effect_size: ""          # small | medium | large | varies
```
