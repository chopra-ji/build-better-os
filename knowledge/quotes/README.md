# Quotes Knowledge Domain

Precisely verified quotes with context and application.

---

## Purpose

Most quote collections are graveyards of misattribution and decoration. This vault's quotes domain is different: every entry is verified against a primary source, every quote earns its place by encoding a specific insight that prose cannot express as efficiently, and every entry includes the context that makes the quote meaningful rather than merely memorable.

For Build Better, quotes serve two purposes: they are a creative resource for content that quotes with integrity, and they are a compressed form of institutional wisdom — a way of carrying important ideas in a form that is easy to recall and transmit.

---

## Knowledge Standards

A quotes entry earns `status: active` when it:

- Has been verified against a primary source — the original book, speech, interview, or documented conversation
- Includes the full citation: author, source title, year, and context
- Is attributed accurately — many famous quotes are misattributed, truncated, or paraphrased into distortion
- Explains specifically why this quote earns its place: what insight does the language encode that a paraphrase would lose?
- Has at least one documented application — a specific situation at Build Better or in content where this quote is useful and appropriate

**Verification requirement:** If you cannot cite a primary source for a quote, it does not enter the vault as `status: active`. Save it as `status: draft`, note the attribution question, and research it before promoting it.

**What good quotes knowledge looks like:** A verified entry on a Buffett quote documents the exact transcript or book page, the year and context of the statement, why this particular phrasing is more precise than a paraphrase, and two specific situations where citing this quote adds value to content or decision-making.

---

## Naming Standards

| Entry Type | Convention | Example |
|---|---|---|
| Quote entry | `<author-last>-<2-3-word-slug>.md` | `buffett-price-value.md` |
| Author collection | `<author-last>-quotes.md` | `munger-quotes.md` |

Use the author's verified last name. Do not use pseudonyms unless the pseudonym is the primary attribution (e.g., Voltaire, not Arouet).

---

## Cross Referencing

Each quote should link to:
- The domain it most directly applies to (a quote about storytelling → `storytelling/`)
- The author's entry if one exists in `books/` (for author-creators)
- Frameworks or concepts the quote encodes

---

## Metadata

```yaml
---
title: ""
domain: quotes
type: quote
tags: []
created: ""
updated: ""
status: draft | active | archived
confidence: high
tldr: ""
related: []
author: ""
source: ""         # Book title, speech name, interview publication
year: null         # Year quote was spoken or published
context: ""        # One sentence: who was the audience, what was the occasion
verified: false    # true = primary source confirmed
primary_source_reference: ""  # "Page 47, Berkshire Hathaway Annual Report 1988"
---
```

**On confidence:** Quotes entries default to `confidence: high` because they should only become active once verified. If a quote is entered as `draft` pending verification, set `confidence: low`.
