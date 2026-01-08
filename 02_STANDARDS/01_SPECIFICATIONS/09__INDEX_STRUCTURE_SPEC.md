# INDEX STRUCTURE SPEC (CANON)
FILE: 02_STANDARDS/01_SPECIFICATIONS/09__INDEX_STRUCTURE_SPEC.md

SCOPE: Universe Engine
LAYER: 02_STANDARDS
DOC_TYPE: SPEC
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.2.0
UID: UE.STD.SPEC.INDEX_STRUCTURE.001
OWNER: SYSTEM
ROLE: Allowed index models + compatibility rules (flex vs strict)

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MINOR
- SUMMARY: "Added STRICT SINGLE-INDEX model as compatible option. Clarified sub-indexes optional and may be banned by a layer."
- REASON: "Устранение конфликтов Standards vs KB strict mode."
- IMPACT: "Layers can choose strict or flex without breaking global rules."

---

## PURPOSE
Определяет допустимые модели индексирования в слоях Universe Engine.

---

## INDEX TYPES (DEFINITIONS)
- MASTER INDEX (ENTRYPOINT): единая точка входа слоя
- REGISTRY (CATALOG): справочник, не existence/nav
- DICTIONARY (VOCABULARY): словарь терминов/типов
- SUB-INDEX: локальное оглавление (опционально)

---

## TWO COMPATIBLE MODELS

### MODEL A — FLEX (MULTI-INDEX)
- master index + registries/dictionaries
- sub-indexes могут существовать

Условие:
- один SoT по existence/nav, явно объявленный.

### MODEL B — STRICT (SINGLE-INDEX / NO-SUB-INDEX)
- один master-index = единственный SoT по existence/nav
- sub-indexes запрещены
- ссылки/пути могут быть запрещены вне master-index

Это валидная и совместимая модель при соблюдении UID-first.

---

## GLOBAL MINIMUM (MUST)
- XREF UID-first: `XREF: <UID> | WHY: ...`
- REL UID-first: `REL: <TYPE> | TARGET: <UID> | WHY: ...`

--- END.
