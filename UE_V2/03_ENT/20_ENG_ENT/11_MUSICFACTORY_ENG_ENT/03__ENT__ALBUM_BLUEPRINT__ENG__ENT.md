# Album Blueprint Engine — ENGINE
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/11_MUSIC_FACTORY_ENGINES/03__ALBUM_BLUEPRINT_ENG.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
ENGINE_FAMILY: 11_MUSIC_FACTORY_ENGINES
DOC_TYPE: ENGINE
ENGINE_TYPE: MUSIC_FACTORY
LEVEL: L3
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.1
UID: UE.ENG.MF.ALBUM_BLUEPRINT.001
OWNER: SYSTEM
ROLE: Builds a deterministic album plan: concept, arc, tracklist skeleton, track roles, variation strategy, duration mix, UGC moment distribution, and anti-repeat constraints.

Outputs a blueprint that Track Factory can execute slot-by-slot.

CHANGE_NOTE:
- DATE: 2026-01-12
- TYPE: PATCH
- SUMMARY: "Reformatted to multi-line + added explicit INPUTS/OUTPUTS sections; no semantic changes."
- REASON: "Operational readability; safer editing; align with engine template structure."
- IMPACT: "Easier audits; less breakage during iteration."
- CHANGE_ID: UE.CHG.2026-01-12.ENG.MF.ALBUM.BLUEPRINT.002

---

## 0) PURPOSE (LAW)
Album Blueprint defines **what the album is** and **what each track must do**.

It must:
- preserve group identity (Style Fingerprint anchors)
- distribute novelty without chaos
- avoid internal repeats (hook/timbre/structure)
- plan UGC moments across the album
- define a clear arc (opening → peak → cooldown/finale)
- output slot-by-slot briefs for Track Factory

---

## 1) INPUTS (CONSUMES)
- Group Foundation
- Artist Factory (cast)
- Genre Taxonomy (A) + Fusion Recipe (optional B/C)
- Style Fingerprint (anchors + forbiddens)
- Duration Strategy / Duration Policy
- Catalog Memory (avoid repeats)
- Audience Segment Target

---

## 2) OUTPUTS (PRODUCES)
- Album Blueprint (single SoT)
- Tracklist Skeleton (slots 01..N)
- Track Role Map (what each slot does)
- Variation Strategy Map (what changes per track)
- UGC Moment Distribution Map
- Album Naming Brief (placeholders; no final titles required)
- Collision Guard Notes (album-internal)

---

## 3) MINI-CONTRACT (MANDATORY)
CONSUMES: [
  "Group Foundation",
  "Artist Factory (cast)",
  "Genre Taxonomy (A) + Fusion Recipe (optional B/C)",
  "Style Fingerprint (anchors + forbiddens)",
  "Duration Strategy / Duration Policy",
  "Catalog Memory (avoid repeats)",
  "Audience Segment Target"
]
PRODUCES: [
  "Album Blueprint (single SoT)",
  "Tracklist Skeleton (slots 01..N)",
  "Track Role Map",
  "Variation Strategy Map",
  "UGC Moment Distribution Map",
  "Album Naming Brief (placeholders)",
  "Collision Guard Notes (album-internal)"
]
DEPENDS_ON: [
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/11_MUSIC_FACTORY_ENGINES/01__GROUP_FOUNDATION_ENG.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/11_MUSIC_FACTORY_ENGINES/02__ARTIST_FACTORY_ENG.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/11_MUSIC_FACTORY_ENGINES/05__DURATION_STRATEGY_ENG.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/12_TREND_GENRE_ENGINES/01__GENRE_TAXONOMY_ENG.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/12_TREND_GENRE_ENGINES/02__FUSION_RECIPE_ENG.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/12_TREND_GENRE_ENGINES/03__STYLE_FINGERPRINT_ENG.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/12_TREND_GENRE_ENGINES/04__VIRAL_HOOK_BLUEPRINT_ENG.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/12_TREND_GENRE_ENGINES/05__UGC_MOMENT_MAP_ENG.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/07__CATALOG_MEMORY_CTL.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/03__DURATION_POLICY_CTL.md"
]
OUTPUT_TARGET: "05_PROJECTS//GROUPS//ALBUMS//"

---

## 4) ALBUM BLUEPRINT (SINGLE SOURCE OF TRUTH)
Album Blueprint is one document that must contain:

### A) Album Identity
- ALBUM_UID:
- GROUP_UID:
- ALBUM_PROMISE: (1 sentence: what fans get)
- PRIMARY_GENRE (A):
- FUSION (optional B/C + ratio):
- MOOD ARC: (start → middle → end)
- CORE ANCHORS (from fingerprint): (2–5)
- FORBIDDENS (top 6–12)

### B) Audience Target
- SEGMENT:
- UGC_INTENT: (why people will use it in content)

### C) Album Arc (simple, readable)
- OPENING: (how it starts)
- RISE: (what increases)
- PEAK: (where the biggest hook lives)
- RELEASE: (cooldown/contrast)
- FINALE: (closing statement)

### D) Tracklist Skeleton (slots)
- SLOT_COUNT: (6–14 typical)
- SLOT TABLE:
  slot → role → tempo band → hook type → novelty knob → duration type

### E) Variation Strategy
Defines what changes per track without breaking identity:
- allowed variable anchors
- max changes per track (2–4)
- reserved “signature tag” appearances (S-tag placements)

### F) UGC Moment Distribution
- which slots contain “clip moments”
- avoid stacking all UGC moments in one area

### G) Collision Guard Notes (album-internal)
What must not repeat across slots:
- same hook contour
- same chant tag
- same intro signature
- same lead timbre dominance

---

## 5) TRACK ROLE MAP (STANDARD)
Each slot must have a role type:
- OPENER (recognition fast, identity stamp)
- LEAD SINGLE (main viral candidate)
- BANGER (energy peak, drop-forward)
- STORY CUT (meaning/lyrics focus)
- CONTRAST (texture shift but still on-brand)
- EXPERIMENT (controlled novelty; strict recipe)
- COOL DOWN (breathing space)
- FINALE (summary / anthem / emotional closer)

Rule:
- Album must have at least:
  - 1 OPENER
  - 1 LEAD SINGLE
  - 1 CONTRAST or COOL DOWN

---

## 6) DURATION MIX (ANTI-CHAOS)
Album blueprint must declare duration policy per slot:
- SHORT: optimized for clips (platform-friendly)
- FULL: full song experience

Rule:
- Do not mix randomly.
- Provide a pattern, e.g.:
  - 60–70% SHORT
  - 30–40% FULL
(or per album goal)

Duration engine/policy decides exact seconds; blueprint decides distribution.

---

## 7) NOVELTY PLAN (CONTROLLED)
Album must declare novelty knobs:
- tempo band shifts (within limits)
- instrumentation swaps (within palette)
- hook grammar variant (H1/H2 geometry)
- mix space variant (dry ↔ wide)
- lyric tone variant (if allowed)

Hard rule:
- never change core anchors
- novelty changes must be spread (avoid 3 tracks in a row with same novelty knob)

---

## 8) WORKFLOW (OPERATIONAL STEPS)
1) Read Group Foundation + cast
2) Lock primary genre (A) and fingerprint anchors
3) Decide if fusion is used:
   - if yes: choose B ratio and insertion strategy
4) Choose slot count (6–14)
5) Assign track roles (map)
6) Apply duration mix plan (short/full per slot)
7) Allocate UGC moments across slots
8) Define variation strategy (what changes per slot)
9) Run album-internal collision guard planning
10) Output Tracklist Skeleton for Track Factory:
    - each slot produces a Track Intent Brief (2–6 bullets)

---

## 9) FAIL MODES & FIXES
1) Album feels like random playlist
- Fix: enforce arc + role map + anchor preservation.

2) Album repeats itself
- Fix: strengthen collision guards and novelty spread; call Catalog Collision engine.

3) Album loses group identity
- Fix: reassert fingerprint anchors; reduce fusion ratio; tighten forbiddens.

4) No clear single / no viral center
- Fix: designate LEAD SINGLE slot with strongest hook blueprint and UGC plan.

---

## 10) HANDOFFS (XREF)
NEXT ENG:
- `11_MUSIC_FACTORY_ENGINES/04__TRACK_FACTORY_ENG.md` (executes slots)
- `11_MUSIC_FACTORY_ENGINES/07__CATALOG_COLLISION_ENG.md` (anti-repeat)
- `11_MUSIC_FACTORY_ENGINES/08__NOVELTY_INJECTION_ENG.md` (controlled novelty)
- `11_MUSIC_FACTORY_ENGINES/06__RELEASE_PACK_ENG.md` (after winners chosen)

TREND/GENRE:
- `12_TREND_GENRE_ENGINES/03__STYLE_FINGERPRINT_ENG.md`
- `12_TREND_GENRE_ENGINES/04__VIRAL_HOOK_BLUEPRINT_ENG.md`
- `12_TREND_GENRE_ENGINES/05__UGC_MOMENT_MAP_ENG.md`

CTL:
- `40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/07__CATALOG_MEMORY_CTL.md`
- `40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/03__DURATION_POLICY_CTL.md`

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED

--- END.
