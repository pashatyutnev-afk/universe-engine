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
ROLE: Detects and prevents catalog-level collisions (same-y hooks, intros, motifs, lyric fragments, timbre palettes, and structure templates). Enforces novelty while preserving group identity.

CHANGE_NOTE:
- DATE: 2026-01-12
- TYPE: MAJOR
- SUMMARY: "Created Catalog Collision Engine: collision types, thresholds wiring, decision outcomes, and fix loop with Novelty Injection."
- REASON: "We produce many tracks; without collision control the catalog becomes repetitive and non-viral."
- IMPACT: "Lower repeat rate, higher uniqueness, safer scaling across many groups."
- CHANGE_ID: UE.CHG.2026-01-12.ENG.MF.CATALOG.COLLISION.001

---

## 0) PURPOSE (LAW)
Catalog Collision Engine answers one question:
**“Этот трек/альбом слишком похож на то, что уже есть?”**

It must:
- block near-duplicates
- flag risky similarities early (before release)
- propose minimal safe changes (controlled novelty)
- preserve group anchors (style fingerprint stays intact)

---

## 1) MINI-CONTRACT (MANDATORY)
CONSUMES: [
  "Track Winner Pack (or candidate takes)",
  "Track Card (hooks/structure/lyrics plan)",
  "Album Blueprint (optional)",
  "Catalog Memory CTL",
  "Fingerprint Collision Thresholds CTL",
  "Poet excerpt collision notes (if PD mosaic used)",
  "Repeat Guard validator outputs"
]
PRODUCES: [
  "Collision Report (single SoT for decision)",
  "Collision Score Summary (by type)",
  "Decision: PASS / WARN / BLOCK",
  "Fix Plan (minimal changes)",
  "Updated constraints for next iteration (what to avoid)"
]
DEPENDS_ON: [
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/07__CATALOG_MEMORY_CTL.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/06__FINGERPRINT_COLLISION_THRESHOLDS_CTL.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/03__REPEAT_GUARD_VAL.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/05__COLLISION_BLOCKER_VAL.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/11_MUSIC_FACTORY_ENGINES/08__NOVELTY_INJECTION_ENG.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/11_MUSIC_FACTORY_ENGINES/09__TAKE_LOG_ENG.md"
]
OUTPUT_TARGET: "05_PROJECTS/<MUSIC_PROJECTS>/GROUPS/<GROUP_UID>/CATALOG/COLLISIONS/"

---

## 2) COLLISION TYPES (STANDARD)
Collision types are evaluated independently.

### A) HOOK COLLISION
- Similar hook contour / chant tag / slogan line
- Similar hook rhythm + accent pattern
- Similar hook “entry timing” and pause pattern

### B) INTRO SIGNATURE COLLISION
- Same 0–10s identity stamp pattern
- Same intro instrument lead + same rhythm bed

### C) STRUCTURE TEMPLATE COLLISION
- Same section order and lengths (intro/verse/hook/drop/bridge)
- Same “drop placement” map
- Same loop-out behavior

### D) TIMBRE / PALETTE COLLISION
- Same lead timbre dominance
- Same palette combo (e.g., identical drum kit feel + bass texture + lead synth color)

### E) GROOVE / RHYTHM COLLISION
- Same groove pattern at same tempo band
- Same hi-hat / snare “signature” behavior

### F) LYRICS / EXCERPT COLLISION (PD + mosaic)
- Reuse of the same strongest lines too often
- Reuse of the same “mosaic stitch” pattern
- Reuse of the same rhyme skeleton/phrase cadence

### G) CROSS-GROUP COLLISION (optional)
- Similarity against other groups’ catalogs (if global memory enabled)

---

## 3) THRESHOLDS (CONTROLLED BY CTL)
This engine does not invent thresholds.
It reads:
- collision thresholds by type
- allowed similarity bands
- what counts as “hard block” vs “warn”

Owner:
- `40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/06__FINGERPRINT_COLLISION_THRESHOLDS_CTL.md`

---

## 4) COLLISION REPORT (SINGLE SoT)
Collision Report must contain:

### 4.1 Header
- GROUP_UID / ALBUM_UID / TRACK_UID
- candidate take id (if take-based)
- date / version / status

### 4.2 Scores by type
- HOOK:
- INTRO:
- STRUCTURE:
- TIMBRE:
- GROOVE:
- LYRICS (if any):
- CROSS-GROUP (if enabled):

### 4.3 Top nearest neighbors (internal)
- list of the 1–5 most similar prior tracks
- what similarity is based on (type)

### 4.4 Decision
- PASS / WARN / BLOCK
- Why (short and specific)

### 4.5 Fix Plan (minimal)
- what to change (1–3 moves)
- what must NOT change (anchors)
- what to retest

---

## 5) PROCESS (OPERATIONAL STEPS)
1) Load catalog memory scope
- group-only memory (default)
- optionally cross-group memory

2) Extract fingerprints from candidate
Minimum extraction:
- hook signature tags
- intro signature tag
- structure template id
- palette id
- groove id
- lyric excerpt ids (if PD)

3) Compare against memory
- compute per-type similarity
- fetch nearest neighbors

4) Apply CTL thresholds
- mark type as PASS/WARN/BLOCK

5) Produce Collision Report
- single SoT

6) Decision output
- PASS: allow Release Pack
- WARN: allow but require 1 novelty move
- BLOCK: stop release, force redesign via Novelty Injection

7) Handoff
- if WARN/BLOCK: call `08__NOVELTY_INJECTION_ENG`
- log diff to `09__TAKE_LOG_ENG`

---

## 6) FIX MOVES (MINIMAL CHANGE PLAYBOOK)
Fix moves must preserve group identity anchors.

### Allowed minimal moves (examples)
- Hook grammar variant (H1 ↔ H2) while keeping slogan theme
- Change hook rhythm accents (without changing tempo band)
- Swap hook owner (vocal ↔ instrument) within roster
- Intro stamp: change lead timbre or first-3s motif
- Palette: replace 1 dominant timbre with allowed alternative
- Groove: micro-variation of hat/snare pattern
- Structure: shift one section length and move a drop by a small offset
- Lyrics: replace repeated “juice” lines with different PD fragments; adjust mosaic stitch

### Forbidden moves (unless evolution approved)
- removing core fingerprint anchors
- changing primary genre identity
- over-fusing until it becomes another group

---

## 7) DECISION RULES (OPERATIVE)
### PASS
- no type exceeds WARN threshold
- repeat guard passes
- lyric excerpt reuse is within policy

### WARN
- 1–2 types exceed PASS but below BLOCK
- must apply a minimal fix move
- must re-test (short batch)

### BLOCK
- any hard-block threshold hit
- or multiple WARN types stack together in a way that makes it “same song again”

---

## 8) FAILURE MODES & FIXES
1) Catalog “one-same-song syndrome”
- Fix: strengthen memory scope, raise strictness, enforce palette and hook rotation.

2) Too aggressive blocking (kills productivity)
- Fix: adjust thresholds in CTL, allow WARN path with minimal fixes.

3) PD lyric reuse too often
- Fix: expand PD sources, strengthen excerpt collision engine + mosaic variation.

4) Cross-group collisions in a multi-group factory
- Fix: enable cross-group memory for hooks only (partial scope).

---

## 9) HANDOFFS (XREF)
If PASS:
- `11_MUSIC_FACTORY_ENGINES/06__RELEASE_PACK_ENG.md`

If WARN/BLOCK:
- `11_MUSIC_FACTORY_ENGINES/08__NOVELTY_INJECTION_ENG.md`
- then back to `11_MUSIC_FACTORY_ENGINES/04__TRACK_FACTORY_ENG.md` for retest

Mandatory logging:
- `11_MUSIC_FACTORY_ENGINES/09__TAKE_LOG_ENG.md`

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED

--- END.
