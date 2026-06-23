# Knowledge — [DEPARTMENT NAME]

This file defines what this department needs to know, where that knowledge lives, and how this department contributes back to the institutional knowledge base. Knowledge is an operational dependency — a department that cannot access the knowledge it needs cannot produce reliable output.

---

## Knowledge Domains Required

These are the knowledge domains this department must have access to in order to perform its responsibilities.

| Domain | Vault Path | Access Level | Why Required |
|---|---|---|---|
| [DOMAIN NAME A] | `knowledge/[domain-a]/` | [Read / Contribute] | [Specific reason — e.g., "Required to validate content against editorial standards"] |
| [DOMAIN NAME B] | `knowledge/[domain-b]/` | [Read / Contribute] | [Reason] |
| [DOMAIN NAME C] | `knowledge/[domain-c]/` | [Read / Contribute] | [Reason] |

---

## Required Knowledge Depth

Not all knowledge is equal. Define the depth of knowledge required per domain.

| Domain | Depth Required | Description |
|---|---|---|
| [DOMAIN A] | Operational | [Must know enough to apply standards consistently — no research required in the moment] |
| [DOMAIN B] | Reference | [Must know where to find the answer — does not need to hold it in working memory] |
| [DOMAIN C] | Awareness | [Must know this domain exists and when to route to a specialist] |

**Depth definitions:**
- **Operational:** The department can apply this knowledge without looking it up. It is embedded in workflow steps and quality checks.
- **Reference:** The department consults this knowledge when processing a specific work item. It is accessed on demand.
- **Awareness:** The department recognizes when this domain is relevant and knows who owns it.

---

## Knowledge Used Per Workflow Step

| Workflow Step | Knowledge Consulted | Source |
|---|---|---|
| Step 1: Intake & Validation | [e.g., Input schema definitions] | [Source — e.g., `INPUTS.md`, platform schema registry] |
| Step 2: Context Assembly | [e.g., Editorial domain standards] | `knowledge/[domain]/` |
| Step 3: Core Processing | [e.g., Style rules, quality benchmarks] | `knowledge/[domain]/`, `QUALITY_STANDARDS.md` |
| Step 4: Quality Review | [e.g., Quality gate criteria] | `QUALITY_STANDARDS.md` |

---

## Knowledge Gaps

[Document any knowledge this department needs but does not currently have reliable access to. These are operational risks. Each gap should have a resolution plan or an owner responsible for resolving it.]

| Knowledge Gap | Impact | Resolution Plan | Owner |
|---|---|---|---|
| [GAP DESCRIPTION] | [How it affects output quality or reliability] | [What is being done to close the gap] | [Who owns the resolution] |

---

## How This Department Contributes to the Knowledge Vault

This department does not only consume knowledge — it generates knowledge through its operations. The following describes what this department is responsible for contributing back.

| Contribution Type | What It Is | Vault Path | Frequency |
|---|---|---|---|
| [CONTRIBUTION TYPE A] | [e.g., Validated findings from processed work items] | `knowledge/[domain]/` | [e.g., Ongoing, per-item / Weekly batch / When threshold is met] |
| [CONTRIBUTION TYPE B] | [e.g., Identified patterns or exceptions that should become reference entries] | `knowledge/[domain]/` | [Frequency] |

**Contribution standard:** All knowledge contributions from this department must include YAML frontmatter, a completed `tldr` field, and at least one `related` link. Do not submit placeholder entries. See the Knowledge Vault standards in `knowledge/README.md`.

---

## Knowledge Maintenance Responsibilities

| Knowledge Asset | Review Frequency | Action Required |
|---|---|---|
| [ASSET — e.g., AI domain entries this department references] | [Every 6 months] | [Re-verify currency and accuracy. Flag stale entries for archival.] |
| [ASSET] | [Frequency] | [Action] |

---

## Knowledge Dependencies Between Departments

Some knowledge this department uses is produced by other departments. Document those dependencies here to surface upstream risks.

| Knowledge Asset | Produced By | How This Department Uses It |
|---|---|---|
| [ASSET] | [UPSTREAM DEPARTMENT] | [How it feeds into this department's workflow] |

---

## Knowledge Onboarding

When this department is first deployed, the following knowledge must be verified as current and accessible before the department accepts live work:

- [ ] Access to all required vault domains confirmed.
- [ ] All required operational knowledge verified as `status: active`.
- [ ] No required knowledge entries are in `draft` or `archived` status.
- [ ] Knowledge gaps documented (if any) and resolution plans initiated.
