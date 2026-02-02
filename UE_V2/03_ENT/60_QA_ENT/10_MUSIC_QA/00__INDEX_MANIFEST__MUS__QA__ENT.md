# 00__INDEX__MUSIC_QA

SCOPE: Universe Engine (UE_V2)
DOC_TYPE: INDEX (REALM)
UID: UE.V2.QA.MUSIC.INDEX.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
NAV_RULE: Use RAW links only
PURPOSE: Каталог QA проверок музыки. Вход в QA.MUSIC реалм.

---

## [M] INDEX TABLE
| FILE | QA_CHECK | PURPOSE | STATUS | UID |
|---|---|---|---|---|
| 01__SCROLL_STOP_5S_QA.md | SCROLL_STOP_5S_QA | Скролл-стоп ≤ 5 сек | ACTIVE | (fill if exists) |
| 02__LOOP_15S_QA.md | LOOP_15S_QA | Луп 15 сек без шва | ACTIVE | (fill if exists) |
| 03__RECOGNITION_10S_QA.md | RECOGNITION_10S_QA | Узнаваемость ≤ 10 сек | ACTIVE | (fill if exists) |
| 04__CREATOR_PANEL_QA.md | CREATOR_PANEL_QA | UGC/creator критерии | ACTIVE | (fill if exists) |
| 05__MIX_TRANSLATION_QA.md | MIX_TRANSLATION_QA | Трансляция микса | ACTIVE | (fill if exists) |
| 06__HOOK_PANEL_QA.md | HOOK_PANEL_QA | Панель качества хука | ACTIVE | (fill if exists) |
| 07__CATALOG_DIFFERENTIATION_QA.md | CATALOG_DIFFERENTIATION_QA | Уникальность/дифференциация | ACTIVE | (fill if exists) |
| 08__VOICE_DIVERSITY_AUDIT_QA.md | VOICE_DIVERSITY_AUDIT_QA | Разнообразие/персоны (если нужно) | ACTIVE | (fill if exists) |
| 09__REGRESSION_GUARD_QA.md | REGRESSION_GUARD_QA | Регресс-охранник | ACTIVE | (fill if exists) |
| 10__TRACK_QA_PANEL_QA.md | TRACK_QA_PANEL_QA | Агрегатор 01–09 в единый QA_REPORT | ACTIVE | UE.V2.QA.MUSIC.TRACK_PANEL.001 |

---

## [M] RULES
- Для MUSIC.TRACK обязательна панель 10 (она агрегирует нужные проверки).
- Узкие задачи (HOOK/MIX) могут вызывать специализированные QA (05/06/03).

---

## [M] GATES
PASS если:
- индекс отражает все QA checks и остаётся коротким
