# Knowledge — Research Department

This file defines what the Research Department must know, where that knowledge lives, and how it contributes back to the institutional knowledge base. The Research Department is both the primary consumer and the primary contributor of institutional knowledge across its ten domains.

---

## Knowledge Domains Required

| Domain | Vault Path | Access Level | Why Required |
|---|---|---|---|
| Artificial Intelligence | `knowledge/ai/` | Read and Contribute | Core monitored domain. Required to evaluate AI developments, assess tool significance, and produce Technology Reports and Trend Reports on AI topics. |
| Technology | `knowledge/technology/` | Read and Contribute | Core monitored domain. Required for Technology Reports, platform evaluations, and infrastructure-related Trend Reports. |
| Business | `knowledge/business/` | Read and Contribute | Core monitored domain. Required for Competitive Analyses, business model assessments, and business Trend Reports. |
| Marketing | `knowledge/marketing/` | Read and Contribute | Core monitored domain. Required for marketing Trend Reports, channel analyses, and audience behavior research. |
| Psychology | `knowledge/psychology/` | Read and Contribute | Core monitored domain. Required for Framework Summaries drawing on behavioral science, audience psychology research, and persuasion-related Research Briefs. |
| Startups | `knowledge/startup/` | Read and Contribute | Core monitored domain. Required for startup Trend Reports, founder strategy research, and funding landscape Competitive Analyses. |
| Books | `knowledge/books/` | Read and Contribute | Core monitored domain. Required for book-based Framework Summaries and Book domain Knowledge Updates. |
| Frameworks | `knowledge/frameworks/` | Read and Contribute | Core monitored domain. Required for Framework Summaries and mental model documentation. |
| Productivity | `knowledge/productivity/` | Read and Contribute | Core monitored domain. Required for Productivity Trend Reports, tool reviews covering productivity tools, and workflow methodology research. |
| Quotes | `knowledge/quotes/` | Read | Secondary domain. Used as supporting context in Framework Summaries and Idea Reports; not a monitored domain for proactive output. |

**Note on Creator Economy:** This domain does not yet have a dedicated vault path. Creator Economy findings are currently distributed across `knowledge/business/`, `knowledge/marketing/`, and `knowledge/startup/`. When a dedicated vault domain is created, this file will be updated.

---

## Required Knowledge Depth

| Domain | Depth Required | Description |
|---|---|---|
| Artificial Intelligence | Operational | The department must understand the structure of AI development, the difference between model types, common deployment patterns, and the AI tooling landscape without needing to research these basics for every request. Core concepts must be held in working knowledge. |
| Technology | Operational | Platform categories, software architecture concepts, adoption cycle dynamics, and developer ecosystem structure must be working knowledge. Specific technologies require on-demand research. |
| Business | Operational | Core business model categories, strategy frameworks, organizational concepts, and market structure dynamics must be working knowledge. Specific companies and industries require on-demand research. |
| Marketing | Operational | Channel mechanics, content format dynamics, audience segmentation concepts, and platform algorithm fundamentals must be working knowledge. |
| Psychology | Reference | The department consults psychology research when producing relevant outputs. Core cognitive bias and behavioral science vocabulary must be working knowledge; specific studies are accessed on demand. |
| Creator Economy | Operational | Monetization model categories, platform dynamics, creator-audience relationship structures, and creator tool categories must be working knowledge. |
| Startups | Reference | Funding stage structures, common startup failure patterns, and ecosystem dynamics must be working knowledge. Specific company research is on-demand. |
| Books | Reference | The department does not need to have read all books in the vault, but must know the vault contents well enough to retrieve relevant books when they apply to a research question. |
| Frameworks | Operational | The department must have working familiarity with major frameworks across the monitored domains and be able to retrieve and apply them without research for common frameworks. |
| Productivity | Reference | Core productivity methodology categories and research directions must be working knowledge. Specific tool and protocol research is on-demand. |

---

## Knowledge Used Per Workflow Step

| Workflow Step | Knowledge Consulted | Source |
|---|---|---|
| Step 1: Intake and Validation | Output type definitions; domain list | `OUTPUTS.md`, `RESPONSIBILITIES.md` |
| Step 2: Deduplication | Output log; prior research outputs | Output log system |
| Step 4: Source Assembly | Domain-specific source lists; reliability tier criteria | `QUALITY_STANDARDS.md`, domain knowledge |
| Step 5: Research and Synthesis | Domain working knowledge; vault entries for context; prior research | `knowledge/[domain]/`, Output log |
| Step 6: Output Drafting | Output schemas | `OUTPUTS.md` |
| Step 7: Quality Review | Quality gate criteria; source reliability standards | `QUALITY_STANDARDS.md` |
| Step 9: Vault Contribution | Vault entry templates; domain-specific templates | `knowledge/_templates/`, domain `Templates/` directories |

---

## Knowledge Gaps

| Knowledge Gap | Impact | Resolution Plan | Owner |
|---|---|---|---|
| Creator Economy vault domain | Creator Economy findings are distributed across multiple vault paths, reducing discoverability and consistency | Raise with Platform Director for a dedicated vault domain creation decision | Platform Director |
| Quantitative data access (market sizing, adoption metrics) | Some Trend Reports and Technology Reports cannot provide quantitative evidence for adoption claims | Identify and subscribe to appropriate data source; interim: downgrade confidence ratings on quantitative claims | Research Department |

---

## How This Department Contributes to the Knowledge Vault

The Research Department is the primary curator and contributor to the vault across its ten domains. Contribution is not optional — it is a core responsibility.

| Contribution Type | What It Is | Vault Path | Frequency |
|---|---|---|---|
| New concept or framework entries | Novel frameworks, mental models, or concepts identified through research that are not yet in the vault | `knowledge/frameworks/` or relevant domain | Ongoing; whenever a significant framework is identified through research |
| Book notes | Structured summaries of books read as part of Books domain monitoring or for Framework Summaries | `knowledge/books/` | Per book reviewed |
| AI tool and research entries | Technology and AI developments that have reached sufficient significance to warrant a permanent reference entry | `knowledge/ai/`, `knowledge/technology/` | When a development meets the significance threshold defined in SOPS |
| Business and startup case entries | Business model innovations, notable company cases, and startup patterns that will be referenced again | `knowledge/business/`, `knowledge/startup/` | Per significant case identified |
| Marketing and creator entries | Channel developments, platform changes, and creator economy patterns with lasting reference value | `knowledge/marketing/`, `knowledge/startup/` | Per significant development |
| Psychology concept entries | Behavioral research findings and cognitive science concepts relevant to the Build Better audience | `knowledge/psychology/` | Per significant finding |
| Framework and productivity entries | Frameworks and productivity methodologies with lasting reference value | `knowledge/frameworks/`, `knowledge/productivity/` | Per significant framework or methodology |
| Entry re-verifications | Review of existing entries approaching their expiry window to confirm currency or update as needed | Relevant domain | Per vault expiry alert |
| Entry archival | Moving superseded entries to Archive/ when a newer, more accurate entry replaces them | `[domain]/Archive/` | Per replacement |

**Contribution standard:** All vault entries from this department must include complete YAML frontmatter, a completed `tldr` field (one sentence), `status: active`, confidence reflecting actual verification depth, and at least one `related` link. Draft entries must not remain in draft status for more than five business days.

---

## Knowledge Maintenance Responsibilities

| Knowledge Asset | Review Frequency | Action Required |
|---|---|---|
| AI domain entries | Every 6 months | Re-verify currency and accuracy. AI developments move fast; entries older than 6 months without re-verification are candidates for archival or update. |
| Technology domain entries | Every 6 months | Re-verify. Platform and tool landscapes shift; outdated entries mislead downstream consumers. |
| Business, Marketing, Startup entries | Every 9 months | Re-verify. Slower-moving than AI/Tech but still subject to structural changes. |
| Psychology, Frameworks, Books entries | Every 18 months | Re-verify. These are slower-moving domains; entries tend to remain accurate longer. Verify that the framework or concept is still considered valid in the field. |
| Productivity domain entries | Every 12 months | Re-verify. Tool and methodology landscape evolves but less rapidly than AI/Tech. |

---

## Knowledge Dependencies Between Departments

| Knowledge Asset | Produced By | How This Department Uses It |
|---|---|---|
| Audience performance signals | Publishing Department | Informs monitoring priority — which topics in which domains are resonating with the audience. Used to calibrate Trend Report focus and Idea Report relevance. |
| Content gaps list | Content Department | Signals which research areas have insufficient vault depth. Triggers proactive Knowledge Updates and Research Briefs to fill the gaps. |
| Editorial calendar | Workflow Department | Informs which domain research is needed in the near term. Allows proactive monitoring to anticipate upcoming content assignments. |

---

## Knowledge Onboarding

When this department is first deployed:

- [ ] Access to all ten monitored vault domains confirmed.
- [ ] All required operational knowledge verified as `status: active` for core domain concepts.
- [ ] Domain monitoring source lists populated and verified for all ten domains.
- [ ] Output log is empty and ready to receive the first outputs.
- [ ] Creator Economy gap documented (gap is known and accepted; interim routing to `business/`, `marketing/`, `startup/` is in use).
- [ ] Knowledge gap resolution plans logged and owner confirmed.
