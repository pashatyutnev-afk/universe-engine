# Poet Pack Orchestrator — ORC
FILE: 03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/06__POET_PACK_ORC.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ORCHESTRATORS (ORC)
ORC_FAMILY: 10_MUSIC_ORCHESTRATORS
DOC_TYPE: ORCHESTRATOR
ORC_TYPE: PD_LYRICS_PIPELINE
LEVEL: L3
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.ORC.MUS.POET_PACK.001
OWNER: SYSTEM
ROLE: Orchestrates the PD-only lyric pipeline to produce a Poet Pack for a specific track:
PD eligibility → fit scoring → juice extraction → mosaic composition → excerpt collision guard.

Outputs a compact pack used by Track Factory / Prompt Compiler without dumping full poems.

CHANGE_NOTE:
- DATE: 2026-01-12
- TYPE: MAJOR
- SUMMARY: "Created Poet Pack ORC: deterministic PD pipeline and output pack schema for Track Factory."
- REASON: "Lyrics must be PD-safe and repeat-safe; orchestration is required."
- IMPACT: "Cleaner PD workflow + stronger hook-ready lyrics + less repetition."
- CHANGE_ID: UE.CHG.2026-01-12.ORC.MUS.POET_PACK.001

---

## 0) PURPOSE (LAW)
Produce a **POET PACK** for one target track:
- PD eligibility verified
- best-fit candidates ranked
- strongest fragments extracted (“juice”)
- coherent mosaic draft built
- excerpt collision checked (avoid overuse)

---

## 1) INPUTS (CONSUMES)
Required:
- TRACK_INTENT_BRIEF (theme/mood/role)
- Style Fingerprint anchors/forbiddens
- Hook Stack needs (Q-line requirement)
- UGC Moment Map (clip windows need)
- Duration mode (short/full)
- Candidate PD corpus references (if provided) OR “choose from allowed PD pool”

Optional:
- scope mode for collisions (group/album/global)

---

## 2) OUTPUTS (PRODUCES)
- POET_PACK (PPD):
  - PD Eligibility Report (PER)
  - Fit Ranking (FRANK)
  - Juice Pack (JP)
  - Mosaic Draft (MD)
  - Excerpt Collision Report (ECR)
  - Tokens update (for memory)
  - Notes for Track Factory (what to paste / what to avoid)

---

## 3) REQUIRED ENTITIES (RAW LINKS)

### PD corpus engines
- PD Filter ENG  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/13_POET_PD_CORPUS_ENGINES/01__PD_FILTER_ENG.md
- Poem Fit Scoring ENG  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/13_POET_PD_CORPUS_ENGINES/02__POEM_FIT_SCORING_ENG.md
- Juice Extractor ENG  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/13_POET_PD_CORPUS_ENGINES/03__JUICE_EXTRACTOR_ENG.md
- Mosaic Composer ENG  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/13_POET_PD_CORPUS_ENGINES/04__MOSAIC_COMPOSER_ENG.md
- Excerpt Collision Guard ENG  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/13_POET_PD_CORPUS_ENGINES/05__EXCERPT_COLLISION_ENG.md

### Controllers / validators
- Poet PD Policy CTL  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/05__POET_PD_POLICY_CTL.md
- Catalog Memory CTL  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/07__CATALOG_MEMORY_CTL.md
- PD Only VAL  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/04__PD_ONLY_VAL.md

---

## 4) PIPELINE (DETERMINISTIC)

### STEP 0 — Load PD policy + scope
- Load Poet PD Policy CTL
- Select collision scope: GROUP default; ALBUM/GLOBAL optional
Output:
- PD_POLICY_SNAPSHOT + SCOPE_MODE

---

### STEP 1 — PD eligibility (hard gate)
Run PD Filter:
- candidates → PASS/FAIL/UNCERTAIN
Output:
- PD_ELIGIBILITY_REPORT (PER)
- ALLOWED_CORPUS_SUBSET (ACS)

STOP CONDITION:
- If no candidates PASS → return “REQUEST_METADATA / PICK_NEW_PD_SOURCE”.

---

### STEP 2 — Fit scoring
Run Poem Fit Scoring using:
- ACS + Track Intent + Fingerprint + Hook/UGC needs
Output:
- FIT_RANKING (FRANK) + TOP_K shortlist

---

### STEP 3 — Juice extraction
Run Juice Extractor on top candidates:
Output:
- JUICE_PACK (JP) + tokens

---

### STEP 4 — Mosaic composition
Run Mosaic Composer using:
- Juice pack + timing/hook needs
Output:
- MOSAIC_DRAFT (MD) + mosaic map + used tokens

---

### STEP 5 — Excerpt collision guard (final gate)
Run Excerpt Collision Guard on:
- used tokens + stitch token
Output:
- EXCERPT_COLLISION_REPORT (ECR)

Decision:
- PASS: poet pack approved
- WARN: substitute fragments and re-run Step 4–5
- BLOCK: return to Step 2 (pick new candidates)

---

### STEP 6 — Package Poet Pack
Emit:
- POET_PACK (PPD) with pointers and “paste-ready mosaic lyric” section labels

---

## 5) OUTPUT SCHEMA (MANDATORY)

### POET_PACK (PPD)
- TRACK_UID:
- DATE:
- SCOPE_MODE:
- PD_POLICY_SNAPSHOT:
- PER:
- FRANK:
- JP:
- MD:
- ECR:
- TOKENS_UPDATE:
- TRACK_FACTORY_NOTES:
  - what to paste (mosaic draft)
  - what to avoid (blocked tokens)
  - where Q-line is

---

## 6) HANDOFFS (XREF)
Used by:
- Album → Track ORC  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/02__ALBUM_TO_TRACK_ORC.md
- Track Factory ENG  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/11_MUSIC_FACTORY_ENGINES/04__TRACK_FACTORY_ENG.md

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED

--- END.
