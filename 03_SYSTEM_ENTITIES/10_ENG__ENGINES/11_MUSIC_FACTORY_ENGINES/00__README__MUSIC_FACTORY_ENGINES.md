# MUSIC FACTORY ENGINES — REALM (README)
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/11_MUSIC_FACTORY_ENGINES/00__README__MUSIC_FACTORY_ENGINES.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
ENGINE_FAMILY: 11_MUSIC_FACTORY_ENGINES
DOC_TYPE: README
LEVEL: L3
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.1.0
UID: UE.ENG.MUS.REALM.MUSIC_FACTORY.001
OWNER: SYSTEM
ROLE: Defines the canonical “Music Factory” pipeline: group → artists → album → track → release pack, with memory/collision control and deterministic iteration.

CHANGE_NOTE:
- DATE: 2026-01-11
- TYPE: MINOR
- SUMMARY: "Added PIPELINE ORDER (LAW) + clarified roles of each engine; wired to Trend/Genre + Poet PD + CTL/VAL/QA."
- REASON: "Operational music production must be deterministic and compatible with platform generation."
- IMPACT: "Fewer repeats, stronger identity, cleaner iteration, better release readiness."
- CHANGE_ID: UE.CHG.2026-01-11.ENG.MUS.REALM.MF.001

---

## 0) PURPOSE (LAW)
This REALM defines how the system **mass-produces high-quality music** with:
- stable group identity
- controlled novelty
- viral/UGC readiness
- strict memory against repeats and collisions
- prompt compatibility (Suno/Udio)

---

## 1) SCOPE (BOUNDARIES)
This family is responsible for **production flow** only:
- creating/maintaining group → album → track artifacts
- orchestrating “test → decide → document → release”
- integrating hooks/genre fusion/poet corpus via dependencies

Not responsible for:
- deep genre theory (owned by `12_TREND_GENRE_ENGINES`)
- public-domain poet filtering (owned by `13_POET_PD_CORPUS_ENGINES`)
- enforcement rules (owned by CTL/VAL/QA entities)

---

## 2) PIPELINE ORDER (LAW) — MUSIC FACTORY
This order is mandatory unless a controller explicitly overrides it.

A) GROUP FOUNDATION
- 01__GROUP_FOUNDATION_ENG.md
Output: Group Identity + Audience + Sound promise + Constraints

B) ARTIST FACTORY
- 02__ARTIST_FACTORY_ENG.md
Output: Group cast (vocalists + instrumental personas) + roles + voice diversity intent

C) ALBUM BLUEPRINT
- 03__ALBUM_BLUEPRINT_ENG.md
Output: Album concept + tracklist skeleton + arc + variation strategy

D) TRACK FACTORY (CORE)
- 04__TRACK_FACTORY_ENG.md
Output: Track brief + Hook plan + Poet excerpt plan + Prompt pack + Test takes + PASS/FAIL gate + docs (if PASS)

E) DURATION STRATEGY
- 05__DURATION_STRATEGY_ENG.md
Output: Short/Full durations per genre/audience + intro/hook timing constraints

F) RELEASE PACK
- 06__RELEASE_PACK_ENG.md
Output: Release variants + metadata + assets checklist + export notes

G) CATALOG COLLISION
- 07__CATALOG_COLLISION_ENG.md
Output: Collision checks (internal + cross-catalog) + novelty adjustments

H) NOVELTY INJECTION
- 08__NOVELTY_INJECTION_ENG.md
Output: controlled novelty moves (change only allowed anchors) without breaking fingerprint

I) TAKE LOG (MEMORY)
- 09__TAKE_LOG_ENG.md
Output: what changed, what worked, what to keep/ban next iteration

---

## 3) REQUIRED DEPENDENCY FAMILIES (XREF)
Music Factory consumes outputs from:

### Trend/Genre system (identity + hooks + prompt compatibility)
- 12_TREND_GENRE_ENGINES/*
  (genre taxonomy, fusion recipe, style fingerprint, viral blueprint, UGC map, earworm stack, prompt compiler)

### Poet PD corpus system (only public domain + “juice” extraction)
- 13_POET_PD_CORPUS_ENGINES/*
  (PD filter, fit scoring, juice extractor, mosaic composer, excerpt collision guard)

### Controllers / Validators / QA (enforcement)
- CTL: duration policy, prompt contract, negative spec, catalog memory, quality gates, phrasebooks
- VAL: hook timing, ugc ready, repeat guard, collision blocker, naming collision, prompt fidelity, rights/credits
- QA: scroll-stop, loop 15s, recognition 10s, mix translation, regression guard

---

## 4) OUTPUT ARTIFACTS (MINIMUM SET)
Minimum useful artifacts for a working pipeline:
- Group Card (identity + anchors + forbiddens)
- Album Blueprint (tracklist + arc)
- Track Card (brief + hooks + prompt pack + decision)
- Take Log (top takes only)
- Release Pack (variants + metadata)

Everything else is optional and added only if it increases speed/quality.

---

## 5) OPERATIONAL LAW — TEST → DOC GATE
A track is produced in two phases:
1) TEST PHASE (fast): generate takes, pick winner, decide PASS/FAIL
2) DOC PHASE (only if PASS): create full documentation pack

No wasted documentation for failed ideas.

---

## 6) FAMILY FILES (CANON)
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
