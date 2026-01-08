# KB GLOBAL REGISTRY (DICTIONARY, CANON)
FILE: 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/02__INDEX__KB_GLOBAL_REGISTRY.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: DICTIONARY
INDEX_TYPE: REGISTRY_CATALOG
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.1.0
UID: UE.KB.IDX.DICT.GLOBAL_REGISTRY.001
OWNER: SYSTEM
ROLE: KB catalog of system anchors (UID-only; not existence; not navigation)

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MINOR
- SUMMARY: "Removed PATH/RAW/URL from registry. Registry is UID-only catalog. Removed footer metadata duplication."
- REASON: "KB strict mode: no intermediate navigation outside master-index."
- IMPACT: "Registry no longer competes with master-index for navigation."

---

## PURPOSE (IMPORTANT)
Этот документ — справочник/каталог системных “якорей” KB по UID.
Он НЕ является:
- навигационным индексом
- реестром существования файлов
- вторым entrypoint

SoT по существованию и навигации KB:
- UID: UE.KB.IDX.MASTER.001

---

## CATALOG FORMAT (UID-ONLY)
Каждая запись должна быть UID-first и без путей:

- UID: <UID>
  NAME: <name>
  TYPE: <RULE|DICTIONARY|TEMPLATE|CONTROL|README|MAP|FLOW>
  NOTES: <optional>

---

## SYSTEM ANCHORS (REFERENCE)

- UID: UE.KB.IDX.MASTER.001
  NAME: KB Master Index
  TYPE: INDEX
  NOTES: Единственная навигация/существование KB.

- UID: UE.KB.README.REALM.001
  NAME: KB Realm README
  TYPE: README

- UID: UE.KB.MAP.STORAGE.001
  NAME: KB Storage Map
  TYPE: MAP

- UID: UE.KB.RULES.001
  NAME: KB Rules
  TYPE: RULE

- UID: UE.KB.FLOW.CREATE.001
  NAME: KB Create Flow
  TYPE: FLOW

- UID: UE.KB.CTRL.DOC.001
  NAME: KB Doc Control
  TYPE: CONTROL

- UID: UE.KB.TPL.ENTITY_PASSPORT.001
  NAME: KB Entity Passport Template
  TYPE: TEMPLATE

- UID: UE.KB.DICT.TAGS.001
  NAME: KB Tags Dictionary
  TYPE: DICTIONARY

- UID: UE.KB.DICT.REL_TYPES.001
  NAME: KB REL Types Dictionary
  TYPE: DICTIONARY

- UID: UE.KB.DICT.XREF_RULES.001
  NAME: KB XREF Rules Dictionary
  TYPE: DICTIONARY

---

## RULES
- Этот каталог не содержит PATH/RAW/URL.
- Этот каталог не вводит существование.
- Любые файлы/пути/RAW перечисляются только в KB master-index.

--- END.
