# Finance Knowledge Domain

Financial analysis, media economics, and investment thinking.

---

## Purpose

This domain captures Build Better's financial knowledge: how media businesses are valued, how to read and build financial models, the economics of content at scale, investment and fundraising dynamics, and the personal finance knowledge that serves our team and our audience.

Financial literacy is a prerequisite for making good business decisions. Every person who influences Build Better's strategy benefits from knowing how the numbers work.

---

## Knowledge Standards

A finance entry earns `status: active` when it:

- Defines terms precisely — financial vocabulary is notorious for casual misuse (revenue vs. profit vs. margin, valuation vs. price, etc.)
- Is grounded in primary data, a primary source, or direct analysis — not recycled financial commentary
- Distinguishes between accounting definitions and economic reality where they diverge
- States the assumptions in any model or analysis explicitly
- Is specific about the stage and context where the analysis applies (early-stage startup vs. mature business vs. public company)
- Has a direct application to Build Better's financial thinking or content

**What good finance knowledge looks like:** An entry on media company valuation documents the primary valuation multiples used by acquirers and investors in media, why they use those specific metrics, the range of multiples by business model and growth rate, the factors that expand or compress multiples, and how this applies to Build Better's own positioning.

---

## Naming Standards

| Entry Type | Convention | Example |
|---|---|---|
| Financial concept | `<concept>.md` | `ltv-cac-ratio.md` |
| Model | `<model-name>-model.md` | `subscription-unit-economics-model.md` |
| Industry analysis | `<topic>-analysis.md` | `creator-economy-economics.md` |
| Investment concept | `<concept>.md` | `convertible-note.md` |
| Personal finance | `<topic>.md` | `equity-compensation.md` |

---

## Cross Referencing

- `business/` — business model analysis, strategy, and operations
- `startup/` — fundraising mechanics, cap tables, venture economics
- `frameworks/` — decision frameworks for financial choices under uncertainty
- `psychology/` — behavioral finance, cognitive biases in financial decision-making

---

## Metadata

```yaml
---
title: ""
domain: finance
type: concept | model | industry-analysis | investment-concept | personal-finance
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

For `model`:
```yaml
model_type: ""           # unit-economics | valuation | forecasting | scenario
inputs: []               # Key input variables
output: ""               # What the model produces
```

For `industry-analysis`:
```yaml
industry_segment: ""
data_vintage: ""         # YYYY-MM
data_source: ""
```
