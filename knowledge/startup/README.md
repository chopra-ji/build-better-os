# Startup Knowledge Domain

Strategy, growth, and operations for building a company from zero.

---

## Purpose

Build Better is a startup operating inside the media industry. This domain captures what we know about how to build a company: hiring, fundraising, product-market fit, growth, organizational design, culture, and the specific dynamics of early-stage companies that differ from established ones.

This is not a collection of startup platitudes. It is a repository of hard-won operational knowledge — what founders and operators have learned by doing, validated by outcome, and documented with enough specificity to be transferable.

---

## Knowledge Standards

A startup entry earns `status: active` when it:

- Is specific about stage: what works at 5 people may be wrong at 50, and definitely wrong at 500
- Is grounded in a real company's experience, not generalized theory — name the company, name the founder, name the outcome
- Distinguishes between what caused success and what merely correlated with it
- Includes the failure mode: what goes wrong when you misapply this, or apply it at the wrong time
- Has a direct implication for Build Better's current situation or a clearly labeled future scenario

**What good startup knowledge looks like:** An entry on performance-based hiring documents the specific evaluation method used by a named company, the signals it screens for and why, the false positives and false negatives they encountered, how the bar changed as the company scaled, and how to adapt it to Build Better's current size and hiring volume.

---

## Naming Standards

| Entry Type | Convention | Example |
|---|---|---|
| Framework | `<framework>.md` | `product-market-fit.md` |
| Operational pattern | `<topic>.md` | `recruiting-at-seed.md` |
| Case study | `<company>-case-study.md` | `substack-case-study.md` |
| Fundraising concept | `<concept>.md` | `safe-note.md` |
| Stage guide | `<stage>-playbook.md` | `pre-seed-playbook.md` |

---

## Cross Referencing

- `business/` — business model, strategy, and competitive positioning
- `finance/` — fundraising mechanics, cap tables, financial modeling
- `psychology/` — leadership psychology, team motivation, founder mental health
- `frameworks/` — decision frameworks for high-uncertainty environments
- `productivity/` — operational efficiency and systems for small, fast teams

---

## Metadata

```yaml
---
title: ""
domain: startup
type: framework | operational-pattern | case-study | fundraising-concept | stage-guide
tags: []
created: ""
updated: ""
status: draft | active | archived
confidence: low | medium | high
tldr: ""
related: []
stage: []    # pre-idea | pre-seed | seed | series-a | series-b | growth | all
---
```

**Additional fields for `case-study`:**
```yaml
company: ""
founder: ""
outcome: ""            # What happened to the company
key_metric: ""         # The number that tells the story
time_period: ""
```

**Additional fields for `fundraising-concept`:**
```yaml
instrument_type: ""    # equity | debt | convertible | grant | revenue-based
applicable_stage: []
```
