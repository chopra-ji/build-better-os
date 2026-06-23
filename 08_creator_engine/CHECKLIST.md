# Checklist — Creator Engine

Operational checklists for every phase of a Creator Engine run. Use in sequence.

---

## Pre-Run: Input Validation

Before Stage 1 begins:

- [ ] Script Package received from Script Department
- [ ] `script` field present and non-empty
- [ ] `hook` field present and non-empty
- [ ] `cta` field present and non-empty
- [ ] `on_screen_text` field present (may be empty if not applicable)
- [ ] `caption_draft` field present (may be empty if not applicable)
- [ ] Engine run ID assigned
- [ ] Input script ID logged
- [ ] Run start timestamp recorded

If any required field is missing: reject input with structured error. Do not begin Stage 1.

---

## Stage 1 — Hook Review

- [ ] Hook line identified within the script
- [ ] Hook mechanism identified (question / contradiction / bold claim / pattern interrupt / identity statement)
- [ ] Hook evaluated against all six Stage 1 questions
- [ ] Score assigned (1–10)
- [ ] If score ≤ 6: optimization checklist applied, script revised, re-scored
- [ ] Score ≥ 7 confirmed before advancing
- [ ] Stage score and any changes logged

---

## Stage 2 — Retention Review

- [ ] Script structural beats mapped
- [ ] Re-hook location identified (must appear before 15-second mark)
- [ ] Drop-off risk points identified
- [ ] Script evaluated against all six Stage 2 questions
- [ ] Score assigned (1–10)
- [ ] If score ≤ 6: optimization checklist applied, script revised, re-scored
- [ ] Score ≥ 7 confirmed before advancing
- [ ] Stage score and any changes logged

---

## Stage 3 — Founder Voice Review

- [ ] Personal, specific claims identified
- [ ] Contrarian or unexpected perspective identified
- [ ] Script evaluated against all six Stage 3 questions
- [ ] Score assigned (1–10)
- [ ] If score ≤ 6: optimization checklist applied, script revised, re-scored
- [ ] Score ≥ 7 confirmed before advancing
- [ ] Stage score and any changes logged

---

## Stage 4 — Social Language Review

- [ ] Script read aloud (or simulated for spoken cadence)
- [ ] All sentences over 20 words identified
- [ ] Corporate or written-register vocabulary identified
- [ ] Script evaluated against all six Stage 4 questions
- [ ] Score assigned (1–10)
- [ ] If score ≤ 6: optimization checklist applied, script revised, re-scored
- [ ] Score ≥ 7 confirmed before advancing
- [ ] Stage score and any changes logged

---

## Stage 5 — Comment Engineering

- [ ] Comment trigger identified (or absence noted)
- [ ] Trigger type identified (question / poll / opinion challenge / identity statement / fill-in-the-blank)
- [ ] Trigger placement within script noted
- [ ] Script evaluated against all six Stage 5 questions
- [ ] Score assigned (1–10)
- [ ] If score ≤ 6: optimization checklist applied, script revised, re-scored
- [ ] Score ≥ 7 confirmed before advancing
- [ ] Stage score and any changes logged

---

## Stage 6 — Shareability Review

- [ ] Share trigger identified (or absence noted)
- [ ] Share emotion mapped (recognition / provocation / aspiration / humor / alarm)
- [ ] Trigger placement within script confirmed (must appear before 40-second mark)
- [ ] Script evaluated against all five Stage 6 questions
- [ ] Score assigned (1–10)
- [ ] If score ≤ 6: optimization checklist applied, script revised, re-scored
- [ ] Score ≥ 7 confirmed before advancing
- [ ] Stage score and any changes logged

---

## Stage 7 — Build Better Brand Review

- [ ] All claims verified as first-person and experience-backed
- [ ] Hype language scan complete
- [ ] Tone assessed: peer-to-peer confirmed
- [ ] Script evaluated against all five Stage 7 questions
- [ ] Score assigned (1–10)
- [ ] If score ≤ 6: optimization checklist applied, script revised, re-scored
- [ ] Score ≥ 7 confirmed before advancing
- [ ] Stage score and any changes logged

---

## Stage 8 — Instagram Optimization Review

- [ ] Word count of spoken script calculated
- [ ] Runtime estimated: word count ÷ 130 wpm
- [ ] Runtime within 45–60 seconds confirmed
- [ ] If runtime > 60 seconds: Runtime Compression Protocol run (see `OPTIMIZATION_PIPELINE.md`)
- [ ] If runtime < 40 seconds: under-length protocol run (see `OPTIMIZATION_PIPELINE.md`)
- [ ] Hook confirmed in opening sentence
- [ ] CTA confirmed in final spoken element
- [ ] Caption draft reviewed: first 125 characters checked
- [ ] On-screen text reviewed: no verbatim duplication of spoken lines
- [ ] Script evaluated against all six Stage 8 questions
- [ ] Score assigned (1–10)
- [ ] Score ≥ 7 confirmed before advancing
- [ ] Stage score and any changes logged

---

## Final Production Gate

- [ ] All eight stage scores recorded
- [ ] All eight scores ≥ 7
- [ ] Aggregate score calculated
- [ ] Aggregate score ≥ 56
- [ ] No dimension scored ≤ 4 at any point in this run
- [ ] Runtime 45–60 seconds confirmed
- [ ] Change log complete — every modification listed with stage, original, revised, and reason
- [ ] Production notes written for creator
- [ ] No open escalations
- [ ] Final Production Script status set to `approved`
- [ ] Run end timestamp recorded
- [ ] Full run record saved

---

## Escalation Checklist

When any escalation is triggered:

- [ ] Failing stage and score recorded
- [ ] Optimizations attempted (both attempts if applicable) documented
- [ ] Script state at time of escalation saved
- [ ] Escalation report prepared: failing dimension, scores, attempts, specific issue
- [ ] Escalation delivered to Platform Director (or Script Department if structural rework needed)
- [ ] Pipeline halted — no further stages run
- [ ] Escalation timestamp recorded
