# Workflow — Creative Department

This file documents how work flows through the Creative Department from input receipt to delivered Creative Brief. The standard workflow covers all brief requests. Exception paths are in `SOPS.md`.

---

## Standard Workflow

```
[BRIEF REQUEST RECEIVED]
          │
          ▼
  1. INTAKE & VALIDATION
          │
          ├─── validation fails ───► REJECT → return structured error (SOP-01)
          │
          ▼
  2. RESEARCH ASSESSMENT
          │
          ├─── research insufficient ───► REQUEST SUPPLEMENTARY RESEARCH (SOP-C02)
          │         └── research received ───► resume at step 2
          │
          ▼
  3. ANGLE EXPLORATION
          │
          ▼
  4. AUDIENCE DEFINITION
          │
          ▼
  5. CORE MESSAGE DISTILLATION
          │
          ├─── cannot reach singular message ───► ESCALATE (SOP-02)
          │
          ▼
  6. DIMENSION DEVELOPMENT
     (Hook · Retention · Story Arc · Visual Direction · Emotion · Curiosity · CTA)
          │
          ▼
  7. BRIEF ASSEMBLY
          │
          ▼
  8. QUALITY REVIEW
          │
          ├─── gate fails — attempt ≤ 2 ───► REWORK → return to relevant step
          │
          ├─── gate fails — attempt > 2 ───► ESCALATE (SOP-04)
          │
          ▼
  9. DELIVERY
          │
          ▼
 10. LOGGING & CLOSURE
```

---

## Step 1: Intake and Validation

**Purpose:** Confirm the request is complete, valid, and ready to brief before any creative work begins.

**Actions:**
1. Receive brief request from Workflow Department.
2. Assign a work item ID and log receipt with timestamp.
3. Validate all required fields per the schema in `INPUTS.md`.
4. Verify all referenced research outputs have `status: complete` in the output log.
5. Verify the topic is specific enough to brief — not a broad domain or category.
6. Verify the requested format is one of the six valid content format enums.

**Decision: Valid?**
- **Yes:** Proceed to Step 2.
- **No:** Reject per `SOPS.md` → SOP-01. Return structured error to Workflow Department. Close work item.

**Output:** Validated, logged brief request with work item ID assigned.

---

## Step 2: Research Assessment

**Purpose:** Evaluate whether the provided research outputs are sufficient to develop every creative dimension. This assessment happens before any creative work begins — a brief developed on insufficient research will fail quality gates.

**Actions:**
1. Read all research outputs referenced in `research_refs`.
2. Assess coverage across each of the ten creative dimensions:
   - **Audience:** Does the research characterize the target audience with enough specificity?
   - **Angle:** Does the research surface differentiated opportunities?
   - **Core Message:** Does the research provide a finding strong enough to build a singular message from?
   - **Hook:** Does the research reveal what the audience finds surprising, counterintuitive, or urgent?
   - **Emotion:** Does the research surface what the audience cares about and what they feel about the topic?
3. Identify any dimensions where research coverage is insufficient.

**Decision: Research sufficient for all dimensions?**
- **Yes:** Proceed to Step 3.
- **No:** Hold work item. Submit a supplementary research request to Research Department per `SOPS.md` → SOP-C02. Specify exactly which dimensions need additional coverage and what type of research is needed. Resume at Step 2 when supplementary research is delivered.

**Output:** Research assessment note (logged internally). Confirmation that all ten dimensions can be supported.

---

## Step 3: Angle Exploration

**Purpose:** Identify the strongest available angle for the topic — not by picking the first angle that comes to mind, but by systematically generating and evaluating multiple options.

**Actions:**
1. Generate at least five distinct angles on the topic using the research as the source of differentiation.
   - An angle is a position on a topic, not a rephrasing of the topic.
   - Each angle should serve a different audience segment, take a different perspective, or emphasize a different finding.
2. Evaluate each angle against three criteria:
   - **Audience alignment:** Does this angle resonate specifically with the target audience or an identifiable audience segment?
   - **Differentiation:** Is this angle underserved in the current content landscape on this topic?
   - **Resonance with research:** Is this angle grounded in a strong research finding rather than creative intuition?
3. Reject at minimum two angles with documented rationale.
4. Select the strongest angle. Document the selection rationale citing specific research evidence.

**Escalation trigger:** All generated angles are either saturated in the content landscape or cannot be grounded in the available research. Escalate per `SOPS.md` → SOP-02 with `escalation_type: ANGLE_EXHAUSTION`.

**Output:** Selected angle with statement, rationale, differentiation note, and at least two documented rejected angles.

---

## Step 4: Audience Definition

**Purpose:** Define the specific person this content is for with enough precision that a scriptwriter can hold that person in mind while writing.

**Actions:**
1. Using research signals and the selected angle, define the primary audience.
   - Who is this person specifically? What do they do? What do they believe?
   - What is their current awareness level on this topic?
   - What do they feel about this topic right now — before seeing this content?
2. Define the psychographic: what belief, value, or struggle makes this content relevant to them at this moment? This must be grounded in research — psychology domain findings, audience behavior signals, or prior content performance data.
3. Identify two to four examples of content this person already consumes. These are calibration references — they signal the sophistication level, style preference, and subject matter appetite of the audience.
4. Define `why_this_content_now`: what makes this topic relevant to this person at this moment?

**Decision: Audience defined specifically enough to guide execution?**
- A good test: would two different scriptwriters, given this audience definition, independently make similar creative choices? If not, the definition is not specific enough.
- If audience cannot be defined with this specificity: escalate per `SOPS.md` → SOP-02 with `escalation_type: AUDIENCE_UNDEFINABLE`. This usually indicates the topic itself needs narrowing.

**Output:** Complete audience definition with primary description, psychographic, awareness level, content calibration references, and why-this-content-now.

---

## Step 5: Core Message Distillation

**Purpose:** Reduce all research findings and the selected angle to a single, clear sentence. This is the center of gravity for the entire brief.

**Actions:**
1. Write ten candidate core message statements. Each must be one sentence. Each must be a specific claim, not a topic area.
2. Test each candidate against three criteria:
   - **Singularity:** Does it contain exactly one idea? If "and" or "but" appears in the message, it is likely two ideas.
   - **Specificity:** Is it a claim, or is it a description of a claim? "AI is changing everything" is a description. "Founders who adopt AI tooling in year one are 3x more likely to reach profitability" is a claim.
   - **Relevance to the audience:** Would the defined audience find this message meaningful and worth engaging with?
3. Select the strongest single message.
4. Write `what_it_is_not` — the adjacent idea or misunderstanding this message is explicitly not conveying. This prevents scriptwriters from hedging the message into ambiguity.

**Escalation trigger:** After ten attempts, no candidate reaches singularity and specificity. This indicates either the research is not strong enough to support a singular message (return to Step 2 with a supplementary research request) or the angle needs to be revisited (return to Step 3).

**Output:** Core message with statement, proof, and what-it-is-not.

---

## Step 6: Dimension Development

**Purpose:** Develop the remaining seven dimensions of the Creative Brief. These are developed together because they must be internally consistent — the emotional journey must serve the story arc; the curiosity mechanism must fit the retention strategy; the CTA must feel natural given the emotional payoff.

**Actions, in recommended order:**

**6a. Emotional Journey:** Define the primary and secondary emotions and the arc from open to close. This decision comes early because it informs the hook type, story arc, and visual direction.

**6b. Curiosity Mechanism:** Define how curiosity is created and sustained. The mechanism must be consistent with the retention strategy.

**6c. Retention Strategy:** Select the primary retention mechanism and describe how it manifests in this specific piece. Define 2–4 secondary hooks that re-engage the viewer at intervals through the middle.

**6d. Hook Direction:** Design the hook concept. It must be consistent with the hook type, serve the curiosity mechanism, and make a promise the rest of the content can keep.

**6e. Story Arc:** Define the narrative structure. The opening must deliver or build on the hook promise. The tension point must be placed to maximize the retention strategy's effectiveness. The resolution must land the core message.

**6f. Visual Direction:** Define the aesthetic mood, pacing, and key visual moments. Pacing must match the emotional journey and story arc rhythm.

**6g. CTA Strategy:** Define the desired action, its placement, its emotional motivation, and friction reduction. The CTA must feel like a natural continuation of the emotional payoff, not an interruption.

**Internal consistency check:** Before proceeding to Step 7, verify that all seven dimensions are mutually consistent. A mismatch (e.g., `pacing: slow_burn` with `primary emotion: urgency` without deliberate justification) is a quality failure.

**Output:** Complete set of all seven dimensions.

---

## Step 7: Brief Assembly

**Purpose:** Compile all ten completed dimensions into a Creative Brief conforming to the schema in `OUTPUTS.md`.

**Actions:**
1. Populate every required field in the Creative Brief schema.
2. Attach output metadata: `trace_id`, `department_id`, `version`, `produced_at`, `request_ref`.
3. Set `revision_number` to 0 (first delivery).
4. Set `source_research_refs` to all research outputs consulted during this brief.
5. Set `status` to `draft` — it becomes `complete` only after passing all quality gates.

**Output:** Draft Creative Brief with all fields populated.

---

## Step 8: Quality Review

**Purpose:** Validate the draft brief against all six quality gates before delivery. No brief leaves the department without passing this step.

**Actions:**
1. Run all six quality gates defined in `QUALITY_STANDARDS.md` in sequence.
2. Record pass/fail for each gate.

**Decision: All gates passed?**
- **Yes:** Set `status` to `complete`. Proceed to Step 9.
- **No:** Rework per `SOPS.md` → SOP-03. Return to the relevant workflow step with gate failure context. Maximum 2 rework attempts before escalation per SOP-04.

---

## Step 9: Delivery

**Actions:**
1. Deliver the completed brief to Script Department and Workflow Department via the output channel.
2. Log delivery confirmation.
3. If delivery fails: queue and retry per `SOPS.md` → SOP-05.

---

## Step 10: Logging and Closure

**Actions:**
1. Write activity log entry: work item ID, trace ID, topic, format, research refs, angle selected, processing time, gate results, rework count (if any), delivery confirmation, final status.
2. Update the brief queue.
3. Mark work item as closed.

---

## Brief Revision Workflow

**Trigger:** A Creative Brief is returned by the Script Department with specific, documented feedback.

```
[BRIEF RETURNED]
      │
      ▼
  1. Validate the revision request (per INPUTS.md — Brief Return schema)
      │
      ├─── vague feedback ───► return clarification request to Script Dept (SOP-C03)
      │
      ▼
  2. Assess the feedback: which dimensions need revision?
      ▼
  3. Revise only the flagged dimensions (do not rebuild the entire brief)
      ▼
  4. Re-run quality gates on revised brief
      ▼
  5. Deliver revised brief with incremented revision_number
      ▼
  6. Log revision with: original_brief_id, dimensions_revised, revision rationale
```

---

## Timing and SLAs

| Output | Urgent | Expedited | Standard |
|---|---|---|---|
| Creative Brief (first delivery) | Same business day | 2 business days | 5 business days |
| Creative Brief (revision) | Same business day | 1 business day | 2 business days |

SLA breach behavior: see `SOPS.md` → SOP-06.

---

## Concurrency

| Attribute | Value |
|---|---|
| **Max concurrent briefs** | 10 |
| **Long-form video briefs** | Maximum 3 concurrent (highest complexity) |
| **Queue discipline** | Priority-weighted: urgent > expedited > standard; within tier, FIFO |
| **Back-pressure behavior** | When queue reaches 10, new requests are queued. Workflow Department notified of expected start dates. |
