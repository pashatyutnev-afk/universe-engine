# CANON PROTOCOL — HOW CANON CHANGES (CANON)
FILE: 01_SYSTEM_LAW/04__CANON_PROTOCOL.md

SCOPE: Universe Engine
LAYER: 01_SYSTEM_LAW
DOC_TYPE: LAW_PROTOCOL
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.1.0
UID: UE.LAW.CANON.PROTOCOL.004
OWNER: SYSTEM
ROLE: Defines the mandatory process for changing canon: proposals, validation gates, index/registry updates, version bump rules, and merge requirements.

CHANGE_NOTE:
- DATE: 2026-01-07
- TYPE: MINOR
- SUMMARY: "Единый протокол изменения канона: заявка→дифф→валидации→обновление индексов→версия→фиксация"
- REASON: "Устранение хаоса и 'тихих' изменений"
- IMPACT: "Все слои и master-index документы"

---

## 0) PRIME LAW (ABSOLUTE)
Любая правка, которая влияет на канон, проходит Canon Protocol.
Канон — это зарегистрированные (в индексах) и валидные (по законам) документы/артефакты.

---

## 1) WHAT IS A CANON CHANGE?
Канон-изменение — любое изменение, которое затрагивает:
- состав master-index (добавление/удаление/переупорядочивание зарегистрированных файлов)
- смысл LAW/STANDARD (нормативные правила)
- SoT документы и их модульные расширения
- схемы артефактов и пайплайны
- UID/Naming/Versioning правила
- KB governance правила и реестры

Если сомневаешься — считать канон-изменением.

---

## 2) ROLES
- **Initiator** — кто предложил изменение.
- **Canon Owner (SYSTEM)** — владелец канона (финальная ответственность).
- **Reviewer** — проверяет соответствие законам (может быть человек или CI).
- **Maintainer** — применяет миграции/исправления/реестры.

---

## 3) CANON CHANGE PACKAGE (MANDATORY ARTIFACTS)
Любое канон-изменение обязано содержать:

1) **Diff**: что меняется (файлы/разделы).
2) **Canon Impact Summary**: какие слои/индексы/пайплайны затронуты.
3) **Version Bump**: обновление `VERSION` по SemVer и `CHANGE_NOTE` в затронутых канон-файлах.
4) **Index/Registry Update**: если меняется состав/путь — обновить мастер-индексы и реестры.
5) **No-Dup Proof**: подтверждение отсутствия дубля смысла (Single SoT).
6) **Migration Plan** (если MAJOR или требуется переименование/сдвиг структуры).

---

## 4) PROCESS (MANDATORY FLOW)
### Step 0 — Identify scope
Определи:
- слой (LAW / STANDARDS / KB / PIPE)
- тип изменения: PATCH / MINOR / MAJOR

### Step 1 — Create Proposal (Canon Change Request)
Минимальная форма:
- TITLE
- TARGET FILES
- CHANGE TYPE (PATCH/MINOR/MAJOR)
- WHY
- EXPECTED IMPACT
- MIGRATION (если нужно)

### Step 2 — Implement change
Правки выполняются в соответствии с:
- `00__SYSTEM_LAW.md` (Core)
- Naming Rules
- UID Rules
- Versioning & Change Policy

### Step 3 — Update indices/registries
Если добавлен файл, перемещён файл или изменён состав:
- обновить master-index слоя
- обновить связанные registries (если есть)

### Step 4 — Validation gates (must pass)
Перед фиксацией канона должны быть пройдены минимальные проверки:

**GATE A — Doc Control**
- полная шапка (SCOPE/LAYER/STATUS/LOCK/VERSION/UID/OWNER/ROLE)
- нет дубля OWNER/LOCK/VERSION внизу
- SemVer валиден

**GATE B — UID**
- UID существует и уникален
- UID не менялся без MAJOR + миграции

**GATE C — Naming**
- имя файла соответствует правилам (NN__...)
- номер в имени совпадает с номером в индексе

**GATE D — Existence**
- все зарегистрированные ссылки/пути реальны
- в слое один канонический master-index

**GATE E — Single SoT**
- нет дублей смысла
- modules не объявляют себя SoT при наличии SoT

### Step 5 — Lock canon
- У канон-файлов `LOCK: FIXED`.
- Черновики остаются `LOCK: OPEN` и не регистрируются в индексах.

---

## 5) SPECIAL CASES
### 5.1 Fast Patch (urgent fix)
Допускается fast patch (PATCH), если:
- исправляет явную ошибку/битые ссылки/Doc Control
- не меняет смысл норм
- не требует миграции

Но даже fast patch обязан:
- поднять PATCH версию
- обновить Change Note

### 5.2 Deprecation
Если документ устаревает:
- ставится `STATUS: DEPRECATED`
- обязателен `DEPRECATED_BY` (UID)
- указывается migration plan (если нужно)
- документ остаётся в индексе, но помечается как deprecated (если индекс поддерживает статусы)

### 5.3 Rename / Move
Переименование/перемещение:
- UID не меняется
- индексы обновляются
- ссылки обновляются
- версия повышается минимум PATCH (иногда MINOR)

---

## 6) STOP CONDITIONS (CANON MUST NOT MERGE)
Запрещено фиксировать канон, если:
- есть два master-index в одном слое
- есть конфликт номеров в папке (два канонических `NN*` в одном каталоге)
- отсутствует UID у зарегистрированного документа
- нарушен SemVer
- есть дубль смысла (две SoT про одно)
- raw-ссылки в индексах сломаны (если слой использует raw как canonical refs)

---

## 7) OUTPUT OF CANON CHANGE
После принятия изменения:
- канонические файлы обновлены по версии и change note
- индексы актуальны
- миграции либо выполнены, либо имеют зафиксированный план
- non-canon алиасы/legacy не влияют на навигацию

---

## FINAL RULE (LOCK)
Canon Protocol обязателен для любых изменений, которые затрагивают канон.
Нарушение протокола = изменение считается неканоничным и подлежит откату/исправлению.
--- END.
