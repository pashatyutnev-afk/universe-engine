# MOSAIC EDITOR — SPC
FILE: 03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/06_SOUND_MUSIC/18__MOSAIC_EDITOR_SPC.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: SPECIALISTS (SPC)
SPECIALIST_DOMAIN: SOUND_MUSIC
DOC_TYPE: SPECIALIST
LEVEL: L3
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.SPC.SND.MOSAIC_EDITOR.001
OWNER: SYSTEM
ROLE: Owns coherence and singability of PD lyric mosaics:
turns curated juice fragments into a coherent, hook-ready lyric draft with section labels,
enforces repeat-safe chorus variation, ensures Q-line placement near UGC windows,
and keeps PD safety (fragments-only, no poem dumps) with collision awareness.

CHANGE_NOTE:
- DATE: 2026-01-12
- TYPE: MAJOR
- SUMMARY: "Created Mosaic Editor SPC: responsibilities, interfaces, outputs, and gates for PD mosaic lyric coherence and UGC-ready placement."
- REASON: "PD mosaics fail when they sound like random collage, are unsingable, or reuse overused lines."
- IMPACT: "Coherent viral-ready lyrics with safer PD workflow and better hook density."
- CHANGE_ID: UE.CHG.2026-01-12.SPC.MOSAIC_EDITOR.001

---

## 0) PURPOSE (LAW)
Mosaic Editor ensures the final lyric mosaic is:
- coherent (single voice/tone)
- singable (short, cadence-ready lines where needed)
- structured (Verse/Chorus/Bridge labels)
- repeat-safe (chorus repeat must vary at least 1 knob)
- UGC-aligned (Q-line placed near primary clip window)
- collision-aware (avoid blocked/overused fragments)

---

## 1) SCOPE
### In scope
- assembling and editing mosaic draft from curated fragments
- enforcing structure templates (short/full/call-response)
- chorus repeat variation rules
- Q-line clarity and placement near UGC moments
- connector minimization (no rewriting into a new poem; minimal glue)
- precheck against excerpt collision findings

### Out of scope
- selecting PD candidates (Fit Scoring / Poet Juice Editor)
- writing original non-PD lyrics (Lyricist / Track Factory open mode)
- policy ownership (CTL) and validator enforcement logic (VAL)

---

## 2) INTERFACES (RAW)
### Primary engines consumed
- Mosaic Composer ENG (core mosaic assembly rules)  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/13_POET_PD_CORPUS_ENGINES/04__MOSAIC_COMPOSER_ENG.md
- Juice Extractor ENG (fragment source)  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/13_POET_PD_CORPUS_ENGINES/03__JUICE_EXTRACTOR_ENG.md
- Excerpt Collision Guard ENG (blocked/penalized tokens)  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/13_POET_PD_CORPUS_ENGINES/05__EXCERPT_COLLISION_ENG.md
- UGC Moment Map ENG (clip windows)  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/12_TREND_GENRE_ENGINES/05__UGC_MOMENT_MAP_ENG.md
- Earworm Hook Stack ENG (Q-line / hook needs)  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/12_TREND_GENRE_ENGINES/06__EARWORM_HOOK_STACK_ENG.md

### Controllers applied
- Poet PD Policy CTL (fragment size + strictness)  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/05__POET_PD_POLICY_CTL.md
- Catalog Memory CTL (avoid reuse)  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/07__CATALOG_MEMORY_CTL.md
- Duration Policy CTL (short/full density)  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/03__DURATION_POLICY_CTL.md

### Validators / QA referenced
- PD Only VAL  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/04__PD_ONLY_VAL.md
- Repeat Guard VAL (no spam repeats in chorus/phrases)  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/03__REPEAT_GUARD_VAL.md
- UGC Ready VAL (Q-line + clip windows support)  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/02__UGC_READY_VAL.md

---

## 3) KNOWLEDGE BASE (KB) SCOPE
### Inputs
- Curated juice fragments (hook/quote/setup/imagery tags)
- Track intent + duration mode (short/full)
- UGC clip windows and moment types
- Hook needs (Q-line / call-response preference)
- Collision blocklist / penalty list tokens
- PD policy constraints (fragment limits)

### Outputs
- Final Mosaic Lyrics Draft (paste-ready; section-labeled)
- Mosaic Map (which fragments used where + minimal transforms)
- Variation Plan (what changes on chorus repeat)
- Collision Tokens Update (used tokens)

### Boundaries
- No montage decisions (only constraints/risks).
- No full poem reproduction; fragments-only + minimal glue.

RAW references: (see INTERFACES section)

---

## 4) OUTPUTS (MANDATORY)
### 4.1 FINAL MOSAIC LYRICS (PASTE-READY)
- [Verse]
- [Chorus]
- [Verse] (optional)
- [Bridge] (optional)
- [Chorus] (repeat with 1 variation)
- [Outro] (optional)

### 4.2 MOSAIC MAP
- fragment_id/token → section → transform (trim/reorder/link/mirror/variate)

### 4.3 VARIATION PLAN (REPEAT-SAFE)
- which line changes on chorus repeat
- which knob is used (word swap / cadence shift / arrangement cue note)

---

## 5) QUALITY RULES (NON-NEGOTIABLE)
- Chorus length:
  - SHORT mode: 4–6 lines max
  - FULL mode: 6–8 lines max
- Q-line:
  - must be clear, caption-ready
  - must sit near primary clip window (UGC map)
- Repeat-safe:
  - chorus repeat must vary at least 1 line OR 1 microhook tag
- Glue words:
  - minimal; do not rewrite into a new poem (avoid heavy paraphrase)
- Avoid:
  - blocked tokens
  - famous-line overuse
  - tongue-twisters that kill singability

---

## 6) PROCESS (OPERATIONAL)
1) Load PD policy constraints + collision report.
2) Filter out blocked fragments/tokens.
3) Choose structure template (short/full/call-response) based on duration + UGC intent.
4) Build Chorus first:
   - include hook-grade fragment(s)
   - include Q-line in or adjacent to chorus
5) Build Verse(s):
   - use setup + imagery kernels
   - keep tone consistent
6) Optional Bridge:
   - short contrast, still on theme
7) Define chorus repeat variation:
   - swap 1 line or alter ending phrase (repeat-safe)
8) Verify UGC alignment:
   - Q-line near clip window
   - at least one clean cut-friendly line placement
9) Output final mosaic + map + variation plan + tokens update.

---

## 7) GATES (PASS/FAIL)
PASS when:
- structure is clear and labeled
- chorus is hook-ready and not bloated
- Q-line is strong and placed near clip window
- repeat-safe variation exists
- collision guard is PASS (or WARN with substitutions applied)
- PD safety holds (fragments-only; no dumps)

FAIL when:
- collage feel (no coherent voice)
- long unsingable lines dominate chorus
- Q-line weak/unclear
- chorus is copy-paste spam
- blocked/overused fragments present

---

## 8) SPC PEER ROLES (NON-ENG)
Works with:
- Poet Juice Editor SPC  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/06_SOUND_MUSIC/17__POET_JUICE_EDITOR_SPC.md
- Prompt Architect SPC  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/06_SOUND_MUSIC/12__PROMPT_ARCHITECT_SPC.md
- UGC Director SPC  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/06_SOUND_MUSIC/13__UGC_DIRECTOR_SPC.md
- Earworm Director SPC  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/06_SOUND_MUSIC/14__EARWORM_DIRECTOR_SPC.md
- Album Showrunner SPC  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/06_SOUND_MUSIC/19__ALBUM_SHOWRUNNER_SPC.md
- Group Creative Director SPC  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/06_SOUND_MUSIC/20__GROUP_CREATIVE_DIRECTOR_SPC.md

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED

--- END.
