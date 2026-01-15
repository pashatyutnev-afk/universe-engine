# SPC PRO PACK — CASE (GOOD-005) — STACKING CLARITY-SAFE PASS ANCHOR (G7) (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/06__CASE_LIBRARY/19__CASE__GOOD_005.md

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
UID: UE.KB.SPC.PACK.VOCAL_DIRECTOR.CASE.GOOD.005.DRAFT.001
OWNER: SYSTEM
ROLE: GOOD case anchor for calibrating Gate G7 STACKING CLARITY-SAFE as PASS. Demonstrates a minimal-first stacking plan with explicit protected zones for P0 targets and QC rules ensuring stacking never reduces intelligibility.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created GOOD-005 anchor case: minimal stacking with protected zones passes G7."
- REASON: "Layering often masks consonants; pack needs a PASS reference for clarity-safe stacking."
- IMPACT: "Hook lift increases while P0 targets remain readable."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.PACK.VOCAL_DIRECTOR.CASE.GOOD005.001

---

## 0) CASE_RECORD
CASE_RECORD:
- CASE_ID: GOOD-005
- TYPE: GOOD
- CONTEXT:
  - format: full song
  - language: RU
  - vocal_mode: melodic hook + firm verse
  - tempo_feel: mid-tempo
  - note: Focus = stacking safety; not an arc or breath edge case.

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
- Chorus (HOOK)
- Final Chorus (HOOK)

### 1.3 MUST-HEAR targets
MUST_HEAR_WORDS:
- P0: маршрут, согнут, возвращаюсь, своему
MUST_HEAR_PHRASES:
- P0: "я вижу маршрут", "я возвращаюсь к своему"

---

## 2) STACKING PACK (PASS ANCHOR)
### 2.1 STACKING_MAP_BY_SECTION (minimal-first)
stacking_used: YES

STACKING_MAP_BY_SECTION:
- Verse: NONE
- Chorus:
  - mode: DOUBLE (limited)
  - where: end-of-line tails only (outside P0 phrases)
- Final Chorus:
  - mode: BACKS (minimal)
  - where: last word echo outside protected zones

Rationale:
- Hook needs lift, but P0 attacks must remain lead-clean.

### 2.2 PROTECTED_ZONES (P0 protection)
PROTECTED_ZONES:
- P0 phrases:
  - "я вижу маршрут"
  - "я возвращаюсь к своему"
- avoid stacking over:
  - consonant attacks on: маршрут / согнут / возвращаюсь / своему
- breath-critical:
  - no added layers that force breath changes inside P0

### 2.3 QC_RULES (PASS/FAIL)
QC_RULES:
- QC-S1 (P0 first listen): PASS when P0 understood on first listen in chorus/hook
- QC-S2 (lift): PASS when stacking increases perceived hook size without clutter
- QC-S3 (no masking): PASS when consonant attacks on P0 remain clean and readable

FAIL triggers:
- any P0 word becomes less clear with stacking → FAIL (remove/move stacking)
- continuous doubling across full chorus lines → FAIL (violates minimal-first)

---

## 3) EXPECTED_GATE_RESULTS (UID-ONLY)
VALIDATED_BY:
- UE.KB.SPC.GATE.VOCAL_DIRECTOR.STACKING_SAFE.001

EXPECTED_GATE_RESULTS:
- UE.KB.SPC.GATE.VOCAL_DIRECTOR.STACKING_SAFE.001 -> PASS

---

## 4) WHY (WHY THIS PASSES G7)
- Stacking map exists and is minimal-first (not everywhere).
- Protected zones explicitly cover P0 phrases and consonant attacks.
- QC rules exist with P0-first constraint and fail triggers.

---

## 5) FIX ROUTE (IF IT REGRESSES)
If stacking starts masking P0:
- apply PB-07 to reduce/move stacking or set explicit N/A.

---

## 6) TRACE
TRACE:
- MEMORY_REUSE: NO
- WEB_LOOKUP_USED: NO

--- END.
