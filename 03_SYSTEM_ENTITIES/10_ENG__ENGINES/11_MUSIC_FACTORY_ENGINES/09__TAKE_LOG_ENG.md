# TAKE LOG ENGINE (ENG)
SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 11_MUSIC_FACTORY_ENGINES
DOC_TYPE: ENGINE
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.MUS.ENG.TAKE_LOG.001
OWNER: SYSTEM
ROLE: Captures generation attempts (takes), changes between takes, and why a take won/lost.
NOTE: This engine prevents repeating failures and accelerates improvement.

---

## PURPOSE
Maintain deterministic memory for track generation attempts:
- what changed
- what improved/worsened
- which take becomes “best”
- which constraints should be kept/removed next iteration

---

## INPUT
- Track UID + current Track Card
- Prompt Contract (Suno/Udio) version
- Take links/ids from platform
- QA results (5s, 15s, hook panel, creator panel)
- Notes (short)

---

## OUTPUT
- Take Records (top 2–5 only; no clutter)
- “Win reasons” and “Fail reasons”
- Next-iteration adjustment list:
  - keep
  - change
  - ban

---

## PROCESS (STANDARD)
1) Collect takes from generation batch (links + short tags).
2) For each take, record:
   - what changed vs previous (tempo/voice/structure/negative packs)
   - QA quick scores + short comment
3) Select winners (top 1–2) and explain why.
4) Produce “Next iteration plan” if track is not yet PASS.

---

## MINI-CONTRACT
CONSUMES:
- takes + prompt contract + QA feedback
PRODUCES:
- take log (top takes + reasons + next-iteration plan)
DEPENDS_ON:
- CTL: PROMPT_CONTRACT_CTL
- CTL: SUNO_PHRASEBOOK_CTL / UDIO_PHRASEBOOK_CTL
- CTL: NEGATIVE_SPEC_LIBRARY_CTL
- CTL: QUALITY_GATES_CTL
OUTPUT_TARGET:
- Track folder: `.../TRACKS/TNN__.../03__TRACK__TAKES.md` (optional doc)
- Or Track Card appendix (if you keep it in one file)

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED
