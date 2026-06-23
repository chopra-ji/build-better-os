# Outputs — Research Department

This file defines the eight structured documents this department produces. Every output has a defined schema, quality standard, consumer, and delivery method. Nothing leaves this department without passing its quality gates.

---

## Primary Outputs

### Output 1: Research Brief

| Attribute | Value |
|---|---|
| **Description** | A focused, direct answer to a specific research question. Targeted and actionable. This is the most common output and the fastest to produce. |
| **Format** | Structured markdown document |
| **Consumer(s)** | Requesting department |
| **Delivery Method** | Direct delivery to requesting department via output channel |
| **SLA** | Standard: 48 hours · Expedited: 24 hours · Urgent: same business day |
| **Quality Gate** | Gates 1–5 in `QUALITY_STANDARDS.md` |

**Schema:**
```
output_id:          string
output_type:        research_brief
request_id:         string (from originating request)
trace_id:           string
department_id:      research_department
version:            string
produced_at:        ISO 8601 timestamp
status:             enum [complete | partial | escalated | rejected]

title:              string (≤ 80 characters)
domain:             enum [technology | ai | business | marketing | psychology |
                         creator_economy | startups | books | frameworks | productivity]
research_question:  string (verbatim from request)
summary_answer:     string (2–4 sentences; the answer, stated directly)
confidence:         enum [high | medium | low | speculative]
confidence_note:    string (explain the confidence rating — what evidence supports it,
                           what uncertainty remains)
findings:
  - finding:        string
    evidence:       string
    source_ref:     string (reference to source in sources list)
implications:       list of strings (what this means for the requesting department)
caveats:            list of strings (what this does NOT answer; known gaps)
sources:            list of {title, author, date, url_or_location, reliability_tier}
related_outputs:    list of output_ids from prior research
```

---

### Output 2: Trend Report

| Attribute | Value |
|---|---|
| **Description** | A synthesized view of a movement, shift, or emerging pattern within a monitored domain. May be reactive (requested) or proactive (monitoring-triggered). |
| **Format** | Structured markdown document |
| **Consumer(s)** | Workflow Department (primary), Content Department, Leadership |
| **Delivery Method** | Delivered to Workflow Department; copies to other consumers as specified |
| **SLA** | Standard: 5 business days · Expedited: 3 business days · Proactive: no SLA (monitoring-triggered) |
| **Quality Gate** | Gates 1–5 in `QUALITY_STANDARDS.md` |

**Schema:**
```
output_id:          string
output_type:        trend_report
trace_id:           string
department_id:      research_department
version:            string
produced_at:        ISO 8601 timestamp
status:             complete | partial | escalated | rejected

title:              string
domain:             enum [domain list]
trend_name:         string (named, specific trend — not a broad topic)
trend_stage:        enum [emerging | growing | peaking | declining | reversing]
time_horizon:       string (e.g., "observed over the past 6 months; expected to continue 12–18 months")
executive_summary:  string (3–5 sentences)
confidence:         enum [high | medium | low | speculative]
confidence_note:    string

signal_evidence:
  - signal:         string (specific data point, event, or development)
    date:           date
    significance:   string
    source_ref:     string

drivers:            list of strings (what is causing this trend)
counterforces:      list of strings (what could slow or reverse it)
implications_for_build_better:
  - implication:    string
    urgency:        enum [immediate | short_term | long_term | monitor_only]
content_opportunities: list of strings
editorial_angles:   list of strings
sources:            list of {title, author, date, url_or_location, reliability_tier}
related_outputs:    list of output_ids
```

---

### Output 3: Competitive Analysis

| Attribute | Value |
|---|---|
| **Description** | A structured comparison of entities — companies, creators, platforms, or products — within a specific domain or competitive space. Surfaces differentiation, gaps, and strategic positioning. |
| **Format** | Structured markdown document with comparison tables |
| **Consumer(s)** | Requesting department, Leadership |
| **Delivery Method** | Direct delivery to requesting department |
| **SLA** | Standard: 7 business days · Expedited: 4 business days |
| **Quality Gate** | Gates 1–5 in `QUALITY_STANDARDS.md` |

**Schema:**
```
output_id:          string
output_type:        competitive_analysis
trace_id:           string
department_id:      research_department
version:            string
produced_at:        ISO 8601 timestamp
status:             complete | partial | escalated | rejected

title:              string
domain:             enum [domain list]
analysis_scope:     string (what is being compared and why)
entities_analyzed:  list of {name, category, brief_description}
analysis_date_range: string
confidence:         enum [high | medium | low | speculative]
confidence_note:    string

executive_summary:  string (4–6 sentences)
comparison_dimensions:
  - dimension:      string (e.g., "Monetization Model", "Audience Size", "Content Frequency")
    entity_ratings: list of {entity_name, assessment, evidence}

landscape_map:      string (narrative description of how entities relate to each other)
gaps_identified:    list of strings (spaces not well-served by any entity)
build_better_positioning: string (where Build Better sits or could sit relative to the landscape)
strategic_implications: list of strings
risks:              list of strings
sources:            list of {title, author, date, url_or_location, reliability_tier}
related_outputs:    list of output_ids
```

---

### Output 4: Idea Report

| Attribute | Value |
|---|---|
| **Description** | A synthesized set of content or strategic ideas generated from cross-domain research signals. Connects observations across domains to surface non-obvious opportunities. |
| **Format** | Structured markdown document |
| **Consumer(s)** | Content Department (primary), Workflow Department |
| **Delivery Method** | Direct delivery to Content and Workflow Departments |
| **SLA** | Standard: 4 business days · Expedited: 2 business days |
| **Quality Gate** | Gates 1–5 in `QUALITY_STANDARDS.md` |

**Schema:**
```
output_id:          string
output_type:        idea_report
trace_id:           string
department_id:      research_department
version:            string
produced_at:        ISO 8601 timestamp
status:             complete | partial | escalated | rejected

title:              string
domains_sourced:    list of domain enums
synthesis_question: string (the question or tension the ideas address)
confidence:         enum [high | medium | low | speculative]

ideas:
  - idea_title:     string
    idea_summary:   string (2–3 sentences)
    research_basis: string (what signals led to this idea)
    content_angles: list of strings
    audience_fit:   string
    urgency:        enum [immediate | short_term | long_term | evergreen]
    effort_estimate: enum [low | medium | high]

cross_domain_patterns: list of strings (patterns observed across domains that generated the ideas)
sources:            list of {title, author, date, url_or_location, reliability_tier}
related_outputs:    list of output_ids
```

---

### Output 5: Technology Report

| Attribute | Value |
|---|---|
| **Description** | A deep-dive document on a specific technology topic — a platform, tool category, technical shift, or infrastructure development. More comprehensive than a Research Brief. Intended for strategic decisions. |
| **Format** | Structured markdown document |
| **Consumer(s)** | Leadership (primary), Publishing Department, Content Department |
| **Delivery Method** | Direct delivery to requesting department; distributed to Leadership by default |
| **SLA** | Standard: 10 business days · Expedited: 6 business days |
| **Quality Gate** | Gates 1–5 in `QUALITY_STANDARDS.md` |

**Schema:**
```
output_id:          string
output_type:        technology_report
trace_id:           string
department_id:      research_department
version:            string
produced_at:        ISO 8601 timestamp
status:             complete | partial | escalated | rejected

title:              string
technology_subject: string (specific technology, platform, or category)
domains:            list of domain enums
maturity_stage:     enum [research | emerging | early_adoption | growth | mature | declining]
confidence:         enum [high | medium | low | speculative]
confidence_note:    string

executive_summary:  string (5–8 sentences)
technical_overview: string (accessible explanation of what the technology is and how it works)
adoption_landscape:
  - segment:        string
    adoption_level: enum [none | exploring | early | mainstream | saturated]
    evidence:       string

key_players:        list of {name, role, significance}
capabilities:       list of strings (what it enables)
limitations:        list of strings (what it does not do or does poorly)
risks:              list of strings (technical, regulatory, adoption risks)
trajectory:         string (where this technology is heading and why)
implications_for_build_better: list of strings
recommended_actions: list of {action, rationale, urgency}
sources:            list of {title, author, date, url_or_location, reliability_tier}
related_outputs:    list of output_ids
```

---

### Output 6: Framework Summary

| Attribute | Value |
|---|---|
| **Description** | A distillation of a thinking framework, mental model, or structured approach. Pulls from the Books or Frameworks domain. Immediately applicable to real decisions. |
| **Format** | Structured markdown document |
| **Consumer(s)** | All departments |
| **Delivery Method** | Delivered to requesting department; also submitted as a Knowledge Update to the vault |
| **SLA** | Standard: 3 business days · Expedited: 1 business day |
| **Quality Gate** | Gates 1–5 in `QUALITY_STANDARDS.md` |

**Schema:**
```
output_id:          string
output_type:        framework_summary
trace_id:           string
department_id:      research_department
version:            string
produced_at:        ISO 8601 timestamp
status:             complete | partial | escalated | rejected

title:              string
framework_name:     string
origin:             string (book title, author, or source — with date)
domain:             enum [frameworks | books | productivity | psychology | business]
confidence:         enum [high | medium | low | speculative]

core_idea:          string (1–2 sentences; the central claim or model)
how_it_works:       string (explanation of the framework's structure and logic)
components:         list of {name, description}
when_to_apply:      list of strings (situations where this framework is useful)
when_not_to_apply:  list of strings (situations where it breaks down or misleads)
application_examples: list of {scenario, application}
limitations:        list of strings
related_frameworks: list of framework names
sources:            list of {title, author, date, url_or_location, reliability_tier}
vault_entry_ref:    string (ID of the corresponding vault entry, if submitted)
```

---

### Output 7: Tool Review

| Attribute | Value |
|---|---|
| **Description** | A structured evaluation of a tool, platform, or product relevant to creators, operators, or the Build Better team. Objective assessment based on defined criteria. |
| **Format** | Structured markdown document |
| **Consumer(s)** | Requesting department, Leadership |
| **Delivery Method** | Direct delivery to requesting department |
| **SLA** | Standard: 3 business days · Expedited: 1 business day |
| **Quality Gate** | Gates 1–5 in `QUALITY_STANDARDS.md` |

**Schema:**
```
output_id:          string
output_type:        tool_review
trace_id:           string
department_id:      research_department
version:            string
produced_at:        ISO 8601 timestamp
status:             complete | partial | escalated | rejected

title:              string
tool_name:          string
tool_category:      string
domain:             enum [domain list]
review_date:        date
confidence:         enum [high | medium | low | speculative]
confidence_note:    string (note if review is based on secondary research vs. direct use)

overview:           string (what the tool does and who it is for)
evaluation_criteria:
  - criterion:      string
    score:          enum [poor | fair | good | excellent]
    evidence:       string

key_strengths:      list of strings
key_weaknesses:     list of strings
pricing_model:      string
best_fit_for:       list of strings (use cases and user types it serves well)
not_recommended_for: list of strings
alternatives:       list of {name, brief_comparison}
overall_assessment: string (2–3 sentences)
recommendation:     enum [strong_yes | yes | neutral | no | strong_no]
recommendation_rationale: string
sources:            list of {title, author, date, url_or_location, reliability_tier}
related_outputs:    list of output_ids
```

---

### Output 8: Knowledge Update

| Attribute | Value |
|---|---|
| **Description** | A structured update to the institutional knowledge vault. May be a new entry, a revision of an existing entry, or an archival action. Triggered by monitoring, request, or vault expiry alert. |
| **Format** | Vault entry with YAML frontmatter (per `knowledge/_templates/` schema) |
| **Consumer(s)** | Knowledge vault system; all departments that access the vault |
| **Delivery Method** | Written directly to the knowledge vault at the appropriate domain path |
| **SLA** | New entry: 2 business days · Revision: 1 business day · Archival: same day |
| **Quality Gate** | Gates 1–5 in `QUALITY_STANDARDS.md` plus vault-specific gate (Gate 6) |

**Schema:** Follows the canonical knowledge vault template for the relevant entry type. See `knowledge/_templates/` and domain-specific `Templates/` directories.

**Additional required fields beyond vault template:**
```
research_basis:     string (what triggered this Knowledge Update)
prior_entry_ref:    string (if revising — ID of the entry being updated)
verification_depth: string (how this was verified — primary sources, secondary synthesis, etc.)
```

---

## Operational Outputs

| Output | Description | Consumer |
|---|---|---|
| Activity log entry | Structured record of every work item processed, with outcome | Platform observability layer |
| Escalation notice | Structured notification when escalation criteria are met | Platform Director |
| Error report | Structured error with code, context, and originating input reference | Source department |
| Quality rejection notice | Internal notice when an output fails a quality gate | Triggers internal rework loop |
| Research queue status | Weekly summary of queue state — open, in-progress, completed, escalated | Platform Director |

---

## Output Metadata

Every output this department produces carries the following metadata fields:

| Field | Type | Description |
|---|---|---|
| `trace_id` | string | Propagated from the originating request. Enables end-to-end traceability. |
| `department_id` | string | `research_department` |
| `version` | string | Version of this department's operating design that produced the output. |
| `produced_at` | ISO 8601 timestamp | When the output was produced. |
| `input_ref` | string | The `request_id` of the originating request. |
| `status` | enum | One of: `complete`, `partial`, `escalated`, `rejected`. |

---

## Output Guarantees

This department guarantees:
- Every claim in every output is supported by at least one named source.
- Every output states its confidence level and the reason for that rating.
- No output is delivered without passing all applicable quality gates.
- Every output is logged and retrievable by `output_id` and `trace_id`.
- Superseded outputs are archived, not deleted.

This department does NOT guarantee:
- Consumer department availability at time of delivery — if a consumer is offline, the output is held and delivered when the consumer is available.
- That research findings will confirm a requesting department's prior assumptions — findings are reported as found.
