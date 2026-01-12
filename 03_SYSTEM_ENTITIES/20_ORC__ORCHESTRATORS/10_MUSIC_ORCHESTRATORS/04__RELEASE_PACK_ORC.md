# Release Pack Orchestrator — ORC
FILE: 03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/04__RELEASE_PACK_ORC.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ORCHESTRATORS (ORC)
ORC_FAMILY: 10_MUSIC_ORCHESTRATORS
DOC_TYPE: ORCHESTRATOR
ORC_TYPE: MUSIC_RELEASE_PIPELINE
LEVEL: L3
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.ORC.MUS.RELEASE_PACK.001
OWNER: SYSTEM
ROLE: Orchestrates packaging of PASS-approved tracks/albums into a Release Pack:
variant planning, naming and platform titles, metadata + credits policy, QA/VAL snapshot,
and final upload-ready checklist.

Uses Release Pack ENG as pack builder and Naming engines for titles.

CHANGE_NOTE:
- DATE: 2026-01-12
- TYPE: MAJOR
- SUMMARY: "Created Release Pack orchestrator: required inputs from TEST→DOC gate, naming pipeline integration, and final readiness checks."
- REASON: "Release packaging must be deterministic and compliant; titles/variants/metadata must be consistent."
- IMPACT: "Cleaner releases + fewer platform issues + faster publishing."
- CHANGE_ID: UE.CHG.2026-01-12.ORC.MUS.RELEASE_PACK.001

---

## 0) PURPOSE (LAW)
Turn PASS-approved track(s) into an upload-ready Release Pack by:
- choosing variants (per policy)
- producing titles per platform (collision-safe)
- producing metadata + credits note (policy)
- producing readiness snapshot and export checklist

---

## 1) INPUTS (CONSUMES)
Required (from TEST→DOC gate):
- DOC_PACK:
  - Track Card final
  - Winner take record
  - Prompt pack frozen
  - QA/VAL snapshot
  - memory tokens update note

Optional:
- Album context (if album release)
- Desired release date/window
- Series markers (if series)

---

## 2) OUTPUTS (PRODUCES)
- Release Pack (track or album):
  - Release Passport
  - Variant Manifest
  - Platform Titles Pack
  - Metadata Sheet
  - Credits & Rights Note
  - QA/VAL Snapshot
  - Export Checklist

---

## 3) REQUIRED ENTITIES (RAW LINKS)

### Release packaging ENG
- Release Pack ENG  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/11_MUSIC_FACTORY_ENGINES/06__RELEASE_PACK_ENG.md

### Controllers (policy)
- Release Variants CTL  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/04__RELEASE_VARIANTS_CTL.md
- Credits/Metadata Policy CTL  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/13__CREDITS_METADATA_POLICY_CTL.md

### Naming engines (titles)
- Naming Brief ENG  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/14_NAMING_IDENTITY_ENGINES/01__NAMING_BRIEF_ENG.md
- Naming Generation ENG  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/14_NAMING_IDENTITY_ENGINES/02__NAMING_GENERATION_ENG.md
- Naming Collision ENG  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/14_NAMING_IDENTITY_ENGINES/03__NAMING_COLLISION_ENG.md
- Platform Format Titles ENG  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/14_NAMING_IDENTITY_ENGINES/04__PLATFORM_FORMAT_TITLES_ENG.md
- Series Naming ENG (optional)  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/14_NAMING_IDENTITY_ENGINES/05__SERIES_NAMING_ENG.md

### Validators
- Release Pack Ready VAL  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/06__RELEASE_PACK_READY_VAL.md
- Naming Collision VAL  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/07__NAMING_COLLISION_VAL.md
- Credits/Rights VAL (if PD or policy requires)  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/09__CREDITS_RIGHTS_VAL.md

---

## 4) PIPELINE (DETERMINISTIC)

### STEP 0 — Load policy constraints
Load CTL:
- Release variants policy
- Credits/metadata policy

Output:
- RELEASE_POLICY_SNAPSHOT (short)

---

### STEP 1 — Decide variants
Using Release Variants CTL, decide:
- MAIN (required)
- SHORT_CUT (recommended if UGC-ready)
- ALT / INSTRUMENTAL / EXTENDED (optional)

Output:
- VARIANT_PLAN (manifest draft)

---

### STEP 2 — Produce naming (titles)
Run naming pipeline:
1) Naming Brief (target type = TRACK or ALBUM)
2) Naming Generation (candidates)
3) Naming Collision (scope per policy)
4) Platform Format Titles (YouTube/Streaming/Short-form)

Validate:
- Naming Collision VAL

Output:
- PLATFORM_TITLES_PACK
- SAFE_FALLBACK_TITLES

---

### STEP 3 — Credits & metadata
Using Credits/Metadata Policy:
- build metadata sheet fields required by release pack
- build credits/rights note
- if PD used: ensure PD marking exists

Validate (if required):
- Credits/Rights VAL

Output:
- METADATA_SHEET
- CREDITS_RIGHTS_NOTE

---

### STEP 4 — Build Release Pack via ENG
Run Release Pack ENG using:
- DOC_PACK
- VARIANT_PLAN
- PLATFORM_TITLES_PACK
- METADATA_SHEET
- CREDITS_RIGHTS_NOTE
- QA/VAL snapshot

Output:
- RELEASE_PACK (draft)

---

### STEP 5 — Readiness validation
Run:
- Release Pack Ready VAL

If FAIL:
- fix missing pieces (variants/titles/metadata) and rerun Step 4–5.

Output:
- RELEASE_PACK_READY (PASS/FAIL) + reasons

---

### STEP 6 — Export checklist
Emit:
- upload file list
- filename-safe strings
- per-platform notes (if any)

---

## 5) HANDOFFS (XREF)
Downstream:
- Portfolio Planner ORC (to schedule next releases)  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/05__PORTFOLIO_PLANNER_ORC.md

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED

--- END.
