# CATALOG MEMORY — CTL
FILE: 03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/07__CATALOG_MEMORY_CTL.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: CONTROLLERS (CTL)
CTL_REALM: 10_MUSIC_CONTROLLERS
DOC_TYPE: CONTROLLER
CTL_TYPE: CATALOG_MEMORY
LEVEL: L3
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.CTL.MUS.CATALOG_MEMORY.001
OWNER: SYSTEM
ROLE: Defines what must be logged into catalog memory after each take/release,
how memory is structured (scopes), what tokens are stored (hooks/voices/palettes/PD fragments),
and how other entities must read memory to avoid repetition and collisions.

CHANGE_NOTE:
- DATE: 2026-01-12
- TYPE: MAJOR
- SUMMARY: "Created Catalog Memory CTL: scopes, token schema, logging requirements, and read rules for collision avoidance."
- REASON: "Main failure mode: repeating the same vocals/hooks/patterns because the system has no usable memory."
- IMPACT: "Repeat-safe scaling, stronger differentiation, better portfolio planning."
- CHANGE_ID: UE.CHG.2026-01-12.CTL.CATALOG.MEMORY.001

---

## 0) PURPOSE (LAW)
Catalog Memory is the factory’s “anti-repeat brain”.
It defines:
- what gets logged after takes and releases
- how to query memory by scope
- what tokens represent identity (hooks, vocals, palettes, PD fragments)
- how to use memory to prevent collisions

---

## 1) MEMORY SCOPES (MANDATORY)
Memory must support these scopes:

- SCOPE.GROUP (default)
- SCOPE.ALBUM
- SCOPE.GLOBAL (optional)

Rules:
- Album production must read/write SCOPE.ALBUM.
- Group production must read/write SCOPE.GROUP.
- Global is used only when scaling across many groups.

---

## 2) MEMORY RECORD TYPES (WHAT WE STORE)
Memory records are token-based, not full content.

### M1 TAKE_RECORD
Logged for each generated take batch:
- take ids
- prompt snapshot id
- quick outcome (PASS/WARN/FAIL)
- notable tokens (see Section 3)

### M2 WINNER_RECORD
Logged when a take becomes a winner (PASS):
- winner take id
- frozen prompt pack id
- hook stack tokens
- vocal identity tokens
- palette/groove tokens
- collision check result

### M3 RELEASE_RECORD
Logged when released:
- platform titles pack id
- variant manifest
- metadata id
- final collision status

### M4 PD_USAGE_RECORD (if PD lyrics used)
- PD eligibility report id
- fragment tokens used
- mosaic stitch token
- collision report id

---

## 3) TOKEN SCHEMA (STANDARD)
Tokens are compact strings. At minimum store:

### T1 HOOK TOKENS
- hook grammar type (chant/slogan/motif)
- Q-line token (if lyrical)
- repetition geometry token
- signature tag token (S-tag)

### T2 VOCAL TOKENS
- vocalist role id(s)
- timbre/character tags (coarse)
- duet pattern token (if used)

### T3 PALETTE TOKENS
- instrumentation palette family token
- mix aesthetic token (coarse)

### T4 GROOVE/TEMPO TOKENS
- tempo band token
- groove feel token

### T5 GENRE/FUSION TOKENS
- primary genre family token
- fusion recipe token (if any)

### T6 PD FRAGMENT TOKENS (PD mode only)
- fragment token(s)
- famous-line token (if flagged)
- mosaic stitch token

### T7 COLLISION RESULT TOKEN
- scope + similarity score + severity

---

## 4) LOGGING REQUIREMENTS (MANDATORY)
### After each production run (take batch)
Must write:
- TAKE_RECORD with tokens T1..T5 (+T6 if PD)

### After PASS (winner)
Must write:
- WINNER_RECORD (frozen snapshot)
- collision result token

### After release
Must write:
- RELEASE_RECORD (platform titles + variants)

---

## 5) READ RULES (HOW OTHERS USE MEMORY)
Entities must read memory BEFORE producing:
- Style Fingerprint (avoid repeating anchors too closely)
- Hook stack design (avoid same slogans/geometry)
- Voice distribution (avoid same voice everywhere)
- Prompt architecting (avoid same tag combos)
- PD pipeline (avoid same fragments and stitch patterns)

Minimum read windows:
- last N winners in the same scope
- last N releases in the same scope

(N is governed by the collision thresholds controller or portfolio policy.)

---

## 6) OUTPUT EXPECTATIONS (FOR ENGINES/ORC)
When an entity outputs a “collision-aware” artifact, it must include:
- scope mode used
- memory items referenced (IDs/tokens)
- avoid list tokens derived from memory

No raw full-text content is required; tokens are enough.

---

## 7) STORAGE LOCATION (OPERATIONAL)
This CTL defines schema; actual storage path is a project decision.
Default target for produced records:
- `05_PROJECTS//CATALOG_MEMORY/`

---

## 8) REFERENCES (RAW)
Written by:
- Take Log ENG  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/11_MUSIC_FACTORY_ENGINES/09__TAKE_LOG_ENG.md
- Track TEST → DOC Gate ORC  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/03__TRACK_TEST_DOC_GATE_ORC.md

Read by:
- Catalog Collision ENG  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/11_MUSIC_FACTORY_ENGINES/07__CATALOG_COLLISION_ENG.md
- Portfolio Planner ORC  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/05__PORTFOLIO_PLANNER_ORC.md

Policy aligned with:
- Fingerprint Collision Thresholds CTL  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/06__FINGERPRINT_COLLISION_THRESHOLDS_CTL.md

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED

--- END.
