# Outputs — Creative Department

The Creative Department produces one primary output type: the **Creative Brief**. Every brief defines the complete creative architecture for a single piece of content across ten dimensions. There are no freeform outputs. Every deliverable conforms to this schema.

---

## Primary Output: Creative Brief

| Attribute | Value |
|---|---|
| **Description** | A structured document defining the complete creative architecture for a piece of content — what story to tell, how to tell it, and why the audience should care. The Creative Brief is the Script Department's primary instruction document. |
| **Format** | Structured document conforming to the schema below |
| **Consumer(s)** | Script Department (primary), Workflow Department (pipeline tracking), Publishing Department (channel strategy metadata) |
| **Delivery Method** | Delivered to Script Department and Workflow Department via output channel |
| **SLA** | Standard: 5 business days · Expedited: 2 business days · Urgent: same business day |
| **Quality Gate** | All six gates in `QUALITY_STANDARDS.md` |

---

## Creative Brief Schema

```
# Output Metadata
output_id:              string
output_type:            creative_brief
trace_id:               string (propagated from the originating request)
department_id:          creative_department
version:                string (current department version)
produced_at:            ISO 8601 timestamp
status:                 enum [complete | draft | escalated | rejected]
request_ref:            string (the request_id from the originating brief request)
revision_number:        integer (0 for first delivery; incremented per revision)

# Source Context
source_research_refs:   list of output_ids (all research outputs used in this brief)
topic:                  string (verbatim from request)
format:                 enum [long_form_video | short_form_video | article |
                              newsletter | podcast | social_post]

# ─────────────────────────────────────────────
# DIMENSION 1: Content Angle
# ─────────────────────────────────────────────
content_angle:
  statement:            string (the specific angle — a position on the topic, not the topic
                                itself; must be a declarative or directional phrase)
  rationale:            string (why this angle over all other possible angles on this topic;
                                must cite a specific finding from source_research_refs)
  differentiation:      string (what makes this angle distinctive relative to what already
                                exists in the content landscape on this topic)
  rejected_angles:      list of strings (at least 2 other angles considered and why each
                                was rejected — the minimum floor; workflow generates at least 5
                                angles and selects 1, so at least 4 are rejected. Documenting
                                2 is the required minimum; more may be included. The minimum
                                exists because documenting all rejected angles would create
                                more audit overhead than value at this stage of the platform.)

# ─────────────────────────────────────────────
# DIMENSION 2: Audience
# ─────────────────────────────────────────────
target_audience:
  primary_description:  string (specific — not a demographic bucket; describes a person:
                                what they do, what they believe, what they want)
  psychographic:        string (what this person believes, values, or struggles with that
                                makes this specific content relevant to them right now)
  awareness_level:      enum [unaware | problem_aware | solution_aware | brand_aware]
                        (their current relationship to the topic before seeing this content)
  content_they_consume: list of strings (examples of content this person already watches,
                                reads, or listens to — for calibration, not for copying)
  why_this_content_now: string (what makes this topic relevant to this person at this
                                moment — must be grounded in research)

# ─────────────────────────────────────────────
# DIMENSION 3: Core Message
# ─────────────────────────────────────────────
core_message:
  statement:            string (ONE sentence. The single idea the viewer should leave with.
                                If it cannot be stated in one sentence, it is not yet
                                a message. No exceptions.)
  proof:                string (what in the research makes this message credible and true)
  what_it_is_not:       string (a common misunderstanding or adjacent idea this message
                                is explicitly not saying — prevents ambiguity in execution)

# ─────────────────────────────────────────────
# DIMENSION 4: Hook Direction
# ─────────────────────────────────────────────
hook_direction:
  type:                 enum [question | statement | visual | contrast | story |
                              data | challenge | confession]
  concept:              string (the specific hook concept — what happens or what is said
                                in the first 3–5 seconds; specific enough to execute)
  why_it_works:         string (why this hook will stop this specific audience from
                                scrolling; must reference the audience definition)
  what_it_promises:     string (what implicit promise the hook makes to the viewer about
                                what they will get if they keep watching)

# ─────────────────────────────────────────────
# DIMENSION 5: Retention Strategy
# ─────────────────────────────────────────────
retention_strategy:
  mechanism:            enum [open_loop | escalating_stakes | transformation_journey |
                              episodic_revelation | contrarian_build | how_it_works |
                              before_and_after | pattern_interrupts]
  description:          string (how this mechanism is specifically executed in this piece —
                                not a definition of the mechanism, but how it manifests here)
  payoff_location:      enum [early | mid | late | end | distributed]
                        (where the primary payoff lands relative to the piece's runtime)
  secondary_hooks:      list of strings (2–4 internal moments that re-engage the viewer
                                mid-piece; specific, not generic)

# ─────────────────────────────────────────────
# DIMENSION 6: Story Arc
# ─────────────────────────────────────────────
story_arc:
  structure:            enum [problem_solution | before_after_bridge | heros_journey |
                              thesis_antithesis_synthesis | case_study | listicle_with_spine |
                              mystery_reveal | contrarian_then_reframe]
  opening:              string (how the piece begins — the situation or premise established)
  development:          string (how the middle unfolds — what the viewer moves through)
  tension_point:        string (the moment of maximum tension, uncertainty, or stakes —
                                where the viewer most wants to know what happens next)
  resolution:           string (how the piece ends — what has changed or been established)
  message_integration:  string (how the story arc serves the core message — where in the
                                arc the message lands and why that placement works)

# ─────────────────────────────────────────────
# DIMENSION 7: Visual Direction
# ─────────────────────────────────────────────
visual_direction:
  mood:                 string (the aesthetic and emotional tone — the feeling of the visuals,
                                not a description of shots)
  pacing:               enum [slow_burn | steady | dynamic | rapid | variable]
  reference_aesthetic:  list of strings (content, creators, or works whose visual language
                                is directionally relevant — for calibration, not copying)
  key_visual_moments:   list of strings (2–5 moments in the piece where the visual execution
                                must carry meaning, not just illustrate; described as intent,
                                not production instruction)
  what_to_avoid:        list of strings (visual approaches that would contradict the mood
                                or undermine the message)

# ─────────────────────────────────────────────
# DIMENSION 8: Emotion
# ─────────────────────────────────────────────
emotion:
  primary:              enum [curiosity | inspiration | validation | surprise | urgency |
                              humor | empathy | admiration | aspiration | discomfort |
                              relief | wonder]
  secondary:            enum [same list as primary]
  emotional_journey:    string (how the viewer's emotional state should shift from the
                                opening to the close — a progression, not a static target)
  emotional_payoff:     string (the dominant feeling the viewer should have in the moment
                                after the piece ends)
  research_basis:       string (what in the research or audience definition supports this
                                emotional direction)

# ─────────────────────────────────────────────
# DIMENSION 9: Curiosity Mechanism
# ─────────────────────────────────────────────
curiosity_mechanism:
  type:                 enum [knowledge_gap | mystery | contrarian_claim |
                              personal_relevance | surprising_data | future_implication |
                              identity_challenge]
  creation:             string (specifically how curiosity is created at or near the opening)
  sustain:              string (how curiosity is maintained through the middle — what keeps
                                the viewer from feeling the question has been answered too soon)
  resolution:           enum [fully_resolved | partially_resolved | deliberately_open]
  resolution_description: string (how and where curiosity is resolved, or why it is
                                intentionally left open and what effect that creates)

# ─────────────────────────────────────────────
# DIMENSION 10: CTA Strategy
# ─────────────────────────────────────────────
cta_strategy:
  desired_action:       string (specific — not "subscribe" but what they're subscribing for
                                and why now; not "buy" but what outcome they're buying toward)
  placement:            enum [end_only | woven_throughout | mid_and_end | implied_no_explicit]
  motivation:           string (what emotional or rational state the viewer is in at the CTA
                                moment that makes the action feel natural)
  friction_reduction:   string (what makes the action feel easy, low-risk, or obvious)
  what_they_get:        string (the specific value the viewer receives by taking the action)
```

---

## Operational Outputs

| Output | Description | Consumer |
|---|---|---|
| Activity log entry | Structured record of every work item processed: inputs, decisions, gate results, delivery | Platform observability layer |
| Escalation notice | Structured notification when escalation criteria are met | Platform Director |
| Supplementary research request | Structured request to Research Department when existing research is insufficient for a dimension | Research Department |
| Brief revision | Updated Creative Brief when returned by Script Department with documented feedback | Script Department, Workflow Department |

---

## Output Metadata

All Creative Briefs carry the following metadata fields:

| Field | Type | Description |
|---|---|---|
| `trace_id` | string | Propagated from the originating request. Enables tracing from brief back to research back to the original trigger. |
| `department_id` | string | `creative_department` |
| `version` | string | Version of this department's operating design at time of production. |
| `produced_at` | ISO 8601 timestamp | When the brief was completed. |
| `request_ref` | string | The `request_id` from the originating brief request. |
| `status` | enum | `complete`, `draft`, `escalated`, or `rejected`. |
| `revision_number` | integer | 0 for first delivery. Incremented each time the brief is revised and re-delivered. |

---

## Output Guarantees

This department guarantees:
- Every creative dimension is populated — no field is left empty or approximate.
- Every creative decision cites a source in `source_research_refs`.
- The core message is one sentence.
- At least two rejected angles are documented in `content_angle.rejected_angles`.
- All quality gates are passed before delivery.
- Every brief is logged and retrievable by `output_id` and `trace_id`.
- Revised briefs carry an incremented `revision_number` and a documented revision note.

This department does NOT guarantee:
- That the content produced from the brief will perform at any specific level — brief quality is separable from production quality and distribution reach.
- That the angle selected is the only strong angle — it is the strongest given the research available at the time of briefing.
