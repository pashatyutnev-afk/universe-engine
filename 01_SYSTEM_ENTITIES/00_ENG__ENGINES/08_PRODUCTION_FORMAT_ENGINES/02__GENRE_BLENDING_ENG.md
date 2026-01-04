# 🧬 GENRE BLENDING ENGINE
## Canonical Engine Specification  
**LEVEL: L3 · PRODUCTION FORMAT ENGINE · BLEND CONTROL · MACHINE-GRADE**

---

## 0. CANONICAL STATUS

- ENGINE_FILE: 02__GENRE_BLENDING_ENG.md
- ENGINE_ID: L3-PROD-GENRE-BLENDING-ENGINE-002
- UID: UE.ENT.ENG.PROD.GENRE_BLENDING
- NAME: Genre Blending Engine
- CLASS: Production Format Engine
- LEVEL: L3
- STATUS: FINAL
- FAILURE_MODE: fail-closed (blend integrity)
- EDITABLE: true

### ABSOLUTE RULE
> Blending is controlled dominance, not chaos. If dominance is unclear, tone collapses.

---

## 1. PURPOSE

Genre Blending Engine defines how multiple genres coexist:
- dominance rules (primary remains primary)
- blend ratios per arc/sequence
- obligation merging without overload
- collision resolution (humor vs dread, romance vs horror, etc.)
- “blend gates” to prevent tonal whiplash

It produces:
- **GENRE_BLEND_PROFILE**
- blend matrix (compatibility map)
- blending schedule (where subgenre rises/falls)
- repair instructions for collisions

This engine prevents “two movies fighting inside one”.

---

## 2. RESPONSIBILITY SCOPE

### IN-SCOPE (ALLOWED)
- Combine primary genre with 1–2 blend genres (bounded)
- Define dominance and ratio by windows
- Merge obligations and forbidden moves
- Define collision rules and transition bridges
- Define blend-safe palettes (what elements can mix)
- Validate blending respects Tone & Mood and platform constraints
- Emit blend profile for format adaptation and scene engines

### OUT-OF-SCOPE (FORBIDDEN)
- Declaring the primary genre (Genre Engine owns it)
- Plot decisions
- Canon authority decisions
- Writing prose/scripts

---

## 3. BLEND MODEL

### 3.1 Output — GENRE_BLEND_PROFILE (required fields)
- `gbp_id`
- `primary_genre_ref` (required)
- `blend_genres` (1–2 max)
- `dominance_rules` (required)
- `blend_ratios_by_window` (required)
- `merged_obligations` (required)
- `merged_forbidden_moves` (required)
- `collision_rules` (required)
- `transition_bridges` (required)
- `blend_gates` (hard rules)
- `integrity_report` (issues + fixes)
- `trace_id` (optional)

Missing any required field → REJECT.

### 3.2 Dominance Rule (required fields)
- `dr_id`
- `statement` (one sentence: who dominates, when)
- `enforcement` (how to keep dominance)
- `exceptions` (optional, bounded)
- `notes`

### 3.3 Ratio Window (required fields)
- `window_id`
- `time_ref`
- `ratio` (map: primary + blend genres sum = 1.0)
- `allowed_palettes` (list)
- `forbidden_palettes` (list)
- `notes`

If ratio sum != 1.0 (±0.01) → INVALID.

### 3.4 Transition Bridge (required fields)
- `tb_id`
- `from_genre_state` (e.g., THRILLER-heavy)
- `to_genre_state` (e.g., ROMANCE-heavy)
- `bridge_method` (beat/device)
- `min_window` (where it occurs)
- `notes`

---

## 4. COMPATIBILITY MATRIX (STANDARD BASE)

This engine uses a baseline compatibility map (editable by system):
- HIGH COMPAT:
  - SCI_FI + THRILLER
  - FANTASY + EPIC
  - MYSTERY + NOIR
  - DRAMA + ROMANCE
  - ACTION + ADVENTURE
- MEDIUM COMPAT (needs bridges):
  - COMEDY + HORROR (dark humor rules)
  - ROMANCE + THRILLER (stakes gating)
  - SCI_FI + MYTHIC (mythic framing gate)
- LOW COMPAT (strict gates):
  - COMEDY + GRIEF-heavy TRAGEDY (requires explicit tragicomedy contract)
  - HORROR + PLAYFUL (requires “camp” contract)
  - NOIR + EPIC (requires dominance clarity and voice constraints)

If blend is LOW COMPAT and no bridges/gates → INVALID.

---

## 5. BLEND GATES (HARD)

- Primary genre remains dominant overall:
  - across ARC total ratio primary ≥ 0.55 unless explicitly declared “hybrid primary” mode (rare).
- Max blend genres: 2.
- Obligations budget:
  - merged obligations max 10 per arc (else checklist overload).
- Collision pairs must have explicit rules:
  - humor vs dread
  - romance vs horror
  - epic awe vs noir cynicism
- Transition bridges required when ratio shifts > 0.25 between adjacent windows.

---

## 6. INPUT ARTIFACTS

### 6.1 INPUT — GENRE_BLEND_REQUEST
**REQUIRED FIELDS**
- `gb_req_id`
- `timestamp`
- `genre_profile_ref` (required)
- `tone_profile_ref` (required)
- `mood_curve_ref` (recommended)
- `platform_constraints_ref` (required)
- `format_target_ref` (optional)
- `trace_id` (optional)

Missing required fields → REJECT.

---

## 7. OUTPUT ARTIFACTS

### 7.1 OUTPUT — GENRE_BLEND_PROFILE
(see model above)

### 7.2 OUTPUT — GENRE_BLEND_VERDICT
- `gb_req_id`
- `verdict` = VALID | INVALID | PARTIAL
- `issues` (list)
- `repair_suggestions` (list)
- `severity` = LOW | MEDIUM | HIGH | CRITICAL

---

## 8. CORE OPERATIONS

- OP_01: INGEST_GENRE_TONE_PLATFORM_CONSTRAINTS
- OP_02: SELECT_BLEND_GENRES (1–2)
- OP_03: CHECK_COMPATIBILITY_MATRIX (baseline + constraints)
- OP_04: DEFINE_DOMINANCE_RULES
- OP_05: BUILD_BLEND_RATIOS_BY_WINDOW (sum=1.0)
- OP_06: MERGE_OBLIGATIONS_AND_FORBIDDEN_MOVES (budgeted)
- OP_07: DEFINE_COLLISION_RULES (pairs)
- OP_08: DEFINE_TRANSITION_BRIDGES (ratio shifts)
- OP_09: BUILD_BLEND_GATES + VALIDATION
- OP_10: EMIT_GENRE_BLEND_PROFILE

---

## 9. COLLISION RULES (STANDARD PAIRS)

### 9.1 Humor vs Dread
- humor allowed only in recovery windows
- humor must be character-based, not stakes-undermining
- after humor beat, return to dread via bridge cue

### 9.2 Romance vs Horror
- romance scenes must not nullify threat layer
- horror spikes require aftermath window; romance can act as recovery only if earned

### 9.3 Epic Awe vs Noir Cynicism
- voice_distance and narration stance must be stable
- noir cynicism cannot erase epic promise; epic cannot sanitize noir consequences

---

## 10. FAILURE CONDITIONS (FAIL-CLOSED)

CRITICAL:
- more than 2 blend genres
- dominance undefined
- ratio sums invalid
- low-compat blend without gates/bridges
- obligations overload with no pruning plan
- tonal collisions with no rules

Reaction:
- Verdict INVALID (CRITICAL)
- Emit repair plan:
  - reduce blends
  - define dominance
  - rebuild ratios with bridges
  - prune obligations
  - add collision rules

---

## 11. TRACE RULES

- trace_id optional unless pipeline requires traced execution
- if present, propagate into format adaptation and packaging engines

---

## 12. NON-GOALS
- Does not choose primary genre
- Does not write scenes
- Does not set canon

---

## 13. FINAL STATEMENT

Blending is ratio + rules + bridges.
Without all three, you don’t blend — you crash.

---

**STATUS:** Genre Blending Engine v1.0  
**REALM:** ACTIVE
