# Quality Gates — Content Production Workflow

This file defines the pass/fail criteria at every stage transition. A gate is evaluated when a stage output is submitted to the next stage. A gate failure prevents advancement and triggers the defined response.

These are workflow-level gates — they govern handoffs between stages. The internal quality standards of each department and engine are documented in their respective systems and are enforced before a stage output is ever submitted here.

---

## Gate Structure

Each gate answers: **is this output ready to enter the next stage?**

Every gate has:
- **Pass criteria** — conditions that must all be true to advance
- **Fail response** — what happens when one or more criteria are not met
- **Escalation trigger** — conditions that bypass normal fail response and escalate directly

---

## Gate 1 — Idea Record → Research Department

**Evaluated at:** Research Department intake (start of Stage 2)

### Pass Criteria
- [ ] `core_idea` is a single sentence
- [ ] `domain` matches one of the ten monitored research domains
- [ ] `target_audience` is specific (names a type of person, not a broad demographic)
- [ ] `urgency` is explicitly set
- [ ] `idea_id` and `created_at` are present

### Fail Response
Return the Idea Record to the Founder with:
- Specific field(s) that failed
- Description of what is required
- Research Department does not begin work

### Escalation Trigger
None at Gate 1. Idea Records are the Founder's responsibility to submit correctly.

---

## Gate 2 — Research Output → Creative Department

**Evaluated at:** Creative Department intake (start of Stage 3)

### Pass Criteria
- [ ] Output type is a valid Research Department output type
- [ ] `status` is `complete` (not partial, escalated, or draft)
- [ ] `confidence` is `high` or `medium`
- [ ] `request_id` traces back to a valid, open Idea Record
- [ ] Output directly addresses the research question in the Idea Record
- [ ] All required Research Department metadata fields are present

### Fail Response
- `status` is not `complete`: return to Research Department for completion
- `confidence` is `low`: hold at Gate 2; notify Platform Director for approval to proceed or hold
- Output does not address the Idea Record's question: return to Research Department with specific gap identified

### Escalation Trigger
- A Research Output returns from Gate 2 with the same failure twice: Platform Director notified; idea reviewed for viability before further research is commissioned

---

## Gate 3 — Creative Brief → Script Department

**Evaluated at:** Script Department intake (start of Stage 4)

### Pass Criteria
- [ ] All ten creative dimensions are present and non-empty
- [ ] `status` is `complete`
- [ ] `request_id` traces back to the originating Research Output
- [ ] Brief has passed the Creative Department's own six quality gates (confirmed by Creative Department status on the document)
- [ ] Core message is singular — not multiple competing messages

### Fail Response
- Any dimension missing or empty: return to Creative Department with specific gap identified
- Multiple competing core messages: return to Creative Department for resolution
- Script Department does not begin work on a failed Creative Brief

### Escalation Trigger
- Creative Brief returns from Gate 3 with the same structural failure twice: Platform Director notified; Creative Department workflow reviewed

---

## Gate 4 — Script Package → Creator Engine

**Evaluated at:** Creator Engine intake (start of Stage 5)

### Pass Criteria
- [ ] `script` is present and non-empty
- [ ] `hook` is present and non-empty
- [ ] `cta` is present and non-empty
- [ ] `status` is `complete`
- [ ] `brief_id` traces back to a valid Creative Brief
- [ ] Script Package has passed all four Script Department quality gates (Brief Fidelity, Component Completeness, Internal Consistency, Traceability)
- [ ] Spoken word count ≥ 80 words

### Fail Response
- Required fields missing: return to Script Department with specific missing fields identified
- Word count < 80: flag to Platform Director before Creator Engine intake; potential under-brief
- Quality gate not passed: return to Script Department for completion

### Escalation Trigger
- Script Package returns from Gate 4 with quality gate failures after Script Department rework: Platform Director notified; Creative Brief reviewed as possible root cause

---

## Gate 5 — Final Production Script → Founder Review

**Evaluated at:** Stage 6 routing (before Founder Review Package assembly)

### Pass Criteria
- [ ] Creator Engine `status` is `approved`
- [ ] All eight dimension scores are ≥ 7
- [ ] `aggregate_score` ≥ 56
- [ ] `runtime_estimate` reflects 45–60 seconds
- [ ] `change_log` is present (may be empty if no changes were made)
- [ ] `caption` is present and non-empty
- [ ] No open escalations on the engine run

### Fail Response
- `status` is `escalated`: escalation must be resolved before Gate 5 is re-evaluated
- `status` is `rejected`: return to Script Department with Creator Engine run record; full re-draft required
- Any dimension score < 7: not a gate failure — this should not occur if the Creator Engine ran correctly; flag as a system issue and notify Platform Director
- Runtime outside 45–60 seconds: not a gate failure — this should not occur post-engine; flag as a system issue

### Escalation Trigger
- Creator Engine escalation unresolved for more than 2× the SLA: Platform Director intervenes to determine whether the Script Package should be reworked or the idea cancelled

---

## Gate 6 — Founder Review (internal to Stage 7)

**This is not a pass/fail gate — it is a human decision point.**

The Founder issues one of three structured decisions (Approval, Revision Request, Rejection). There is no pass/fail evaluation at this gate beyond confirming the Founder's decision document is complete and valid.

### Decision Document Validity Check
- [ ] `decision` is one of: `approved`, `revision_requested`, `rejected`
- [ ] If `revision_requested`: `description` and `route_to` are both present
- [ ] If `rejected`: `reason` and `disposition` are both present
- [ ] `reviewed_at` timestamp is present

An incomplete decision document is returned to the Founder for completion before any routing action is taken.

---

## Gate 7 — Founder Approval → Production

**Evaluated at:** Production intake (start of Stage 8)

### Pass Criteria
- [ ] Founder Review decision is `approved`
- [ ] `reviewed_at` timestamp is present
- [ ] Approval traces back to the correct workflow run ID
- [ ] No pending revision requests or unresolved escalations on this run

### Fail Response
- Decision is not `approved`: Production does not begin. Decision is routed per Stage 7 rules.
- Approval does not match workflow run ID: flag as administrative error; hold production until resolved

### Escalation Trigger
- Founder has issued revision requests on the same content piece three or more times: Platform Director notified; workflow run reviewed before any further revision cycles are commissioned

---

## Gate 8 — Production Package → Publishing

**Evaluated at:** Publishing intake (start of Stage 9)

### Pass Criteria
- [ ] `video_file` references an accessible, playable file
- [ ] Video runtime is within 45–60 seconds
- [ ] `caption` is present and non-empty
- [ ] `deviations` field is present (empty list is acceptable; missing field is not)
- [ ] If `deviations` contains changes to hook, key claims, or CTA: a new Founder Review approval is present for this production version

### Fail Response
- Video file not accessible: return to creator for re-delivery
- Runtime outside 45–60 seconds: return to creator; if over 60 seconds, requires Creator Engine re-run on the revised script
- Caption missing: return to creator
- Deviation in hook/claim/CTA without new Founder approval: hold; route Founder Review Package for the production version

### Escalation Trigger
- Video runtime exceeds 60 seconds and the approved script was within range: indicates a production deviation. Creator Engine re-run required on the actual recorded content.

---

## Gate Summary Table

| Gate | Between | Hard Blockers |
|---|---|---|
| Gate 1 | Idea → Research | Missing required fields; multi-sentence core_idea |
| Gate 2 | Research → Creative | status ≠ complete; confidence = low |
| Gate 3 | Creative → Script | Any dimension missing; multiple core messages |
| Gate 4 | Script → Creator Engine | Missing script/hook/cta; word count < 80 |
| Gate 5 | Engine → Founder Review | status ≠ approved; any dimension < 7 |
| Gate 6 | Founder Review (internal) | Incomplete decision document |
| Gate 7 | Approval → Production | Decision ≠ approved |
| Gate 8 | Production → Publishing | Inaccessible file; runtime > 60s; missing caption |
