# Inputs — Content Production Workflow

This file defines what each stage requires to begin. A stage that does not receive a valid input must reject it and return a structured error to the sender rather than proceeding with incomplete information.

---

## Stage 1 — Idea Record

**Submitted by:** Founder  
**Received by:** Research Department (Stage 2)

The Idea Record is the workflow's trigger document. It must be specific enough for the Research Department to understand what question to answer, but it does not need to be a polished brief.

### Required Fields

```
idea_id:          string (assigned at creation)
created_at:       ISO 8601 timestamp
submitted_by:     string (Founder name or identifier)

core_idea:        string (one sentence — what is this content about?)
domain:           enum [technology | ai | business | marketing | psychology |
                        creator_economy | startups | books | frameworks | productivity]
target_audience:  string (who is this for — be specific)
urgency:          enum [standard | expedited | urgent]

angles:           list of strings (optional — specific angles or questions to explore)
constraints:      list of strings (optional — things this content must or must not do)
context:          string (optional — background that helps the Research Department)
```

### Validation Rules
- `core_idea` must be a single sentence. Multi-sentence entries are returned for tightening.
- `domain` must match one of the Research Department's ten monitored domains.
- `target_audience` must name a specific person or type, not a generic label ("founders building their first team," not "business people").
- `urgency` must be explicitly set. No default is assumed.

### Rejection
An Idea Record that fails validation is returned to the Founder with the specific field(s) that failed and the correction required. The Research Department does not begin work on a rejected Idea Record.

---

## Stage 2 — Research Output

**Submitted by:** Research Department  
**Received by:** Creative Department (Stage 3)

The Research Output is one of the Research Department's eight output types. For most content ideas, this is a Research Brief. The Creative Department accepts any valid Research Department output type.

### Required Fields (all output types)
All Research Department outputs carry standard metadata:

```
output_id:        string
output_type:      string
request_id:       string (traces back to the Idea Record idea_id)
trace_id:         string
department_id:    research_department
produced_at:      ISO 8601 timestamp
status:           complete
confidence:       enum [high | medium | low]
```

Full output schemas are in `07_agents/research_department/OUTPUTS.md`.

### Validation Rules
- `status` must be `complete`. Partial or escalated outputs are not accepted.
- `confidence` must be `high` or `medium`. A `low` confidence Research Output is not accepted as a basis for a Creative Brief without Platform Director approval.
- `request_id` must trace back to a valid Idea Record.

### Rejection
A Research Output that fails validation is returned to the Research Department with the specific failure and required action. The Creative Department does not begin work on a rejected Research Output.

---

## Stage 3 — Creative Brief

**Submitted by:** Creative Department  
**Received by:** Script Department (Stage 4)

The Creative Brief is the contract between the Creative Department and the Script Department. It defines all ten creative dimensions of the content piece.

### Required Fields
All ten dimensions must be populated. See `07_agents/creative_department/OUTPUTS.md` for the complete field-level schema.

```
brief_id:             string
request_id:           string (traces back to the Idea Record)
trace_id:             string
department_id:        creative_department
produced_at:          ISO 8601 timestamp
status:               complete

content_angle:        object (fully populated)
audience:             object (fully populated)
core_message:         object (fully populated)
hook_direction:       object (fully populated)
retention_strategy:   object (fully populated)
story_arc:            object (fully populated)
visual_direction:     object (fully populated)
emotion:              object (fully populated)
curiosity_mechanism:  object (fully populated)
cta_strategy:         object (fully populated)
```

### Validation Rules
- All ten dimension objects must be present and non-empty.
- `status` must be `complete`.
- `request_id` must trace back to the originating Idea Record.

### Rejection
A Creative Brief with any missing dimension or incomplete field is returned to the Creative Department before the Script Department begins work.

---

## Stage 4 — Script Package

**Submitted by:** Script Department  
**Received by:** Creator Engine (Stage 5)

The Script Package is the Script Department's production document. It must contain all components required by the Creator Engine for intake.

### Required Fields (Creator Engine intake minimum)
```
script_package_id:    string
brief_id:             string (traces back to the Creative Brief)
trace_id:             string
department_id:        script_department
produced_at:          ISO 8601 timestamp
status:               complete

script:               string (full spoken content — required)
hook:                 string (opening line(s) designated as the hook — required)
cta:                  string (call to action — required)
on_screen_text:       list (may be empty if not applicable)
caption_draft:        string (may be empty if not applicable)
```

Additional components (scene breakdown, voiceover notes, b-roll notes, etc.) are required per the format-component applicability matrix in `07_agents/script_department/OUTPUTS.md`.

### Validation Rules
- `script`, `hook`, and `cta` must all be present and non-empty.
- `status` must be `complete`.
- `brief_id` must trace back to a valid Creative Brief.
- Spoken word count must be ≥ 80 words. Scripts under 80 words are flagged before Creator Engine intake for Founder review (potential under-brief).

### Rejection
A Script Package missing required fields is rejected at Creator Engine intake before Stage 5 begins. The rejection is returned to the Script Department with the specific missing fields identified.

---

## Stage 5 — Final Production Script (Creator Engine Output)

**Submitted by:** Creator Engine  
**Received by:** Stage 6 (routing to Founder Review)

The Final Production Script is the Creator Engine's approved output. It must carry `status: approved`.

### Required Fields
```
engine_run_id:        string
input_script_id:      string (traces back to the Script Package)
produced_at:          ISO 8601 timestamp
status:               approved

final_script:         string
runtime_estimate:     string
word_count:           integer (110–140 for approved outputs)

dimension_scores:     object (all 8 dimensions scored, all ≥ 7)
aggregate_score:      integer (≥ 56)

change_log:           list (all modifications made during the run)
production_notes:     string
caption:              string (finalized)
```

Full schema in `08_creator_engine/ARCHITECTURE.md`.

### Validation Rules
- `status` must be `approved`. Scripts with `escalated` or `rejected` status are not routed to Founder Review.
- All eight dimension scores must be ≥ 7.
- `aggregate_score` must be ≥ 56.
- `runtime_estimate` must reflect 45–60 seconds.

---

## Stage 7 — Founder Review Decision

**Submitted by:** Founder  
**Received by:** Stage 8 (Production) on approval, or upstream stage on revision/rejection

### Approval (advances to Stage 8)
```
review_id:        string
workflow_run_id:  string
reviewed_by:      string (Founder)
reviewed_at:      ISO 8601 timestamp
decision:         approved
notes:            string (optional — any production guidance)
```

### Revision Request (routed upstream)
```
review_id:        string
workflow_run_id:  string
reviewed_by:      string
reviewed_at:      ISO 8601 timestamp
decision:         revision_requested
revision_type:    enum [factual_error | wrong_angle | voice_mismatch | wrong_premise]
description:      string (specific, actionable — what is wrong and what is needed)
route_to:         enum [script_department | creative_department | stage_1 | cancel]
```

### Rejection (idea cancelled or returned to Stage 1)
```
review_id:        string
workflow_run_id:  string
reviewed_by:      string
reviewed_at:      ISO 8601 timestamp
decision:         rejected
reason:           string
disposition:      enum [cancelled | return_to_stage_1]
```

### Validation Rules
- Every Founder Review must produce one of the three structured decisions above.
- A `revision_requested` decision must include a `description` and a `route_to`.
- A `rejected` decision must include a `reason` and a `disposition`.

---

## Stage 8 — Production Package

**Submitted by:** Creator  
**Received by:** Stage 9 (Publishing)

The Production Package is the output of the recording and editing stage.

### Required Fields
```
production_id:    string
workflow_run_id:  string
produced_by:      string
produced_at:      ISO 8601 timestamp

video_file:       string (file path or asset reference)
caption:          string (final caption, taken from Final Production Script)
metadata:
  content_topic:  string
  domain:         string
  script_version: string (traces back to Final Production Script)

deviations:       list of strings (any changes from the approved script; empty if none)
```

### Validation Rules
- `video_file` must reference an accessible file.
- `caption` must not be empty.
- `deviations` must be present (empty list is valid; omitted field is not).
- Any `deviations` entry that touches the hook, a key claim, or the CTA requires a new Founder Review before publishing.
