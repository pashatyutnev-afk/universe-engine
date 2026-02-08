# 13__MUS__CTL__MIX_TIGHTNESS__CTL__ENT

DOC_TYPE: ENTITY
ROLE: CTL
SCOPE: MUSIC / Mix instruction controller
CHANGELOG:
- 2026-02-08: Added as STOPGAP entity (v0.1)

---

## MISSION
Keep prompt mix notes consistent: tight low end, guitars dominant, avoid muddiness/busy hats.

---

## INPUTS
- ARR_PROFILE
- PROMPT_DRAFT

---

## OUTPUTS
- PROMPT_MIX_TIGHT
- NEGATIVE_UPDATED

---

## INTERFACES
- MUS.ARR.ROUTER
- MUS.QA.SUNO_CHECK

---

## GATES
- No conflicting mix notes
- Low-end tightness emphasized
- Avoid 'soft choir' wording

---

## NOTES
- Minimal placeholder to unblock orchestration. Expand later with KB links and strict contracts.
