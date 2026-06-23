# Standard Operating Procedures — Creative Department

SOPs cover what the standard workflow does not: exceptions, edge cases, escalations, and the specific situations that require a defined response rather than improvisation. If a situation arises without a documented SOP, the correct response is escalation.

---

## SOP Index

| SOP | Trigger | Summary |
|---|---|---|
| SOP-01 | Input validation failure | How to handle malformed, incomplete, or unauthorized requests |
| SOP-02 | Escalation criteria met | How to execute a proper escalation |
| SOP-03 | Quality gate failure (rework) | How to manage the rework loop |
| SOP-04 | Quality gate failure (rework maximum reached) | When rework is exhausted |
| SOP-05 | Output delivery failure | How to handle consumer unavailability |
| SOP-06 | SLA breach | How to respond to missed or imminent SLA deadlines |
| SOP-07 | Tool or knowledge access outage | How to operate when a required vault domain or system is unavailable |
| SOP-08 | Duplicate brief request | How to handle a request that matches a prior brief |
| SOP-09 | Rejection procedure | How to formally reject and close a work item |
| SOP-10 | Department onboarding | How to activate this department for the first time |
| SOP-11 | Out-of-authority request | How to respond when asked to act outside defined scope |
| SOP-C01 | Brief revision process | The formal process for revising a returned Creative Brief |
| SOP-C02 | Supplementary research request | How to request additional research when inputs are insufficient |
| SOP-C03 | Vague revision feedback | How to handle Script Department feedback that is not specific enough to act on |
| SOP-C04 | Angle exhaustion | How to respond when no viable angle can be identified |
| SOP-C05 | Message cannot be singularized | How to respond when core message distillation fails after multiple attempts |
| SOP-C06 | Editorial override conflict | How to handle a situation where editorial direction conflicts with research-grounded creative decisions |

---

## SOP-01: Input Validation Failure

**Trigger:** An incoming brief request fails validation checks defined in `INPUTS.md`.

**Procedure:**
1. Log the failure: work item ID, source, timestamp, which validation rules failed.
2. Return a structured rejection to Workflow Department:
   - `error_code`: `INPUT_VALIDATION_FAILURE`
   - `work_item_id`: generated ID
   - `failed_rules`: list with explanations
   - `resubmission_guide`: specific corrections needed
3. Do not begin creative work.
4. Close work item with status `rejected`.

**Common failures and guidance:**
- **Research refs missing or incomplete:** Specify which refs are missing or invalid. Provide the research output ID format.
- **Topic too broad:** Return with an example of how to narrow the topic to a briefable level.
- **Format not in valid enums:** Return the list of six valid formats.
- **Research outputs not `status: complete`:** Specify which outputs are pending and suggest the requesting department check Research Department queue status.

---

## SOP-02: Escalation Procedure

**Trigger:** Any escalation criterion defined in `WORKFLOW.md` or `QUALITY_STANDARDS.md` is met.

**Procedure:**
1. Stop processing the current work item.
2. Record the escalation trigger: which criterion was met, current workflow step, full working context.
3. Construct escalation notice:
   - `escalation_type`: [see types below]
   - `work_item_id` and `trace_id`
   - `trigger_criterion`: what specifically triggered escalation
   - `context_summary`: current state; what has been done; what is blocked
   - `recommended_action`: the department's recommendation if one exists
4. Deliver notice to Platform Director.
5. Notify Workflow Department with a brief explanation and revised timeline estimate.
6. Update work item status to `escalated`.
7. Write activity log entry.
8. Await direction. Do not re-process without explicit instruction.

**Escalation types:**
- `RESEARCH_INSUFFICIENT`: Research does not provide enough coverage to develop a defensible brief.
- `ANGLE_EXHAUSTION`: No viable, differentiated angle can be identified from the available research.
- `MESSAGE_CANNOT_SINGULARIZE`: Core message cannot be reduced to one idea — research or topic requires narrowing.
- `AUDIENCE_UNDEFINABLE`: Topic is too broad to assign to a specific audience without editorial direction.
- `QUALITY_REWORK_EXCEEDED`: Rework maximum reached; brief cannot pass quality gates without escalated intervention.
- `DIMENSIONAL_INCONSISTENCY_STRUCTURAL`: Dimensional inconsistency is structural, not a drafting error.
- `EDITORIAL_OVERRIDE_CONFLICT`: See SOP-C06.
- `SLA_BREACH`: Processing time exceeded or will exceed SLA.
- `AUTHORITY_BOUNDARY_VIOLATION`: See SOP-11.

---

## SOP-03: Quality Gate Failure — Rework

**Trigger:** A quality gate fails during Workflow Step 8, rework attempt count is below maximum (2).

**Procedure:**
1. Record gate failure: gate number, specific checks failed, observed values.
2. Increment rework attempt counter.
3. Return to the relevant workflow step with failure context:
   - Gate 1 (Research Grounding): return to Step 2 or the specific dimension in Step 6.
   - Gate 2 (Message Singularity): return to Step 5.
   - Gate 3 (Audience Specificity): return to Step 4.
   - Gate 4 (Hook-Retention Coherence): return to Steps 6b–6d.
   - Gate 5 (Dimensional Consistency): return to the first inconsistent dimension in Step 6.
   - Gate 6 (Traceability): return to Step 7 for metadata issues; escalate immediately for systemic logging failures.
4. After re-processing, re-run all six gates from Gate 1.

---

## SOP-04: Quality Gate Failure — Rework Maximum Reached

**Trigger:** A quality gate fails and the rework attempt count has reached 2.

**Procedure:**
1. Do not attempt further rework.
2. Compile the full rework history: all gate failures, failure contexts, and brief state after each attempt.
3. Escalate per SOP-02 with `escalation_type: QUALITY_REWORK_EXCEEDED` and full rework history attached.

---

## SOP-05: Output Delivery Failure

**Trigger:** Brief delivery to Script Department or Workflow Department fails.

**Procedure:**
1. Log: consumer, delivery method, error, timestamp.
2. Hold brief in outbound queue.
3. Retry:
   - Attempt 1: 1 hour after failure.
   - Attempt 2: 4 hours after Attempt 1.
   - Attempt 3: 24 hours after Attempt 2.
   - After 3 failures: escalate per SOP-02 with `escalation_type: DELIVERY_FAILURE`.
4. Notify Workflow Department after Attempt 2 fails.

---

## SOP-06: SLA Breach

**Trigger:** Processing time is approaching (80% of SLA elapsed) or has exceeded the SLA.

**At 80% elapsed:**
1. Assess whether remaining steps can complete within the SLA.
2. If unlikely: notify Platform Director and Workflow Department with current step, estimated completion, and cause.
3. Continue processing.

**Post-breach:**
1. Log breach: work item ID, SLA target, elapsed time, current step, cause.
2. Escalate per SOP-02 with `escalation_type: SLA_BREACH`.
3. Continue processing — a late brief is better than no brief.
4. Notify Workflow Department of breach and revised delivery time.

---

## SOP-07: Knowledge Access Outage

**Trigger:** A required vault domain or system is unavailable.

**Procedure:**
1. Identify which domain is unavailable and which workflow steps are blocked.
2. Assess impact: which creative dimensions cannot be developed without this domain?
3. If the affected dimensions can be developed from other available sources (other vault domains, research outputs): continue with a note that the unavailable domain was not accessible. Reduce confidence where applicable.
4. If the affected dimensions cannot be developed without the unavailable domain: hold the work item. Notify Platform Director and Workflow Department. Resume when access is restored.
5. Log outage duration and impact.

---

## SOP-08: Duplicate Brief Request

**Trigger:** A brief request arrives for a topic that has already been briefed in a prior output.

**Procedure:**
1. Retrieve the prior brief from the output log.
2. Assess whether it can be reused:
   - Is the format the same?
   - Is the audience direction the same or compatible?
   - Is the prior brief's research still current per the Research Department's domain currency standards?
3. If reusable: return the prior brief with a reuse assessment note. Do not re-brief.
4. If not reusable (different format, different audience, or stale research): proceed with a new brief. Reference the prior brief in `source_research_refs` if its findings remain relevant.
5. Log the duplication check outcome.

---

## SOP-09: Rejection Procedure

**Trigger:** A work item meets rejection criteria and cannot be reworked or escalated.

**Procedure:**
1. Construct rejection notice:
   - `error_code`: `WORK_ITEM_REJECTED`
   - `work_item_id`: ID
   - `rejection_reason`: specific criterion
   - `recommended_action`: what the requesting department should do
2. Deliver to Workflow Department.
3. Update status to `rejected`. Log entry. Do not process further.

---

## SOP-10: Department Onboarding

**Trigger:** This department is being activated for the first time.

**Procedure:**
1. Complete the Pre-Work Checklist in `CHECKLIST.md` from top to bottom.
2. Verify all six vault domains are accessible with `status: active` entries.
3. Confirm Research Department output log is readable.
4. Confirm Platform Director can receive escalations.
5. Run a complete test brief through the full workflow.
6. Document the activation date in `CHANGELOG.md`.
7. Register the department in `07_agents/README.md` Deployed Departments table.
8. Begin accepting live requests.

---

## SOP-11: Out-of-Authority Request

**Trigger:** A request is received to act outside the authority defined in `ROLE.md` — e.g., to select a topic, write a script fragment, modify research findings, produce non-Creative Brief content, or apply creative direction outside the brief format.

**Procedure:**
1. Do not comply, even partially.
2. Log the request: source, content summary, timestamp, authority boundary crossed.
3. Return structured refusal:
   - `error_code`: `OUT_OF_AUTHORITY_REQUEST`
   - `request_summary`: what was asked
   - `authority_boundary_reference`: specific `ROLE.md` section
   - `recommended_action`: who should handle the request
4. If request is repeated or represents a pattern: escalate per SOP-02 with `escalation_type: AUTHORITY_BOUNDARY_VIOLATION`.

**Specific to creative departments:** Requests to suppress a creative direction for political or interpersonal reasons ("just make it more upbeat"), to confirm a decision that has already been made rather than develop a defensible brief, or to write any prose that would appear in the final content are all out-of-authority requests.

---

## SOP-C01: Brief Revision Process

**Trigger:** A Creative Brief is returned by the Script Department with documented revision feedback.

**Procedure:**
1. Validate the revision request per `INPUTS.md` — Brief Return schema.
2. If feedback is vague: apply SOP-C03 immediately. Do not begin revision.
3. If feedback is specific: identify which dimensions are flagged.
4. Revise only the flagged dimensions. Do not rebuild the entire brief.
5. Re-run all six quality gates on the revised brief.
6. Increment `revision_number`.
7. Deliver revised brief to Script Department and Workflow Department.
8. Log: original brief ID, dimensions revised, revision rationale.

**Revision limits:** If a brief is returned for revision more than twice, escalate to Platform Director per SOP-02. Repeated returns indicate a systemic issue — in the brief production process, the Script Department's interpretation of briefs, or the alignment between departments on brief expectations.

---

## SOP-C02: Supplementary Research Request

**Trigger:** Research assessment (Workflow Step 2) reveals that the available research is insufficient to support one or more creative dimensions.

**Procedure:**
1. Identify specifically which dimensions lack sufficient research coverage.
2. Specify what type of research is needed for each gap (Research Brief, Trend Report, Competitive Analysis, etc.).
3. Submit a structured supplementary research request to the Research Department, referencing the work item ID and the specific dimensions requiring coverage.
4. Hold the brief work item in the queue with status `pending_research`.
5. When supplementary research is delivered: log receipt and resume at Step 2 (Research Assessment) with the complete research set.
6. If supplementary research is not delivered within the requesting timeline: escalate per SOP-02 with `escalation_type: RESEARCH_INSUFFICIENT`.

---

## SOP-C03: Vague Revision Feedback

**Trigger:** A revision request from the Script Department contains feedback that is not specific enough to act on (e.g., "this doesn't feel right," "make it more engaging," "the audience feels off").

**Procedure:**
1. Do not begin revision.
2. Return the revision request to the Script Department with a Feedback Clarification Template:
   ```
   The revision request received for brief [brief_id] cannot be actioned as submitted.
   Revision requests must specify:
   - Which specific dimension(s) need revision (from the ten defined dimensions)
   - What specifically is unclear, incorrect, or unworkable in the current brief
   - What the brief should achieve in the flagged dimension that it currently does not

   Please resubmit with dimension-specific feedback.
   ```
3. Log the clarification request with timestamp.
4. Hold the work item until clarified feedback is received.
5. If clarified feedback does not arrive within 48 hours: notify Platform Director.

---

## SOP-C04: Angle Exhaustion

**Trigger:** Angle exploration (Workflow Step 3) generates multiple angles and none are viable — all are either saturated in the content landscape, not grounded in the available research, or misaligned with the definable audience.

**Procedure:**
1. Document all angles generated and why each was rejected.
2. Assess root cause:
   - If the research is insufficient to surface differentiated angles: apply SOP-C02 to request additional research (specifically a Competitive Analysis or Idea Report for this topic).
   - If the topic itself is too saturated for a strong angle to be found: escalate to Platform Director per SOP-02 with `escalation_type: ANGLE_EXHAUSTION` and a recommendation to narrow the topic or find an adjacent angle with more room.
3. Do not select a weak angle to avoid escalation. A brief built on a saturated angle is worse than no brief.

---

## SOP-C05: Message Cannot Be Singularized

**Trigger:** Core message distillation (Workflow Step 5) fails after generating ten candidates. All candidates are either multi-idea or non-specific.

**Procedure:**
1. Assess root cause:
   - If the research surfaces multiple strong findings but no single dominant claim: the angle may be too broad. Return to Step 3 (Angle Exploration) and narrow the angle until the research supports a singular claim.
   - If the research itself is weak (low-confidence findings across the board): apply SOP-C02 for a targeted Research Brief seeking primary source evidence on the specific claim the angle requires.
2. If neither adjustment produces a singular message after two rounds: escalate per SOP-02 with `escalation_type: MESSAGE_CANNOT_SINGULARIZE`.

---

## SOP-C06: Editorial Override Conflict

**Trigger:** The Workflow Department or Platform Director instructs the Creative Department to use a specific creative direction (angle, message, audience, or hook) that contradicts the research-grounded decision the department has developed.

**Procedure:**
1. Do not silently comply by substituting the directed decision for the researched one.
2. Log the override instruction: source, content, timestamp, and which dimension is affected.
3. Respond with a structured conflict notice:
   - The research-grounded decision that was developed and its rationale.
   - The override instruction received and its source.
   - The specific dimension where the conflict exists.
   - A request for explicit written confirmation that the override is intentional.
4. If written confirmation is received: implement the override. Document it in the brief under the relevant dimension with a note that this decision was editorially directed and does not reflect the research-grounded recommendation. Include the override in the activity log.
5. If confirmation is not received within 24 hours: proceed with the research-grounded decision.

**Why this SOP exists:** Creative departments are occasionally pressured to confirm decisions that have already been made rather than develop defensible ones. This SOP creates a documented trail when editorial direction overrides research-grounded creative judgment — which is sometimes appropriate, but must always be explicit.
