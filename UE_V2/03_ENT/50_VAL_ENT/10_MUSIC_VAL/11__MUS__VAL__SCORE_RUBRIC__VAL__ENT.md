# 11__MUS__VAL__SCORE_RUBRIC__VAL__ENT

DOC_TYPE: ENTITY
ROLE: VAL
SCOPE: MUSIC / Scoring rubric
CHANGELOG:
- 2026-02-08: Added as STOPGAP entity (v0.1)

---

## MISSION
Score candidates across hook, emotion arc, clarity, originality, brand fit, and platform compliance.

---

## INPUTS
- HOOK_POOL / LYRICS variants
- PROMPT variants

---

## OUTPUTS
- SCORECARD (0–10 per axis)
- WINNERS (per section)
- MERGE_GUIDE

---

## INTERFACES
- MUS.HOOK.FORGE
- MUS.PROMPT.PACK
- MUS.QA.*

---

## GATES
- Top pick Hook≥8, Emotion≥8, Clarity≥8, Compliance PASS

---

## NOTES
- Minimal placeholder to unblock orchestration. Expand later with KB links and strict contracts.
