# Fitness Knowledge Domain

Health and performance science for high-output individuals and teams.

---

## Purpose

Build Better operates at a high pace. The people who build it need physical and mental capacity to match. This domain captures the science of health, performance, recovery, and longevity — with a specific focus on protocols that are practical for people with demanding schedules and high cognitive output requirements.

This is also a content domain for Build Better. Fitness is a subject we cover, and this domain serves both the people who create that content and the depth of understanding behind it.

---

## Knowledge Standards

A fitness entry earns `status: active` when it:

- Is grounded in peer-reviewed research, not influencer consensus — the fitness industry is particularly susceptible to unverified claims
- States the evidence quality honestly: systematic review, RCT, observational study, expert opinion, or n=1 experimentation
- Specifies the population the research applies to (trained vs. untrained, age, sex, health status)
- Distinguishes between statistically significant effects and practically meaningful ones
- Includes the protocol specifics necessary to replicate the result (dose, frequency, duration, intensity)
- Notes contraindications and who should not apply the protocol without professional guidance

**What good fitness knowledge looks like:** An entry on sleep and cognitive performance documents the primary studies, the effect sizes on specific cognitive tasks, the dose-response relationship (how much sleep deprivation produces how much impairment), the known recovery trajectories, and two to three practical protocols for optimizing sleep in a demanding work environment.

---

## Naming Standards

| Entry Type | Convention | Example |
|---|---|---|
| Protocol | `<topic>-protocol.md` | `strength-training-protocol.md` |
| Research summary | `<topic>-research.md` | `sleep-research.md` |
| Concept | `<concept>.md` | `progressive-overload.md` |
| Supplement analysis | `<supplement>-analysis.md` | `creatine-analysis.md` |
| Program | `<name>-program.md` | `foundation-training-program.md` |

---

## Cross Referencing

- `psychology/` — motivation, habit formation, willpower, stress physiology
- `productivity/` — energy management, recovery, cognitive performance optimization
- `books/` — key fitness and health books (Attia, Huberman, etc.)
- `frameworks/` — frameworks for evaluating health claims and designing personal protocols

---

## Metadata

```yaml
---
title: ""
domain: fitness
type: protocol | research-summary | concept | supplement-analysis | program
tags: []
created: ""
updated: ""
status: draft | active | archived
confidence: low | medium | high
tldr: ""
related: []
---
```

**Additional fields for research-based entries:**
```yaml
evidence_level: ""      # systematic-review | rct | observational | expert-opinion | n1
population: ""          # Who the research applies to
effect_size: ""         # small | medium | large | varies
primary_researcher: ""
```

**Additional fields for protocols:**
```yaml
goal: []                # strength | endurance | fat-loss | recovery | longevity | cognitive
time_commitment: ""     # e.g., "45 min, 4x/week"
equipment_required: ""  # none | minimal | gym
difficulty: beginner | intermediate | advanced
```
