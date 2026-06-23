# Changelog — Script Department

All significant changes to this department's operating design are recorded here. The format follows Keep a Changelog conventions adapted for organizational design documents.

Entries are listed in reverse chronological order (newest first).

---

## [1.0.0] — 2026-06-23

### Added

**Core Documentation**
- `README.md` — Department overview, 11-component table with format-universal markers, quick reference
- `MISSION.md` — Mission statement, strategic alignment, KPIs, definition of success, scope boundary, non-negotiables
- `ROLE.md` — Org chart, reporting lines, scope of authority, scope of influence, escalation path, succession
- `INPUTS.md` — Creative Brief validation checklist, 10-dimension reference table, supplementary research input, revision request input, brief return procedure and package schema
- `OUTPUTS.md` — Format-component applicability matrix (6 formats × 11 components), package metadata schema, all 11 component schemas with typed fields, output guarantees
- `WORKFLOW.md` — 6-step workflow with ASCII flow diagram, per-step procedures, format-specific scripting notes, component assembly sequence, SLA reference table, revision workflow
- `QUALITY.md` — Definition of done, 4 quality gates with per-dimension checks, failure escalation procedure, rejection criteria, quality metrics, review cadence
- `KNOWLEDGE.md` — 4 primary vault domains, 10 secondary vault domains, knowledge contribution types, reliability standards, known gaps
- `CHECKLIST.md` — 7 operational checklists: brief receipt/validation, brief comprehension, script draft self-check, component assembly (per-component), quality gate review, delivery, revision
- `SOPS.md` — 11 SOPs: brief return, revision, ambiguous dimension hold, SLA breach prevention, SLA breach response, expedited/urgent handling, format mismatch, supplementary research request, out-of-scope revision, new format onboarding, out-of-authority request
- `VERSION.md` — Versioning schema (MAJOR/MINOR/PATCH with organizational meaning), version lifecycle, planned improvements
- `CHANGELOG.md` — This file

**Script Package Schema (11 Components)**
- Component 1: Script — full text with format conventions
- Component 2: Hook — isolated opening, annotated and timed
- Component 3: Scene Breakdown — numbered scenes with purpose, arc function, timing
- Component 4: Voiceover — narration track separated and formatted for recording
- Component 5: Talking Head Notes — energy, pacing, eye contact, emphasis guidance
- Component 6: B-roll Notes — intent-based coverage per scene section
- Component 7: Camera Notes — framing and movement per scene
- Component 8: Editing Notes — rhythm, music direction, cut points, effects
- Component 9: On-screen Text — all text elements with final copy and timing
- Component 10: Caption Draft — subtitle text accurate to script, estimated timecodes
- Component 11: CTA — final copy, placement, delivery direction, brief fidelity note

**Format Coverage**
- `long_form_video`: all 11 components applicable
- `short_form_video`: all 11 components applicable
- `article`: Script, Hook, Scene Breakdown, CTA
- `newsletter`: Script, Hook, Scene Breakdown, CTA
- `podcast`: Script, Hook, Scene Breakdown, Voiceover, Editing Notes, CTA
- `social_post`: Script, Hook, Talking Head Notes (video), Camera Notes (video), On-screen Text (video), CTA

**Quality Framework**
- Gate 1: Brief Fidelity — 10-dimension execution check
- Gate 2: Component Completeness — presence and population check
- Gate 3: Internal Consistency — cross-component alignment check
- Gate 4: Traceability — creative decision linkage to brief dimensions

---

*This department is part of the Build Better OS agent layer. See `07_agents/README.md` for the full department registry and inter-department communication protocols.*
