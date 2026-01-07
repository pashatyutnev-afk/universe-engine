# NAMING RULES — FILES / FOLDERS / IDENTIFIERS (CANON)
FILE: 01_SYSTEM_LAW/01__NAMING_RULES.md

SCOPE: Universe Engine
LAYER: 01_SYSTEM_LAW
DOC_TYPE: LAW
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.1.0
UID: UE.LAW.NAMING.001
OWNER: SYSTEM
ROLE: Defines canonical naming patterns for folders/files, index rules, numbering alignment, allowed exceptions, and legacy alias handling.

CHANGE_NOTE:
- DATE: 2026-01-07
- TYPE: MINOR
- SUMMARY: "Нормализованы правила именования: единый паттерн, связь индекса и имени файла, legacy-алиасы, запрет alt-index как канон"
- REASON: "Устранение коллизий и обеспечение машинной навигации"
- IMPACT: "Все слои и реестры"

---

## 0) PRIME GOAL
Именование должно обеспечивать:
- однозначную навигацию (человек + машина),
- соответствие индексу (номер/путь),
- совместимость с registry/index валидаторами,
- отсутствие дублей и “скрытых алиасов”.

---

## 1) CANONICAL FILE NAME PATTERN
### 1.1 Базовый паттерн (рекомендуемый и канонический)
**`NN__NAME.md`**
- `NN` — двухзначный номер (00..99)
- `__` — двойное подчёркивание (разделитель)
- `NAME` — UPPER_SNAKE_CASE (A–Z, 0–9, `_`)
- расширение `.md`

Пример:
- `00__INDEX__SYSTEM_LAW.md`
- `03__VERSIONING_CHANGE_POLICY.md`

### 1.2 Папки-слои
Папки слоёв и подслоёв — UPPER_SNAKE_CASE, допускаются цифры и `_`:
- `01_SYSTEM_LAW`
- `02_STANDARDS`
- `04_KNOWLEDGE_BASE`
- `00_KB_GOVERNANCE`

---

## 2) INDEX ↔ FILE NUMBER ALIGNMENT (ABSOLUTE)
### 2.1 Закон совпадения номера
Номер в индексе и номер в имени файла обязаны совпадать.

Пример (валидно):
- INDEX: `02 — UID Rules`
- FILE: `02__UID_RULES.md`

Пример (невалидно):
- INDEX: `02 — ...`
- FILE: `01__...md`

### 2.2 Один канонический entrypoint index на слой
На слой допускается **ровно один** канонический master-index (L1):
- `00__INDEX__<LAYER>.md` или иной формат, но он должен быть единственным зарегистрированным entrypoint.

Любые “alt index / legacy index”:
- либо удаляются,
- либо фиксируются как **NON-CANON ALIASES** (см. раздел 6).

---

## 3) SUFFIX RULES (A/B/…)
### 3.1 Когда разрешены буквенные суффиксы
Формат `NN[A-Z]__NAME.md` разрешён **только** для:
- TEMPLATE
- APPENDIX
- EXAMPLE

То есть: `05A__TEMPLATE__SCENE_PACK.md` допустимо, если это явно TEMPLATE/APPENDIX.

### 3.2 Запрет “бесконечных суффиксов”
Суффиксы не используются для “дробления SoT”.
Если нужен новый SoT — создаётся новый номер (NN) и регистрируется по Canon Protocol.

---

## 4) KB REALMS & SPECIAL CASES
### 4.1 Realm-файлы (KB)
Для realm-файлов Knowledge Base допускаются два режима:

**MODE A (рекомендуется):**
- `NN__REALM__NAME.md` (строго по общему паттерну)

**MODE B (временно допустим для миграции):**
- `NN_REALM_NAME.md` (одиночные `_` вместо `__`), но должен быть миграционный план и фикс в ближайшем MINOR.

### 4.2 Запрет конфликтов номеров в одной папке (ABSOLUTE)
В одной папке не может существовать два канонических файла, начинающихся с одного и того же `NN`, если они оба зарегистрированы в master-index.

Пример конфликта:
- `02_CHARACTER_CRAFT.md`
- `02__KB_TAGS.md`

Решение:
- либо переименовать один файл на другой номер,
- либо вынести в подпапку,
- либо зафиксировать исключение в этом документе (раздел 5) и описать мост в реестрах.

---

## 5) EXCEPTIONS REGISTRY (CONTROLLED)
Исключения допускаются только если:
- они перечислены в этом документе (в этом разделе),
- и имеют MIGRATION PLAN или постоянное обоснование.

### 5.1 CURRENT APPROVED EXCEPTIONS
(пусто — по умолчанию никаких исключений)

---

## 6) LEGACY / ALIAS HANDLING (NON-CANON)
### 6.1 Что такое legacy alias
Legacy/alias — файл, который существует для обратной совместимости, но:
- не является каноническим entrypoint,
- не может определять состав слоя,
- не может противоречить master-index.

### 6.2 Как оформлять legacy alias
Legacy alias должен быть:
- либо редиректом/указателем на канонический файл (кратко),
- либо удалён.

Запрещено:
- держать legacy alias как “второй индекс” и считать его равноправным.

---

## 7) CONTENT NAMING (HEADERS / SECTIONS)
- Заголовки H1 в документах должны совпадать по смыслу с названием документа.
- Разделы внутри файла именуются последовательно (0..N), где `0)` — purpose/law.

---

## 8) ENFORCEMENT (VALIDATION)
Нарушение Naming Rules = документ не может считаться каноничным, пока не исправлен:
- несоответствие номера,
- два master-index в одном слое,
- конфликт номеров в одной папке,
- неразрешённые суффиксы,
- “legacy index” зарегистрирован как канон.

---

## FINAL RULE (LOCK)
Эти правила обязательны для всех слоёв Universe Engine.
Любая правка — изменение канона и проходит Canon Protocol.
--- END.
