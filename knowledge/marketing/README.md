# Marketing Knowledge Domain

Audience growth, distribution strategy, and brand building for media.

---

## Purpose

This domain captures what Build Better knows about reaching, growing, and retaining an audience. For a media company, marketing is not adjacent to the product — it is inseparable from it. How you distribute is part of what you make.

This includes: platform-specific distribution tactics, audience psychology, content strategy frameworks, brand building, SEO, paid acquisition, email, social, and the analytics that tell you what is working.

---

## Knowledge Standards

A marketing entry earns `status: active` when it:

- Is based on tested results, not received wisdom — "best practices" that have not been verified against our audience are hypotheses, not knowledge
- Specifies the context in which results were observed (platform, audience size, content type, time period)
- Includes at least one concrete metric or measurable outcome
- Separates tactics that are platform-specific from principles that are durable
- Has a clear shelf life label for anything highly platform-dependent (platforms change; tactics expire)

**What good marketing knowledge looks like:** A distribution analysis documents what was tested, over what time period, on what audience, with what metrics, and what the result was. It separates the tactic from the insight — tactics expire, but the underlying insight about human behavior or platform mechanics often persists in a different form.

---

## Naming Standards

| Entry Type | Convention | Example |
|---|---|---|
| Platform analysis | `<platform>-distribution.md` | `youtube-distribution.md` |
| Campaign analysis | `<campaign-type>-analysis.md` | `newsletter-launch-analysis.md` |
| Concept | `<concept>.md` | `content-moat.md` |
| Audience strategy | `<topic>-strategy.md` | `email-growth-strategy.md` |
| Framework | `<framework>.md` | `hook-retain-reward.md` |

---

## Cross Referencing

- `psychology/` — the behavioral science behind marketing decisions
- `storytelling/` — narrative techniques applied to content marketing
- `business/` — how marketing connects to business model and revenue
- `design/` — visual identity, creative direction, brand standards
- `analytics/` in `services/` — how marketing performance is measured at the system level

---

## Metadata

```yaml
---
title: ""
domain: marketing
type: platform-analysis | campaign-analysis | concept | strategy | framework
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

For `platform-analysis`:
```yaml
platform: ""
audience_size: ""       # Approximate audience size when tested
time_period: ""         # YYYY-MM to YYYY-MM
shelf_life: short | medium | long  # short = 6mo, medium = 1-2yr, long = 3yr+
```

For `campaign-analysis`:
```yaml
campaign_type: ""
channel: ""
metric: ""              # Primary metric tracked
result: ""              # Quantified outcome
```
