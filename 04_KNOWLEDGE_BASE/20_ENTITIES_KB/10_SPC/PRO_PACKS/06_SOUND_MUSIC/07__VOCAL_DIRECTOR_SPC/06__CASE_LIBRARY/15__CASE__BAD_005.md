# SPC PRO PACK — CASE (BAD-005) — FLAT ARC / NO LIFT (G5 FAIL) (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/06__CASE_LIBRARY/15__CASE__BAD_005.md

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
UID: UE.KB.SPC.PACK.VOCAL_DIRECTOR.CASE.BAD.005.DRAFT.001
OWNER: SYSTEM
ROLE: BAD case anchor for calibrating Gate G5 ARC/CONTRAST as FAIL when arc map and contrast levers are missing (flat performance). Demonstrates the “no lift” failure: verse and chorus are indistinguishable because no arc is specified.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created BAD-005 anchor case: missing arc map/levers triggers G5 FAIL (flat verse=chorus)."
- REASON: "Without arc/contrast, hook impact is accidental; pack must require explicit lift design."
- IMPACT: "Forces PB-05 to create a real arc map and minimal lever set."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.PACK.VOCAL_DIRECTOR.CASE.BAD005.001

---

## 0) CASE_RECORD
CASE_RECORD:
- CASE_ID: BAD-005
- TYPE: BAD
- CONTEXT:
  - format: full song
  - language: RU
  - vocal_mode: melodic chorus
  - tempo_feel: mid-tempo
  - note: Failure is intentional: no arc/contrast defined.

---

## 1) INPUTS (MINIMAL)
### 1.1 Lyric excerpt (verse + hook)
[Verse fragment]
Я был слишком долго “не тем” для витрин.

[Chorus / Hook]
Я вижу маршрут — меня не согнут.

### 1.2 Structure labels
STRUCTURE:
- Verse
- Chorus (HOOK)
- Verse 2
- Chorus (HOOK)

### 1.3 Must-hear targets (present)
MUST_HEAR_WORDS:
- P0: маршрут, согнут
MUST_HEAR_PHRASES:
- P0: "вижу маршрут", "не согнут"

---

## 2) BASELINE_DIRECTION_PACK (BAD — FLAT)
What exists (insufficient):
- "Пой одинаково ровно во всех частях, без изменений."
- "Не делай припев громче и эмоциональнее — пусть всё будет одинаково."

What is missing (critical):
- PERFORMANCE_ARC_MAP (by section)
- CONTRAST_LEVERS (1–3)
- any QC arc checks

Observed result:
- Verse and chorus sound indistinguishable → hook does not lift.

---

## 3) EXPECTED_GATE_RESULTS (UID-ONLY)
VALIDATED_BY:
- UE.KB.SPC.GATE.VOCAL_DIRECTOR.ARC_CONTRAST.001

EXPECTED_GATE_RESULTS:
- UE.KB.SPC.GATE.VOCAL_DIRECTOR.ARC_CONTRAST.001 -> FAIL

Stop rule:
- Do NOT proceed to G6..G9 until G5 is rebuilt (arc must exist).

---

## 4) WHY (WHY THIS FAILS)
- G5 requires an explicit arc map + 1–3 levers.
- Here:
  - arc map is missing entirely
  - lever set is missing entirely
  - direction explicitly forbids lift
Therefore:
- This is FAIL, not REWORK.

---

## 5) FIX ROUTE (PB-05)
Apply PB-05 SECTION ARC DESIGN:
- create PERFORMANCE_ARC_MAP
- declare 1–3 contrast levers (e.g., energy + articulation focus)
- add QC_ARC_CHECKS:
  - chorus_lift_present YES/NO
  - lever_count_ok <=3 YES/NO
  - intelligibility_preserved YES/NO

After patch:
- rerun G5 → expected PASS.

---

## 6) TRACE
TRACE:
- MEMORY_REUSE: NO
- WEB_LOOKUP_USED: NO

--- END.
