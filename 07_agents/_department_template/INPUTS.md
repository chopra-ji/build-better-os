# Inputs — [DEPARTMENT NAME]

This file defines everything this department needs to receive in order to begin and complete its work. An input is not just data — it includes triggers, context, permissions, and format requirements.

---

## What Triggers This Department

A unit of work enters this department when one of the following trigger conditions is met:

| Trigger | Source | Description |
|---|---|---|
| [TRIGGER NAME] | [SOURCE DEPARTMENT / SYSTEM / EVENT] | [What causes this trigger to fire] |
| [TRIGGER NAME] | [SOURCE DEPARTMENT / SYSTEM / EVENT] | [What causes this trigger to fire] |
| [TRIGGER NAME] | [SOURCE DEPARTMENT / SYSTEM / EVENT] | [What causes this trigger to fire] |

---

## Required Inputs

Required inputs must be present and valid before this department begins work. If a required input is missing, malformed, or fails validation, the work item is rejected and returned to the sender with a structured error.

### Input: [INPUT NAME A]

| Attribute | Value |
|---|---|
| **Source** | [DEPARTMENT / SYSTEM / EVENT THAT PROVIDES THIS] |
| **Format** | [Structured description — e.g., JSON object, markdown file, typed event payload] |
| **Required Fields** | [Field 1, Field 2, Field 3] |
| **Validation Rules** | [Rules that must pass before this input is accepted] |
| **Rejection Behavior** | [What happens if this input fails validation] |

### Input: [INPUT NAME B]

| Attribute | Value |
|---|---|
| **Source** | [DEPARTMENT / SYSTEM / EVENT THAT PROVIDES THIS] |
| **Format** | [Structured description] |
| **Required Fields** | [Field 1, Field 2] |
| **Validation Rules** | [Rules that must pass] |
| **Rejection Behavior** | [What happens if this input fails validation] |

---

## Optional Inputs

Optional inputs enrich this department's output but are not required to begin work. If absent, the department proceeds with reduced context and notes the absence in its output metadata.

| Input | Source | Effect If Absent |
|---|---|---|
| [OPTIONAL INPUT A] | [SOURCE] | [What the department does without it — e.g., applies defaults, flags as low-confidence] |
| [OPTIONAL INPUT B] | [SOURCE] | [Effect if absent] |

---

## Input Validation Rules

All inputs are validated against the following rules before work begins:

1. **Completeness:** All required fields are present and non-empty.
2. **Format conformance:** Input matches the expected schema or structure.
3. **Source authorization:** The input originates from an authorized source.
4. **Freshness:** [If applicable] The input was generated within the acceptable time window: `[TIME WINDOW]`.
5. **Idempotency key:** [If applicable] The input carries a unique identifier to prevent duplicate processing.

---

## Input Failure Handling

The table below summarizes failure behavior. The full step-by-step procedure for each failure type is documented in `SOPS.md`:
- Validation failures → **SOP-01**
- Duplicate inputs → **SOP-08**
- Rejection (unresolvable) → **SOP-09**

| Failure Type | Behavior |
|---|---|
| Missing required field | Reject input. Return structured error to source with field name and reason. See SOP-01. |
| Schema mismatch | Reject input. Return structured error with expected vs. received format. See SOP-01. |
| Unauthorized source | Reject input. Log the attempt. Do not return details to sender. See SOP-01. |
| Stale input | Reject input. Return structured error with timestamp comparison. See SOP-01. |
| Duplicate input | Acknowledge receipt. Do not reprocess. Return reference to original output. See SOP-08. |

---

## Input Volume and Frequency

| Attribute | Value |
|---|---|
| **Expected volume** | [e.g., 10–50 items per day] |
| **Peak volume** | [e.g., up to 200 items during publishing windows] |
| **Frequency** | [e.g., continuous, batch at 09:00 UTC, event-driven] |
| **Backlog handling** | [How the department handles a queue backlog — e.g., FIFO, priority-weighted] |

---

## Input Dependencies

Some inputs from this department depend on outputs from other departments completing first. Document that ordering here.

| This Input Requires | Which Means | Dependency On |
|---|---|---|
| [INPUT A] | [It cannot be ready until...] | [UPSTREAM DEPARTMENT completes its workflow step X] |
