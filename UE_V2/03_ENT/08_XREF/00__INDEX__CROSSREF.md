# 00__INDEX__CROSSREF

SCOPE: Universe Engine (UE_V2)
DOC_TYPE: INDEX (REALM)
UID: UE.V2.XREF.INDEX.001
VERSION: 1.1.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
NAV_RULE: Use RAW links only
PURPOSE: Каталог XREF карт. Единственный вход в CROSSREF реалм.

---

## [M] ENTRYPOINT
- UE_V2/03_ENT/08_XREF/00__README__CROSSREF.md
- UE_V2/04_NAV/09__IDX_XREF.md

---

## [M] INDEX TABLE
| FILE | MAP_NAME | PURPOSE | STATUS |
|---|---|---|---|
| 01__MAP_ENG_to_ORC.md | MAP_ENG_to_ORC | Кто какие ENG вызывает (общие связи) | ACTIVE |
| 02__MAP_ORC_to_SPC.md | MAP_ORC_to_SPC | Как ORC подключает SPC (иерархия) | ACTIVE |
| 03__MAP__VALIDATION_MATRIX.md | MAP__VALIDATION_MATRIX | Обязательные CTL/VAL/QA по артефактам | ACTIVE |
| 04__MAP__PIPELINES.md | MAP__PIPELINES | Какой артефакт -> какой PIPE/ORC/режим | ACTIVE |
| 05__MAP__ENTITY_IO_TYPES.md | MAP__ENTITY_IO_TYPES | Совместимость по IO типов | ACTIVE |
| 06__MAP__KB_SCOPE_BINDINGS.md | MAP__KB_SCOPE_BINDINGS | Привязки сущностей к KB scopes | ACTIVE |
| 07__MAP__COVERAGE_TO_ENTITIES.md | MAP__COVERAGE_TO_ENTITIES | Pillars -> роли/капабилити | ACTIVE |
| 08__MAP__DEFAULT_CHAIN.md | MAP__DEFAULT_CHAIN | Базовая цепочка ролей и токенов | ACTIVE |

---

## [M] RULES
- Вся маршрутизация и обязательность проверок живёт здесь.
- Любые изменения фиксировать в CHANGE_LOG.

---

## [M] GATES
PASS если:
- индекс содержит все карты и остаётся коротким
