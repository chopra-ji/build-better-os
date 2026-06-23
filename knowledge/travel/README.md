# Travel Knowledge Domain

Destination knowledge, logistics, and travel content craft.

---

## Purpose

Travel is a content vertical for Build Better and a lived experience of the people who work here. This domain serves both: it is a reference for producing accurate, distinctive travel content, and a practical guide for the team's own travel.

Travel knowledge decays. Visa requirements change, restaurants close, prices shift, borders open and close. Every entry must be dated and reviewed regularly. A travel entry that was accurate 18 months ago may be actively misleading today.

---

## Knowledge Standards

A travel entry earns `status: active` when it:

- Is dated precisely — travel information is highly time-sensitive and must be treated as such
- Distinguishes between what is timeless (a city's character, a region's culture, a landscape's nature) and what is perishable (prices, hours, availability, visa rules)
- Is specific enough to be actionable — "Barcelona is beautiful" is not knowledge
- Has been verified against a primary source (official tourism authority, official government visa portal, or direct experience)
- Includes a `verified_date` field and is archived when content becomes unreliable

**What good travel knowledge looks like:** An entry on a destination documents the practical logistics at the level of specificity that removes uncertainty (which airport terminal, which neighborhood to stay in and why, the specific transit option that is fastest vs. cheapest, the seasonal considerations that actually matter), plus the editorial angle — what makes this place interesting, what the clichéd take misses, what story is worth telling about it.

---

## Naming Standards

| Entry Type | Convention | Example |
|---|---|---|
| Destination | `<destination>.md` | `tokyo.md` |
| Itinerary | `<destination>-<days>-days.md` | `japan-14-days.md` |
| Logistics guide | `<topic>-<region>.md` | `visa-schengen.md` |
| Travel concept | `<concept>.md` | `slow-travel.md` |
| Hotel/property | `<property-name>.md` | `aman-tokyo.md` |

---

## Cross Referencing

- `storytelling/` — travel narrative technique, destination writing craft
- `design/` — travel photography, visual storytelling, location scouting
- `psychology/` — the psychology of novelty, culture shock, travel motivation
- `productivity/` — remote work travel, travel logistics optimization

---

## Metadata

```yaml
---
title: ""
domain: travel
type: destination | itinerary | logistics-guide | concept | property
tags: []
created: ""
updated: ""
status: draft | active | archived
confidence: low | medium | high
tldr: ""
related: []
---
```

**Additional fields for `destination` and `itinerary`:**
```yaml
region: ""              # Continent or major region
country: ""
verified_date: ""       # YYYY-MM — when logistics were last verified
best_season: []         # e.g., ["March", "April", "May"]
visa_required: ""       # For [nationality] passport holders
```

**Archiving rule:** Destination and itinerary entries older than 24 months without a `verified_date` update must be moved to Archive/.
