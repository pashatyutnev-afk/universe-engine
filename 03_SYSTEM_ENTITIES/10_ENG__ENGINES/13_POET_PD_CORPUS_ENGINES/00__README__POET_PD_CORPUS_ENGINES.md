# POET PD CORPUS ENGINES — REALM (README)
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/13_POET_PD_CORPUS_ENGINES/00__README__POET_PD_CORPUS_ENGINES.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
ENGINE_FAMILY: 13_POET_PD_CORPUS_ENGINES
DOC_TYPE: README
README_TYPE: REALM
LEVEL: L3
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.ENG.REALM.POET_PD_CORPUS.001
OWNER: SYSTEM
ROLE: Operational entrypoint for public-domain (PD) poetry usage: filtering, fit scoring,
“juice” extraction, mosaic composition, and excerpt collision control.

CHANGE_NOTE:
- DATE: 2026-01-12
- TYPE: MAJOR
- SUMMARY: "Created realm README for 13_POET_PD_CORPUS_ENGINES: scope, pipeline order, and RAW-only navigation."
- REASON: "PD-only lyric pipeline must be deterministic and safe."
- IMPACT: "Clean PD workflow + anti-repeat + better lyrical hooks."
- CHANGE_ID: UE.CHG.2026-01-12.ENG.REALM.POET_PD_CORPUS.001

---

## 0) PURPOSE (LAW)
This realm exists to ensure:
- only **public-domain** poetry (or explicitly allowed sources) are used
- we extract only the strongest fragments (“juice”)
- we can build a new lyric mosaic without dumping full poems
- we avoid reusing the same famous lines too often (excerpt collisions)

This is a **safety + quality** family for lyrics.

---

## 1) SCOPE & BOUNDARIES

### In scope
- PD filtering (source eligibility)
- poem/fragment fit scoring for a track brief
- extracting “hook-worthy” lines (juice)
- composing mosaics from fragments (with coherent voice)
- excerpt collision control (anti-repeat)

### Out of scope
- writing original lyrics from scratch (Track Factory / Lyricist SPC)
- music composition / melody decisions (09_SOUND_MUSIC_ENGINES)
- legal policy wording / enforcement thresholds (CTL/VAL)

---

## 2) PIPELINE ORDER (LAW)
Engines must be applied in this order unless a controller overrides:

01 — PD Filter  
02 — Poem Fit Scoring  
03 — Juice Extractor  
04 — Mosaic Composer  
05 — Excerpt Collision Guard

---

## 3) OUTPUT TYPES (WHAT THIS FAMILY PRODUCES)
- PD_ELIGIBILITY_REPORT (pass/fail + why)
- FIT_RANKING (top candidate poems/fragments)
- JUICE_PACK (selected best lines + cadence notes)
- MOSAIC_DRAFT (assembled lyric draft plan)
- EXCERPT_COLLISION_REPORT (what is overused / blocked)

---

## 4) NAV (RAW LINKS)

### Family templates
ENGINE TEMPLATE  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/13_POET_PD_CORPUS_ENGINES/00__TEMPLATE__ENGINE__POET_PD_CORPUS_ENGINES.md

README TEMPLATE  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/13_POET_PD_CORPUS_ENGINES/00__TEMPLATE__README__POET_PD_CORPUS_ENGINES.md

### Engines (canon order)
01 — PD Filter Engine  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/13_POET_PD_CORPUS_ENGINES/01__PD_FILTER_ENG.md

02 — Poem Fit Scoring Engine  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/13_POET_PD_CORPUS_ENGINES/02__POEM_FIT_SCORING_ENG.md

03 — Juice Extractor Engine  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/13_POET_PD_CORPUS_ENGINES/03__JUICE_EXTRACTOR_ENG.md

04 — Mosaic Composer Engine  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/13_POET_PD_CORPUS_ENGINES/04__MOSAIC_COMPOSER_ENG.md

05 — Excerpt Collision Guard Engine  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/13_POET_PD_CORPUS_ENGINES/05__EXCERPT_COLLISION_ENG.md

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED

--- END.
