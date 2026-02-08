# 12__MUS__QA__SUNO_PACKAGE_CHECK__QA__ENT

DOC_TYPE: ENTITY
ROLE: QA
SCOPE: MUSIC / Suno package check
CHANGELOG:
- 2026-02-08: Added as STOPGAP entity (v0.1)

---

## MISSION
Ensure prompt is concise, chorus length fixed, duration target, instrumentation tokens coherent.

---

## INPUTS
- SUNO_PACK (title/lyrics/prompt/negative)

---

## OUTPUTS
- QA_PASS
- SUGGESTED_TOGGLES

---

## INTERFACES
- MUS.PROMPT.PACK
- MUS.CTL.MIX_TIGHTNESS

---

## GATES
- Chorus exactly 4 lines
- No instruction conflicts
- Duration feasible

---

## NOTES
- Minimal placeholder to unblock orchestration. Expand later with KB links and strict contracts.
