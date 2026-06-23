# Workflow — Script Department

---

## Overview

The Script Department operates as a sequential production pipeline. Every script follows the same six-step workflow regardless of content format or urgency tier. Steps are not skipped. Steps 1 and 2 are validation gates — work does not proceed if either gate fails.

```
Creative Brief Received
        │
        ▼
  Step 1: Input Validation ──── FAIL ────► Return to Creative Department
        │                                   (or Hold + Escalate)
       PASS
        │
        ▼
  Step 2: Brief Comprehension ─ FLAG ────► Hold pending Creative Department clarification
        │
       CLEAR
        │
        ▼
  Step 3: Script Drafting
        │
        ▼
  Step 4: Component Assembly
        │
        ▼
  Step 5: Quality Gate Review ── FAIL ──► Rework (max 2 attempts before escalation)
        │
       PASS
        │
        ▼
  Step 6: Delivery
        │
        ▼
  Script Package Delivered
```

---

## Step 1: Input Validation

**Duration target:** < 30 minutes

Validate the received Creative Brief against all checks in INPUTS.md before any scripting work begins.

### Actions

1. Confirm `status: complete` on the brief.
2. Confirm all 10 dimensions are present with non-empty, non-placeholder values.
3. Confirm `core_message.statement` is one sentence with one idea.
4. Confirm `hook_direction.concept` is specific enough to execute.
5. Confirm `source_research_refs` contains at least one entry.
6. Confirm `format` is a valid enum value.
7. Log the brief receipt in the input log with: `brief_ref`, `received_at`, `disposition: in_progress`.
8. Determine applicable components using the Format-Component Applicability Matrix in OUTPUTS.md.
9. Log the applicable component list.

### Outcomes

| Result | Action |
|---|---|
| All checks pass | Proceed to Step 2 |
| Status is `draft` or `escalated` | Hold brief; contact Creative Department; log `disposition: held` |
| A dimension is missing or empty | Return brief to Creative Department with specific dimension gap documented |
| Core message is not one sentence | Return brief to Creative Department |
| Hook concept is not specific | Return brief to Creative Department with specificity request |
| Format is missing or invalid | Contact Creative Department; do not return brief — this is a metadata error |

---

## Step 2: Brief Comprehension

**Duration target:** 30–60 minutes

Read the complete brief. Before scripting, produce a comprehension summary — an internal document that maps every brief dimension to a scripting implication. This step exists to catch misalignments before execution, not during.

### Brief Comprehension Summary

The comprehension summary is an internal working document, not a deliverable. It is not sent anywhere. It serves as the scripting anchor.

```
# Brief Comprehension Summary (internal)

brief_ref:              [brief output_id]
prepared_at:            [timestamp]

angle_understood_as:    [restate the angle in own words — what position on the topic
                          this script must take, and what it must NOT argue]
audience_calibration:   [restate the audience in terms of what this means for word
                          choice, assumed knowledge, and register]
message_test:           [state the core message as a test: every scene must pass —
                          "does this scene serve [message]?"]
hook_execution_plan:    [describe specifically what will happen in the first 3–5 seconds]
retention_map:          [which scenes carry which secondary hooks; where the payoff lands]
arc_sequence:           [opening → development → tension → resolution, in specific terms]
visual_notes:           [what the visual direction means for B-roll, camera, editing]
emotional_journey:      [how tone shifts from opening to close; specific not vague]
curiosity_plan:         [how the knowledge gap opens, what sustains it, when it resolves]
cta_plan:               [exact CTA placement, what precedes it, what emotional state it lands in]

flags:                  [any dimension that was hard to interpret or might generate questions
                          during scripting — noted here before work begins]
```

### Flagged Dimensions

If a brief dimension is ambiguous but not clearly unexecutable, the Script Department has two paths:

1. **Proceed with judgment** if the dimension provides sufficient direction to make a defensible scripting decision. The judgment call is logged in the comprehension summary.
2. **Hold and request clarification** if proceeding would require guessing at the Creative Department's intent. The hold is logged, the Creative Department is contacted, and the 48-hour response window begins.

A dimension is flagged — not returned — when the issue is interpretive ambiguity, not a structural failure of the brief. Structural failures (empty dimensions, non-singular core message) are return conditions, not flag conditions.

---

## Step 3: Script Drafting

**Duration target:** 2–4 hours (standard format); 4–6 hours (long_form_video or article)

Draft the Script component (Component 1) and the Hook component (Component 2) as the first act of scripting. All other components derive from the Script; the Script cannot be assembled after the components.

### Scripting Sequence

1. **Write the Hook first.** The hook is the highest-leverage moment in any piece of content. It must execute the brief's hook concept precisely. Write it, test it against the brief, and lock it before drafting the body.

2. **Write the opening and establish the arc.** Translate the brief's `story_arc.opening` into the first scene or section of the full script.

3. **Draft through development and tension.** Execute `story_arc.development` and `story_arc.tension_point` in sequence. Each scene is tested: does it serve the core message? Does it execute the arc function? Does the retention mechanism remain active?

4. **Draft the resolution and CTA.** Execute `story_arc.resolution`. Ensure the resolution delivers the core message. Draft the CTA in the script. The CTA must match the brief's `cta_strategy.placement` — if `end_only`, the CTA appears once at the end. If `woven_throughout`, CTA moments appear at multiple points in the script.

5. **Self-test the draft.** Before moving to component assembly:
   - Read the hook: does it execute the brief's hook concept, or a different concept that seemed better during drafting? If different, revise.
   - Read the core message delivery moment: is it the one message from the brief, or has it grown? If grown, trim.
   - Read the CTA: does it match the brief's desired action and placement? If not, revise.

### Format-Specific Scripting Notes

| Format | Key scripting considerations |
|---|---|
| long_form_video | Scene markers required. Stage directions in [brackets]. Secondary hooks spaced throughout — viewer must re-engage at each act. |
| short_form_video | Hook is 80% of the work. Every second of script must justify itself. Cutting is a scripting act, not an editing afterthought. |
| article | Section headers function as the hook and secondary hooks. The opening paragraph is the hook — it must execute the brief's hook concept in written form. |
| newsletter | Subject line is the hook. The first paragraph holds the reader. Sectioned structure with one clear CTA at the end or woven. |
| podcast | Hook is the first spoken sentence. No visual, no B-roll. Every retention mechanism is audio. Speaker transitions are scripted. |
| social_post | Caption IS the script. The first line is the hook. Character limits are a scripting constraint, not an editing task. |

---

## Step 4: Component Assembly

**Duration target:** 1–2 hours

Assemble all applicable components from the Script. Components are derived from the Script — they do not introduce new creative decisions. Every component field contains specific, actionable content.

### Assembly Sequence

Work through applicable components in order:

1. **Component 3 (Scene Breakdown):** Extract from the Script. Every scene gets a number, label, purpose statement, arc function, and duration estimate.

2. **Component 4 (Voiceover, if applicable):** Extract narration from the Script. Remove all stage directions, music cues, and on-screen text references. Format for a recording session.

3. **Component 5 (Talking Head Notes, if applicable):** Derive from the brief's emotion and audience dimensions and the script's pacing. Write specific direction — not "be energetic" but what energy looks like for this piece.

4. **Component 6 (B-roll Notes, if applicable):** Map the Script's sections to visual coverage needs. Each section gets a coverage description, mood requirement, duration estimate, and priority level.

5. **Component 7 (Camera Notes, if applicable):** Derive from the brief's visual direction. Framing and movement serve the brief's visual mood — every camera note is anchored to a brief dimension, not to production preference.

6. **Component 8 (Editing Notes, if applicable):** Derive from the brief's visual pacing and retention strategy. Overall rhythm, music direction, and key cut points are all grounded in the brief.

7. **Component 9 (On-screen Text, if applicable):** Extract from the Script and the brief's core message and CTA. All text is final — no placeholders. TEXT-01, TEXT-02 etc.

8. **Component 10 (Caption Draft, if applicable):** Derive from the Script. Caption text is accurate to the script — not summarized. Timecodes are estimated.

9. **Component 11 (CTA):** Derive from the brief's `cta_strategy`. CTA text is final. Placement matches the brief's `placement` field exactly.

### Component Assembly Check

After assembling all applicable components, run the consistency check:

- Does Component 5 (Talking Head Notes) match the emotional journey described in Component 2 (Hook)?
- Does Component 6 (B-roll Notes) match the visual mood in Component 7 (Camera Notes)?
- Does Component 9 (On-screen Text) carry the same core message as Component 11 (CTA)?
- Does the pacing in Component 8 (Editing Notes) match the pacing described in Component 5 (Talking Head Notes)?

Inconsistencies at this stage are scripting gaps, not production gaps. Fix them now.

---

## Step 5: Quality Gate Review

**Duration target:** 30–60 minutes

Run all quality gates defined in QUALITY.md in sequence. Gates are not optional. A gate failure stops delivery.

| Gate | Check | Fail Action |
|---|---|---|
| Gate 1: Brief Fidelity | All 10 brief dimensions faithfully executed | Identify gap; rework specific component(s) |
| Gate 2: Component Completeness | All applicable components present and fully populated | Complete missing component(s) or populate empty fields |
| Gate 3: Internal Consistency | Components are consistent with each other | Resolve inconsistency; components must align |
| Gate 4: Traceability | Every scripting decision can be linked to a brief dimension | Add traceability notes or revise decisions that cannot be linked |

**Maximum rework attempts:** 2. If the package fails a gate on the second rework attempt, escalate to the Platform Director with a documented gate failure report. Do not deliver a failed package.

---

## Step 6: Delivery

**Duration target:** 15–30 minutes

Deliver the completed Script Package via the output channel. Notify all consumers.

### Delivery Actions

1. Set `status: complete` and `produced_at` timestamp on the package.
2. Confirm `applicable_components` list matches the components actually included.
3. Log the delivery: update the input log entry with `disposition: completed` and `script_package_ref`.
4. Deliver to Production Team (full package).
5. Deliver Components 10 and 11 (Caption Draft and CTA) to Publishing Department separately, with a note indicating the full package is available if needed for SEO/metadata purposes.
6. Notify Workflow Department: Script Package delivered, content item advancing to production.
7. Log the Workflow Department notification.

### Post-Delivery

The Script Department's work is complete at delivery. The production team does not contact the Script Department after delivery for creative clarification — if a completed package generates clarification requests, that is a quality failure, logged and reviewed in the next quality cycle.

If a revision request is received post-delivery, it enters the revision workflow (see SOPS.md → SOP-S02).

---

## SLA Reference

| Urgency Tier | Definition | Delivery Target |
|---|---|---|
| Standard | Default tier for all requests | 3 business days from brief receipt |
| Expedited | Requested by Workflow Department with documented reason | 1 business day from brief receipt |
| Urgent | Platform Director authorization required | Same business day — scripting begins immediately |

SLA clock starts when the Creative Brief passes Step 1 validation. Briefs that fail validation and are returned to the Creative Department pause the SLA clock. The clock resumes when the revised brief passes validation.

---

## Revision Workflow

When a delivered Script Package is returned by the Production Team or Platform Director with documented feedback:

1. Receive the revision request. Confirm it is valid (see INPUTS.md — Revision Request Validity).
2. If invalid (out of scope, asks for brief-dimension changes): decline in writing, document, and escalate if the requester disputes the scope boundary.
3. If valid: acknowledge receipt and provide an expected re-delivery date (same as applicable SLA tier).
4. Rework only the component(s) identified in the revision request. Do not revise components not referenced.
5. Increment `revision_number` on the package.
6. Run all quality gates on the full package (not just the revised component).
7. Deliver the revised package and notify all consumers.

**Maximum revisions:** 2 post-delivery revisions. If a package requires a third revision, escalate to the Platform Director. A third revision is a signal of either a brief quality problem or a systemic scripting gap, and requires cross-department review.
