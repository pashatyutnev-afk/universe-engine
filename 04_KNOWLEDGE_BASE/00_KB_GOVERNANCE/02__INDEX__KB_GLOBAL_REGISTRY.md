# KB GLOBAL REGISTRY (DICTIONARY, CANON)
FILE: 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/02__INDEX__KB_GLOBAL_REGISTRY.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: INDEX
INDEX_TYPE: DICTIONARY
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.IDX.DICT.GLOBAL_REGISTRY.001
OWNER: SYSTEM
ROLE: Справочник понятий и системных объектов KB (НЕ реестр существования)

---

## PURPOSE (IMPORTANT)
Этот документ — словарь/справочник терминов и системных объектов KB.
Он НЕ является:
- навигационным индексом
- реестром существования
- источником истины по структуре

SoT по существованию и навигации — только главный индекс:
- UID: UE.KB.IDX.MASTER.001

---

## DEFINITIONS (SYSTEM OBJECTS)

### KB Document
Любой файл KB с обязательной шапкой и UID.

### Canon
Множество документов, перечисленных в главном индексе.

### NON-CANON
Файл, который существует в репозитории, но не зарегистрирован в главном индексе.

### Governance Docs
Документы, задающие правила, форматы и контроль KB.
Не определяют существование.

### Content Docs
Документы знаний (realms/topics).
Могут ссылаться только через XREF по UID.

### Alias
Legacy pointer документ (98/99), который не содержит контента.
Содержит только указание на главный индекс по UID.

---

## SYSTEM UIDS (REFERENCE ONLY)
Ниже перечислены системные “якоря” (для удобства ссылок по UID, без навигации):

- Main KB Index: UE.KB.IDX.MASTER.001
- KB Rules: UE.KB.RULES.001
- KB Storage Map: UE.KB.MAP.STORAGE.001
- KB Create Flow: UE.KB.FLOW.CREATE.001
- KB Doc Control: UE.KB.CTRL.DOC.001
- KB Tags Dictionary: UE.KB.DICT.TAGS.001
- KB REL Types Dictionary: UE.KB.DICT.REL_TYPES.001
- KB XREF Rules: UE.KB.DICT.XREF_RULES.001
- KB Entity Types Dictionary: UE.KB.IDX.DICT.ENTITY_TYPES.001

NOTE:
Это НЕ реестр существования файлов. Это только справочный список UID якорей.

--- END.
