# Workflow — Research Department

This file documents how work flows through the Research Department from input receipt to output delivery. It covers both the reactive workflow (responding to research requests) and the proactive workflow (monitoring-initiated research). Exception paths are in `SOPS.md`.

---

## Workflow A: Reactive Research (Request-Driven)

The standard flow for a research request submitted by another department.

```
[RESEARCH REQUEST RECEIVED]
          │
          ▼
  1. INTAKE & VALIDATION
          │
          ├─── validation fails ───► REJECT → return structured error to source (SOP-01)
          │
          ▼
  2. DEDUPLICATION CHECK
          │
          ├─── prior output is current and relevant ───► RETURN PRIOR OUTPUT → close request
          │
          ▼
  3. SCOPE CONFIRMATION (Competitive Analysis only: entity list approval)
          │
          ▼
  4. SOURCE ASSEMBLY
          │
          ├─── insufficient sources ───► ESCALATE → notify Platform Director (SOP-02)
          │
          ▼
  5. RESEARCH & SYNTHESIS
          │
          ├─── escalation criteria met ───► ESCALATE → notify Platform Director (SOP-02)
          │
          ▼
  6. OUTPUT DRAFTING
          │
          ▼
  7. QUALITY REVIEW
          │
          ├─── gate fails ─── attempt ≤ max ───► REWORK → return to step 5
          │
          ├─── gate fails ─── attempt > max ───► ESCALATE (SOP-04)
          │
          ▼
  8. OUTPUT DELIVERY
          │
          ├─── delivery fails ───► QUEUE & RETRY (SOP-05)
          │
          ▼
  9. VAULT CONTRIBUTION (where applicable)
          │
          ▼
 10. LOGGING & CLOSURE
```

---

## Step 1: Intake and Validation

**Purpose:** Confirm the request is complete, valid, and within scope before any research begins.

**Actions:**
1. Receive research request document via the request channel.
2. Assign a work item ID and log receipt with timestamp.
3. Validate all required fields against the schema in `INPUTS.md`.
4. Validate that the output type is appropriate for the research question.
5. Validate that the domain falls within the ten monitored domains.
6. Confirm the requesting department is an authorized source (see `ROLE.md`).

**Decision: Valid?**
- **Yes:** Proceed to Step 2.
- **No:** Reject per SOP-01. Return structured error to requesting department. Close the work item.

**Output:** Validated, logged request with work item ID assigned.

---

## Step 2: Deduplication Check

**Purpose:** Avoid conducting research that has already been completed and remains current.

**Actions:**
1. Search the output log for research outputs that answer substantially the same question.
2. If a prior output is found, assess its currency:
   - For fast-moving domains (Technology, AI, Creator Economy): prior output is current if ≤ 90 days old.
   - For slower-moving domains (Books, Frameworks, Psychology): prior output is current if ≤ 180 days old.
3. If a current, relevant prior output exists: return the prior output with a brief note on its age and remaining currency. Close the new request.
4. If the prior output is outdated: note it as a starting point and proceed with fresh research. Reference the prior output in the new output's `related_outputs` field.

**Decision: Current prior output exists?**
- **Yes:** Return prior output. Close request.
- **No:** Proceed to Step 3.

---

## Step 3: Scope Confirmation

**Purpose:** Resolve any ambiguity in scope before investing research time. Required for all output types; mandatory pre-research entity list approval for Competitive Analysis.

**Actions:**
1. If the research question has unresolved scope ambiguity, send a scope clarification request to the requesting department. Wait up to 24 hours for a response.
2. For Competitive Analysis requests: draft the entity list and submit it for requesting department approval before beginning full research.
3. If no scope ambiguity exists (most requests): proceed without delay.

**Decision: Scope clear?**
- **Yes:** Proceed to Step 4.
- **No (awaiting clarification):** Hold the work item. Resume when response received. Log hold with timestamp.

---

## Step 4: Source Assembly

**Purpose:** Identify and gather all primary and secondary sources needed for this research item.

**Actions:**
1. Identify required source types for the output type (primary literature, industry reports, case studies, direct observation, expert synthesis, etc.).
2. Access sources via the tools defined in `TOOLS.md`.
3. Evaluate each source for reliability tier (see `QUALITY_STANDARDS.md` → Source Reliability Standards).
4. Assemble source list with preliminary reliability assessments.
5. Identify any source gaps — types of evidence needed that are not yet available.

**Decision: Source quality and coverage sufficient?**
- **Yes:** Proceed to Step 5.
- **No (critical source gap):** Attempt to resolve gaps using alternative sources. If unresolvable within SLA, escalate per SOP-02 with the specific gap described.

---

## Step 5: Research and Synthesis

**Purpose:** Conduct the actual research and synthesize findings into a structured set of claims, evidence, and implications.

**Actions:**
1. Read and process assembled sources.
2. Extract relevant findings, data points, patterns, and developments.
3. Identify agreements and contradictions across sources. Where sources conflict, document both positions and assess which has stronger evidence.
4. Assign a confidence level to each key finding based on: source quality, source consensus, recency, and directness of evidence.
5. Identify implications for the requesting department — translate findings into practical meaning.
6. Identify the overall output confidence level.

**Escalation triggers:**
- Findings fundamentally contradict the requesting department's stated premise and the research question cannot be answered as asked.
- Source quality across all available sources is uniformly low, making a defensible confidence rating impossible.
- Research reveals information that is significantly more urgent or consequential than the request framing suggested — warrants a delivery priority upgrade.
- Processing time is projected to exceed SLA due to source complexity.

**Decision: Escalation trigger met?**
- **Yes:** Proceed per SOP-02. Stop standard workflow.
- **No:** Proceed to Step 6.

**Output:** Complete synthesis notes with findings, evidence, source references, confidence assessments, and implications.

---

## Step 6: Output Drafting

**Purpose:** Convert synthesis notes into a structured output document conforming to the schema defined in `OUTPUTS.md`.

**Actions:**
1. Select the schema for the requested output type from `OUTPUTS.md`.
2. Populate every required field. No required field may be left empty.
3. Write the `confidence` and `confidence_note` fields with honesty — if confidence is low, state it clearly.
4. Populate `implications`, `caveats`, and `sources` sections completely.
5. Attach all required output metadata.

**Output:** Draft output document with all required fields populated.

---

## Step 7: Quality Review

**Purpose:** Validate the draft output against all quality standards before delivery. No output leaves the department without passing this step.

**Actions:**
1. Run all quality gates defined in `QUALITY_STANDARDS.md` in sequence.
2. For Knowledge Updates: also run the vault-specific Gate 6.
3. Record pass/fail result for each gate.

**Decision: All gates passed?**
- **Yes:** Proceed to Step 8.
- **No:** Rework per SOP-03. Return to Step 5 or Step 6 with gate failure context. Track rework attempt count.
  - Maximum rework attempts: **2** (defined in `QUALITY_STANDARDS.md` → Rework Policy).
  - If rework attempts exceeded: escalate per SOP-04.

**Output:** Quality-validated output with gate results attached.

---

## Step 8: Output Delivery

**Purpose:** Deliver the completed output to all defined consumers.

**Actions:**
1. Confirm delivery targets per the output type table in `OUTPUTS.md`.
2. Deliver output to each consumer via the designated channel.
3. Log delivery confirmation.
4. If delivery fails: queue and retry per SOP-05.

---

## Step 9: Vault Contribution

**Purpose:** Ensure that research outputs which produce vault-worthy knowledge are captured in the institutional knowledge base.

**Actions:**
1. Assess whether the output contains findings that warrant a Knowledge Update.
   - Framework Summaries: always generate a vault entry.
   - Technology Reports: generate a vault entry for the core technology assessed.
   - Research Briefs and Trend Reports: generate a vault entry when findings are novel, significant, and likely to be referenced again.
   - Competitive Analyses and Idea Reports: generate vault entries only when findings contain durable reference knowledge.
2. If a vault entry is warranted: draft and submit the Knowledge Update following the vault templates.
3. If a vault entry is not warranted: document the rationale in the activity log.

---

## Step 10: Logging and Closure

**Actions:**
1. Write activity log entry: work item ID, trace ID, output type, domain, processing time, quality gate results, rework count (if any), delivery confirmation, vault contribution (if any), and final status.
2. Update the research queue.
3. Mark the work item as closed.

---

## Workflow B: Proactive Monitoring (Monitoring-Triggered)

The flow for research produced without a request — initiated by the domain monitoring cycle.

```
[MONITORING TRIGGER FIRES]
          │
          ▼
  1. SIGNAL ASSESSMENT: does this meet the significance threshold?
          │
          ├─── no ───► LOG SIGNAL → continue monitoring. No output produced.
          │
          ▼
  2. OUTPUT TYPE SELECTION: Trend Report or Knowledge Update?
          │
          ▼
  3. FOLLOW WORKFLOW A FROM STEP 4 (no intake validation needed; no request ID)
```

For proactive outputs: `request_id` is set to `proactive_monitoring`. The monitoring trigger is logged as the input reference.

---

## Timing and SLAs

| Urgency Tier | Research Brief | Trend Report | Competitive Analysis | Idea Report | Technology Report | Framework Summary | Tool Review |
|---|---|---|---|---|---|---|---|
| Urgent | Same day | 3 days | 4 days | 2 days | 6 days | 1 day | 1 day |
| Expedited | 24 hours | 3 days | 4 days | 2 days | 6 days | 1 day | 1 day |
| Standard | 48 hours | 5 days | 7 days | 4 days | 10 days | 3 days | 3 days |

SLA breach behavior: see `SOPS.md` → SOP-06.

---

## Concurrency

| Attribute | Value |
|---|---|
| **Max concurrent work items** | 8 (across all output types) |
| **Technology/AI Reports** | Maximum 2 concurrent (high source density) |
| **Research Briefs** | Maximum 4 concurrent |
| **Queue discipline** | Priority-weighted by urgency tier; within tier, FIFO |
| **Back-pressure behavior** | When queue reaches 8 active items, new incoming requests are logged as queued, requesting departments are notified of expected start date, and Platform Director is informed |
