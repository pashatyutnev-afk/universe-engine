# INDEX STRUCTURE SPEC (CANON)
FILE: 02_STANDARDS/01_SPECIFICATIONS/09__INDEX_STRUCTURE_SPEC.md

SCOPE: Universe Engine
LAYER: 02_STANDARDS
DOC_TYPE: SPEC
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.1.0
UID: UE.STD.SPEC.INDEX_STRUCTURE.001
OWNER: SYSTEM
ROLE: Defines allowed index models (multi-index vs strict single-index) and compatibility rules

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MINOR
- SUMMARY: "Introduced STRICT SINGLE-INDEX mode as compatible option. Clarified that sub-indexes are optional and may be banned by a layer."
- REASON: "Совместимость с KB (single-index, no intermediate links) и устранение конфликтов 'standards vs strict layers'."
- IMPACT: "Layers can choose strict or flexible indexing without breaking global rules."

---

## PURPOSE (LAW)
Определяет допустимые модели индексирования в слоях Universe Engine.

Важно:
- “INDEX” бывает разного типа (master-map, registry, dictionary).
- Слой может выбрать строгую модель (single-index) или гибкую (multi-index).

---

## INDEX TYPES (DEFINITIONS)

### MASTER INDEX (ENTRYPOINT)
Единая точка входа слоя.
- Может быть единственным SoT по existence/nav.

### REGISTRY (CATALOG)
Справочный список сущностей/доков, не обязательно навигация.
- Не должен конкурировать с master-index по existence.

### DICTIONARY (VOCABULARY)
Словари терминов/типов/перечислений.
- Не nav и не existence.

### SUB-INDEX (OPTIONAL)
Локальное оглавление/карта внутри зоны.
- Разрешено только если слой это допускает.
- В strict mode запрещено.

---

## TWO COMPATIBLE MODELS

### MODEL A — FLEX (MULTI-INDEX)
Допускаются:
- master index слоя (entrypoint)
- registry / dictionaries
- локальные sub-indexes (по необходимости)

Условия совместимости:
- master index должен явно определять authority по existence/nav
- registry не должен заявлять, что он SoT по existence

### MODEL B — STRICT (SINGLE-INDEX / NO-SUB-INDEX)
Запрещены:
- любые sub-indexes как оглавления/реестры
- любые промежуточные навигационные ссылки вне одного master-index (если слой так решил)

Разрешено:
- один master-index = единственный SoT по existence/nav
- dictionaries внутри governance (без навигации)

Это валидная модель и считается совместимой со стандартами при соблюдении UID-first.

---

## GLOBAL COMPATIBILITY RULE (MINIMUM)
Независимо от модели:
- XREF и REL должны быть UID-first:
  - XREF: <UID> | WHY: ...
  - REL: <TYPE> | TARGET: <UID> | WHY: ...

PATH/URL могут быть:
- опциональны (flex model)
- запрещены (strict model)

---

## ANTI-CONFLICT RULES
- Нельзя иметь два SoT по existence внутри одного слоя.
- Нельзя, чтобы registry/index объявлял existence, если слой выбрал strict single-index.
- Любой слой обязан документально объявить свою модель (A или B) в governance.

--- END.
