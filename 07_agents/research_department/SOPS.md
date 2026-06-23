# Standard Operating Procedures — Research Department

SOPs are the decision playbook for situations not covered by the standard workflow. When an unusual situation arises, the correct response is always: find the SOP, follow it. If no SOP covers the situation, escalate. Do not improvise.

---

## SOP Index

| SOP | Trigger | Summary |
|---|---|---|
| SOP-01 | Input validation failure | How to handle malformed, out-of-scope, or unauthorized requests |
| SOP-02 | Escalation criteria met | How to execute a proper escalation |
| SOP-03 | Quality gate failure (rework) | How to manage the rework loop |
| SOP-04 | Quality gate failure (rework maximum reached) | When rework is exhausted |
| SOP-05 | Output delivery failure | How to handle consumer unavailability |
| SOP-06 | SLA breach | How to respond to missed or imminent SLA deadlines |
| SOP-07 | Core tool outage | How to operate when a core tool is unavailable |
| SOP-08 | Duplicate research request | How to handle a request that matches a prior output |
| SOP-09 | Rejection procedure | How to formally reject and close a work item |
| SOP-10 | Department onboarding | How to activate this department for the first time |
| SOP-11 | Out-of-authority request | How to respond when asked to act outside defined scope |
| SOP-R01 | Signal significance assessment | How to assess whether a monitoring signal warrants an output |
| SOP-R02 | Domain monitoring cadences | The defined monitoring schedule for all ten domains |
| SOP-R03 | Competitive Analysis entity list approval | How to handle the entity list approval step |
| SOP-R04 | Vault expiry emergency | How to handle a vault entry with fewer than five business days to expiry |
| SOP-R05 | Research question outside monitored domains | How to handle a request for a topic outside the ten domains |
| SOP-R06 | Contradictory findings | How to handle research that contradicts the requesting department's premise |

---

## SOP-01: Input Validation Failure

**Trigger:** An incoming research request fails one or more validation checks defined in `INPUTS.md`.

**Procedure:**
1. Log the validation failure: work item ID, requesting department, timestamp, and which validation rules failed.
2. Return a structured rejection to the requesting department:
   - `error_code`: `INPUT_VALIDATION_FAILURE`
   - `work_item_id`: the generated ID
   - `failed_rules`: list of rule names and explanations
   - `received_values`: what was submitted (do not include sensitive content)
   - `resubmission_guide`: specific guidance on how to correct the request
3. Do not begin research.
4. Log closure with status `rejected`.

**Common failure types and guidance:**
- **Research question is a broad topic, not a specific question:** Return with an example of how to reframe it as a specific, answerable question.
- **Output type mismatch:** Return with a description of all eight output types and guidance on which fits the question.
- **Domain out of scope:** Return with the list of ten monitored domains and the escalation path for out-of-scope requests (SOP-R05).
- **Missing required fields:** Return the schema with the missing fields highlighted.

---

## SOP-02: Escalation Procedure

**Trigger:** Any escalation criterion defined in `WORKFLOW.md` or `QUALITY_STANDARDS.md` is met, or any situation arises that exceeds this department's operating parameters.

**Procedure:**
1. Stop processing the current work item.
2. Record the escalation trigger: which criterion was met, current workflow step, and full context assembled to this point.
3. Construct an escalation notice:
   - `escalation_type`: [specific type — see types below]
   - `work_item_id`: ID
   - `trace_id`: propagated trace ID
   - `trigger_criterion`: description of what triggered escalation
   - `context_summary`: what has been done, what was found, why processing stopped
   - `rework_history`: if applicable
   - `recommended_action`: if the department has a recommendation, state it clearly; if not, leave blank
4. Deliver the notice to the Platform Director via the escalation channel.
5. Notify the requesting department that the request has been escalated, with a brief explanation.
6. Update work item status to `escalated`.
7. Write activity log entry.
8. Await direction from Platform Director. Do not re-process without explicit direction.

**Escalation types:**
- `SOURCE_UNAVAILABILITY`: Required source tier unavailable; cannot produce defensible output.
- `QUALITY_REWORK_EXCEEDED`: Rework maximum reached without passing all quality gates.
- `CONFIDENCE_FULFILLMENT_FAILURE`: Research cannot achieve the confidence level the request requires.
- `SLA_BREACH`: Processing time has exceeded or will exceed SLA.
- `SCOPE_AMBIGUITY`: Request scope cannot be resolved without strategic direction.
- `TOOL_OUTAGE_BLOCKING`: Core tool outage is blocking research from proceeding.
- `AUTHORITY_BOUNDARY_VIOLATION`: See SOP-11.
- `VAULT_EXPIRY_EMERGENCY`: See SOP-R04.
- `CONTRADICTORY_FINDINGS`: See SOP-R06.

---

## SOP-03: Quality Gate Failure — Rework

**Trigger:** A quality gate fails during Workflow Step 7, and the rework attempt count is below the maximum (2).

**Procedure:**
1. Record the gate failure: gate number, specific checks that failed, observed values.
2. Increment rework attempt counter.
3. Attach the gate failure context to the work item.
4. Return to the appropriate workflow step:
   - Gate 1 (Schema Completeness): return to Step 6.
   - Gate 2 (Source Adequacy): return to Step 4 or Step 5.
   - Gate 3 (Confidence Calibration): return to Step 6.
   - Gate 4 (Claim-Implication Alignment): return to Step 5 or Step 6.
   - Gate 5 (Traceability): return to Step 6 (metadata issue) or escalate immediately (systemic logging failure).
   - Gate 6 (Vault Compliance): return to Step 6.
5. After re-processing, run all gates from Gate 1. Do not skip gates that previously passed.

---

## SOP-04: Quality Gate Failure — Rework Maximum Reached

**Trigger:** A quality gate fails and the rework attempt count has reached 2.

**Procedure:**
1. Do not attempt further rework.
2. Compile the full rework history: all gate failures, failure contexts, and the output state after each attempt.
3. Follow SOP-02 with `escalation_type: QUALITY_REWORK_EXCEEDED` and full rework history attached.

---

## SOP-05: Output Delivery Failure

**Trigger:** Output delivery to a consumer fails.

**Procedure:**
1. Log: consumer, delivery method, error received, timestamp.
2. Hold output in the outbound queue.
3. Retry schedule:
   - Attempt 1: 1 hour after failure.
   - Attempt 2: 4 hours after Attempt 1.
   - Attempt 3: 24 hours after Attempt 2.
   - After 3 failed attempts: escalate per SOP-02 with `escalation_type: DELIVERY_FAILURE`.
4. Notify requesting department after Attempt 2 fails, with current status and next retry time.

---

## SOP-06: SLA Breach

**Trigger:** Processing time is approaching or has exceeded the SLA for this request.

**SLA warning (80% of SLA elapsed):**
1. Assess whether remaining steps can complete within the SLA.
2. If completion is unlikely: notify Platform Director and requesting department with current status, estimated completion time, and the cause of the delay.
3. Continue processing — do not halt.

**Post-breach:**
1. Log SLA breach: work item ID, SLA target, actual elapsed time, current step, cause.
2. Notify Platform Director per SOP-02 with `escalation_type: SLA_BREACH`.
3. Continue processing — a late output is better than no output.
4. Notify requesting department of the breach and revised delivery time.

---

## SOP-07: Core Tool Outage

**Trigger:** A core tool listed in `TOOLS.md` is unavailable.

**Procedure:**
1. Identify which tool is affected and which workflow steps are blocked.
2. Apply the fallback defined in `TOOLS.md` for that tool.
3. If no fallback exists:
   - Halt intake of new requests requiring that tool.
   - Hold all queued items requiring that tool.
   - Notify Platform Director and all affected requesting departments.
   - Provide estimated impact on delivery timelines.
4. When the tool is restored: run the relevant Pre-Work Checklist items before resuming.
5. Log outage duration and impact.

---

## SOP-08: Duplicate Research Request

**Trigger:** A request is received that matches a prior research output.

**Procedure:**
1. Identify the prior output via the output log.
2. Assess currency using the domain-specific thresholds in `WORKFLOW.md` Step 2.
3. If prior output is current:
   - Return prior output to requesting department with a note on its age, currency assessment, and the domains' standard re-verification window.
   - Mark the new request as `closed — prior output returned`.
4. If prior output is outdated:
   - Proceed with fresh research.
   - Reference the prior output in `related_outputs` in the new output.
   - Archive the prior output when the new output is completed.

---

## SOP-09: Rejection Procedure

**Trigger:** A work item meets the rejection criteria in `QUALITY_STANDARDS.md` and cannot be reworked or escalated.

**Procedure:**
1. Construct a structured rejection notice:
   - `error_code`: `WORK_ITEM_REJECTED`
   - `work_item_id`: ID
   - `rejection_reason`: specific criterion met
   - `context`: what was attempted and why it cannot be resolved
   - `recommended_action`: what the requesting department should do
2. Deliver to requesting department.
3. Update status to `rejected`.
4. Write activity log entry.

---

## SOP-10: Department Onboarding

**Trigger:** This department is being activated for the first time in an environment.

**Procedure:**
1. Complete the Pre-Work Checklist in `CHECKLIST.md` from top to bottom.
2. Verify all ten domain monitoring cadences are configured per SOP-R02.
3. Confirm Platform Director is aware of activation and can receive escalation notices.
4. Process a test Research Brief through the full workflow.
5. Document the activation date and environment in `CHANGELOG.md`.
6. Register the department in `07_agents/README.md` Deployed Departments table.
7. Begin accepting live requests.

---

## SOP-11: Out-of-Authority Request

**Trigger:** The department receives a request to act outside its defined authority in `ROLE.md` — for example: to make editorial decisions, to approve or modify another department's content, to suppress findings for strategic reasons, or to produce content rather than structured research.

**Procedure:**
1. Do not comply with the request — not even partially.
2. Log the request: source, content summary, timestamp, and which `ROLE.md` authority boundary it crosses.
3. Return a structured refusal:
   - `error_code`: `OUT_OF_AUTHORITY_REQUEST`
   - `request_summary`: brief description of what was asked
   - `authority_boundary_reference`: the specific `ROLE.md` section defining the limit
   - `recommended_action`: who the requester should contact (e.g., Platform Director for editorial decisions, Workflow Department for topic selection)
4. If the request represents a pattern or the requester persists: escalate per SOP-02 with `escalation_type: AUTHORITY_BOUNDARY_VIOLATION`.

**Why this matters for a research department specifically:** Research departments are occasionally pressured to frame findings favorably, omit inconvenient evidence, or confirm pre-existing decisions. These requests always violate the department's authority boundary and the honesty requirements in `QUALITY_STANDARDS.md`. The refusal must be clear, structured, and non-negotiable.

---

## SOP-R01: Signal Significance Assessment

**Trigger:** The monitoring cycle surfaces a development, announcement, or publication from a monitored domain.

**Significance threshold — a signal warrants an output when TWO OR MORE of the following are true:**
- The development represents a structural change in a domain (new business model, new platform capability, regulatory shift, major study publication).
- Multiple independent sources are reporting or discussing the development.
- The development has direct implications for Build Better's content strategy, audience, or operations.
- The development contradicts a currently active vault entry, requiring a Knowledge Update.
- The development is time-sensitive — a window exists within which content on the topic would be distinctively timely.

**Procedure when threshold is met:**
1. Log the signal with date, source, domain, and significance rationale.
2. Select output type: Trend Report (patterns and implications) or Knowledge Update (vault entry revision).
3. Follow Workflow B from Step 4.

**Procedure when threshold is not met:**
1. Log the signal with date, source, domain, and rationale for not triggering an output.
2. Continue monitoring. If additional signals on the same topic accumulate to meet the threshold, trigger an output at that point.

---

## SOP-R02: Domain Monitoring Cadences

The Research Department monitors all ten domains on the following schedule:

| Domain | Daily Scan | Weekly Synthesis | Monthly Deep Review |
|---|---|---|---|
| Artificial Intelligence | Yes | Yes | Yes |
| Technology | Yes | Yes | Yes |
| Creator Economy | Yes | Yes | Yes |
| Marketing | Yes | Yes | No (quarterly) |
| Business | No | Yes | Yes |
| Startups | No | Yes | Yes |
| Psychology | No | No | Yes |
| Books | No | Weekly new release scan | Yes |
| Frameworks | No | No | Yes |
| Productivity | No | Yes | No (quarterly) |

**Daily scan:** Review aggregated signals from configured sources. Apply SOP-R01 significance assessment to any signals surfaced.

**Weekly synthesis:** Review the week's accumulated signals for each domain. Identify patterns that individually fell below the threshold but collectively meet it. Produce Trend Reports or Knowledge Updates as warranted.

**Monthly deep review:** Comprehensive review of the domain's current state. Assess vault entries for currency. Identify any slow-moving trends that weekly synthesis has not captured.

---

## SOP-R03: Competitive Analysis Entity List Approval

**Trigger:** A Competitive Analysis request is received and the entity list must be established.

**Procedure:**
1. If the requesting department provided an entity list: review it for completeness. If any significant entities are missing, note them and add them provisionally.
2. Draft the entity list with: entity name, category, brief rationale for inclusion.
3. Send to requesting department for approval. Allow 24 hours for response.
4. If the requesting department approves: proceed to Step 4 of Workflow A.
5. If the requesting department requests changes: incorporate and resubmit. Do not begin research until approval is received in writing.
6. If the requesting department does not respond within 24 hours: proceed with the drafted entity list and note in the output that the list was confirmed unilaterally after the approval window elapsed.

---

## SOP-R04: Vault Expiry Emergency

**Trigger:** A vault expiry alert arrives with fewer than five business days before the entry's expiry date.

**Procedure:**
1. Immediately log the expiry emergency with entry ID, domain, expiry date, and available days.
2. Notify Platform Director.
3. Assess the entry's significance:
   - If the entry is frequently referenced by consuming departments: escalate the re-verification to `urgent` tier and begin immediately.
   - If the entry is infrequently referenced: begin re-verification on an `expedited` basis; if re-verification cannot complete before expiry, update the entry's status to `draft` in the vault to prevent it being cited as `active` while unverified.
4. Produce a Knowledge Update within the available window or as quickly as possible.
5. If re-verification cannot be completed at all within a reasonable window: archive the entry and note the archival reason.

---

## SOP-R05: Research Question Outside Monitored Domains

**Trigger:** A research request is received for a topic that falls outside the ten monitored domains.

**Procedure:**
1. Do not begin research.
2. Reject the request per SOP-01 with:
   - `error_code`: `DOMAIN_OUT_OF_SCOPE`
   - Explanation of the ten monitored domains
   - Contact: Platform Director — for requesting a domain scope extension
   - Note: If the topic is adjacent to a monitored domain (e.g., a fitness topic that has significant psychology or marketing dimensions), note the adjacent domain and offer to research those dimensions.
3. If the requesting department escalates to the Platform Director and the Platform Director approves a temporary scope extension: process the request under the approved scope, noting in the output that it was produced under a temporary scope extension.

---

## SOP-R06: Contradictory Findings

**Trigger:** Research synthesis (Workflow Step 5) produces findings that directly contradict the premise in the requesting department's research question or the stated expectations in their context note.

**Procedure:**
1. Do not suppress or soften the contradictory finding.
2. Document both the original premise (as stated in the request) and the research finding clearly in the output.
3. Apply Gate 3 (Confidence Calibration) rigorously — contradictory findings must be held to the same evidence standard as any other finding.
4. In the output's `implications` section: explicitly note that the findings differ from the stated premise and explain what this means for the requesting department.
5. In the output's `caveats` section: note any limitations in the research that could explain the discrepancy or that leave room for the original premise to be partially correct.
6. Deliver the output normally — contradiction does not warrant escalation unless the confidence in the contradictory finding is `low` or `speculative`.
7. If confidence in the contradictory finding is `low` or `speculative` AND the finding significantly changes the actionability of the output: escalate per SOP-02 with `escalation_type: CONTRADICTORY_FINDINGS` so the Platform Director can determine whether to communicate the nuance to the requesting department directly.
