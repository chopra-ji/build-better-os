# Quality Standards — Research Department

This file defines what "done" means for every output this department produces. Every output passes every applicable quality gate before delivery. Quality failures are reworked or escalated — they are never quietly delivered.

Research quality has a unique property: a low-confidence finding delivered honestly is higher quality than a high-confidence finding delivered without sufficient evidence. Honesty about uncertainty is a quality requirement, not a weakness.

---

## Definition of Done

A research output is complete when all of the following are true:

- [ ] All required schema fields for the output type are populated and non-empty.
- [ ] Every claim in the output is supported by at least one named source.
- [ ] The `confidence` field is set and the `confidence_note` explains the rating specifically.
- [ ] All sources are listed with title, author (or organization), date, location or URL, and reliability tier.
- [ ] All quality gates for this output type have passed.
- [ ] Output metadata is complete (`trace_id`, `department_id`, `version`, `produced_at`, `input_ref`, `status`).
- [ ] The output has been delivered to all defined consumers.
- [ ] The activity log entry is written.
- [ ] Vault contribution has been assessed and either submitted or documented as not warranted.

---

## Source Reliability Standards

All sources used in research outputs are assigned a reliability tier. The tier must be disclosed in the source list and informs the confidence rating.

| Tier | Label | Description | Examples |
|---|---|---|---|
| 1 | Primary — Controlled | Peer-reviewed research, controlled studies, official regulatory filings, primary data | Academic journals, government data, company SEC filings |
| 2 | Primary — Reported | Direct firsthand accounts, official company announcements, primary interviews | Press releases, founder interviews, official platform documentation |
| 3 | Secondary — Established | Reporting by established, named publications with editorial standards and correction practices | Major business and technology publications with known fact-checking practices |
| 4 | Secondary — Analytical | Industry analysis reports, research firm reports, expert synthesis | Analyst reports, research firm publications |
| 5 | Secondary — General | General web sources, blogs, social media, aggregated news | Newsletter mentions, social commentary, unattributed online sources |

**Rules:**
- No output may rely solely on Tier 5 sources. At least one Tier 1–3 source is required for any factual claim.
- A claim supported only by Tier 4–5 sources must be labeled speculative or low-confidence.
- Source dates must be disclosed. Undated sources are treated as Tier 5.

---

## Quality Gates

Quality gates run in sequence during Workflow Step 7. A gate failure stops delivery and triggers the rework loop.

### Gate 1: Schema Completeness

| Attribute | Value |
|---|---|
| **Purpose** | Ensure the output conforms to the defined schema for its type and no required field is absent or empty. |
| **Applies To** | All outputs |
| **Criteria** | Every required field in the output type schema (defined in `OUTPUTS.md`) is present and non-empty. Optional fields are present if the schema marks them as conditionally required. |
| **Failure Behavior** | Rework. Return to Step 6 (Output Drafting). |

**Checks:**
- [ ] Output type field is set and matches one of the eight defined types.
- [ ] All required schema fields are present and non-empty.
- [ ] `title` is ≤ 80 characters (Research Brief) or within the bounds for its type.
- [ ] `domain` field contains only valid domain enums.
- [ ] `status` is set to a valid value.
- [ ] All output metadata fields are present and populated.

---

### Gate 2: Source Adequacy

| Attribute | Value |
|---|---|
| **Purpose** | Ensure every factual claim has source support and no output relies entirely on unreliable sources. |
| **Applies To** | All outputs |
| **Criteria** | Every non-trivial factual claim is supported by at least one named source. At least one Tier 1–3 source is included. No claim is marked as high confidence unless it has Tier 1–3 source support. |
| **Failure Behavior** | Rework. Return to Step 4 (Source Assembly) or Step 5 (Research and Synthesis). |

**Checks:**
- [ ] Sources list contains at least one Tier 1–3 source.
- [ ] Every factual claim in the output can be traced to a source in the sources list.
- [ ] No source is listed without a date (or a note that no date is available with Tier 5 applied).
- [ ] Sources are sufficiently recent for the domain (see currency standards below).
- [ ] No source is used to support a claim it does not actually make.

**Source currency standards by domain:**
- Technology, AI, Creator Economy, Marketing: sources older than 18 months require a recency note.
- Business, Startups: sources older than 24 months require a recency note.
- Psychology, Frameworks, Books, Productivity: sources older than 5 years require a recency note and a check for superseding research.

---

### Gate 3: Confidence Calibration

| Attribute | Value |
|---|---|
| **Purpose** | Ensure confidence levels are accurately stated and the confidence note specifically explains the rating. |
| **Applies To** | All outputs |
| **Criteria** | The stated confidence level is consistent with the source quality, source consensus, recency, and directness of evidence. The confidence note explains the rating with specificity. |
| **Failure Behavior** | Rework. Return to Step 6 (Output Drafting). |

**Checks:**
- [ ] `confidence` is set to one of: `high`, `medium`, `low`, `speculative`.
- [ ] `confidence_note` explains specifically why that level was chosen — not a generic statement.
- [ ] A `high` confidence rating is supported by Tier 1–3 sources with consensus and recency.
- [ ] A `medium` confidence rating is supported by Tier 2–4 sources or Tier 1–3 sources with some conflicting evidence.
- [ ] A `low` confidence rating reflects limited sources, older evidence, or significant conflicting evidence.
- [ ] A `speculative` confidence rating is used when findings are extrapolated rather than directly evidenced.
- [ ] No individual finding within the output carries a higher confidence than the overall output confidence.

---

### Gate 4: Claim-Implication Alignment

| Attribute | Value |
|---|---|
| **Purpose** | Ensure that the implications and recommendations in the output follow from the findings, and that no implications are stated that are not grounded in the research. |
| **Applies To** | Trend Report, Competitive Analysis, Technology Report, Idea Report |
| **Criteria** | Each implication stated in the output can be directly traced to a specific finding. No implication overstates what the evidence supports. Caveats section explicitly states what the research does NOT establish. |
| **Failure Behavior** | Rework. Return to Step 5 (Research and Synthesis) or Step 6 (Output Drafting). |

**Checks:**
- [ ] Each `implication` can be traced to at least one specific `finding` or `signal`.
- [ ] No implication uses stronger language than the underlying evidence supports.
- [ ] `caveats` section identifies at least one thing the research does not establish.
- [ ] `recommended_actions` (Technology Report) are proportionate to the confidence level of the underlying findings.

---

### Gate 5: Traceability

| Attribute | Value |
|---|---|
| **Purpose** | Every output must be fully traceable from its originating request through its findings to its delivery. |
| **Applies To** | All outputs |
| **Criteria** | `trace_id` and `input_ref` fields are present, non-empty, and match the logged request record. |
| **Failure Behavior** | Output is quarantined. Escalation notice sent to Platform Director. |

**Checks:**
- [ ] `trace_id` is present and matches the originating request or monitoring trigger record.
- [ ] `input_ref` resolves to a real, logged request or monitoring event.
- [ ] `produced_at` timestamp is within the SLA window relative to intake.
- [ ] `department_id` is set to `research_department`.
- [ ] `version` reflects the current department version from `VERSION.md`.

---

### Gate 6: Vault Entry Compliance (Knowledge Updates only)

| Attribute | Value |
|---|---|
| **Purpose** | Ensure Knowledge Update outputs meet the knowledge vault's own standards before submission. |
| **Applies To** | Knowledge Update outputs only |
| **Criteria** | The vault entry conforms to the template for its entry type, has complete YAML frontmatter, a completed `tldr` field, `status: active` or `status: draft`, and at least one `related` link if `status: active`. |
| **Failure Behavior** | Rework. Return to Step 6 (Output Drafting). Do not submit to vault. |

**Checks:**
- [ ] YAML frontmatter is present and complete for the entry type.
- [ ] `tldr` field is one sentence, specific, and non-empty.
- [ ] `status` is set to `active` or `draft` (never submitted as `archived`).
- [ ] If `status: active`: at least one `related` link is present.
- [ ] `confidence` reflects actual verification depth.
- [ ] Entry follows the canonical template from `knowledge/_templates/` or the domain-specific `Templates/` directory.

---

## Rework Policy

| Attempt | Behavior |
|---|---|
| 1st failure | Log the gate failure with gate name and specific checks failed. Return to the appropriate workflow step with failure context. |
| 2nd failure | Log the failure. Notify Platform Director. Return to workflow with extended context. |
| 3rd failure (exceeds maximum) | Halt. Escalate to Platform Director per `SOPS.md` → SOP-04 with full rework history. |

**Maximum rework attempts: 2** (before automatic escalation).

---

## Escalation Quality Threshold

A work item is automatically escalated regardless of rework count when:

- Gate 2 (Source Adequacy) fails because no Tier 1–3 sources exist for a factual claim that requires them — indicating a fundamental source availability problem, not a drafting error.
- Gate 3 (Confidence Calibration) reveals that the highest honest confidence rating for the output is `speculative` for a claim the requesting department requires at `medium` or above — the research cannot fulfill the request as specified.
- Gate 5 (Traceability) fails — this indicates a systemic logging or process problem, not a content issue.

---

## Quality Metrics

| Metric | Description | Target | Alert Threshold |
|---|---|---|---|
| First-pass quality rate | Outputs passing all gates without rework | ≥ 90% | Below 80% |
| Gate 2 failure rate | Source adequacy failures per output | < 10% | Above 15% |
| Gate 3 failure rate | Confidence calibration failures per output | < 8% | Above 12% |
| Rework rate | Outputs requiring at least one rework | < 10% | Above 20% |
| Escalation rate | Requests escalated due to quality threshold | < 5% per quarter | Above 8% |
| Vault entry quality failure rate | Knowledge Updates rejected from vault for compliance failures | < 5% | Above 10% |

---

## Quality Review Cadence

| Review | Frequency | Purpose | Owner |
|---|---|---|---|
| Output quality sample audit | Monthly | Review 10% of completed outputs against all quality gates | Research Department |
| Source reliability audit | Quarterly | Review source tier assignments for consistency and accuracy | Research Department |
| Confidence calibration review | Quarterly | Compare stated confidence levels against outcomes — were speculative findings confirmed or disproved? | Research Department + Platform Director |
| Vault contribution quality audit | Quarterly | Review Knowledge Updates submitted to vault for frontmatter compliance and entry quality | Research Department |
