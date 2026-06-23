# Books Knowledge Domain

Synthesized reading notes from the books that matter.

---

## Purpose

Reading without capture is recreation. This domain is where reading becomes compounding knowledge. Every entry represents a book whose ideas are worth preserving, challenging, and applying — and the synthesis work to make that possible.

The books in this vault are not necessarily the most famous or most recommended. They are the ones whose ideas have direct application to Build Better's work in media, technology, storytelling, business, and human performance.

---

## Knowledge Standards

A books entry earns `status: active` when it:

- Contains original synthesis, not just a list of the author's points — your job is to tell the reader what to take away, not to summarize the chapter structure
- Honestly evaluates the book: where it is strong, where it overreaches, where the evidence is thin
- Identifies the one or two ideas that are genuinely original or underrated
- Has a clear recommendation for who should read it and what they will get from it
- Links outward: what other entries in the vault does this book illuminate or connect to?
- Includes at least one verbatim quote that demonstrates the author's thinking at its best

**What good book notes look like:** A notes entry on a business book doesn't recap the chapter structure — it identifies the three ideas that are actually new, challenges the two claims the author does not support adequately, pulls the three quotes that encapsulate the argument, and explains what someone who has read it should do differently from someone who hasn't.

---

## Naming Standards

| Entry Type | Convention | Example |
|---|---|---|
| Book note | `<author-last>-<short-title>.md` | `kahneman-thinking-fast-slow.md` |
| Author profile | `<author-last>-profile.md` | `taleb-profile.md` |
| Reading list | `<topic>-reading-list.md` | `media-strategy-reading-list.md` |

Use the author's last name and a shortened title (3 words max). Drop articles (a, an, the).

---

## Cross Referencing

Every book note should link to at least one domain where the book's ideas apply:

- `frameworks/` — books that introduce or popularize mental models
- `psychology/` — behavioral science books
- `storytelling/` — craft and narrative books
- `business/` — business and strategy books
- `startup/` — startup and entrepreneurship books

---

## Metadata

```yaml
---
title: ""
domain: books
type: book-note | author-profile | reading-list
tags: []
created: ""
updated: ""
status: draft | active | archived
confidence: high
tldr: ""
related: []
author: ""
published_year: null
publisher: ""
genre: []
rating: null          # 1–10 integer
read_date: ""         # YYYY-MM-DD
key_concepts: []      # Array of concept names this book introduces or develops
---
```

**Rating guide:**
| Rating | Meaning |
|---|---|
| 9–10 | Required reading — foundational for Build Better's work |
| 7–8 | High value — read if the domain is relevant to your work |
| 5–6 | Useful in parts — read selectively or rely on this note |
| 3–4 | Interesting but thin — this note captures what's worth knowing |
| 1–2 | Not recommended — note exists to explain why |
