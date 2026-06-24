# 09 Workflows

This directory contains documented workflows for Build Better OS. Each workflow describes how work moves through the system from trigger to output, connecting departments, engines, and human checkpoints into a single auditable process.

---

## What Is a Workflow?

A workflow documents a repeatable, multi-stage process. It defines:
- What triggers the process
- What each stage does, who owns it, and what it produces
- The quality gates between stages
- How failures, revisions, and escalations are handled

Workflows are not automation specs. They are operating documentation — the written record of how the system is designed to behave.

---

## Deployed Workflows

| Workflow | Purpose | Status |
|---|---|---|
| [Content Production Workflow](./content_production_workflow/README.md) | End-to-end process for creating and publishing an Instagram Reel | active |

---

## How to Create a New Workflow

1. Create a new directory under `09_workflows/` using `kebab-case`.
2. At minimum, include: `README.md`, `WORKFLOW.md`, `INPUTS.md`, `OUTPUTS.md`, `QUALITY_GATES.md`, `CHECKLIST.md`, `VERSION.md`, `CHANGELOG.md`.
3. Every directory must have a `README.md`.
4. Do not create a workflow that duplicates a process already owned by a department or engine. Workflows connect systems — they do not replace departmental documentation.
