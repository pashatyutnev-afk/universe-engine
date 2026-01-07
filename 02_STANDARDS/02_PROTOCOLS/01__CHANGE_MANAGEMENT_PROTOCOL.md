# CHANGE MANAGEMENT PROTOCOL (STANDARDS)
FILE: 02_STANDARDS/02_PROTOCOLS/01__CHANGE_MANAGEMENT_PROTOCOL.md

SCOPE: Universe Engine
LAYER: 02_STANDARDS
DOC_TYPE: PROTOCOL
INDEX_TYPE: OPERATIONAL
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.PROTO.STD.CHANGE_MANAGEMENT.001
OWNER: SYSTEM
ROLE: Operational protocol for proposing, reviewing, approving, implementing, and logging changes across the repo

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Протокол нормализован под Doc Control + Naming (NN__) и приведён к минимальному каноническому пайплайну изменений"
- REASON: "Нужен единый и простой процесс изменений как фундамент для всех слоёв"
- IMPACT: "Любая правка канона теперь обязана проходить этот протокол"

---

## 0) PURPOSE
Этот протокол описывает **как вносить изменения** в Universe Engine безопасно и без разрушения канона.

Он обязателен для:
- новых файлов
- переименований/переносов
- изменения правил/стандартов/индексов
- массовых миграций

---

## 1) DEFINITIONS (MINIMAL)
- **CANON** — то, что зарегистрировано в master-index слоя и соответствует Doc Control.
- **ALIAS POINTER** — legacy-файл, который не содержит содержания, а только указывает на новый канон-путь.
- **SoT** — Single source of truth (главный документ смысла).
- **DRAFT** — подготовка, не канон.
- **ACTIVE** — канон.
- **DEPRECATED** — канон прошлого, заменён.
- **FIXED** — заморожен, правки только через Canon Protocol.

---

## 2) CHANGE CLASSES (STANDARD)
- **PATCH** — правка текста без изменения смысла/структуры/путей.
- **MINOR** — добавление совместимое (новый раздел, новый файл без ломки).
- **MAJOR** — ломающее изменение (переименование/перенос/смена правил/структуры).

---

## 3) REQUIRED ARTIFACTS (ALWAYS)
Любое изменение должно иметь минимум:

1) **CHANGE_NOTE** (в шапке затронутых файлов)  
2) **Registry update**:
   - master-index слоя (existence)
   - doc-registry слоя (учёт/UID/версии) — если применимо
3) **Audit trail**:
   - запись в `99_LOGS/LOG__CHANGES.md` (если это системная миграция)
   - и/или в `99_LOGS/LOG__AUDIT.md` (если затронуты законы/индексы)

---

## 4) CANON CHANGE PIPELINE (MANDATORY FLOW)
0) **Classify**: PATCH / MINOR / MAJOR.
1) **Impact scan**: какие слои/индексы/UID затрагиваются.
2) **Plan**: список файлов:
   - create / edit / rename / alias / deprecate
4) **Implement**:
   - правки файлов
   - создание alias-pointer для переименований
5) **Register**:
   - обновить master-index слоя (existence)
   - обновить doc-registry слоя
6) **Log**:
   - добавить запись в audit/changelog
7) **Freeze** (если канон):
   - `STATUS: ACTIVE`, `LOCK: FIXED`

---

## 5) RENAMES (HARD RULE)
Переименование/перенос **всегда** делается так:
- создаётся новый файл в канон-пути
- старый файл превращается в `DOC_TYPE: ALIAS_POINTER`, `STATUS: DEPRECATED`, `LOCK: FIXED`
- alias содержит только: CANON PATH + RAW link

Запрещено:
- удалять старый файл сразу (если он был публично доступен по raw)
- оставлять “полу-копию” (часть текста в alias)

---

## 6) CHANGE BLOCKERS (STOP RULES)
Изменение запрещено, если:
- ломает existence rule (файл удалён без регистрации)
- создаёт дубли смысла (2 SoT на одну тему)
- создаёт коллизии нумерации (NN конфликт внутри папки)
- добавляет второй OWNER/LOCK/VERSION вне шапки

---

## FINAL RULE (LOCK)
Этот протокол обязателен для всех изменений канона.
--- END.
