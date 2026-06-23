# Inputs — Research Department

This file defines everything this department needs to receive in order to begin and complete its work. The Research Department operates in two modes: **reactive** (responding to requests) and **proactive** (self-initiated monitoring). Both modes have defined inputs.

---

## What Triggers This Department

| Trigger | Source | Description |
|---|---|---|
| Research Request | Any department via the research request channel | A structured request document submitted by a consuming department specifying the research question, required output type, urgency, and context. |
| Editorial Calendar Signal | Workflow Department | Upcoming content assignments flagged by Workflow for which proactive research support is needed. Triggers early-start research before a formal request arrives. |
| Domain Monitoring Cycle | Internal schedule | A recurring self-initiated trigger that activates domain scanning for each of the ten monitored domains on its defined cadence. Produces proactive Trend Reports and Knowledge Updates. |
| Knowledge Vault Expiry Alert | Knowledge vault system | An alert indicating that a vault entry in a monitored domain has reached its re-verification window. Triggers a Knowledge Update workflow. |
| Inbound Signal — High Relevance | Any source (filtered by monitoring tools) | A development, announcement, publication, or event in a monitored domain that meets the signal significance threshold defined in `SOPS.md`. Triggers an unscheduled Trend Report or Knowledge Update. |

---

## Required Inputs

### Input: Research Request Document

| Attribute | Value |
|---|---|
| **Source** | Any department via the research request channel |
| **Format** | Structured document (see schema below) |
| **Required Fields** | `request_id`, `requesting_department`, `output_type`, `research_question`, `urgency_tier`, `context`, `submitted_at` |
| **Validation Rules** | All required fields present; `output_type` must match one of the eight defined output types; `research_question` must be a specific, answerable question (not a broad topic); `urgency_tier` must be one of: `standard`, `expedited`, `urgent` (SLA per tier defined in `WORKFLOW.md` → Timing and SLAs) |
| **Rejection Behavior** | If validation fails, return a structured rejection with the failed rule and a resubmission guide. See `SOPS.md` → SOP-01. |

**Research Request Document Schema:**
```
request_id:          string (assigned by requesting department)
requesting_department: string
output_type:         enum [research_brief | trend_report | competitive_analysis |
                          idea_report | technology_report | framework_summary |
                          tool_review | knowledge_update]
research_question:   string (specific question, not broad topic)
urgency_tier:        enum [standard | expedited | urgent]
context:             string (why this is needed, how it will be used)
related_outputs:     list of prior output IDs (optional)
due_date:            ISO 8601 date (optional — if absent, SLA applies by urgency tier)
submitted_at:        ISO 8601 timestamp
```

---

### Input: Editorial Calendar Signal

| Attribute | Value |
|---|---|
| **Source** | Workflow Department |
| **Format** | Structured calendar notification |
| **Required Fields** | `assignment_id`, `topic_area`, `domain`, `planned_publish_date`, `research_lead_time_needed` |
| **Validation Rules** | `domain` must be one of the ten monitored domains; `planned_publish_date` must be at least five business days in the future for proactive research to be feasible. |
| **Rejection Behavior** | If lead time is insufficient, return a notification specifying the minimum lead time required and the earliest feasible research delivery date. Do not silently accept and under-deliver. |

---

### Input: Domain Monitoring Schedule

| Attribute | Value |
|---|---|
| **Source** | Internal — defined in this department's operating configuration |
| **Format** | Monitoring cadence table (defined in `SOPS.md` → Domain Monitoring Cadences) |
| **Required Fields** | Domain name, monitoring frequency, signal sources, output trigger threshold |
| **Validation Rules** | All ten domains must have an active monitoring cadence defined. No domain may go unmonitored for more than seven days. |
| **Rejection Behavior** | N/A — internal trigger. If a monitoring cadence cannot be maintained, escalate to Platform Director. |

---

### Input: Knowledge Vault Expiry Alert

| Attribute | Value |
|---|---|
| **Source** | Knowledge vault system |
| **Format** | Structured alert |
| **Required Fields** | `entry_id`, `entry_title`, `domain`, `last_verified_at`, `expiry_date` |
| **Validation Rules** | `domain` must be one of the ten monitored domains; alert must arrive no later than 14 days before expiry to allow re-verification time. |
| **Rejection Behavior** | If the alert arrives with fewer than five business days before expiry, escalate immediately. See `SOPS.md` → SOP for Vault Expiry Emergency. |

---

## Optional Inputs

| Input | Source | Effect If Absent |
|---|---|---|
| Related prior research outputs | Requesting department | Research proceeds without the context of prior work. Risk of duplication; department notes the absence and searches the output log for related prior work independently. |
| Audience signal data | Publishing Department | Research proceeds without audience resonance data. Output confidence on relevance claims is reduced; this is noted in the output's confidence section. |
| Subject matter context from requesting department | Requesting department | Research is conducted from first principles. May take longer; requesting department is informed. |
| Competitive entity list | Requesting department (for Competitive Analysis) | Department constructs the entity list based on domain knowledge. Requesting department must approve the entity list before research begins (SOP-CA-01). |

---

## Input Validation Rules

All inputs are validated against the following rules before work begins:

1. **Completeness:** All required fields are present and non-empty.
2. **Format conformance:** Input matches the defined schema.
3. **Source authorization:** Research requests must come from departments with an established relationship with the Research Department (see `ROLE.md` — Departments This Department Serves). Anonymous or unattributed requests are rejected.
4. **Scope conformance:** The research question or domain falls within the ten monitored domains. Out-of-scope requests are rejected with a redirect to the Platform Director for scope extension decisions.
5. **Output type validity:** The requested output type matches one of the eight defined types and is appropriate for the research question being asked.
6. **Idempotency:** The research question is checked against the output log for substantially similar prior work. If a sufficiently current and relevant output already exists, the prior output is returned rather than conducting duplicate research.

---

## Input Failure Handling

The table below summarizes failure behavior. The full step-by-step procedure for each failure type is documented in `SOPS.md`:
- Validation failures → **SOP-01**
- Duplicate inputs → **SOP-08**
- Rejection (unresolvable) → **SOP-09**

| Failure Type | Behavior |
|---|---|
| Missing required field | Reject input. Return structured error to source with field name and reason. See SOP-01. |
| Invalid output type | Reject input. Return list of valid output types with guidance on which fits the question. See SOP-01. |
| Out-of-scope domain | Reject input. Return structured explanation and escalation path for scope extension. See SOP-01. |
| Insufficient lead time (editorial signal) | Reject. Return minimum lead time requirement and feasible delivery date. See SOP-01. |
| Duplicate research question | Do not reprocess. Return reference to prior output with assessment of whether it remains current. See SOP-08. |

---

## Input Volume and Frequency

| Attribute | Value |
|---|---|
| **Expected request volume** | 5–15 research requests per week across all departments |
| **Peak volume** | Up to 25 requests per week during editorial planning cycles |
| **Monitoring cycle frequency** | Daily signal scanning; weekly synthesis per domain |
| **Queue discipline** | Priority-weighted: `urgent` > `expedited` > `standard`; within same tier, FIFO |
| **Backlog handling** | If queue exceeds capacity, the Platform Director is notified. No silent delays — all requesting departments are informed of revised delivery dates. |

---

## Input Dependencies

| This Input Requires | Which Means | Dependency On |
|---|---|---|
| Competitive Analysis inputs | Entity list must be approved before full research begins | Requesting department must confirm the entity list within 24 hours of receiving the draft list |
| Technology Report inputs | Domain context may require specialized source access | Platform Director approval for access to premium or gated sources |
