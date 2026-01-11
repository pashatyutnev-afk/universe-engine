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
ROLE: Eliminates duration chaos by locking track length targets per format + role + genre energy, and producing a deterministic “duration map” for album + release variants.

CHANGE_NOTE:
- DATE: 2026-01-11
- TYPE: MAJOR
- SUMMARY: "Defined Duration Strategy Engine: duration map, role-based targets, UGC cuts, and enforcement rules."
- REASON: "Track length chaos breaks consistency, UGC readiness, and album pacing."
- IMPACT: "All tracks get predictable lengths; platform variants become systematic."
- CHANGE_ID: UE.CHG.2026-01-11.ENG.MF.DURATION_STRATEGY.001

---

## 0) PURPOSE
This engine sets **duration targets** before generation:
- per platform format (UGC short / standard / extended)
- per track role in album (hook single vs story core vs interlude vs finale)
- per energy/genre characteristics (fast vs slow; dense vs minimal)
It outputs a **Duration Map** that all prompts must follow.

---

## 1) INPUTS (CONSUMES)
- Album Blueprint Spec (track roles + sequencing)
- Audience segments CTL
- Duration policy baseline CTL:
  - `40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/03__DURATION_POLICY_CTL.md`
- Release variants CTL:
  - `40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/04__RELEASE_VARIANTS_CTL.md`
- Optional: platform phrasebooks (Suno/Udio) for practical constraints

---

## 2) OUTPUTS (PRODUCES)
Primary:
- **Album Duration Map** (per track: target range + variant ranges)

Secondary:
- **Duration Ruleset for Track Factory** (how to ask generator)
- **Pacing Notes** (why these durations improve retention)

---

## 3) MINI-CONTRACT (MANDATORY)
CONSUMES: [
  "Album Blueprint Spec",
  "Audience Segments CTL",
  "Duration Policy CTL",
  "Release Variants CTL"
]
PRODUCES: [
  "Album Duration Map",
  "Track Duration Targets (per role)",
  "Variant Duration Plan (short/main/extended)",
  "Duration Instructions for Prompting"
]
DEPENDS_ON: [
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/03__DURATION_POLICY_CTL.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/60_QA__QUALITY/10_MUSIC_QA/01__SCROLL_STOP_5S_QA.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/60_QA__QUALITY/10_MUSIC_QA/02__LOOP_15S_QA.md"
]
OUTPUT_TARGET: "05_PROJECTS/<MUSIC_PROJECTS>/GROUPS/<GROUP_ID>/ALBUMS/<ALBUM_ID>/"

---

## 4) DURATION MAP MODEL (STANDARD)
For each track slot:

- TRACK_ID
- TRACK_ROLE
- MAIN_DURATION_TARGET: <min:max seconds>
- SHORT_CUT_TARGET (UGC): <min:max seconds> (if needed)
- EXTENDED_TARGET: <min:max seconds> (optional)
- STRUCTURE_COMPRESSION_RULES:
  - intro max seconds
  - first hook by second X
  - chorus count guidance
- NOTES: why this fits role/audience

---

## 5) CORE DURATION RULES (DEFAULTS)
These are defaults; CTL may override.

### 5.1 UGC SHORT CUT (for reels/tiktok loops)
- 15–25s (pure hook loop) OR 25–40s (micro-story + hook)
Hard:
- recognizable motif in first 3–5s
- loop window must not “break” on restart

### 5.2 MAIN RELEASE (streaming standard)
- Hook Single: 2:00–2:40
- Story Core: 2:40–3:30
- Contrast Track: 2:10–3:00
- Finale: 2:40–3:40
- Interlude (only if justified): 0:40–1:30

### 5.3 EXTENDED (optional)
- Only when genre benefits (ambient / cinematic / live-feel):
  3:40–5:30

---

## 6) ROLE-BASED COMPRESSION LOGIC
### Hook Single
- intro: 0–8s
- first hook: <= 25–35s
- total: keep tight; avoid long bridges

### Story Core
- allow longer verse development
- still must contain memorable phrase/motif

### Contrast Track
- shorter than story core unless concept requires otherwise

### Finale
- can revisit motifs from earlier tracks
- can breathe slightly longer, but not drag

---

## 7) PROMPTING INSTRUCTIONS (FOR SUNO)
When Track Factory outputs the prompt, it must include:
- duration target range (seconds)
- structural constraint:
  - “first hook by <X>s”
  - “no long intro”
  - “keep bridge short”
- for short cut:
  - “loopable 15–25s hook segment”

If platform ignores duration:
- enforce by structure instructions + repeated hook windows.

---

## 8) FAILURE MODES & FIXES
1) **Generator outputs too long**
- Fix: “shorter arrangement, fewer sections, no extended intro/bridge”.

2) **Generator outputs too short**
- Fix: request “add second verse/chorus variation” + “full ending”.

3) **Loop breaks**
- Fix: remove hard endings, use “circular ending” or sustained tail.

4) **Album pacing feels flat**
- Fix: tighten mid tracks, keep 1–2 longer tracks max.

---

## 9) HANDOFFS (XREF)
NEXT ENG:
- `11_MUSIC_FACTORY_ENGINES/04__TRACK_FACTORY_ENG.md` (must use duration map)
- `11_MUSIC_FACTORY_ENGINES/06__RELEASE_PACK_ENG.md` (variants durations)
NEXT CTL:
- `03__DURATION_POLICY_CTL`
REQUIRED QA:
- `01__SCROLL_STOP_5S_QA`
- `02__LOOP_15S_QA`
- `03__RECOGNITION_10S_QA`

---

## 10) OUTPUT PACK (MANDATORY LIST)
1) Album Duration Map (per track)
2) Role-based Duration Targets (summary)
3) Variant Duration Plan (short/main/extended)
4) Prompting Instructions (copy-ready rules)

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED

--- END.
