# Novelty Injection Engine — ENGINE
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/11_MUSIC_FACTORY_ENGINES/08__NOVELTY_INJECTION_ENG.md

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
UID: UE.ENG.MF.NOVELTY_INJECTION.001
OWNER: SYSTEM
ROLE: Applies controlled novelty to a track/album slot to avoid collisions and repetition while preserving Group Fingerprint anchors.

Produces a minimal-change plan and updated constraints for the next take.

CHANGE_NOTE:
- DATE: 2026-01-12
- TYPE: MAJOR
- SUMMARY: "Created Novelty Injection: mutation knobs, safe moves, forbidden moves, and retest loop integration with collision/validators."
- REASON: "Scaling many tracks requires deterministic novelty without breaking group identity."
- IMPACT: "Less sameness, higher viral uniqueness, faster iteration after WARN/BLOCK."
- CHANGE_ID: UE.CHG.2026-01-12.ENG.MF.NOVELTY.INJECT.001
- DATE: 2026-01-12
- TYPE: PATCH
- SUMMARY: "Reformatted to multi-line sections for operational readability; no semantic changes."
- REASON: "Compressed formatting is error-prone during edits."
- IMPACT: "Safer copy/paste; easier audits."
- CHANGE_ID: UE.CHG.2026-01-12.ENG.MF.NOVELTY.INJECT.002

---

## 0) PURPOSE (LAW)
Novelty Injection is the **repair engine** after:
- catalog collision WARN/BLOCK
- repeat guard warnings
- “all tracks sound the same” symptoms

It must:
- keep Group DNA + Style Fingerprint anchors intact
- change only what is necessary to break similarity
- output a clear “next take” mutation plan

---

## 1) MINI-CONTRACT (MANDATORY)

CONSUMES: [
  "Collision Report (PASS/WARN/BLOCK details)",
  "Track Intent Brief (slot role + required hooks)",
  "Group DNA + Style Fingerprint (anchors/forbiddens)",
  "Artist Roster Spec (who can own hook/roles)",
  "Negative Spec Library (platform)",
  "Catalog Memory constraints"
]

PRODUCES: [
  "Novelty Injection Plan (single SoT)",
  "Mutation Knob Set (what changes; limited count)",
  "Updated Negative Specs (what to block)",
  "Retest Brief for Track Factory",
  "Take Log Note (delta + reason)"
]

DEPENDS_ON: [
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/11_MUSIC_FACTORY_ENGINES/07__CATALOG_COLLISION_ENG.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/11_MUSIC_FACTORY_ENGINES/04__TRACK_FACTORY_ENG.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/12__NEGATIVE_SPEC_LIBRARY_CTL.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/06__FINGERPRINT_COLLISION_THRESHOLDS_CTL.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/03__REPEAT_GUARD_VAL.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/05__COLLISION_BLOCKER_VAL.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/11_MUSIC_FACTORY_ENGINES/09__TAKE_LOG_ENG.md"
]

OUTPUT_TARGET: "05_PROJECTS//GROUPS//NOVELTY/"

---

## 2) ANCHOR PRESERVATION (ABSOLUTE)
Novelty Injection **must not** break:
- Primary Genre identity (A)
- Style Fingerprint core anchors (2–5)
- Group “signature tag” (S-tag) policy
- vocal language constraint (RU)
- album slot role intent (opener/single/contrast etc.)

If a fix requires breaking anchors → not novelty injection → requires governance/evolution decision.

---

## 3) MUTATION KNOBS (ALLOWED SET)
Novelty is applied via a small set of knobs.
Each run must select **1–3 knobs max**.

### A) Hook Grammar Variant
- change hook entry phrasing, accent rhythm, chant geometry
- keep theme/slogan intent, mutate form

### B) Hook Ownership Swap
- vocal → instrument hook lead, or instrument → vocal
- only within Artist Roster roles

### C) Intro Stamp Mutation (0–10s)
- change the first motif shape or lead timbre
- preserve recognition anchor but alter “surface”

### D) Palette Swap (1 dominant timbre)
- replace one dominant sound with an allowed alternative
- keep the rest stable

### E) Groove Micro-Shift
- hi-hat/snare/bounce behavior changes
- keep tempo band stable

### F) Structure Micro-Shift
- change one section length or move a drop slightly
- avoid rewriting full structure

### G) Lyric Mosaic Swap (PD mode)
- swap repeated “fat lines”
- change stitch order
- preserve theme and rhyme family

### H) Mix Space Variant (light)
- dry/close ↔ wider/atmo within group mix aesthetic
- do not change mastering “identity”

---

## 4) FORBIDDEN MOVES (STRICT)
- changing primary genre (A) to another genre
- adding random instruments not in palette
- changing language away from RU (unless explicitly planned)
- rewriting album arc role (opener becomes ballad etc.)
- injecting too many changes at once (more than 3 knobs)

---

## 5) NOVELTY INJECTION PLAN (SINGLE SoT)
Plan must be short and executable.

### Header
- GROUP_UID / ALBUM_UID / TRACK_UID / SLOT_ID
- INPUT: collision type(s)
- TARGET: pass thresholds + preserve anchors

### Anchors (locked)
- CORE_ANCHORS:
- FORBIDDENS:

### Selected knobs (1–3)
1) KNOB:
- WHAT CHANGES:
- WHY:
- HOW TO VERIFY:

2) KNOB:
- WHAT CHANGES:
- WHY:
- HOW TO VERIFY:

### Negative specs update
- Add “avoid X” rules (concrete)
- Add “do not repeat Y” (from nearest neighbors)

### Retest instructions
- Number of takes to run:
- What to listen for in first 10s:
- Hook window requirement:
- Pass conditions:

---

## 6) PROCESS (OPERATIONAL LOOP)
1) Read Collision Report
- identify dominant collision type(s): HOOK/INTRO/STRUCTURE/TIMBRE/GROOVE/LYRICS

2) Lock anchors
- list 2–5 anchors
- list forbiddens

3) Choose minimal knobs
- if HOOK collision → choose A or B first
- if INTRO collision → choose C first
- if TIMBRE collision → choose D first
- if GROOVE collision → choose E first
- if STRUCTURE collision → choose F first
- if LYRICS collision → choose G first

4) Update negative specs
- concrete “avoid” lines; no vague text

5) Output Retest Brief
- go back to Track Factory with mutation plan

6) Log changes
- Take Log must record:
  - delta knobs
  - reason
  - result (pass/warn/block)

---

## 7) DECISION OUTCOMES

### PASS TARGET
- collision types below WARN threshold
- repeat guard passes
- prompt fidelity stays high (no random drift)

### WARN TARGET
- still borderline but improved
- allow 1 more novelty injection run with 1 knob only

### FAIL (BLOCK)
If still blocked after 2 novelty cycles:
- force a new slot concept (album blueprint adjustment)
OR
- change hook blueprint (not just surface)

---

## 8) FAILURE MODES & FIXES
1) Too much novelty → group identity breaks
- Fix: reduce knobs to 1; re-lock anchors.

2) Too little novelty → still same song
- Fix: switch knob category (e.g. from palette to hook grammar).

3) AI drifts into random style
- Fix: tighten negative specs + reinforce fingerprint anchors.

4) Lyrics keep repeating the same “fat lines”
- Fix: increase PD excerpt pool; swap mosaic stitch.

---

## 9) HANDOFFS (XREF)

Returns to:
- `11_MUSIC_FACTORY_ENGINES/04__TRACK_FACTORY_ENG.md` (retest execution)

Validated by:
- `50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/03__REPEAT_GUARD_VAL.md`
- `50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/05__COLLISION_BLOCKER_VAL.md`
- `50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/08__PROMPT_FIDELITY_VAL.md`

Logged in:
- `11_MUSIC_FACTORY_ENGINES/09__TAKE_LOG_ENG.md`

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED

--- END.
