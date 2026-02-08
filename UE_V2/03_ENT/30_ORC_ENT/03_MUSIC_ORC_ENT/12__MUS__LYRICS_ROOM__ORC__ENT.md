# 12__MUS__LYRICS_ROOM__ORC__ENT

DOC_TYPE: ENTITY
ROLE: ORC
SCOPE: MUSIC / Lyric drafting
CHANGELOG:
- 2026-02-08: Added as STOPGAP entity (v0.1)

---

## MISSION
Draft verses, pre-chorus, bridge with strong imagery, internal rhyme, and narrative arc. Provide alt-lines for swap/merge.

---

## INPUTS
- TASK_TEXT
- HOOK_POOL/CHORUS_FINAL
- STYLE_PROFILE
- LEXICON (optional)
- BANNED

---

## OUTPUTS
- LYRICS_DRAFT v1
- ALT_LINES (by section)
- STORY_BEATS

---

## INTERFACES
- MUS.HOOK.FORGE
- MUS.CTL.TONE
- MUS.QA.LYRICS_CHECK

---

## GATES
- Narrative arc present
- No prohibited content
- Pronunciation-friendly RU

---

## NOTES
- Minimal placeholder to unblock orchestration. Expand later with KB links and strict contracts.
