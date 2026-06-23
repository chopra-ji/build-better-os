# Shared Templates

Canonical base templates for all Knowledge Vault entries.

## Purpose

These are the source-of-truth templates that define the YAML frontmatter schema and document structure for each entry type. Domain-specific templates in each domain's `Templates/` folder derive from these and add domain-specific fields.

When the base schema changes, update here first, then propagate to domain templates.

## Templates

| Template | Use For |
|---|---|
| [article.md](article.md) | Analysis of external articles, essays, papers |
| [book-note.md](book-note.md) | Reading notes for a completed book |
| [concept.md](concept.md) | Explanations of a mental model, idea, or principle |
| [framework.md](framework.md) | Structured frameworks and decision-making systems |
| [quote.md](quote.md) | Curated quotes with context |
| [resource.md](resource.md) | Tools, links, and external references |

## YAML Frontmatter Schema

### Common Fields (All Entry Types)

```yaml
title: ""          # Full entry title — sentence case, no trailing period
domain: ""         # Knowledge domain (ai, business, psychology, etc.)
type: ""           # Entry type (article, book-note, concept, framework, quote, resource)
tags: []           # Lowercase, kebab-case tags
created: ""        # YYYY-MM-DD
updated: ""        # YYYY-MM-DD
status: draft      # draft | active | archived
confidence: medium # low | medium | high — your confidence in this entry's accuracy
tldr: ""           # One sentence. If you can't write this, the thinking isn't done.
related: []        # Relative paths from vault root: ["frameworks/jobs-to-be-done.md"]
```

### Type-Specific Fields

**article**
```yaml
source_url: ""     # Original URL
source_author: ""  # Author name
source_date: ""    # YYYY-MM-DD publication date
publication: ""    # Publication name
```

**book-note**
```yaml
author: ""         # Book author(s)
published_year: null # Integer year
publisher: ""
genre: []          # Array of genres
rating: null       # 1–10 integer
read_date: ""      # YYYY-MM-DD
key_concepts: []   # Array of key concept names
```

**concept**
```yaml
origin: ""         # Who coined or popularized this concept
field: ""          # Academic or professional field it comes from
```

**framework**
```yaml
creator: ""        # Who created this framework
origin_year: null  # Integer year
maturity: ""       # emerging | established | foundational
best_for: []       # Array of use cases
```

**quote**
```yaml
author: ""         # Who said it
source: ""         # Book, speech, interview, etc.
year: null         # Integer year (approximate is fine)
context: ""        # One sentence on when/why it was said
```

**resource**
```yaml
url: ""            # Direct URL
resource_type: ""  # tool | dataset | course | podcast | newsletter | community
price_model: ""    # free | freemium | paid | subscription
```

## Confidence Field Guide

| Value | Meaning |
|---|---|
| `high` | Primary source verified, multiple corroborating sources |
| `medium` | Secondary source, generally accepted, spot-checked |
| `low` | Single source, unverified, personal interpretation |
