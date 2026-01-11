# Earworm Hook Stack Engine — ENGINE
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/12_TREND_GENRE_ENGINES/06__EARWORM_HOOK_STACK_ENG.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
ENGINE_FAMILY: 12_TREND_GENRE_ENGINES
DOC_TYPE: ENGINE
ENGINE_TYPE: TREND_GENRE
LEVEL: L3
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.ENG.TG.EARWORM_HOOK_STACK.001
OWNER: SYSTEM
ROLE: Builds a multi-layer hook stack (lyric/melody/rhythm/sound/cadence) to maximize “stuck-in-head” effect while preventing cheap repetition and style drift.

CHANGE_NOTE:
- DATE: 2026-01-11
- TYPE: MAJOR
- SUMMARY: "Created earworm hook stack: primary+secondary+micro hooks, timing windows, variation rules, anti-repeat guard, and UGC-ready hooks."
- REASON: "We need controllable viral memory mechanics, not random luck."
- IMPACT: "Higher recognition, more replays, stronger quoteability, fewer dead intros."
- CHANGE_ID: UE.CHG.2026-01-11.ENG.TG.EARWORM.STACK.001

---

## 0) PURPOSE (LAW)
This engine outputs a **HOOK STACK** that:
- creates a **recognizable identity** in first seconds
- produces **repeat-safe** hooks (variation and distribution rules)
- supports both **lyrical** and **instrumental** tracks
- feeds downstream engines: Viral Hook Blueprint + UGC Moment Map + Prompt Compiler

---

## 1) INPUTS (CONSUMES)
- Genre Taxonomy (what “works” in target genre family)
- Fusion Recipe (allowed cross-genre moves)
- Style Fingerprint (identity anchors)
- Audience Segments (what hooks them)
- Duration Strategy (hook timing constraints)
- UGC Moment Map (clip windows requirements)
- Negative Spec Library (avoid annoying artifacts)

---

## 2) OUTPUTS (PRODUCES)
- HOOK STACK (structured):
  - Primary Hook (H1)
  - Secondary Hook (H2)
  - Microhooks (H3..Hn)
  - Signature Sound Tag (S-tag)
  - Quote Line / Caption Hook (Q-line) — if lyrical
  - Timing Plan (when each appears)
  - Variation Plan (how repeats evolve)
- Hook Placement Notes (for prompt compiler)
- Anti-Repeat Guard Rules (for validator alignment)

---

## 3) MINI-CONTRACT (MANDATORY)
CONSUMES: [
  "Genre Taxonomy",
  "Fusion Recipe",
  "Style Fingerprint",
  "Audience Segments",
  "Duration Strategy",
  "UGC Moment Map",
  "Negative Spec Library"
]
PRODUCES: [
  "Hook Stack",
  "Timing Plan",
  "Variation Plan",
  "Anti-Repeat Guard Rules"
]
DEPENDS_ON: [
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/12_TREND_GENRE_ENGINES/01__GENRE_TAXONOMY_ENG.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/12_TREND_GENRE_ENGINES/02__FUSION_RECIPE_ENG.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/12_TREND_GENRE_ENGINES/03__STYLE_FINGERPRINT_ENG.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/12_TREND_GENRE_ENGINES/05__UGC_MOMENT_MAP_ENG.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/03__DURATION_POLICY_CTL.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/12__NEGATIVE_SPEC_LIBRARY_CTL.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/08__AUDIENCE_SEGMENTS_CTL.md"
]
OUTPUT_TARGET: "05_PROJECTS/<MUSIC_PROJECTS>/HOOKS/"

---

## 4) CORE MODEL — HOOK TYPES
We model earworm as a **stack** of hooks (not one “chorus” only).

### 4.1 H1 — Primary Hook (identity)
Must be one of:
- melodic motif (2–6 notes) + repeat-safe contour
- lyric phrase (3–7 words) with rhythm signature
- riff (guitar/synth) 1–2 bars
- chant/call-response “tag”

Hard rules:
- recognition window: early (see Timing Plan)
- must survive “phone speaker” listening (simple contour / clear rhythm)

### 4.2 H2 — Secondary Hook (support / contrast)
Purpose:
- refresh attention
- create “reply” to H1 (answer phrase)
- bridge energy before next H1

Rules:
- cannot be stronger than H1 (otherwise identity flips)
- can introduce small harmonic or rhythmic lift

### 4.3 H3..Hn — Microhooks (dopamine sprinkles)
Examples:
- short fill before chorus
- micro-drop or pause-snap
- sound tag (one-shot, vocal chop, riser)
- “turn-of-phrase” internal rhyme (if lyrical)

Rules:
- microhooks are **distributed**, not stacked in one spot
- each appears 1–2 times max unless it is the signature tag

### 4.4 S-tag — Signature Sound Tag
One signature element that makes the track instantly “ours”:
- a specific synth patch + 2-note tag
- a drum fill identity
- a vocal ad-lib tag

Rule:
- S-tag must appear in first ~15 seconds and again near the end (loop imprint)

### 4.5 Q-line — Quote Line (lyrical only)
A single line designed for captions / comments:
- short, clean, emotionally pointed
- pronounceable, no tongue-twister

Rule:
- Q-line must be near a UGC moment window (from UGC Moment Map)

---

## 5) TIMING PLAN (ANTI-CHAOS)
Output must include **hook timing targets** (relative, platform-safe):

Required fields:
- INTRO_GRAB: where the first “grab” happens
- H1_FIRST: first clear H1 statement
- H1_REPEAT_1: first repeat (with variation)
- H2_FIRST: first H2 statement
- S_TAG_FIRST / S_TAG_REPEAT
- UGC_CLIP_WINDOW_1..N: align to UGC Moment Map
- OUTRO_LOOP: loopable last 3–8 seconds (if allowed)

Default timing heuristics (override by Duration Policy):
- intro grab: 0–7s
- H1 first: by ~10–15s
- H2 first: before mid-track
- outro loop hint: last ~5–12s

---

## 6) VARIATION PLAN (REPEAT-SAFE)
We do NOT want copy-paste repeats. We want “same but evolved”.

Variation knobs:
- melodic: same contour, altered ending note
- rhythm: same phrase, different syncopation accent
- lyric: same key phrase, new setup line
- arrangement: drop instruments on repeat 1, add on repeat 2
- vocal: lead vs backing call-response alternate

Hard rule:
- H1 repeats 2–4 times depending on duration,
  but each repeat must change at least 1 knob (small change is enough).

---

## 7) HOOK STACK OUTPUT FORMAT (MANDATORY)
Engine output must be stored as:

### HOOK_STACK
- H1:
  - type: <melody|lyric|riff|chant>
  - core: <short description>
  - execution: <how it sounds / performed>
- H2:
  - type:
  - core:
  - execution:
- H3..Hn:
  - list of microhooks (each: type/core/execution)
- S_TAG:
  - sound identity + placement notes
- Q_LINE (optional):
  - exact line text (RU) + placement note

### TIMING_PLAN
- intro_grab:
- h1_first:
- h1_repeat_1:
- h2_first:
- s_tag_first:
- ugc_windows:
- outro_loop:

### VARIATION_PLAN
- h1_variations:
- arrangement_variations:
- vocal_variations:
- microhook_distribution:

### ANTI_REPEAT_GUARD
- forbidden: exact copy-paste of H1 > 2 times
- forbidden: same drum loop unchanged for entire track (unless genre requires)
- forbidden: 12+ identical words repeated in a row (lyrical)
- required: at least one “attention reset” event (pause/drop/switch)

---

## 8) INSTRUMENTAL MODE SUPPORT
If track is instrumental:
- Q-line removed
- lyric hook replaced by:
  - lead motif hook (H1) + timbre tag (S-tag)
- microhooks become:
  - fills, risers, cut-stops, ear-candy

---

## 9) COMMON FAIL MODES & FIX RULES
1) Hook late / too long intro
- Fix: compress intro, force H1 first earlier, add intro grab.

2) Hook annoying (over-repeated)
- Fix: reduce repeats, enforce variation plan.

3) Hook not memorable (too complex)
- Fix: simplify contour, make rhythm clearer, reduce harmonic wandering.

4) Track loses identity (drift)
- Fix: re-anchor with Style Fingerprint + S-tag recurrence.

---

## 10) HANDOFFS (WHO USES THIS)
- Viral Hook Blueprint Engine consumes H1/H2 + timing to define “viral shape”.
- UGC Moment Map Engine aligns Q-line and pause/drop windows.
- Prompt Compiler Engine converts stack into platform-native prompt constraints.
- Validators check: recognition time, repeat guard, fidelity.

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED

--- END.
