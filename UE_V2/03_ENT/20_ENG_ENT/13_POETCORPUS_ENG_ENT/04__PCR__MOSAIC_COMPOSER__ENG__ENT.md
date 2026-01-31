# Mosaic Composer Engine — ENGINE
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/13_POET_PD_CORPUS_ENGINES/04__MOSAIC_COMPOSER_ENG.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
ENGINE_FAMILY: 13_POET_PD_CORPUS_ENGINES
DOC_TYPE: ENGINE
ENGINE_TYPE: POET_PD_CORPUS
LEVEL: L3
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.ENG.PD.MOSAIC_COMPOSER.001
OWNER: SYSTEM
ROLE: Composes a coherent lyric mosaic from PD “juice” fragments: assembles hook-ready lines,
sets up verses, places quote line near UGC windows, and ensures repeat-safe structure.

Outputs a Mosaic Draft that Track Factory can paste into Suno (with section labels).

CHANGE_NOTE:
- DATE: 2026-01-12
- TYPE: MAJOR
- SUMMARY: "Created Mosaic Composer: structure templates, coherence rules, fragment stitching, and output schema for lyric mosaics."
- REASON: "We need new lyrics from PD fragments without dumping full poems or repeating famous lines."
- IMPACT: "Coherent viral-ready lyrics with PD safety and better hook density."
- CHANGE_ID: UE.CHG.2026-01-12.ENG.PD.MOSAIC_COMPOSER.001

---

## 0) PURPOSE (LAW)
This engine answers:
**“How do we assemble extracted PD fragments into a usable song lyric?”**

It must:
- create a coherent voice/tone across fragments
- produce a hook + setup + (optional) bridge
- place Q-line near UGC moment window
- label sections for prompt packs (Verse/Chorus/Bridge)
- avoid full poem reproduction: mosaic is a new arrangement of fragments

---

## 1) INPUTS (CONSUMES)
- Juice Pack (ranked fragments + tags)
- Track Intent Brief (role + mood + theme)
- Hook Stack needs (H1/Q-line placement)
- Viral Hook Blueprint timing plan (where hook lands)
- UGC Moment Map (clip windows)
- Duration Strategy (short/full)
- Style Fingerprint forbiddens (avoid tone drift)
- PD Policy CTL (fragment size limits)
- Excerpt Collision memory (blocked fragments/tokens)

---

## 2) OUTPUTS (PRODUCES)
Primary:
- MOSAIC_DRAFT (MD): structured lyric draft with sections

Secondary:
- MOSAIC_MAP:
  - which fragments were used where
  - what was altered (reorder/trim)
- COLLISION TOKENS UPDATE:
  - tokens of used fragments for collision guard
- “CUT LIST”:
  - fragments considered but rejected

---

## 3) MINI-CONTRACT (MANDATORY)
CONSUMES: [
  "Juice Pack",
  "Track Intent Brief",
  "Hook Stack needs",
  "Viral Hook Blueprint",
  "UGC Moment Map",
  "Duration Strategy",
  "Style Fingerprint forbiddens",
  "PD Policy CTL",
  "Excerpt Collision memory (optional)"
]
PRODUCES: [
  "Mosaic Draft (MD)",
  "Mosaic Map",
  "Collision Tokens Update",
  "Cut List"
]
DEPENDS_ON: [
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/13_POET_PD_CORPUS_ENGINES/03__JUICE_EXTRACTOR_ENG.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/12_TREND_GENRE_ENGINES/06__EARWORM_HOOK_STACK_ENG.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/12_TREND_GENRE_ENGINES/04__VIRAL_HOOK_BLUEPRINT_ENG.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/12_TREND_GENRE_ENGINES/05__UGC_MOMENT_MAP_ENG.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/05__POET_PD_POLICY_CTL.md"
]
OUTPUT_TARGET: "05_PROJECTS//PD_CORPUS/MOSAICS/"

---

## 4) MOSAIC DESIGN RULES (ABSOLUTE)
- Use fragments as building blocks; do not output full original poems.
- Keep lines short and singable where possible.
- Preserve theme consistency (Track Intent Brief).
- Q-line must be clear and placed near UGC window.
- Hook must be repeat-safe: allow slight variation between repeats.

---

## 5) STRUCTURE TEMPLATES (STANDARD)
Choose one structure based on Duration Strategy:

### S1 — SHORT (UGC-first)
- [Intro] (optional, 1–2 lines)
- [Chorus] (hook core, 4–6 lines max)
- [Verse] (2–6 lines)
- [Chorus] (hook repeat with 1 small variation)
- [Outro] (1–2 lines, loop-friendly)

### S2 — FULL (song-first)
- [Verse 1]
- [Chorus]
- [Verse 2] (variation)
- [Chorus]
- [Bridge] (optional)
- [Chorus] (final)

### S3 — CALL/RESPONSE (duet-ready)
- [Chorus] split into CALL + RESPONSE lines
- [Verse] minimal
- [Chorus] repeat with swapped ownership hints

---

## 6) STITCHING MODEL (HOW TO COMPOSE)
Mosaic composition uses:
- REORDER: reorder fragments to create narrative arc
- TRIM: trim fragments to hook-friendly length
- LINK: add minimal connector words (if policy allows) to improve flow
- MIRROR: repeat a key phrase as a chant tag (repeat-safe rule applies)
- VARIATE: small change in one line on chorus repeat

Rule:
- connectors must be minimal; primary material stays PD fragments.

---

## 7) PROCEDURE (DETERMINISTIC)
1) Load Juice Pack; remove any blocked fragments (collision memory).
2) Select core hook set:
   - pick 1–2 HOOK_LINE fragments
   - pick 1 Q_LINE fragment
   - pick 1–2 SETUP_LINE fragments
3) Choose structure template (S1/S2/S3) based on Duration Strategy + UGC intent.
4) Compose Chorus:
   - 4–6 lines max (short), 6–8 lines max (full)
   - include Q-line inside or adjacent to chorus
5) Compose Verse(s):
   - pick imagery kernels + setup lines
   - keep consistent tone
6) If Bridge exists:
   - use bridge material fragments, keep it short
7) Compose Outro/Loop:
   - 1–2 lines or a short repeated tag
8) Apply repeat-safe rule:
   - chorus repeat must vary at least 1 line or micro-detail
9) Output Mosaic Draft with section labels.
10) Output Mosaic Map:
   - fragment_id → used_in_section → trim/reorder notes
11) Output tokens update for collision engine.

---

## 8) OUTPUT SCHEMA (MANDATORY)

### MOSAIC_DRAFT (MD)
- TRACK_UID:
- DATE:
- STRUCTURE_TEMPLATE: (S1/S2/S3)
- LYRICS (paste-ready, RU):
  [Verse]
  ...
  [Chorus]
  ...
  [Bridge] (optional)
  ...
  [Chorus] (repeat)
  ...
- Q_LINE:
  - text:
  - placement:
- NOTES:
  - tone/voice notes (1–3 lines)
  - UGC window alignment note

### MOSAIC_MAP
- USED_FRAGMENTS:
  - fragment_id:
    source_candidate_id:
    type_tags:
    used_in_section:
    transforms: (trim/reorder/link/mirror/variate)
- CUT_LIST:
  - fragment_id: reason

### COLLISION TOKENS UPDATE
- TOKENS:
  - list of fragment tokens used (compact)

---

## 9) FAILURE MODES & FIXES
1) Mosaic feels like random collage (no voice)
- Fix: reduce number of sources; enforce single theme; add consistent cadence type.

2) Chorus is too long or not singable
- Fix: replace long lines with SHORT_PUNCH fragments; trim.

3) Q-line not clear or not placed near clip window
- Fix: choose a better Q-line from Juice Pack; reposition.

4) Too close to famous original poem
- Fix: avoid dominant contiguous stanza; mix across sources; change ordering and trimming; run excerpt collision guard.

---

## 10) HANDOFFS (XREF)
Feeds into:
- `11_MUSIC_FACTORY_ENGINES/04__TRACK_FACTORY_ENG.md` (lyrics section for prompt pack)
- `13_POET_PD_CORPUS_ENGINES/05__EXCERPT_COLLISION_ENG.md` (token update + overuse check)

Validated by:
- `50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/04__PD_ONLY_VAL.md`
- `50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/09__CREDITS_RIGHTS_VAL.md`

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED

--- END.
