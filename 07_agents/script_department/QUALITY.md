# Quality — Script Department

---

## Definition of Done

A Script Package is complete when:

1. All components applicable to the content format are present in the package.
2. Every component field contains specific, final, non-placeholder content.
3. The script faithfully executes all ten dimensions of the Creative Brief.
4. All four quality gates have passed.
5. The package has been delivered to all consumers with notifications logged.

A package is not done if any field contains a placeholder, any applicable component is absent, or any quality gate has not been run and documented.

---

## Quality Gates

Gates are run in sequence after component assembly and before delivery. A gate failure stops the delivery. The package is reworked, then all gates are re-run from Gate 1.

---

### Gate 1: Brief Fidelity

**What it checks:** Every applicable component executes the corresponding brief dimension faithfully. No component contradicts the brief. No brief dimension is missing from the script.

| Dimension | Gate 1 Check |
|---|---|
| Content Angle | The script takes the position specified by the brief's angle statement — not a related or softer position |
| Target Audience | Word choice, assumed knowledge, and register match the brief's audience description |
| Core Message | One idea — the same idea in the brief — is delivered clearly in the script |
| Hook Direction | The hook type matches exactly; the hook concept executes what the brief specifies in the first 3–5 seconds |
| Retention Strategy | The mechanism described in the brief is active in the script; secondary hooks match the brief's list |
| Story Arc | Opening, development, tension, and resolution all follow the brief's arc specification |
| Visual Direction | B-roll Notes, Camera Notes, and Editing Notes are consistent with the brief's visual mood and pacing |
| Emotion | The emotional journey in the script matches the progression in the brief — opening, development, payoff |
| Curiosity Mechanism | The knowledge gap opens as specified; it is sustained through the middle; it resolves as specified |
| CTA Strategy | The CTA text matches the brief's desired action; placement matches exactly; friction reduction is executed |

**Pass condition:** All ten dimensions are executed faithfully. No dimension is missing from the script. No component invents creative direction not in the brief.

**Fail condition:** Any dimension is not executed, is executed differently than specified, or is absent from the script.

**Fail action:** Identify the specific dimension(s) and component(s) at fault. Rework those components. Re-run all gates from Gate 1.

---

### Gate 2: Component Completeness

**What it checks:** Every applicable component is present and every field within each component is populated with specific, non-placeholder content.

**Completeness rules:**
- "Applicable" means the format-component matrix in OUTPUTS.md says ✓ for this format.
- "Populated" means the field contains real, specific, production-usable content — not "TBD", "[INSERT X]", "to be determined", "as discussed", or any variant.
- A field that says "none" is populated. A field that says "[none if not applicable]" is not populated.
- Every list field must contain at least the minimum number of items specified in OUTPUTS.md.

**Per-component completeness checks:**

| Component | Completeness Requirement |
|---|---|
| 1. Script | `full_text` is complete; no placeholders; word count and runtime are accurate |
| 2. Hook | `hook_text` matches the Script exactly; `brief_promise_executed` is specific analysis, not brief restatement |
| 3. Scene Breakdown | All scenes in the Script are represented; every scene has all fields populated |
| 4. Voiceover | Narration only; no stage directions in the text; all fields populated |
| 5. Talking Head Notes | `energy_description` is specific to this piece, not generic; `emphasis_moments` cites specific script moments |
| 6. B-roll Notes | Every scene with significant on-camera content has B-roll coverage; all coverage descriptions are intent-based, not shot lists |
| 7. Camera Notes | Every scene has a camera note; `framing` rationale is tied to brief's visual direction |
| 8. Editing Notes | `music_direction` describes what the music must convey emotionally, not a genre; `cut_points` cites specific script moments |
| 9. On-screen Text | All text elements use final copy — no brackets; all `timing` fields reference scenes or timestamps |
| 10. Caption Draft | `caption_blocks` covers the complete script; `text` fields are accurate to the script |
| 11. CTA | `cta_text` is final; `placement` matches brief exactly; `brief_fidelity_note` documents the match |

**Pass condition:** All applicable components are present. All fields are populated with specific content.

**Fail condition:** Any applicable component is missing. Any required field contains a placeholder or is empty.

**Fail action:** Complete or populate the specific component(s) and field(s) at fault. Re-run all gates from Gate 1.

---

### Gate 3: Internal Consistency

**What it checks:** All components of the Script Package are consistent with each other. A component must not contradict another component.

**Consistency checks:**

| Check | What Is Being Verified |
|---|---|
| Hook → Script | The hook text in Component 2 matches the Script in Component 1 exactly — it is an excerpt, not a rewrite |
| Scene Breakdown → Script | The scene count, scene labels, and script excerpts in Component 3 match the Script in Component 1 |
| Voiceover → Script | Component 4 contains the narration from the Script with no additions or omissions |
| Talking Head Notes energy → Hook delivery | The energy direction in Component 5 is consistent with the hook's delivery direction in Component 2 |
| B-roll mood → Camera Notes mood | The mood requirements in Component 6 are consistent with the visual mood in Component 7 |
| Editing Notes rhythm → Talking Head pacing | The cut rhythm in Component 8 is consistent with the pacing direction in Component 5 |
| On-screen Text → Script | All text elements in Component 9 that are spoken words match the Script in Component 1 exactly |
| On-screen Text CTA → CTA Component | The `cta_text` in Component 11 matches any CTA on-screen text in Component 9 |
| Estimated runtimes | Duration estimates across Scene Breakdown, Voiceover, and Editing Notes are internally consistent |

**Pass condition:** No component contradicts another. Duration estimates align. Text excerpts match exactly.

**Fail condition:** Any component contradicts another. Any text excerpt does not match the Script.

**Fail action:** Identify the specific inconsistency. Resolve it by anchoring to the Script (Component 1) as the source of truth for all text, and to the brief for all creative decisions. Re-run all gates from Gate 1.

---

### Gate 4: Traceability

**What it checks:** Every significant scripting decision can be linked to a brief dimension. No scripting decision introduces a creative direction that is not in the brief.

**Traceability requirement:**

Every component field that represents a creative decision — not a format convention — must be traceable to a brief dimension. The traceability can be implicit (a B-roll mood that directly mirrors `brief.visual_direction.mood`) or explicit (a `brief_fidelity_note` that cites the brief field).

This gate is intentionally lighter than Gate 1 — it does not re-verify execution quality. It verifies that no orphaned creative decisions exist in the package.

**Untraceable decision types to look for:**
- A camera framing choice that comes from production preference rather than the brief's visual direction
- A tone direction in Talking Head Notes that comes from general content instinct rather than the brief's emotion fields
- An editing rhythm choice that contradicts the brief's visual pacing enum
- An on-screen text element that introduces a second core message not in the brief
- A B-roll section that requires footage serving a visual direction the brief did not specify

**Pass condition:** Every creative decision in every component has a clear link (implicit or explicit) to a brief dimension.

**Fail condition:** Any field contains a creative decision that cannot be linked to any brief dimension.

**Fail action:** If the decision is consistent with the brief but not traceable, add traceability documentation. If the decision contradicts or extends the brief, revise the field to execute the brief. Re-run all gates from Gate 1.

---

## Quality Failure Escalation

| Rework Attempt | Action |
|---|---|
| 1st failure | Identify gate and specific field(s) at fault. Rework. Re-run all gates. |
| 2nd failure | Identify root cause. If root cause is in the brief (a dimension is ambiguous or unexecutable), return the brief to Creative Department. If root cause is in scripting, rework. Re-run all gates. |
| 3rd failure | Escalate to Platform Director with gate failure report. The package is held. |

**Gate failure report format:**
```
gate_failure_report_id: string
script_package_ref:     string
brief_ref:              string
reported_at:            ISO 8601 timestamp
gate_failed:            enum [1 | 2 | 3 | 4]
failure_description:    string (specific — which field, what is wrong, what was attempted)
rework_attempts:        integer
root_cause:             string (assessment of whether the failure is in the brief or in the scripting)
escalation_recommendation: string (what the Script Department recommends: brief revision, cross-department review, or other)
```

---

## Rejection Criteria

A Script Package delivered to the production team is rejected (returned) when:

| Reason | Classification |
|---|---|
| An applicable component is missing | Package completeness failure — Script Department responsibility |
| A field contains placeholder text | Package completeness failure — Script Department responsibility |
| The hook does not execute the brief's hook concept | Brief fidelity failure — Script Department responsibility |
| The core message delivered by the script is not the one in the brief | Brief fidelity failure — Script Department responsibility |
| Two components contradict each other | Internal consistency failure — Script Department responsibility |
| A component requires creative clarification to use | Ambiguity failure — Script Department responsibility |

When a package is rejected by the production team, the Script Department receives the rejection with documented reason, logs it, and enters the revision workflow (see WORKFLOW.md — Revision Workflow).

Rejections are tracked and reviewed in the monthly quality cycle. Three rejections on the same dimension type within a quarter triggers a systemic review and a report to the Platform Director.

---

## Quality Metrics

| Metric | Target | Measurement |
|---|---|---|
| First-pass gate pass rate | ≥ 90% | Gate log: packages passing all 4 gates without rework, as percentage of all packages |
| Brief fidelity rate | ≥ 95% | Gate 1 log: packages where all 10 dimensions are faithfully executed on the first gate check |
| Package completeness rate | 100% | Gate 2 log: packages with all applicable components fully populated |
| Production rejection rate | < 5% | Rejection log: packages returned by production team as percentage of all delivered packages |
| Production clarification request rate | < 5% | Clarification log: delivered packages generating clarification requests as percentage of all delivered |

Metrics are reviewed monthly. Any metric outside its target for two consecutive months triggers a root-cause review and an improvement plan delivered to the Platform Director.

---

## Review Cadence

| Review | Frequency | Trigger |
|---|---|---|
| Per-package gate review | Every package, before delivery | Standard workflow |
| Monthly quality cycle | Monthly | Calendar — first week of each month |
| Systemic gap review | As needed | Same failure dimension appearing 3+ times in a quarter |
| Brief quality pattern review | Quarterly | Script Department reports brief-quality patterns to Platform Director for Creative Department feedback |
| Post-delivery clarification review | As needed | Any clarification request from production team triggers a root-cause review |
