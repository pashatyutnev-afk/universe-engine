# SPC PRO PACK — CASE (GOOD-001) — INPUT+TARGETS+INTELLIGIBILITY PASS ANCHOR (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/06__CASE_LIBRARY/01__CASE__GOOD_001.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC
PACK_CLASS: SPC_PRO_PACK
DOMAIN: SOUND_MUSIC
DOC_TYPE: CASE
LEVEL: L3
STATUS: DRAFT
LOCK: FIXED
VERSION: 0.1.0
UID: UE.KB.SPC.PACK.VOCAL_DIRECTOR.CASE.GOOD.001.DRAFT.001
OWNER: SYSTEM
ROLE: GOOD case anchor for calibrating G1 INPUT READINESS, G2 MUST-HEAR TARGETS, and G3 INTELLIGIBILITY checklist correctness.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created GOOD-001 anchor case: minimum inputs present, must-hear targets prioritized, intelligibility gates are explicit and testable."
- REASON: "Pack needs a PASS reference for the first three core gates (G1–G3)."
- IMPACT: "Enables deterministic PASS threshold and faster diagnosis for missing/weak target definitions."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.PACK.VOCAL_DIRECTOR.CASE.GOOD001.001

---

## 0) CASE_RECORD
CASE_RECORD:
- CASE_ID: GOOD-001
- TYPE: GOOD
- CONTEXT:
  - format: full song (~3 min)
  - language: RU
  - vocal_mode: mixed (rap verse + melodic chorus)
  - tempo_feel: 94 bpm / half-time stomp
  - delivery_character: clean-aggressive, consonant-forward on hook words
  - note: This is a “clarity-first” anchor; not an extreme performance case.

---

## 1) INPUTS (MINIMAL)
### 1.1 Lyric excerpt (hook + 1 verse fragment)
[Verse fragment]
Экран моргает — и город завис,
Шум в проводах режет мысль на куски.

[Chorus / Hook]
Я вижу маршрут — меня не согнут.
Я возвращаюсь к своему.

### 1.2 Structure labels (minimal)
STRUCTURE:
- Intro
- Verse 1
- Chorus 1 (HOOK)
- Verse 2
- Chorus 2 (HOOK)
- Bridge
- Final Chorus (HOOK)
- Outro

### 1.3 MUST-HEAR targets (P0)
MUST_HEAR_WORDS:
- P0: маршрут, согнут, возвращаюсь, своему
- P1: город, шум, мысль
- P2: (optional) моргает, куски

MUST_HEAR_PHRASES:
- P0: "я вижу маршрут", "я возвращаюсь к своему"
- P1: (N/A)

PRONUNCIATION_RISK_NOTES:
- item: "маршрут"
  - risk: stress/attack blur on fast delivery
  - fix (non-meaning): slightly separate syllables on hook, land final consonant clearly

---

## 2) BASELINE_DIRECTION_PACK (SHORT)
### 2.1 VOCAL_STYLE_PROFILE (principles)
delivery_principles:
- consonant-forward on P0 phrases (hook first)
- clean-aggressive tone, controlled grit only outside P0 attacks
- medium breathiness; avoid airy blur on hook
- articulation: mixed, but hook phrases = crisp
forbidden_styles:
- mushy vowel-only delivery on chorus
- breath break inside P0 phrases
- heavy distortion over P0 words (masking)

section_intensity_map (0..100):
- Verse: 55
- Chorus: 78
- Bridge: 60
- Final Chorus: 82

### 2.2 PERFORMANCE_ARC_MAP (by section)
- Verse: restrained aggression, clear diction baseline
- Chorus (HOOK): lift + clarity focus; P0 phrases must punch
- Bridge: slight drop for reset; keep clarity, reduce grit
- Final Chorus: strongest lift; keep P0 consonant attacks clean

### 2.3 INTELLIGIBILITY_GATES_CHECKLIST (explicit)
- Gate A (P0 first listen): PASS when all P0 words/phrases are understood on first listen in HOOK
- Gate B (P1 by second listen): PASS when P1 is understandable by second listen
- Gate C (no breath split inside P0): PASS when "я вижу маршрут" and "я возвращаюсь к своему" are uninterrupted
- Gate D (consonant attacks protected): PASS when final consonants on P0 words are not swallowed
- Gate E (chorus clarity >= verse): PASS when chorus is at least as clear as verse despite lift

HARD_FAIL_TRIGGERS:
- HF-1: any P0 word/phrase not understood on first listen in HOOK
- HF-2: breath break inside P0 phrase

### 2.4 BREATH_POLICY (hook protected)
allowed:
- breath before P0 phrases (before "я вижу маршрут", before "я возвращаюсь к своему")
forbidden:
- any breath between "я" and "вижу", between "возвращаюсь" and "к своему"

### 2.5 STACKING_PLAN (high-level)
- Verse: NONE
- Chorus: DOUBLE only on non-P0 tail words (avoid P0 attacks); keep P0 lead solo-clean
- Final Chorus: minimal BACKS on last word of line (outside protected zones)

Protected zones:
- do not stack over: "маршрут", "возвращаюсь", "своему" consonant attacks

### 2.6 TAKE_GOALS + QC (short)
TAKE_GOALS_BY_SECTION:
- Verse:
  - goal: stable diction baseline; keep rhythm tight
- Chorus (HOOK):
  - goal: P0 clarity first; lift without masking
  - goal: land consonants early on P0 attacks
- Final Chorus:
  - goal: biggest lift; keep P0 readable

QC_HARD_FAILS:
- P0 not understood on first listen (HF-1)
- breath split inside P0 phrase (HF-2)
- distortion masks P0 words

QC_SOFT_FAILS:
- minor timing smear not on P0
- slight over-energy in verse

COMP_NOTES:
- do not comp different pronunciations of “маршрут/своему”
- splice only outside P0 phrases

---

## 3) EXPECTED_GATE_RESULTS (UID-ONLY)
VALIDATED_BY:
- UE.KB.SPC.GATE.VOCAL_DIRECTOR.INPUT_READINESS.001
- UE.KB.SPC.GATE.VOCAL_DIRECTOR.MUST_HEAR.001
- UE.KB.SPC.GATE.VOCAL_DIRECTOR.INTELLIGIBILITY.001

EXPECTED_GATE_RESULTS:
- UE.KB.SPC.GATE.VOCAL_DIRECTOR.INPUT_READINESS.001 -> PASS
- UE.KB.SPC.GATE.VOCAL_DIRECTOR.MUST_HEAR.001 -> PASS
- UE.KB.SPC.GATE.VOCAL_DIRECTOR.INTELLIGIBILITY.001 -> PASS

---

## 4) WHY (WHY THIS IS A GOOD ANCHOR)
- Has minimum inputs: lyrics + structure + language → G1 PASS.
- P0 list is short (4 words) + phrases are promoted → G2 PASS.
- Intelligibility checklist is explicit, testable, and includes hard fails → G3 PASS.
- Breath policy protects P0 phrases (no splits) supporting G3 evidence.
- Stacking plan is minimal and defines protected zones (does not contradict intelligibility).

---

## 5) FIX ROUTE (IF IT EVER FAILS)
If a run using this case fails G2:
- apply PB-02 (rebuild P0/P1 + phrases)

If a run fails G3:
- apply PB-03 (repair directives) and/or PB-04 (breath/density) depending on failure type

---

## 6) TRACE
TRACE:
- MEMORY_REUSE: NO
- WEB_LOOKUP_USED: NO

--- END.
