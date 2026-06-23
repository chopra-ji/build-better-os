# AI Knowledge Domain

Understanding artificial intelligence as a practitioner, not a spectator.

---

## Purpose

This domain captures Build Better's working knowledge of AI systems: what they can do, how to evaluate them, where they fail, and how to integrate them into media workflows. The goal is not academic completeness — it is operational clarity. Every entry should answer the question: what does knowing this let us do better?

This is not a place to collect news about AI. It is a place to build durable understanding of AI capabilities, limitations, and principles that remain true across model generations.

---

## Knowledge Standards

An AI entry earns `status: active` when it:

- Describes a capability, pattern, or limitation at the level of mechanism, not surface behavior ("why does this happen" not just "this happens")
- Is grounded in hands-on evaluation or a primary source, not secondhand summaries
- Distinguishes clearly between what is known, what is inferred, and what is speculated
- Has been tested against at least one real Build Better use case
- Includes a `confidence` rating that reflects actual verification depth
- Will remain materially accurate for at least 6 months (or is explicitly marked as time-sensitive)

**What good AI knowledge looks like:** A model evaluation entry documents the specific prompts used, the exact failure modes observed, the conditions under which performance varied, and the conclusion for which tasks this model is and is not appropriate. It reads like an engineer's field notes, not a marketing summary.

---

## Naming Standards

| Entry Type | Convention | Example |
|---|---|---|
| Model evaluation | `<model-name>-evaluation.md` | `gpt-4o-evaluation.md` |
| Tool review | `<tool-name>-review.md` | `cursor-review.md` |
| Research note | `<topic>-research.md` | `context-window-limits-research.md` |
| Concept | `<concept-name>.md` | `hallucination.md` |
| Technique | `<technique-name>.md` | `chain-of-thought.md` |

Use the tool or model's canonical name, lowercase, with hyphens. Do not include version numbers in filenames — use YAML frontmatter for version specificity.

---

## Cross Referencing

AI knowledge connects frequently to:

- `technology/` — infrastructure for running AI systems, API integration patterns
- `productivity/` — AI tools for individual and team workflows
- `frameworks/` — mental models for evaluating AI outputs and making AI-assisted decisions
- `psychology/` — cognitive biases that affect how humans interpret AI outputs

When an AI capability directly enables a media workflow, link explicitly to the relevant content domain entry.

---

## Metadata

**Required frontmatter for all AI entries:**

```yaml
---
title: ""
domain: ai
type: model-evaluation | tool-review | research-note | concept | technique
tags: []
created: ""
updated: ""
status: draft | active | archived
confidence: low | medium | high
tldr: ""
related: []
---
```

**Additional fields by type:**

For `model-evaluation`:
```yaml
model_name: ""      # Canonical model name
model_version: ""   # Specific version tested
provider: ""        # OpenAI, Anthropic, Google, Meta, etc.
test_date: ""       # YYYY-MM-DD
context_window: null # Integer token count
---
```

For `tool-review`:
```yaml
url: ""
provider: ""
price_model: free | freemium | paid | subscription
last_tested: ""     # YYYY-MM-DD
```

**Time sensitivity:** AI knowledge degrades faster than most domains. All entries older than 6 months should be reviewed and either reconfirmed or archived.
