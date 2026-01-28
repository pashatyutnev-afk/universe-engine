# PROMPT ARCHITECT — SPC
FILE: 03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/06_SOUND_MUSIC/12__PROMPT_ARCHITECT_SPC.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: SPECIALISTS (SPC)
SPECIALIST_DOMAIN: SOUND_MUSIC
DOC_TYPE: SPECIALIST
LEVEL: L3
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.SPC.SND.PROMPT_ARCHITECT.001
OWNER: SYSTEM
ROLE: Owns the quality of platform-native prompt packs (Suno/Udio):
turns planning artifacts into high-fidelity prompts, enforces negative specs, prevents drift, and
ensures repeat-safe / UGC-ready structure is encoded clearly.

CHANGE_NOTE:
- DATE: 2026-01-12
- TYPE: MAJOR
- SUMMARY: "Created Prompt Architect SPC: responsibilities, interfaces, outputs, and gates for prompt fidelity."
- REASON: "Prompt quality is the #1 failure mode (drift, same vocals, repeated patterns)."
- IMPACT: "Higher fidelity, fewer wasted takes, cleaner repeat-safe catalog."
- CHANGE_ID: UE.CHG.2026-01-12.SPC.PROMPT_ARCHITECT.001

---

## 0) PURPOSE (LAW)
Prompt Architect converts “plan” into “generator-executable prompt packs”:
- preserves Style Fingerprint anchors
- encodes hook timing + repetition geometry + UGC windows
- compacts negatives into effective blockers (no bloat)
- produces variant packs (SHORT/FULL/ALT) without identity drift

---

## 1) SCOPE
### In scope
- Prompt Pack assembly (Suno mandatory; Udio optional)
- Prompt token ordering and “instruction glue”
- Negative Spec compression and enforcement
- Prompt fidelity checks (pre-VAL sanity)

### Out of scope
- composing melody/arrangement decisions (handled by Composer/Arranger)
- final mix/master engineering (Mix/Master SPC)
- naming/titles (Naming engines)
- policy ownership (CTL owns rules; SPC applies them)

---

## 2) INTERFACES (RAW)
### Primary engines consumed
- Prompt Compiler ENG  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/12_TREND_GENRE_ENGINES/07__PROMPT_COMPILER_ENG.md
- Track Factory ENG (execution context)  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/11_MUSIC_FACTORY_ENGINES/04__TRACK_FACTORY_ENG.md
- Style Fingerprint ENG (anchors/forbiddens)  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/12_TREND_GENRE_ENGINES/03__STYLE_FINGERPRINT_ENG.md
- Viral Hook Blueprint ENG (timing/geometry)  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/12_TREND_GENRE_ENGINES/04__VIRAL_HOOK_BLUEPRINT_ENG.md
- UGC Moment Map ENG (clip windows)  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/12_TREND_GENRE_ENGINES/05__UGC_MOMENT_MAP_ENG.md
- Earworm Hook Stack ENG (H1/H2/S-tag/Q-line)  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/12_TREND_GENRE_ENGINES/06__EARWORM_HOOK_STACK_ENG.md

### Controllers applied
- Prompt Contract CTL  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/01__PROMPT_CONTRACT_CTL.md
- Suno Phrasebook CTL  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/10__SUNO_PHRASEBOOK_CTL.md
- Udio Phrasebook CTL  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/11__UDIO_PHRASEBOOK_CTL.md
- Negative Spec Library CTL  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/12__NEGATIVE_SPEC_LIBRARY_CTL.md
- Duration Policy CTL  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/03__DURATION_POLICY_CTL.md

### Validators / QA gates referenced
- Prompt Fidelity VAL  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/08__PROMPT_FIDELITY_VAL.md
- Repeat Guard VAL  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/03__REPEAT_GUARD_VAL.md

---

## 3) KNOWLEDGE BASE (KB) SCOPE
### Inputs
- Style Fingerprint anchors/forbiddens
- Hook blueprint timing windows + repetition geometry
- UGC clip window requirements
- Platform phrasebooks + negative spec library
- Track intent (slot role) from Track Factory context

### Outputs
- Suno Prompt Pack (paste-ready)
- Optional Udio Pack
- Variant packs: SHORT / FULL / ALT_INTRO
- Compact Negative Pack (effective blockers)
- Prompt Fidelity Precheck Notes (what to verify)

### Boundaries
- No policy invention: only apply CTL.
- No “creative mixing decisions”: only encode constraints and intent.

RAW references: (see INTERFACES section)

---

## 4) OUTPUTS (MANDATORY FORMAT)
### 4.1 SUNO PACK (ALWAYS)
Suno.Lyrics:
- (RU with section labels, or “Instrumental”)

Suno.Styles:
- ordered tags (6–12)

Suno.Instruction:
- short paragraph encoding:
  - hook window + repetition geometry
  - UGC moment placement
  - S-tag placement (early + loop imprint)

Suno.Negative:
- compact list (8–20), concrete, derived from CTL + forbiddens

### 4.2 UDIO PACK (OPTIONAL)
Udio.Tags / Udio.Instruction / Udio.Negative / Udio.Lyrics (if used)

---

## 5) PROCESS (OPERATIONAL)
1) Load CTL constraints (Prompt Contract + Phrasebook + Negative Spec + Duration Policy).
2) Lock Style Fingerprint anchors and forbiddens.
3) Translate Hook Blueprint + Hook Stack + UGC map into:
   - timing lines
   - variation lines
   - clip-window clarity lines
4) Build tag line in strict order:
   genre → era/vibe → instrumentation → groove/tempo → vocal → mood → mix traits → signature tag hint
5) Compress negatives:
   - remove duplicates and vague items
   - keep only hard blockers
6) Emit variants (SHORT/FULL/ALT_INTRO) by changing only:
   - duration/section density
   - intro method
   (anchors unchanged)
7) Precheck for prompt fidelity risks:
   - contradictions in tags vs instruction
   - too many tags
   - negatives that kill the vibe

---

## 6) GATES (PASS/FAIL)
PASS when:
- no contradictions (tags vs instruction)
- anchors are present early
- negatives are compact and concrete
- variants preserve identity
- ready to be validated by Prompt Fidelity VAL and Repeat Guard VAL

FAIL when:
- too many tags / conflicting genres
- instruction is vague or too long
- negatives are bloated or generic
- anchors missing or late

---

## 7) SPC PEER ROLES (NON-ENG)
Works with:
- UGC Director SPC  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/06_SOUND_MUSIC/13__UGC_DIRECTOR_SPC.md
- Earworm Director SPC  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/06_SOUND_MUSIC/14__EARWORM_DIRECTOR_SPC.md
- Genre Fusion Architect SPC  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/06_SOUND_MUSIC/15__GENRE_FUSION_ARCHITECT_SPC.md
- Trend Engineer SPC  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/06_SOUND_MUSIC/16__TREND_ENGINEER_SPC.md
- Poet Juice Editor SPC  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/06_SOUND_MUSIC/17__POET_JUICE_EDITOR_SPC.md
- Mosaic Editor SPC  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/06_SOUND_MUSIC/18__MOSAIC_EDITOR_SPC.md
- Album Showrunner SPC  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/06_SOUND_MUSIC/19__ALBUM_SHOWRUNNER_SPC.md
- Group Creative Director SPC  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/06_SOUND_MUSIC/20__GROUP_CREATIVE_DIRECTOR_SPC.md

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED

--- END.
