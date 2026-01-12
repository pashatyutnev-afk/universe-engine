# Track TEST → DOC Gate Orchestrator — ORC
FILE: 03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/03__TRACK_TEST_DOC_GATE_ORC.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ORCHESTRATORS (ORC)
ORC_FAMILY: 10_MUSIC_ORCHESTRATORS
DOC_TYPE: ORCHESTRATOR
ORC_TYPE: MUSIC_PIPELINE_GATE
LEVEL: L3
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.ORC.MUS.TRACK_TEST_DOC_GATE.001
OWNER: SYSTEM
ROLE: Enforces the TEST→DOC gate:
- evaluates candidate takes using VAL + QA gates,
- decides PASS/WARN/FAIL,
- only on PASS produces the documentation pack and prepares release-pack handoff.

Prevents documentation bloat and keeps factory fast.

CHANGE_NOTE:
- DATE: 2026-01-12
- TYPE: MAJOR
- SUMMARY: "Created TEST→DOC gate orchestrator: decision outcomes, required validators/QA, and doc packaging rules."
- REASON: "Docs must exist only for winners; otherwise system slows and repeats."
- IMPACT: "Clean catalog, faster iteration, higher quality."
- CHANGE_ID: UE.CHG.2026-01-12.ORC.MUS.TESTDOC.001

---

## 0) PURPOSE (LAW)
This ORC performs one job:
**decide if a track candidate is worthy of documentation + release packaging.**

Rules:
- TEST phase is cheap and fast.
- DOC phase is only for PASS winners.

---

## 1) INPUTS (CONSUMES)
Required:
- Track Pack from Album→Track ORC:
  - prompt pack used (snapshot)
  - take ids / candidate outputs
  - track card draft (intent + hook plan)
  - known risks (optional)
- Active constraints snapshot:
  - CTL quality gates (if any)
  - negative specs (context)

---

## 2) OUTPUTS (PRODUCES)
- DECISION_RECORD:
  - PASS / WARN / FAIL
  - why
  - next action

If PASS:
- DOC_PACK:
  - finalized Track Card (SoT)
  - frozen Prompt Pack
  - Winner Take Record
  - QA/VAL snapshot
  - Credits/rights note pointer (policy controlled)
- RELEASE_HANDOFF_NOTE:
  - what variants to produce
  - naming needs
  - any special platform notes

If WARN/FAIL:
- RETEST_BRIEF:
  - what to change (1–2 knobs max)
  - which validators failed
  - what to re-run

---

## 3) REQUIRED ENTITIES (RAW LINKS)

### Validators (VAL)
- Hook Timing VAL  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/01__HOOK_TIMING_VAL.md
- UGC Ready VAL  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/02__UGC_READY_VAL.md
- Repeat Guard VAL  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/03__REPEAT_GUARD_VAL.md
- PD Only VAL (if PD lyrics)  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/04__PD_ONLY_VAL.md
- Collision Blocker VAL  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/05__COLLISION_BLOCKER_VAL.md
- Prompt Fidelity VAL  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/08__PROMPT_FIDELITY_VAL.md
- Credits/Rights VAL (if needed)  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/09__CREDITS_RIGHTS_VAL.md

### QA (quick listening gates)
- Scroll Stop 5s QA  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/60_QA__QUALITY/10_MUSIC_QA/01__SCROLL_STOP_5S_QA.md
- Loop 15s QA  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/60_QA__QUALITY/10_MUSIC_QA/02__LOOP_15S_QA.md
- Recognition 10s QA  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/60_QA__QUALITY/10_MUSIC_QA/03__RECOGNITION_10S_QA.md
- Catalog Differentiation QA  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/60_QA__QUALITY/10_MUSIC_QA/07__CATALOG_DIFFERENTIATION_QA.md

### Engines used on PASS packaging
- Take Log ENG  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/11_MUSIC_FACTORY_ENGINES/09__TAKE_LOG_ENG.md
- Catalog Collision ENG (if collision flagged)  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/11_MUSIC_FACTORY_ENGINES/07__CATALOG_COLLISION_ENG.md
- Release Pack ENG (handoff target)  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/11_MUSIC_FACTORY_ENGINES/06__RELEASE_PACK_ENG.md

---

## 4) GATE LOGIC (DECISION)
This gate yields:

### PASS
- critical validators pass:
  - Hook Timing
  - Repeat Guard
  - Prompt Fidelity
  - Collision Blocker (or acceptable WARN handled)
- QA gates pass:
  - Scroll Stop 5s
  - Recognition 10s
  - Loop 15s
- If PD lyrics used:
  - PD Only passes (and any excerpt collision warnings handled upstream)

### WARN
- one non-critical validator warning OR one QA weak area
- but track is promising and fixable with 1 knob

### FAIL
- critical validator fails OR multiple QA fails
- or obvious drift/off-brand result

---

## 5) PROCEDURE (DETERMINISTIC)

### STEP 0 — Collect candidate takes
- Identify top 1–2 take(s) to evaluate.
- Ensure prompt pack snapshot is attached.

### STEP 1 — Run validators (VAL)
- Run relevant validators.
- If PD used: include PD Only and Credits/Rights checks.

### STEP 2 — Run quick QA
- Perform listening QA checks (as per QA entities).

### STEP 3 — Collision check (if not already clean)
- If warnings indicate sameness:
  - ensure Catalog Differentiation QA
  - optionally call Catalog Collision ENG

### STEP 4 — Decide PASS/WARN/FAIL
- Produce DECISION_RECORD.

### STEP 5 — If PASS: produce DOC_PACK
- finalize Track Card (SoT)
- freeze prompt pack
- write winner take record
- write QA/VAL snapshot
- write take log record (winner + tokens for memory)

### STEP 6 — If WARN/FAIL: produce RETEST_BRIEF
- specify:
  - 1–2 knobs to change
  - what to keep fixed (anchors)
  - which step to re-run in Album→Track (usually hook/prompt/intro)

---

## 6) OUTPUT SCHEMA (MANDATORY)

### DECISION_RECORD
- TRACK_UID:
- DATE:
- TOP_TAKE_ID:
- DECISION: {PASS | WARN | FAIL}
- FAILURES:
  - list of failed VAL/QA checks
- WHY:
  - 3–8 bullets
- NEXT_ACTION:
  - {DOC_AND_RELEASE | RETEST | REDESIGN_SLOT}
- RETEST_KNOBS (if WARN/FAIL):
  - list of 1–2 knobs

### DOC_PACK (PASS only)
- TRACK_CARD_FINAL
- PROMPT_PACK_FROZEN
- WINNER_TAKE_RECORD
- QA_VAL_SNAPSHOT
- MEMORY_TOKENS_UPDATE (for catalog memory)
- RELEASE_HANDOFF_NOTE

---

## 7) HANDOFFS (XREF)
If PASS:
- Release Pack ORC  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/04__RELEASE_PACK_ORC.md

If WARN/FAIL:
- back to Album→Track ORC  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/02__ALBUM_TO_TRACK_ORC.md

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED

--- END.
