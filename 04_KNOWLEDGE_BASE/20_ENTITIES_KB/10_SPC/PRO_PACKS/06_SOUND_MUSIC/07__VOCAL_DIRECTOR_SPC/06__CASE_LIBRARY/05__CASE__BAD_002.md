# SPC PRO PACK — CASE (BAD-002) — P0 MISSING (G2 FAIL) (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/06__CASE_LIBRARY/05__CASE__BAD_002.md

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
UID: UE.KB.SPC.PACK.VOCAL_DIRECTOR.CASE.BAD.002.DRAFT.001
OWNER: SYSTEM
ROLE: BAD case anchor for calibrating G2 MUST-HEAR TARGETS as FAIL: P0 targets are missing (no intelligibility target). Demonstrates STOP rule: do not proceed to intelligibility/arc/take work without a testable P0 list + phrase promotion when needed.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created BAD-002 anchor case: MUST-HEAR P0 missing triggers G2 FAIL."
- REASON: "Without P0, intelligibility cannot be tested; outputs become subjective."
- IMPACT: "Forces explicit must-hear targets before any vocal direction is considered READY."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.PACK.VOCAL_DIRECTOR.CASE.BAD002.001

---

## 0) CASE_RECORD
CASE_RECORD:
- CASE_ID: BAD-002
- TYPE: BAD
- CONTEXT:
  - format: full song
  - language: RU
  - vocal_mode: melodic chorus + rap/spoken verse
  - tempo_feel: mid-tempo
  - note: Inputs exist (G1 can PASS), but targets are missing (G2 must FAIL).

---

## 1) INPUTS (MINIMAL)
### 1.1 Lyric excerpt (hook + verse fragment)
[Verse fragment]
В переулках эхо, как битый металл,
Мне нужен удар, чтобы выйти из спин.

[Chorus / Hook]
Я возвращаюсь к своему.
Без шума, без позы, без лишних “почему”.

### 1.2 Structure labels (minimal)
STRUCTURE:
- Intro
- Verse 1
- Chorus (HOOK)
- Verse 2
- Chorus (HOOK)
- Outro

### 1.3 MUST-HEAR targets (bad version — missing P0)
MUST_HEAR_WORDS:
- P0: (missing)
- P1: (missing)
- P2: (missing)

MUST_HEAR_PHRASES:
- P0: (missing)
- P1: (missing)

CLARITY_TARGETS:
- (missing)

This is the failure: there is no testable intelligibility target.

---

## 2) BASELINE_DIRECTION_PACK
NOT READY by definition because G2 FAIL.
Bad “direction” example (what NOT to do):
- "Сделай припев максимально разборчивым и мощным."
Problem:
- no P0/P1 targets, no phrases, no pass criteria.

---

## 3) EXPECTED_GATE_RESULTS (UID-ONLY)
VALIDATED_BY:
- UE.KB.SPC.GATE.VOCAL_DIRECTOR.INPUT_READINESS.001
- UE.KB.SPC.GATE.VOCAL_DIRECTOR.MUST_HEAR.001

EXPECTED_GATE_RESULTS:
- UE.KB.SPC.GATE.VOCAL_DIRECTOR.INPUT_READINESS.001 -> PASS
- UE.KB.SPC.GATE.VOCAL_DIRECTOR.MUST_HEAR.001 -> FAIL

Stop rule:
- Do NOT proceed to G3..G9 when G2 FAIL.

---

## 4) WHY (WHY THIS FAILS)
- G1 can PASS: lyrics + structure + language context exist.
- G2 must FAIL because:
  - P0 missing entirely (no must-hear targets)
  - no phrase promotion
  - no clarity targets
Therefore:
- intelligibility cannot be validated; any “repair” is guessing.

---

## 5) FIX ROUTE (PB-02) — MINIMAL PATCH SHAPE
Apply PB-02 MUST-HEAR WORDS PRIORITY:

Example patched targets:
MUST_HEAR_WORDS:
- P0: возвращаюсь, своему, почему
- P1: шума, позы, удар
- P2: (optional) эхо, металл

MUST_HEAR_PHRASES:
- P0: "я возвращаюсь к своему"
- P1: "без шума, без позы"

CLARITY_TARGETS:
- Target A: "P0 phrase understood on first listen in chorus/hook"
- Target B: "No breath split inside P0 phrase"

After patch:
- rerun G2 → expected PASS
- only then proceed to G3.

---

## 6) TRACE
TRACE:
- MEMORY_REUSE: NO
- WEB_LOOKUP_USED: NO

--- END.
