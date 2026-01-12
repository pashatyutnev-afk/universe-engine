# MUSIC ORCHESTRATORS — REALM (README)
FILE: 03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/00__README__MUSIC_ORCHESTRATORS.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ORCHESTRATORS (ORC)
ORC_FAMILY: 10_MUSIC_ORCHESTRATORS
DOC_TYPE: README
README_TYPE: REALM
LEVEL: L3
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.ORC.REALM.MUSIC.001
OWNER: SYSTEM
ROLE: Operational entrypoint for music production pipelines (group → album → track → test/doc gate → release pack),
plus portfolio planning and poet pack preparation.

CHANGE_NOTE:
- DATE: 2026-01-12
- TYPE: MAJOR
- SUMMARY: "Created missing Music Orchestrators realm README: scope, pipeline order, and RAW-only navigation."
- REASON: "ORC layer must provide deterministic execution order across ENG/CTL/VAL/QA."
- IMPACT: "Stable production flow; less chaos; faster iteration."
- CHANGE_ID: UE.CHG.2026-01-12.ORC.REALM.MUSIC.001

---

## 0) PURPOSE (LAW)
This realm defines “how we run the factory”:
- what runs first / second / third
- what artifacts are expected at each step
- where gates happen (TEST→DOC)
- when we package releases and plan portfolio

ORC does not invent creative content — it orchestrates engines/controllers/validators.

---

## 1) SCOPE & BOUNDARIES

### In scope
- Sequencing Music Factory engines (11_*) and Trend/Genre engines (12_*)
- Calling PD corpus pipeline (13_*) when lyrics use PD-only mode
- Calling naming pipeline (14_*) for titles
- Enforcing gates via CTL/VAL/QA references

### Out of scope
- Writing engines themselves
- Policy definitions (CTL ownership)
- Validator logic (VAL ownership)
- QA test design (QA ownership)

---

## 2) PIPELINE ORDER (LAW) — MUSIC FACTORY EXECUTION
1) GROUP → ALBUM  
2) ALBUM → TRACK  
3) TRACK TEST → DOC GATE  
4) RELEASE PACK  
5) PORTFOLIO PLANNER  
6) POET PACK

Notes:
- 03 is mandatory: docs only for PASS winners.
- 06 is used when PD corpus is needed as an input pack for track generation.

---

## 3) OUTPUT ARTIFACTS (MINIMUM)
- Group Pack (identity + cast + fingerprint pointers)
- Album Pack (blueprint + slot briefs)
- Track Pack (prompt pack + test batch + PASS/FAIL)
- Doc Pack (only if PASS)
- Release Pack (variants + titles + metadata + snapshot)
- Portfolio Plan (what to produce next)
- Poet Pack (PD shortlist + juice + mosaic draft pointers)

---

## 4) NAV (RAW LINKS)

01 — Group to Album ORC  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/01__GROUP_TO_ALBUM_ORC.md

02 — Album to Track ORC  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/02__ALBUM_TO_TRACK_ORC.md

03 — Track Test Doc Gate ORC  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/03__TRACK_TEST_DOC_GATE_ORC.md

04 — Release Pack ORC  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/04__RELEASE_PACK_ORC.md

05 — Portfolio Planner ORC  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/05__PORTFOLIO_PLANNER_ORC.md

06 — Poet Pack ORC  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/06__POET_PACK_ORC.md

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED

--- END.
