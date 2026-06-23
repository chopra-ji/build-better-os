# Outputs — [DEPARTMENT NAME]

This file defines everything this department produces. An output is a deliverable with a defined format, quality standard, and consumer. Nothing leaves this department without passing the quality gates defined here and in `QUALITY_STANDARDS.md`.

---

## Primary Outputs

Primary outputs are the core deliverables this department produces. They are produced on every standard work cycle.

### Output: [OUTPUT NAME A]

| Attribute | Value |
|---|---|
| **Description** | [What this output is and what it represents] |
| **Format** | [Structured description — e.g., typed event, structured document, JSON payload] |
| **Fields** | [Field 1 (type, description), Field 2 (type, description), ...] |
| **Consumer(s)** | [DEPARTMENT / SYSTEM that receives this output] |
| **Delivery Method** | [How it is delivered — e.g., event emission, API call, written to shared store] |
| **SLA** | [Maximum acceptable time from input receipt to output delivery] |
| **Quality Gate** | See `QUALITY_STANDARDS.md` → Gate [GATE NAME] |

### Output: [OUTPUT NAME B]

| Attribute | Value |
|---|---|
| **Description** | [What this output is] |
| **Format** | [Structured description] |
| **Fields** | [Field 1, Field 2, ...] |
| **Consumer(s)** | [DEPARTMENT / SYSTEM] |
| **Delivery Method** | [Delivery method] |
| **SLA** | [SLA] |
| **Quality Gate** | See `QUALITY_STANDARDS.md` → Gate [GATE NAME] |

---

## Secondary Outputs

Secondary outputs are produced in specific scenarios, not every work cycle.

| Output | Scenario | Consumer | Format |
|---|---|---|---|
| [SECONDARY OUTPUT A] | [When it is produced — e.g., escalation triggered] | [CONSUMER] | [FORMAT] |
| [SECONDARY OUTPUT B] | [Scenario] | [CONSUMER] | [FORMAT] |

---

## Operational Outputs

Operational outputs are metadata, logs, and signals this department produces about its own operation. They are consumed by platform-level observability, not by business-domain consumers.

| Output | Description | Consumer |
|---|---|---|
| Activity log entry | Structured record of every work item processed, with outcome | Platform observability layer |
| Escalation notice | Structured notification when escalation criteria are met | Escalation owner (see `ROLE.md`) |
| Error report | Structured error with code, context, and originating input reference | Source department / error handling system |
| Quality rejection notice | Structured notice when an output fails a quality gate before delivery | Internal — triggers rework loop |

---

## Output Metadata

Every output this department produces must carry the following metadata fields, regardless of format:

| Field | Type | Description |
|---|---|---|
| `trace_id` | string | Propagated from the originating input. Enables end-to-end traceability. |
| `department_id` | string | Identifier for this department. |
| `version` | string | Version of this department's operating design that produced the output. |
| `produced_at` | ISO 8601 timestamp | When the output was produced. |
| `input_ref` | string | Reference to the input that triggered this output. |
| `status` | enum | One of: `complete`, `partial`, `escalated`, `rejected`. |

---

## Output Guarantees

This department guarantees:

- **Completeness:** Every required field in the output schema is populated before delivery.
- **Traceability:** Every output can be traced back to its originating input via `trace_id` and `input_ref`.
- **Idempotency:** Delivering the same output twice does not cause duplicate downstream effects. Outputs carry unique identifiers.
- **Quality gate passage:** No output is delivered without passing the quality gates defined in `QUALITY_STANDARDS.md`.

This department does NOT guarantee:

- [NON-GUARANTEE 1 — e.g., "Downstream consumer availability — if a consumer is offline, the output is queued."]
- [NON-GUARANTEE 2]

---

## Output Failure Scenarios

| Failure Scenario | Behavior |
|---|---|
| Quality gate fails | Output is not delivered. Rework loop is triggered. Logged as quality failure. |
| Consumer unavailable | Output is held in outbound queue. Retry per SLA retry policy. |
| Output schema violation detected post-production | Output is quarantined. Escalation notice sent. Manual review required. |
| SLA breach imminent | Escalation notice sent to escalation owner before SLA is missed. |
