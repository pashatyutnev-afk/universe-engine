# SPC PRO PACK — CASE (GOOD-007) — FULL-STACK READY PACK (G1..G9 PASS) (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/06__CASE_LIBRARY/25__CASE__GOOD_007.md

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
UID: UE.KB.SPC.PACK.VOCAL_DIRECTOR.CASE.GOOD.007.DRAFT.001
OWNER: SYSTEM
ROLE: Full-stack GOOD case anchor representing a “READY” VOCAL_DIRECTOR output pack. Calibrates the complete gate sequence G1..G9 as PASS with explicit evidence artifacts for each gate.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created GOOD-007 full-stack READY case: passes G1..G9 with complete evidence set."
- REASON: "Pack needs a canonical 'what READY looks like' reference to prevent drift and speed audits."
- IMPACT: "Deterministic quality; faster convergence; fewer scope violations."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.PACK.VOCAL_DIRECTOR.CASE.GOOD007.001

---

## 0) CASE_RECORD
CASE_RECORD:
- CASE_ID: GOOD-007
- TYPE: GOOD
- CONTEXT:
  - format: full song (~3 min)
  - language: RU
  - vocal_mode: rap verse + melodic hook
  - tempo_feel: 94 bpm / half-time stomp
  - note: This is the canonical READY reference case.

---

## 1) INPUTS (G1 — READY)
### 1.1 Lyric excerpt (hook + verse fragment)
[Verse fragment]
Я обновлюсь на своих скоростях,
И если опять меня тянет назад — я выберу шаг.

[Chorus / Hook]
Я вижу маршрут — меня не согнут.
Я возвращаюсь к своему.

### 1.2 Structure labels
STRUCTURE:
- Intro
- Verse 1
- Chorus 1 (HOOK)
- Verse 2
- Chorus 2 (HOOK)
- Bridge
- Final Chorus (HOOK)
- Outro

### 1.3 Language
LANGUAGE:
- RU
PRONUNCIATION_RISK_NOTES:
- item: "маршрут"
  - risk: attack blur at lift intensity
  - fix: consonant-forward on hook, stable pronunciation across takes

Evidence:
- LYRIC_DRAFT_PRESENT: YES
- SECTION_STRUCTURE_PRESENT: YES
- LANGUAGE_PRESENT: YES
- HOOK_SECTION_IDENTIFIABLE: YES

---

## 2) MUST-HEAR TARGETS (G2 — READY)
MUST_HEAR_WORDS:
- P0: маршрут, согнут, возвращаюсь, своему
- P1: вижу, шаг
- P2: (optional) скоростях

MUST_HEAR_PHRASES:
- P0: "я вижу маршрут", "я возвращаюсь к своему"
- P1: (N/A)

CLARITY_TARGETS:
- Target A: P0 phrases understood on first listen in chorus/hook
- Target B: No breath split inside P0 phrases

---

## 3) INTELLIGIBILITY (G3 — READY)
INTELLIGIBILITY_GATES_CHECKLIST:
- Gate A (P0 first listen): YES/NO (must be YES for PASS)
- Gate B (P1 by second listen): YES/NO
- Gate C (no breath split inside P0): YES/NO (must be YES)
- Gate D (consonant attacks protected): YES/NO (must be YES)
- Gate E (chorus clarity >= verse): YES/NO

HARD_FAIL_TRIGGERS:
- HF-1: any P0 not understood on first listen in hook
- HF-2: breath split inside P0 phrase
- HF-3: distortion/stacking masks P0 attacks

REPAIR_ROUTE:
- T1/T5 (consonant loss/masking) -> PB-03
- density/breath trap -> PB-04

---

## 4) DELIVERY PROFILE (G4 — READY)
VOCAL_STYLE_PROFILE:
delivery_principles (<=6):
1) Character: clean-aggressive, controlled
2) Hook articulation: consonant-forward on P0 attacks
3) Breathiness: medium-low on hook (avoid airy blur)
4) Timing: tight on hook phrases; verse slightly looser
5) Dynamics: chorus lift via energy, not via masking grit
6) Consistency: same pronunciation on P0 across takes

forbidden_styles:
- heavy distortion on P0 words
- breath break inside P0 phrases
- vowel-only chorus (swallowed consonants)
- character switching between takes (clean ↔ raspy) without arc plan
- stacking over P0 consonant attacks

COHERENCE_CHECK:
- contradictions_found: NO
- executability_ok: YES

---

## 5) ARC / CONTRAST (G5 — READY)
PERFORMANCE_ARC_MAP:
- Verse: baseline intensity, story clarity
- Chorus (HOOK): lift + clarity focus
- Bridge: reset contrast
- Final Chorus: biggest lift

CONTRAST_LEVERS (2):
- L1 ENERGY/INTENSITY (0..100):
  - Verse 55 / Chorus 78 / Bridge 60 / Final 82
- L3 ARTICULATION FOCUS:
  - Verse mixed / Chorus consonant-forward on P0 / Bridge softer / Final strong

QC_ARC_CHECKS:
- chorus_lift_present: YES
- lever_count_ok (<=3): YES
- intelligibility_preserved: YES

---

## 6) BREATH / SINGABILITY (G6 — READY)
MUST_HEAR_PROTECTION_RULES:
- never split P0 phrases:
  - "я вижу маршрут"
  - "я возвращаюсь к своему"

BREATH_POLICY:
allowed:
- breath before each P0 phrase
- breath between lines
forbidden:
- any breath inside P0 phrases
- any breath between "не" and "согнут"

DENSITY_SCAN:
- Chorus-L1: R1 (consonant-heavy P0) — protect attacks
- Verse lines: R0/R1 (ok with baseline)

ESCALATION_NOTES:
- present: NO (singable under policy)

---

## 7) STACKING CLARITY-SAFE (G7 — READY)
stacking_used: YES

STACKING_MAP_BY_SECTION:
- Verse: NONE
- Chorus:
  - DOUBLE on tails only (outside P0 phrases)
- Final Chorus:
  - minimal BACKS as end-word echo (outside protected zones)

PROTECTED_ZONES:
- P0 phrases and consonant attacks on: маршрут/согнут/возвращаюсь/своему

QC_RULES:
- QC-S1: P0 first listen remains YES
- QC-S2: lift increases without clutter
- QC-S3: no consonant masking on P0

---

## 8) TAKE PACK REPEATABILITY (G8 — READY)
SESSION_INTENT:
- priorities: P0 clarity > arc lift > texture
- forbidden: breath splits inside P0; pronunciation drift

TAKE_GOALS_BY_SECTION:
- Verse:
  - stable diction baseline
  - rhythm tight
- Chorus:
  - P0 clarity first
  - lift via energy, not masking
  - land consonant attacks on P0
- Bridge:
  - reset intensity; keep clarity
- Final Chorus:
  - biggest lift; same pronunciation as prior choruses

REPEATABILITY_RULES:
- fixed pronunciation for P0 across takes
- chorus intensity band within target range
- hook articulation policy stays stable

QC_HARD_FAILS:
- P0 not understood first listen
- breath split inside P0
- stacking/delivery masks P0

COMP_NOTES:
- do not comp across pronunciation variants
- splice only outside P0 phrases

---

## 9) SCOPE COMPLIANCE (G9 — READY)
SCOPE_AUDIT:
- lyric_rewrite_present: NO
- structure_edit_present: NO
- arrangement_ownership_present: NO
- mix_chain_present: NO
- guessing_present: NO

ESCALATION_NOTES:
- present: NO

---

## 10) EXPECTED_GATE_RESULTS (UID-ONLY)
VALIDATED_BY:
- UE.KB.SPC.GATE.VOCAL_DIRECTOR.INPUT_READINESS.001
- UE.KB.SPC.GATE.VOCAL_DIRECTOR.MUST_HEAR.001
- UE.KB.SPC.GATE.VOCAL_DIRECTOR.INTELLIGIBILITY.001
- UE.KB.SPC.GATE.VOCAL_DIRECTOR.DELIVERY_COHERENCE.001
- UE.KB.SPC.GATE.VOCAL_DIRECTOR.ARC_CONTRAST.001
- UE.KB.SPC.GATE.VOCAL_DIRECTOR.BREATH_SINGABILITY.001
- UE.KB.SPC.GATE.VOCAL_DIRECTOR.STACKING_SAFE.001
- UE.KB.SPC.GATE.VOCAL_DIRECTOR.TAKE_PACK.001
- UE.KB.SPC.GATE.VOCAL_DIRECTOR.SCOPE_COMPLIANCE.001

EXPECTED_GATE_RESULTS:
- UE.KB.SPC.GATE.VOCAL_DIRECTOR.INPUT_READINESS.001 -> PASS
- UE.KB.SPC.GATE.VOCAL_DIRECTOR.MUST_HEAR.001 -> PASS
- UE.KB.SPC.GATE.VOCAL_DIRECTOR.INTELLIGIBILITY.001 -> PASS
- UE.KB.SPC.GATE.VOCAL_DIRECTOR.DELIVERY_COHERENCE.001 -> PASS
- UE.KB.SPC.GATE.VOCAL_DIRECTOR.ARC_CONTRAST.001 -> PASS
- UE.KB.SPC.GATE.VOCAL_DIRECTOR.BREATH_SINGABILITY.001 -> PASS
- UE.KB.SPC.GATE.VOCAL_DIRECTOR.STACKING_SAFE.001 -> PASS
- UE.KB.SPC.GATE.VOCAL_DIRECTOR.TAKE_PACK.001 -> PASS
- UE.KB.SPC.GATE.VOCAL_DIRECTOR.SCOPE_COMPLIANCE.001 -> PASS

---

## 11) TRACE
TRACE:
- MEMORY_REUSE: NO
- WEB_LOOKUP_USED: NO

--- END.
