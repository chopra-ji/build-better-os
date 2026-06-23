# Changelog — Research Department

All significant changes to this department's operating design are recorded here in reverse chronological order.

---

## [1.0.0] — 2026-06-23

### Added

**Core Design**
- Department established with mission: "Transform information into actionable insights across ten strategic domains."
- Department positioned as a platform-level shared service reporting to the Platform Director.
- Department registered in `07_agents/README.md` Deployed Departments table.

**Monitored Domains (10)**
- Artificial Intelligence
- Technology
- Business
- Marketing
- Psychology
- Creator Economy
- Startups
- Books
- Frameworks
- Productivity

**Output Types (8)**
- Research Brief — targeted answer to a specific research question; 24–48 hour SLA at standard tier.
- Trend Report — synthesized view of a domain movement; 5 business day SLA at standard tier.
- Competitive Analysis — structured entity comparison; 7 business day SLA at standard tier.
- Idea Report — cross-domain ideation from research signals; 4 business day SLA at standard tier.
- Technology Report — deep-dive on a specific technology; 10 business day SLA at standard tier.
- Framework Summary — distillation of a thinking framework; 3 business day SLA at standard tier.
- Tool Review — structured tool evaluation; 3 business day SLA at standard tier.
- Knowledge Update — vault entry creation, revision, or archival; 1–2 business day SLA at standard tier.

**Workflow**
- Workflow A (Reactive — Request-Driven): 10-step workflow from intake to closure.
- Workflow B (Proactive — Monitoring-Triggered): Monitoring cycle to signal assessment to Workflow A Step 4.
- Concurrency limit: 8 active work items maximum.
- Priority queue: urgent > expedited > standard; within tier, FIFO.

**Quality Gates (6)**
- Gate 1: Schema Completeness — all required schema fields populated.
- Gate 2: Source Adequacy — all claims sourced; at least one Tier 1–3 source present.
- Gate 3: Confidence Calibration — confidence level accurately stated and specifically explained.
- Gate 4: Claim-Implication Alignment — implications grounded in findings (Trend Reports, Competitive Analyses, Technology Reports, Idea Reports).
- Gate 5: Traceability — trace_id and input_ref present and valid.
- Gate 6: Vault Entry Compliance — Knowledge Updates meet vault template and frontmatter standards.
- Rework maximum: 2 attempts before automatic escalation.

**Source Reliability Standards**
- Five-tier source reliability system (Tier 1: Primary Controlled through Tier 5: Secondary General).
- Domain-specific source currency windows: 18 months for fast-moving domains, 24 months for mid-pace, 5 years for slower-moving domains.

**Standard Operating Procedures (17)**
- SOP-01 through SOP-11: Standard department SOPs (intake failure, escalation, rework, delivery failure, SLA breach, tool outage, duplicate, rejection, onboarding, out-of-authority).
- SOP-R01: Signal significance assessment — two-or-more threshold for proactive output triggering.
- SOP-R02: Domain monitoring cadences — daily, weekly, and monthly schedule for all ten domains.
- SOP-R03: Competitive Analysis entity list approval — 24-hour approval window process.
- SOP-R04: Vault expiry emergency — five-business-day threshold for emergency escalation.
- SOP-R05: Out-of-scope domain requests — rejection and escalation path.
- SOP-R06: Contradictory findings — procedure for honest delivery of findings that contradict the requesting department's premise.

**Tools**
- Knowledge vault (read and write)
- Research queue system (read and write)
- Output log (read and write)
- Activity log (append)
- News and signal aggregator (read)
- Academic and industry source access (read)

### Decisions Made

- **Creator Economy as a monitored domain without a dedicated vault path:** Creator Economy is a core monitored domain but does not yet have a dedicated vault path. Interim routing to `knowledge/business/`, `knowledge/marketing/`, and `knowledge/startup/`. This is a known gap documented in `KNOWLEDGE.md` with a resolution plan tied to a future vault domain creation decision.

- **Research Department reports to Platform Director, not to a content or editorial function:** This ensures research remains independent of the decisions it informs. A research department that reports to editorial is structurally incentivized to produce findings that support editorial decisions rather than challenge them.

- **Output types are fixed; no freeform research deliverables:** All outputs conform to one of eight defined schemas. This ensures every output is machine-readable, comparable across time, and usable by downstream departments without requiring interpretation. Freeform research notes are never delivered as outputs.

- **Confidence calibration is a quality gate, not a preference:** Gate 3 (Confidence Calibration) treats honesty about uncertainty as a quality requirement. An output that overstates confidence fails a quality gate the same way an output with an empty field does.

- **Maximum 2 rework attempts before automatic escalation:** Two attempts provide sufficient opportunity to correct drafting and sourcing errors. A third failure signals a systemic problem — insufficient sources, unresolvable scope ambiguity — that requires human judgment, not another rework cycle.
