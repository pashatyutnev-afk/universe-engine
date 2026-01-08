# KB ENTITY TYPES (DICTIONARY, CANON)
FILE: 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/03__INDEX__KB_ENTITY_TYPES.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: INDEX
INDEX_TYPE: DICTIONARY
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.IDX.DICT.ENTITY_TYPES.001
OWNER: SYSTEM
ROLE: Справочник типов сущностей KB (НЕ навигация и НЕ реестр существования)

---

## PURPOSE
Определяет допустимые типы сущностей KB для паспортов и структурирования знаний.
Не является индексом существования.

---

## ENTITY TYPE LIST (ALLOWED)

### ENTITY: TOPIC
Сущность “тема” (файл в topics).
- Используется для практик, гайдов, техник, локальных правил.

### ENTITY: REALM
Сущность “область знаний”.
- Используется для крупных сводов и обзорных слоёв.

### ENTITY: RULE
Сущность “правило”.
- Используется для нормативных законов/ограничений.

### ENTITY: DICTIONARY
Сущность “словарь”.
- Используется для системных перечислений: tags, rel types, xref rules.

### ENTITY: TEMPLATE
Сущность “шаблон”.
- Используется для стандартных заготовок документов.

### ENTITY: PROCESS
Сущность “процесс/flow”.
- Используется для процедур: create flow, review flow.

### ENTITY: CONTROL
Сущность “контроль/стандарты”.
- Используется для doc control, quality control.

---
3) Любые другие index-файлы как NAV/EXISTENCE реестр ЗАПРЕЩЕНЫ.
   - Запрещено: любые sub-indexes в любых подпапках (особенно вне `00_KB_GOVERNANCE/`),
     которые пытаются быть оглавлением/реестром существования/навигацией.
   - Примеры запрещённого: `*/00__INDEX__*.md`, `*/_index.md`, `*/00_INDEX*.md`,
     и любые `INDEX*.md` вне `00_KB_GOVERNANCE/` если они не DICTIONARY.
   - Разрешено: governance-словари внутри `00_KB_GOVERNANCE/` (в т.ч. с `INDEX` в имени),
     но они НЕ имеют authority по existence/nav.

## REQUIRED FIELDS (WHEN PASSPORT IS USED)
Если сущность оформляется паспортом (см. шаблон), обязательны:
- UID
- NAME
- ENTITY_TYPE (из списка выше)
- STATUS
- SUMMARY
- RELATIONS (если применимо)

--- END.
