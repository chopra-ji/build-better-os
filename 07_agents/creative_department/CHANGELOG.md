# Changelog — Creative Department

All significant changes to this department's operating design are recorded here in reverse chronological order.

---

## [1.0.0] — 2026-06-23

### Added

**Core Design**
- Department established with mission: "Transform research into compelling content ideas by making deliberate, defensible decisions about what story to tell, how to tell it, and why a specific audience should care."
- Department positioned as the translation layer between Research Department and Script Department, reporting to Platform Director.
- Department registered in `07_agents/README.md` Deployed Departments table.

**Creative Brief — Primary Output**
- Creative Brief defined as the single output type of this department.
- Complete 10-dimension schema specified in `OUTPUTS.md`.
- Creative Brief is the Script Department's primary instruction document.
- `revision_number` field enables tracking of brief versions through the revision cycle.
- `rejected_angles` field (minimum 2 required) documents that angle exploration was performed rigorously.

**The Ten Creative Dimensions**
1. Content Angle — including `statement`, `rationale`, `differentiation`, and `rejected_angles` (minimum 2).
2. Audience — including `primary_description`, `psychographic`, `awareness_level`, `content_they_consume`, `why_this_content_now`.
3. Core Message — one sentence, one idea, no exceptions. `what_it_is_not` prevents hedging.
4. Hook Direction — `type`, `concept`, `why_it_works`, `what_it_promises`.
5. Retention Strategy — `mechanism`, `description`, `payoff_location`, `secondary_hooks` (2–4 required).
6. Story Arc — `structure`, `opening`, `development`, `tension_point`, `resolution`, `message_integration`.
7. Visual Direction — `mood`, `pacing`, `reference_aesthetic`, `key_visual_moments`, `what_to_avoid`.
8. Emotion — `primary`, `secondary`, `emotional_journey`, `emotional_payoff`, `research_basis`.
9. Curiosity Mechanism — `type`, `creation`, `sustain`, `resolution`, `resolution_description`.
10. CTA Strategy — `desired_action`, `placement`, `motivation`, `friction_reduction`, `what_they_get`.

**Workflow**
- Standard 10-step workflow: Intake → Research Assessment → Angle Exploration → Audience Definition → Core Message → Dimension Development → Brief Assembly → Quality Review → Delivery → Logging.
- Separate Brief Revision Workflow for returned briefs.
- Concurrency limit: 10 active briefs; long-form video sub-limit: 3.

**Quality Gates (6)**
- Gate 1: Research Grounding — every creative decision cites a research source.
- Gate 2: Message Singularity — one sentence, one idea; no exceptions.
- Gate 3: Audience Specificity — specific enough to guide execution.
- Gate 4: Hook and Retention Coherence — hook, curiosity, and retention form a consistent system.
- Gate 5: Dimensional Consistency — all ten dimensions are mutually consistent.
- Gate 6: Traceability and Completeness — full metadata and schema compliance.
- Maximum rework attempts: 2.

**Standard Operating Procedures (17)**
- SOP-01 through SOP-11: Standard department SOPs (adapted from department template).
- SOP-C01: Brief revision process — formal revision workflow; revision limit of 2 before escalation.
- SOP-C02: Supplementary research request — how to request additional research when inputs are insufficient.
- SOP-C03: Vague revision feedback — feedback clarification template; 48-hour response window.
- SOP-C04: Angle exhaustion — what to do when no viable angle can be identified.
- SOP-C05: Message cannot be singularized — what to do when distillation fails after multiple attempts.
- SOP-C06: Editorial override conflict — documented process for handling directed creative decisions that conflict with research-grounded ones.

### Decisions Made

- **Creative Brief as the sole output type:** The department produces one output type with a fixed schema. This ensures every downstream consumer (Script Department, Workflow Department) receives a consistent, comparable document. It also makes brief quality auditable over time — all briefs share the same structure and can be compared.

- **`rejected_angles` is a required field with a minimum of two entries:** Requiring documented rejected angles proves that angle exploration was performed. Without this requirement, the temptation is to select the first viable angle and rationalize it post-hoc. Two documented rejections demonstrate genuine exploration.

- **Gate 2 (Message Singularity) is a hard gate with no exceptions:** A brief with two core messages is a brief with no core message. This is enforced at the quality gate level, not as guidance. The rework loop for Gate 2 failures returns to Workflow Step 5 (Core Message Distillation) every time.

- **SOP-C06 (Editorial Override Conflict) requires written confirmation before compliance:** When editorial direction overrides research-grounded creative judgment, that override must be documented. This creates an auditable trail of when creative decisions were research-driven versus editorially directed — a distinction that matters for performance analysis and accountability.

- **The Creative Department does not hold authority over topic selection:** Creative direction and topic selection are separated by design. The department that decides how to cover a topic is deliberately not the same department that decides which topics to cover. This separation prevents the Creative Department from steering editorial direction through its angle and message choices.

- **No TOOLS.md in this department:** The Creative Department's operational dependencies are vault domains (documented in `KNOWLEDGE.md`) and input/output channels (documented in `INPUTS.md` and `OUTPUTS.md`). It does not have the specialized tooling dependencies that warrant a dedicated TOOLS file.
