# Checklist — Creative Department

Every item is a concrete, verifiable action. Do not advance to the next phase until every applicable item is checked. These lists exist because the cost of delivering a weak brief and discovering it during production is always higher than catching it here.

---

## Pre-Work Checklist

Complete before accepting live brief requests. Run when the department is first activated and after any significant configuration change.

### Readiness

- [ ] Access to all six required vault domains confirmed: storytelling, psychology, frameworks, marketing, books, design.
- [ ] All required vault entries are `status: active` — no required knowledge is in draft or archived.
- [ ] Brief queue system is live and accepting entries.
- [ ] Output log is accessible and writeable.
- [ ] Activity log is accepting entries.
- [ ] Research Department output log is readable for deduplication and reference.
- [ ] Escalation channel to Platform Director is confirmed reachable.
- [ ] Script Department output channel is connected and accepting deliveries.
- [ ] Workflow Department output channel is connected and accepting deliveries.

### Configuration

- [ ] Input validation rules match the schema in `INPUTS.md`.
- [ ] Quality gate criteria match all six gates in `QUALITY_STANDARDS.md`.
- [ ] SLA timers match `WORKFLOW.md` → Timing and SLAs.
- [ ] Concurrency limit is set to 10 (maximum concurrent briefs).
- [ ] Long-form video concurrency sub-limit is set to 3.
- [ ] Priority queue ordered: urgent > expedited > standard; within tier, FIFO.

### First-Item Verification

- [ ] Process a test brief request (non-live topic) through the full workflow.
- [ ] Confirm all six quality gates run correctly.
- [ ] Confirm the test brief is delivered to Script Department and Workflow Department test channels.
- [ ] Confirm the activity log entry is written with all required fields.
- [ ] Remove test item from the queue, output log, and delivery channels before accepting live requests.

---

## Per-Brief Checklist

Complete for every Creative Brief request.

### Step 1: Intake and Validation

- [ ] Request received from Workflow Department (authorized source).
- [ ] Work item ID assigned and logged with timestamp.
- [ ] All required schema fields present: `request_id`, `topic`, `format`, `urgency_tier`, `submitted_at`, `research_refs`.
- [ ] `format` is one of the six valid content format enums.
- [ ] `urgency_tier` is `standard`, `expedited`, or `urgent`.
- [ ] All `research_refs` resolve to `status: complete` research outputs in the Research Department output log.
- [ ] Topic is specific enough to brief (not a broad domain).

### Step 2: Research Assessment

- [ ] All referenced research outputs read and assessed.
- [ ] Research coverage assessed for each of the ten creative dimensions.
- [ ] Dimensions with insufficient research coverage identified.
- [ ] If gaps found: supplementary research request submitted to Research Department; work item held.
- [ ] If no gaps: confirmed that all ten dimensions can be supported by available research.

### Step 3: Angle Exploration

- [ ] At least five distinct angles generated on the topic.
- [ ] Each angle evaluated against audience alignment, differentiation, and research grounding.
- [ ] At least two angles rejected with documented rationale.
- [ ] One angle selected with statement, rationale, and differentiation note.
- [ ] Angle is a position on the topic, not a rephrasing of the topic.
- [ ] Angle rationale cites a specific finding from research.

### Step 4: Audience Definition

- [ ] Primary audience description identifies a specific person (not a demographic bracket).
- [ ] Psychographic identifies a specific belief, value, or struggle — grounded in research.
- [ ] Awareness level set to one of the four valid enums — one level, not a range.
- [ ] At least two specific, real content calibration examples listed.
- [ ] `why_this_content_now` is specific and tied to the current moment.
- [ ] Audience definition is consistent with the selected angle.

### Step 5: Core Message Distillation

- [ ] At least ten candidate messages generated.
- [ ] Each candidate tested for singularity: one idea, no "and" or "but" making it two ideas.
- [ ] Selected message tested for specificity: it is a claim someone could disagree with.
- [ ] Selected message is relevant to the defined audience.
- [ ] `what_it_is_not` identifies a real adjacent misunderstanding, not a generic disclaimer.

### Step 6: Dimension Development

- [ ] 6a: Emotional journey — primary and secondary emotions defined; arc from open to close is a progression, not a static target; emotional payoff is specific.
- [ ] 6b: Curiosity mechanism — type selected; creation is specific; sustain approach described; resolution type and description complete.
- [ ] 6c: Retention strategy — mechanism selected and described for this specific piece; 2–4 specific secondary hooks defined; payoff location set.
- [ ] 6d: Hook direction — type selected; concept is specific enough to execute; `why_it_works` references the audience definition; `what_it_promises` is explicit.
- [ ] 6e: Story arc — structure selected; opening, development, tension point, and resolution all described specifically; `message_integration` explains where and how the message lands.
- [ ] 6f: Visual direction — mood described as a feeling, not a shot description; pacing set; at least two reference aesthetics listed; at least two specific key visual moments described; `what_to_avoid` populated.
- [ ] 6g: CTA strategy — `desired_action` is specific; placement set; `motivation` describes the viewer's emotional state at the CTA moment; `friction_reduction` is concrete; `what_they_get` is specific.
- [ ] Internal consistency check complete: all seven dimensions are mutually consistent with no unexplained contradictions.

### Step 7: Brief Assembly

- [ ] All ten dimensions compiled into the Creative Brief schema.
- [ ] Output metadata attached: `trace_id`, `department_id`, `version`, `produced_at`, `request_ref`.
- [ ] `revision_number` set to 0.
- [ ] `source_research_refs` lists all research outputs consulted.
- [ ] `status` set to `draft` before quality review.

### Step 8: Quality Review

- [ ] Gate 1 (Research Grounding) — passed.
- [ ] Gate 2 (Message Singularity) — passed.
- [ ] Gate 3 (Audience Specificity) — passed.
- [ ] Gate 4 (Hook and Retention Coherence) — passed.
- [ ] Gate 5 (Dimensional Consistency) — passed.
- [ ] Gate 6 (Traceability and Completeness) — passed.
- [ ] `status` updated to `complete` after all gates pass.
- [ ] Rework count recorded if any gate failed previously.

### Step 9: Delivery

- [ ] Brief delivered to Script Department.
- [ ] Brief delivered to Workflow Department.
- [ ] Delivery confirmation logged for both consumers.

### Step 10: Logging and Closure

- [ ] Activity log entry written with all required fields.
- [ ] Brief queue updated.
- [ ] Work item marked closed.

---

## Brief Revision Checklist

Complete when revising a returned brief.

- [ ] Revision request validated: all `dimensions_flagged` are specific and reference valid dimension names.
- [ ] If feedback is vague: clarification request sent to Script Department per SOP-C03.
- [ ] Dimensions to revise identified: only the flagged dimensions are revised.
- [ ] Revised dimensions re-evaluated against their relevant quality gate checks.
- [ ] Full brief re-run through all six quality gates.
- [ ] `revision_number` incremented.
- [ ] Revision note logged: original `brief_id`, dimensions revised, rationale for changes.
- [ ] Revised brief delivered to Script Department and Workflow Department.
- [ ] Activity log updated.

---

## Escalation Checklist

Complete when an escalation criterion is met.

- [ ] Escalation criterion documented specifically: which criterion was met.
- [ ] Work item ID and trace ID recorded.
- [ ] Full context assembled: original request, current workflow step, research used, gate results, rework history.
- [ ] Escalation notice formatted: work item ID, escalation type, criterion, context summary, recommended action.
- [ ] Escalation delivered to Platform Director.
- [ ] Workflow Department notified that the brief is escalated, with explanation.
- [ ] Work item status updated to `escalated`.
- [ ] Activity log entry written.

---

## Periodic Review Checklist

Complete monthly.

- [ ] Quality metrics reviewed against targets in `QUALITY_STANDARDS.md`.
- [ ] Gate failure distribution reviewed: which gates are failing most often?
- [ ] Script Department brief return log reviewed for feedback patterns.
- [ ] Angle audit: no two recently delivered briefs share an identical angle on the same topic.
- [ ] Vault knowledge currency verified: storytelling, psychology, and marketing entries accessed regularly are still `status: active`.
- [ ] Knowledge gaps reviewed for resolution progress.
- [ ] Open incidents from prior period resolved or tracked with owner and deadline.
