# FINGERPRINT COLLISION THRESHOLDS — CTL
FILE: 03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/06__FINGERPRINT_COLLISION_THRESHOLDS_CTL.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: CONTROLLERS (CTL)
CTL_REALM: 10_MUSIC_CONTROLLERS
DOC_TYPE: CONTROLLER
CTL_TYPE: FINGERPRINT_COLLISION_THRESHOLDS
LEVEL: L3
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.CTL.MUS.FINGERPRINT_COLLISION_THRESHOLDS.001
OWNER: SYSTEM
ROLE: Defines collision thresholds and actions for Style Fingerprint similarity across the catalog:
when to allow, warn, penalize, or block near-duplicate tracks/groups based on fingerprint overlap.
Used by Catalog Collision ENG, Collision Blocker VAL, and portfolio planning.

CHANGE_NOTE:
- DATE: 2026-01-12
- TYPE: MAJOR
- SUMMARY: "Created fingerprint collision thresholds: scope modes, similarity components, default thresholds, and required actions (allow/warn/block)."
- REASON: "Main failure mode: catalog sameness (same vocal feel, same hook grammar, same palette) causing repeatable patterns."
- IMPACT: "Higher differentiation, safer scaling, fewer identical outputs."
- CHANGE_ID: UE.CHG.2026-01-12.CTL.FINGERPRINT.COLLISION.001

---

## 0) PURPOSE (LAW)
This controller defines **when two outputs are “too similar”** and what to do about it:
- ALLOW (safe)
- PENALIZE (soft push away)
- WARN (must inject novelty)
- BLOCK (do not ship; redesign)

CTL defines thresholds; implementation lives in ENG/VAL/QA.

---

## 1) SCOPE MODES (WHERE COLLISIONS ARE CHECKED)
- SCOPE.GROUP (default): within one group catalog
- SCOPE.ALBUM: within an album (slot-to-slot)
- SCOPE.GLOBAL: across all groups (optional strict mode)

Default enforcement:
- production uses SCOPE.GROUP
- album pipelines also enforce SCOPE.ALBUM
- SCOPE.GLOBAL used only for heavy scaling / high-volume output

---

## 2) FINGERPRINT COMPONENTS (WHAT IS COMPARED)
Collision scoring must consider these components (not all must be present, but missing fields reduce confidence):

C1 GENRE IDENTITY
- primary genre family + fusion structure (if any)

C2 INSTRUMENTATION PALETTE
- dominant instruments / timbre palette

C3 GROOVE / TEMPO BAND
- tempo band + rhythmic feel

C4 VOCAL IDENTITY
- vocal role + timbre hints (or “instrumental”)

C5 HOOK GRAMMAR
- hook type pattern (chant / slogan / motif), repeat geometry

C6 SIGNATURE TAG (S-TAG)
- presence and pattern of identity tag

---

## 3) SIMILARITY SCORE (NORMALIZED)
A run must compute a normalized similarity score:
- SIMILARITY_0_1 where 0 = unrelated, 1 = identical.

Recommended model (policy-level, not implementation):
- weighted similarity over components C1..C6
- weights may be adapted per scope (album cares more about hook and vocal diversity)

---

## 4) DEFAULT THRESHOLDS (POLICY PARAMETERS)
These defaults apply unless overridden by governance.

### 4.1 Global thresholds (generic)
- ALLOW: SIM < 0.70
- PENALIZE: 0.70 ≤ SIM < 0.78
- WARN: 0.78 ≤ SIM < 0.86
- BLOCK: SIM ≥ 0.86

### 4.2 Album thresholds (stricter for uniqueness)
- ALLOW: SIM < 0.65
- PENALIZE: 0.65 ≤ SIM < 0.74
- WARN: 0.74 ≤ SIM < 0.82
- BLOCK: SIM ≥ 0.82

### 4.3 Group thresholds (balanced)
- ALLOW: SIM < 0.68
- PENALIZE: 0.68 ≤ SIM < 0.76
- WARN: 0.76 ≤ SIM < 0.84
- BLOCK: SIM ≥ 0.84

---

## 5) REQUIRED ACTIONS BY SEVERITY (MANDATORY)
### ALLOW
- proceed, log similarity score for memory

### PENALIZE
- proceed but require at least one novelty knob in next iteration:
  - change one component among {C2 palette, C3 groove/tempo, C5 hook grammar}
- scoring engines should lower ranking for near-duplicates

### WARN
- must apply novelty injection before shipping:
  - change at least two knobs
  - one must be from {C4 vocal identity OR C5 hook grammar}
- run collision check again after mutation

### BLOCK
- do not ship / do not document as winner
- forced redesign:
  - new hook grammar AND new palette OR new vocal identity
- re-run validators/QA after redesign

---

## 6) NOVELTY KNOB MENU (APPROVED MUTATIONS)
Allowed knobs (choose minimal set to clear WARN/BLOCK):
- K1: change hook grammar (chant → motif → slogan, etc.)
- K2: change instrumentation palette (swap dominant timbre family)
- K3: change groove/tempo band (adjacent band preferred)
- K4: change vocal identity (new role / duet split / instrumental)
- K5: change signature tag pattern (new S-tag)
- K6: limit fusion axes (reduce drift while changing uniqueness driver)

Forbidden knobs:
- random genre switching without fusion recipe
- changing identity anchors defined as “locked” in Style Fingerprint (unless approved by group creative director)

---

## 7) OUTPUT EXPECTATIONS (FOR ENGINES/VAL)
Any collision check output must include:
- scope mode
- similarity score
- top matching “nearest neighbor” references (IDs, not full text)
- severity (ALLOW/PENALIZE/WARN/BLOCK)
- required actions and chosen knobs

---

## 8) REFERENCES (RAW)
Used by:
- Catalog Memory CTL  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/07__CATALOG_MEMORY_CTL.md

Applied by:
- Catalog Collision ENG  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/11_MUSIC_FACTORY_ENGINES/07__CATALOG_COLLISION_ENG.md
- Novelty Injection ENG  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/11_MUSIC_FACTORY_ENGINES/08__NOVELTY_INJECTION_ENG.md

Validator alignment:
- Collision Blocker VAL  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/05__COLLISION_BLOCKER_VAL.md
- Catalog Differentiation QA  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/60_QA__QUALITY/10_MUSIC_QA/07__CATALOG_DIFFERENTIATION_QA.md

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED

--- END.
