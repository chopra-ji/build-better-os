# Version — [DEPARTMENT NAME]

---

## Current Version

| Attribute | Value |
|---|---|
| **Version** | `[MAJOR.MINOR.PATCH]` |
| **Status** | [draft \| active \| deprecated \| archived] |
| **Effective Date** | [YYYY-MM-DD] |
| **Author** | [WHO DEFINED THIS VERSION] |
| **Approved By** | [WHO APPROVED THIS VERSION] |

---

## Versioning Schema

This department uses semantic versioning: `MAJOR.MINOR.PATCH`.

| Change Type | Version Increment | Examples |
|---|---|---|
| **MAJOR** | Breaking change to mission, role, or fundamental scope | Mission redefinition, removal of a primary responsibility, change in reporting line |
| **MINOR** | Additive or subtractive change to capabilities | New responsibility added, tool added or removed, input or output schema change, new SOP added |
| **PATCH** | Non-breaking correction or clarification | Wording correction, formatting fix, broken link repaired, example updated |

**Rule:** When in doubt, increment the higher-order component. Under-versioning is a worse mistake than over-versioning.

---

## Version History Summary

| Version | Date | Type | Summary |
|---|---|---|---|
| `1.0.0` | [YYYY-MM-DD] | Initial | Department activated. |

*For detailed change descriptions, see `CHANGELOG.md`.*

---

## Version Lifecycle

```
draft (0.x.x)
    │
    ▼ approved and deployed
active (1.x.x+)
    │
    ▼ superseded by successor or decommissioned
deprecated (final version remains, no new changes)
    │
    ▼ no longer referenced
archived
```

**Draft:** The department design is in progress. It is not deployed and does not accept live work.

**Active:** The department is deployed and operating. All changes require a version increment and a `CHANGELOG.md` entry.

**Deprecated:** The department is being wound down. It continues to process existing work items but does not accept new ones. A deprecation notice is added to `README.md`.

**Archived:** The department is no longer operational. Documentation is preserved for reference.

---

## How to Update This File

1. Determine the change type: MAJOR, MINOR, or PATCH.
2. Increment the version number according to the schema above.
3. Update the Current Version table with the new version, effective date, and author.
4. Add a row to the Version History Summary.
5. Write the full change description in `CHANGELOG.md`.
