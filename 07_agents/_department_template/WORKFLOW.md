# Workflow — [DEPARTMENT NAME]

This file documents how work flows through this department from input receipt to output delivery. It is the operational map. Every standard scenario is covered here. Exception paths are covered in `SOPS.md`.

---

## Standard Workflow

The following describes the default operating flow for a single unit of work through this department.

```
[INPUT RECEIVED]
      │
      ▼
 1. INTAKE & VALIDATION
      │
      ├─── validation fails ───► REJECT → return structured error to source
      │
      ▼
 2. CONTEXT ASSEMBLY
      │
      ▼
 3. CORE PROCESSING
      │
      ├─── escalation criteria met ───► ESCALATE → notify escalation owner
      │
      ▼
 4. QUALITY REVIEW
      │
      ├─── quality gate fails ───► REWORK → return to step 3
      │                           (max rework attempts: [N])
      │
      ▼
 5. OUTPUT DELIVERY
      │
      ▼
 6. LOGGING & CLOSURE
```

---

## Step 1: Intake and Validation

**Purpose:** Confirm the incoming work item is complete and valid before any processing begins.

**Actions:**
1. Receive work item from input channel.
2. Validate against all rules defined in `INPUTS.md` — required fields, format, source authorization, freshness.
3. Assign a work item ID and log receipt.

**Decision: Input valid?**
- **Yes:** Proceed to Step 2.
- **No:** Reject the work item. Return a structured error to the source specifying which validation rule failed. Log the rejection. Stop.

**Output of this step:** Validated work item with assigned work item ID.

---

## Step 2: Context Assembly

**Purpose:** Gather all information this department needs to perform its work correctly. This step resolves references, fetches optional inputs, and assembles the full working context.

**Actions:**
1. Resolve any references in the input (e.g., fetch related records, retrieve linked documents).
2. Fetch optional inputs if available (see `INPUTS.md`).
3. Assemble the full context object that will be passed into core processing.
4. Note any optional inputs that are absent — log them for output metadata.

**Decision: Context sufficient?**
- **Yes:** Proceed to Step 3.
- **No (missing critical context):** [Define: does the department proceed with reduced context, or escalate? Document the threshold here.]

**Output of this step:** Complete context object for core processing.

---

## Step 3: Core Processing

**Purpose:** Perform the department's primary function on the assembled context.

**Actions:**
1. [PROCESSING ACTION 1 — describe what the department actually does here, specifically]
2. [PROCESSING ACTION 2]
3. [PROCESSING ACTION 3]
4. Assemble draft output with all required fields populated.

**Escalation triggers (check throughout processing):**
- [ESCALATION TRIGGER 1 — e.g., confidence below defined threshold]
- [ESCALATION TRIGGER 2 — e.g., input contains contradictory signals]
- [ESCALATION TRIGGER 3 — e.g., processing time exceeds internal SLA warning threshold]

**Decision: Escalation trigger met?**
- **Yes:** Proceed to escalation path (see `SOPS.md` → Escalation Procedure). Stop standard workflow.
- **No:** Proceed to Step 4.

**Output of this step:** Draft output package.

---

## Step 4: Quality Review

**Purpose:** Validate the draft output against all quality standards before delivery. This is an internal gate — the output does not leave this department until it passes.

**Actions:**
1. Run all quality checks defined in `QUALITY_STANDARDS.md`.
2. Record the result of each check.

**Decision: All quality gates passed?**
- **Yes:** Proceed to Step 5.
- **No:** Enter rework loop.
  - Identify which gate(s) failed.
  - Return to Step 3 with failure context.
  - Track rework attempt count. If rework attempts exceed the maximum defined in `QUALITY_STANDARDS.md` → Rework Policy, escalate via `SOPS.md` → SOP-04 instead of retrying.

**Output of this step:** Quality-validated output package with gate results attached.

---

## Step 5: Output Delivery

**Purpose:** Deliver the completed output to its defined consumer(s).

**Actions:**
1. Attach required output metadata (see `OUTPUTS.md` — Output Metadata).
2. Deliver to each consumer via the method defined in `OUTPUTS.md`.
3. Confirm receipt if delivery method supports acknowledgment.
4. If delivery fails: hold in outbound queue and apply retry policy.

**Decision: Delivery confirmed?**
- **Yes:** Proceed to Step 6.
- **No (consumer unavailable):** Queue output. Retry per SLA retry policy. Log as pending.

**Output of this step:** Delivered output with delivery confirmation record.

---

## Step 6: Logging and Closure

**Purpose:** Close the work item and produce the operational record.

**Actions:**
1. Write activity log entry with: work item ID, trace ID, input summary, output summary, processing time, quality gate results, delivery confirmation, and final status.
2. Update any department-level counters or metrics.
3. Mark work item as closed.

**Output of this step:** Completed activity log entry. Closed work item.

---

## Workflow Variants

Some inputs activate workflow variants that differ from the standard flow. Document those variants here.

### Variant: [VARIANT NAME]

**Trigger:** [Condition that activates this variant — e.g., priority flag is set on input]

**Difference from standard workflow:** [What changes — e.g., Step 2 is skipped, Step 5 uses a different delivery channel]

**When to use:** [Criteria]

---

## Timing and SLAs

| Workflow Step | Target Duration | Maximum Duration |
|---|---|---|
| Step 1: Intake and Validation | [TARGET] | [MAX] |
| Step 2: Context Assembly | [TARGET] | [MAX] |
| Step 3: Core Processing | [TARGET] | [MAX] |
| Step 4: Quality Review | [TARGET] | [MAX] |
| Step 5: Output Delivery | [TARGET] | [MAX] |
| Step 6: Logging and Closure | [TARGET] | [MAX] |
| **End-to-end (input to delivery)** | **[TARGET]** | **[MAX]** |

SLA breach behavior: see `SOPS.md` → SLA Breach Procedure.

---

## Concurrency

| Attribute | Value |
|---|---|
| **Max concurrent work items** | [Number or "unlimited"] |
| **Queue discipline** | [FIFO / Priority-weighted / Other] |
| **Back-pressure behavior** | [What the department does when queue exceeds capacity] |
