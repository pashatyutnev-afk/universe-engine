# KB REL TYPES (DICTIONARY, CANON)
FILE: 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/91__KB_REL_TYPES.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: DICTIONARY
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.1.0
UID: UE.KB.DICT.REL_TYPES.001
OWNER: SYSTEM
ROLE: Canonical dictionary of KB relation types (UID-only, no navigation)

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MINOR
- SUMMARY: "REL made UID-only. Removed PATH/RAW/URL usage. Aligned with KB single-index and no-intermediate-links law."
- REASON: "Совместимость KB с собственным законом и глобальными стандартами."
- IMPACT: "Relations in KB passports/docs no longer depend on file paths."

---

## PURPOSE (LAW)
Определяет типы отношений (REL) между сущностями KB.

Ключевое:
- REL НЕ является навигацией.
- REL НЕ содержит PATH/RAW/URL.
- REL указывает TARGET строго по UID.

---

## FORMAT (ABSOLUTE)
Единственный допустимый формат:

REL: <REL_TYPE> | TARGET: <UID> | WHY: <reason>

RULES:
- WHY обязателен (1 строка, конкретно).
- TARGET всегда UID (строка).
- Никаких путей, ссылок, raw, URL.

---

## REL TYPES (BASE SET)

### DEFINES
Документ определяет правила/словарь/норму для TARGET.

### DEPENDS_ON
Документ зависит от TARGET (без него смысл/валидность ломается).

### EXTENDS
Документ расширяет TARGET (добавляет новые части, не отменяя исходное).

### IMPLEMENTS
Документ реализует требования/норму, заданные TARGET.

### REPLACES
Документ полностью заменяет TARGET (TARGET становится устаревшим).

### DEPRECATES
Документ объявляет TARGET устаревшим (TARGET сохраняется для истории).

### CONFLICTS_WITH
Документ конфликтует с TARGET (нужна явная развязка/приоритет).

### EXAMPLE_FOR
Документ служит примером/референсом для TARGET.

---

## REL GOVERNANCE NOTES
- REL не создаёт существование: existence определяется только KB master-index.
- Навигация по файлам (PATH/RAW) разрешена только в KB master-index.
- Внутри документов KB — только UID и WHY.

--- END.
