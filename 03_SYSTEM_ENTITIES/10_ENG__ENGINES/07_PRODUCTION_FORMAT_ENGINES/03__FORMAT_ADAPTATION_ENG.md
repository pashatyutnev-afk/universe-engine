# Format Adaptation Engine
FILE: 03__FORMAT_ADAPTATION_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 07_PRODUCTION_FORMAT_ENGINES
LEVEL: L3
STATUS: ACTIVE
VERSION: 1.0
ROLE: Maps content between formats (book↔series↔video↔game) using keep/cut/merge/split/transform rules

---

## PURPOSE

Перенос между форматами ломает историю, если делать “просто пересказ”.
Движок строит **ADAPTATION MAP**:
- что сохраняем (keep)
- что режем (cut)
- что объединяем (merge)
- что дробим (split)
- что трансформируем (transform)

---

## INPUTS

- Source format spec
- Target format spec
- Canon locks (world law, continuity)
- Budget/time constraints

---

## OUTPUTS

- Adaptation Map table
- Target structure draft
- Risk list (что может сломаться)
- Compensation plan (чем компенсируем потери)

---

## ADAPTATION MAP (CANON)

For each source unit (chapter/scene/episode):
- SOURCE UNIT ID
- CORE FUNCTION (зачем оно)
- TARGET ACTION:
  - KEEP / CUT / MERGE / SPLIT / TRANSFORM
- TARGET UNIT ID(s)
- NOTES (риски, условия)

---

## PROCEDURE

1) Identify core functions of source units
2) Define target unit size + beat density
3) Apply mapping rules
4) Validate continuity and stakes
5) Write compensation:
   - если cut — где возвращаем важную функцию

---

## VALIDATION RULES

- FA1: Нельзя резать “функцию”, можно резать “форму”.
- FA2: Любой merge/split должен сохранять причинно-следственную логику.
- FA3: Таргет-формат диктует ритм и структуру, не исходник.

---
OWNER: Universe Engine
STATUS: FIXED
