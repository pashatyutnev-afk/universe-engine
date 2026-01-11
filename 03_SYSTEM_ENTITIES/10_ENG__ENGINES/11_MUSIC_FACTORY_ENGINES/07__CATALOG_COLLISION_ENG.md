# Catalog Collision Engine — ENGINE
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/11_MUSIC_FACTORY_ENGINES/07__CATALOG_COLLISION_ENG.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
ENGINE_FAMILY: 11_MUSIC_FACTORY_ENGINES
DOC_TYPE: ENGINE
ENGINE_TYPE: MUSIC_FACTORY
LEVEL: L3
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.ENG.MF.CATALOG_COLLISION.001
OWNER: SYSTEM
ROLE: Prevents internal repetition by detecting collisions across catalog: style fingerprint, hook grammar, intro signature, lyric fragments, and naming.

CHANGE_NOTE:
- DATE: 2026-01-11
- TYPE: MAJOR
- SUMMARY: "Defined Catalog Collision Engine: collision vectors, thresholds, and fix mutations."
- REASON: "Scaling many groups/tracks without collision control leads to sameness and loss of viral edge."
- IMPACT: "Catalog remains diverse; repeat patterns are blocked early."
- CHANGE_ID: UE.CHG.2026-01-11.ENG.MF.CATALOG_COLLISION.001

---

## 0) PURPOSE
This engine blocks repetition at multiple layers:
- **Group-level** collisions (identity + fingerprint)
- **Album-level** collisions (track roles too similar)
- **Track-level** collisions:
  - hook placement & hook grammar
  - intro signature (first 10s)
  - timbre + groove combo
  - lyric fragment collisions (esp. PD fragments)
  - naming collisions (group/album/track titles)

It outputs a Collision Report and a Fix Plan (mutations).

---

## 1) INPUTS (CONSUMES)
- Catalog Memory Snapshot CTL:
  - `40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/07__CATALOG_MEMORY_CTL.md`
- Style Fingerprint for current candidate
- Track Candidate Pack (or Album Blueprint)
- Naming candidates (if available)
- Fingerprint collision thresholds CTL:
  - `40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/06__FINGERPRINT_COLLISION_THRESHOLDS_CTL.md`
- PD policy + excerpt handling (if PD mode)

---

## 2) OUTPUTS (PRODUCES)
Primary:
- **Collision Report** (PASS / SOFT COLLISION / HARD COLLISION)

Secondary:
- **Mutation Fix Plan** (what to change to pass)
- **Collision Log Entry** (for audit / take log)

---

## 3) MINI-CONTRACT (MANDATORY)
CONSUMES: [
  "Catalog Memory Snapshot",
  "Candidate Style Fingerprint",
  "Track Candidate Pack and/or Album Blueprint",
  "Naming Candidates (optional)",
  "Collision Thresholds CTL",
  "PD Policy (optional)"
]
PRODUCES: [
  "Collision Report",
  "Mutation Fix Plan",
  "Collision Log Entry"
]
DEPENDS_ON: [
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/06__FINGERPRINT_COLLISION_THRESHOLDS_CTL.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/05__COLLISION_BLOCKER_VAL.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/03__REPEAT_GUARD_VAL.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/07__NAMING_COLLISION_VAL.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/14_NAMING_IDENTITY_ENGINES/03__NAMING_COLLISION_ENG.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/13_POET_PD_CORPUS_ENGINES/05__EXCERPT_COLLISION_ENG.md"
]
OUTPUT_TARGET: "05_PROJECTS/<MUSIC_PROJECTS>/CATALOG/COLLISIONS/"

---

## 4) COLLISION VECTORS (WHAT WE COMPARE)
### 4.1 Style Fingerprint Collision
Compare anchors:
- tempo window + groove label
- timbre palette
- hook grammar pattern
- structure compression pattern
- lead persona delivery

### 4.2 Hook Grammar Collision
Compare:
- first hook timing (seconds window)
- repeat count + repeat spacing
- phrase length (syllable count proxy)
- call-response pattern

### 4.3 Intro Signature Collision (First 10s)
Compare:
- instrumentation entry order
- rhythmic motif type
- opening vocal cadence
- texture density

### 4.4 Timbre+Groove Combo Collision
Compare dominant combo:
- {groove driver + lead texture + vocal delivery}

### 4.5 Lyric Fragment Collision (PD mode)
Compare:
- reused fragments (exact or near-exact)
- same famous lines (hard collision risk)

### 4.6 Naming Collision
Compare:
- group name similarity
- album name similarity
- track title similarity
- platform formatted titles

---

## 5) COLLISION SEVERITY
- PASS: below thresholds
- SOFT COLLISION: similar, but can be fixed by 1–2 mutations
- HARD COLLISION: too close; must change at least 3 axes or discard

Hard collision triggers (examples):
- same intro signature + same hook grammar + same timbre combo
- reused PD “famous” line without transformation + same role
- naming collision with high similarity

---

## 6) FIX / MUTATION RULES
When collision detected, apply mutation plan:

### Minimal fix (for SOFT)
Change at least 2 axes:
- shift hook timing (earlier/later)
- change intro signature instrument order
- change lead instrument timbre
- change vocal delivery (clean → raspy, etc.)
- change groove feel (straight → half-time, etc.)

### Hard fix (for HARD)
Change at least 4 axes:
- replace hook grammar pattern
- rotate lead persona + supporting persona
- change key texture instrument family
- change structure (remove/shorten bridge, etc.)
- rewrite lyric hook phrase (or use different PD juice set)
- regenerate naming (new title set)

---

## 7) FAILURE MODES & FIXES
1) **Catalog memory missing / stale**
- Fix: update snapshot; do not approve without memory.

2) **Collision keeps repeating**
- Fix: invoke Novelty Injection Engine (08) then re-check.

3) **PD collisions too frequent**
- Fix: increase excerpt collision thresholds + require mosaic blend transformations.

---

## 8) HANDOFFS (XREF)
NEXT ENG:
- `11_MUSIC_FACTORY_ENGINES/08__NOVELTY_INJECTION_ENG.md` (when collisions persist)
- `11_MUSIC_FACTORY_ENGINES/09__TAKE_LOG_ENG.md` (log outcomes)

REQUIRED CTL:
- `06__FINGERPRINT_COLLISION_THRESHOLDS_CTL`
- `07__CATALOG_MEMORY_CTL`

REQUIRED VAL:
- `05__COLLISION_BLOCKER_VAL`
- `03__REPEAT_GUARD_VAL`
- `07__NAMING_COLLISION_VAL`

REQUIRED QA:
- `07__CATALOG_DIFFERENTIATION_QA`

---

## 9) OUTPUT PACK (MANDATORY LIST)
1) Collision Report (PASS/SOFT/HARD)
2) Collision Vector Breakdown (which vectors triggered)
3) Mutation Fix Plan (exact axes to change)
4) Collision Log Entry (for history)

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED

--- END.
