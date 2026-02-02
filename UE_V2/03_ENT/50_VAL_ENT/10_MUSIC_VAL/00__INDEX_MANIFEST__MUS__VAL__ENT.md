# 00__INDEX__MUSIC_VALIDATORS

SCOPE: Universe Engine (UE_V2)
DOC_TYPE: INDEX (REALM)
UID: UE.V2.VAL.MUSIC.INDEX.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
NAV_RULE: Use RAW links only
PURPOSE: Каталог валидаторов музыки. Вход в VAL.MUSIC реалм.

---

## [M] INDEX TABLE
| FILE | VAL_NAME | PURPOSE | STATUS | UID |
|---|---|---|---|---|
| 01__DOC_FORMAT_VAL.md | DOC_FORMAT_VAL | Формат/маркеры (если есть) | ACTIVE | (fill if exists) |
| 02__PROMPT_SANITY_VAL.md | PROMPT_SANITY_VAL | Санити промптов (если есть) | ACTIVE | (fill if exists) |
| 03__STRUCTURE_CONSISTENCY_VAL.md | STRUCTURE_CONSISTENCY_VAL | Структурная целостность (если есть) | ACTIVE | (fill if exists) |
| 04__COLLISION_BLOCKER_VAL.md | COLLISION_BLOCKER_VAL | Коллизии/повторы (если есть) | ACTIVE | (fill if exists) |
| 05__CREDITS_RIGHTS_VAL.md | CREDITS_RIGHTS_VAL | Права/кредиты (если есть) | ACTIVE | (fill if exists) |
| 06__PACK_READY_VAL.md | PACK_READY_VAL | Готовность упаковки (если есть) | ACTIVE | (fill if exists) |
| 07__EXPORT_READY_VAL.md | EXPORT_READY_VAL | Готовность экспорта (если есть) | ACTIVE | (fill if exists) |
| 08__METADATA_VAL.md | METADATA_VAL | Метаданные (если есть) | ACTIVE | (fill if exists) |
| 09__SERIES_NAMING_VAL.md | SERIES_NAMING_VAL | Названия/серии (если есть) | ACTIVE | (fill if exists) |
| 10__DROP_RULES_VAL.md | DROP_RULES_VAL | Политики дропа (если есть) | ACTIVE | (fill if exists) |
| 11__CHAIN_COMPLETENESS_VAL.md | CHAIN_COMPLETENESS_VAL | Полнота токенов/решений/архива | ACTIVE | UE.V2.VAL.MUSIC.CHAIN_COMPLETENESS.001 |
| 12__COVERAGE_PASS_VAL.md | COVERAGE_PASS_VAL | Покрытие Pillars | ACTIVE | UE.V2.VAL.MUSIC.COVERAGE_PASS.001 |
| 13__PROMPT_SPEC_VAL.md | PROMPT_SPEC_VAL | Контракт PROMPT_SPEC + запреты | ACTIVE | UE.V2.VAL.MUSIC.PROMPT_SPEC.001 |
| 14__SYNTHESIS_COHERENCE_VAL.md | SYNTHESIS_COHERENCE_VAL | Целостность композита после синтеза | ACTIVE | UE.V2.VAL.MUSIC.SYNTHESIS_COHERENCE.001 |

---

## [M] RULES
- На релиз-уровне обязателен VAL 11 и 12.
- При наличии PROMPT_SPEC шага обязателен VAL 13.
- При наличии SYNTHESIS шага обязателен VAL 14.

---

## [M] GATES
PASS если:
- индекс отражает полный набор валидаторов и не раздувается
