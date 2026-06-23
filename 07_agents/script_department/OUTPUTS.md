# Outputs — Script Department

The Script Department produces one primary output: the **Script Package**. Every Script Package contains all applicable components for its content format. Components are not optional — if a component applies to the format, it must be present, populated, and specific.

---

## Format-Component Applicability Matrix

Before scripting begins, the applicable components for the content format are determined using this matrix. Every applicable component must be in the final package.

| Component | long_form_video | short_form_video | article | newsletter | podcast | social_post |
|---|---|---|---|---|---|---|
| 1. Script | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| 2. Hook | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| 3. Scene Breakdown | ✓ | ✓ | ✓ | ✓ | ✓ | — |
| 4. Voiceover | ✓ | ✓ | — | — | ✓ | — |
| 5. Talking Head Notes | ✓ | ✓ | — | — | — | ✓ |
| 6. B-roll Notes | ✓ | ✓ | — | — | — | — |
| 7. Camera Notes | ✓ | ✓ | — | — | — | ✓ |
| 8. Editing Notes | ✓ | ✓ | — | — | ✓ | — |
| 9. On-screen Text | ✓ | ✓ | — | — | — | ✓ |
| 10. Caption Draft | ✓ | ✓ | — | — | — | — |
| 11. CTA | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |

**Legend:** ✓ = required · — = not applicable (do not include)

*Note: Social posts using video require Camera Notes and Talking Head Notes. Social posts using text/image only require neither. The format field in the brief determines applicability; use the brief's format, not an assumption.*

---

## Primary Output: Script Package

| Attribute | Value |
|---|---|
| **Description** | A complete, multi-component production document derived from a single Creative Brief, sufficient for a production team to begin work without further creative clarification |
| **Format** | Structured document with typed components per this schema |
| **Consumer(s)** | Production Team (primary), Publishing Department (Component 10: Caption Draft, Component 11: CTA), Workflow Department (pipeline milestone) |
| **Delivery Method** | Output channel (logged, retrievable by output_id and trace_id) |
| **SLA** | Standard: 3 business days · Expedited: 1 business day · Urgent: same business day |
| **Quality Gates** | All gates in `QUALITY.md` |

---

## Package Metadata

All Script Packages carry the following metadata fields:

```
output_id:              string (generated)
output_type:            script_package
trace_id:               string (propagated from Creative Brief)
department_id:          script_department
version:                string (current department version)
produced_at:            ISO 8601 timestamp
status:                 enum [complete | draft | in_revision | escalated]
brief_ref:              string (output_id of the Creative Brief this package executes)
revision_number:        integer (0 for first delivery; incremented per revision)
format:                 enum [long_form_video | short_form_video | article |
                              newsletter | podcast | social_post]
applicable_components:  list of integers (component numbers included in this package)
word_count:             integer (total script word count)
estimated_runtime:      string (estimated total duration, e.g. "8:30–9:00")
```

---

## Component Schemas

### Component 1: Script *(Required — all formats)*

The complete, formatted script. Every word spoken or written in the final content. Structural markers included. No placeholder text anywhere.

```
component:              1
component_name:         script
brief_dimension_map:    [all 10 dimensions]

# Script fields
full_text:              string (the complete script with all dialogue, narration,
                                and structural markers — formatted per format conventions)
word_count:             integer
estimated_runtime:      string
scene_count:            integer
format_conventions:
  marker_style:         string (how scenes, sections, or beats are delimited in this script)
  speaker_labels:       boolean (whether multiple speakers are labeled)
  stage_directions:     boolean (whether on-camera action is indicated inline)
```

**Format conventions:**
- *long_form_video / short_form_video:* Scene markers (SCENE 1, HOOK, etc.), stage directions in [brackets], speaker labels if multiple voices
- *article / newsletter:* Section headers as H2/H3, no stage directions
- *podcast:* Speaker labels, [MUSIC] and [SFX] cues in brackets, section markers
- *social_post:* Caption text, no markers needed

**Non-negotiable:** The script executes the Core Message, Hook Direction, Story Arc, and CTA Strategy exactly as the brief specifies. No creative re-interpretation.

---

### Component 2: Hook *(Required — all formats)*

The opening sequence isolated from the full script, annotated, and analyzed. Enables the production team to understand the hook's intent and pacing independent of the full script.

```
component:              2
component_name:         hook
brief_dimension_map:    [hook_direction, emotion, curiosity_mechanism]

# Hook fields
hook_text:              string (the complete hook text, verbatim from the Script)
hook_type:              enum [question | statement | visual | contrast | story |
                              data | challenge | confession]
                        (must match brief's hook_direction.type)
duration_estimate:      string (estimated duration, e.g. "0:00–0:15")
word_count:             integer
brief_promise_executed: string (how this hook delivers on hook_direction.what_it_promises
                                — specific analysis, not a restatement of the brief field)
curiosity_gap_created:  string (what question or tension the hook opens that the viewer
                                needs the rest of the content to resolve)
delivery_direction:     string (how this hook should be performed or presented —
                                energy level, pacing, tone; specific to this hook)
production_note:        string (any production-specific consideration for the hook moment
                                — framing, text on screen, sound, or pacing)
```

**Non-negotiable:** `hook_type` must match `brief.hook_direction.type`. The hook concept must execute `brief.hook_direction.concept` — not a similar or adjacent concept.

---

### Component 3: Scene Breakdown *(Required — all formats except social_post)*

Numbered scenes with purpose, content summary, timing, and brief dimension mapping. The production team's navigation document for the full script.

```
component:              3
component_name:         scene_breakdown
brief_dimension_map:    [story_arc, retention_strategy, hook_direction, cta_strategy]

# Scene Breakdown fields
scenes:                 list of scene objects

# Per-scene object:
scene_number:           integer
scene_label:            string (e.g., "Hook", "Setup", "Tension Point", "Reveal", "CTA")
script_excerpt:         string (first line of this scene from the Script, for navigation)
purpose:                string (what this scene accomplishes in the story arc)
arc_function:           enum [opening | development | tension | resolution | cta | transition]
duration_estimate:      string (e.g., "0:45–1:00")
retention_mechanism:    string (how this scene keeps the viewer watching —
                                which secondary hook or mechanism is active here, if any)
brief_dimension:        string (which brief dimension this scene primarily executes)
```

---

### Component 4: Voiceover *(long_form_video, short_form_video, podcast)*

The narration track separated from all other script elements. Formatted specifically for a recording session — the talent reads this document, not the full Script.

```
component:              4
component_name:         voiceover
brief_dimension_map:    [emotion, target_audience, core_message]

# Voiceover fields
full_text:              string (narration only — no stage directions, no music cues,
                                no on-screen text references; pure spoken word)
word_count:             integer
estimated_duration:     string
pacing_notes:           string (overall pacing direction for the recording session —
                                where to slow down, where to accelerate, natural break points)
tone_direction:         string (vocal tone calibration — not vague adjectives,
                                but specific direction: "conversational, not authoritative;
                                pause after [X] for effect")
emphasis_words:         list of strings (words or phrases that should receive
                                vocal emphasis — affects meaning or retention)
recording_notes:        string (any session-specific direction: takes, retakes,
                                environmental notes, or recording sequence preferences)
```

---

### Component 5: Talking Head Notes *(long_form_video, short_form_video, social_post video)*

On-camera direction for the presenter or subject. Energy, pacing, eye contact, and emphasis guidance. The production team uses this alongside the Script to direct talent.

```
component:              5
component_name:         talking_head_notes
brief_dimension_map:    [emotion, target_audience, hook_direction]

# Talking Head Notes fields
energy_level:           enum [high | moderate_high | moderate | moderate_low | low]
energy_description:     string (what this energy level looks like in practice for this
                                specific piece — not a definition of the enum value)
pacing:                 enum [rapid | brisk | conversational | deliberate | slow]
pacing_description:     string (how pacing should shift across the piece —
                                where to speed up, where to slow down, and why)
eye_contact:            string (eye contact direction: straight to camera, off-camera
                                interview style, shifting — and when each applies)
emphasis_moments:       list of strings (specific moments in the script where
                                delivery emphasis is critical — scene or line references)
authenticity_notes:     string (what makes the on-camera performance feel genuine
                                for this specific piece — calibrated to the brief's emotion
                                and audience)
wardrobe_color_note:    string (any color/wardrobe direction relevant to the visual
                                mood in the brief — or "none" if not applicable)
```

---

### Component 6: B-roll Notes *(long_form_video, short_form_video)*

Visual coverage needed for each script section. What footage must exist for the editor to assemble this piece. Specific enough that the production team knows what to capture; not so prescriptive that it overrides on-set judgment.

```
component:              6
component_name:         broll_notes
brief_dimension_map:    [visual_direction, story_arc, emotion]

# B-roll Notes fields
sections:               list of b-roll section objects

# Per-section object:
section_ref:            string (scene number or label from Scene Breakdown)
coverage_description:   string (what this B-roll footage must show or convey —
                                described as intent, not as a shot list; e.g.,
                                "footage that shows the scale of the problem, not the solution"
                                rather than "wide shot of empty warehouse")
mood_requirement:       string (the visual mood this footage must carry, consistent
                                with brief.visual_direction.mood)
duration_needed:        string (estimated seconds of coverage needed for this section)
priority:               enum [essential | preferred | optional]
                        (essential = no alternative; preferred = strong default; optional = nice to have)
what_to_avoid:          list of strings (visual approaches that would contradict
                                the mood or undermine the message for this section —
                                propagated from brief.visual_direction.what_to_avoid
                                with section-specific additions)
```

---

### Component 7: Camera Notes *(long_form_video, short_form_video, social_post video)*

Technical framing and movement direction per scene. Bridges the creative visual direction in the brief to specific production decisions.

```
component:              7
component_name:         camera_notes
brief_dimension_map:    [visual_direction, emotion, story_arc]

# Camera Notes fields
scenes:                 list of camera direction objects

# Per-scene object:
scene_ref:              string (scene number or label from Scene Breakdown)
framing:                string (primary framing for this scene: medium close-up,
                                wide, over-shoulder, etc. — with rationale tied to
                                the brief's visual direction, not just production preference)
movement:               string (camera movement direction: static, slow push-in,
                                handheld, etc. — and why this movement serves this scene)
depth_of_field:         string (shallow, deep, or specific direction — and what it
                                must convey in this scene)
lighting_note:          string (any lighting direction relevant to the scene's
                                emotional requirement — or "standard" if no special direction)
transition_out:         string (how this scene transitions to the next — cut, dissolve,
                                or specific transition direction)
```

---

### Component 8: Editing Notes *(long_form_video, short_form_video, podcast)*

Post-production direction for the editor. Cut rhythm, pacing targets, music direction, and effects. The editor should not need to guess the intended feel of the finished piece.

```
component:              8
component_name:         editing_notes
brief_dimension_map:    [visual_direction, retention_strategy, emotion]

# Editing Notes fields
overall_rhythm:         enum [fast_cut | rhythmic | breathing | slow]
rhythm_description:     string (how the overall rhythm should feel and where
                                it should accelerate or decelerate across the runtime)
music_direction:        string (what the music must do emotionally — not a genre
                                label, but what it must convey; e.g., "builds tension
                                through the development section, drops to near-silence
                                at the reveal, then swells into the CTA")
music_placement:        string (where music enters, exits, and shifts — referenced
                                to scene labels from the Scene Breakdown)
cut_points:             list of strings (specific moments in the script where the
                                cut matters most to the piece's impact — referenced
                                to scene or line)
pacing_targets:         list of objects (scene_ref + target_duration pairs, where
                                timing is critical to the piece's retention)
effects_direction:      string (any graphics, transitions, text animations, or
                                sound effects direction — or "none" if not applicable)
color_direction:        string (color grading direction tied to the brief's
                                visual_direction.mood — or "standard" if not specified)
```

---

### Component 9: On-screen Text *(long_form_video, short_form_video, social_post)*

Every piece of text that appears on screen: titles, callouts, lower thirds, graphics text, and caption overlays. All text is specific and final — no placeholders.

```
component:              9
component_name:         onscreen_text
brief_dimension_map:    [core_message, hook_direction, cta_strategy]

# On-screen Text fields
elements:               list of text element objects

# Per-text-element object:
element_id:             string (sequential: TEXT-01, TEXT-02, etc.)
text_content:           string (the exact text — no brackets, no placeholders,
                                no "[INSERT X]"; the final, specific text)
element_type:           enum [title | lower_third | callout | graphic_text |
                              caption_overlay | cta_text | data_label]
timing:                 string (when this element appears: scene reference,
                                or timestamp range)
duration_on_screen:     string (how long the element stays on screen, in seconds
                                or a description like "until end of scene")
style_note:             string (any specific style direction for this element —
                                or "standard" if default brand style applies)
brief_purpose:          string (why this text element is in the script —
                                what brief dimension it serves)
```

---

### Component 10: Caption Draft *(long_form_video, short_form_video)*

Subtitle and caption text for the complete piece, formatted for upload to the publishing platform. This component is delivered to the Publishing Department for pre-publication preparation.

```
component:              10
component_name:         caption_draft
brief_dimension_map:    [script (derived from)]

# Caption Draft fields
format:                 enum [srt | vtt | plain_text]
caption_blocks:         list of caption block objects
total_blocks:           integer
notes_for_publisher:    string (any formatting, platform-specific, or timing
                                notes the Publishing Department needs to process
                                this caption file correctly)

# Per-caption-block object:
block_number:           integer
timecode_in:            string (HH:MM:SS,mmm format)
timecode_out:           string (HH:MM:SS,mmm format)
text:                   string (the caption text for this block — accurate to
                                the script; not summarized, not paraphrased)
```

**Note:** Caption timecodes are estimated at scripting time based on the word count and pacing direction in the Script. Final timecodes are adjusted by the Publishing Department after the video is timed in post-production. The Script Department delivers the text content and approximate timing; the Publishing Department finalizes the sync.

---

### Component 11: CTA *(Required — all formats)*

The call-to-action execution: exact wording, timing, delivery direction, and friction reduction. Derived directly from the CTA Strategy in the Creative Brief.

```
component:              11
component_name:         cta
brief_dimension_map:    [cta_strategy, emotion]

# CTA fields
cta_text:               string (the exact words of the call-to-action — no
                                placeholders, no "insert CTA here"; the final script)
placement:              enum [end_only | woven_throughout | mid_and_end | implied_no_explicit]
                        (must match brief.cta_strategy.placement)
timing:                 string (when in the piece the CTA lands — scene reference
                                or timestamp)
delivery_direction:     string (how the CTA should be performed: energy, pacing,
                                directness; calibrated to the emotional state the
                                viewer is in at this moment per the brief)
friction_reduction_execution: string (how the brief's friction_reduction strategy
                                is executed in these specific words and this delivery —
                                not a restatement of the brief field but its execution)
secondary_cta:          string (any supporting action adjacent to the primary CTA,
                                if applicable — or "none")
cta_on_screen:          string (the on-screen version of the CTA, if different
                                from spoken — or "same as spoken")
brief_fidelity_note:    string (how this CTA execution matches
                                brief.cta_strategy.desired_action and
                                brief.cta_strategy.what_they_get — a self-check,
                                not a summary)
```

---

## Operational Outputs

| Output | Description | Consumer |
|---|---|---|
| Activity log entry | Structured record of every Script Package processed: brief_ref, components completed, gate results, delivery timestamp | Platform observability layer |
| Brief return package | Structured return notice when a brief dimension cannot be executed (see INPUTS.md) | Creative Department, Workflow Department |
| Revision acknowledgment | Structured confirmation when a revision request is received, with expected re-delivery date | Production Team or Platform Director |
| Escalation notice | Structured notification when escalation criteria are met | Platform Director |

---

## Output Guarantees

This department guarantees:
- Every applicable component is present and populated with specific, non-placeholder content.
- Every script decision is traceable to a brief dimension.
- The hook executes the brief's hook concept — not a related or improved concept.
- The core message is delivered as specified — not reinterpreted, diluted, or expanded.
- The CTA placement matches the brief's CTA strategy placement field exactly.
- All quality gates are passed before delivery.
- Every Script Package is logged and retrievable by `output_id` and `trace_id`.
- Revised packages carry an incremented `revision_number` and a documented revision note.

This department does NOT guarantee:
- That the content produced from the Script Package will perform at any metric — performance is determined by production quality, distribution, and audience behavior, all outside the Script Department's authority.
- That the creative direction in the brief is optimal — the Script Department executes briefs, it does not evaluate them.
