# 23__SCORE_RUBRIC_FMT

SCOPE: Universe Engine (UE_V2)
DOC_TYPE: STD
UID: UE.V2.STD.SCORE_RUBRIC_FMT.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
NAV_RULE: Use RAW links only
PURPOSE: Единая рубрика скоринга вариантов для выбора победителей и синтеза.

---

## [M] INTENT
Свести сравнение вариантов к понятной шкале, связанной с QA/VAL/CTL.

---

## [M] SCORE SCALE
0–10 по каждому критерию.
- 0–3: плохо
- 4–6: средне/терпимо
- 7–8: хорошо
- 9–10: отлично

---

## [M] MUSIC TRACK RUBRIC (DEFAULT)
C1 Hook impact (узнаваемость/скролл-стоп)
C2 Loop integrity (без шва)
C3 Mix translation (телефон/наушники/колонка)
C4 Uniqueness (нет ощущения "уже было")
C5 Structure/energy map (динамика, пики)
C6 Palette clarity (тембры читаются, нет каши)
C7 Compliance (нет нарушений правил/табуу/метаданных)
C8 Release readiness (готовность к упаковке)

---

## [M] WEIGHTS (DEFAULT)
- C1: 2
- C2: 2
- C3: 2
- C4: 2
- C5: 1
- C6: 1
- C7: 2 (если релиз-уровень), иначе 1
- C8: 2 (если релиз-уровень), иначе 0

---

## [M] SCORE_TOKEN_TEMPLATE
SCORE_TOKEN:
- TOKEN_ID:
- STEP_ID:
- CANDIDATES:
  - ID: scores: {C1:.. C8:..} total: .. notes: (0–5 bullets)
- TOP_PICK:
  - winner: ID
  - runner_up: ID
  - why: (3–8 строк)
- FAIL_FLAGS:
  - ID: (QA/VAL fail reasons)

---

## [M] GATES
PASS если:
- есть total и winner/runner_up
REWORK если:
- нет связи с QA/VAL fail reasons
