# Checklist — Script Department

These checklists are operational tools. They are run on every script, in sequence. A checklist item is checked only when it is confirmed true — not when it is assumed true.

---

## Checklist 1: Brief Receipt and Validation

Run this checklist when a Creative Brief is received, before any scripting work begins.

- [ ] Creative Brief received and logged in the input log with `received_at` timestamp
- [ ] `status` field on the brief is `complete` (not `draft`, not `escalated`, not `rejected`)
- [ ] `format` field is a valid enum value (one of: `long_form_video`, `short_form_video`, `article`, `newsletter`, `podcast`, `social_post`)
- [ ] All 10 dimensions are present in the brief (none are null, absent, or placeholder)
- [ ] `core_message.statement` is one sentence containing one idea
- [ ] `hook_direction.concept` is specific — states what will be said or shown in the first 3–5 seconds (not a description of the hook type)
- [ ] `source_research_refs` contains at least one research output ID
- [ ] Applicable components identified using the Format-Component Applicability Matrix in OUTPUTS.md
- [ ] Applicable component list logged alongside the brief receipt entry
- [ ] SLA tier confirmed (standard / expedited / urgent) and delivery target logged

**If any item fails:** Take the appropriate action from WORKFLOW.md Step 1 before proceeding.

---

## Checklist 2: Brief Comprehension

Run this checklist after validation passes, before scripting begins. The Brief Comprehension Summary must be complete before this checklist is checked.

- [ ] Brief Comprehension Summary drafted (internal working document per WORKFLOW.md Step 2)
- [ ] Content angle restated in own words — confirmed distinct from general topic
- [ ] Audience calibration translated to specific word choice, register, and assumed-knowledge implications for this script
- [ ] Core message test written as a pass/fail test applicable to individual scenes
- [ ] Hook execution plan is specific (what happens in seconds 0–5, 0–15, or equivalent for this format)
- [ ] Retention map shows where secondary hooks land and where the payoff releases
- [ ] Arc sequence maps brief's opening → development → tension → resolution to planned script sections
- [ ] Emotional journey mapped — how tone shifts from opening through close, with specific transition points
- [ ] Curiosity plan specifies: what gap opens, what sustains it, when it resolves, and where
- [ ] CTA plan confirms: exact placement, emotional state of the viewer at CTA moment, and friction reduction approach
- [ ] Flagged dimensions logged (any dimension that required interpretive judgment or a hold request)

**If a dimension required a hold request:** Confirm hold has been logged and Creative Department has been contacted before proceeding.

---

## Checklist 3: Script Draft Self-Check

Run this checklist immediately after completing the Script draft (Component 1), before beginning component assembly.

- [ ] Hook: the hook text executes the brief's `hook_direction.concept` — not a different concept that seemed stronger during drafting
- [ ] Hook: `hook_direction.type` matches the brief's exact enum value
- [ ] Core message: the single idea in the brief is delivered in the script — it has not been expanded to two ideas, diluted, or reframed
- [ ] Story arc: the script follows the brief's `story_arc` sequence — opening → development → tension → resolution
- [ ] CTA: CTA text is present; placement matches `brief.cta_strategy.placement` exactly
- [ ] CTA: the action the viewer is asked to take matches `brief.cta_strategy.desired_action`
- [ ] Emotional journey: the script's emotional tone shifts as specified in `brief.emotion.emotional_journey`
- [ ] Curiosity gap: the knowledge gap opens near the start, sustains through the middle, and resolves as specified in `brief.curiosity_mechanism.resolution`
- [ ] No creative additions: the script does not introduce a new angle, a second message, an alternative hook concept, or a CTA variant not in the brief
- [ ] No placeholder text anywhere in the Script

---

## Checklist 4: Component Assembly

Run this checklist during component assembly (WORKFLOW.md Step 4). Check each component as it is completed.

### Component 2: Hook
- [ ] `hook_text` matches the Script exactly (extracted, not rewritten)
- [ ] `hook_type` matches `brief.hook_direction.type`
- [ ] `brief_promise_executed` is specific analysis — explains how this specific hook delivers on the brief's promise, not a restatement of the brief
- [ ] `curiosity_gap_created` states the specific question or tension the hook opens
- [ ] `delivery_direction` is specific to this hook, not a generic "be engaging"
- [ ] `production_note` is present (or explicitly "none" if no specific production consideration)

### Component 3: Scene Breakdown *(if applicable)*
- [ ] Scene count matches the Script
- [ ] Every scene has: `scene_label`, `script_excerpt` (accurate first line), `purpose`, `arc_function`, `duration_estimate`
- [ ] All six `arc_function` types are used correctly (not every scene is "development")
- [ ] `retention_mechanism` field is populated for scenes where a secondary hook or mechanism is active

### Component 4: Voiceover *(if applicable)*
- [ ] Narration text is extracted from the Script with no stage directions, music cues, or on-screen text references present
- [ ] `pacing_notes` identifies specific points in the narration where pacing shifts
- [ ] `tone_direction` is specific — cites a specific moment or phrase, not a vague adjective
- [ ] `emphasis_words` are real emphasis points, not just important words generally

### Component 5: Talking Head Notes *(if applicable)*
- [ ] `energy_level` enum matches the brief's emotion dimension
- [ ] `energy_description` describes what this energy level looks like for THIS piece specifically
- [ ] `pacing` enum is consistent with the brief's `visual_direction.pacing`
- [ ] `emphasis_moments` cites specific script lines or scene references
- [ ] `authenticity_notes` is calibrated to the brief's audience — what feels genuine to THIS audience

### Component 6: B-roll Notes *(if applicable)*
- [ ] Every scene with significant visual content has a B-roll section
- [ ] `coverage_description` is intent-based ("footage that conveys X") not a shot list ("wide shot of Y")
- [ ] `mood_requirement` matches the brief's `visual_direction.mood`
- [ ] `what_to_avoid` includes entries from `brief.visual_direction.what_to_avoid`
- [ ] All sections have a `priority` level (essential / preferred / optional)

### Component 7: Camera Notes *(if applicable)*
- [ ] Every scene has a camera note entry
- [ ] `framing` rationale is tied to the brief's visual direction, not to production convention
- [ ] `movement` direction has a "why" that connects to the scene's purpose
- [ ] `transition_out` is specified for every scene

### Component 8: Editing Notes *(if applicable)*
- [ ] `overall_rhythm` enum matches the brief's `visual_direction.pacing`
- [ ] `music_direction` describes what the music must CONVEY (emotional function), not a genre
- [ ] `music_placement` references scene labels from the Scene Breakdown
- [ ] `cut_points` cites specific script moments where cuts are critical
- [ ] `effects_direction` is either specific or explicitly "none"

### Component 9: On-screen Text *(if applicable)*
- [ ] Every text element has final, specific copy — no brackets, no placeholders
- [ ] Every element has a timing reference (scene or timestamp)
- [ ] Element IDs are sequential: TEXT-01, TEXT-02, etc.
- [ ] `brief_purpose` field explains which brief dimension each text element serves

### Component 10: Caption Draft *(if applicable)*
- [ ] Caption text is accurate to the Script — not summarized or paraphrased
- [ ] Caption blocks cover the complete script with no gaps
- [ ] `notes_for_publisher` is populated (or explicitly "none")

### Component 11: CTA
- [ ] `cta_text` is final copy — no placeholders
- [ ] `placement` matches `brief.cta_strategy.placement` exactly
- [ ] `delivery_direction` is specific to the emotional state the viewer is in at this moment (not generic)
- [ ] `friction_reduction_execution` explains how the brief's friction reduction strategy is executed in THESE SPECIFIC WORDS
- [ ] `brief_fidelity_note` documents how the CTA matches `brief.cta_strategy.desired_action` and `brief.cta_strategy.what_they_get`

---

## Checklist 5: Quality Gate Review

Run this checklist after component assembly, before delivery. This is the final gate checklist.

### Gate 1: Brief Fidelity
- [ ] All 10 brief dimensions are executed in the script
- [ ] The content angle is taken — not softened, not reframed
- [ ] The core message is one idea, and it is the same idea in the brief
- [ ] The hook type and concept match the brief exactly
- [ ] The retention mechanism from the brief is active in the script
- [ ] The story arc follows the brief's opening → development → tension → resolution
- [ ] Visual components match the brief's visual mood and pacing
- [ ] Emotional journey in the script matches the brief's specified progression
- [ ] Curiosity mechanism opens, sustains, and resolves as brief specifies
- [ ] CTA placement and desired action match the brief exactly

### Gate 2: Component Completeness
- [ ] All applicable components are present (referenced against the applicable component list logged at receipt)
- [ ] No component field contains a placeholder, "TBD", "[INSERT]", or equivalent
- [ ] No component field is empty
- [ ] All list fields have the minimum number of items specified in OUTPUTS.md

### Gate 3: Internal Consistency
- [ ] Hook text in Component 2 matches the Script in Component 1 exactly
- [ ] Scene count in Component 3 matches the Script
- [ ] Voiceover in Component 4 contains only narration (no stage directions or cues)
- [ ] Energy in Component 5 is consistent with Hook delivery direction in Component 2
- [ ] B-roll mood in Component 6 is consistent with Camera Notes mood in Component 7
- [ ] Editing rhythm in Component 8 is consistent with pacing in Component 5
- [ ] On-screen text excerpts in Component 9 match the Script in Component 1
- [ ] CTA text in Component 11 matches any CTA on-screen text in Component 9
- [ ] Duration estimates are internally consistent across Scene Breakdown, Voiceover, and Editing Notes

### Gate 4: Traceability
- [ ] Every creative decision in every component can be linked to a brief dimension (implicit or explicit)
- [ ] No component introduces a visual direction, emotional direction, or message not in the brief
- [ ] No on-screen text element introduces a second message

---

## Checklist 6: Delivery

Run this checklist immediately before and during delivery.

- [ ] `status` set to `complete` and `produced_at` timestamp recorded
- [ ] `applicable_components` list matches the components actually included in the package
- [ ] Full package delivered to Production Team
- [ ] Components 10 and 11 delivered to Publishing Department with note on full package availability
- [ ] Workflow Department notified: Script Package delivered, content item advancing
- [ ] Input log updated: `disposition: completed`, `script_package_ref` logged
- [ ] All delivery notifications logged with timestamps

---

## Checklist 7: Revision (when applicable)

Run this checklist when a revision request is received from the Production Team or Platform Director.

- [ ] Revision request received and logged with `received_at` timestamp
- [ ] Revision request is valid: identifies a specific component, documents a specific issue, does not ask for brief-dimension changes
- [ ] If invalid: decline documented in writing; escalation initiated if disputed
- [ ] If valid: acknowledgment sent with expected re-delivery date
- [ ] Revision number incremented on the package
- [ ] Only the component(s) specified in the revision request have been revised
- [ ] All quality gates re-run on the full package (not just the revised component)
- [ ] All gates passed before re-delivery
- [ ] Revised package delivered to all consumers
- [ ] All delivery notifications logged
