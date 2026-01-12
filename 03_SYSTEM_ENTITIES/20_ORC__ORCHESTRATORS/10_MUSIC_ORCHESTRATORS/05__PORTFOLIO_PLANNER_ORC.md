# Portfolio Planner Orchestrator — ORC
FILE: 03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/05__PORTFOLIO_PLANNER_ORC.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ORCHESTRATORS (ORC)
ORC_FAMILY: 10_MUSIC_ORCHESTRATORS
DOC_TYPE: ORCHESTRATOR
ORC_TYPE: MUSIC_PORTFOLIO_PLANNING
LEVEL: L3
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.ORC.MUS.PORTFOLIO_PLANNER.001
OWNER: SYSTEM
ROLE: Plans what to produce next across groups/albums/tracks based on:
catalog memory, collision risks, audience segments, and release cadence.
Outputs a prioritized production queue for the Music Factory.

CHANGE_NOTE:
- DATE: 2026-01-12
- TYPE: MAJOR
- SUMMARY: "Created Portfolio Planner ORC: priority rules, inputs from take logs/releases, and queue output schema."
- REASON: "Without portfolio planning, production repeats itself and wastes effort."
- IMPACT: "Clear roadmap, controlled novelty, stable release cadence."
- CHANGE_ID: UE.CHG.2026-01-12.ORC.MUS.PORTFOLIO.001

---

## 0) PURPOSE (LAW)
Answer:
**“Что делаем дальше и в каком порядке?”**

This ORC produces a deterministic **Production Queue**:
- next groups to activate
- next album slots to execute
- where to inject novelty
- what to avoid due to collisions
- release cadence planning

---

## 1) INPUTS (CONSUMES)
- Catalog Memory snapshot (what exists)
- Recent Release Packs (what shipped)
- Take Logs (what worked/failed)
- Audience segment goals
- Trend/genre coverage goals (optional)
- Capacity constraints (how many tracks per cycle)

---

## 2) OUTPUTS (PRODUCES)
- PORTFOLIO_PLAN (PP):
  - prioritized queue of production tasks
  - per task: objective + required ORC step + constraints
- NOVELTY_MAP:
  - which groups need novelty injection vs stability
- COLLISION_AVOID_LIST:
  - tokens to avoid (hooks/palettes/PD fragments)

---

## 3) REQUIRED ENTITIES (RAW LINKS)
- Catalog Memory CTL  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/07__CATALOG_MEMORY_CTL.md
- Fingerprint Collision Thresholds CTL  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/06__FINGERPRINT_COLLISION_THRESHOLDS_CTL.md
- Take Log ENG  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/11_MUSIC_FACTORY_ENGINES/09__TAKE_LOG_ENG.md
- Catalog Collision ENG  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/11_MUSIC_FACTORY_ENGINES/07__CATALOG_COLLISION_ENG.md
- Novelty Injection ENG  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/11_MUSIC_FACTORY_ENGINES/08__NOVELTY_INJECTION_ENG.md

---

## 4) PRIORITY RULES (DETERMINISTIC)
Rank tasks using these dimensions:

P1 RELEASE_CADENCE (weight high)
- ensure steady cadence; don’t starve releases

P2 HIT_SIGNAL (weight high)
- if take logs show “liked/develop”, prioritize finishing and releasing

P3 COLLISION_RISK (weight high)
- if collisions increasing, prioritize novelty injection or new palette

P4 COVERAGE_BALANCE (weight medium)
- avoid all tracks being same tempo/genre/energy

P5 PIPELINE_BLOCKERS (weight medium)
- fix missing docs/packs that block next steps

---

## 5) PROCEDURE (DETERMINISTIC)
1) Load catalog memory + last releases + recent take logs.
2) Identify:
   - READY_TO_RELEASE candidates (PASS winners not packaged)
   - IN_PROGRESS candidates (liked/develop)
   - STALE lanes (too repetitive, collision heavy)
3) For each group:
   - compute stability vs novelty need
   - propose next slot to execute
4) Build queue:
   - top: package releases and ship
   - then: finish in-progress winners
   - then: generate new tracks for highest value slots (opener/single)
5) Attach constraints to each task:
   - avoid tokens
   - required knobs
   - scope mode for collision checks
6) Output PP + novelty map.

---

## 6) OUTPUT SCHEMA (MANDATORY)

### PORTFOLIO_PLAN (PP)
- DATE:
- CAPACITY:
- QUEUE (ranked):
  - rank:
    TASK_ID:
    TARGET: (group/album/track/slot)
    ORC_STEP: (G2A | A2T | TESTDOC | RELEASE_PACK | POET_PACK)
    OBJECTIVE:
    CONSTRAINTS:
      - avoid_tokens:
      - required_anchors:
      - novelty_knobs (optional):
    WHY_THIS_PRIORITY:

### NOVELTY_MAP
- GROUP_UID:
  - mode: {STABLE | LIGHT_NOVELTY | HEAVY_NOVELTY}
  - recommended knobs:

### COLLISION_AVOID_LIST
- tokens (compact list)

---

## 7) HANDOFFS (XREF)
Feeds into:
- `10_MUSIC_ORCHESTRATORS/01__GROUP_TO_ALBUM_ORC.md`
- `10_MUSIC_ORCHESTRATORS/02__ALBUM_TO_TRACK_ORC.md`
- `10_MUSIC_ORCHESTRATORS/04__RELEASE_PACK_ORC.md`
- `10_MUSIC_ORCHESTRATORS/06__POET_PACK_ORC.md`

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED

--- END.
