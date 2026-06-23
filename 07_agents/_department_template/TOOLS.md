# Tools — [DEPARTMENT NAME]

This file documents every tool, system, and integration this department uses to perform its work. Tools are not optional preferences — they are operating dependencies. A change to any tool listed here requires a version update to this department's documentation.

---

## Core Tools

Core tools are required for this department to function. Without them, the department cannot complete its primary responsibilities.

### Tool: [TOOL NAME A]

| Attribute | Value |
|---|---|
| **Category** | [e.g., Knowledge Access / Communication / Storage / Data Processing / Workflow] |
| **Purpose** | [Specific reason this department uses this tool — not a generic description of the tool] |
| **Used In** | [Which workflow steps use this tool — reference `WORKFLOW.md` step numbers] |
| **Access Level** | [Read / Write / Admin / API] |
| **Owned By** | [Team or system that manages this tool] |
| **Failure Impact** | [What happens to this department if this tool is unavailable] |
| **Fallback** | [Alternative if this tool is unavailable, or "none — escalate"] |

### Tool: [TOOL NAME B]

| Attribute | Value |
|---|---|
| **Category** | [Category] |
| **Purpose** | [Specific purpose] |
| **Used In** | [Workflow steps] |
| **Access Level** | [Access level] |
| **Owned By** | [Owner] |
| **Failure Impact** | [Impact] |
| **Fallback** | [Fallback] |

---

## Supporting Tools

Supporting tools improve efficiency or quality but are not required for basic function. The department can operate without them, with reduced capability.

| Tool | Category | Purpose | Effect If Unavailable |
|---|---|---|---|
| [TOOL NAME] | [Category] | [Purpose] | [Reduced capability description] |
| [TOOL NAME] | [Category] | [Purpose] | [Reduced capability description] |

---

## Integration Points

This department integrates with the following systems. An integration point is a programmatic connection — not a manual hand-off.

| System | Integration Type | Direction | Data Exchanged |
|---|---|---|---|
| [SYSTEM NAME] | [API / Event / File / Message Queue] | [Inbound / Outbound / Bidirectional] | [What data flows] |
| [SYSTEM NAME] | [Integration type] | [Direction] | [Data] |

---

## Access and Permissions

| Resource | Access Type | Granted By | Required For |
|---|---|---|---|
| [RESOURCE / SYSTEM] | [Read / Write / Execute] | [TEAM OR ROLE] | [Which responsibilities] |
| [RESOURCE / SYSTEM] | [Access type] | [Grantor] | [Purpose] |

This department does not request more access than it needs. The principle of least privilege applies.

---

## Tool Onboarding

When this department is first deployed or moves to a new environment, the following tool setup steps must be completed in order:

1. [SETUP STEP 1 — e.g., "Configure read access to knowledge vault: domains X, Y, Z"]
2. [SETUP STEP 2]
3. [SETUP STEP 3]
4. Verify all core tools are reachable.
5. Run intake validation on a test work item before accepting live inputs.

---

## Tool Change Protocol

When a tool used by this department changes — new version, deprecation, replacement, or access change:

1. Assess impact on each workflow step that uses the tool.
2. Update this file to reflect the new state.
3. Update `WORKFLOW.md` if step behavior changes.
4. Run a test work item through the full workflow to verify.
5. Increment version in `VERSION.md` (MINOR for tool changes).
6. Add entry to `CHANGELOG.md`.

---

## Future Tool Needs

[Optional. Document tools this department would benefit from but does not yet have access to. Include rationale and expected impact. This feeds into platform tooling roadmap decisions.]

| Tool | Category | Rationale | Expected Impact |
|---|---|---|---|
| [TOOL NAME] | [Category] | [Why this department needs it] | [How it improves the department's output or efficiency] |
