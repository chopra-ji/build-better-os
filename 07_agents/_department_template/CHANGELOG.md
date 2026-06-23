# Changelog — [DEPARTMENT NAME]

All significant changes to this department's operating design are recorded here. The format follows [Keep a Changelog](https://keepachangelog.com/) conventions adapted for organizational design documents.

Changes are listed in reverse chronological order. Every entry must reference the version in `VERSION.md`.

---

## [Unreleased]

*Changes that are drafted but not yet assigned a version.*

---

## [1.0.0] — [YYYY-MM-DD]

### Added
- Initial department design across all files: `README.md`, `MISSION.md`, `ROLE.md`, `RESPONSIBILITIES.md`, `INPUTS.md`, `OUTPUTS.md`, `WORKFLOW.md`, `TOOLS.md`, `KNOWLEDGE.md`, `QUALITY_STANDARDS.md`, `CHECKLIST.md`, `SOPS.md`, `VERSION.md`.
- Mission statement: [BRIEF SUMMARY OF MISSION].
- Primary responsibilities: [LIST PRIMARY RESPONSIBILITIES].
- Input channels: [LIST INPUT CHANNELS].
- Output channels: [LIST OUTPUT CHANNELS].
- Quality gates: [LIST GATE NAMES].
- SOPs: SOP-01 through SOP-10 plus [any department-specific SOPs].

### Decisions Made
- [KEY DECISION 1 — e.g., "Department reports to [X] rather than [Y] because..."]
- [KEY DECISION 2]

---

## Changelog Entry Format

When recording a new version entry, use the following format:

```markdown
## [MAJOR.MINOR.PATCH] — YYYY-MM-DD

### Added
- [New responsibilities, inputs, outputs, tools, SOPs, or quality gates]

### Changed
- [Modifications to existing responsibilities, workflow steps, quality gates, or reporting lines]

### Removed
- [Responsibilities, inputs, outputs, tools, or SOPs that no longer apply]

### Fixed
- [Corrections to errors in prior versions — schema mistakes, broken references, incorrect criteria]

### Decisions Made
- [Any significant decisions made during this version that are not obvious from the changes above]

### Migration Notes
- [For MAJOR versions: what existing work items or consumers need to know]
```

**Rules for changelog entries:**

1. **Every version must have an entry.** There are no undocumented version changes.
2. **Be specific.** "Updated quality standards" is not acceptable. "Raised first-pass quality rate target from 85% to 95% based on Q1 audit findings" is.
3. **Include the why.** Changes without rationale rot. Future reviewers need to understand why a decision was made, not just what changed.
4. **MAJOR version entries must include Migration Notes.** Any department or system that consumes this department's outputs must be notified of breaking changes.
