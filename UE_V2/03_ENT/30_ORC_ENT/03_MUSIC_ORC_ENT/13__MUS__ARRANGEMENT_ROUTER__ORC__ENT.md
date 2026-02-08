# 13__MUS__ARRANGEMENT_ROUTER__ORC__ENT

DOC_TYPE: ENTITY
ROLE: ORC
SCOPE: MUSIC / Arrangement & sound profile
CHANGELOG:
- 2026-02-08: Added as STOPGAP entity (v0.1)

---

## MISSION
Translate style intent into arrangement tokens (tempo, half-time, instrument layers, dynamics) and generate 2–3 prompt profiles.

---

## INPUTS
- STYLE_PROFILE
- BPM/FEEL
- REFERENCE_VIBES (optional)
- PLATFORM

---

## OUTPUTS
- ARR_PROFILE_A/B/C
- DYNAMICS_PLAN (build, drop, silence, final lift)
- MIX_NOTES

---

## INTERFACES
- MUS.QA.SUNO_CHECK
- MUS.CTL.MIX_TIGHTNESS

---

## GATES
- Profiles distinct
- Avoid muddy low end
- Bridge->silence->lift explicitly defined

---

## NOTES
- Minimal placeholder to unblock orchestration. Expand later with KB links and strict contracts.
