# Group → Album Orchestrator — ORC
FILE: 03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/01__GROUP_TO_ALBUM_ORC.md

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
UID: UE.ORC.MUS.GROUP_TO_ALBUM.001
OWNER: SYSTEM
ROLE: Deterministic pipeline from “group idea” to “album blueprint”:
locks identity (Group DNA + cast + fingerprint), then produces album blueprint (track slots + arc),
and optionally creates naming brief + candidates + collision-safe options.

CHANGE_NOTE:
- DATE: 2026-01-12
- TYPE: MAJOR
- SUMMARY: "Created Group→Album orchestrator: step order, required artifacts, and enforcement hooks."
- REASON: "Music factory needs deterministic orchestration before track generation."
- IMPACT: "Stable identity + clean album planning; fewer collisions and repeats."
- CHANGE_ID: UE.CHG.2026-01-12.ORC.MUS.G2A.001

---

## 0) PURPOSE (LAW)
Run the minimum deterministic steps to produce:
- Group Pack (identity + cast + fingerprint + constraints)
- Album Pack (blueprint + slot briefs)
so that Album→Track and Track Factory can execute without drift.

---

## 1) INPUTS (CONSUMES)
Minimum inputs:
- Group concept (1–3 lines)
- Target audience segment (or “unknown”)
- Release intent: {viral/ugc-first | album-first}
- Language mode (default RU)

Optional inputs:
- desired primary genre family
- “avoid list” (things the group must never sound like)
- PD lyrics intent: {PD_ONLY | instrumental | open} (policy decides)

---

## 2) OUTPUTS (PRODUCES)
### Group Pack (G-PACK)
- Group DNA Spec
- Artist Roster Spec
- Style Fingerprint Pack
- Group Constraints Pack (negative specs + forbiddens)
- Group Take Log entry

### Album Pack (A-PACK)
- Album Blueprint (single SoT)
- Tracklist Skeleton (slots 01..N)
- Track Role Map + duration mix guidance
- Album collision guard notes (internal)

Optional:
- Naming Brief + name candidates + collision-safe shortlist (group/album)

---

## 3) REQUIRED ENTITIES (RAW LINKS)

### Music Factory ENG
- Group Foundation ENG  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/11_MUSIC_FACTORY_ENGINES/01__GROUP_FOUNDATION_ENG.md
- Artist Factory ENG  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/11_MUSIC_FACTORY_ENGINES/02__ARTIST_FACTORY_ENG.md
- Album Blueprint ENG  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/11_MUSIC_FACTORY_ENGINES/03__ALBUM_BLUEPRINT_ENG.md

### Trend/Genre ENG (identity & prompt compatibility)
- Genre Taxonomy  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/12_TREND_GENRE_ENGINES/01__GENRE_TAXONOMY_ENG.md
- Fusion Recipe (optional)  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/12_TREND_GENRE_ENGINES/02__FUSION_RECIPE_ENG.md
- Style Fingerprint  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/12_TREND_GENRE_ENGINES/03__STYLE_FINGERPRINT_ENG.md

### Controllers (CTL) used as constraints
- Prompt Contract  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/01__PROMPT_CONTRACT_CTL.md
- UGC Viral Ruleset  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/02__UGC_VIRAL_RULESET_CTL.md
- Duration Policy  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/03__DURATION_POLICY_CTL.md
- Negative Spec Library  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/12__NEGATIVE_SPEC_LIBRARY_CTL.md
- Catalog Memory  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/07__CATALOG_MEMORY_CTL.md
- Audience Segments  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/08__AUDIENCE_SEGMENTS_CTL.md

### Validators / QA (group-level checks)
- Voice Diversity VAL  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/10__VOICE_DIVERSITY_VAL.md
- Naming Collision VAL (optional naming path)  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/07__NAMING_COLLISION_VAL.md
- Catalog Differentiation QA  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/60_QA__QUALITY/10_MUSIC_QA/07__CATALOG_DIFFERENTIATION_QA.md

---

## 4) PIPELINE (DETERMINISTIC STEPS)

### STEP 0 — Load constraints (CTL snapshot)
Load and lock these constraints for the run:
- Prompt Contract CTL
- UGC Viral Ruleset CTL
- Duration Policy CTL
- Negative Spec Library CTL
- Catalog Memory CTL
- Audience Segments CTL (if provided)

Output:
- CONSTRAINTS_SNAPSHOT (short list of active rules)

STOP CONDITION:
- If no audience segment is provided, choose a default segment from CTL and record it.

---

### STEP 1 — Genre selection (Trend/Genre)
Run:
- Genre Taxonomy ENG → choose primary family (A)
- Fusion Recipe ENG (optional) → only if novelty is required at group identity level

Output:
- GENRE_SPEC (A) (+ FUSION_SPEC optional)

---

### STEP 2 — Style Fingerprint (identity lock)
Run:
- Style Fingerprint ENG using:
  - group concept + audience + genre A (+ fusion)
  - catalog memory (avoid collisions)

Output:
- STYLE_FINGERPRINT_PACK (anchors/variables/forbiddens + platform encoding)

---

### STEP 3 — Group Foundation (Group DNA)
Run:
- Group Foundation ENG
Inputs include:
- audience segment
- UGC ruleset
- prompt contract
- catalog memory
- negative spec library
- naming brief dependency (if needed later)

Output:
- GROUP_DNA_SPEC
- GROUP_CONSTRAINTS_PACK
- GROUP_TAKE_LOG_ENTRY

---

### STEP 4 — Artist Factory (cast roster)
Run:
- Artist Factory ENG using Group DNA + fingerprint
Then validate:
- Voice Diversity VAL

Output:
- ARTIST_ROSTER_SPEC
- PERFORMER_CONTRACTS_PACK
- ROLE_BOUNDARIES_MATRIX
- VOICE_DIVERSITY_PASS/FAIL note

STOP CONDITION:
- If voice diversity fails → return to Artist Factory step with required mutations.

---

### STEP 5 — Album Blueprint (album plan)
Run:
- Album Blueprint ENG using:
  - Group DNA + cast
  - genre A (+ fusion)
  - fingerprint anchors
  - duration policy guidance (distribution short/full)

Output:
- ALBUM_BLUEPRINT (SoT)
- TRACKLIST_SKELETON (slots)
- TRACK_ROLE_MAP + duration mix
- ALBUM_INTERNAL_COLLISION_NOTES

---

### STEP 6 — Optional naming path (group/album)
If the production intends to release/publish under titles now:
Run naming family (14_NAMING_IDENTITY_ENGINES):
- Naming Brief → Naming Generation → Naming Collision → Platform Format Titles
Validate:
- Naming Collision VAL

Output:
- SAFE_GROUP_NAME options
- SAFE_ALBUM_NAME options
- PLATFORM_TITLES_PACK (if needed)

---

### STEP 7 — Package outputs
Emit:
- G-PACK + A-PACK
- a minimal handoff note for Album→Track ORC (what slot to start with first)

---

## 5) HANDOFFS (XREF)
NEXT ORC:
- Album → Track ORC  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/02__ALBUM_TO_TRACK_ORC.md

DOWNSTREAM:
- Track Factory ENG (execution per slot)  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/11_MUSIC_FACTORY_ENGINES/04__TRACK_FACTORY_ENG.md

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED

--- END.
