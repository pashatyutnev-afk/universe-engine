# CHANGE MANAGEMENT PROTOCOL (CANON)

FILE: 02_STANDARDS/02_PROTOCOLS/01__CHANGE_MANAGEMENT_PROTOCOL.md
SCOPE: Universe Engine
LAYER: 02_STANDARDS
DOC_TYPE: PROTOCOL
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.2.0
UID: UE.PROTO.CHANGE.001
OWNER: SYSTEM
ROLE: Canon protocol for proposing, executing, recording, and validating changes across controlled documents, entities, templates, indexes, registries, and KB modules. Enforces deterministic CHANGE_ID discipline, version bump rules, and signoff chain.

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: PATCH
- SUMMARY: "Normalized CHANGE_ID discipline + deterministic version bump rules + mandatory signoff chain and log/registry update obligations."
- REASON: "Changes were occurring without consistent IDs, version bumps, and auditability."
- IMPACT: "Every change becomes traceable, reviewable, and reversible by policy."
- CHANGE_ID: UE.CHG.2026-01-20.PROTO.CHANGE.001

---

## 0) PURPOSE (LAW)
Этот протокол отвечает на вопрос: как менять систему так, чтобы:
- изменения были воспроизводимы и аудируемы
- версии и CHANGE_ID не ломались
- индексы/реестры/пайплайны не расходились
- не появлялись “призрачные” документы без регистрации

---

## 1) SCOPE
Применяется ко всем контролируемым документам и сущностям:
- SYSTEM LAW (01_SYSTEM_LAW)
- STANDARDS / PROTOCOLS (02_STANDARDS)
- SYSTEM ENTITIES (03_SYSTEM_ENTITIES)
- KNOWLEDGE BASE (04_KNOWLEDGE_BASE)
- PROJECTS / DATABASES / LOGS (05/08/99)
- INDEX documents (ROOT, MASTER, sub-indexes)
- Templates / Registries

---

## 2) ABSOLUTE LAWS
### 2.1 No-guessing change
Нельзя “поправить по ощущениям” без фиксации:
- что именно меняется
- почему меняется
- какой эффект ожидается
- где будет отражено (лог/реестр/индекс)

### 2.2 One change = one CHANGE_ID
Любое атомарное изменение (commit-sized) обязано иметь один CHANGE_ID.

### 2.3 Version bump is mandatory
Любая правка controlled document обязана менять VERSION.

### 2.4 Signoff chain is mandatory
Изменение считается завершённым только после signoff цепочки (см. 7).

---

## 3) CHANGE TYPES (CANON)
### PATCH
- исправление формулировок, структуры, опечаток
- добавление уточнений без изменения контрактов
- фиксы ссылок/маркировки, которые не меняют смысл интерфейса

### MINOR
- добавление новых правил/секций
- расширение контрактов (новые поля) без ломания старых
- добавление новых сущностей/шаблонов/чеклистов

### MAJOR
- ломающее изменение контракта/интерфейса
- переименование, перемещение с обязательной миграцией ссылок
- изменение порядка/обязательности гейтов, влияющее на пайплайны

---

## 4) VERSIONING RULES (DETERMINISTIC)
Версия: `MAJOR.MINOR.PATCH`

- PATCH: увеличить PATCH на +1
- MINOR: увеличить MINOR на +1, PATCH сбросить в 0
- MAJOR: увеличить MAJOR на +1, MINOR=0, PATCH=0

Запрещено менять версию “как попало”.

---

## 5) CHANGE_ID RULES (DETERMINISTIC)
### 5.1 Format (required)
`UE.CHG.YYYY-MM-DD.<SCOPE_TAG>.<SEQ>`

Пример:
`UE.CHG.2026-01-20.PROTO.CHANGE.001`

### 5.2 Scope tags (recommended)
- ROOTIDX
- START
- LAW
- STD
- PROTO
- ENT
- KB
- ORC
- CTL
- VAL
- QA
- DB
- LOG

### 5.3 Sequencing (required)
SEQ — трёхзначный счётчик для данного дня и scope tag.
Если в один день несколько изменений одного scope tag — инкрементировать SEQ.

---

## 6) REQUIRED CHANGE NOTE BLOCK (IN EVERY CONTROLLED DOC)
Каждый controlled document обязан содержать блок:

CHANGE_NOTE:
- DATE: YYYY-MM-DD
- TYPE: PATCH | MINOR | MAJOR
- SUMMARY: "..."
- REASON: "..."
- IMPACT: "..."
- CHANGE_ID: UE.CHG....

Если блока нет или он неполный → документ считается некорректным.

---

## 7) SIGNOFF CHAIN (REQUIRED)
Минимальная цепочка при внесении изменений:

1) DOC_CONTROLLER_SPC
- проверяет DOC CONTROL блок, версию, CHANGE_NOTE, ссылки, формат

2) Relevant CTL/VAL/QA (по типу документа)
- если документ влияет на пайплайн/контракт, должны быть проверки
- для протоколов: минимум READINESS/QA gate логика применима как концепт

3) MACHINE_ARCHITECT_SPC
- финальное согласование на уровне системы

Если signoff отсутствует → изменение не считается принятым.

---

## 8) UPDATE OBLIGATIONS (INDEX / REGISTRY / LOG)
После изменения controlled documents система обязана проверить, требуется ли обновление:

### 8.1 Index update
Если документ находится в индексируемом слое (ROOT/Master/sub-index):
- проверить, что RAW ссылка присутствует в нужном индексе
- если документ новый — добавить
- если документ переименован/перемещён — обновить ссылку и добавить deprecation pointer

### 8.2 Registry update
Если документ относится к registries (templates/entities/doc registry):
- обновить соответствующий registry, если он ведётся для данного слоя

### 8.3 Log update
Если включены логи изменений:
- добавить запись в LOG__CHANGES или эквивалент (если используется)

---

## 9) DEPRECATION / RENAME / MOVE RULES
### 9.1 Deprecation pointer required
При замене документа:
- старый документ не удаляется “молча”
- добавляется указатель на replacement (RAW)
- фиксируется CHANGE_NOTE с причиной

### 9.2 Rename/Migrate
Если переименование/перенос:
- обновить все известные индексы/реестры, которые на него ссылаются
- сохранить совместимость через deprecation pointer там, где это требуется

---

## 10) CHANGE EXECUTION DISCIPLINE
### 10.1 Atomicity
Один CHANGE_ID должен соответствовать одному атомарному набору правок:
- либо один документ
- либо небольшой набор документов, которые должны поменяться вместе (например CTL+VAL синхронизация)

### 10.2 No mixed intents
Запрещено мешать в одном CHANGE_ID:
- правки формата
- и изменения логики
- и добавление новых сущностей
Если нужно — разбивать на несколько CHANGE_ID.

### 10.3 Backout readiness
Изменение должно быть так оформлено, чтобы его можно было откатить:
- ясный список файлов
- ясный список “что стало иначе”

---

## 11) MINIMUM CHANGE PACK (RECOMMENDED OUTPUT)
Для каждого изменения (в чате или в PR) желательно фиксировать:

- CHANGE_ID
- FILES TOUCHED (RAW list)
- TYPE (PATCH/MINOR/MAJOR)
- VERSION bumps summary
- RISK NOTES (если есть)
- REQUIRED FOLLOW-UPS (indexes/registries/logs)

---

## 12) STOP CONDITIONS (WHEN CHANGE WORK MUST STOP)
Остановка разрешена только если:
- RAW missing (нет доступа к файлу/ссылке)
- marker not confirmed (нельзя подтвердить правила/маркер)
- input absent (нет списка правок/нет файла-цели)

---

END.
