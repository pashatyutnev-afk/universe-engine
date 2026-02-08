# 11__MUS__HOOK_FORGE__ORC__ENT

DOC_TYPE: ENTITY
ROLE: ORC
SCOPE: MUSIC / Hook & Chorus engineering
CHANGELOG:
- 2026-02-08: Added as STOPGAP entity (v0.1)

---

## MISSION
Generate multiple hook/chorus candidates (3–12) with different rhythmic grammars and chant patterns; select top hooks for assembly.

---

## INPUTS
- TASK_TEXT
- STYLE_PROFILE (genre blend)
- CONSTRAINTS (platform, duration, structure)
- HERO_DATA (names, facts)
- BANNED (no slurs, no extreme profanity)

---

## OUTPUTS
- HOOK_POOL (ranked)
- CHORUS_FINAL (1)
- CHORUS_VARIANTS (optional)
- HOOK_NOTES

---

## INTERFACES
- IDX_MUSIC entry
- MUS.QA.SUNO_CHECK
- MUS.VAL.SCORE_RUBRIC

---

## GATES
- HOOK memorability ≥ 8/10
- Chorus is singable and short
- Constraint compliance PASS

---

## NOTES
- Minimal placeholder to unblock orchestration. Expand later with KB links and strict contracts.
