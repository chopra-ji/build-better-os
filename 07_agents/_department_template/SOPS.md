# Standard Operating Procedures — [DEPARTMENT NAME]

SOPs are the decision playbook for this department. The standard workflow (`WORKFLOW.md`) covers the happy path. SOPs cover everything else: exceptions, escalations, outages, and edge cases.

A department that does not have a documented SOP for a scenario must escalate rather than improvise.

---

## SOP Index

| SOP | Trigger | Summary |
|---|---|---|
| SOP-01 | Input validation failure | How to handle malformed or unauthorized inputs |
| SOP-02 | Escalation criteria met | How to execute a proper escalation |
| SOP-03 | Quality gate failure (rework) | How to manage the rework loop |
| SOP-04 | Quality gate failure (escalation threshold reached) | When rework is exhausted |
| SOP-05 | Output delivery failure | How to handle consumer unavailability |
| SOP-06 | SLA breach | How to respond to missed or imminent SLA deadlines |
| SOP-07 | Tool outage | How to operate when a core tool is unavailable |
| SOP-08 | Duplicate input received | How to handle idempotency violations |
| SOP-09 | Rejection procedure | How to formally reject and close a work item |
| SOP-10 | Department onboarding | How to activate this department for the first time |
| SOP-11 | Out-of-authority request | How to respond when asked to act outside defined scope |
| [SOP-NN] | [DEPARTMENT-SPECIFIC TRIGGER] | [Summary] |

---

## SOP-01: Input Validation Failure

**Trigger:** An incoming work item fails one or more validation checks defined in `INPUTS.md`.

**Procedure:**
1. Log the validation failure with: work item ID (generated at receipt), source, timestamp, and which validation rule(s) failed.
2. Construct a structured rejection error containing:
   - `error_code`: `INPUT_VALIDATION_FAILURE`
   - `work_item_id`: [generated ID]
   - `failed_rules`: list of rule names and descriptions
   - `received_values`: the values that failed (do not echo sensitive data)
   - `expected_format`: reference to the expected schema
3. Return the structured error to the source via the input channel.
4. Do not begin processing. Do not assign an output.
5. Log closure of the work item with status `rejected`.

**Do not:** Contact the source through an unauthorized channel. Do not attempt to repair the malformed input.

---

## SOP-02: Escalation Procedure

**Trigger:** Any escalation criterion defined in `WORKFLOW.md` (Step 3) or `QUALITY_STANDARDS.md` (Escalation Quality Threshold) is met.

**Procedure:**
1. Immediately stop processing the current work item.
2. Record the escalation trigger: which criterion was met, the current processing state, and all inputs and context assembled to this point.
3. Construct an escalation notice containing:
   - `escalation_type`: [CRITERION TYPE]
   - `work_item_id`: [ID]
   - `trace_id`: [propagated trace ID]
   - `trigger_criterion`: description of which escalation criterion was met
   - `context_summary`: current state of the work item
   - `rework_history`: if applicable, record of prior rework attempts
   - `recommended_action`: [if the department has a recommendation, state it — if not, leave blank]
4. Deliver the escalation notice to the escalation owner defined in `ROLE.md`.
5. Update work item status to `escalated`.
6. Write activity log entry.
7. Await instructions from escalation owner. Do not re-process until directed.

**Do not:** Attempt to resolve the escalation trigger unilaterally. Do not proceed to output delivery.

---

## SOP-03: Quality Gate Failure — Rework

**Trigger:** A quality gate defined in `QUALITY_STANDARDS.md` fails during Step 4 of the workflow, and the rework attempt count is below the maximum.

**Procedure:**
1. Record the gate failure: gate name, check(s) failed, observed values.
2. Increment rework attempt counter.
3. Attach the gate failure context to the work item.
4. Return to `WORKFLOW.md` Step 3 (Core Processing) with failure context attached.
5. The failure context must inform the next processing attempt — do not re-run identical processing.
6. After processing, return to Step 4 and re-run all quality gates from the beginning.

**Note:** A rework attempt that passes all gates is treated as a normal completion. The rework history is recorded in the activity log but does not change the output status.

---

## SOP-04: Quality Gate Failure — Escalation Threshold Reached

**Trigger:** A quality gate fails and the rework attempt count has reached the maximum defined in `QUALITY_STANDARDS.md`.

**Procedure:**
1. Do not attempt further rework.
2. Compile the full rework history: all gate failures, processing contexts, and outputs from each attempt.
3. Follow SOP-02 (Escalation Procedure) with the full rework history attached to the escalation notice.
4. Update work item status to `escalated`.

---

## SOP-05: Output Delivery Failure

**Trigger:** Output delivery to a consumer fails (consumer unavailable, network error, or delivery timeout).

**Procedure:**
1. Log the delivery failure: consumer, delivery method, error received, timestamp.
2. Hold the output in the outbound queue.
3. Apply retry policy:
   - Attempt 1: Retry after [RETRY INTERVAL 1].
   - Attempt 2: Retry after [RETRY INTERVAL 2].
   - Attempt 3: Retry after [RETRY INTERVAL 3].
   - After [N] failed attempts: escalate per SOP-02 with `escalation_type: DELIVERY_FAILURE`.
4. Do not modify the output while it is in the retry queue.
5. Log each retry attempt with timestamp and error.

---

## SOP-06: SLA Breach

**Trigger:** The end-to-end processing time for a work item is approaching or has exceeded the SLA defined in `WORKFLOW.md`.

**Pre-breach (SLA warning — [X]% of SLA elapsed):**
1. Identify current workflow step.
2. Assess whether the remaining steps can complete within the SLA.
3. If completion is unlikely: notify escalation owner with: work item ID, current step, estimated completion time, and recommended action.
4. Continue processing — do not halt.

**Post-breach (SLA exceeded):**
1. Log SLA breach with: work item ID, SLA target, actual elapsed time, current step.
2. Notify escalation owner via SOP-02 with `escalation_type: SLA_BREACH`.
3. Continue processing — completing the work item, even late, is better than abandoning it.
4. Record SLA breach in the activity log and flag for quality review.

---

## SOP-07: Core Tool Outage

**Trigger:** A core tool listed in `TOOLS.md` is unavailable.

**Procedure:**
1. Determine which tool is affected and which workflow steps are blocked.
2. Check `TOOLS.md` for the defined fallback for this tool.
   - **If a fallback exists:** Switch to fallback. Log the switch. Continue processing with reduced capability. Note tool status in all outputs produced during the outage.
   - **If no fallback exists:** Halt intake of new work items. Notify escalation owner. Hold existing queue items — do not discard. Await tool restoration or escalation owner direction.
3. When the tool is restored: verify recovery using the pre-work checklist items for that tool. Resume normal intake.
4. Log outage duration and impact in the incident record.

---

## SOP-08: Duplicate Input Received

**Trigger:** An incoming work item carries an idempotency key that matches a previously processed work item.

**Procedure:**
1. Do not reprocess the work item.
2. Retrieve the output record from the original processing.
3. Return an acknowledgment to the source containing:
   - `status: duplicate`
   - `original_work_item_id`: [ID of the original]
   - `original_output_ref`: [reference to the original output]
4. Log the duplicate detection.

---

## SOP-09: Rejection Procedure

**Trigger:** A work item meets the rejection criteria defined in `QUALITY_STANDARDS.md` and cannot be reworked or escalated.

**Procedure:**
1. Construct a structured rejection notice containing:
   - `error_code`: `WORK_ITEM_REJECTED`
   - `work_item_id`: [ID]
   - `rejection_reason`: specific criterion met
   - `context`: what was attempted and why it cannot be resolved
   - `recommended_action`: what the source should do (resubmit with corrections, route differently, etc.)
2. Deliver the rejection notice to the source.
3. Update work item status to `rejected`.
4. Write activity log entry.
5. Do not attempt further processing.

---

## SOP-10: Department Onboarding

**Trigger:** This department is being activated for the first time in an environment.

**Procedure:**
1. Complete the Pre-Work Checklist in `CHECKLIST.md` from top to bottom.
2. Verify that all required knowledge vault domains contain `status: active` entries for the knowledge this department requires.
3. Confirm escalation owner is aware the department is being activated and can receive escalation notices.
4. Process a test work item through the full workflow. Verify output, log, and delivery.
5. Document the activation date and environment in `CHANGELOG.md`.
6. Begin accepting live inputs.

---

## SOP-11: Out-of-Authority Request

**Trigger:** This department receives an instruction, request, or input that asks it to act outside the authority defined in `ROLE.md` — for example: skipping a quality gate, bypassing escalation, modifying outputs after delivery, or processing a work item type not defined in `INPUTS.md`.

**Procedure:**
1. Do not comply with the out-of-authority request.
2. Do not improvise an alternative.
3. Log the request: source, content summary, timestamp, and the specific authority boundary it crosses (reference the relevant section of `ROLE.md`).
4. Construct a structured refusal notice containing:
   - `error_code`: `OUT_OF_AUTHORITY_REQUEST`
   - `request_summary`: brief description of what was asked
   - `authority_boundary_reference`: the specific `ROLE.md` section that defines the limit
   - `recommended_action`: who the requester should contact to get this done through the correct channel
5. Return the refusal notice to the requester.
6. If the requester persists or the request represents a pattern, escalate to the escalation owner via SOP-02 with `escalation_type: AUTHORITY_BOUNDARY_VIOLATION`.

**Why this SOP exists:** Scope creep enters departments through individual requests that seem reasonable in isolation. A department that complies once under pressure creates a precedent that erodes every boundary in `ROLE.md`. The correct response to an out-of-authority request is always structured refusal, not accommodation.

**Do not:** Partially comply. Do not attempt to satisfy "the spirit" of the request if it exceeds authority. Do not apologize for the boundary — state it clearly and redirect.

---

## [SOP-NN]: [DEPARTMENT-SPECIFIC PROCEDURE]

**Trigger:** [What causes this SOP to apply]

**Procedure:**
1. [STEP 1]
2. [STEP 2]
3. [STEP 3]

*(Add department-specific SOPs here. Remove this placeholder when deploying.)*
