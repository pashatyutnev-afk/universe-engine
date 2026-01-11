# Duration Strategy Engine — ENGINE
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/11_MUSIC_FACTORY_ENGINES/05__DURATION_STRATEGY_ENG.md

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
UID: UE.ENG.MF.DURATION_STRATEGY.001
OWNER: SYSTEM
ROLE: Converts genre + audience + platform goals into deterministic duration targets (short/full) with hook timing constraints and section budgets. Eliminates duration chaos across catalog.

CHANGE_NOTE:
- DATE: 2026-01-12
- TYPE: MAJOR
- SUMMARY: "Created Duration Strategy: short/full modes, section budgets, hook timing law, and album-level distribution guidance."
- REASON: "Track length chaos breaks UGC performance and catalog coherence."
- IMPACT: "Consistent lengths per style, faster production, better retention and reuse in content."
- CHANGE_ID: UE.CHG.2026-01-12.ENG.MF.DURATION.STRAT.001

---

## 0) PURPOSE (LAW)
Duration Strategy defines **how long tracks should be** and **where hooks must land**.

It outputs:
- short vs full targets
- section time budgets (intro/verse/hook/drop/bridge/outro)
- hook timing requirements
- album-level duration mix guidance

This engine does not enforce. Enforcement is done by CTL/VAL/QA.

---

## 1) MINI-CONTRACT (MANDATORY)
CONSUMES: [
  "Primary Genre (A) + Fusion plan (optional)",
  "Audience Segment Target",
  "Platform mode (Suno/Udio + UGC intent)",
  "Viral Hook Blueprint + UGC Moment Map",
  "Catalog Memory (avoid repeating same length patterns)",
  "Duration Policy CTL (hard constraints)"
]
PRODUCES: [
  "Duration Plan (Short)",
  "Duration Plan (Full)",
  "Hook Timing Window",
  "Section Budget Map",
  "Album Duration Mix Guidance",
  "Duration Variant Notes (if multiple)"
]
DEPENDS_ON: [
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/03__DURATION_POLICY_CTL.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/12_TREND_GENRE_ENGINES/04__VIRAL_HOOK_BLUEPRINT_ENG.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/12_TREND_GENRE_ENGINES/05__UGC_MOMENT_MAP_ENG.md"
]
OUTPUT_TARGET: "05_PROJECTS/<MUSIC_PROJECTS>/GROUPS/<GROUP_UID>/DURATION/"

---

## 2) CORE MODES (STANDARD)
### 2.1 SHORT MODE (UGC-OPTIMIZED)
Goal: maximum retention + clip usability.

- Total duration target: **~1:30 to ~2:15** (policy may override)
- Hook must arrive early (see Hook Timing Window)
- Minimal long intros; no long outros
- Loop-friendly ending preferred

### 2.2 FULL MODE (SONG-OPTIMIZED)
Goal: full listening satisfaction + replay value.

- Total duration target: **~2:30 to ~3:45** (policy may override)
- Hook still must arrive reasonably early
- Allows bridge/breakdown if it increases emotional peak
- Still must preserve loop/recognition windows for the first 10–15s

Rule:
- Album Blueprint decides **distribution** (short/full per slot).
- Duration Strategy decides **targets** and **budgets**.

---

## 3) HOOK TIMING WINDOW (LAW)
Duration plan must declare:
- Hook Window Start
- Hook Window Latest
- Secondary hook (optional) placement

Default operational rules (unless CTL overrides):
- SHORT: hook appears very early and repeats often
- FULL: hook appears early and is reinforced

Hook timing must align with:
- Hook Timing Validator (VAL)
- Recognition / Loop QA checks

---

## 4) SECTION BUDGET MAP (MANDATORY)
Duration plan must output a budget for:
- INTRO
- BUILD / VERSE (if any)
- PRE-HOOK (optional)
- HOOK
- DROP / SWITCH (optional, genre-dependent)
- BRIDGE (optional, full mode)
- OUTRO / LOOP OUT

### Default budget philosophy
- Intro is a “stamp”, not a journey
- First 10 seconds must contain recognition material
- Hook gets the largest share of attention
- Ending should be loop-friendly, not dead air

---

## 5) GENRE-AWARE DURATION TUNING (GUIDELINES)
This engine does not hardcode every genre number, but it defines tuning principles:

- Hook-forward genres (pop/trap/phonk/edm): shorten intro; emphasize hook cycles
- Narrative-heavy tracks: allow slightly longer setup but keep early recognition
- High-tempo genres: avoid long bridges; keep energy continuity
- Cinematic/epic: allow build if it serves peak, but still ensure early identity stamp

Fusion note:
- If fusion is used, budget must specify where fusion happens (drop/bridge) without extending intro.

---

## 6) VARIATION CONTROL (ANTI-REPEAT)
To avoid catalog sameness:
- do not use identical duration + identical section order for many tracks
- rotate 2–3 structural “duration templates” per group
- keep identity anchors constant, vary only allowed structure knobs

This links to Catalog Memory and Repeat Guard.

---

## 7) OUTPUT FORMAT (DURATION PLAN PACK)
Duration Strategy outputs a compact pack:

### DURATION PLAN — SHORT
- TARGET_TOTAL:
- HOOK_WINDOW:
- SECTION_BUDGETS:
- LOOP_END_NOTE:
- NO_GO (what must not happen)

### DURATION PLAN — FULL
- TARGET_TOTAL:
- HOOK_WINDOW:
- SECTION_BUDGETS:
- OPTIONAL_BRIDGE_RULE:
- NO_GO:

### ALBUM MIX GUIDANCE
- Recommended ratio short/full:
- Where full tracks should sit in arc:

---

## 8) FAILURE MODES & FIXES
1) Tracks feel too long / boring
- Fix: shorten intro; reduce bridge; increase hook density; enforce early recognition.

2) Tracks feel too short / unfinished
- Fix: in short mode add micro-bridge or hook variation; in full mode add structured bridge.

3) Hook comes late
- Fix: re-budget; move hook earlier; cut intro.

4) Catalog sameness in lengths
- Fix: rotate duration templates; adjust section budgets per slot.

---

## 9) HANDOFFS (XREF)
Used by:
- `11_MUSIC_FACTORY_ENGINES/03__ALBUM_BLUEPRINT_ENG.md`
- `11_MUSIC_FACTORY_ENGINES/04__TRACK_FACTORY_ENG.md`
- `40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/03__DURATION_POLICY_CTL.md`
Validated by:
- `50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/01__HOOK_TIMING_VAL.md`
- `60_QA__QUALITY/10_MUSIC_QA/02__LOOP_15S_QA.md`
- `60_QA__QUALITY/10_MUSIC_QA/03__RECOGNITION_10S_QA.md`

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED

--- END.
