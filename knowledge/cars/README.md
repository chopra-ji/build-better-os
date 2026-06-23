# Cars Knowledge Domain

Automotive knowledge for a media company covering the car world.

---

## Purpose

Cars is a core content vertical for Build Better. This domain serves two purposes: it is the knowledge base for content creators producing automotive content, and it is a reference for maintaining editorial accuracy and depth across car-related coverage.

The test for inclusion: does this entry make Build Better's automotive coverage more accurate, more insightful, or more distinctive than coverage produced without it?

---

## Knowledge Standards

A cars entry earns `status: active` when it:

- Is technically accurate — automotive specifications, engineering principles, and historical facts are verifiable and should be verified
- Distinguishes between marketing claims and verified performance data
- Includes the source for specifications and technical claims (manufacturer, independent testing, regulatory filing)
- Is written at a level of depth that serves the specialist reader without excluding the engaged non-specialist
- Notes where specifications or context change significantly by market or model year

**What good automotive knowledge looks like:** An entry on a vehicle platform documents the engineering architecture, which models share it, the engineering tradeoffs built into that platform, how it compares to competing platforms, and what this means for the ownership experience and long-term reliability. It gives a writer the foundation to say something true and interesting that goes beyond the press release.

---

## Naming Standards

| Entry Type | Convention | Example |
|---|---|---|
| Vehicle review | `<year>-<make>-<model>-review.md` | `2024-porsche-911-review.md` |
| Platform analysis | `<platform>-platform.md` | `meb-platform.md` |
| Technical concept | `<concept>.md` | `torque-vectoring.md` |
| Industry analysis | `<topic>-analysis.md` | `ev-adoption-analysis.md` |
| Comparison | `<car1>-vs-<car2>.md` | `model-s-vs-taycan.md` |
| Brand profile | `<brand>-brand.md` | `porsche-brand.md` |

---

## Cross Referencing

- `technology/` — automotive technology: EV powertrains, ADAS systems, software-defined vehicles
- `business/` — automotive industry economics, OEM business models, dealer networks
- `finance/` — vehicle cost of ownership, depreciation, leasing economics
- `design/` — automotive design language, interior UX, visual identity

---

## Metadata

```yaml
---
title: ""
domain: cars
type: vehicle-review | platform-analysis | technical-concept | industry-analysis | comparison | brand-profile
tags: []
created: ""
updated: ""
status: draft | active | archived
confidence: low | medium | high
tldr: ""
related: []
---
```

**Additional fields for `vehicle-review`:**
```yaml
make: ""
model: ""
year: null
trim: ""
powertrain: ice | hybrid | phev | ev | hydrogen
msrp_usd: null
tested: false         # true = personally tested; false = research-based
```

**Additional fields for `technical-concept`:**
```yaml
technology_type: ""   # powertrain | chassis | safety | software | body
---
```
