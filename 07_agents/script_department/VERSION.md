# Version — Script Department

---

## Current Version

| Field | Value |
|---|---|
| **Version** | 1.0.0 |
| **Status** | active |
| **Released** | 2026-06-23 |
| **Author** | Platform Director |

---

## Versioning Schema

The Script Department uses semantic versioning with meaning specific to organizational design.

| Version Component | Meaning | Examples |
|---|---|---|
| **MAJOR** | Mission change, fundamental scope change, or restructuring of the department's place in the pipeline | Changing the primary output type; changing what the department reports to; redefining the brief-to-script relationship |
| **MINOR** | Capability added or removed; new content format supported; new SOP added; quality gate added or removed | Adding a new content format to the applicability matrix; adding a new SOP; adding a new component to the Script Package schema |
| **PATCH** | Correction, clarification, or improvement to existing documentation without changing what the department does | Fixing an ambiguous field description; clarifying a checklist item; correcting a cross-reference |

---

## Version History

| Version | Status | Released | Summary |
|---|---|---|---|
| 1.0.0 | active | 2026-06-23 | Initial deployment. 11-component Script Package schema. 6-format applicability matrix. 11 SOPs. 4-gate quality framework. |

---

## Version Lifecycle

```
draft → active → deprecated → archived
```

| Status | Meaning |
|---|---|
| `draft` | Under development; not in production use |
| `active` | Current operating version; all Script Packages are produced under this version |
| `deprecated` | Superseded by a newer version; still valid for Script Packages produced under it; no new packages produced |
| `archived` | Retired; historical reference only |

When a new version is released:
1. The current version is set to `deprecated`.
2. The new version is set to `active`.
3. In-progress packages at the time of the version change are completed under the version they were started under, unless the Platform Director specifies otherwise.
4. CHANGELOG.md is updated before any version change takes effect.

---

## Planned Improvements (Not Yet Versioned)

The following are identified improvements for future versions. They are tracked here, not implemented, until the Platform Director authorizes a version update.

| Improvement | Target Version | Description |
|---|---|---|
| Performance feedback integration | 1.1.0 | Incorporate content performance data into the quality cycle — allow performance signals to inform which scripting patterns are validated or retired |
| Creator Economy scripting norms | 1.1.0 | Formalize scripting conventions for creator-economy formats currently distributed across vault domains |
| Caption Draft format expansion | 1.1.0 | Add platform-specific caption format variants (YouTube SRT, Instagram caption format, etc.) |
| Inter-department feedback protocol | 1.2.0 | Define a structured protocol for the Script Department to communicate brief quality patterns to the Platform Director, enabling a feedback loop to the Creative Department |
