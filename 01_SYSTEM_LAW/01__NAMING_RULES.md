# NAMING RULES — GLOBAL FILE/FOLDER NAMING LAW (SoT)
FILE: 01_SYSTEM_LAW/01__NAMING_RULES.md

SCOPE: Universe Engine
LAYER: 01_SYSTEM_LAW
DOC_TYPE: LAW
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.2.0
UID: UE.LAW.NAMING.RULES.001
OWNER: SYSTEM
ROLE: Single source of truth for canonical file/folder naming, numbering, allowed characters, collision prevention, and alias-pointer migrations

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MINOR
- SUMMARY: "Зафиксированы допустимые символы, единый NN__ формат, правила папок семейств, запрет мусора (пробелы/скобки/кракозябры), и обязательный alias-pointer при переносах"
- REASON: "Переносимость, автоматизация, отсутствие коллизий, стабильные raw-ссылки"
- IMPACT: "Все новые файлы/папки и любые миграции обязаны соответствовать"

---

## 0) PURPOSE (LAW)
Naming Rules обеспечивают:
- строгий порядок навигации (by number)
- отсутствие коллизий в папках
- переносимость путей (Windows/Linux/macOS)
- возможность линтинга/валидатора
- безопасные переименования без поломки ссылок (alias-pointer)

---

## 1) ALLOWED CHARACTERS (HARD)

### 1.1 For file & folder names
Разрешены только:
- латиница: `A-Z a-z`
- цифры: `0-9`
- подчёркивание: `_`
- дефис: `-` (разрешён, но предпочтение `_`)
- точка `.` только как часть расширения файла (например `.md`)

Запрещено:
- пробелы
- скобки `()`
- кавычки, запятые, двоеточия, `&`, `+`, `=`, `#`, `@` и прочие спецсимволы
- кириллица в именах файлов/папок
- “битая кодировка” / нечитаемые символы

Нарушение в каноническом слое = **NON-CANON** до исправления.

---

## 2) NUMBERING FORMAT (HARD)

### 2.1 Canon numbered file pattern
Если папка использует упорядочивание, то канонический формат файла:

`NN__NAME.md`

Где:
- `NN` = `00..99`
- `NAME` = `UPPER_SNAKE_CASE` (рекомендуется) или `Title_Case` (если уже так принято), но **единый стиль внутри папки обязателен**

### 2.2 Reserved number `00__`
`00__` зарезервирован под:
- `00__INDEX__...` (master-index слоя/папки)
- `00__README__...` (realm/readme)
- `00__TEMPLATE__...` (базовые templates папки)
- другие entrypoint’ы, если явно разрешено master-index’ом папки

В одной папке допускается несколько `00__*` только если:
- это заранее описано в master-index’е папки как допустимый набор entrypoints
иначе это считается **коллизией**.

---

## 3) COLLISION RULE (HARD)
В одной папке запрещено:
- два файла с одинаковым номером `NN`
- два файла с одинаковым именем (без учёта регистра)
- два разных “entrypoint’а” с номером `00__`, если это не разрешено правилами папки

При коллизии:
- выбирается один канонический путь/файл
- остальные переводятся в alias-pointer или DEPRECATED/ARCHIVED (см. §6)

---

## 4) CANON NAMING PATTERNS (STANDARD)

### 4.1 Laws / Standards / Protocols / Indexes
Рекомендуемые паттерны (не догма, но единообразие обязательно внутри папки):

- LAW: `NN__TOPIC.md`
- STANDARD: `NN__TOPIC_STANDARD.md`
- PROTOCOL: `NN__TOPIC_PROTOCOL.md` или `NN__TOPIC.md` (если так принято)
- INDEX: `00__INDEX__<SCOPE_OR_LAYER>.md`

Главное правило: номер в имени файла отражает порядок навигации.

---

### 4.2 Templates
Канонический шаблон:

`NN__TEMPLATE__SUBJECT.md`

Опционально, если важно указать класс:
`NN__TEMPLATE__<CLASS>__SUBJECT.md`

Где `<CLASS>` ∈ `ENG|ORC|SPC|CTL|VAL|QA|KB|PRJ|AST|DOC`.

---

### 4.3 System Entities (ENG/ORC/SPC/CTL/VAL/QA)
Канонический файл сущности:

`NN__NAME_<CLASS>.md`

Примеры:
- `01__AUDIT_LOG_ENG.md`
- `07__DIALOGUE_ENG.md`
- `04__DOC_CONTROLLER_SPC.md`

---

## 5) FOLDER NAMING (HARD)

### 5.1 Layer folders
Имена слоёв фиксируются как:
`NN_LAYER_NAME` (как у тебя: `01_SYSTEM_LAW`, `02_STANDARDS`, ...)

### 5.2 Family folders (пример ENG)
Формат:
`NN_FAMILY_NAME_ENGINES`

Пример:
`00_GOVERNANCE_ENGINES`

Правило:
- `NN` семейства должен совпадать с порядком семейства в master-index (например `02__INDEX_ALL_ENGINES.md`).

---

## 6) ALIAS-POINTER MIGRATION RULE (HARD)
Любое переименование или перенос файла обязаны использовать безопасную миграцию:

1) Создаётся новый файл в новом каноническом пути/имени.
2) Старый файл **не удаляется сразу**.
3) Старый файл превращается в alias-pointer:
   - `STATUS: DEPRECATED`
   - `LOCK: FIXED`
   - короткий текст: `Moved to: <CANON_PATH>` и/или `RAW: <link>`
4) Master-index обновляется:
   - новый путь становится каноническим
   - старый путь фиксируется как legacy alias (если слой это поддерживает)

Цель: не ломать raw-ссылки и внешние упоминания.

---

## 7) BROKEN PATH ZERO-TOLERANCE (HARD)
Файлы/папки с:
- пробелами
- скобками
- “кракозябрами”
- невалидной кодировкой

должны быть нормализованы через §6 (перенос + alias-pointer).
Оставлять их как канонический путь запрещено.

---

## FINAL RULE (LOCK)
LOCK: FIXED
--- END.
