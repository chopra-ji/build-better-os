# Standard Operating Procedures — Script Department

---

## SOP Index

| SOP ID | Name | Trigger |
|---|---|---|
| SOP-S01 | Brief Return — Unexecutable Dimension | A brief dimension cannot be executed as written |
| SOP-S02 | Script Package Revision | A delivered Script Package is returned with revision feedback |
| SOP-S03 | Brief Hold — Ambiguous Dimension | A brief dimension is ambiguous but not clearly unexecutable |
| SOP-S04 | SLA Breach Prevention | A script is at risk of missing its delivery target |
| SOP-S05 | SLA Breach Response | A script has missed its delivery target |
| SOP-S06 | Expedited and Urgent Request Handling | An expedited or urgent-tier request is received |
| SOP-S07 | Format Mismatch — Brief vs. Actual Content | The brief's format field does not match the actual content being produced |
| SOP-S08 | Supplementary Research Request | A script requires a specific data point or claim that the brief does not supply |
| SOP-S09 | Out-of-Scope Revision Request | A revision request asks the Script Department to change a brief-owned creative direction |
| SOP-S10 | New Content Format Onboarding | A new content format is introduced that is not covered by the current component matrix |
| SOP-S11 | Out-of-Authority Request | The Script Department receives a request outside its defined scope |

---

## SOP-S01: Brief Return — Unexecutable Dimension

**Trigger:** A Creative Brief dimension cannot be executed as written. Specifically:
- Hook concept is not specific enough to execute (describes a type, not a concept)
- Core message contains more than one idea
- Story arc resolution contradicts the core message
- Format and visual direction are incompatible
- A dimension references content that requires research the brief does not supply

**Not a trigger for this SOP:** A dimension that is ambiguous but potentially executable (use SOP-S03) or a dimension that the Script Department would have executed differently (that is not grounds for return).

### Procedure

1. Stop scripting. If scripting has begun, do not deliver a partial package.
2. Identify the specific dimension that cannot be executed and document exactly why.
3. Draft the return package per the Return Package Contents schema in INPUTS.md.
4. Deliver the return package to the Creative Department via the output channel.
5. Notify the Workflow Department: brief returned, content item on hold pending Creative Department revision.
6. Log: `disposition: returned`, `returned_at` timestamp, `return_reason` (dimension + issue).
7. Start the 48-hour response clock.

### Monitoring

At the 48-hour mark: if no response from Creative Department, escalate to the Platform Director with the return package and the elapsed time.

### Receiving the Revised Brief

When the revised brief arrives:
1. Run Checklist 1 (Brief Receipt and Validation) on the revised brief in full.
2. If the revision resolves the return condition, proceed with scripting.
3. If the revision does not resolve the return condition, return the brief again with the same SOP-S01 procedure. Log the second return.
4. If a second return is required: simultaneously escalate to the Platform Director. The content item requires cross-department intervention.

---

## SOP-S02: Script Package Revision

**Trigger:** A delivered Script Package is returned by the Production Team or Platform Director with documented feedback requesting revision to a specific component.

### Procedure

1. Receive the revision request. Confirm it is documented (not a verbal request).
2. Validate the revision request:
   - Does it identify a specific component by name? (Required)
   - Does it document a specific issue? (Required)
   - Does it ask for a change within the Script Department's authority? (Required — see SOP-S09 if not)
3. If valid: acknowledge receipt to the requester with the expected re-delivery date.
4. Log: `revision_received_at`, `revision_request_summary`, `expected_redelivery`.
5. Rework only the component(s) identified in the request. Do not rework components not referenced.
6. Run all quality gates on the full package (not just the revised component).
7. Increment `revision_number` on the package.
8. Deliver the revised package to all consumers (not just the requester).
9. Log: `revision_delivered_at`, `revised_components`.

### Limits

Maximum 2 post-delivery revisions. If a 3rd revision is requested:
1. Do not process it.
2. Log the request.
3. Escalate to the Platform Director with: the full revision history, the current package, and the new request.
4. The Platform Director determines whether a 3rd revision is warranted or whether the issue is structural.

---

## SOP-S03: Brief Hold — Ambiguous Dimension

**Trigger:** A brief dimension is interpretively ambiguous — it provides direction but not enough specificity to execute without guessing at the Creative Department's intent. This is distinct from an unexecutable dimension (SOP-S01 applies there).

**Examples of ambiguous (not unexecutable):**
- Hook concept states "open with a provocative question about X" — a question type is specified, but not a specific question or angle for the question
- Visual direction mood is "cinematic and intense" — directionally useful but open to multiple interpretations
- Retention strategy secondary hooks are generic ("remind viewers why this matters") without scene specificity

### Procedure

1. Document the ambiguous dimension in the Brief Comprehension Summary under `flags`.
2. Assess: can a defensible judgment call be made within the brief's direction? If yes, proceed with judgment documented.
3. If judgment would require guessing at intent: contact the Creative Department with a specific question. Do not ask for creative decisions — ask for clarification of the existing direction.
4. Log: `hold_started_at`, `dimension_flagged`, `clarification_request_sent`.
5. Start the 48-hour response clock.
6. If no response in 48 hours: escalate to the Platform Director.

**Clarification request format:**
```
clarification_request_id: string
brief_ref:                string
dimension:                string (which of the 10 dimensions)
ambiguity_description:    string (what is unclear)
specific_question:        string (the precise question — not "what did you mean?"
                                  but "did you intend [interpretation A] or [interpretation B]?")
```

---

## SOP-S04: SLA Breach Prevention

**Trigger:** At 50% of the SLA window remaining, the script is not in Step 5 (Quality Gate Review) or later.

| Tier | SLA | 50% mark |
|---|---|---|
| Standard | 3 business days | End of day 1 |
| Expedited | 1 business day | 4 business hours |
| Urgent | Same business day | 2 business hours |

### Procedure

1. Assess the current position in the workflow and the realistic time remaining.
2. If delivery within SLA is still achievable: no action required. Continue scripting.
3. If delivery within SLA is at risk:
   - Identify the specific delay cause (brief hold, ambiguous dimension, component rework, gate failure).
   - If the delay is caused by a brief hold or return that is waiting on the Creative Department: escalate to the Platform Director, as the SLA clock is paused but the overall content item timeline is affected.
   - If the delay is internal (scripting complexity, gate failure): notify the Workflow Department of the risk with a revised estimate.
4. Log all notifications.

---

## SOP-S05: SLA Breach Response

**Trigger:** A script has been delivered after its SLA deadline.

### Procedure

1. Complete and deliver the package — a delayed delivery is better than a non-delivery.
2. Log: `sla_breached: true`, `delivered_at`, `sla_target`, `breach_duration`.
3. Notify the Workflow Department of the breach and the actual delivery time.
4. Within 24 hours of delivery: document the breach cause. Breach causes are:
   - `brief_hold` — brief was returned or held pending Creative Department response
   - `ambiguity_hold` — a dimension clarification required a hold
   - `gate_failure` — quality gate failure required rework that extended the timeline
   - `scope_complexity` — the brief's format or creative complexity exceeded standard time estimates
   - `internal_error` — a scripting gap or process failure that is the Script Department's responsibility
5. Report breaches and causes to the Platform Director in the monthly quality cycle.

---

## SOP-S06: Expedited and Urgent Request Handling

**Trigger:** A brief arrives with an expedited or urgent urgency designation.

### Procedure

**Expedited (1 business day):**
1. Confirm the urgency designation is authorized (Workflow Department designation, not self-assigned by a requester).
2. Log receipt immediately and confirm the delivery target.
3. Begin Step 1 validation within 30 minutes of receipt.
4. No process steps are skipped — all six workflow steps run; all checklists run; all gates run.
5. Expedited means faster execution of the same process, not a reduced process.

**Urgent (same business day):**
1. Confirm Platform Director authorization.
2. Log receipt immediately and confirm the delivery target (typically EOD or a specific time).
3. Begin Step 1 validation immediately upon receipt.
4. If the brief has any validation issue that would trigger SOP-S01 or SOP-S03: escalate to the Platform Director immediately — there is no time for the standard 48-hour hold window.
5. Notify the Platform Director of the delivery time estimate before scripting begins.
6. All process steps run. Quality gates run. No exceptions.

---

## SOP-S07: Format Mismatch — Brief vs. Actual Content

**Trigger:** The brief's `format` field specifies one content format, but the actual content being produced is a different format (e.g., brief says `long_form_video` but the piece is a YouTube Short).

### Procedure

1. Do not assume the format — confirm with the requesting party (Workflow Department or Creative Department).
2. Document the discrepancy: `brief_format`, `actual_format`, `source_of_discrepancy`.
3. Request formal confirmation of the correct format. The format field in the brief is the authoritative source — it may not be changed informally.
4. If the format is being changed: the Creative Department must issue a brief revision with the corrected format field (increment `revision_number`). The Script Department does not proceed on the original brief with an informally-agreed different format.
5. Receive the revised brief. Run Checklist 1. Determine the new applicable component set.
6. Log the format change and the revised brief receipt.

---

## SOP-S08: Supplementary Research Request

**Trigger:** During scripting, a specific claim, data point, or quote needs to be included in the script. The Creative Brief cites a research reference but the Script Department needs the underlying research to script accurately (e.g., the exact number, the exact quote, the specific definition).

### Procedure

1. Identify the specific information needed and which brief dimension references it.
2. Check the knowledge vault for an existing entry that resolves the need.
3. If the vault entry is `status: active` and contains the specific information: use it. Log the vault entry reference.
4. If no vault entry resolves the need: submit a supplementary research request to the Research Department.

**Supplementary research request format:**
```
supp_request_id:        string
brief_ref:              string
script_package_ref:     string (in progress)
requested_at:           ISO 8601 timestamp
requesting_department:  script_department
information_needed:     string (specific — not "more info about X" but "the exact
                                statistic from [study] cited in research ref [ID]")
brief_dimension:        string (which dimension this information serves)
urgency:                enum [standard | expedited | urgent]
                        (must match the script's urgency tier)
```

5. If supplementary research will delay delivery beyond the SLA: notify the Workflow Department and Platform Director.
6. Do not include unverified claims in the script while waiting for research. Placeholder claims in a delivered package are a Gate 2 failure.

---

## SOP-S09: Out-of-Scope Revision Request

**Trigger:** A revision request is received from the Production Team, Platform Director, or any other party that asks the Script Department to change a brief-owned dimension — the content angle, core message, hook concept, story arc, audience, emotion, retention strategy, curiosity mechanism, visual direction, or CTA strategy.

### Procedure

1. Do not comply with the revision request.
2. Document the request: who requested, what was requested, which brief dimension it would change.
3. Respond to the requester in writing:
   - Acknowledge the feedback.
   - State clearly that the requested change is a creative direction decision owned by the Creative Department.
   - Explain that implementing it would require a formal brief revision (Creative Department issues a revised brief, revision_number incremented).
   - Do not offer an alternative — the Script Department does not make creative direction decisions.
4. If the requester accepts: escalate to the Creative Department or Workflow Department to initiate the formal brief revision process.
5. If the requester disputes the scope boundary: escalate to the Platform Director. The dispute is not resolved by the Script Department alone.
6. Log: `out_of_scope_request_received_at`, `requestor`, `dimension_affected`, `disposition`.

---

## SOP-S10: New Content Format Onboarding

**Trigger:** The Workflow Department or Platform Director introduces a new content format not currently in the format-component applicability matrix.

### Procedure

1. Receive formal notification of the new format from the Platform Director or Workflow Department.
2. Do not script for a new format without a documented component matrix. Proceeding without a defined component set creates an inconsistent package that cannot be quality-gated.
3. Develop a draft component matrix for the new format:
   - Identify which of the 11 components are applicable based on the format's production requirements.
   - Document why each non-applicable component is excluded.
   - Identify any format-specific variations in how applicable components are structured.
4. Submit the draft matrix to the Platform Director for review.
5. Upon approval: update OUTPUTS.md with the new format column.
6. Create a `knowledge/editing/` vault entry documenting the scripting standard for this format.
7. Update VERSION.md with a minor version increment (new format = new capability, not a mission change).
8. Notify the Creative Department: the new format is available for briefs.

---

## SOP-S11: Out-of-Authority Request

**Trigger:** The Script Department receives a request that falls outside its defined scope of authority. This includes:
- Requests to make creative direction decisions (angle, message, hook concept, etc.)
- Requests to conduct research
- Requests to make publishing decisions
- Requests to decide which topics or content items to prioritize
- Requests to approve content for publication
- Requests to manage production scheduling, casting, or equipment
- Requests to communicate creative feedback to the Creative Department on behalf of anyone other than the Script Department itself

### Procedure

1. Do not comply with the request.
2. Identify the correct department or authority for the requested action.
3. Respond to the requester:
   - Acknowledge the request.
   - State clearly that this is outside the Script Department's scope.
   - Direct the requester to the correct department.
4. If the request came from the Platform Director and represents an explicit scope expansion: document it and escalate back to the Platform Director for formal scope decision. Scope changes are not implemented informally.
5. Log: `out_of_authority_request_received_at`, `requestor`, `nature_of_request`, `directed_to`.

**Response template:**
```
This request is outside the Script Department's defined scope of authority.

The Script Department's scope covers: scripting within the creative architecture 
defined by the Creative Brief, producing all applicable Script Package components, 
and returning Creative Briefs when a specific dimension cannot be executed.

The action you have requested — [description of the request] — is owned by 
[correct department]. Please direct this request there.

If this represents a change to the Script Department's scope, please escalate 
to the Platform Director.
```
