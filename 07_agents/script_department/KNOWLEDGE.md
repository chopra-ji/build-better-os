# Knowledge — Script Department

---

## Knowledge Domains This Department Draws From

The Script Department draws on three types of knowledge: craft knowledge (how to write), format knowledge (how specific content formats behave), and brief intelligence (what a specific Creative Brief requires). The first two are sourced from the knowledge vault and from institutional practice. The third is sourced from the Creative Brief itself.

### Primary Vault Domains

| Domain | How the Script Department Uses It | Vault Path |
|---|---|---|
| **Storytelling** | The primary craft domain. Story arc structures, narrative tension mechanics, hook mechanics, payoff placement, secondary hook patterns. Every script draws on storytelling knowledge. | `knowledge/storytelling/` |
| **Psychology** | Understanding why audiences stop, continue, or disengage. Attention mechanics, emotional response patterns, the cognitive basis of curiosity gaps and knowledge progression. | `knowledge/psychology/` |
| **Editing** | Post-production craft as it intersects with scripting — how editing pacing decisions are set up in the script, how cut rhythm is anticipated in the script's pacing, how music direction interacts with scripted moments. | `knowledge/editing/` |
| **Marketing** | CTA mechanics, friction reduction patterns, conversion language, the relationship between emotional state and action. Directly relevant to Component 11 (CTA). | `knowledge/marketing/` |

### Secondary Vault Domains

| Domain | When Used | Vault Path |
|---|---|---|
| **AI** | When scripting content about AI, machine learning, or related technologies — for terminology accuracy and claim validation | `knowledge/ai/` |
| **Technology** | When scripting technology-focused content — for conceptual accuracy and appropriate register | `knowledge/technology/` |
| **Business** | When scripting business, operations, or organizational content | `knowledge/business/` |
| **Frameworks** | When a brief references a known framework (e.g., Jobs-to-be-Done, Lean, etc.) — the script must represent it accurately | `knowledge/frameworks/` |
| **Books** | When a brief references a specific book or idea — the script must represent the idea accurately and attribute correctly | `knowledge/books/` |
| **Quotes** | When a script includes a quotation — the script must use the verified version from the vault, not a common misquotation | `knowledge/quotes/` |
| **Design** | When scripting visual-heavy content where design principles are discussed or demonstrated | `knowledge/design/` |
| **Fitness** | When scripting fitness or health content — for claim accuracy and appropriate register | `knowledge/fitness/` |
| **Finance** | When scripting financial content — for accuracy, claim verification, and appropriate disclaimer awareness | `knowledge/finance/` |
| **Cars** | When scripting automotive content | `knowledge/cars/` |
| **Travel** | When scripting travel content — note that travel entries expire after 24 months; check `updated_at` before use | `knowledge/travel/` |
| **Startup** | When scripting startup, entrepreneurship, or venture content | `knowledge/startup/` |
| **Productivity** | When scripting productivity, workflow, or personal effectiveness content | `knowledge/productivity/` |

### Domains This Department Rarely Uses

| Domain | Notes |
|---|---|
| **Psychology (advanced clinical)** | The Script Department uses psychology at the consumer behavior and attention level, not at clinical depth. Briefs should not require clinical psychological claims in scripts. |

---

## Knowledge This Department Contributes

The Script Department contributes two types of knowledge to the vault:

### 1. Scripting Craft Entries

When the Script Department identifies a scripting pattern, hook structure, or retention mechanism that:
- Works consistently across multiple formats
- Is not already documented in the vault
- Is specific enough to be reusable (not "write a good hook" but a specific hook architecture with conditions for use)

...the Script Department creates or updates a `knowledge/storytelling/` entry documenting the pattern.

**Entry requirements (all vault standards apply):**
- YAML frontmatter with `status: draft` on creation
- `tldr` required for `status: active` promotion
- `confidence` reflects actual evidence (how many executions confirmed this pattern)
- At least one `related` link before promotion to `active`

### 2. Format-Specific Component Notes

When a content format evolves — a new format is introduced, or an existing format's component applicability changes — the Script Department updates the applicable component matrix in OUTPUTS.md and creates a vault entry in `knowledge/editing/` documenting the scripting standard for that format.

**Example:** If a new format "interactive_audio" is added to the platform, the Script Department defines:
- Which components apply
- How those components are structured for that format
- What production conventions differ from existing podcast or long_form_video conventions

This becomes the vault's reference for scripting that format going forward.

---

## Knowledge Reliability Standards

When using vault content in scripting decisions:

| Content Type | Reliability Requirement |
|---|---|
| Claims stated in the script (data, statistics, attributed quotes) | Must be `status: active` in the vault or sourced from the Creative Brief's `source_research_refs`; do not include claims from `status: draft` vault entries |
| Craft techniques (hook types, arc structures) | `status: active` or `status: draft` both acceptable — craft patterns do not have the same fact-claim reliability requirement |
| Attributed quotes | Must use the exact quote from `knowledge/quotes/` or from a source cited in the brief — never a paraphrase styled as a quote |
| Technical terminology | Use vault-standard terminology; do not introduce alternative terms for established concepts |

---

## Knowledge Gaps

| Gap | Description | Interim Approach |
|---|---|---|
| Platform-specific scripting norms | As the platform grows, some scripting patterns will become platform-wide standards. Until formal vault entries are created, platform norms are documented in SOPS.md. | Use SOPS.md until a formal vault entry exists |
| Creator Economy scripting conventions | The knowledge vault has no dedicated creator economy domain. Creator economy scripting conventions (e.g., YouTube retention mechanics, short-form hook patterns) are currently distributed across `storytelling/`, `psychology/`, and `marketing/` domains. | Reference all three domains; request consolidated vault entry via Platform Director if gap is consistently encountered |
| Format-specific performance data | The Script Department does not currently have access to performance data linking specific scripting approaches to content performance metrics. Scripting decisions are based on craft knowledge, not performance evidence. | Note this limitation in quality reviews; flag to Platform Director when performance feedback would improve scripting decisions |

---

## Knowledge Update Responsibility

The Script Department is responsible for:
- Flagging when a vault entry used in scripting is `status: archived` or has an `updated_at` older than 12 months (6 months for `ai/` domain entries)
- Requesting a Research Department review of flagged entries before using them as the basis for claims in scripts
- Promoting draft scripting craft entries to `active` after they have been validated across at least 3 executed scripts

The Script Department is **not** responsible for:
- Creating research entries (Research Department owns primary research output)
- Updating domain knowledge entries outside `storytelling/` and `editing/` (the Script Department contributes craft knowledge; domain knowledge is owned by Research Department)
- Deciding which topics to cover (Workflow Department)
