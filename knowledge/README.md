# Knowledge Vault

The institutional knowledge base for Build Better Media Company.

---

## What This Is

The Knowledge Vault is where Build Better captures, organizes, and compounds its understanding of every domain that matters to the company. It is not a link dump. It is not a wiki. It is a structured system where every entry has a defined format, a quality standard, and a place in a larger map of understanding.

A media company's most durable competitive advantage is what it knows and how quickly it learns. This vault is how we make that advantage structural rather than personal.

---

## Domains

| Domain | Focus |
|---|---|
| [AI](ai/README.md) | Models, tools, evaluation, emerging capabilities |
| [Technology](technology/README.md) | Infrastructure, software, platforms, technical patterns |
| [Business](business/README.md) | Models, strategy, operations, industry analysis |
| [Marketing](marketing/README.md) | Audience, distribution, brand, growth |
| [Psychology](psychology/README.md) | Behavior, cognition, persuasion, motivation |
| [Storytelling](storytelling/README.md) | Narrative structure, technique, craft |
| [Editing](editing/README.md) | Editorial standards, copy, video, audio |
| [Design](design/README.md) | Visual design, UX, brand, layout |
| [Fitness](fitness/README.md) | Health, performance, recovery, protocols |
| [Finance](finance/README.md) | Analysis, models, media economics, investment |
| [Cars](cars/README.md) | Automotive industry, reviews, technical knowledge |
| [Travel](travel/README.md) | Destinations, logistics, content, culture |
| [Startup](startup/README.md) | Strategy, growth, fundraising, operations |
| [Productivity](productivity/README.md) | Systems, workflows, tools, habits |
| [Books](books/README.md) | Reading notes, synthesis, key concepts |
| [Frameworks](frameworks/README.md) | Mental models, decision tools, thinking systems |
| [Quotes](quotes/README.md) | Curated quotes with context and application |

---

## Vault Structure

Each domain follows an identical structure:

```
<domain>/
├── README.md       ← domain purpose, standards, and conventions
├── INDEX.md        ← navigable directory of all entries
├── Templates/      ← domain-specific entry templates
├── Resources/      ← curated external references and tools
├── Archive/        ← deprecated or superseded entries
└── Examples/       ← annotated examples of high-quality entries
```

Shared base templates live in [`_templates/`](_templates/README.md). Domain templates derive from these.

---

## Entry Lifecycle

```
Draft → Active → Archived
```

- **Draft** — incomplete, not yet ready for use
- **Active** — complete, current, and trustworthy
- **Archived** — superseded, outdated, or no longer relevant (kept for history)

Never delete entries. Archive them.

---

## Quality Standard

An entry earns `status: active` when it:

1. Has complete and accurate YAML frontmatter
2. Has a clear, specific `tldr` (one sentence — if you can't write one, the thinking isn't done)
3. Contains original synthesis, not just a copy of source material
4. Has at least one `related` link to another entry
5. Has been reviewed for accuracy within the last 12 months

---

## Cross-Domain Linking

Entries link to each other using relative paths from the vault root:

```
related:
  - ai/INDEX.md
  - frameworks/first-principles-thinking.md
```

Use the `related` YAML field for structured links. Use inline markdown links for in-text references.

---

## Naming Conventions

| Thing | Convention | Example |
|---|---|---|
| Entry files | `kebab-case.md` | `loss-aversion.md` |
| Template files | `kebab-case.md` | `concept.md` |
| Domain folders | `lowercase` | `psychology/` |
| Multi-word entries | `kebab-case` | `jobs-to-be-done.md` |

Never use spaces in filenames. Never use uppercase in filenames (except `README.md`, `INDEX.md`).

---

## Metadata Schema

See [`_templates/`](_templates/README.md) for the full YAML frontmatter specification and all base templates.
