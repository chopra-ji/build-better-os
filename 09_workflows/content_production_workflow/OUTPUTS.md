# Outputs — Content Production Workflow

This file defines what each stage produces and what the final workflow output is. Every output is traceable to its upstream input through a shared `workflow_run_id`.

---

## Workflow Run ID

Every content production run is assigned a `workflow_run_id` at Stage 1 (Idea). This ID travels with every document produced throughout the workflow. It is the primary key for tracing any output back to its originating idea.

---

## Stage Outputs Summary

| Stage | Produces | Consumer |
|---|---|---|
| Stage 1 — Idea | Idea Record | Research Department |
| Stage 2 — Research | Research Output (Brief / Report) | Creative Department |
| Stage 3 — Creative | Creative Brief | Script Department |
| Stage 4 — Script | Script Package | Creator Engine |
| Stage 5 — Creator Engine | Final Production Script | Stage 6 (routing) |
| Stage 6 — Routing | Founder Review Package | Founder |
| Stage 7 — Founder Review | Approval / Revision Request / Rejection | Stage 8 or upstream |
| Stage 8 — Production | Production Package | Stage 9 (Publishing) |
| Stage 9 — Publishing | Publish Record | Activity log / archive |

---

## Stage 1 — Idea Record

The Idea Record is the workflow's trigger document. It captures the raw content idea in structured form. It does not solve the content — it frames the problem for the Research Department.

See `INPUTS.md` → Stage 1 for the full schema.

**Archived:** Yes. Retained as the originating document for the workflow run.

---

## Stage 2 — Research Output

The Research Department produces one or more structured output documents addressing the research question implicit in the Idea Record. The most common output for a content idea is a Research Brief.

Output types and full schemas: `07_agents/research_department/OUTPUTS.md`.

**Archived:** Yes. Retained as the research foundation for the workflow run.

---

## Stage 3 — Creative Brief

The Creative Brief is a fully structured ten-dimension document that defines what the content piece is — its angle, audience, message, hook, retention strategy, story arc, visual direction, emotion, curiosity mechanism, and CTA.

Full schema: `07_agents/creative_department/OUTPUTS.md`.

**Archived:** Yes. The Script Department's work is evaluated against this document throughout production.

---

## Stage 4 — Script Package

The Script Package is the complete production document produced by the Script Department. It includes the full spoken script and all applicable production components (hook, scene breakdown, voiceover notes, talking head notes, b-roll notes, camera notes, editing notes, on-screen text, caption draft, CTA).

Full schema and format-component applicability matrix: `07_agents/script_department/OUTPUTS.md`.

**Archived:** Yes. The Creator Engine's changes are logged against this as the baseline.

---

## Stage 5 — Final Production Script

The Creator Engine's approved output. The Final Production Script contains the optimized spoken script, all eight dimension scores, the change log, runtime estimate, production notes, and finalized caption.

Full schema: `08_creator_engine/ARCHITECTURE.md`.

**Archived:** Yes. This is the document the Founder reviews and the creator records from.

---

## Stage 6 — Founder Review Package

The Founder Review Package is a compiled document assembled for human review. It does not add new content — it packages the Creator Engine output into a format designed for the Founder's review task.

```
founder_review_package_id:  string
workflow_run_id:             string
assembled_at:                ISO 8601 timestamp

final_script:                string (full spoken content)
runtime_estimate:            string
word_count:                  integer
dimension_scores:            object (all 8 scores)
aggregate_score:             integer
change_log:                  list (all Creator Engine modifications)
production_notes:            string
caption:                     string
```

**Archived:** Yes, as part of the workflow run record.

---

## Stage 7 — Founder Review Decision

A structured decision document: Approval, Revision Request, or Rejection.

Full schemas: `INPUTS.md` → Stage 7.

**Archived:** Yes. The Founder's decision and reasoning are retained as part of the workflow run record.

---

## Stage 8 — Production Package

The Production Package is the output of the recording and editing stage. It contains the final video file, the caption as it will be published, content metadata, and a log of any deviations from the approved script.

Full schema: `INPUTS.md` → Stage 8.

**Archived:** Yes. The video file is retained as a production asset.

---

## Stage 9 — Publish Record (Final Workflow Output)

The Publish Record is the final output of the Content Production Workflow. It confirms that the content has been published and provides the information needed to trace the published post back to its originating idea.

```
publish_record_id:    string
workflow_run_id:      string
published_by:         string
published_at:         ISO 8601 timestamp

platform:             instagram_reels
post_url:             string
caption_published:    string
cover_frame_ref:      string (optional)

workflow_summary:
  idea_record_id:     string
  research_output_id: string
  creative_brief_id:  string
  script_package_id:  string
  engine_run_id:      string
  founder_review_id:  string
  production_id:      string
```

**Archived:** Yes. The Publish Record closes the workflow run and connects the published post to every document produced during the run.

---

## Workflow Archive

When a workflow run is closed, all stage outputs are archived together under the `workflow_run_id`. The archive contains:

- Idea Record
- Research Output(s)
- Creative Brief
- Script Package
- Final Production Script (Creator Engine output)
- Founder Review Package
- Founder Review Decision
- Production Package
- Publish Record

The archive is the complete, auditable history of how that piece of content was created.

Cancelled runs (idea rejected at Stage 7 or abandoned at any stage) are archived with their final state and a `status: cancelled` record. They are not deleted.
