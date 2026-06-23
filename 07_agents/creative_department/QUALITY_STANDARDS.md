# Quality Standards — Creative Department

This file defines what "done" means for a Creative Brief. Every brief passes every quality gate before delivery. A brief that fails a gate is reworked or escalated — it is never quietly delivered at lower quality.

Creative quality has a specific character: vagueness is the dominant failure mode. A brief that is technically complete but populated with generic descriptions is a quality failure as real as a brief with missing fields. Quality gates are designed to catch both.

---

## Definition of Done

A Creative Brief is complete when all of the following are true:

- [ ] All required schema fields are populated — no required field is empty or contains a placeholder.
- [ ] The core message is one sentence and contains exactly one idea.
- [ ] At least two rejected angles are documented with specific rationale.
- [ ] Every creative decision in every dimension cites its grounding in a research source from `source_research_refs`.
- [ ] All six quality gates have passed.
- [ ] Output metadata is complete: `trace_id`, `department_id`, `version`, `produced_at`, `request_ref`, `status: complete`.
- [ ] The brief has been delivered to Script Department and Workflow Department.
- [ ] The activity log entry is written.

---

## Quality Gates

Gates run in sequence during Workflow Step 8. A gate failure stops delivery and triggers the rework loop.

### Gate 1: Research Grounding

| Attribute | Value |
|---|---|
| **Purpose** | Every creative decision must be traceable to research evidence. The Creative Department does not make decisions on intuition — it makes decisions on research. This gate ensures no dimension is developed without grounding. |
| **Applies To** | All Creative Briefs |
| **Failure Behavior** | Rework. Return to the relevant workflow step — typically Step 2 (Research Assessment) or the specific dimension development step in Step 6. |

**Checks:**
- [ ] `source_research_refs` contains at least one `status: complete` research output.
- [ ] `content_angle.rationale` cites a specific finding from a research output in `source_research_refs` — not a general claim about the topic.
- [ ] `target_audience.why_this_content_now` is grounded in research — not editorial assumption.
- [ ] `core_message.proof` references specific evidence from research.
- [ ] `hook_direction.why_it_works` references the defined audience and a behavioral or psychological basis.
- [ ] `emotion.research_basis` cites research grounding for the emotional direction.
- [ ] No dimension relies solely on creative intuition without a corresponding research citation.

---

### Gate 2: Message Singularity

| Attribute | Value |
|---|---|
| **Purpose** | A brief with two core messages is a brief with no core message. This gate is the hardest to pass and the most important — the core message is the center of gravity for the entire brief. |
| **Applies To** | All Creative Briefs |
| **Failure Behavior** | Rework. Return to Workflow Step 5 (Core Message Distillation). |

**Checks:**
- [ ] `core_message.statement` is one sentence.
- [ ] `core_message.statement` contains one idea. Test: remove "and," "but," and "also" — if the message falls apart or produces two independent claims, it is two messages.
- [ ] `core_message.statement` is a specific claim, not a topic description. Test: can someone disagree with this message? If not, it is not a claim — it is a description.
- [ ] `core_message.what_it_is_not` is present and specific — it identifies a real adjacent misunderstanding, not a generic disclaimer.
- [ ] The content angle, story arc, and emotional payoff all serve the stated core message. A message about one idea that is surrounded by content pointing in a different direction is a coherence failure.

---

### Gate 3: Audience Specificity

| Attribute | Value |
|---|---|
| **Purpose** | A vague audience definition produces vague content. "Young professionals interested in productivity" is not a specific enough audience to brief against. This gate ensures the audience is defined with enough precision to guide execution. |
| **Applies To** | All Creative Briefs |
| **Failure Behavior** | Rework. Return to Workflow Step 4 (Audience Definition). |

**Checks:**
- [ ] `target_audience.primary_description` describes a specific person — what they do, what they believe, what they want — not a demographic bracket.
- [ ] `target_audience.psychographic` identifies a specific belief, value, or struggle — not a general interest area.
- [ ] `target_audience.awareness_level` is set to one of the four valid enums. It is not set to a range ("unaware to problem-aware") — the brief picks the single most accurate level.
- [ ] `target_audience.content_they_consume` lists at least two specific, real examples — not categories ("YouTube channels about business").
- [ ] `target_audience.why_this_content_now` is a specific reason tied to the current moment — not an evergreen rationale.
- [ ] The defined audience is consistent with the content angle. A mismatch (e.g., an `unaware` audience receiving a `solution_aware` brief) is a coherence failure.

---

### Gate 4: Hook and Retention Coherence

| Attribute | Value |
|---|---|
| **Purpose** | The hook makes a promise. The retention strategy delivers on that promise. The curiosity mechanism sustains the gap between them. These three dimensions must form a coherent system — a hook that promises something the retention strategy cannot deliver is a broken user experience. |
| **Applies To** | All Creative Briefs |
| **Failure Behavior** | Rework. Return to Steps 6b–6d. |

**Checks:**
- [ ] `hook_direction.concept` is specific enough to execute — it describes what happens or what is said, not a general approach.
- [ ] `hook_direction.what_it_promises` is explicit — the implicit promise the hook makes to a viewer who keeps watching.
- [ ] `retention_strategy.description` explains how the retention mechanism manifests in this specific piece — not a definition of the mechanism type.
- [ ] `retention_strategy.secondary_hooks` lists at least 2 specific internal re-engagement moments, not categories ("interesting facts").
- [ ] `curiosity_mechanism.creation` is consistent with the hook concept — the hook and curiosity mechanism work together, not independently.
- [ ] `curiosity_mechanism.sustain` describes a specific approach to keeping the question alive through the middle.
- [ ] The hook's implicit promise is resolvable by the content described in the story arc.

---

### Gate 5: Dimensional Consistency

| Attribute | Value |
|---|---|
| **Purpose** | A brief is a system, not a collection of independent fields. All ten dimensions must be internally consistent. A brief where the emotional direction contradicts the visual pacing, or where the story arc structure is incompatible with the retention mechanism, will produce incoherent content. |
| **Applies To** | All Creative Briefs |
| **Failure Behavior** | Rework. Return to the inconsistent dimension(s) in Step 6 and rebuild from the first inconsistent element. |

**Checks:**
- [ ] Visual `pacing` is compatible with the `emotional_journey` — a `rapid` pace cannot serve a `slow_burn` emotional arc without explicit justification.
- [ ] `story_arc.structure` is compatible with `retention_strategy.mechanism` — e.g., a `mystery_reveal` arc pairs naturally with `open_loop` retention; incompatible pairings need documented justification.
- [ ] `emotion.primary` is consistent with `hook_direction.type` — e.g., a `humor` emotional direction paired with a `data` hook type needs explicit justification.
- [ ] `cta_strategy.motivation` is consistent with `emotion.emotional_payoff` — the viewer should be in the emotional state described in `motivation` at the CTA moment.
- [ ] The `story_arc.resolution` lands the `core_message.statement` — the resolution must be the message made concrete.
- [ ] `content_angle.statement` and `target_audience.primary_description` are compatible — the angle must be meaningful to the defined audience.

---

### Gate 6: Traceability and Completeness

| Attribute | Value |
|---|---|
| **Purpose** | Every brief is traceable to its originating request and to the research that grounded it. This gate ensures the brief is fully logged and retrievable. |
| **Applies To** | All Creative Briefs |
| **Failure Behavior** | Quarantine the brief. Escalation notice sent to Platform Director. |

**Checks:**
- [ ] `trace_id` is present and matches the originating request record.
- [ ] `request_ref` resolves to a real, logged request from Workflow Department.
- [ ] `source_research_refs` contains at least one valid, logged research output ID.
- [ ] `department_id` is set to `creative_department`.
- [ ] `version` reflects the current department version from `VERSION.md`.
- [ ] `revision_number` is set to `0` for first delivery (or the correct increment for a revision).
- [ ] All required schema fields are present — no required field is empty.

---

## Rework Policy

| Attempt | Behavior |
|---|---|
| 1st failure | Log gate failure (gate number, specific checks failed). Return to the relevant workflow step with failure context attached. |
| 2nd failure | Log failure. Notify Platform Director. Return to workflow with extended context. |
| 3rd failure (maximum exceeded) | Halt. Escalate per `SOPS.md` → SOP-04 with full rework history. |

**Maximum rework attempts: 2** (before automatic escalation).

---

## Brief Revision Policy

When a delivered Creative Brief is returned by the Script Department, the following policy applies. This is separate from the internal quality gate rework policy above — revisions happen after delivery, not during production.

| Return | Behavior |
|---|---|
| 1st return | Validate the feedback (see `SOPS.md` → SOP-C03 for vague feedback). Revise only the flagged dimensions. Re-run all quality gates. Re-deliver with incremented `revision_number`. |
| 2nd return | Revise. Before re-delivering, notify Platform Director that the brief has been returned twice. Identify whether the root cause is brief quality, Script Department brief interpretation, or brief expectation misalignment. |
| 3rd return | Do not revise further. Escalate to Platform Director per `SOPS.md` → SOP-C01. Repeated returns indicate a systemic issue that requires human resolution. |

**Maximum revision cycles: 2** (before escalation). The full revision procedure is in `SOPS.md` → SOP-C01.

---

## Automatic Escalation Threshold

A brief is escalated regardless of rework count when:

- Gate 2 (Message Singularity) fails because the research does not surface a strong enough singular finding to build a message from — this is a research insufficiency problem, not a drafting problem.
- Gate 3 (Audience Specificity) fails because the topic is too broad to assign to a specific audience without topic narrowing — this requires editorial direction from Workflow Department.
- Gate 5 (Dimensional Consistency) fails twice on the same inconsistency — indicating the inconsistency is structural rather than a drafting error.
- Gate 6 (Traceability) fails — systemic logging failure requires Platform Director involvement.

---

## Quality Metrics

| Metric | Target | Alert Threshold |
|---|---|---|
| First-pass quality rate (all gates without rework) | ≥ 90% | Below 80% |
| Gate 2 (Message Singularity) failure rate | < 10% | Above 15% |
| Gate 3 (Audience Specificity) failure rate | < 10% | Above 15% |
| Gate 4 (Hook-Retention Coherence) failure rate | < 8% | Above 12% |
| Brief return rate from Script Department | < 5% | Above 10% |
| Rework rate | < 10% | Above 20% |
| Escalation rate | < 5% per quarter | Above 8% |

---

## Quality Review Cadence

| Review | Frequency | Purpose |
|---|---|---|
| Brief quality audit | Monthly — sample 20% of delivered briefs | Review against all six gates retrospectively. Identify if any gates are being passed that should have failed. |
| Script feedback analysis | Monthly | Analyze Script Department feedback on returned briefs. Identify which dimensions generate the most revision requests. |
| Angle diversity audit | Quarterly | Review briefs from the past quarter for angle repetition. No two briefs should share an identical angle on the same topic. |
| Dimensional pattern analysis | Quarterly | Which hook types, story arcs, and retention mechanisms are being selected most? Is the department over-relying on a small set of patterns? |
