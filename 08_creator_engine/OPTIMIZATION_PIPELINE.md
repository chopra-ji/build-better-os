# Optimization Pipeline — Creator Engine

This file documents what happens when a stage fails, including the optimization cycle, iteration limits, and the Runtime Compression Protocol.

For stage-specific optimization checklists, see `WORKFLOW.md`. For scoring thresholds, see `SCORING_SYSTEM.md`.

---

## When a Stage Fails

A stage fails when the dimension score is 6 or below. On failure, the engine does not advance to the next stage. It runs the optimization cycle for that stage:

```
STAGE FAILS (score ≤ 6)
       │
       ▼
Apply optimization checklist for this stage (see WORKFLOW.md)
       │
       ▼
Re-score the dimension
       │
       ├── score ≥ 7 ──► ADVANCE to next stage
       │
       └── score ≤ 6 ──► second optimization attempt
                             │
                             ├── score ≥ 7 ──► ADVANCE
                             │
                             └── score ≤ 6 ──► ESCALATE
```

**Maximum optimization attempts per stage: 2.** A stage that still fails after two optimization attempts is escalated. The engine does not continue to the next stage until escalation is resolved.

---

## Escalation

Escalation is triggered by:
1. A stage still failing after 2 optimization attempts
2. Any dimension scoring ≤ 4 (auto-escalation threshold)
3. Runtime still exceeding 60 seconds after Runtime Compression Protocol

On escalation:
- The engine logs the current state of the script, the failing dimension, the scores, and the optimizations attempted
- The script is returned to the upstream requestor (Platform Director or Script Department) with the full escalation report
- No further pipeline stages run until the escalation is resolved

Escalation is not a failure of the Creator Engine. It is the correct output when a script has a problem the engine cannot resolve within defined parameters.

---

## Runtime Compression Protocol

Runtime compression is triggered when Stage 8 (Instagram Optimization Review) calculates an estimated runtime exceeding 60 seconds.

**Target after compression: 45–55 seconds.** The compression target is not 60 seconds — it is 45–55. Compressing to exactly 60 leaves no room for pauses, emphasis, or natural variation in speaking pace.

### Compression is done in this order

**Step 1 — Remove redundant statements.**
Identify any point that is made more than once. Keep the sharper version; remove the rest. Redundancy is common in scripts that have been optimized across many stages and may have accumulated restatements.

**Step 2 — Cut the weakest supporting point.**
If the script has multiple examples or supporting points, identify the one that adds the least value relative to its word count. Remove it. The script must still make sense and still pay off its opening promise.

**Step 3 — Compress transitions.**
Transitions between points ("And that brings me to my next point, which is...") are often the most compressible elements. Replace with direct pivots ("Second:") or remove entirely if the flow is clear without them.

**Step 4 — Shorten the setup.**
The opening setup before the hook often contains more words than it needs. Tighten it. Every word before the hook is borrowed against attention.

**Step 5 — Verify the hook, share trigger, and CTA survived.**
After compression, confirm that the hook (Stage 1), the shareability moment (Stage 6), and the CTA (Stage 8) are all intact and uncompromised. Compression must not sacrifice the engine's highest-value elements to gain seconds.

**Step 6 — Re-calculate runtime.**
Recount words. Recalculate at 130 wpm. If runtime is now within 45–60 seconds, advance. If still over 60 seconds, return to Step 1 for a second compression pass.

**Step 7 — If still over 60 seconds after two compression passes: ESCALATE.**
The script requires structural rework that is beyond the Creator Engine's remit. Return to Script Department with the compression log and a specific note on what needs to change.

---

## What Compression Must Never Do

Compression serves runtime. It must not serve itself. The following are prohibited regardless of the time saved:

- Remove the hook
- Remove the comment trigger (Stage 5)
- Remove the share trigger (Stage 6)
- Cut a specific, personal claim and replace it with a generic one
- Reduce the script to a list of points without emotional beats
- Remove the CTA

If meeting the runtime constraint requires any of the above, the script is escalated rather than compressed.

---

## Under-Length Protocol

If Stage 8 calculates an estimated runtime under 40 seconds, the script is flagged for review — not automatically padded.

Under-length scripts are typically a symptom of over-compression in earlier stages. The engine checks the Stage 3 (Founder Voice) and Stage 2 (Retention) outputs for content that was removed during optimization that should be restored. Padding for the sake of duration is not acceptable.

If the script is genuinely complete at under 40 seconds and cannot be expanded without compromising quality, the script is flagged for production with a note: **short-form approved**. The creator must confirm intentional short-form delivery.
