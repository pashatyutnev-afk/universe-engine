# KB REL TYPES (DICTIONARY, CANON)
FILE: 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/91__KB_REL_TYPES.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: DICTIONARY
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.DICT.REL_TYPES.001
OWNER: SYSTEM
ROLE: Словарь типов отношений между сущностями KB (UID-only)

---

## PURPOSE
Определяет стандартные типы связей (REL) для паспортов и перекрёстных указаний.
REL — это семантика связи, не ссылка.

---

## REL FORMAT (MANDATORY)
- REL: <REL_TYPE> | TARGET: <UID> | WHY: <reason>

---

## REL TYPES (BASE SET)

### DEFINES
Этот документ определяет правила/словарь для TARGET.

### DEPENDS_ON
Этот документ зависит от TARGET (без него смысл ломается).

### EXTENDS
Этот документ расширяет TARGET (добавляет слой/часть).

### CONFLICTS_WITH
Этот документ конфликтует с TARGET (нужно разрешение конфликта).

### REPLACES
Этот документ заменяет TARGET.

### DEPRECATES
Этот документ объявляет TARGET устаревшим.

### IMPLEMENTS
Этот документ реализует норму/требование, описанное в TARGET.

### EXAMPLE_FOR
Этот документ служит примером для TARGET.

---

## RULES
- REL всегда указывает TARGET по UID.
- REL не содержит URL/путей.
- REL не является навигацией по файлам.

--- END.
