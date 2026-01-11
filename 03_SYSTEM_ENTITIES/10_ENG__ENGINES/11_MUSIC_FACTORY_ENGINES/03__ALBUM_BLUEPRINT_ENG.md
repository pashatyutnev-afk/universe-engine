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
VERSION: 1.0.0
UID: UE.ENG.MF.ALBUM_BLUEPRINT.001
OWNER: SYSTEM
ROLE: Designs a deterministic album blueprint (concept + arc + track roles + sequencing + duration targets) that maximizes audience capture and prevents internal repetition.

CHANGE_NOTE:
- DATE: 2026-01-11
- TYPE: MAJOR
- SUMMARY: "Defined Album Blueprint Engine: album concept, arc, track map, roles, durations, variants, and anti-repeat structure."
- REASON: "Without a blueprint, tracks become random and inconsistent; album must be engineered for retention and virality."
- IMPACT: "Albums become reproducible systems with planned hooks, contrasts, and platform variants."
- CHANGE_ID: UE.CHG.2026-01-11.ENG.MF.ALBUM_BLUEPRINT.001

---

## 0) PURPOSE
This engine creates the **Album Blueprint** that drives track creation:
- album identity (concept + promise + emotional arc)
- tracklist skeleton (roles, contrast, pacing)
- UGC/viral moment placements as a design constraint (not luck)
- duration targets per track role and platform
- release variants plan (radio edit / short cut / extended / instrumental etc.)
- uniqueness guardrails (avoid same hook shape across tracks)

Blueprint is the “album constitution”.

---

## 1) INPUTS (CONSUMES)
- Group DNA Spec (from `01__GROUP_FOUNDATION_ENG`)
- Artist Roster Spec (from `02__ARTIST_FACTORY_ENG`)
- Audience segments (CTL)
- UGC/Viral rules (CTL)
- Duration policy baseline (CTL) — and/or duration strategy engine later
- Optional: poet corpus mode (PD-only)

---

## 2) OUTPUTS (PRODUCES)
Primary:
- **Album Blueprint Spec**

Secondary:
- **Track Map (Album Track Skeleton)** — ordered list with roles + hook intent
- **Album Arc Map** — emotional/energy curve
- **Release Variant Plan** — what versions will exist and why
- **Album Naming Brief** — inputs for naming engines

---

## 3) MINI-CONTRACT (MANDATORY)
CONSUMES: [
  "Group DNA Spec",
  "Artist Roster Spec",
  "Audience Segments CTL",
  "UGC Viral Ruleset CTL",
  "Duration Policy baseline",
  "PD Policy (optional)"
]
PRODUCES: [
  "Album Blueprint Spec",
  "Track Map Skeleton",
  "Album Arc Map",
  "Release Variant Plan",
  "Album Naming Brief"
]
DEPENDS_ON: [
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/04__RELEASE_VARIANTS_CTL.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/03__DURATION_POLICY_CTL.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/03__REPEAT_GUARD_VAL.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/12_TREND_GENRE_ENGINES/05__UGC_MOMENT_MAP_ENG.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/14_NAMING_IDENTITY_ENGINES/01__NAMING_BRIEF_ENG.md"
]
OUTPUT_TARGET: "05_PROJECTS/<MUSIC_PROJECTS>/GROUPS/<GROUP_ID>/ALBUMS/<ALBUM_ID>/"

---

## 4) ALBUM BLUEPRINT MODEL (STANDARD)
Album blueprint must include:

### A) Album Identity
- ALBUM_ID
- ALBUM_PROMISE (1 sentence)
- CONCEPT (2–5 lines)
- PRIMARY EMOTION (e.g., triumph / nostalgia / rage / sacred calm)
- COLOR PRINCIPLES (contrast principles; no fixed palette)

### B) Audience Target
- PRIMARY SEGMENT
- SECONDARY SEGMENTS
- “Why this album wins for them” (bullets)

### C) Arc Map
- ENERGY CURVE (intro → peak → release)
- EMOTIONAL ARC (themes per act)

### D) Track Map (ordered)
For each track slot:
- TRACK_ROLE (hook single / story core / contrast / interlude / finale)
- HOOK_INTENT (what must stick)
- UGC_MOMENT (yes/no + where)
- LYRICS_MODE (PD_ONLY / PD_PLUS_PATCHES / ORIGINAL)
- DURATION_TARGET (range)
- LEAD_PERFORMER (persona id)
- MAIN_TEXTURE (persona id)
- “Do/Don’t” quick rules

### E) Release Variant Plan
- For each track role define required versions:
  - SHORT CUT (UGC)
  - MAIN RELEASE
  - ALT (instrumental / acoustic / live-sim)
  - OPTIONAL EXTENDED (if style allows)

### F) Anti-repeat plan
- “hook shapes” must vary across track roles
- timbre rotation plan (who leads which tracks)
- lyric topic rotation plan

---

## 5) WORKFLOW (OPERATIONAL STEPS)
1) **Choose album size**
   - Default: 8–12 tracks (depending on strategy)
   - Rule: blueprint must specify why this size fits the audience.

2) **Define album promise**
   - One sentence: “This album gives you X feeling via Y sound.”

3) **Design arc**
   - 3-act or 4-block structure:
     - Setup → Lift → Peak → Afterglow
   - Place peak track(s) intentionally.

4) **Build track roles distribution**
   - Minimum required roles in any album:
     - 1–2 Hook Singles (viral core)
     - 1 Story Core track (meaning depth)
     - 1 Contrast track (tempo/mood flip)
     - 1 Finale (resolution + memory)
   - Optional:
     - Interlude (only if it serves arc and keeps retention)

5) **Assign performers + texture rotation**
   - Rotate lead persona across tracks to avoid sameness.
   - Ensure instruments have moments of ownership.

6) **UGC moment mapping**
   - For at least 2 tracks, define explicit UGC moments:
     - “hook phrase” + “gesture rhythm” + “loop window”
   - Use UGC moment map engine output patterns.

7) **Duration targets**
   - Set duration ranges per role (actual policy enforced later by duration engine).
   - Prevent chaos by locking a target window now.

8) **Release variants**
   - Use `RELEASE_VARIANTS_CTL` to decide required variants.
   - Mark which tracks get short cut vs extended.

9) **Anti-repeat rules**
   - Ensure no two tracks share:
     - same hook placement pattern
     - same primary timbre + groove combo
     - same lyrical “topic frame”

---

## 6) DECISION RULES (FACTORY LOGIC)
Hard rules:
- Album must have a **planned contrast** every 2–3 tracks (energy/mood/timbre).
- At least 2 tracks must be designed to be **UGC-ready** (explicit loop windows).
- Hook singles must:
  - introduce recognizable motif early
  - repeat a core phrase or motif with controlled variation
- Finale must reintroduce at least one motif from earlier track(s) for memory glue.
- If PD lyrics mode enabled:
  - every track must specify PD source strategy (PD_ONLY / PD_PLUS_PATCHES).

---

## 7) FAILURE MODES & FIXES
1) **Album feels like random playlist**
- Fix: strengthen album promise + arc + enforce role distribution.

2) **Tracks too similar**
- Fix: rotate lead personas + change groove/timbre plan + enforce anti-repeat patterns.

3) **Too many “filler” tracks**
- Fix: reduce track count, replace with stronger contrast roles or remove interludes.

4) **UGC moments missing**
- Fix: add explicit UGC windows + hook phrases.

Escalate to:
- `50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/03__REPEAT_GUARD_VAL.md`
- `60_QA__QUALITY/10_MUSIC_QA/06__HOOK_PANEL_QA.md`

---

## 8) HANDOFFS (XREF)
NEXT ORC:
- `20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/02__ALBUM_TO_TRACK_ORC.md`

NEXT ENG:
- `11_MUSIC_FACTORY_ENGINES/04__TRACK_FACTORY_ENG.md`
- `11_MUSIC_FACTORY_ENGINES/05__DURATION_STRATEGY_ENG.md`
- Naming engines:
  - `14_NAMING_IDENTITY_ENGINES/*`

REQUIRED CTL:
- `03__DURATION_POLICY_CTL`
- `04__RELEASE_VARIANTS_CTL`
- `08__AUDIENCE_SEGMENTS_CTL`
- `02__UGC_VIRAL_RULESET_CTL`

REQUIRED VAL/QA:
- `02__UGC_READY_VAL`
- `03__REPEAT_GUARD_VAL`
- `06__HOOK_PANEL_QA`
- `07__CATALOG_DIFFERENTIATION_QA`

---

## 9) OUTPUT PACK (MANDATORY LIST)
1) Album Blueprint Spec
2) Track Map Skeleton (ordered)
3) Album Arc Map
4) Release Variant Plan
5) Album Naming Brief

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED

--- END.
