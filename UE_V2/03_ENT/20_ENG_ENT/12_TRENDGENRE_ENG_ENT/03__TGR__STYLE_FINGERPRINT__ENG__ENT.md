# Style Fingerprint Engine — ENGINE
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/12_TREND_GENRE_ENGINES/03__STYLE_FINGERPRINT_ENG.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
ENGINE_FAMILY: 12_TREND_GENRE_ENGINES
DOC_TYPE: ENGINE
ENGINE_TYPE: TREND_GENRE
LEVEL: L3
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.1
UID: UE.ENG.TG.STYLE_FINGERPRINT.001
OWNER: SYSTEM
ROLE: Produces a compact, deterministic “style fingerprint” that encodes group identity in audible anchors
(vocal/instrument/mix/groove/hook grammar) and defines what may vary.

Used to prevent drift and enable consistent series output.

CHANGE_NOTE:
- DATE: 2026-01-11
- TYPE: MAJOR
- SUMMARY: "Created Style Fingerprint system: anchors, variables, tokens, collision control, and platform-friendly encoding."
- REASON: "Without fingerprint, the generator drifts; tracks become inconsistent and repetitive."
- IMPACT: "Recognizable brand sound + controlled variation across albums/tracks."
- CHANGE_ID: UE.CHG.2026-01-11.ENG.TG.STYLE.FINGERPRINT.001
- DATE: 2026-01-12
- TYPE: PATCH
- SUMMARY: "Reformatted to multi-line sections for operational readability; no semantic changes."
- REASON: "Compressed formatting is error-prone during edits."
- IMPACT: "Safer copy/paste; easier audits."
- CHANGE_ID: UE.CHG.2026-01-12.ENG.TG.STYLE.FINGERPRINT.002

---

## 0) PURPOSE (LAW)
This engine outputs a **STYLE FINGERPRINT (SF)** — a minimal, stable identity spec that:
- makes the group recognizable within seconds
- keeps generation consistent across tracks/albums
- defines what can vary (novelty) without breaking identity
- is compressible into platform-native style tags

---

## 1) INPUTS (CONSUMES)
- Group Foundation (identity promise + audience + vibe)
- Artist Roster Spec (vocalists + instrumental personas)
- Genre Taxonomy (core genre family)
- Fusion Recipe (optional, limits and ratio)
- Hook Blueprint preferences (hook grammar tendencies)
- Catalog Memory (avoid collisions inside the group and across groups)
- Mix/Master preference class (clean/dirty/wide/dry etc.)

---

## 2) OUTPUTS (PRODUCES)
- STYLE FINGERPRINT (SF PACK):
  - Core Anchors (must stay)
  - Variable Anchors (allowed to change)
  - Forbidden Drift List (must never happen)
  - Token Set (short tokens for logs/memory)
  - Platform Encoding (Suno/Udio tags order)
  - Fingerprint Diff (if updated)
  - Collision Check Notes (what to compare)

---

## 3) MINI-CONTRACT (MANDATORY)
CONSUMES: [
  "Group Foundation",
  "Artist Roster Spec",
  "Genre Taxonomy",
  "Fusion Recipe (optional)",
  "Catalog Memory",
  "Mix/Master preference"
]
PRODUCES: [
  "Style Fingerprint Pack",
  "Platform Encoding",
  "Fingerprint Diff",
  "Collision Check Notes"
]
DEPENDS_ON: [
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/12_TREND_GENRE_ENGINES/01__GENRE_TAXONOMY_ENG.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/12_TREND_GENRE_ENGINES/02__FUSION_RECIPE_ENG.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/07__CATALOG_MEMORY_CTL.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/05__COLLISION_BLOCKER_VAL.md"
]
OUTPUT_TARGET: "05_PROJECTS//FINGERPRINTS/"

---

## 4) STYLE FINGERPRINT — CORE MODEL
Fingerprint is split into:
- **CORE ANCHORS** (2–5) — NEVER change inside a group
- **VARIABLE ANCHORS** (3–8) — can vary across tracks
- **DRIFT FORBIDDENS** — explicit “no-go”
- **TOKENS** — short labels for memory/logging and collision detection

---

## 5) CORE ANCHORS (MANDATORY)
Pick 2–5 anchors total.
At least one must be AUDIO-OBVIOUS.

Allowed core anchor types:

### A) Genre Core
- primary genre family (e.g., post-punk / trap / folk-rock)
- must be stable unless "evolution" is explicitly planned

### B) Groove Core
- “rhythm feel”: straight / half-time / swing / bounce
- 1 core groove tendency

### C) Timbre Signature
- signature lead texture (guitar tone / synth patch / vocal texture)
- signature drum character (punchy dry / roomy live)

### D) Hook Grammar
- how hooks behave:
  - short chant tags
  - call-response
  - melodic motif repetition geometry

### E) Vocal Identity (if lyrical)
- delivery: clean / raspy / whisper / chant
- register preference
- articulation: tight / loose

Rule:
- Core anchors must be described in terms a generator can follow (tags + short instructions).

---

## 6) VARIABLE ANCHORS (ALLOWED VARIATION)
These can vary without breaking identity:
- tempo range (within band)
- instrumentation swaps (within palette)
- secondary groove variation (one per track)
- microhook style
- mix “space” amount (dry ↔ wide)
- lyric tone variants (dark ↔ tender) if allowed by group foundation

Hard limit:
- change max 2–4 variable anchors per track (prevents chaos).

---

## 7) DRIFT FORBIDDENS (MANDATORY)
A compact list (6–12 items), e.g.:
- no random genre jumps
- no “AI chant spam repeats”
- no muddy vocals / unintelligible RU
- no overlong intro (if short-form target)
- no chaotic structure
- no off-brand vocal style (e.g., opera vibrato) unless part of identity

This list is fed into Negative Spec Library in prompts.

---

## 8) TOKENS (FOR MEMORY & COLLISION)
Fingerprint must output tokens.

### 8.1 Anchor Tokens (3–8)
Examples pattern (tokens are short):
- GENRE_CORE:
- GROOVE_CORE:
- TIMBRE_TAG:
- HOOK_GRAMMAR:
- VOCAL_TAG:

### 8.2 Collision Vector Tokens (2–6)
Used by collision engine:
- INTRO_SIGNATURE
- HOOK_CONTOUR
- RHYTHM_CELL
- CHANT_TAG
- SOUND_TAG

Tokens are descriptive but short and repeatable.

---

## 9) PLATFORM ENCODING (SUNO / UDIO)
Fingerprint must provide:
- SUNO_STYLE_TAGS (ordered list, 6–12)
- UDIO_TAGS (ordered list, 8–15)
- 1–2 lines of “instruction glue” (what tags can’t express)

Order rule:
- genre → era → instrumentation → vocal → groove → mood → mix traits → signature tag

---

## 10) UPDATE RULES (FINGERPRINT DIFF)
Fingerprint changes are dangerous.

Allowed update reasons:
- group evolution phase
- persistent collision problems
- audience segment retarget

When updated, output:
- what changed (bullets)
- what stayed (core anchors preserved)
- why (tie to logs/QA)

---

## 11) FAIL MODES & FIX
1) Fingerprint too broad → outputs feel generic  
- Fix: add one timbre signature + one hook grammar anchor.

2) Fingerprint too narrow → outputs repeat  
- Fix: widen variable anchors (tempo band, instrumentation swaps).

3) Drifts happen despite fingerprint  
- Fix: strengthen forbiddens + push anchors earlier in prompt compiler.

4) Collisions inside group  
- Fix: adjust collision vector tokens and call Novelty Injection Engine for selective changes.

---

## 12) HANDOFFS (XREF)
Feeds into:
- `12_TREND_GENRE_ENGINES/04__VIRAL_HOOK_BLUEPRINT_ENG.md`
- `12_TREND_GENRE_ENGINES/06__EARWORM_HOOK_STACK_ENG.md`
- `12_TREND_GENRE_ENGINES/07__PROMPT_COMPILER_ENG.md`
- `11_MUSIC_FACTORY_ENGINES/07__CATALOG_COLLISION_ENG.md`
- `11_MUSIC_FACTORY_ENGINES/09__TAKE_LOG_ENG.md`

Validated by:
- `50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/10__VOICE_DIVERSITY_VAL.md`
- `50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/05__COLLISION_BLOCKER_VAL.md`

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED

--- END.
