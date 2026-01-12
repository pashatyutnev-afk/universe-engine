# Album → Track Orchestrator — ORC
FILE: 03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/02__ALBUM_TO_TRACK_ORC.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ORCHESTRATORS (ORC)
ORC_FAMILY: 10_MUSIC_ORCHESTRATORS
DOC_TYPE: ORCHESTRATOR
ORC_TYPE: MUSIC_PIPELINE
LEVEL: L3
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.ORC.MUS.ALBUM_TO_TRACK.001
OWNER: SYSTEM
ROLE: Deterministic pipeline that executes an Album Blueprint slot-by-slot into Track Packs:
builds hook/ugc plans, compiles prompts, runs take batches, and produces PASS/FAIL-ready candidates.

Delegates the actual generation logic to Track Factory and Trend/Genre engines.

CHANGE_NOTE:
- DATE: 2026-01-12
- TYPE: MAJOR
- SUMMARY: "Created Album→Track orchestrator: slot execution order, required artifacts, and minimal repeat-safe iteration loop."
- REASON: "Album planning must translate into repeatable track execution without drift."
- IMPACT: "Faster production, fewer repeats, cleaner handoff to TEST→DOC gate."
- CHANGE_ID: UE.CHG.2026-01-12.ORC.MUS.A2T.001

---

## 0) PURPOSE (LAW)
Turn an Album Blueprint into executable track production runs by:
- selecting slot(s) to produce
- running the required engines in the correct order
- outputting a Track Pack per slot (ready for TEST→DOC gate ORC)

---

## 1) INPUTS (CONSUMES)
Required:
- Group Pack:
  - Group DNA Spec
  - Artist Roster Spec
  - Style Fingerprint Pack
  - Constraints Pack + Negative Specs
- Album Pack:
  - Album Blueprint (SoT)
  - Tracklist Skeleton (slots)
  - Track Role Map + duration mix
- Slot selection:
  - SLOT_ID list (e.g., 01, 02, 03) or “next slot”

Optional:
- PD lyric mode flag per slot: {PD_ONLY | instrumental | open}
- collision strictness level (group-only vs global)

---

## 2) OUTPUTS (PRODUCES)
Per slot (Track Pack):
- Track Intent Brief (slot requirements)
- Hook Stack + Viral Hook Blueprint + UGC Moment Map
- Prompt Pack (Suno mandatory, Udio optional)
- Test Batch Plan (N takes + knobs)
- Take Log draft entry (IDs + short notes)
- Pre-check notes (collision risk intent)

---

## 3) REQUIRED ENTITIES (RAW LINKS)

### Execution engine (core)
- Track Factory ENG  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/11_MUSIC_FACTORY_ENGINES/04__TRACK_FACTORY_ENG.md
- Duration Strategy ENG  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/11_MUSIC_FACTORY_ENGINES/05__DURATION_STRATEGY_ENG.md

### Trend/Genre (hook + prompt)
- Earworm Hook Stack  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/12_TREND_GENRE_ENGINES/06__EARWORM_HOOK_STACK_ENG.md
- Viral Hook Blueprint  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/12_TREND_GENRE_ENGINES/04__VIRAL_HOOK_BLUEPRINT_ENG.md
- UGC Moment Map  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/12_TREND_GENRE_ENGINES/05__UGC_MOMENT_MAP_ENG.md
- Prompt Compiler  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/12_TREND_GENRE_ENGINES/07__PROMPT_COMPILER_ENG.md

### PD corpus (optional lyrical mode)
- Poet Pack ORC (if PD-only)  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/06__POET_PACK_ORC.md

### Controllers
- Prompt Contract  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/01__PROMPT_CONTRACT_CTL.md
- Duration Policy  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/03__DURATION_POLICY_CTL.md
- Negative Spec Library  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/12__NEGATIVE_SPEC_LIBRARY_CTL.md
- Catalog Memory  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/07__CATALOG_MEMORY_CTL.md

---

## 4) PIPELINE (DETERMINISTIC PER SLOT)

### STEP 0 — Select slot
Pick SLOT_ID(s) from Album Blueprint.
If none specified: pick next “highest priority” slot (opener or lead single).

Output:
- SLOT_EXEC_PLAN (slot list + order)

---

### STEP 1 — Build Track Intent Brief
From Album Blueprint slot:
- role type
- duration mode (short/full)
- required hook type / UGC intent
- forbidden overlaps (album-internal)

Output:
- TRACK_INTENT_BRIEF

---

### STEP 2 — PD input (optional)
If slot lyrical mode is PD_ONLY:
- run Poet Pack ORC to produce:
  - shortlist + juice + mosaic draft pointers
Else:
- set lyrics mode to instrumental or open per plan.

Output:
- LYRICS_INPUT_PACK (optional)

---

### STEP 3 — Hook planning
Run:
- Earworm Hook Stack (H1/H2/S-tag/Q-line if lyrical)
- UGC Moment Map (clip windows)
- Viral Hook Blueprint (timing + geometry)

Output:
- HOOK_PLAN_PACK

---

### STEP 4 — Prompt compilation
Run:
- Prompt Compiler → produce:
  - Suno pack (mandatory)
  - optional Udio pack
  - variants: short/full/alt intro (if needed)

Output:
- PROMPT_PACK

---

### STEP 5 — Execution via Track Factory
Run Track Factory with:
- group identity + cast + fingerprint
- slot brief + hook plan + prompt pack
- duration strategy/policy + negative specs
- optional PD lyric mosaic draft

Output:
- TEST_BATCH_PLAN
- TAKE_LOG_DRAFT (IDs only)
- TRACK_PACK (candidate + metadata placeholders)

---

### STEP 6 — Pre-handoff note to TEST→DOC gate
Package the slot output into:
- TRACK_PACK_READY_FOR_GATE
including:
- prompt pack snapshot
- top take ids (if any)
- known risks (if any)

---

## 5) LOOP RULE (ITERATION)
If Track Factory returns FAIL:
- update only 1–2 knobs (hook grammar / intro stamp / palette)
- re-run Step 3–5
- stop after policy max iterations (set elsewhere)

---

## 6) HANDOFFS (XREF)
NEXT ORC:
- Track Test → Doc Gate ORC  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/03__TRACK_TEST_DOC_GATE_ORC.md

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED

--- END.
