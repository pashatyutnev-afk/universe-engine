# 00__README__CASES — MUSIC_PRODUCER_SPC (PRO PACK)

FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/02__MUSIC_PRODUCER_SPC/06__CASE_LIBRARY/00__README__CASES.md
SCOPE: KB — SPC Pro Pack — Music Producer — Case Library (README)
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC / PRO_PACKS / 06__CASE_LIBRARY
DOC_TYPE: README
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.SPC.PACK.MUSIC_PRODUCER.CASES.README.001
OWNER: SPC (Music Producer)
ROLE: Explains how to use cases for calibration, QA gates, and regression guard.

CHANGE_NOTE:
- DATE: 2026-01-21
- TYPE: INIT
- SUMMARY: "Case library README initialized for Music Producer SPC pack."
- REASON: "Make gate calibration concrete via exemplars."
- IMPACT: "Defines case types and how they bind to rubric + gates."
- CHANGE_ID: UE.CHG.2026-01-21.KB.SPC.MPROD.CASES.README.001

---

## PURPOSE (LAW)
Case Library — это эталоны и анти-эталоны.
Используется для:
- калибровки оценок по RUBRIC (D1–D9),
- примеров PASS/REWORK/FAIL,
- обучения “что хорошо/плохо” без угадываний.

---

## CASE TYPES
- GOOD: эталон PASS (7–9+)
- BAD: явный FAIL (0–3) или hard-limit violation
- BORDERLINE: 4–6 (нужен REWORK)
- EDGE: крайний случай, где важна дисциплина scope/variants/constraints

---

## HOW TO USE
### During authoring (self-check)
1) Compare output with GOOD case structure.
2) Run rubric quickly (D1–D9).
3) If drift resembles BAD/BORDERLINE → run PB-02 repair.

### During validation
- Use GOOD as “anchor” for what PASS means.
- Use BAD to detect forbidden patterns (engineering recipes, scope drift).
- Use EDGE to test routing + guard behavior.

### During regression guard
- After patch, re-check that output still aligns with GOOD
- and does not reintroduce BAD signatures.

---

## CASE CONTENT STANDARD (EACH CASE MUST INCLUDE)
- CASE_ID (UID)
- INTENT
- INPUTS (minimal)
- OUTPUT (O1/O2/O3 fragments)
- RUBRIC SCORES (D1–D9 rough)
- FAIL MODES (if applicable)
- WHY THIS CASE EXISTS

---

## REQUIRED BASE CASES (MIN SET)
- UE.KB.SPC.PACK.MUSIC_PRODUCER.CASE.GOOD.001
- UE.KB.SPC.PACK.MUSIC_PRODUCER.CASE.BAD.001
- UE.KB.SPC.PACK.MUSIC_PRODUCER.CASE.BORDERLINE.001
- UE.KB.SPC.PACK.MUSIC_PRODUCER.CASE.EDGE.001

---
END
