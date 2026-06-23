# Inputs — Creative Department

This file defines everything this department needs to begin and complete a Creative Brief. The Creative Department is primarily reactive — it responds to brief requests and editorial calendar signals. It does not initiate work without an input trigger.

---

## What Triggers This Department

| Trigger | Source | Description |
|---|---|---|
| Creative Brief Request | Workflow Department | A structured request from Workflow specifying a topic, required format, target audience direction (if known), and urgency tier. This is the primary trigger for reactive brief production. |
| Editorial Calendar Signal | Workflow Department | An upcoming content slot in the editorial calendar for which a Creative Brief is needed by a specified date. May arrive before a formal brief request, giving the Creative Department advance notice to begin research coordination. |
| Research Output — Proactive | Research Department | A proactive Trend Report or Idea Report delivered by the Research Department without a specific brief request. May trigger the Creative Department to develop a speculative brief for Workflow Department review. |
| Brief Return — Revision Request | Script Department | A Creative Brief returned by the Script Department with specific, documented feedback requesting revision of one or more dimensions. Triggers the brief revision workflow. |

---

## Required Inputs

### Input: Creative Brief Request

| Attribute | Value |
|---|---|
| **Source** | Workflow Department |
| **Format** | Structured request document |
| **Required Fields** | `request_id`, `topic`, `format`, `urgency_tier`, `submitted_at`, `research_refs` (at least one) |
| **Validation Rules** | All required fields present; `format` must be a valid content format enum; `urgency_tier` must be `standard`, `expedited`, or `urgent`; `research_refs` must reference at least one completed, `status: complete` research output from the Research Department |
| **Rejection Behavior** | If validation fails, return a structured rejection with the failed rule and resubmission guidance. See `SOPS.md` → SOP-01. |

**Creative Brief Request Schema:**
```
request_id:         string (assigned by Workflow Department)
topic:              string (the subject matter — specific, not a broad domain)
format:             enum [long_form_video | short_form_video | article |
                         newsletter | podcast | social_post]
urgency_tier:       enum [standard | expedited | urgent]
                    (SLAs per tier defined in WORKFLOW.md → Timing and SLAs)
audience_direction: string (optional — any audience constraints from editorial direction)
angle_constraints:  string (optional — any angles that have been ruled out editorially)
research_refs:      list of output_ids from Research Department (minimum: 1 required)
submitted_at:       ISO 8601 timestamp
due_date:           ISO 8601 date (optional — if absent, SLA applies by urgency tier)
notes:              string (optional — any additional context)
```

---

### Input: Research Output(s)

Research outputs are the raw material for every Creative Brief. The Creative Department does not develop briefs without research grounding. At least one completed Research Department output must be present for every dimension of the brief.

| Attribute | Value |
|---|---|
| **Source** | Research Department |
| **Format** | One or more completed research outputs: Research Brief, Trend Report, Idea Report, Technology Report, Framework Summary, or Competitive Analysis |
| **Required Fields** | `output_id`, `output_type`, `domain`, `status: complete`, `findings` (or equivalent), `sources`, `confidence` |
| **Validation Rules** | All referenced outputs must have `status: complete` (not draft, escalated, or rejected); outputs must not have expired per domain-specific currency standards (see Research Department `QUALITY_STANDARDS.md`); confidence must be at least `low` — speculative-only research cannot support a Creative Brief |
| **Rejection Behavior** | If research is insufficient to develop one or more creative dimensions, the department does not produce a partial brief. It identifies the gap, requests a supplementary Research Brief, and holds the work item until supplementary research is delivered. See `SOPS.md` → SOP-C02. |

---

### Input: Brief Return — Revision Request

| Attribute | Value |
|---|---|
| **Source** | Script Department |
| **Format** | Structured revision request |
| **Required Fields** | `original_brief_id`, `returned_by`, `dimensions_flagged` (list), `feedback_per_dimension`, `returned_at` |
| **Validation Rules** | Feedback must be specific and per-dimension — general feedback ("this doesn't feel right") is not actionable and is returned to Script Department for clarification (see `SOPS.md` → SOP-C03). `dimensions_flagged` must reference valid dimension names from the Creative Brief schema. |
| **Rejection Behavior** | Vague revision requests are returned to Script Department with a feedback clarification template. |

---

## Optional Inputs

| Input | Source | Effect If Absent |
|---|---|---|
| Audience direction from editorial | Workflow Department | The Creative Department defines the audience independently based on research signals and platform knowledge. |
| Angle constraints | Workflow Department | All angles are considered equally. The Creative Department selects the strongest without editorial constraint. |
| Competitive Analysis | Research Department | The angle exploration step proceeds without competitive landscape context. Risk of selecting a saturated angle; this risk is noted in the brief's `angle_rationale`. |
| Performance data from prior content | Publishing Department | The brief is developed without performance signal input. The Creative Department notes the absence and flags that the angle and hook directions have not been calibrated against historical performance. |
| Idea Report from Research Department | Research Department | Ideation is conducted independently by the Creative Department during angle exploration. |

---

## Input Validation Rules

1. **Research currency:** Research outputs must not have exceeded their domain-specific currency window (defined in Research Department `QUALITY_STANDARDS.md`). Stale research produces stale creative direction.
2. **Research completeness:** The research provided must cover the topic with enough depth to support a decision on every creative dimension. A single three-paragraph Research Brief may be insufficient for a long-form video brief; the Creative Department assesses and requests supplementary research if needed.
3. **Format validity:** The requested format must be one of the six defined content format enums.
4. **Research confidence floor:** Research outputs with confidence rated `speculative` across all findings cannot support a brief. At least one finding at `low` confidence or above is required. A brief built entirely on speculation would fail Gate 1 (Research Grounding).
5. **Topic specificity:** The `topic` field must be specific enough to be briefable. "Artificial Intelligence" is not a briefable topic. "How small business owners are using AI to replace their first hire" is.

---

## Input Failure Handling

The full procedure for each failure type is in `SOPS.md`. Summary:

| Failure Type | Behavior |
|---|---|
| Missing required field in request | Reject per SOP-01. Return structured error with field and resubmission guide. |
| Research outputs missing or not `status: complete` | Hold. Request supplementary research via SOP-C02. Do not begin brief. |
| Research confidence entirely `speculative` | Reject per SOP-01. Note that brief cannot be defensibly developed on speculative research alone. |
| Topic not specific enough to brief | Return to Workflow with topic clarification request. Hold until topic is refined. |
| Revision request is vague | Return to Script Department per SOP-C03 with clarification template. |

---

## Input Volume and Frequency

| Attribute | Value |
|---|---|
| **Expected volume** | 5–20 brief requests per week |
| **Peak volume** | Up to 30 requests per week during editorial planning cycles |
| **Revision requests** | Expected at < 5% of delivered briefs |
| **Queue discipline** | Priority-weighted: `urgent` > `expedited` > `standard`; within tier, FIFO |
| **Backlog behavior** | When queue exceeds 10 active briefs, new requests are queued. Workflow Department is notified of expected start dates for queued items. |
