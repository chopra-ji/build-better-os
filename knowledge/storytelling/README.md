# Storytelling Knowledge Domain

The craft of narrative — structure, technique, and the mechanics of why stories work.

---

## Purpose

Build Better is a media company. Everything it makes tells a story in some form. This domain captures the craft knowledge that separates stories that move people from stories that merely inform them.

This is not a repository of story ideas. It is a repository of structural understanding: why certain narrative choices work, what the underlying mechanics are, and how to apply them deliberately rather than by intuition alone.

---

## Knowledge Standards

A storytelling entry earns `status: active` when it:

- Explains why a technique works at the level of human psychology or cognitive processing — not just that it works
- Demonstrates the concept with a concrete example from published work (film, book, article, podcast, script)
- Distinguishes between what is a proven principle and what is a stylistic preference
- Is precise enough to be actionable — a writer could apply this in their next draft
- Notes the genre, format, or medium where the technique is most applicable and where it fails

**What good storytelling knowledge looks like:** An entry on the "false ending" technique explains what it is, why audiences find it satisfying (the psychology of expectation and subversion), demonstrates it in three specific examples from different formats, explains when it works and when it feels manipulative, and provides one concrete exercise for practicing it.

---

## Naming Standards

| Entry Type | Convention | Example |
|---|---|---|
| Narrative structure | `<structure-name>.md` | `three-act-structure.md` |
| Technique | `<technique>.md` | `in-media-res.md` |
| Story analysis | `<title>-analysis.md` | `shawshank-redemption-analysis.md` |
| Concept | `<concept>.md` | `narrative-transportation.md` |
| Format-specific guide | `<format>-storytelling.md` | `podcast-storytelling.md` |

---

## Cross Referencing

- `psychology/` — the cognitive science behind why stories work (transportation theory, narrative identity, emotional contagion)
- `editing/` — how narrative decisions are executed in the editing process
- `books/` — story craft books and their key frameworks
- `frameworks/` — structured storytelling frameworks (Hero's Journey, Story Circle, etc.)
- `design/` — visual storytelling, layout as narrative

---

## Metadata

```yaml
---
title: ""
domain: storytelling
type: structure | technique | analysis | concept | format-guide
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

For `technique`:
```yaml
applicable_formats: []    # article | video | podcast | social | all
difficulty: beginner | intermediate | advanced
```

For `analysis`:
```yaml
work_title: ""
creator: ""
format: film | book | article | podcast | series | other
year: null
```
