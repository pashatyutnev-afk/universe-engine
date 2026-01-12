# Track Factory Engine — ENGINE
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/11_MUSIC_FACTORY_ENGINES/04__TRACK_FACTORY_ENG.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
ENGINE_FAMILY: 11_MUSIC_FACTORY_ENGINES
DOC_TYPE: ENGINE
ENGINE_TYPE: MUSIC_FACTORY
LEVEL: L3
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.2.1
UID: UE.ENG.MUS.TRACK_FACTORY.001
OWNER: SYSTEM
ROLE: Produces a track from album blueprint: builds track brief, hook plan, PD poet excerpt plan,
compiles platform-native prompt pack, runs TEST→DOC gate, triggers QA/VAL,
and outputs release-ready winner without repetition.

CHANGE_NOTE:
- DATE: 2026-01-11
- TYPE: MAJOR
- SUMMARY: "Rebuilt Track Factory around TEST→DOC gate, prompt pack output, anti-repeat/collision checks, and UGC/earworm hook system integration."
- REASON: "We generate many tracks; docs only for winners; need deterministic compatibility with Suno/Udio."
- IMPACT: "Faster iteration, fewer failures, higher fidelity, stronger viral structure."
- CHANGE_ID: UE.CHG.2026-01-11.ENG.MUS.TRACK.FACTORY.001
- DATE: 2026-01-12
- TYPE: PATCH
- SUMMARY: "Reformatted to multi-line sections for operational readability; no semantic changes."
- REASON: "Compressed single-line formatting is error-prone during edits."
- IMPACT: "Safer copy/paste; easier audits."
- CHANGE_ID: UE.CHG.2026-01-12.ENG.MUS.TRACK.FACTORY.002

---

## 0) PURPOSE (LAW)
Track Factory is the **operational core** of music production.

It must:
- produce a track that matches group identity + album plan
- ensure early recognition + hook strength (viral-ready)
- use **public-domain** text only (PD policy) and extract “best juice”
- output **platform-native prompt pack** (Suno/Udio)
- prevent repeats (catalog memory + collision checks)
- run **TEST → DOC** decision gate

---

## 1) MINI-CONTRACT (MANDATORY)

CONSUMES: [
  "Group Foundation",
  "Artist Factory (cast)",
  "Album Blueprint (track slot)",
  "Duration Strategy",
  "Trend/Genre outputs (taxonomy/fusion/fingerprint/hooks/ugc/prompt compiler)",
  "Poet PD outputs (pd filter/fit scoring/juice/mosaic)",
  "CTL policies (prompt contract, negative spec, duration policy, quality gates, phrasebooks, catalog memory)",
  "VAL + QA results (hook timing, ugc ready, repeat guard, recognition, loop)"
]

PRODUCES: [
  "Track Card (single source of truth)",
  "Suno Prompt Pack",
  "Udio Prompt Pack (optional)",
  "Test Batch Plan (N takes)",
  "Take Log (top takes only)",
  "PASS/FAIL decision record",
  "Documentation Pack (only if PASS)",
  "Release Variant Notes (handoff)"
]

DEPENDS_ON: [
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/11_MUSIC_FACTORY_ENGINES/01__GROUP_FOUNDATION_ENG.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/11_MUSIC_FACTORY_ENGINES/02__ARTIST_FACTORY_ENG.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/11_MUSIC_FACTORY_ENGINES/03__ALBUM_BLUEPRINT_ENG.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/11_MUSIC_FACTORY_ENGINES/05__DURATION_STRATEGY_ENG.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/12_TREND_GENRE_ENGINES/03__STYLE_FINGERPRINT_ENG.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/12_TREND_GENRE_ENGINES/04__VIRAL_HOOK_BLUEPRINT_ENG.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/12_TREND_GENRE_ENGINES/06__EARWORM_HOOK_STACK_ENG.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/12_TREND_GENRE_ENGINES/07__PROMPT_COMPILER_ENG.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/13_POET_PD_CORPUS_ENGINES/01__PD_FILTER_ENG.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/13_POET_PD_CORPUS_ENGINES/03__JUICE_EXTRACTOR_ENG.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/01__PROMPT_CONTRACT_CTL.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/03__DURATION_POLICY_CTL.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/12__NEGATIVE_SPEC_LIBRARY_CTL.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/07__CATALOG_MEMORY_CTL.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/01__HOOK_TIMING_VAL.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/02__UGC_READY_VAL.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/03__REPEAT_GUARD_VAL.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/08__PROMPT_FIDELITY_VAL.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/60_QA__QUALITY/10_MUSIC_QA/01__SCROLL_STOP_5S_QA.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/60_QA__QUALITY/10_MUSIC_QA/02__LOOP_15S_QA.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/60_QA__QUALITY/10_MUSIC_QA/03__RECOGNITION_10S_QA.md"
]

OUTPUT_TARGET: "05_PROJECTS//TRACKS//"

---

## 2) CORE LAW — TEST → DOC GATE (ABSOLUTE)

### 2.1 TEST PHASE (FAST)
- Generate takes (batch N)
- Pick top 1–2 candidates
- Run quick QA/VAL checks
- Decision: PASS or FAIL

### 2.2 DOC PHASE (ONLY IF PASS)
- Produce documentation pack for the winning take
- Register in catalog memory
- Handoff to Release Pack engine

No documentation is produced for FAIL tracks.

---

## 3) TRACK CARD (SINGLE SOURCE OF TRUTH)
Track Factory maintains one core artifact: **TRACK CARD**.

### TRACK CARD MUST INCLUDE
- Track UID + name placeholders (final naming later)
- Group ID + Album ID + Track slot role
- Audience target (segment)
- Style Fingerprint summary (anchors + forbiddens)
- Fusion recipe summary (if used)
- Hook Blueprint summary (timing + geometry)
- Earworm Hook Stack summary (H1/H2/S-tag/Q-line)
- Poet PD plan:
  - sources
  - selected excerpts (“juice”)
  - mosaic assembly notes
- Duration target (short/full)
- Prompt Pack output (Suno/Udio)
- Test batch + results
- PASS/FAIL + why
- If PASS: winner take id/link + release variant notes

---

## 4) PROCESS (STANDARD)

### STEP 0 — Input consolidation
Inputs:
- group identity + cast
- album blueprint track slot (what this track must do in album)
- duration strategy (short/full)
- catalog memory (avoid repeats)

Output:
- Track Intent Brief (2–6 bullets)

### STEP 1 — Style & fusion lock
- build/confirm Style Fingerprint (anchors)
- if novelty needed: Fusion Recipe (A/B with ratio + insertion point)
- load Negative Spec (anti-drift)

Output:
- Style Lock Block (for prompt compiler)

### STEP 2 — Hook plan
- Earworm Hook Stack (H1/H2/microhooks/S-tag)
- Viral Hook Blueprint (template + timing + pause/drop + loop)
- UGC alignment (clip windows intent)

Output:
- Hook Plan Block

### STEP 3 — Poet PD “juice” plan (lyrical mode)
- PD filter pass (only allowed corpus)
- fit scoring (style/meaning/cadence)
- juice extractor:
  - keep only strongest lines
  - avoid “full poem dump”
- mosaic composer:
  - allow blending across PD works if needed
  - keep unified voice tone

Output:
- Lyrics Source Plan + Mosaic Draft

### STEP 4 — Prompt compilation (platform-native)
Compile Suno Prompt Pack:
- SUNO.LYRICS (RU) or instrumental instruction
- SUNO.STYLES (tags)
- SUNO.INSTRUCTION (hook timing + structure)
- SUNO.NEGATIVE (compact)
- variants: short/full/alt intro (if required)

Optional:
- compile Udio pack too

Output:
- Prompt Pack (ready to paste)

### STEP 5 — TEST BATCH generation
- batch size: 4–12 takes depending on policy
- each take changes only 1–2 knobs (controlled)
- log take ids + short tags

Output:
- Take Log draft

### STEP 6 — Quick QA/VAL gate
Minimum checks:
- scroll-stop 5s
- recognition 10s
- loop 15s
- hook timing validator
- repeat guard validator
- prompt fidelity validator

Decision:
- FAIL → iterate (Step 2–5) with diff notes
- PASS → proceed to DOC PHASE

### STEP 7 — DOC PHASE (only if PASS)
Create docs (minimal useful set, no clutter):
- Track Card (final)
- Winner Take Record
- Prompt Pack snapshot (frozen)
- Credits/metadata notes (policy)
- Release variants notes (handoff)

---

## 5) SUNO PROMPT PACK (MANDATORY OUTPUT)
Track Factory must always output a paste-ready Suno pack:
- SUNO.LYRICS (RU) with section labels
- SUNO.STYLES: 6–12 tags, ordered
- SUNO.INSTRUCTION: short paragraph (hook timing + structure + UGC moment)
- SUNO.NEGATIVE: compact list

If instrumental:
- set lyrics as “Instrumental”
- move constraints to instruction.

---

## 6) ANTI-REPEAT / COLLISION CONTROL (MANDATORY)
Before declaring PASS:
- check internal group memory:
  - do we reuse the same hook contour / chant tag?
  - do we reuse the same intro signature?
- check cross-catalog collision (if enabled):
  - flag too-similar style fingerprint + hook geometry combos

If collision risk:
- call Novelty Injection Engine to change ONLY allowed variable anchors
- never alter core anchors without explicit evolution approval

---

## 7) OUTPUT: PASS/FAIL CRITERIA (OPERATIVE)

### PASS requires
- Hook is recognizable early (policy window)
- At least one strong UGC moment exists
- Repeat guard passes (no spam)
- Prompt fidelity: track matches prompt intent
- Overall sound not “muddy/garbled” per negative spec and QA

### FAIL triggers
- late hook / dead intro
- messy structure
- vocals unintelligible RU
- annoying repetition
- drift off group identity

---

## 8) ITERATION RULE (DIFF REQUIRED)
Every iteration must write:
- what changed (3–8 bullets)
- why changed (tie to specific fail reason)
- what must be kept next time (anchors)

This feeds TAKE LOG engine.

---

## 9) OUTPUT FILE SUGGESTED LAYOUT (SIMPLE)
Track folder may contain only:
- 00__TRACK_CARD.md (single SoT)
- 01__PROMPT_PACK__SUNO.md
- 02__TAKE_LOG.md
- 03__RELEASE_NOTES.md (only if PASS)

No extra docs unless clearly useful.

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED

--- END.
