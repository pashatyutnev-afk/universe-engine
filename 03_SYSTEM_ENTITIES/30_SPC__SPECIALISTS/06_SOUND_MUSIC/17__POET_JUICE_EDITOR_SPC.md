# POET JUICE EDITOR — SPC
FILE: 03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/06_SOUND_MUSIC/17__POET_JUICE_EDITOR_SPC.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: SPECIALISTS (SPC)
SPECIALIST_DOMAIN: SOUND_MUSIC
DOC_TYPE: SPECIALIST
LEVEL: L3
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.SPC.SND.POET_JUICE_EDITOR.001
OWNER: SYSTEM
ROLE: Owns “juice quality” for PD lyric pipeline:
selects the strongest PD fragments (quote lines, hook lines, cadence-ready phrases),
tags them for hook/UGC use, enforces fragment-size constraints, and reduces overuse risk.

CHANGE_NOTE:
- DATE: 2026-01-12
- TYPE: MAJOR
- SUMMARY: "Created Poet Juice Editor SPC: responsibilities, interfaces, juice standards, and gates for PD fragment selection."
- REASON: "PD lyrics fail when fragments are too long, not singable, or overused (famous lines)."
- IMPACT: "Stronger hook-ready lyric material + safer PD workflow + less repetition."
- CHANGE_ID: UE.CHG.2026-01-12.SPC.POET_JUICE_EDITOR.001

---

## 0) PURPOSE (LAW)
Poet Juice Editor ensures PD fragments (“juice”) are:
- hook-usable (short, punchy, pronounceable)
- caption/quote-friendly (Q-line quality)
- cadence-aligned to track intent (short-form vs full)
- compliant with PD constraints (no full poem dumps)
- collision-aware (avoid famous/overused lines)

---

## 1) SCOPE
### In scope
- selecting and ranking PD fragments for hooks/quotes/setup/imagery
- fragment tagging (hook/quote/setup/call-response/bridge)
- cadence tagging (SHORT_PUNCH / MEDIUM_FLOW / LONG_LYRICAL)
- fragment-size and safety constraints enforcement (policy-driven)
- quality precheck before mosaic composition

### Out of scope
- composing final mosaic lyrics (Mosaic Editor SPC / Mosaic Composer)
- writing original lyrics outside PD mode (Lyricist / Track Factory mode)
- policy ownership (CTL) and validator enforcement logic (VAL)

---

## 2) INTERFACES (RAW)
### Primary engines consumed
- Poem Fit Scoring ENG  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/13_POET_PD_CORPUS_ENGINES/02__POEM_FIT_SCORING_ENG.md
- Juice Extractor ENG (core)  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/13_POET_PD_CORPUS_ENGINES/03__JUICE_EXTRACTOR_ENG.md
- Excerpt Collision Guard ENG  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/13_POET_PD_CORPUS_ENGINES/05__EXCERPT_COLLISION_ENG.md

### Controllers applied
- Poet PD Policy CTL (fragment limits + strictness)  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/05__POET_PD_POLICY_CTL.md
- Catalog Memory CTL (what was already used)  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/07__CATALOG_MEMORY_CTL.md

### Validators / QA referenced
- PD Only VAL  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/04__PD_ONLY_VAL.md
- Repeat Guard VAL (anti-spam patterns in lyric fragments usage)  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/03__REPEAT_GUARD_VAL.md

---

## 3) KNOWLEDGE BASE (KB) SCOPE
### Inputs
- Track intent (theme/mood/role; short vs full)
- Top PD candidates from Fit Scoring
- PD policy constraints (fragment size, quoting rules)
- Collision memory signals (overused fragments)
- Hook needs (Q-line, chant tag, call/response)

### Outputs
- JUICE QUALITY NOTES:
  - which fragments are hook-grade vs imagery-grade
- CURATED JUICE PACK:
  - top fragments with tags + cadence profiles
- “DO NOT USE” list:
  - blocked/penalized fragments with reasons
- Tokens update:
  - fragment tokens selected/used

### Boundaries
- No external legal claims; only apply PD policy CTL.
- No full poem dumps; fragments-only.

RAW references: (see INTERFACES section)

---

## 4) OUTPUTS (MANDATORY)
### 4.1 CURATED JUICE PACK (CJP)
- TOP_FRAGMENTS (ranked 6–20)
- TAGS per fragment:
  - Q_LINE / HOOK_LINE / SETUP_LINE / IMAGERY_KERNEL / CALL / RESPONSE / BRIDGE
- CADENCE tag:
  - SHORT_PUNCH / MEDIUM_FLOW / LONG_LYRICAL
- USAGE_HINT:
  - hook / verse / clip window alignment
- RISK_NOTES:
  - famous-line risk
  - collision risk

### 4.2 DO-NOT-USE LIST (DNU)
- fragment token/id + reason (too long / off-theme / overused / unclear)

---

## 5) QUALITY STANDARDS (JUICE RULES)
A fragment is “hook-grade” only if:
- short enough to sing cleanly
- has a clear rhythmic bite (cadence)
- can be repeated without sounding like spam (variation possible)
- is intelligible in RU (if RU mode)

A fragment is “quote-grade” (Q-line) only if:
- can be captioned as-is
- emotionally pointed or memetic
- not a well-worn famous line (unless policy allows; usually avoid)

---

## 6) PROCESS (OPERATIONAL)
1) Load PD policy constraints (fragment size, strictness).
2) Load collision memory scope (group default).
3) Review Top-K candidates from Fit Scoring.
4) Curate fragments from Juice Extractor output:
   - keep hook-grade and quote-grade items
   - balance with imagery kernels for verses
5) Run collision guard check (tokens):
   - if WARN/BLOCK → substitute fragments and recheck
6) Output Curated Juice Pack + Do-Not-Use list + token update notes.

---

## 7) GATES (PASS/FAIL)
PASS when:
- at least 1 strong Q-line exists (lyrical mode)
- hook-grade fragments are short and cadence-ready
- fragments comply with PD policy limits (no dumps)
- collision guard result is PASS (or manageable WARN with substitutions)

FAIL when:
- fragments are long/unsingable
- Q-line is weak or unclear
- overused/famous lines dominate
- collision guard BLOCK triggers

---

## 8) SPC PEER ROLES (NON-ENG)
Works with:
- Mosaic Editor SPC  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/06_SOUND_MUSIC/18__MOSAIC_EDITOR_SPC.md
- Prompt Architect SPC  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/06_SOUND_MUSIC/12__PROMPT_ARCHITECT_SPC.md
- Earworm Director SPC  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/06_SOUND_MUSIC/14__EARWORM_DIRECTOR_SPC.md
- UGC Director SPC  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/06_SOUND_MUSIC/13__UGC_DIRECTOR_SPC.md
- Album Showrunner SPC  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/06_SOUND_MUSIC/19__ALBUM_SHOWRUNNER_SPC.md

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED

--- END.
