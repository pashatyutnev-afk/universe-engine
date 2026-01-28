# SPC PRO PACK — CASE (BORDERLINE-003) — TOO MANY CONTRAST LEVERS (G5 REWORK) (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/06__CASE_LIBRARY/13__CASE__BORDERLINE_003.md

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
UID: UE.KB.SPC.PACK.VOCAL_DIRECTOR.CASE.BORDERLINE.003.DRAFT.001
OWNER: SYSTEM
ROLE: BORDERLINE anchor for calibrating Gate G5 ARC/CONTRAST as REWORK when contrast levers exceed the limit (<=3). Demonstrates performer overload and the minimal PB-05 patch: prune to 1–3 levers while preserving lift.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created BORDERLINE-003: lever overload triggers G5 REWORK; PB-05 prunes to <=3."
- REASON: "Too many levers destroy executability and make arc inconsistent across takes."
- IMPACT: "Enforces minimal lever discipline; improves repeatability."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.PACK.VOCAL_DIRECTOR.CASE.BORDER003.001

---

## 0) CASE_RECORD
CASE_RECORD:
- CASE_ID: BORDERLINE-003
- TYPE: BORDERLINE
- CONTEXT:
  - format: full song
  - language: RU
  - vocal_mode: mixed
  - tempo_feel: mid-tempo
  - note: Inputs exist and arc intent exists; failure is lever overload.

---

## 1) INPUTS (MINIMAL)
### 1.1 Lyric excerpt (hook)
[Chorus / Hook]
Я вижу маршрут — меня не согнут.
Я возвращаюсь к своему.

### 1.2 Structure labels
STRUCTURE:
- Verse
- Chorus (HOOK)
- Verse 2
- Chorus
- Bridge
- Final Chorus

### 1.3 Must-hear targets
MUST_HEAR_WORDS:
- P0: маршрут, согнут, возвращаюсь, своему
MUST_HEAR_PHRASES:
- P0: "я вижу маршрут", "я возвращаюсь к своему"

---

## 2) ARC PACK (BORDERLINE VERSION — OVERLOAD)
### 2.1 PERFORMANCE_ARC_MAP (exists)
- Verse: baseline
- Chorus: lift
- Bridge: contrast
- Final Chorus: biggest lift

### 2.2 CONTRAST_LEVERS (too many — problem)
Levers (bad):
- L1 ENERGY/INTENSITY (Verse 55 → Chorus 80)
- L2 DELIVERY MODE (Verse clean → Chorus shout)
- L3 ARTICULATION FOCUS (Verse mixed → Chorus consonant-forward)
- L4 DYNAMICS SHAPE (Verse narrow → Chorus wide)
- L5 TIMING FEEL (Verse laid-back → Chorus ahead)

lever_count = 5 (>3) → performer overload, inconsistent execution likely.

### 2.3 Observed risk (why REWORK not FAIL)
- Arc exists; lift is defined.
- But 5 levers cannot be executed reliably; needs pruning.
- This is REWORK (not FAIL) because a minimal patch can fix it.

---

## 3) EXPECTED_GATE_RESULTS (UID-ONLY)
VALIDATED_BY:
- UE.KB.SPC.GATE.VOCAL_DIRECTOR.ARC_CONTRAST.001

EXPECTED_GATE_RESULTS:
- UE.KB.SPC.GATE.VOCAL_DIRECTOR.ARC_CONTRAST.001 -> REWORK

---

## 4) WHY (WHY THIS IS BORDERLINE)
- Arc map exists and chorus is lift point.
- But lever_count > 3 violates gate threshold.
- Therefore: REWORK with PB-05 to reduce to 1–3 levers.

---

## 5) FIX ROUTE (PB-05) — MINIMAL PATCH
PB-05 patch rule:
- keep only 1–3 levers that are most audible and least harmful to intelligibility

Example pruned levers (<=3):
- Keep L1 ENERGY/INTENSITY
- Keep L3 ARTICULATION FOCUS (protect P0)
- Optional keep L4 DYNAMICS SHAPE (if still needed)

Remove:
- L2 DELIVERY MODE (risk masking P0)
- L5 TIMING FEEL (secondary; adds confusion)

After patch:
- lever_count = 2–3 → rerun G5 → expected PASS.

---

## 6) TRACE
TRACE:
- MEMORY_REUSE: NO
- WEB_LOOKUP_USED: NO

--- END.
