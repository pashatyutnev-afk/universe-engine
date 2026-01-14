# TOPICS — SOUND & MUSIC (README) (CANON)
FILE: 04_KNOWLEDGE_BASE/10_TOPICS/50_SOUND_MUSIC/00__README__TOPICS_SOUND_MUSIC.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 10_TOPICS / 50_SOUND_MUSIC
DOC_TYPE: README
INDEX_TYPE: REALM_README
LEVEL: L2
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.README.TOPICS.SOUND_MUSIC.001
OWNER: SYSTEM
ROLE: Orientation for SOUND_MUSIC topics scope: what belongs here, how entities use it, and a deterministic roadmap to populate the realm with high-signal music/sound craft modules and QA practices (no navigation authority).

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created SOUND_MUSIC topics realm README: scope boundaries, usage order, and roadmap for composition/arrangement/vocals/mix/master/QA modules."
- REASON: "Entities need a structured sound/music knowledge library to avoid repetition, voice sameness, and inconsistent mix quality."
- IMPACT: "More consistent track quality, clearer prompts, and stronger QA calibration."
- CHANGE_ID: UE.CHG.2026-01-14.KB.TOPICS.SOUND.README.001

---

## 0) PURPOSE (KB)
This realm contains SOUND & MUSIC craft knowledge:
- songwriting structure (verse/chorus/hook)
- genre fingerprinting and arrangement principles
- vocal performance direction (conceptual, not acting coaching)
- sound design language (texture, rhythm, energy)
- mix/master principles and QA (translation, loudness discipline)
- prompt craft for music generation (constraints, negative specs)

Goal:
- produce music outputs that are:
  - catchy (when required)
  - stylistically consistent
  - vocally differentiated
  - mix-competent and replayable

---

## 1) WHAT BELONGS HERE / WHAT DOES NOT
### BELONGS (IN-SCOPE)
- composition: melody/harmony/rhythm basics as craft
- arrangement: energy curve, instrumentation roles
- vocals: voice separation intent, delivery modes, clarity constraints
- mix/master: translation principles, common fails, quick fixes
- sound design: texture language, dynamics, contrast
- QA: hook timing, loopability, recognition, uniqueness, repeat-guard
- prompt craft: constraints, negative specs, contract-like prompts

### DOES NOT BELONG (OUT-OF-SCOPE)
- narrative/scene craft (belongs to 10_NARRATIVE)
- character psychology/lore writing (belongs to 20_CHARACTER)
- cinematography/visual composition (belongs to 40_VISUAL)
- marketing/packaging (belongs to 70_MARKETING)
- governance laws and navigation maps (master index only)

---

## 2) NAVIGATION RULE (STRICT)
- This README is NOT navigation authority.
- KB navigation/existence authority is ONLY:
  - `04_KNOWLEDGE_BASE/00__INDEX__KNOWLEDGE_BASE.md`
- Do not add RAW registries here.

---

## 3) HOW ENTITIES USE SOUND_MUSIC TOPICS (DETERMINISTIC)
Order:
1) Load governance minimum set (no-fantasy, uid-only xref, trace).
2) Identify the music task scope:
   - compose / arrange / prompt / vocals / mix / QA
3) Load minimal required modules:
   - constraints/gates first (if any)
   - then the specific topic module(s)
4) Use exemplars + gates for calibration (if relevant).
5) Output RUN_TRACE (UID-only sources + memory reuse).

---

## 4) FILL PLAN (ROADMAP: WHAT FILES WE MUST CREATE)
Roadmap list (not navigation authority).

### P1 — Core music craft
- SOUND__SONG_STRUCTURE_HOOK_LOGIC
- SOUND__RHYTHM_GROOVE_FOUNDATIONS
- SOUND__MELODY_HOOK_SHAPES
- SOUND__ARRANGEMENT_ROLES_ENERGY_CURVE

### P1 — Vocals (key weakness area)
- SOUND__VOCAL_DIVERSITY_INTENT (distinct voices, delivery modes)
- SOUND__VOCAL_PHRASE_VARIATION (avoid repeated patterns)
- SOUND__RAP_VS_MELODIC_TRANSITION_METHOD

### P1 — Mix/master baseline + QA
- SOUND__MIX_TRANSLATION_PRINCIPLES
- SOUND__MIX_COMMON_FAILS_FAST_FIXES
- SOUND__MASTERING_INTENT_LOUDNESS_DISCIPLINE
- SOUND__QA_GATES_OVERVIEW (hook/loop/recognition/uniqueness)

### P2 — Prompt craft for generators
- SOUND__PROMPT_CONTRACT_PATTERN (positive specs + negatives + constraints)
- SOUND__NEGATIVE_SPEC_LIBRARY (how to block clichés/pattern repeats)
- SOUND__STYLE_FINGERPRINT_CONTROL (consistency without collision)

### P3 — Advanced
- SOUND__GENRE_FUSION_RULES
- SOUND__TEXTURE_SOUND_DESIGN_LIBRARY
- SOUND__ALBUM_COHESION_METHOD

---

## 5) STYLE RULES FOR SOUND_MUSIC MODULES
- Prefer operational guidance:
  - what to control
  - how to test
  - common fails and fixes
- Avoid “taste-only” advice unless tied to measurable-ish gates.
- Keep modules atomic (one purpose per file).
- Always distinguish:
  - composition vs arrangement vs performance vs mix/master vs prompt craft.

---

## 6) HARD FAIL CONDITIONS
FAIL IF:
- realm becomes a second navigation index (RAW registries)
- modules become generic “music theory course” without operational relevance
- invented facts are presented as sourced truth
- outputs claim compliance without trace

---

## 7) RELATED (UID-ONLY)
XREF:
- XREF: UE.KB.RULES.GOV.001 | WHY: governance rules apply everywhere
- XREF: UE.KB.REF.GLOSSARY.AUDIO_MIX_MASTER.001 | WHY: shared vocabulary for mix/master terms
- XREF: UE.KB.POL.EXAMPLE_LIBRARY.081 | WHY: exemplars calibrate QA judgement
- XREF: UE.KB.STD.GATE_DEF.088 | WHY: measurable QA gates for music outputs
- XREF: UE.KB.RULE.SCOPE_BOUNDARIES.076 | WHY: prevents domain mixing

--- END.
