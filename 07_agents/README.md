# 07 Agents — AI Department Layer

This directory contains the organizational architecture for every AI department inside Build Better OS.

---

## What Is an AI Department?

An AI department is a bounded organizational unit that owns a specific domain of work within the platform. It operates with the same clarity, accountability, and process discipline expected of a human team. The difference is execution speed and scale — not structure.

Each department has:
- A defined **mission** (why it exists)
- A defined **role** (where it sits in the organization)
- Defined **inputs** it accepts and **outputs** it produces
- Defined **quality standards** it is accountable to
- Defined **relationships** with other departments

Departments do not improvise. They follow documented workflows, escalate when criteria are met, and produce outputs that meet their stated quality gates.

---

## How Departments Are Structured

Every department is a directory inside `07_agents/`. Its internal documentation follows the standard template defined in `_department_template/`.

```
07_agents/
├── README.md                  ← This file
├── _department_template/      ← Canonical template (do not deploy directly)
└── <department-name>/         ← One directory per deployed department
    ├── README.md
    ├── MISSION.md
    ├── ROLE.md
    ├── RESPONSIBILITIES.md
    ├── INPUTS.md
    ├── OUTPUTS.md
    ├── WORKFLOW.md
    ├── TOOLS.md
    ├── KNOWLEDGE.md
    ├── QUALITY_STANDARDS.md
    ├── CHECKLIST.md
    ├── SOPS.md
    ├── VERSION.md
    └── CHANGELOG.md
```

The `_department_template/` directory is the canonical source. When creating a new department, copy the template and fill in every placeholder. Do not leave placeholder text in a deployed department.

---

## How AI Employees Work

An AI department operates like a specialized employee, not a general-purpose assistant. It:

- **Knows its scope.** It works within defined inputs and outputs. It does not reach outside its domain without an explicit handoff protocol.
- **Follows written process.** All standard scenarios are covered by SOPs. The department executes SOPs before improvising.
- **Escalates predictably.** Escalation criteria are defined in advance. When those criteria are met, the department escalates — it does not attempt to resolve out-of-scope problems unilaterally.
- **Produces auditable outputs.** Every output is traceable to an input and a workflow step. Nothing is produced without context.
- **Maintains its own documentation.** Departments update their CHANGELOG and VERSION files when their operating design changes.

---

## How Departments Communicate

Departments communicate through defined handoff protocols, not ad-hoc messages.

**Upstream → Department:** A department receives work through its defined input channels. Inputs must match the schema described in the department's `INPUTS.md`. Malformed inputs are rejected with a structured error and returned to the sender. A structured rejection error always contains: `error_code`, `work_item_id`, the specific rule(s) that failed, and a `recommended_action` for the sender. Senders must be able to parse and act on this error without contacting the rejecting department.

**Department → Downstream:** A department delivers work through its defined output channels. Outputs must match the schema described in the department's `OUTPUTS.md` and must pass the department's own quality gates before being sent. Every output carries metadata that makes it self-describing: `trace_id`, `department_id`, `version`, `produced_at`, `input_ref`, and `status`.

**Lateral (Department → Department):** When a department needs to coordinate with a peer, it does so through documented inter-department protocols. No department calls another department's internal processes directly. They request outputs; they do not reach inside.

**Escalation:** When a department encounters a situation outside its defined operating criteria, it escalates to its designated escalation owner. The escalation path is documented in `ROLE.md` and triggered by criteria defined in `WORKFLOW.md`.

**Out-of-authority requests:** If a department receives a request to act outside its defined scope, it refuses with a structured response (`error_code: OUT_OF_AUTHORITY_REQUEST`) and redirects the requester to the correct channel. It does not comply, even partially. See each department's `SOPS.md` → SOP-11.

---

## How to Create a New Department

1. **Define the mission first.** Before creating any files, articulate in one sentence why this department needs to exist and what problem it solves that no other department already owns.

2. **Check for overlap.** Review existing department `MISSION.md` files to confirm the new department's scope does not duplicate an existing one.

3. **Copy the template.**
   ```
   cp -r 07_agents/_department_template/ 07_agents/<department-name>/
   ```

4. **Fill every file.** Replace every `[PLACEHOLDER]` with real, specific content. A department is not deployed until every file is complete.

5. **Register the department.** Add the new department to `07_agents/README.md` under the Deployed Departments index below.

6. **Record the decision.** If the new department represents a significant architectural decision (new domain, new integration boundary, new capability), record it as an ADR in `docs/adr/`.

7. **Version the department.** Set `VERSION.md` to `1.0.0` and add an initial entry to `CHANGELOG.md`.

---

## Versioning

Each department maintains its own semantic version in `VERSION.md`.

**Schema:** `MAJOR.MINOR.PATCH`

| Change Type | Version Increment |
|---|---|
| Fundamental change to mission, role, or scope | MAJOR |
| Addition or removal of responsibilities, inputs, outputs, or tools | MINOR |
| Corrections, clarifications, or wording improvements | PATCH |

Version history is recorded in `CHANGELOG.md`. Every meaningful change to a department's operating design must be logged.

---

## Documentation Standards

All department documentation follows these rules:

1. **Plain language.** Write for someone reading the file for the first time. Avoid jargon unless the term is defined in the same file or linked.

2. **Specific, not general.** Every field must contain real, specific content. "TBD" and "placeholder" are not acceptable in a deployed department.

3. **Present tense.** Describe what the department does, not what it will do.

4. **One purpose per file.** Each file in the template has a single, defined purpose. Do not duplicate content across files. Cross-reference with links.

5. **Placeholders only in the template.** The `_department_template/` directory is the only place `[PLACEHOLDER]` text is permitted.

6. **Every directory must have a README.md.** This is a hard constraint inherited from the project-wide standard.

---

## Deployed Departments

| Department | Domain | Status |
|---|---|---|
| *(none yet)* | — | — |

---

## Template Reference

See [`_department_template/README.md`](./_department_template/README.md) for the complete template guide, including a description of every file and what it must contain.
