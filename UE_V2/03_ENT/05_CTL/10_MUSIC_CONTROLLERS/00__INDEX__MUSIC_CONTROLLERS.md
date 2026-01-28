# 00__INDEX__MUSIC_CONTROLLERS

SCOPE: Universe Engine (UE_V2)
DOC_TYPE: INDEX (REALM)
UID: UE.V2.CTL.MUSIC.INDEX.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
NAV_RULE: Use RAW links only
PURPOSE: Каталог контроллеров музыки. Вход в CTL.MUSIC реалм.

---

## [M] INDEX TABLE
| FILE | CTL_NAME | PURPOSE | STATUS | UID |
|---|---|---|---|---|
| 01__PROMPT_CONTRACT_CTL.md | PROMPT_CONTRACT_CTL | Контракт промптов (если есть) | ACTIVE | (fill if exists) |
| 02__DURATION_POLICY_CTL.md | DURATION_POLICY_CTL | Политика длительности (если есть) | ACTIVE | (fill if exists) |
| 03__STYLE_BOUNDARY_CTL.md | STYLE_BOUNDARY_CTL | Границы стиля (если есть) | ACTIVE | (fill if exists) |
| 04__STRUCTURE_GUARD_CTL.md | STRUCTURE_GUARD_CTL | Контроль структуры (если есть) | ACTIVE | (fill if exists) |
| 05__VARIATION_AXES_CTL.md | VARIATION_AXES_CTL | Оси вариативности (если есть) | ACTIVE | (fill if exists) |
| 06__OUTPUT_PACK_POLICY_CTL.md | OUTPUT_PACK_POLICY_CTL | Политика упаковки (если есть) | ACTIVE | (fill if exists) |
| 07__METADATA_POLICY_CTL.md | METADATA_POLICY_CTL | Политика метаданных (если есть) | ACTIVE | (fill if exists) |
| 08__CREATOR_POLICY_CTL.md | CREATOR_POLICY_CTL | Creator/UGC правила (если есть) | ACTIVE | (fill if exists) |
| 09__QUALITY_GATES_CTL.md | QUALITY_GATES_CTL | Гейты качества (если есть) | ACTIVE | (fill if exists) |
| 10__NOISE_POLICY_CTL.md | NOISE_POLICY_CTL | Лимиты/шум (если есть) | ACTIVE | (fill if exists) |
| 11__RUN_PROTOCOL_CTL.md | RUN_PROTOCOL_CTL | Протокол прогона (если есть) | ACTIVE | (fill if exists) |
| 12__NEGATIVE_SPEC_LIBRARY_CTL.md | NEGATIVE_SPEC_LIBRARY_CTL | Библиотека негатив-спек (если есть) | ACTIVE | (fill if exists) |
| 13__EXPORT_POLICY_CTL.md | EXPORT_POLICY_CTL | Экспорт/форматы (если есть) | ACTIVE | (fill if exists) |
| 14__STEP_BUDGET_CTL.md | STEP_BUDGET_CTL | Лимиты шагов/вариантов/проходов | ACTIVE | UE.V2.CTL.MUSIC.STEP_BUDGET.001 |
| 15__VARIANT_POLICY_CTL.md | VARIANT_POLICY_CTL | Правила полезных вариантов (оси различий) | ACTIVE | UE.V2.CTL.MUSIC.VARIANT_POLICY.001 |
| 16__FOCUS_LOOP_STOP_RULES_CTL.md | FOCUS_LOOP_STOP_RULES_CTL | Стоп/продолжать итерации | ACTIVE | UE.V2.CTL.MUSIC.FOCUS_LOOP_STOP.001 |
| 17__SYNTHESIS_MERGE_POLICY_CTL.md | SYNTHESIS_MERGE_POLICY_CTL | Политика смешивания компонентов | ACTIVE | UE.V2.CTL.MUSIC.SYNTHESIS_MERGE_POLICY.001 |

---

## [M] RULES
- Любой MUSIC пайп обязан использовать CTL 14–16 минимум.
- Для best-of синтеза обязателен CTL 17.

---

## [M] GATES
PASS если:
- новые CTL добавлены и индекс остаётся коротким
