# Tools — Research Department

This file documents every tool, system, and integration the Research Department uses to perform its work. A change to any tool listed here requires a version update and a `CHANGELOG.md` entry.

---

## Core Tools

### Tool: Knowledge Vault

| Attribute | Value |
|---|---|
| **Category** | Knowledge Access and Contribution |
| **Purpose** | Primary repository for all institutional knowledge. Research Department reads from the vault for context and writes to it as the primary contributor of new and updated entries across its ten domains. |
| **Used In** | Workflow Steps 2 (deduplication), 4 (context and prior research), 9 (vault contribution) |
| **Access Level** | Read and Write |
| **Owned By** | Build Better OS Platform |
| **Failure Impact** | Cannot check for prior research (deduplication fails); cannot contribute Knowledge Updates; vault entries cannot be verified or archived. Department can continue producing outputs but all vault contributions are queued. |
| **Fallback** | Maintain a local working queue of pending vault contributions; apply them when vault access is restored. |

---

### Tool: Research Queue System

| Attribute | Value |
|---|---|
| **Category** | Workflow Management |
| **Purpose** | Tracks all incoming research requests, their status (queued, in-progress, completed, escalated, closed), priority tier, and delivery deadlines. Used to manage concurrency limits and provide status visibility to requesting departments. |
| **Used In** | Workflow Steps 1 (intake logging), 3 (queue management), 10 (closure) |
| **Access Level** | Read and Write |
| **Owned By** | Research Department |
| **Failure Impact** | Cannot track request status or enforce concurrency limits. Manual tracking required. Intake temporarily suspended at more than four concurrent items. |
| **Fallback** | Shared document maintained with requesting departments for manual queue tracking. Platform Director notified. |

---

### Tool: Output Log

| Attribute | Value |
|---|---|
| **Category** | Knowledge Access and Traceability |
| **Purpose** | Indexed archive of all completed research outputs. Enables deduplication checks, output retrieval by `output_id` and `trace_id`, and historical research reference. Prevents the same question from being answered twice. |
| **Used In** | Workflow Step 2 (deduplication), all output delivery steps |
| **Access Level** | Read and Write |
| **Owned By** | Research Department |
| **Failure Impact** | Cannot perform deduplication checks; risk of duplicate research. All outputs must be manually logged until system is restored. |
| **Fallback** | Local output index maintained in shared document. Retrospectively loaded into the Output Log when access is restored. |

---

### Tool: News and Signal Aggregator

| Attribute | Value |
|---|---|
| **Category** | Domain Monitoring |
| **Purpose** | Aggregates news, articles, announcements, and publications from defined sources across the ten monitored domains. Used for the daily signal scanning step of proactive monitoring and for source assembly in reactive research. |
| **Used In** | Workflow B (monitoring trigger assessment), Workflow A Step 4 (source assembly) |
| **Access Level** | Read |
| **Owned By** | Research Department (subscription) |
| **Failure Impact** | Domain monitoring cycle cannot run. Proactive output rate drops to zero. Source assembly for reactive research requires manual sourcing, which increases turnaround time. |
| **Fallback** | Manual monitoring of direct source feeds (publisher RSS feeds, platform announcement channels, curated newsletters). Processing time increases; Platform Director is notified. |

---

### Tool: Academic and Industry Source Access

| Attribute | Value |
|---|---|
| **Category** | Primary Source Access |
| **Purpose** | Access to peer-reviewed research, academic publications, and premium industry reports relevant to the monitored domains, particularly Psychology, Technology, AI, and Business. |
| **Used In** | Workflow A Step 4 (source assembly), Step 5 (research and synthesis) |
| **Access Level** | Read (licensed access) |
| **Owned By** | Research Department (subscription) |
| **Failure Impact** | Cannot access primary research for domains requiring academic sourcing. Source quality degrades for Psychology, AI, and Technology outputs. Confidence ratings on affected outputs are downgraded to reflect this. |
| **Fallback** | Open-access academic sources (preprint servers, open-access journals, institutional repositories). Quality noted in source reliability tier. Platform Director notified when premium access is unavailable. |

---

### Tool: Activity Log

| Attribute | Value |
|---|---|
| **Category** | Observability and Audit |
| **Purpose** | Structured, append-only log of every work item processed by the Research Department. Records intake, processing steps, quality gate results, rework events, delivery confirmations, and closure. |
| **Used In** | All workflow steps (logging) |
| **Access Level** | Write (append-only); Read (for internal review and quality audits) |
| **Owned By** | Research Department |
| **Failure Impact** | Cannot maintain audit trail. Research continues, but all unlogged activity must be reconstructed manually after restoration. |
| **Fallback** | Maintain a temporary local activity log; merge into system log when access is restored. |

---

## Supporting Tools

| Tool | Category | Purpose | Effect If Unavailable |
|---|---|---|---|
| Web search | Source discovery | Finding current sources, announcements, publications, and developments not yet captured by the aggregator | Increases source assembly time; some emerging developments may be missed during the outage window |
| Creator and industry newsletter corpus | Domain monitoring | Curated newsletters covering Creator Economy, Marketing, Startups, and Productivity domains. Primary signal source for fast-moving domain developments | Reduced signal coverage for affected domains; monitoring cycle relies more heavily on aggregator sources |
| Book and publication access | Knowledge access | Access to books, long-form reports, and whitepapers used for Books and Frameworks domain research | Framework Summaries and Book-domain outputs are delayed until access is restored; output type still available, turnaround extended |
| Trend and data visualization tools | Research synthesis | Visual tools for identifying patterns in quantitative data (adoption curves, search trend data, market data) | Trend Report sections relying on quantitative pattern evidence are noted as qualitative-only; confidence may be reduced |

---

## Integration Points

| System | Integration Type | Direction | Data Exchanged |
|---|---|---|---|
| Knowledge vault | File-based | Bidirectional | Reads existing entries for context; writes new and revised entries as Knowledge Updates |
| Research queue system | API | Bidirectional | Receives research requests; updates request status throughout the workflow |
| Output log | API | Bidirectional | Writes completed outputs; reads for deduplication and retrieval |
| Activity log | API | Outbound | Writes structured log entries at each workflow step |
| Escalation channel | Message | Outbound | Sends structured escalation notices to Platform Director |
| Requesting departments | Output channel | Outbound | Delivers completed research outputs |

---

## Access and Permissions

| Resource | Access Type | Granted By | Required For |
|---|---|---|---|
| Knowledge vault (`knowledge/`) | Read and Write | Platform Director | Vault contribution, prior research context |
| Output log | Read and Write | Research Department | Deduplication, output retrieval |
| Research queue system | Read and Write | Research Department | Request tracking and management |
| Activity log | Append (write) | Research Department | Audit trail |
| News aggregator | Read | Research Department (license) | Domain monitoring, source assembly |
| Academic source access | Read | Research Department (license) | Primary source research |

---

## Tool Onboarding

When this department is first deployed in an environment:

1. Verify knowledge vault access with a test read and a test write to a scratch entry (delete after verification).
2. Verify the research queue system is receiving test requests correctly.
3. Verify the output log is writable and readable.
4. Verify the activity log is accepting entries.
5. Confirm aggregator subscription is active and domain feeds are configured.
6. Confirm academic source access credentials are valid.
7. Run a complete test workflow item (Research Brief on a non-sensitive topic) from intake to delivery and vault contribution.
8. Confirm the Platform Director is receiving escalation notices from the escalation channel.

---

## Future Tool Needs

| Tool | Category | Rationale | Expected Impact |
|---|---|---|---|
| Structured domain signal scoring system | Domain Monitoring | A system that scores incoming signals by significance automatically, rather than relying on manual threshold assessment. Would reduce the subjectivity in the monitoring cycle and enable faster proactive output triggering. | Higher proactive output rate; reduced monitoring cycle time |
| Cross-domain pattern detection | Research Synthesis | A system that identifies when signals from multiple domains align, triggering Idea Reports proactively when cross-domain patterns are detected. | Enables more non-obvious Idea Reports; reduces dependence on reactive requests for ideation |
| Output retrieval with semantic search | Knowledge Access | The ability to search the output log by meaning rather than exact keyword, improving deduplication accuracy and enabling requesting departments to self-serve prior research. | Reduces duplicate requests; improves institutional memory utilization |
