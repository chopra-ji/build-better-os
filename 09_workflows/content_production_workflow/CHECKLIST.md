# Checklist — Content Production Workflow

Operational checklists for running the Content Production Workflow end to end. Use in sequence. Each checklist maps to a stage or gate.

---

## Workflow Initialization

Before Stage 1 begins:

- [ ] `workflow_run_id` assigned
- [ ] Run start timestamp recorded
- [ ] Idea source noted (spontaneous / research-triggered / comment-triggered / other)

---

## Stage 1 — Idea Record

- [ ] `core_idea` written as a single sentence
- [ ] `domain` selected from the ten monitored domains
- [ ] `target_audience` is specific — names a type of person, not a broad category
- [ ] `urgency` explicitly set
- [ ] `idea_id` and `created_at` assigned
- [ ] Decision made: advance to Research or hold
- [ ] If advance: Idea Record submitted to Research Department

---

## Gate 1 Check

- [ ] All required Idea Record fields present and valid
- [ ] Research Department has acknowledged receipt
- [ ] If Gate 1 failed: Idea Record returned to Founder with failure details

---

## Stage 2 — Research Department

- [ ] Research request submitted with Idea Record attached
- [ ] Urgency tier communicated
- [ ] Research output received
- [ ] Output type noted (Research Brief / Trend Report / Idea Report / other)

---

## Gate 2 Check

- [ ] `status` is `complete`
- [ ] `confidence` is `high` or `medium`
- [ ] `request_id` matches Idea Record `idea_id`
- [ ] Output addresses the Idea Record's core idea
- [ ] If `confidence` is `low`: Platform Director notified before proceeding

---

## Stage 3 — Creative Department

- [ ] Research Output submitted to Creative Department
- [ ] Creative Brief received

---

## Gate 3 Check

- [ ] All ten creative dimensions present and non-empty
- [ ] `status` is `complete`
- [ ] Core message is singular
- [ ] `request_id` traces back to Idea Record
- [ ] Creative Department's quality gates confirmed passed

---

## Stage 4 — Script Department

- [ ] Creative Brief submitted to Script Department
- [ ] Script Package received

---

## Gate 4 Check

- [ ] `script`, `hook`, and `cta` all present and non-empty
- [ ] `status` is `complete`
- [ ] Spoken word count ≥ 80 words
- [ ] `brief_id` traces back to Creative Brief
- [ ] All four Script Department quality gates confirmed passed

---

## Stage 5 — Creator Engine

- [ ] Script Package submitted to Creator Engine
- [ ] All eight stages of Creator Engine pipeline confirmed run
- [ ] Final Production Script received with `status: approved`

---

## Gate 5 Check

- [ ] `status` is `approved`
- [ ] All eight dimension scores ≥ 7
- [ ] `aggregate_score` ≥ 56
- [ ] `runtime_estimate` is within 45–60 seconds
- [ ] `caption` present and non-empty
- [ ] `change_log` present

---

## Stage 6 — Founder Review Package Assembly

- [ ] Founder Review Package assembled from Final Production Script
- [ ] Package delivered to Founder
- [ ] Founder notified with timestamp

---

## Stage 7 — Founder Review

- [ ] Founder Review decision received
- [ ] Decision is one of: `approved`, `revision_requested`, `rejected`
- [ ] If `revision_requested`: `description` and `route_to` both present
- [ ] If `rejected`: `reason` and `disposition` both present
- [ ] If `approved`: advance to Gate 7

### If Revision Requested:
- [ ] Revision Request routed to the correct upstream stage
- [ ] Upstream stage notified with revision details
- [ ] Revision count incremented on this workflow run
- [ ] If revision count ≥ 3 on the same issue: Platform Director notified

### If Rejected:
- [ ] Rejection reason logged
- [ ] `disposition` actioned (cancel or return to Stage 1)
- [ ] Workflow run closed with `status: cancelled` if cancelled

---

## Gate 7 Check

- [ ] Decision is `approved`
- [ ] Approval traces to correct `workflow_run_id`
- [ ] No pending revisions or open escalations

---

## Stage 8 — Production

- [ ] Approved Final Production Script distributed to creator
- [ ] Recording completed
- [ ] Editing completed
- [ ] On-screen text added per Creator Engine recommendations
- [ ] Production Package assembled
- [ ] `deviations` field completed (empty list if none)
- [ ] If deviations include hook, key claim, or CTA: flagged for new Founder Review before Gate 8

---

## Gate 8 Check

- [ ] `video_file` accessible and playable
- [ ] Video runtime within 45–60 seconds
- [ ] `caption` present
- [ ] `deviations` field present
- [ ] If significant deviations: new Founder approval obtained
- [ ] `workflow_run_id` on Production Package matches run

---

## Stage 9 — Publishing

- [ ] Caption reviewed and finalized
- [ ] Hashtags selected (if applicable)
- [ ] Cover frame selected
- [ ] Posting time confirmed (scheduled or immediate)
- [ ] Post published to Instagram as a Reel
- [ ] Post URL confirmed live
- [ ] Publish Record created with `post_url` and `published_at`
- [ ] `workflow_run_id` included in Publish Record

---

## Workflow Closure

- [ ] Publish Record logged
- [ ] All stage outputs archived under `workflow_run_id`
- [ ] Run end timestamp recorded
- [ ] Total run duration calculated (Stage 1 `created_at` → Stage 9 `published_at`)
- [ ] Workflow run marked `complete`

---

## Escalation Checklist

When any escalation is triggered at any stage:

- [ ] Escalation type and triggering condition recorded
- [ ] Current stage output state saved
- [ ] Platform Director notified with:
  - Workflow run ID
  - Stage where escalation occurred
  - Specific failure or trigger
  - Options for resolution
- [ ] Downstream stages halted
- [ ] Escalation timestamp recorded
- [ ] Resolution documented when complete
- [ ] Pipeline resumed or run closed per Platform Director direction
