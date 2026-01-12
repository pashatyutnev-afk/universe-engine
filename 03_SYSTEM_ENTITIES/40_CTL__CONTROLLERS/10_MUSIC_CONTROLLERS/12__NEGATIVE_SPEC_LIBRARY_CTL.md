# NEGATIVE SPEC LIBRARY — CTL
FILE: 03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/12__NEGATIVE_SPEC_LIBRARY_CTL.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: CONTROLLERS (CTL)
CTL_REALM: 10_MUSIC_CONTROLLERS
DOC_TYPE: CONTROLLER
CTL_TYPE: NEGATIVE_SPEC_LIBRARY
LEVEL: L3
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.CTL.MUS.NEGATIVE_SPEC_LIBRARY.001
OWNER: SYSTEM
ROLE: Reusable negative-spec packs (“DON'T” packs) to prevent platform hallucination, clichés, bad loops,
unwanted genre drift, muddy vocals, and overproduction. Used by Prompt Compiler / Prompt Architect and enforced by
Repeat Guard / Prompt Fidelity gates.

CHANGE_NOTE:
- DATE: 2026-01-12
- TYPE: MAJOR
- SUMMARY: "Rebuilt Negative Spec Library as operational pack registry: standardized packs, selection rules, and hard blockers."
- REASON: "Prior file was a 1-line stub; production needs deterministic reusable negative packs."
- IMPACT: "Cleaner outputs, fewer spam loops, less drift, higher prompt fidelity."
- CHANGE_ID: UE.CHG.2026-01-12.CTL.NEGATIVE.SPECS.001

---

## 0) PURPOSE (LAW)
Negative Spec Library provides **standard reusable negative packs** that can be attached to prompts.
It prevents repeated failure modes:
- endless repetition loops
- mumble / unclear diction
- unwanted genre drift / genre soup
- overproduced clutter and loss of groove
- cliché lyric lines and generic phrasing

This CTL defines:
- available packs
- when to use which pack
- how many packs may be attached (anti-bloat)

---

## 1) PACK SELECTION RULE (MANDATORY)
Default selection per track:
- MUST include **1–2 packs** by default.
- MAY include **up to 3 packs** when risk is high (repair mode).
- HARD MAX: 4 packs (requires explicit reason recorded in output notes).

Never add raw long “walls of negatives”.
Always prefer packs.

---

## 2) PACK OUTPUT FORMAT (MANDATORY)
Each pack must define:
- PACK_ID
- PURPOSE
- NEGATIVE_ITEMS (concrete, short)
- WHEN_TO_USE
- CONFLICTS / NOTES (optional)

Prompt producers must output:
- SELECTED_PACKS: [PACK_ID...]
- EXPANDED_NEGATIVES: merged list (deduped, concrete)

---

## 3) PACKS (REUSABLE / CANON)

### PACK: NO_ENDLESS_REPEAT
PACK_ID: NO_ENDLESS_REPEAT
PURPOSE: Prevent identical phrase loops / chant spam / copy-paste chorus repeats.
NEGATIVE_ITEMS:
- "no endless repetition"
- "no chant spam"
- "avoid repeating the exact same line over and over"
- "no copy-paste chorus loops"
- "avoid stuck hook loops"
WHEN_TO_USE:
- always for UGC-first OR when Repeat Guard risk is medium/high

---

### PACK: CLEAR_DICTION
PACK_ID: CLEAR_DICTION
PURPOSE: Prevent mumble and unclear consonants; keep lead intelligible.
NEGATIVE_ITEMS:
- "no mumble vocals"
- "clear diction, avoid slurred consonants"
- "avoid muddy lead vocal"
- "no buried vocals"
WHEN_TO_USE:
- lyrical tracks, RU vocals, or when recognition depends on Q-line

---

### PACK: NO_UNWANTED_GENRE_DRIFT
PACK_ID: NO_UNWANTED_GENRE_DRIFT
PURPOSE: Prevent random genre switching and accidental style collapse.
NEGATIVE_ITEMS:
- "no genre switching"
- "avoid genre soup"
- "no unexpected style changes"
- "do not drift away from the core genre identity"
WHEN_TO_USE:
- fusion risk exists OR identity anchors must stay locked

---

### PACK: KEEP_SPACE_NOT_OVERPRODUCED
PACK_ID: KEEP_SPACE_NOT_OVERPRODUCED
PURPOSE: Prevent overproduction clutter; keep groove and space.
NEGATIVE_ITEMS:
- "no overproduced wall of sound"
- "avoid cluttered layers"
- "avoid too many random instruments"
- "no excessive effects that smear the groove"
WHEN_TO_USE:
- when mixes get busy, or groove clarity is a known risk

---

### PACK: NO_CLICHE_LYRICS
PACK_ID: NO_CLICHE_LYRICS
PURPOSE: Prevent generic cliché lines and cheap phrases.
NEGATIVE_ITEMS:
- "avoid cliché lyrics"
- "no generic love song phrases"
- "avoid overused slogans"
- "no corny punchlines"
WHEN_TO_USE:
- lyrical tracks, especially meme/punch or emo-quote modes

---

### PACK: NO_MUDDY_LOW_END
PACK_ID: NO_MUDDY_LOW_END
PURPOSE: Prevent muddy low end that kills groove and translation.
NEGATIVE_ITEMS:
- "no muddy bass"
- "avoid boomy low end"
- "no distorted low-end blur"
WHEN_TO_USE:
- club/gym energy, bass-driven tracks, or translation issues flagged

---

### PACK: NO_GENERIC_VOCAL
PACK_ID: NO_GENERIC_VOCAL
PURPOSE: Prevent “same vocalist everywhere” syndrome (generic delivery).
NEGATIVE_ITEMS:
- "avoid generic pop vocal delivery"
- "no bland lead vocal"
- "avoid samey vocal tone"
WHEN_TO_USE:
- when vocal diversity is a key objective or catalog sameness is detected

---

## 4) DEDUP & BLOAT CONTROL (HARD RULES)
- Deduplicate identical negatives across packs.
- Remove vague negatives ("bad", "boring", "viral", "cool").
- Keep final negative list:
  - recommended 8–20 items
  - hard max 30 items (Prompt Contract CTL)

---

## 5) REQUIRED USAGE (WHO MUST APPLY THIS)
- Prompt Compiler ENG must select 1–2 packs by default.
- Prompt Architect SPC must ensure negatives remain concrete and deduped.
- Track Factory must carry selected packs into prompt pack snapshots.
- TEST→DOC gate uses Repeat Guard + Prompt Fidelity to catch violations.

---

## 6) DEPENDENCIES (RAW)
Must align with:
- Prompt Contract CTL  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/01__PROMPT_CONTRACT_CTL.md
- Suno Phrasebook CTL  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/10__SUNO_PHRASEBOOK_CTL.md
- Udio Phrasebook CTL  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/11__UDIO_PHRASEBOOK_CTL.md

Validator alignment:
- Repeat Guard VAL  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/03__REPEAT_GUARD_VAL.md
- Prompt Fidelity VAL  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/08__PROMPT_FIDELITY_VAL.md

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED

--- END.
