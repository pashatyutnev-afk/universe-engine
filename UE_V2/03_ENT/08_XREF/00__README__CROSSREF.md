# 00__README__CROSSREF

SCOPE: Universe Engine (UE_V2)
DOC_TYPE: README (REALM)
UID: UE.V2.XREF.README.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
NAV_RULE: Use RAW links only
PURPOSE: Короткая инструкция как пользоваться XREF картами без блуждания. Это "карта завода".

---

## [M] INTENT
XREF — это не сущности и не контент. XREF — это правила связности:
- куда идти (PIPELINES)
- кого судить (VALIDATION_MATRIX)
- как стыковать (IO + KB scopes)
- как обеспечить качество со всех сторон (coverage)

---

## [M] ENTRYPOINT
- Index: UE_V2/03_ENT/08_XREF/00__INDEX__CROSSREF.md
- NAV: UE_V2/04_NAV/09__IDX_XREF.md

---

## [M] HOW TO USE (CANON)
1) Определи ARTIFACT_TYPE (например MUSIC.TRACK).
2) Открой:
   - 04__MAP__PIPELINES -> найди ARTIFACT_TYPE -> получи PIPE + DEFAULT_ORC + EXEC_MODE.
3) Открой:
   - 03__MAP__VALIDATION_MATRIX -> найди ARTIFACT_TYPE -> получи обязательные CTL/VAL/QA.
4) Если нужно подобрать участников автоматически:
   - используй REG_ENTITY_CATALOG + 06__MAP__KB_SCOPE_BINDINGS + 05__MAP__ENTITY_IO_TYPES.
5) Если нужно качество "со всех сторон":
   - используй 07__MAP__COVERAGE_TO_ENTITIES + STD/16 coverage rules.
6) Если нужно базовое выполнение без хаоса:
   - используй 08__MAP__DEFAULT_CHAIN + STEP-RUN протокол.

---

## [M] ANTI-NOISE
- Не сканировать дерево папок.
- Открывать только 1 карту, которая нужна сейчас.
- Не копировать карты в контекст: использовать точечно.

---

## [M] GATES
PASS если:
- XREF карты используются для роутинга/валидации/совместимости
REWORK если:
- система выбирает пайпы/сущности “по памяти” без карт
