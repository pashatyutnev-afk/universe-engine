# SPC PRO PACK — CASE (BAD-007) — STACKING MASKS P0 (G7 FAIL) (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/06__CASE_LIBRARY/21__CASE__BAD_007.md

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
UID: UE.KB.SPC.PACK.VOCAL_DIRECTOR.CASE.BAD.007.DRAFT.001
OWNER: SYSTEM
ROLE: BAD case anchor for calibrating Gate G7 STACKING CLARITY-SAFE as FAIL: stacking is applied everywhere across the chorus, no protected zones exist, and P0 intelligibility is reduced by design. Demonstrates automatic FAIL and PB-07 fix route.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created BAD-007 anchor case: uncontrolled stacking masks P0 and triggers G7 FAIL."
- REASON: "Layering is a common source of consonant loss; gate must enforce protected zones and minimalism."
- IMPACT: "Prevents ‘big chorus, unreadable hook’ due to stacking."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.PACK.VOCAL_DIRECTOR.CASE.BAD007.001

---

## 0) CASE_RECORD
CASE_RECORD:
- CASE_ID: BAD-007
- TYPE: BAD
- CONTEXT:
  - format: full song
  - language: RU
  - vocal_mode: melodic hook
  - tempo_feel: mid-tempo
  - note: Failure is uncontrolled stacking, not performance or lyrics.

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

### 1.3 MUST-HEAR targets
MUST_HEAR_WORDS:
- P0: маршрут, согнут, возвращаюсь, своему
MUST_HEAR_PHRASES:
- P0: "я вижу маршрут", "я возвращаюсь к своему"

---

## 2) STACKING PLAN (BAD — UNCONTROLLED)
stacking_used: YES

STACKING_MAP_BY_SECTION (bad):
- Chorus:
  - mode: DOUBLE + BACKS + HARMONY (all at once)
  - where: entire chorus lines (continuous)
  - note: "stack everywhere to make it huge"

PROTECTED_ZONES:
- (missing)

QC_RULES:
- (missing)

Observed effect (textual):
- consonant attacks on “маршрут/согнут” are smeared; listener cannot understand P0 on first listen.

---

## 3) WHY THIS IS A HARD FAIL
- No protected zones: stacking is placed over P0 phrases.
- No QC rules: no way to validate intelligibility impact.
- Violates minimal-first constraint: continuous stacking across full lines.
- Therefore: must FAIL G7.

---

## 4) EXPECTED_GATE_RESULTS (UID-ONLY)
VALIDATED_BY:
- UE.KB.SPC.GATE.VOCAL_DIRECTOR.STACKING_SAFE.001
- UE.KB.SPC.GATE.VOCAL_DIRECTOR.INTELLIGIBILITY.001

EXPECTED_GATE_RESULTS:
- UE.KB.SPC.GATE.VOCAL_DIRECTOR.STACKING_SAFE.001 -> FAIL
- UE.KB.SPC.GATE.VOCAL_DIRECTOR.INTELLIGIBILITY.001 -> REWORK (or FAIL depending on severity)

Stop rule:
- Must rebuild stacking plan before proceeding.

---

## 5) FIX ROUTE (PB-07) — MINIMAL PATCH
Apply PB-07 STACKING MINIMAL PLAN:

Patched shape (example):
- Verse: NONE
- Chorus:
  - DOUBLE only on tails outside P0 phrases
  - optional BACKS on last word echo outside protected zones
- Define PROTECTED_ZONES:
  - no stacking over P0 phrases and consonant attacks
- Add QC_RULES:
  - P0 first listen must remain YES
  - fail if P0 becomes less clear

After patch:
- rerun G7 → expected PASS.

---

## 6) TRACE
TRACE:
- MEMORY_REUSE: NO
- WEB_LOOKUP_USED: NO

--- END.
