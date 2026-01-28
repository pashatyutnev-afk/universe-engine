# SPC PRO PACK — CASE (BORDERLINE-001) — P0 TOO LONG / NO PHRASES (G2 REWORK) (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/06__CASE_LIBRARY/03__CASE__BORDERLINE_001.md

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
UID: UE.KB.SPC.PACK.VOCAL_DIRECTOR.CASE.BORDERLINE.001.DRAFT.001
OWNER: SYSTEM
ROLE: BORDERLINE anchor for calibrating G2 MUST-HEAR TARGETS as REWORK: P0 list is bloated/untestable and phrase promotion is missing. Demonstrates threshold: P0 must be short (3–8) and phrases must be promoted when meaning depends on multi-word units.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created BORDERLINE-001 anchor case: P0 too long and missing phrases triggers G2 REWORK."
- REASON: "Teaches the exact threshold between PASS and REWORK for must-hear targets."
- IMPACT: "Improves target discipline; faster intelligibility convergence."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.PACK.VOCAL_DIRECTOR.CASE.BORDER001.001

---

## 0) CASE_RECORD
CASE_RECORD:
- CASE_ID: BORDERLINE-001
- TYPE: BORDERLINE
- CONTEXT:
  - format: full song
  - language: RU
  - vocal_mode: melodic chorus + spoken/rap verse
  - tempo_feel: mid-tempo
  - note: Inputs exist (G1 PASS), but must-hear targets are poorly formed.

---

## 1) INPUTS (MINIMAL)
### 1.1 Lyric excerpt (hook + verse fragment)
[Verse fragment]
Я был слишком долго “не тем” для витрин,
Мне нужен удар, чтобы выйти из спин.

[Chorus / Hook]
Я возвращаюсь к своему —
Без шума, без позы, без лишних “почему”.

### 1.2 Structure labels (minimal)
STRUCTURE:
- Intro
- Verse
- Chorus (HOOK)
- Verse 2
- Chorus (HOOK)
- Outro

### 1.3 MUST-HEAR targets (bad borderline version)
MUST_HEAR_WORDS:
- P0: я, возвращаюсь, к, своему, без, шума, без, позы, без, лишних, почему, удар, выйти, спин
- P1: витрин, долго, не тем
- P2: (none)

MUST_HEAR_PHRASES:
- P0: (missing)
- P1: (missing)

CLARITY_TARGETS:
- (missing explicit pass statements)

Problems (intentional):
- P0 is 13 items (too long) and includes filler (“я”, “к”, “без”).
- Meaning depends on phrases (“я возвращаюсь к своему”, “без шума, без позы…”), but phrases are not promoted.
- No explicit clarity targets → untestable.

---

## 2) BASELINE_DIRECTION_PACK (SHORT)
Minimal direction exists but targets are flawed:
- Delivery: “make chorus clear”
- No explicit intelligibility checklist present (not assessed in this case; focus = G2 thresholds)

---

## 3) EXPECTED_GATE_RESULTS (UID-ONLY)
VALIDATED_BY:
- UE.KB.SPC.GATE.VOCAL_DIRECTOR.INPUT_READINESS.001
- UE.KB.SPC.GATE.VOCAL_DIRECTOR.MUST_HEAR.001

EXPECTED_GATE_RESULTS:
- UE.KB.SPC.GATE.VOCAL_DIRECTOR.INPUT_READINESS.001 -> PASS
- UE.KB.SPC.GATE.VOCAL_DIRECTOR.MUST_HEAR.001 -> REWORK

---

## 4) WHY (WHY THIS IS BORDERLINE)
- Inputs exist (lyrics + structure + language) → G1 PASS.
- Must-hear targets exist, but violate thresholds:
  - P0 too long (>8) → REWORK
  - P0 contains fillers → REWORK
  - Phrase promotion missing → REWORK
  - No clarity targets → REWORK

This is not FAIL because:
- P0 block exists (not empty).
It is REWORK because:
- targets are not testable.

---

## 5) FIX ROUTE (MINIMAL PATCH)
Apply PB-02 MUST-HEAR WORDS PRIORITY:

Minimal patch result (example target shape):
MUST_HEAR_WORDS (patched):
- P0: возвращаюсь, своему, почему
- P1: шума, позы, удар
- P2: (optional) витрин, спин

MUST_HEAR_PHRASES (patched):
- P0: "я возвращаюсь к своему"
- P1: "без шума, без позы"

CLARITY_TARGETS (patched):
- Target A: "P0 phrases understood on first listen in chorus/hook"
- Target B: "No breath split inside P0 phrase"

After patch:
- rerun G2 → expected PASS, then proceed to G3.

---

## 6) TRACE
TRACE:
- MEMORY_REUSE: NO
- WEB_LOOKUP_USED: NO

--- END.
