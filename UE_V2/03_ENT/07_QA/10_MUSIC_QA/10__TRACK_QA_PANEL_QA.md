# 10__TRACK_QA_PANEL_QA

SCOPE: Universe Engine (UE_V2)
DOC_TYPE: QA
UID: UE.V2.QA.MUSIC.TRACK_PANEL.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
NAV_RULE: Use RAW links only
PURPOSE: Единая QA-панель трека: агрегирует существующие MUSIC_QA проверки 01–09 в один отчёт.

---

## [M] INTENT
Сделать “одну кнопку QA”: вместо хаоса отдельных проверок, панель выдаёт единый QA_REPORT и решение PASS/REWORK.

---

## [M] INPUTS
- DRAFT/SELECTION ref (что проверяем)
- PLAN_TOKEN (mode/coverage)
- KB_TOKEN (ограничения/запреты)

---

## [M] USES (EXISTING QA CHECKS)
Обязательные проверки (по умолчанию):
- 01__SCROLL_STOP_5S_QA
- 02__LOOP_15S_QA
- 03__RECOGNITION_10S_QA
- 05__MIX_TRANSLATION_QA
- 07__CATALOG_DIFFERENTIATION_QA
- 09__REGRESSION_GUARD_QA

Условные/доменные:
- 04__CREATOR_PANEL_QA (если на UGC/Creator workflow)
- 06__HOOK_PANEL_QA (если фокус на хуке)
- 08__VOICE_DIVERSITY_AUDIT_QA (если важно разнообразие/персоны/серии)

---

## [M] OUTPUTS
- IO.MUSIC.TRACK_QA_REPORT
- REPORT_TOKEN (QA): PASS/REWORK + список проблем + приоритеты фикса

---

## [M] RUBRIC (SIMPLE)
PASS если:
- loop ok
- recognition ok
- mix translation ok (без major дефектов)
- differentiation ok (нет ощущения “это уже было”)
- regression guard ok

REWORK если:
- есть 1+ major defect или 2+ medium defects

---

## [M] GATES
PASS если:
- сформирован единый QA_REPORT и принято решение PASS/REWORK
REWORK если:
- нет связки с исходными QA checks или нет выводов
