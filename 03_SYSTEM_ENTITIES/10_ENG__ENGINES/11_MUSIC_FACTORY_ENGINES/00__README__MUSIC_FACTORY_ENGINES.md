# MUSIC FACTORY ENGINES — README (REALM)
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/11_MUSIC_FACTORY_ENGINES/00__README__MUSIC_FACTORY_ENGINES.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
DOC_TYPE: README
README_TYPE: REALM
LEVEL: L3
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.ENG.REALM.MUSIC_FACTORY.001
OWNER: SYSTEM
ROLE: Realm entrypoint for the Music Factory pipeline (group → artists → album → tracks → release), with novelty + collision control

CHANGE_NOTE:
- DATE: 2026-01-11
- TYPE: MAJOR
- SUMMARY: "Created realm README for Music Factory engines family."
- REASON: "Need a deterministic entrypoint explaining scope/boundaries and how to run music production pipeline."
- IMPACT: "Music Factory family becomes navigable and operational."
- CHANGE_ID: UE.CHG.2026-01-11.ENG.REALM.MUSIC_FACTORY.001

---

## 0) WHAT THIS REALM IS
This family contains engines that turn strategy into production:
- define GROUP foundation (identity + brand + sonic DNA)
- build ARTIST roster (vocals + instruments + roles)
- blueprint ALBUM structure (concept + arc + track roles)
- manufacture TRACK variants for testing
- enforce DURATION strategy by style/format
- package RELEASE (variants, metadata, credits)
- prevent repeats via catalog memory + fingerprint collision
- inject novelty safely when output becomes too similar

This is the “factory layer” that coordinates creative systems into repeatable output.

---

## 1) SCOPE & BOUNDARIES (CRITICAL)
### 1.1 In scope
- Group creation as a production object (not lore-character)
- Artist roster design (vocal/instrument personas + roles)
- Album blueprinting (track map, arcs, sequencing intent)
- Track generation strategy (variants + hooks + structure targets)
- Duration policy enforcement per format
- Release packaging (versions, edits, metadata pack)
- Collision avoidance (style fingerprint + catalog memory)
- Novelty injection (controlled mutation, not random noise)
- Take log (generation attempts history)

### 1.2 Out of scope
- Deep music theory composition (belongs to `09_SOUND_MUSIC_ENGINES`)
- Production audio sync/editing (belongs to `08_KNOWLEDGE_PRODUCTION_ENGINES`)
- Trend research taxonomy (belongs to `12_TREND_GENRE_ENGINES`)
- Public-domain poet corpus handling (belongs to `13_POET_PD_CORPUS_ENGINES`)
- Naming system itself (belongs to `14_NAMING_IDENTITY_ENGINES`)

---

## 2) RULES USED (REFERENCES ONLY)
- ENG global rules:
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/01__RULES__ENGINES.md
- ENG global index:
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/02__INDEX_ALL_ENGINES.md

---

## 3) HOW TO USE (OPERATIONAL)
Recommended pipeline (high level):
1) Run `01__GROUP_FOUNDATION_ENG` → create group DNA + audience intent.
2) Run `02__ARTIST_FACTORY_ENG` → roster: vocal + instrument personas.
3) Run `03__ALBUM_BLUEPRINT_ENG` → album concept + track map.
4) Run `04__TRACK_FACTORY_ENG` → generate 2–5 variants per track for testing.
5) Run `05__DURATION_STRATEGY_ENG` → lock durations per style/format (no chaos).
6) Run `07__CATALOG_COLLISION_ENG` → check for repeats/collisions.
7) If similarity too high → `08__NOVELTY_INJECTION_ENG`.
8) When approved → `06__RELEASE_PACK_ENG` to produce release pack.
9) Log every attempt with `09__TAKE_LOG_ENG`.

---

## 4) STRUCTURE (WHAT FILES EXIST HERE)
### Mandatory
- 00__README__MUSIC_FACTORY_ENGINES
- 00__TEMPLATE__ENGINE__MUSIC_FACTORY_ENGINES
- 00__TEMPLATE__README__MUSIC_FACTORY_ENGINES
- Engines 01..09 (see NAV below)

---

## 5) NAV (RAW LINKS)
### Templates
- TEMPLATE: ENGINE
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/11_MUSIC_FACTORY_ENGINES/00__TEMPLATE__ENGINE__MUSIC_FACTORY_ENGINES.md
- TEMPLATE: README
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/11_MUSIC_FACTORY_ENGINES/00__TEMPLATE__README__MUSIC_FACTORY_ENGINES.md

### Engines
01 — Group Foundation Engine  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/11_MUSIC_FACTORY_ENGINES/01__GROUP_FOUNDATION_ENG.md

02 — Artist Factory Engine  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/11_MUSIC_FACTORY_ENGINES/02__ARTIST_FACTORY_ENG.md

03 — Album Blueprint Engine  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/11_MUSIC_FACTORY_ENGINES/03__ALBUM_BLUEPRINT_ENG.md

04 — Track Factory Engine  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/11_MUSIC_FACTORY_ENGINES/04__TRACK_FACTORY_ENG.md

05 — Duration Strategy Engine  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/11_MUSIC_FACTORY_ENGINES/05__DURATION_STRATEGY_ENG.md

06 — Release Pack Engine  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/11_MUSIC_FACTORY_ENGINES/06__RELEASE_PACK_ENG.md

07 — Catalog Collision Engine  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/11_MUSIC_FACTORY_ENGINES/07__CATALOG_COLLISION_ENG.md

08 — Novelty Injection Engine  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/11_MUSIC_FACTORY_ENGINES/08__NOVELTY_INJECTION_ENG.md

09 — Take Log Engine  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/11_MUSIC_FACTORY_ENGINES/09__TAKE_LOG_ENG.md

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED

--- END.
