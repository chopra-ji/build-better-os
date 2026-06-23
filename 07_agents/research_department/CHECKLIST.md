# Checklist — Research Department

Every item on these checklists is a concrete, verifiable action. Do not advance to the next phase until every item for the current phase is checked. These checklists are operational tools — they exist because the cost of catching a problem after delivery is always higher than catching it here.

---

## Pre-Work Checklist

Complete before accepting any live research requests. Run when the department is first activated and after any significant configuration change.

### Readiness

- [ ] Knowledge vault access confirmed — test read from `knowledge/ai/` and `knowledge/technology/`.
- [ ] Research queue system is live and accepting entries.
- [ ] Output log is accessible and writeable.
- [ ] Activity log is accepting entries.
- [ ] News and signal aggregator is connected and domain feeds are active for all ten domains.
- [ ] Academic and industry source access credentials are valid.
- [ ] Escalation channel to Platform Director is confirmed and reachable.
- [ ] All ten domain monitoring cadences are configured (see `SOPS.md` → Domain Monitoring Cadences).

### Configuration

- [ ] Input validation rules match the schema defined in `INPUTS.md`.
- [ ] Quality gate criteria match `QUALITY_STANDARDS.md` (all six gates).
- [ ] SLA timers match the turnaround table in `WORKFLOW.md`.
- [ ] Concurrency limit is set to 8 (maximum concurrent work items).
- [ ] Priority queue is ordered: `urgent` > `expedited` > `standard`.
- [ ] Source reliability tier definitions match `QUALITY_STANDARDS.md`.
- [ ] Domain currency standards are configured for source recency checks.

### First-Item Verification

- [ ] Process a test Research Brief on a non-sensitive topic through the full workflow.
- [ ] Confirm all six quality gates run correctly on the test output.
- [ ] Confirm test output is delivered to the test consumer and delivery is logged.
- [ ] Confirm vault contribution assessment runs at Step 9 (even if the test does not warrant a vault entry).
- [ ] Confirm the activity log entry is written with all required fields.
- [ ] Remove test item from the queue and output log before accepting live requests.

---

## Per-Request Checklist

Complete for every research request. Map to workflow steps.

### Step 1: Intake and Validation

- [ ] Request received from an authorized source (department is listed in `ROLE.md`).
- [ ] Work item ID assigned and logged with timestamp.
- [ ] All required schema fields present and non-empty.
- [ ] `output_type` is one of the eight valid types.
- [ ] `research_question` is specific and answerable (not a broad topic).
- [ ] Domain is within the ten monitored domains.
- [ ] `urgency_tier` is set to `standard`, `expedited`, or `urgent`.

### Step 2: Deduplication Check

- [ ] Output log searched for substantially similar prior research.
- [ ] If prior output found: currency assessed against domain-specific thresholds (see `WORKFLOW.md` Step 2).
- [ ] Outcome documented: either prior output returned (request closed) or fresh research initiated with prior output noted.

### Step 3: Scope Confirmation

- [ ] Scope ambiguities identified and resolved, or scope clarification request sent with a 24-hour response window.
- [ ] For Competitive Analysis: entity list drafted and sent to requesting department for approval before research begins.
- [ ] Scope is confirmed in writing before Step 4 begins.

### Step 4: Source Assembly

- [ ] Required source types identified for this output type and domain.
- [ ] At least one Tier 1–3 source identified and accessible.
- [ ] Source gaps documented; resolution attempted or escalated if critical.
- [ ] Preliminary reliability tier assigned to each source.

### Step 5: Research and Synthesis

- [ ] All assembled sources read and processed.
- [ ] Findings documented with evidence and source references.
- [ ] Conflicts between sources documented with both positions and evidence assessment.
- [ ] Confidence level assessed for each key finding.
- [ ] Overall output confidence level set.
- [ ] Escalation triggers checked — none met, or escalation initiated.
- [ ] Implications drafted for the requesting department.

### Step 6: Output Drafting

- [ ] Correct schema selected for the output type.
- [ ] Every required field populated — no empty required fields.
- [ ] `confidence` and `confidence_note` written with specificity.
- [ ] `implications` grounded in specific findings.
- [ ] `caveats` section states at least one thing the research does not establish.
- [ ] `sources` list is complete with title, author, date, location, and reliability tier for each source.
- [ ] Output metadata attached: `trace_id`, `department_id`, `version`, `produced_at`, `input_ref`.

### Step 7: Quality Review

- [ ] Gate 1 (Schema Completeness) — passed.
- [ ] Gate 2 (Source Adequacy) — passed.
- [ ] Gate 3 (Confidence Calibration) — passed.
- [ ] Gate 4 (Claim-Implication Alignment) — passed (if applicable to output type).
- [ ] Gate 5 (Traceability) — passed.
- [ ] Gate 6 (Vault Entry Compliance) — passed (Knowledge Updates only).
- [ ] Rework count recorded if any gate failed previously.

### Step 8: Output Delivery

- [ ] Delivery targets confirmed per `OUTPUTS.md` for this output type.
- [ ] Output delivered to all required consumers.
- [ ] Delivery confirmation logged (where delivery method provides confirmation).

### Step 9: Vault Contribution

- [ ] Vault contribution assessed: does this output contain findings warranting a Knowledge Update?
- [ ] If yes: Knowledge Update drafted and submitted with full YAML frontmatter.
- [ ] If no: rationale documented in activity log.

### Step 10: Logging and Closure

- [ ] Activity log entry written: work item ID, trace ID, output type, domain, processing time, gate results, rework count, delivery confirmation, vault contribution outcome, final status.
- [ ] Research queue updated.
- [ ] Work item marked as closed.

---

## Competitive Analysis — Additional Checklist

Used in addition to the standard per-request checklist for Competitive Analysis outputs.

- [ ] Entity list submitted to requesting department before research begins.
- [ ] Entity list approval received in writing before research begins.
- [ ] Analysis dimensions agreed with requesting department (or set by research department with notification).
- [ ] Each entity has at least two sources supporting its assessment.
- [ ] `gaps_identified` section contains at least one finding.
- [ ] `build_better_positioning` reflects the actual competitive landscape, not an aspirational view.

---

## Technology Report — Additional Checklist

- [ ] `maturity_stage` is assessed against a consistent adoption framework, not intuition.
- [ ] `key_players` list includes entities across the maturity spectrum, not only the most prominent.
- [ ] `limitations` section is at least as detailed as `capabilities` section.
- [ ] `recommended_actions` are proportionate to the confidence level of the findings.
- [ ] At least one Tier 1 or Tier 2 source is present (primary research or official documentation).

---

## Monitoring-Triggered Output Checklist

For Trend Reports and Knowledge Updates produced by the proactive monitoring cycle (no request ID).

- [ ] Signal significance threshold has been met (see `SOPS.md` → Signal Significance Standards).
- [ ] Signal is logged with date, source, domain, and significance assessment.
- [ ] `request_id` is set to `proactive_monitoring`.
- [ ] Monitoring trigger is logged as the input reference in the activity log.
- [ ] All standard quality gates apply — proactive outputs are not exempt.

---

## Escalation Checklist

Complete when an escalation criterion is met before triggering the escalation.

- [ ] Escalation criterion documented — which specific criterion was met.
- [ ] Work item ID and trace ID recorded.
- [ ] Full context assembled: original request, current workflow step, sources assembled, gate results if applicable, rework history if applicable.
- [ ] Escalation notice formatted with: work item ID, criterion met, context summary, and recommended action (if research department has a recommendation).
- [ ] Escalation notice delivered to Platform Director.
- [ ] Work item status updated to `escalated`.
- [ ] Requesting department notified that the request has been escalated with an explanation.
- [ ] Activity log entry written.

---

## Periodic Review Checklist

Complete monthly.

- [ ] Quality metrics reviewed against targets in `QUALITY_STANDARDS.md`.
- [ ] Gate failure distribution reviewed — which gates are failing most often and why.
- [ ] Escalation log reviewed for patterns.
- [ ] All ten domain monitoring cadences are running as configured.
- [ ] Vault entries approaching their re-verification window identified and scheduled.
- [ ] Knowledge gaps reviewed for resolution progress.
- [ ] Output log checked for completeness — no closed requests without a logged output.
- [ ] Open incidents from the prior period resolved or tracked with owner and deadline.
