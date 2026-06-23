# Creator Engine — Build Better OS

The Creator Engine is the quality review and optimization system that transforms a technically correct script into a production-ready Instagram Reel.

It is not a content creation system. It does not generate ideas, write briefs, or produce first drafts. It receives a completed script from the Script Department and runs it through a structured, multi-stage review pipeline before approving it for production.

---

## What It Does

The Creator Engine accepts a Script Package and returns a Final Production Script — the same content, optimized for Instagram performance. Every word, every pause, every structural choice is reviewed against a defined standard. If a script does not meet the standard, the engine improves it or rejects it. Nothing proceeds to production unchecked.

---

## What It Is Not

- Not a creative department. It does not originate content.
- Not a script writer. It improves scripts; it does not replace them.
- Not a general video production tool. It is scoped to Instagram Reels, 45–60 seconds.
- Not a subjective taste filter. Every judgment is made against documented criteria.

---

## Runtime Constraint

**All Instagram Reels must target 45–60 seconds. Scripts that exceed 60 seconds are not approved for production.** The engine is responsible for enforcing this constraint. If a script exceeds the target, the engine compresses it using the protocol defined in `OPTIMIZATION_PIPELINE.md`.

---

## File Index

| File | Purpose |
|---|---|
| `README.md` | This file. Entry point and overview. |
| `MISSION.md` | Why this engine exists and what success means. |
| `ARCHITECTURE.md` | Stage diagram, data flow, and how stages connect. |
| `WORKFLOW.md` | Complete per-stage documentation: mission, questions, pass/fail, optimization, examples. |
| `SCORING_SYSTEM.md` | How each dimension is scored and how scores are aggregated. |
| `OPTIMIZATION_PIPELINE.md` | What happens when a stage fails; runtime compression protocol. |
| `QUALITY_STANDARDS.md` | Final production gate and definition of done. |
| `CHECKLIST.md` | Operational checklists for each stage and the full run. |
| `VERSION.md` | Current engine version. |
| `CHANGELOG.md` | History of changes to the engine's design. |

---

## Review Dimensions

The engine reviews every script across eight dimensions:

| # | Dimension | What It Evaluates |
|---|---|---|
| 1 | Hook | Does the first 3 seconds demand attention? |
| 2 | Retention | Does the structure prevent drop-off throughout? |
| 3 | Founder Voice | Does it sound like a real person, not a content machine? |
| 4 | Social Language | Is the language native to Instagram, not a blog post? |
| 5 | Comment Engineering | Does it provoke a response? |
| 6 | Shareability | Does someone want to send this to someone else? |
| 7 | Build Better Brand | Does it reflect Build Better's positioning? |
| 8 | Instagram Optimization | Does it meet platform-specific technical requirements? |

---

## Pipeline Summary

```
Script Package (input)
        ↓
[Stage 1]  Hook Review
        ↓
[Stage 2]  Retention Review
        ↓
[Stage 3]  Founder Voice Review
        ↓
[Stage 4]  Social Language Review
        ↓
[Stage 5]  Comment Engineering
        ↓
[Stage 6]  Shareability Review
        ↓
[Stage 7]  Build Better Brand Review
        ↓
[Stage 8]  Instagram Optimization Review
        ↓
Final Production Script (output)
```

The pipeline is sequential. A stage that fails triggers optimization before proceeding. See `WORKFLOW.md` for full stage detail and `OPTIMIZATION_PIPELINE.md` for failure handling.

---

## Quick Reference

| Attribute | Value |
|---|---|
| **Engine Name** | Creator Engine |
| **Input** | Script Package (from Script Department) |
| **Output** | Final Production Script |
| **Target Runtime** | 45–60 seconds |
| **Maximum Runtime** | 60 seconds (hard limit) |
| **Review Dimensions** | 8 |
| **Pipeline Stages** | 8 |
| **Version** | See `VERSION.md` |
