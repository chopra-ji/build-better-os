# Business Knowledge Domain

Strategy, operations, and economics for a media company built to last.

---

## Purpose

This domain captures Build Better's understanding of how businesses work, how media companies specifically create and capture value, and how organizations scale without losing what made them good. It includes strategy frameworks, business model analysis, competitive intelligence, and operational patterns.

The question this domain answers: how do you build and run a company that compounds over time rather than burning bright and collapsing?

---

## Knowledge Standards

A business entry earns `status: active` when it:

- Is grounded in a primary source (original research, first-person case study, primary data) rather than a recycled opinion
- Makes a falsifiable claim — "this works" must specify the conditions under which it works
- Is relevant to a media company operating at Build Better's stage and scale
- Distinguishes between what worked in a specific context and what is generalizable
- Includes the mechanism: not just that something works, but why it works
- Has at least one direct implication for how Build Better operates

**What good business knowledge looks like:** A business model analysis documents the unit economics, the value chain, the defensibility mechanism, the conditions under which the model scales, and where it breaks. It tells you how to evaluate whether a similar model could work for Build Better, not just whether it worked elsewhere.

---

## Naming Standards

| Entry Type | Convention | Example |
|---|---|---|
| Business model | `<model-name>-model.md` | `subscription-model.md` |
| Case study | `<company>-case-study.md` | `stratechery-case-study.md` |
| Framework | `<framework-name>.md` | `value-chain-analysis.md` |
| Concept | `<concept>.md` | `unit-economics.md` |
| Industry analysis | `<topic>-analysis.md` | `media-bundling-analysis.md` |

---

## Cross Referencing

- `marketing/` — how business strategy translates to audience acquisition and retention
- `finance/` — financial models and metrics that underpin business analysis
- `startup/` — early-stage specific business strategy and operations
- `frameworks/` — strategic thinking frameworks (Porter's Five Forces, Blue Ocean, etc.)
- `psychology/` — behavioral economics, decision-making under uncertainty

---

## Metadata

```yaml
---
title: ""
domain: business
type: business-model | case-study | framework | concept | industry-analysis
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

For `case-study`:
```yaml
company: ""
industry: ""
time_period: ""       # e.g., "2018–2023"
outcome: success | failure | mixed
key_metric: ""        # The metric that tells the story
```

For `industry-analysis`:
```yaml
industry: ""
scope: ""             # What question this analysis answers
data_vintage: ""      # YYYY or YYYY-MM — when the data is from
```
