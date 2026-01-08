# KB CREATE FLOW (CANON)
FILE: 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/06__KB_CREATE_FLOW.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: FLOW
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.FLOW.CREATE.001
OWNER: SYSTEM
ROLE: Процесс создания новых KB документов (без под-индексов и промежуточных ссылок)

---

## PURPOSE (LAW)
Дать один корректный путь создания новых документов KB.
Этот flow НЕ создаёт локальные индексы и НЕ использует навигационные ссылки, кроме главного индекса.

---

## RULES (MUST)

### R1 — Register Only in Main Index
Новый документ считается каноном только после регистрации в:
- `04_KNOWLEDGE_BASE/00__INDEX__KNOWLEDGE_BASE.md`

### R2 — No Sub-Indexes
Запрещено создавать любые локальные индексы/реестры “для удобства”.

### R3 — No Intermediate Links
Запрещено добавлять PATH/RAW/URL ссылки в любой документ кроме главного индекса.
Внутри контент-доков разрешены только XREF по UID (без ссылок).

---

## CREATE STEPS (STANDARD)

### STEP 1 — Choose type
Выбери тип документа:
- REALM (крупная область) → файл в корне `04_KNOWLEDGE_BASE/` в диапазоне 01..08
- TOPIC (конкретная тема) → файл в `04_KNOWLEDGE_BASE/10_TOPICS/`
- GOVERNANCE (правила/контроль) → файл в `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/`
- ALIAS (legacy pointer) → файл 98/99 в корне

### STEP 2 — Name file
Имя файла:
- читаемое, стабильное, без “временных” названий
- префиксы диапазонов соблюдать (01..08, 10_TOPICS, 98/99)

### STEP 3 — Fill mandatory header
Каждый новый документ должен иметь шапку:
SCOPE / LAYER / DOC_TYPE / LEVEL / STATUS / LOCK / VERSION / UID / OWNER / ROLE

### STEP 4 — Content rules
- Не вставлять PATH/RAW/URL ссылки.
- Для перекрёстных ссылок использовать XREF по UID:
  `XREF: <UID> | WHY: <reason>`

### STEP 5 — Register in main index
Добавить в `00__INDEX__KNOWLEDGE_BASE.md`:
- NAME (человеческое имя)
- PATH (путь)
- RAW (ссылка на raw) — ТОЛЬКО здесь разрешена навигация

Без регистрации в главном индексе файл считается NON-CANON.

### STEP 6 — Optional: alias
Если нужен alias (legacy):
- он не содержит контент
- он содержит только pointer на главный индекс

---

## DEPRECATION NOTE
Любые исторические локальные индексы должны быть удалены.
Главный индекс — единственный entrypoint.

--- END.
