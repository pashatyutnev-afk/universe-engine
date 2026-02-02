FILE: UE_V2/03_ENT/90_XREF/05__MAP__ENTITY_IO_TYPES__XREF.md
SCOPE: Universe Engine (UE_V2)
DOC_TYPE: XREF_SCHEMA_MAP
DOMAIN: XREF
UID: UE.V2.XREF.ENTITY_IO_TYPES.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-01-30
OWNER: SYS

---

# XREF — ENTITY IO TYPES

PURPOSE:
Нормализует типы входов/выходов, чтобы ORC мог стыковать сущности без фантазии.

---

## INPUT TYPES
| TYPE | DESCRIPTION |
|---|---|
| TASK_TEXT | текст задачи пользователя |
| BRIEF_TOKEN | краткий бриф |
| ROUTE_TOKEN | токен маршрута (domain, artifact_type, pipe, checks) |
| KB_TOKEN | знания/ограничения из KB |
| STYLE_TOKEN | стиль/тон/референсы |
| STRUCTURE_TOKEN | структура артефакта |
| DRAFT_ARTIFACT | черновой результат |
| FINAL_ARTIFACT | финальный результат |
| VALIDATION_REPORT | отчёт проверок |
| DECISION_TOKEN | решение/выбор |

---

## OUTPUT TYPES
| TYPE | DESCRIPTION |
|---|---|
| OUTPUT_PACK | упакованный артефакт |
| RUN_LOG_ENTRY | запись прогона |
| DECISION_LOG_ENTRY | запись решения |
| TOKEN_ARCHIVE_ENTRY | архив токенов |
