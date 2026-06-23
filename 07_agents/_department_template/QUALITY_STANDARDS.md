# Quality Standards — [DEPARTMENT NAME]

This file defines what "done" means for this department. Every output must pass every applicable quality gate before delivery. Quality is not negotiable — an output that fails a gate is not delivered. It is either reworked or escalated.

---

## Definition of Done

A unit of work is complete when all of the following are true:

- [ ] All required output fields are populated and non-empty.
- [ ] All output values conform to their defined types and constraints.
- [ ] All quality gates listed in this file have passed.
- [ ] Output metadata is complete (see `OUTPUTS.md` — Output Metadata).
- [ ] Activity log entry is written.
- [ ] Output has been delivered to all defined consumers.
- [ ] Delivery confirmation is recorded (where delivery method supports it).

---

## Quality Gates

Quality gates are ordered checks. A gate failure stops delivery and triggers the rework loop (see `WORKFLOW.md` — Step 4).

### Gate 1: [GATE NAME — e.g., Completeness]

| Attribute | Value |
|---|---|
| **Purpose** | [What this gate checks and why it matters] |
| **Applies To** | [Which outputs this gate applies to] |
| **Criteria** | [Specific, testable pass criteria — not vague descriptions] |
| **Failure Behavior** | [What happens if this gate fails — rework, escalate, or reject with reason] |

**Checks:**
- [ ] [CHECK 1 — e.g., All required fields in output schema are present and non-empty]
- [ ] [CHECK 2]
- [ ] [CHECK 3]

---

### Gate 2: [GATE NAME — e.g., Accuracy]

| Attribute | Value |
|---|---|
| **Purpose** | [Purpose] |
| **Applies To** | [Outputs] |
| **Criteria** | [Pass criteria] |
| **Failure Behavior** | [Failure behavior] |

**Checks:**
- [ ] [CHECK 1]
- [ ] [CHECK 2]

---

### Gate 3: [GATE NAME — e.g., Format Conformance]

| Attribute | Value |
|---|---|
| **Purpose** | [Purpose] |
| **Applies To** | [Outputs] |
| **Criteria** | [Pass criteria] |
| **Failure Behavior** | [Failure behavior] |

**Checks:**
- [ ] [CHECK 1]
- [ ] [CHECK 2]

---

### Gate 4: [GATE NAME — e.g., Traceability]

| Attribute | Value |
|---|---|
| **Purpose** | Every output must be traceable to its originating input. |
| **Applies To** | All outputs. |
| **Criteria** | `trace_id` and `input_ref` fields are present, non-empty, and correspond to a logged input record. |
| **Failure Behavior** | Output is quarantined. Escalation notice sent. |

**Checks:**
- [ ] `trace_id` is present and matches the originating input record.
- [ ] `input_ref` resolves to a real, logged input.
- [ ] `produced_at` timestamp is within the SLA window relative to input receipt.

---

## Rework Policy

When a quality gate fails, the rework policy applies:

| Attempt | Behavior |
|---|---|
| 1st failure | Log the failure. Return to core processing (Step 3) with gate failure context attached. |
| 2nd failure | Log the failure. Notify escalation owner. Return to core processing with extended context. |
| 3rd failure | Halt processing. Escalate to escalation owner with full failure log. Do not rework again without manual direction. |

**Maximum rework attempts:** [N] (before automatic escalation)

---

## Escalation Quality Threshold

A work item is automatically escalated (regardless of rework count) if:

- [AUTOMATIC ESCALATION CRITERION 1 — e.g., Output confidence score is below [X] after any rework attempt]
- [AUTOMATIC ESCALATION CRITERION 2 — e.g., The gate failure indicates a systemic problem rather than a one-off error]
- [AUTOMATIC ESCALATION CRITERION 3]

---

## Rejection Criteria

Some outputs are rejected outright and not reworked. A work item is rejected (not escalated) when:

- [REJECTION CRITERION 1 — e.g., Input was malformed at the source and cannot produce a valid output regardless of processing]
- [REJECTION CRITERION 2]

Rejected outputs are returned to the source with a structured rejection notice. See `SOPS.md` → Rejection Procedure.

---

## Quality Metrics

This department tracks the following quality metrics and reports them as part of its operational outputs.

| Metric | Description | Target | Alert Threshold |
|---|---|---|---|
| First-pass quality rate | Percentage of outputs that pass all gates without rework | [Target %] | Below [Alert %] |
| Rework rate | Percentage of outputs that require at least one rework cycle | Below [Target %] | Above [Alert %] |
| Escalation rate | Percentage of work items that reach escalation | Below [Target %] | Above [Alert %] |
| Rejection rate | Percentage of inputs rejected at intake | Below [Target %] | Above [Alert %] |
| Gate failure distribution | Which gates fail most often | Tracked for pattern detection | — |

---

## Quality Review Cadence

Beyond per-output quality gates, this department conducts periodic quality reviews:

| Review | Frequency | Purpose | Owner |
|---|---|---|---|
| Output quality audit | [Weekly / Monthly] | Sample review of recent outputs against standards | [ROLE] |
| Gate calibration review | [Quarterly] | Are quality gates still appropriate and correctly calibrated? | [ROLE] |
| Escalation pattern review | [Monthly] | What are escalations revealing about systemic issues? | [ROLE] |

---

## Continuous Improvement

When a quality review reveals a systemic issue:

1. Document the finding.
2. Determine root cause — is it an input problem, a processing problem, or a gate calibration problem?
3. Propose a specific change to the relevant document (`WORKFLOW.md`, `INPUTS.md`, gate criteria here).
4. Implement the change.
5. Version and log in `CHANGELOG.md`.
