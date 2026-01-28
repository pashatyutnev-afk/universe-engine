# SPC PRO PACK — CASE (GOOD-003) — ARC/CONTRAST PASS ANCHOR (G5) (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/06__CASE_LIBRARY/10__CASE__GOOD_003.md

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
UID: UE.KB.SPC.PACK.VOCAL_DIRECTOR.CASE.GOOD.003.DRAFT.001
OWNER: SYSTEM
ROLE: GOOD case anchor for calibrating Gate G5 ARC/VERSE→CHORUS CONTRAST as PASS. Demonstrates explicit arc map and 1–3 performer-executable contrast levers with intelligibility preserved on P0 targets.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created GOOD-003 anchor case: explicit arc + 2 contrast levers; chorus lift without harming P0 clarity."
- REASON: "Pack needs a stable PASS reference for arc mapping and minimal lever discipline."
- IMPACT: "Stronger hook perception and consistent section dynamics across takes."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.PACK.VOCAL_DIRECTOR.CASE.GOOD003.001

---

## 0) CASE_RECORD
CASE_RECORD:
- CASE_ID: GOOD-003
- TYPE: GOOD
- CONTEXT:
  - format: full song
  - language: RU
  - vocal_mode: rap verse + melodic chorus
  - tempo_feel: half-time stomp, mid-tempo delivery
  - note: Focus = arc + contrast; not a stacking or breath edge case.

---

## 1) INPUTS (MINIMAL)
### 1.1 Lyric excerpt (verse + hook)
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
- Chorus 1 (HOOK / RELEASE)
- Verse 2
- Chorus 2 (HOOK / RELEASE)
- Bridge (CONTRAST)
- Final Chorus (HOOK / RELEASE)
- Outro

### 1.3 MUST-HEAR targets
MUST_HEAR_WORDS:
- P0: маршрут, согнут, возвращаюсь, своему
- P1: шаг
- P2: (none)

MUST_HEAR_PHRASES:
- P0: "я вижу маршрут", "я возвращаюсь к своему"

---

## 2) ARC PACK (THE PASS ANCHOR)
### 2.1 PERFORMANCE_ARC_MAP (by section)
- Intro: tension set, low intensity
- Verse 1 (SETUP): restrained aggression, clear diction baseline
- Chorus 1 (RELEASE/HOOK): clear lift; P0 phrases punch and stay readable
- Verse 2 (BUILD): slightly higher intensity than Verse 1, still controlled
- Chorus 2 (RELEASE/HOOK): same lift as Chorus 1 (repeatable)
- Bridge (CONTRAST): drop intensity to reset; reduce grit, keep clarity
- Final Chorus (RELEASE/HOOK): highest lift; keep P0 consonant attacks clean
- Outro: release cooldown

### 2.2 CONTRAST_LEVERS (2 levers only)
Lever L1 — ENERGY/INTENSITY (0..100):
- Verse: 55
- Chorus: 78
- Bridge: 60
- Final Chorus: 82

Lever L3 — ARTICULATION FOCUS:
- Verse: mixed articulation (story flow)
- Chorus: consonant-forward on P0 phrase attacks (“маршрут/согнут/возвращаюсь/своему”)
- Bridge: slightly softer articulation, but keep P0 readable if repeated

Lever count = 2 (<=3) — performer-executable.

### 2.3 SECTION_DELIVERY_NOTES (short)
- Verse: hold energy, keep words clear but not “shouted”
- Chorus: lift via energy, not distortion; keep P0 attacks crisp
- Bridge: contrast via drop; prepare for final lift
- Final Chorus: maximum lift while preserving P0 intelligibility

### 2.4 QC_ARC_CHECKS (YES/NO)
- chorus_lift_present: YES
- lever_count_ok (<=3): YES
- intelligibility_preserved (P0): YES
- bridge_contrast_without_identity_break: YES

---

## 3) EXPECTED_GATE_RESULTS (UID-ONLY)
VALIDATED_BY:
- UE.KB.SPC.GATE.VOCAL_DIRECTOR.ARC_CONTRAST.001

EXPECTED_GATE_RESULTS:
- UE.KB.SPC.GATE.VOCAL_DIRECTOR.ARC_CONTRAST.001 -> PASS

---

## 4) WHY (WHY THIS PASSES G5)
- Arc map covers all major sections with explicit roles (setup/build/release/contrast).
- Chorus is explicitly the lift/release point.
- Only 2 contrast levers (<=3) and both are executable.
- Lever choices protect intelligibility: chorus articulation is consonant-forward on P0.

---

## 5) FIX ROUTE (IF IT EVER FAILS)
If levers become too many or vague:
- PB-05 (reduce to 1–3 levers)
If lift harms P0 clarity:
- PB-03 (intelligibility repair) while keeping arc intact
Or PB-08 axis A2 (arc) minimal patch.

---

## 6) TRACE
TRACE:
- MEMORY_REUSE: NO
- WEB_LOOKUP_USED: NO

--- END.
