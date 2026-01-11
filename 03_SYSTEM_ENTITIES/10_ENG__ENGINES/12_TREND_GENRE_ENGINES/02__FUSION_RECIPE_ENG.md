# Fusion Recipe Engine — ENGINE
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/12_TREND_GENRE_ENGINES/02__FUSION_RECIPE_ENG.md

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
UID: UE.ENG.TG.FUSION_RECIPE.001
OWNER: SYSTEM
ROLE: Designs controlled genre fusions (A+B, A+B+C) with explicit ratios, insertion points, anchor preservation, and drift blockers. Produces a deterministic fusion recipe usable by Style Fingerprint and Prompt Compiler.

CHANGE_NOTE:
- DATE: 2026-01-11
- TYPE: MAJOR
- SUMMARY: "Defined Fusion Recipe system: ratio rules, insertion points, anchor mapping, and failure guards for genre blending."
- REASON: "Raw genre mixing causes drift and incoherent tracks; we need controlled fusion."
- IMPACT: "Trend-ready hybrids with stable identity and repeatable production."
- CHANGE_ID: UE.CHG.2026-01-11.ENG.TG.FUSION.RECIPE.001

---

## 0) PURPOSE (LAW)
Fusion Recipe is a **controlled blending plan** that:
- keeps one primary identity (Genre A)
- injects secondary spice (Genre B) without breaking coherence
- optionally adds micro-spice (Genre C) for novelty
- specifies where fusion happens (intro/hook/drop/bridge)
- defines what must stay constant (fingerprint anchors)

---

## 1) INPUTS (CONSUMES)
- Genre Taxonomy (A/B/C selection space)
- Style Fingerprint Core Anchors (must remain)
- Audience Segment Target (what hybrid will attract)
- Viral Hook Blueprint (where hook lives)
- UGC Moment Map (drop/snap windows)
- Catalog Memory (avoid repeating same fusion inside catalog)
- Negative Spec Library (anti-drift constraints)

---

## 2) OUTPUTS (PRODUCES)
- Fusion Recipe Pack (FRP):
  - Primary Genre (A)
  - Secondary Genre (B)
  - Optional Micro Genre (C)
  - Ratio (A/B/C)
  - Feature Map (what each genre contributes: drums/bass/harmony/vocals/etc.)
  - Insertion Points (where fusion is applied)
  - Anchor Preservation List (what must stay)
  - Drift Blockers (what must NOT appear)
  - Prompt Encoding Notes (platform-ready phrasing)
- Fusion Variant Set (optional V1..V3)
- Fusion Risk Notes (what can go wrong + how to fix)

---

## 3) MINI-CONTRACT (MANDATORY)
CONSUMES: [
  "Genre Taxonomy",
  "Style Fingerprint (core anchors)",
  "Audience Segment Target",
  "Viral Hook Blueprint",
  "UGC Moment Map",
  "Catalog Memory",
  "Negative Spec Library"
]
PRODUCES: [
  "Fusion Recipe Pack (FRP)",
  "Fusion Variant Set (optional)",
  "Fusion Risk Notes",
  "Prompt Encoding Notes"
]
DEPENDS_ON: [
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/12_TREND_GENRE_ENGINES/01__GENRE_TAXONOMY_ENG.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/12_TREND_GENRE_ENGINES/03__STYLE_FINGERPRINT_ENG.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/12_TREND_GENRE_ENGINES/04__VIRAL_HOOK_BLUEPRINT_ENG.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/12__NEGATIVE_SPEC_LIBRARY_CTL.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/07__CATALOG_MEMORY_CTL.md"
]
OUTPUT_TARGET: "05_PROJECTS/<MUSIC_PROJECTS>/FUSION_RECIPES/"

---

## 4) FUSION AXES (WHAT YOU MIX)
Fusion is not “mix everything”. It’s mixing on axes.

Allowed axes:
A) DRUMS / GROOVE (rhythm feel)
B) BASS POCKET (movement + weight)
C) HARMONY / CHORD COLOR
D) MELODY / HOOK CONTOUR
E) INSTRUMENT PALETTE (timbre)
F) VOCAL DELIVERY (if lyrical)
G) MIX AESTHETIC (dry/roomy/wide/lofi-clean)

Rule:
- Primary genre owns at least 3 axes.
- Secondary genre may own max 1–2 axes (unless special case).

---

## 5) RATIO RULES (STRICT)
### 5.1 Standard fusion
- A/B = 70/30 (default)
- C optional = 10% max (micro spice)

### 5.2 Aggressive fusion (riskier)
- A/B = 60/40
Only if:
- style fingerprint allows it
- drift blockers are strong

### 5.3 Micro-fusion (safe)
- A/B = 85/15
Use when:
- the group must remain very recognizable

Hard rule:
- Never exceed B > 40% unless the goal is a deliberate “evolution phase”.

---

## 6) INSERTION POINTS (WHERE FUSION HAPPENS)
The recipe must declare fusion placement:
- INTRO: short taste, not full switch
- PRE-HOOK: tension / lift
- HOOK: only if hook clarity won’t suffer
- DROP/SWITCH: best place for B influence
- BRIDGE: optional experimental pocket
- OUTRO/LOOP: micro-spice for memory imprint

Rule:
- Don’t fuse everywhere. Choose 1–2 primary insertion points.

---

## 7) FEATURE MAP (MANDATORY)
For each genre A/B/C define contributions:

Example schema:
- A contributes:
  - drums:
  - bass:
  - harmony:
  - hook style:
  - mix traits:
- B contributes:
  - (max 2 axes owned)
- C contributes:
  - (max 1 axis micro)

This prevents “genre soup”.

---

## 8) ANCHOR PRESERVATION (MUST STAY)
From Style Fingerprint keep:
- at least 2 core anchors unchanged
- keep signature sound tag (S-tag) present
- keep hook grammar consistent (unless fusion explicitly targets hook grammar)

---

## 9) DRIFT BLOCKERS (MANDATORY)
A compact set of “no-go” outcomes:
- no full genre switch mid-track
- no conflicting vocal style (e.g., opera vibrato) unless specified
- no random tempo jump
- no new unrelated instruments that signal a different genre identity
- no structural chaos (must match blueprint)

These become negative prompt constraints.

---

## 10) VARIANT SET (OPTIONAL, V1..V3)
If multiple candidates are needed:
- V1: safe ratio (85/15 or 70/30), fuse in drop only
- V2: standard (70/30), fuse in pre-hook + drop
- V3: aggressive (60/40), fuse in hook + drop (only if approved)

Never output more than 3 fusion variants at once.

---

## 11) FAILURE MODES & FIX
1) Sounds incoherent (two songs glued)
- Fix: reduce B ratio; move fusion to drop only; preserve more anchors.

2) Hook clarity dies
- Fix: remove B influence from hook axis; keep B on drums or mix only.

3) Track drifts away from group identity
- Fix: reintroduce S-tag earlier; enforce anchor preservation; strengthen drift blockers.

4) Fusion feels too subtle (no novelty)
- Fix: allow B to own one stronger axis (e.g., drum groove), but keep A on hook.

---

## 12) PROMPT ENCODING NOTES (PLATFORM READY)
The recipe must output:
- a short “fusion descriptor” line:
  - "Primary A with B flavor in <axis> during <section>"
- tags that communicate fusion without confusion:
  - avoid listing contradictory genres together unless phrased as “influenced by”

---

## 13) HANDOFFS (XREF)
Feeds into:
- `12_TREND_GENRE_ENGINES/03__STYLE_FINGERPRINT_ENG.md`
- `12_TREND_GENRE_ENGINES/07__PROMPT_COMPILER_ENG.md`
- `12_TREND_GENRE_ENGINES/04__VIRAL_HOOK_BLUEPRINT_ENG.md`

Validated by:
- `50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/08__PROMPT_FIDELITY_VAL.md`
- `50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/05__COLLISION_BLOCKER_VAL.md`

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED

--- END.
