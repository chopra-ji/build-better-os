# Content Production Workflow

This document describes how a content idea moves through Build Better OS from initial concept to published Instagram Reel.

---

## What This Workflow Is

The Content Production Workflow is the end-to-end process that governs how Build Better creates and publishes content. It connects four AI departments, one quality engine, one human review checkpoint, and two production stages into a single, auditable pipeline.

Every piece of content that Build Better publishes passes through this workflow in full. There are no shortcuts and no stages that can be skipped. Each stage has defined inputs, outputs, and acceptance criteria. A stage that does not produce an output that meets its acceptance criteria does not advance.

---

## What This Workflow Is Not

- Not an automation spec. This document describes the process; it does not define how any stage is executed technically.
- Not a replacement for departmental documentation. Each department and engine has its own detailed operating documentation. This workflow document describes the handoffs between them — not the internal workings within them.
- Not a creative brief or content guide. This is a process document.

---

## The Nine Stages

```
[Stage 1]  Idea
              ↓
[Stage 2]  Research Department
              ↓
[Stage 3]  Creative Department
              ↓
[Stage 4]  Script Department
              ↓
[Stage 5]  Creator Engine
              ↓
[Stage 6]  Final Production Script
              ↓
[Stage 7]  Founder Review
              ↓
[Stage 8]  Production
              ↓
[Stage 9]  Publishing
```

---

## File Index

| File | Purpose |
|---|---|
| `README.md` | This file. Overview and orientation. |
| `WORKFLOW.md` | Full stage-by-stage documentation: owner, inputs, outputs, acceptance criteria, escalation. |
| `INPUTS.md` | What each stage requires to begin — schemas and validation rules. |
| `OUTPUTS.md` | What each stage produces — schemas and delivery requirements. |
| `QUALITY_GATES.md` | Pass/fail criteria at every stage transition. |
| `CHECKLIST.md` | Operational checklists for running the workflow end to end. |
| `VERSION.md` | Current workflow version. |
| `CHANGELOG.md` | History of changes to this workflow. |

---

## Quick Reference

| Attribute | Value |
|---|---|
| **Workflow Name** | Content Production Workflow |
| **Output** | Published Instagram Reel |
| **Runtime Constraint** | 45–60 seconds |
| **Stages** | 9 |
| **AI Stages** | Stages 2–5 (Research, Creative, Script, Creator Engine) |
| **Human Stages** | Stages 1, 7, 8, 9 (Idea, Founder Review, Production, Publishing) |
| **Version** | See `VERSION.md` |

---

## Related Documentation

| System | Documentation |
|---|---|
| Research Department | `07_agents/research_department/` |
| Creative Department | `07_agents/creative_department/` |
| Script Department | `07_agents/script_department/` |
| Creator Engine | `08_creator_engine/` |
