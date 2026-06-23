# [DEPARTMENT NAME] — Department Overview

> **Template notice:** This directory is `_department_template/`. It is the canonical framework for all AI departments in Build Better OS. Copy this directory when creating a new department. Replace every `[PLACEHOLDER]` with real, specific content before deploying.

---

## What This Department Does

[One paragraph. Describe what this department does in plain language. Write it as if explaining to a new colleague on their first day. Avoid jargon. Be specific about the domain this department owns.]

---

## Why This Department Exists

[One to three sentences. What problem does this department solve? What would happen if it did not exist? This should be distinct from the MISSION.md — this is the layperson explanation, not the formal statement.]

---

## File Index

| File | Purpose |
|---|---|
| `README.md` | This file. Entry point and orientation. |
| `MISSION.md` | Formal statement of purpose, strategic alignment, and definition of success. |
| `ROLE.md` | Position in the org chart, reporting lines, and scope of authority. |
| `RESPONSIBILITIES.md` | What this department owns, what it contributes to, and what is explicitly out of scope. |
| `INPUTS.md` | What this department needs to receive to do its work — triggers, required data, format expectations. |
| `OUTPUTS.md` | What this department produces — deliverables, format, quality requirements, and consumers. |
| `WORKFLOW.md` | Step-by-step description of how work flows through this department. |
| `TOOLS.md` | Tools, systems, and integrations this department uses. |
| `KNOWLEDGE.md` | Knowledge domains and vault references this department draws from and contributes to. |
| `QUALITY_STANDARDS.md` | Definition of done, quality gates, review requirements, and rejection criteria. |
| `CHECKLIST.md` | Pre-work, in-progress, and completion checklists for standard operations. |
| `SOPS.md` | Standard Operating Procedures for common scenarios, exceptions, and escalations. |
| `VERSION.md` | Current version of this department's operating design. |
| `CHANGELOG.md` | Full history of changes to this department's design. |

---

## Quick Reference

| Attribute | Value |
|---|---|
| **Department Name** | [DEPARTMENT NAME] |
| **Domain** | [DOMAIN — e.g., Content, Analytics, Editorial] |
| **Status** | [draft \| active \| archived] |
| **Version** | See `VERSION.md` |
| **Reports To** | [PARENT DEPARTMENT or ROLE] |
| **Primary Output** | [ONE-LINE DESCRIPTION OF PRIMARY DELIVERABLE] |
| **Primary Consumer** | [DEPARTMENT OR SYSTEM THAT RECEIVES PRIMARY OUTPUT] |

---

## How to Use This Template

1. Copy this directory: `cp -r 07_agents/_department_template/ 07_agents/<department-name>/`
2. Update `README.md` — replace all `[PLACEHOLDER]` values with real content.
3. Complete `MISSION.md` before any other file — mission drives everything else.
4. Complete `ROLE.md` — determine reporting lines and peer relationships.
5. Complete `RESPONSIBILITIES.md` — define scope clearly, especially what is out of scope.
6. Complete `INPUTS.md` and `OUTPUTS.md` — define the department's contract with other departments.
7. Complete `WORKFLOW.md` — document the standard operating flow.
8. Complete all remaining files.
9. Set `VERSION.md` to `1.0.0` and add the initial entry to `CHANGELOG.md`.
10. Register the department in `07_agents/README.md`.

Do not deploy a department with incomplete files. Every `[PLACEHOLDER]` must be replaced.
