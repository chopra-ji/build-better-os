# Architecture — Creator Engine

---

## System Overview

The Creator Engine is a sequential, eight-stage review pipeline. Each stage evaluates one dimension of script quality, scores it, and either passes the script to the next stage or triggers an optimization cycle before advancing.

```
┌─────────────────────────────────────────────────────────────┐
│                  CREATOR ENGINE PIPELINE                    │
│                                                             │
│  INPUT: Script Package                                      │
│         ↓                                                   │
│  [Stage 1]  Hook Review                                     │
│         ↓                                                   │
│  [Stage 2]  Retention Review                                │
│         ↓                                                   │
│  [Stage 3]  Founder Voice Review                            │
│         ↓                                                   │
│  [Stage 4]  Social Language Review                          │
│         ↓                                                   │
│  [Stage 5]  Comment Engineering                             │
│         ↓                                                   │
│  [Stage 6]  Shareability Review                             │
│         ↓                                                   │
│  [Stage 7]  Build Better Brand Review                       │
│         ↓                                                   │
│  [Stage 8]  Instagram Optimization Review                   │
│         ↓                                                   │
│  OUTPUT: Final Production Script                            │
└─────────────────────────────────────────────────────────────┘
```

---

## Stage Design

Each stage follows the same internal structure:

```
STAGE N
  │
  ├─ 1. EVALUATE  — apply stage questions to script
  │
  ├─ 2. SCORE     — assign dimension score (1–10)
  │
  ├─ 3. DECIDE ───── score ≥ pass threshold ──────► ADVANCE
  │                                                   │
  │            └── score < pass threshold ──► OPTIMIZE
  │                                              │
  │                                         apply optimization checklist
  │                                              │
  │                                         re-score (max 2 attempts)
  │                                              │
  │                     score ≥ threshold ──► ADVANCE
  │                     score < threshold ──► ESCALATE
  │
  └─ 4. LOG       — record score, decision, changes made
```

---

## Why Sequential

The eight dimensions are not independent. Each stage builds on the previous one:

- **Hook** must be evaluated first because a failing hook means no one sees the rest — retention, voice, and language optimizations are wasted if stage 1 fails.
- **Retention** is evaluated second because the structural arc determines where social language and hooks land inside the script.
- **Founder Voice** is evaluated before Social Language because the voice defines the register; language optimization works within the established voice, not independently of it.
- **Comment Engineering** and **Shareability** are evaluated after the language pass because social mechanics depend on the final wording, not the draft wording.
- **Build Better Brand** is evaluated near the end because brand consistency is assessed against the near-final script, not the raw draft.
- **Instagram Optimization** is always last — it verifies that all previous optimizations have produced a script that meets platform requirements, including runtime.

---

## Runtime Enforcement Architecture

Runtime is checked at Stage 8 (Instagram Optimization Review) and is enforced as a hard constraint. If a script exceeds 60 seconds after all previous optimizations, the engine runs the Runtime Compression Protocol defined in `OPTIMIZATION_PIPELINE.md` before the script can advance to Final Production.

Runtime estimation uses the following model:

| Speaking Pace | Words per Second | Words per Minute |
|---|---|---|
| Slow / emphatic | 1.8 wps | 108 wpm |
| Natural / conversational | 2.2 wps | 130 wpm |
| Fast / energetic | 2.7 wps | 160 wpm |

**Target word count for spoken script content: 110–140 words.**

This range assumes natural conversational pace (130 wpm) with room for pauses, emphasis, and breath. The engine uses 130 wpm as its baseline estimation. Creators who speak faster or slower must calibrate their own baseline.

Word count applies to spoken content only — on-screen text overlays, captions, and silent visual instructions are not included in the word count.

---

## Data Flow

```
Script Package (from Script Department)
  ↓
  contains: script, hook, scene breakdown, voiceover notes,
            talking head notes, b-roll notes, on-screen text,
            caption draft, CTA
  ↓
Stage 1 → Stage 2 → ... → Stage 8
  ↓
At each stage:
  - stage receives: current working script + all prior stage scores
  - stage produces: updated working script + current stage score + change log
  ↓
Final Production Script
  contains: optimized script, all 8 dimension scores, change log,
            runtime estimate, approval status
```

---

## Inputs and Outputs

### Input: Script Package

The Creator Engine accepts a Script Package as produced by the Script Department. The Script Package must include:
- `script` — full spoken content
- `hook` — the opening line(s) designated as the hook
- `cta` — the call to action
- `on_screen_text` — any text overlays (if applicable)
- `caption_draft` — the intended caption (if applicable)

A Script Package missing any of these fields is rejected at intake with a structured error before Stage 1 begins.

### Output: Final Production Script

```
engine_run_id:        string
input_script_id:      string
produced_at:          ISO 8601 timestamp
status:               enum [approved | escalated | rejected]

final_script:         string (full spoken content)
runtime_estimate:     string (e.g. "52 seconds at 130 wpm")
word_count:           integer

dimension_scores:
  hook:               integer (1–10)
  retention:          integer (1–10)
  founder_voice:      integer (1–10)
  social_language:    integer (1–10)
  comment_engineering: integer (1–10)
  shareability:       integer (1–10)
  build_better_brand: integer (1–10)
  instagram_optimization: integer (1–10)

aggregate_score:      integer (sum of dimension scores, max 80)
pass_threshold:       56 (70% of 80)

change_log:
  - stage:            string
    original:         string
    revised:          string
    reason:           string

production_notes:     string (any notes for the creator)
escalation_notes:     string (populated only if status = escalated)
```

---

## Position in Build Better OS

The Creator Engine sits between the Script Department (upstream) and the production recording (downstream). It is not a department — it has no org chart position, no escalation owner within the department structure. It reports its outputs to the requesting party (the Script Department's downstream consumer) and escalation to the Platform Director.

```
Script Department
      ↓
Creator Engine
      ↓
Production (recording, editing, publishing)
```
