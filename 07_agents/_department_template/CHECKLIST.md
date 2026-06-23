# Checklist — [DEPARTMENT NAME]

Checklists are operational tools, not aspirational documents. Every item on a checklist is a concrete, verifiable action. If an item cannot be checked off with confidence, the department does not advance to the next phase.

These checklists are used in `WORKFLOW.md` steps. Cross-reference step numbers when applicable.

---

## Pre-Work Checklist

Complete before accepting any live work items into the department's queue. Run this checklist when the department is first activated and after any tool or configuration change.

### Readiness

- [ ] All core tools listed in `TOOLS.md` are accessible and responding.
- [ ] All required knowledge vault sections are accessible and contain `status: active` entries.
- [ ] All required input channels are connected and receiving.
- [ ] All required output channels are connected and accepting delivery.
- [ ] Escalation path is verified — escalation owner is reachable.
- [ ] Activity log is writable.
- [ ] Department version in `VERSION.md` is current and matches deployed configuration.

### Configuration

- [ ] Input validation rules are loaded and current (match `INPUTS.md`).
- [ ] Quality gate criteria are loaded and current (match `QUALITY_STANDARDS.md`).
- [ ] SLA timers are configured correctly (match `WORKFLOW.md` — Timing and SLAs).
- [ ] Rework limit is set to the value defined in `QUALITY_STANDARDS.md`.

### First-Item Verification

- [ ] Process a test work item (not a live input) through the full workflow.
- [ ] Confirm test output meets all quality gates.
- [ ] Confirm test output is delivered correctly to the test consumer.
- [ ] Confirm activity log entry is written correctly.
- [ ] Remove test item from all queues and logs before accepting live work.

---

## Per-Work-Item Checklist

Complete for every work item. This checklist maps to `WORKFLOW.md` steps.

### Step 1: Intake and Validation

- [ ] Work item received from authorized source.
- [ ] Work item ID assigned and logged.
- [ ] All required fields present (see `INPUTS.md`).
- [ ] Input format conforms to expected schema.
- [ ] Input freshness within acceptable window (if applicable).
- [ ] Idempotency key checked — this is not a duplicate (if applicable).

### Step 2: Context Assembly

- [ ] All references in the input resolved.
- [ ] All optional inputs fetched (or absence noted).
- [ ] Full context object assembled.
- [ ] Any absent optional inputs noted in working metadata.

### Step 3: Core Processing

- [ ] Processing completed without hitting an escalation trigger.
- [ ] Draft output assembled with all required fields.
- [ ] Escalation triggers checked throughout processing — none met (or escalation initiated).

### Step 4: Quality Review

- [ ] Gate 1 ([GATE NAME]) — passed.
- [ ] Gate 2 ([GATE NAME]) — passed.
- [ ] Gate 3 ([GATE NAME]) — passed.
- [ ] Gate 4: Traceability — passed.
- [ ] All additional gates for this output type — passed.
- [ ] Rework count recorded (if applicable).

### Step 5: Output Delivery

- [ ] Output metadata attached (trace_id, department_id, version, produced_at, input_ref, status).
- [ ] Output delivered to all defined consumers.
- [ ] Delivery confirmation received and recorded (where applicable).

### Step 6: Logging and Closure

- [ ] Activity log entry written with all required fields.
- [ ] Work item marked as closed.
- [ ] Any flags or notes for the quality review cadence added.

---

## Escalation Checklist

Complete when escalation criteria are met before triggering escalation.

- [ ] Escalation criterion documented — which specific criterion was met.
- [ ] Work item ID recorded.
- [ ] Full context assembled (inputs, processing state, gate results, rework history).
- [ ] Escalation notice formatted with: work item ID, criterion met, context summary, recommended action.
- [ ] Escalation notice delivered to escalation owner defined in `ROLE.md`.
- [ ] Work item status updated to `escalated`.
- [ ] Activity log entry written.

---

## Post-Incident Checklist

Complete after any incident — quality failure pattern, SLA breach, tool outage, or escalation spike.

- [ ] Incident timeline documented.
- [ ] Root cause identified (input problem / processing problem / gate calibration problem / tool failure / other).
- [ ] Affected work items identified and their status confirmed.
- [ ] Impact on downstream consumers assessed and communicated.
- [ ] Corrective action determined.
- [ ] Corrective action implemented or assigned with owner and deadline.
- [ ] Relevant documentation updated (`WORKFLOW.md`, `QUALITY_STANDARDS.md`, `SOPS.md`, `TOOLS.md`).
- [ ] Version incremented in `VERSION.md`.
- [ ] Entry added to `CHANGELOG.md`.

---

## Periodic Review Checklist

Complete on the quality review cadence defined in `QUALITY_STANDARDS.md`.

- [ ] Quality metrics reviewed against targets.
- [ ] Escalation pattern reviewed.
- [ ] Gate failure distribution reviewed.
- [ ] Knowledge vault dependencies verified as current and `status: active`.
- [ ] Tool access and versions verified.
- [ ] Open incidents from previous period resolved or tracked.
- [ ] Any identified improvements documented and prioritized.
