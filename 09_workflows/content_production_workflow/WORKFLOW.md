# Workflow — Content Production

This file documents all nine stages of the Content Production Workflow. For each stage: the owner, what triggers it, what work is performed, what it produces, and what governs escalation. Pass/fail criteria for each stage transition are in `QUALITY_GATES.md`.

---

## Stage 1 — Idea

**Owner:** Founder  
**Type:** Human

### What Triggers This Stage
An idea is an observation, a question, an experience, or a signal that suggests a piece of content worth making. It can come from anywhere: a conversation, a mistake, a trend spotted in the research vault, a comment on a previous reel, or a direct prompt from another department's output.

### What Happens Here
The Founder captures the idea in a structured Idea Record (see `INPUTS.md`). The Idea Record is not a brief — it is a raw input. Its purpose is to give downstream stages enough context to work with, not to pre-solve the content.

The Founder makes one decision at this stage: is this idea worth routing through the full workflow? If yes, the Idea Record is submitted to the Research Department. If no, the idea is logged but not advanced.

### What This Stage Produces
An **Idea Record** — a structured document containing:
- A one-sentence statement of the core idea
- The domain it belongs to
- The intended audience
- Any specific angles, questions, or constraints the Founder wants respected
- Urgency tier (standard / expedited / urgent)

### Acceptance Criteria to Advance
See `QUALITY_GATES.md` → Gate 1. The Idea Record must pass intake validation before the Research Department accepts it.

### Escalation
None at this stage. The Founder owns the decision to advance or hold any idea.

---

## Stage 2 — Research Department

**Owner:** Research Department  
**Type:** AI  
**Documentation:** `07_agents/research_department/`

### What Triggers This Stage
Receipt of a validated Idea Record from Stage 1.

### What Happens Here
The Research Department receives the Idea Record and produces the research output appropriate to the idea's scope. For most content ideas, this is a Research Brief. For trend-driven or competitive content, it may be a Trend Report or Idea Report.

The Research Department operates according to its own documented workflow (`07_agents/research_department/WORKFLOW.md`). This workflow document does not override that — it records what the Content Production Workflow requires of the Research Department.

### What This Stage Produces
A **Research Output** — one or more of:
- Research Brief (most common)
- Trend Report
- Idea Report
- Framework Summary

The output type is determined by the Research Department based on the Idea Record scope.

### Acceptance Criteria to Advance
See `QUALITY_GATES.md` → Gate 2. The Research Output must meet the Research Department's quality standards and must directly address the research question implied by the Idea Record.

### Escalation
Escalation within this stage is handled by the Research Department per its own documented escalation path. If the Research Department cannot produce a usable output (insufficient sources, out-of-scope topic, SLA breach), it escalates to the Platform Director. The Platform Director determines whether the idea is held, redirected, or cancelled.

---

## Stage 3 — Creative Department

**Owner:** Creative Department  
**Type:** AI  
**Documentation:** `07_agents/creative_department/`

### What Triggers This Stage
Receipt of a validated Research Output from Stage 2.

### What Happens Here
The Creative Department receives the Research Output and produces a Creative Brief — a structured document that defines the ten creative dimensions of the content piece (angle, audience, core message, hook direction, retention strategy, story arc, visual direction, emotion, curiosity mechanism, and CTA strategy).

The Creative Brief is the contract between the Creative Department and the Script Department. Everything the Script Department produces must trace back to it.

### What This Stage Produces
A **Creative Brief** containing all ten creative dimensions, fully populated. See `07_agents/creative_department/OUTPUTS.md` for the complete schema.

### Acceptance Criteria to Advance
See `QUALITY_GATES.md` → Gate 3. The Creative Brief must pass the Creative Department's own quality gates and must be traceable to the Research Output it was built from.

### Escalation
Handled by the Creative Department per `07_agents/creative_department/WORKFLOW.md`. If a Research Output is insufficient to support a Creative Brief, the Creative Department returns it to the Research Department with a structured explanation. The Research Department re-runs or escalates.

---

## Stage 4 — Script Department

**Owner:** Script Department  
**Type:** AI  
**Documentation:** `07_agents/script_department/`

### What Triggers This Stage
Receipt of a validated Creative Brief from Stage 3.

### What Happens Here
The Script Department receives the Creative Brief and produces a Script Package — a complete production document including the full script, hook, scene breakdown, voiceover notes, talking head notes, b-roll notes, camera notes, editing notes, on-screen text, caption draft, and CTA.

The Script Package is a production-ready document in structure. It is not yet optimized for Instagram performance — that is the Creator Engine's responsibility.

### What This Stage Produces
A **Script Package** containing all applicable components for the format. See `07_agents/script_department/OUTPUTS.md` for the complete schema and format-component applicability matrix.

### Acceptance Criteria to Advance
See `QUALITY_GATES.md` → Gate 4. The Script Package must pass the Script Department's four quality gates (Brief Fidelity, Component Completeness, Internal Consistency, Traceability) and must include all required fields for Creator Engine intake.

### Escalation
Handled by the Script Department per `07_agents/script_department/WORKFLOW.md`. If the Creative Brief is insufficient to support a complete Script Package, the Script Department returns it to the Creative Department with a structured explanation.

---

## Stage 5 — Creator Engine

**Owner:** Creator Engine  
**Type:** AI  
**Documentation:** `08_creator_engine/`

### What Triggers This Stage
Receipt of a validated Script Package from Stage 4.

### What Happens Here
The Creator Engine runs the Script Package through its eight-stage review pipeline: Hook, Retention, Founder Voice, Social Language, Comment Engineering, Shareability, Build Better Brand, and Instagram Optimization. Each stage scores the script, applies optimizations where needed, and advances or escalates.

The Creator Engine enforces the 45–60 second runtime constraint. If a script exceeds 60 seconds, the Runtime Compression Protocol runs before the script can advance.

The Creator Engine does not change the ideas or the core message. It changes the delivery, language, structure, and timing.

### What This Stage Produces
A **Final Production Script** — the Creator Engine's approved output — containing:
- Optimized spoken script
- All eight dimension scores
- Aggregate score
- Change log of all modifications made
- Runtime estimate
- Production notes for the creator
- Caption copy, finalized

### Acceptance Criteria to Advance
See `QUALITY_GATES.md` → Gate 5. The Final Production Script must carry `status: approved` from the Creator Engine. A script with `status: escalated` or `status: rejected` does not advance until the escalation is resolved.

### Escalation
Handled by the Creator Engine per `08_creator_engine/OPTIMIZATION_PIPELINE.md`. Escalations are returned to the Platform Director with a full run record identifying the failing dimension and what was attempted.

---

## Stage 6 — Final Production Script

**Owner:** Platform Director (routing)  
**Type:** Handoff checkpoint

### What This Stage Is
Stage 6 is not a work stage — it is the formal checkpoint between AI production and human review. The Final Production Script is packaged for Founder Review and routed to Stage 7.

### What Happens Here
1. The Final Production Script is compiled into the Founder Review Package (see `OUTPUTS.md` → Stage 6).
2. The Founder Review Package is delivered to the Founder.
3. The Founder is notified that a script is ready for review.

### What This Stage Produces
A **Founder Review Package** containing:
- Final Production Script (spoken content)
- Creator Engine dimension scores and change log
- Runtime estimate
- Caption copy
- Production notes

### Acceptance Criteria to Advance
The Founder Review Package is complete and delivered. No quality evaluation happens at this stage — evaluation is the Founder's job in Stage 7.

---

## Stage 7 — Founder Review

**Owner:** Founder  
**Type:** Human

### What Triggers This Stage
Receipt of the Founder Review Package from Stage 6.

### What Happens Here
The Founder reads the Final Production Script and makes one of three decisions:

**Approve** — The script is accurate, authentic, and ready to record. It advances to Stage 8.

**Request Revision** — The script has a specific problem the Founder identifies. The Founder documents the issue using the Revision Request format (see `INPUTS.md` → Stage 7 Revision Request). The Revision Request is routed to the appropriate upstream stage for resolution.

**Reject** — The script is fundamentally wrong — wrong angle, wrong message, or based on a premise the Founder no longer supports. The Founder documents the reason and the idea is either cancelled or returned to Stage 1 for reframing.

### What the Founder Reviews For
Founder Review is not a quality review. The Creator Engine has already handled quality. The Founder reviews for:

- **Factual accuracy.** Are all specific claims, numbers, and dates correct?
- **Personal authenticity.** Does this sound like the Founder? Would the Founder say this?
- **Claim ownership.** Is the Founder comfortable making every claim in this script publicly?
- **Strategic fit.** Does this piece of content belong in the content mix right now?

The Founder does not review for hook strength, retention architecture, or Instagram optimization — those are the Creator Engine's domain.

### SLA
Standard: 24 hours from receipt of Founder Review Package.  
If the Founder is unavailable for more than 48 hours, the Platform Director is notified and the work item is flagged as held.

### What This Stage Produces
One of:
- **Approval** — advances to Stage 8
- **Revision Request** — routed upstream with documented reason
- **Rejection** — idea cancelled or returned to Stage 1

### Revision Routing
| Problem Type | Routed To |
|---|---|
| Factual error in script content | Script Department |
| Wrong angle or core message | Creative Department (may also require Research) |
| Language doesn't sound like me | Script Department (Founder Voice revision) |
| Wrong premise entirely | Stage 1 (idea reframe) or cancel |

### Acceptance Criteria to Advance
Founder has issued written approval. No script advances to Production on a verbal or implied approval.

### Escalation
If a script returns from Founder Review more than twice with revision requests on the same issue, the Platform Director is notified. Repeated revision cycles on the same problem indicate a breakdown in an upstream stage that requires diagnosis, not iteration.

---

## Stage 8 — Production

**Owner:** Creator (Founder or designated producer)  
**Type:** Human

### What Triggers This Stage
Founder approval from Stage 7.

### What Happens Here
The creator records the reel using the approved Final Production Script. Production includes:
- Recording the talking head footage
- Recording or sourcing b-roll footage (if applicable)
- Editing to the approved script
- Adding on-screen text per the Creator Engine's recommendations
- Reviewing the produced video against the script

Production must stay faithful to the approved script. If the creator deviates significantly from the script during recording, the deviation must be documented. A significant deviation is any change to the hook, a key claim, the CTA, or a section that affects the comment or share trigger.

### What This Stage Produces
A **Production Package** containing:
- Final edited video file
- Caption copy (from the Final Production Script)
- Metadata: content topic, domain, workflow run ID, script version
- Production notes: any deviations from the approved script

### Acceptance Criteria to Advance
See `QUALITY_GATES.md` → Gate 8.

### Escalation
If the creator discovers during recording that a factual claim in the approved script is incorrect, recording stops. The claim is flagged to the Script Department for correction. The revised script requires a new Founder Review (Stage 7) before production resumes.

---

## Stage 9 — Publishing

**Owner:** Platform Director or designated publisher  
**Type:** Human

### What Triggers This Stage
Receipt of a complete Production Package from Stage 8.

### What Happens Here
The produced video is published to Instagram as a Reel. Publishing includes:
- Final caption review and formatting
- Hashtag selection
- Cover frame selection
- Scheduling or immediate posting
- Confirmation of successful publish

### What This Stage Produces
A **Publish Record** containing:
- Published post URL
- Publish timestamp
- Caption as published
- Workflow run ID (for traceability back to the Idea Record)

### Acceptance Criteria
The reel is live, the caption is published, and the Publish Record is logged.

### Escalation
If the platform rejects the post (technical failure, policy flag, or account restriction), the Platform Director is notified immediately. The production package is held and the publish is retried or escalated per the platform's specific failure.

---

## Workflow Closure

When Stage 9 is complete, the workflow run is closed:

1. Publish Record logged with workflow run ID
2. All stage outputs archived by workflow run ID
3. Workflow run marked complete in the activity log
4. Run duration (Idea to Publish) recorded

Archived outputs are retained. They are not deleted. They form the institutional record of what was produced, why, and how it was shaped.
