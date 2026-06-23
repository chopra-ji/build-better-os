# Scoring System — Creator Engine

---

## Overview

Every stage in the Creator Engine produces a score from 1–10 for its dimension. These scores are aggregated into a single engine run score. The aggregate score determines whether the script is approved, escalated, or rejected.

---

## Dimension Scoring Scale

Each dimension uses the same 1–10 scale:

| Score | Label | Meaning |
|---|---|---|
| 9–10 | Excellent | The dimension is fully optimized. No changes required. |
| 7–8 | Pass | The dimension meets the standard. Minor improvements possible but not required. |
| 5–6 | Borderline | The dimension falls short of the standard. Optimization is required before advancing. |
| 3–4 | Fail | The dimension has significant problems. Full optimization cycle required. |
| 1–2 | Critical Fail | The dimension is broken. The script cannot advance until this is resolved. |

---

## Per-Dimension Pass Threshold

Every dimension has a pass threshold of **7**. A score of 6 or below triggers the optimization cycle for that stage before the script advances. A score of 4 or below on any single dimension triggers automatic escalation regardless of the aggregate score.

| Dimension | Pass Threshold | Auto-Escalation Threshold |
|---|---|---|
| Hook | 7 | ≤ 4 |
| Retention | 7 | ≤ 4 |
| Founder Voice | 7 | ≤ 4 |
| Social Language | 7 | ≤ 4 |
| Comment Engineering | 7 | ≤ 4 |
| Shareability | 7 | ≤ 4 |
| Build Better Brand | 7 | ≤ 4 |
| Instagram Optimization | 7 | ≤ 4 |

---

## Aggregate Score

The aggregate score is the sum of all eight dimension scores.

| Aggregate | Range | Interpretation |
|---|---|---|
| Maximum | 80 | All dimensions excellent |
| Pass threshold | 56 (70%) | Minimum to approve for production |
| Caution zone | 48–55 | Approved with production notes flagging weak dimensions |
| Fail | ≤ 47 | Not approved; return to Script Department with full score report |

**A script may not be approved if any single dimension scored ≤ 4, regardless of aggregate score.**

---

## Scoring Discipline

Scores are not rounded toward leniency. The scoring system exists to protect production quality, not to approve scripts. When in doubt between two scores, use the lower one and document the reasoning. Optimizations are inexpensive; a weak script in production is expensive.

---

## Score Recording

Every score is logged in the pipeline run record with:
- The numeric score
- The specific criteria that were met or failed
- The optimizations applied (if any)
- The post-optimization score (if re-scored)

Scores may not be changed retroactively once a stage is complete. If an earlier stage score is found to be incorrect upon review of a later stage, the discrepancy is noted in the run record and flagged for escalation — the pipeline is not rewound.
