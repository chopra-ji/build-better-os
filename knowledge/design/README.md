# Design Knowledge Domain

Visual language, user experience, and brand identity.

---

## Purpose

This domain captures Build Better's working knowledge of design — the principles that govern visual communication, the craft of layout and typography, UX patterns for digital products, brand identity systems, and the evaluation criteria for design quality.

For a media company, design is not decoration. It is the first communication the audience has with content — before a word is read or a second of video is watched. This domain makes our design thinking explicit and transmissible.

---

## Knowledge Standards

A design entry earns `status: active` when it:

- States a principle at the level of mechanism: not just "whitespace is good" but why whitespace reduces cognitive load and how to calibrate the amount
- Includes visual examples where applicable — ASCII diagrams, references to specific works, or annotated screenshots
- Distinguishes between timeless design principles and current aesthetic trends
- Specifies the medium and context where the principle applies (print vs. digital, editorial vs. product, web vs. mobile)
- Has a Build Better application — how does this principle affect decisions we make?

**What good design knowledge looks like:** An entry on typographic hierarchy documents the cognitive principle behind hierarchy (the eye needs a path through the page), the specific tools for creating it (size, weight, color, spacing), shows three examples in our actual format context, and states our current hierarchy system with the reasoning for each choice.

---

## Naming Standards

| Entry Type | Convention | Example |
|---|---|---|
| Design principle | `<principle>.md` | `visual-hierarchy.md` |
| UX pattern | `<pattern>.md` | `progressive-disclosure.md` |
| Brand element | `<element>.md` | `color-system.md` |
| Tool review | `<tool>-review.md` | `figma-review.md` |
| Format guide | `<format>-design.md` | `thumbnail-design.md` |

---

## Cross Referencing

- `psychology/` — perceptual psychology, attention, color cognition, gestalt principles
- `technology/` — design system tooling, CSS frameworks, image optimization
- `storytelling/` — visual storytelling, layout as narrative flow
- `marketing/` — conversion design, thumbnail optimization, brand recognition

---

## Metadata

```yaml
---
title: ""
domain: design
type: principle | ux-pattern | brand-element | tool-review | format-guide
tags: []
created: ""
updated: ""
status: draft | active | archived
confidence: low | medium | high
tldr: ""
related: []
applies_to: []      # web | mobile | print | video | brand | all
is_timeless: true   # true = principle persists across trends; false = trend-dependent
---
```
