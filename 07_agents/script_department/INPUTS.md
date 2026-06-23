# Inputs — Script Department

The Script Department has one required input and two optional supplementary inputs. Work does not begin until the required input passes validation.

---

## Required Input: Creative Brief

| Attribute | Value |
|---|---|
| **Source** | Creative Department |
| **Delivery Channel** | Output channel (logged, retrievable by output_id) |
| **Format** | Structured document conforming to Creative Department OUTPUTS.md schema |
| **Status Required** | `complete` |
| **Minimum Revision** | 0 (first delivery) or higher (revised brief) |

### Validation Checklist

Before scripting begins, the Creative Brief must pass all of the following:

| Check | Pass Condition | Fail Action |
|---|---|---|
| Status field | `status: complete` — not `draft`, not `escalated` | Hold; contact Creative Department for resolution |
| All 10 dimensions present | No dimension is null, empty, or contains placeholder text | Return to Creative Department with specific gap documented |
| Core message singularity | `core_message.statement` is one sentence containing one idea | Return to Creative Department — this is a brief quality failure, not a scripting decision |
| Hook concept specificity | `hook_direction.concept` is specific enough to execute (references what is said or shown in first 3–5 seconds) | Return to Creative Department with specificity request |
| Source research refs | `source_research_refs` contains at least one research output ID | Return to Creative Department — no brief dimension can rest on intuition |
| Format field | `format` is one of the six valid content formats | Hold; contact Creative Department |
| Revision number logged | `revision_number` is present and matches the expected delivery | Log mismatch; do not hold on this check alone |

### The Ten Brief Dimensions

Every Creative Brief must contain all ten dimensions. The Script Department maps its components directly to these dimensions during scripting.

| # | Dimension | Script Department Use |
|---|---|---|
| 1 | Content Angle | Frames the entire script — every scene and section must serve this angle |
| 2 | Target Audience | Calibrates word choice, pacing, assumed knowledge, and register |
| 3 | Core Message | The one idea the script must deliver — the test for every scripting decision |
| 4 | Hook Direction | Directly executed in Hook Component — type, concept, and promise must be honored |
| 5 | Retention Strategy | Determines story structure pacing, secondary hook placement, and payoff location |
| 6 | Story Arc | Defines scene order, development, tension, and resolution — mapped in Scene Breakdown |
| 7 | Visual Direction | Informs B-roll Notes, Camera Notes, and Editing Notes |
| 8 | Emotion | Calibrates tone, delivery notes, pacing, and emotional progression across the script |
| 9 | Curiosity Mechanism | Determines how knowledge gaps are opened, sustained, and resolved in the script |
| 10 | CTA Strategy | Directly executed in CTA Component — action, motivation, friction reduction |

---

## Optional Input 1: Supplementary Research

| Attribute | Value |
|---|---|
| **Source** | Research Department (via Creative Department or direct request) |
| **When Used** | When a brief dimension references a research finding that the Script Department needs to see directly to execute accurately — e.g., a specific data point that appears in the script, a quote that must be attributed, a technical claim that requires verification |
| **Format** | Research output conforming to Research Department OUTPUTS.md schema |
| **Required?** | No — the Creative Brief is the instruction document. Supplementary research is reference material only, never a substitute for a brief dimension. |

**Important:** Supplementary research does not grant the Script Department authority to reinterpret a brief dimension. If research suggests a different angle than what the brief specifies, the Script Department does not act on that signal — it executes the brief. A brief dimension conflict is escalated, not silently resolved.

---

## Optional Input 2: Script Package Revision Request

| Attribute | Value |
|---|---|
| **Source** | Production Team (returned Script Package) or Platform Director |
| **When Used** | When a delivered Script Package is returned with documented feedback on a specific component |
| **Format** | Structured revision request with: component name, specific issue description, requested change, and requestor identity |
| **Required?** | No — applies only to revision workflow |

### Revision Request Validity

A revision request is valid if and only if:
- It identifies a specific component by name (not "the script generally")
- It documents a specific issue (not "make it better")
- The requested change does not ask the Script Department to alter a brief dimension

A revision request that asks the Script Department to change the angle, core message, hook concept, or any other brief-owned dimension is out of scope. The Script Department documents this and escalates to the Platform Director rather than either complying or ignoring it.

---

## Input Rejection: Returning a Creative Brief

The Script Department may return a Creative Brief to the Creative Department when a specific dimension cannot be executed as written. This is not a failure of the scripting process — it is a quality signal about the brief.

### Return Conditions

A brief is returned when:

| Condition | Example |
|---|---|
| Hook concept is not specific enough to execute | "Use an engaging visual hook" — no concept, not executable |
| Core message contains more than one idea | Two-sentence core message presenting two separate claims |
| Story arc resolution contradicts the core message | Resolution concludes a different point than the message specifies |
| Format and visual direction are incompatible | Podcast format with required-visual key moments that cannot be audio-described |
| A dimension references content that requires research the brief doesn't supply | A data point is cited but no source research ref supports it |

### Return Package Contents

When returning a brief, the Script Department delivers:

```
return_id:          string (generated)
brief_ref:          string (output_id of the returned brief)
returned_at:        ISO 8601 timestamp
returned_by:        script_department
dimension_affected: string (which of the 10 dimensions cannot be executed)
issue_description:  string (specific, precise — what is wrong with this dimension)
execution_blocker:  string (what specifically cannot be done given the current specification)
revision_request:   string (what the Script Department needs the Creative Department to change)
```

The return package does not include the Script Department's preferred creative direction. It documents the blocker and requests a fix — creative resolution is the Creative Department's job.

### Return SLA

The Creative Department has **48 hours** to respond to a returned brief. If no response is received within 48 hours, the Script Department escalates to the Platform Director. The content item is held, not abandoned.

---

## Input Archival

Every received Creative Brief — whether executed, returned, or held — is logged with:
- `brief_ref` (the originating brief's output_id)
- `received_at` timestamp
- `disposition`: `in_progress` | `returned` | `completed` | `held`
- `disposition_at` timestamp
- `script_package_ref` (the output_id of the completed Script Package, when applicable)

This log is the primary audit trail linking Script Packages to their originating briefs.
