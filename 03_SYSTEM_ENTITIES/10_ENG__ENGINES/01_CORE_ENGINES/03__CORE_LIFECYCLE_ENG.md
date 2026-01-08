# CORE LIFECYCLE ENGINE (CANON)
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/01_CORE_ENGINES/03__CORE_LIFECYCLE_ENG.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 01_CORE_ENGINES
DOC_TYPE: ENGINE
LEVEL: L1
STATUS: ACTIVE
VERSION: 1.0.0
UID: UE.ENG.CORE.LIFECYCLE.001
OWNER: SYSTEM
ROLE: Defines canonical lifecycle for all system entities, documents, indexes, and artifacts (birth → draft → active → deprecated → archived), with strict gates, transitions, and audit enforcement

---

## 0) ENGINE HEADER (REQUIRED)

ENGINE_NAME: 03__CORE_LIFECYCLE_ENG
ENGINE_CLASS: CORE
ENGINE_FAMILY: 01_CORE_ENGINES
ENGINE_NUMBER: 03
ENGINE_UID: UE.ENG.CORE.LIFECYCLE.001
ENGINE_STATUS: ACTIVE

---

## 1) PURPOSE (WHAT THIS ENGINE SOLVES)

Этот движок определяет **единый канонический жизненный цикл** для всего, что существует в Universe Engine:
- документы
- индексы
- сущности (ENG/ORC/SPC/CTL/VAL/QA/KB/PRJ/AST/DB/LOG)
- артефакты проекта

Он решает главную боль: **как правильно переводить “нечто” из состояния в состояние**, чтобы:
- не ломать канон
- не плодить “полуживые” файлы
- не терять историю
- не создавать скрытых конфликтов и несостыковок

Ключ: **жизненный цикл — это закон, а не пожелание**.

---

## 2) SCOPE & BOUNDARIES (ANTI-CONFLICT)

### IN SCOPE
- Универсальная модель жизненного цикла (states + transitions)
- Стандарты переходов: кто может инициировать, какие условия, какие записи обязательны
- Gates (OK/WARN/BLOCK) для промоушена в канон
- Правила деприкации, архивирования, замены, миграции и алиасов
- Привязка к Audit/Change Control/Canon Authority

### OUT OF SCOPE
- Определение “что такое система” (это `01__CORE_IDENTITY_ENG`)
- Определение “состояния системы прямо сейчас” (это `02__CORE_STATE_ENG`)
- Доменная логика (Narrative/Character/World и т.д.)
- Фактчекинг/качество текста/культура/научность (это VAL/QA)
- Частные инструкции по каждому семейству (они в README семействах и governance)

---

## 3) MINI-CONTRACT (MANDATORY)

CONSUMES:
- SYS_IDENTITY (core identity anchors lifecycle law)
- SYS_STATE_SNAPSHOT (для безопасных переходов: нельзя промоутить при BLOCK)
- CHANGE_REQUEST (если переход затрагивает канон/структуру/порядок)
- ENTITY_OR_DOC_TARGET (описание, что именно переводим)

PRODUCES:
- LIFECYCLE_MODEL (универсальная модель состояний/переходов)
- TRANSITION_CHECKLISTS (чеклисты по ключевым переходам)
- TRANSITION_RECORD (аудит-запись о переходе)
- DEPRECATION_MAP (замены/алиасы/куда переехало)

DEPENDS_ON:
- 01_CORE_ENGINES/01__CORE_IDENTITY_ENG (HARD)
- 01_CORE_ENGINES/02__CORE_STATE_ENG (HARD)
- 00_GOVERNANCE_ENGINES/01__AUDIT_LOG_ENG (HARD)
- 00_GOVERNANCE_ENGINES/04__CHANGE_CONTROL_ENG (HARD for canon-impact transitions)
- 00_GOVERNANCE_ENGINES/02__CANON_AUTHORITY_ENG (SOFT, when disputes)
- 00_GOVERNANCE_ENGINES/07__DECISION_APPROVAL_ENG (SOFT, approvals)
- 00_GOVERNANCE_ENGINES/05__CONSISTENCY_ENG (HARD for structure-affecting moves)

OUTPUT_TARGET:
- 01_SYSTEM_LAW/ (если lifecycle закреплён как закон верхнего уровня)
- 99_LOGS/LOG__AUDIT.md (обязательная запись о переходах)
- 03_SYSTEM_ENTITIES/* (используется каждым семейством как обязательная опора)
- 08_DATABASES/DB__RELEASE_LOG.md (pointer на актуальные состояния/релизы)

---

## 4) LIFECYCLE MODEL (CANONICAL STATES)

### 4.1 Canon state set (strict)
Базовый жизненный цикл должен быть совместим со стандартом статусов:

- `DRAFT` — в разработке, не канон, может быть неполным
- `ACTIVE` — канон, рабочее, допускается развитие только через правила
- `DEPRECATED` — устарело, заменено, сохраняется ради совместимости/истории
- `ARCHIVED` — выведено из оборота, трогать нельзя, только хранить

> Важное: `STATUS` — не “настроение”, а юридическое состояние объекта.

### 4.2 Supplement flags (non-status)
Для уточнения, без расширения списка STATUS, используются “теги жизненного цикла” внутри тела документа:

- `LIFECYCLE_TAGS: [WIP|CANON_READY|MIGRATING|LOCKED_HISTORY]`
- `REPLACED_BY: <canonical path or UID>`
- `MIGRATION_FROM: <old path>`
- `SUNSET_DATE: YYYY-MM-DD` (если применимо)
- `COMPAT_LEVEL: <OK|WARN|BREAK>` (для совместимости)

---

## 5) TRANSITIONS (CANONICAL MOVES)

### 5.1 Allowed transitions (strict)
- T1: `DRAFT -> ACTIVE`
- T2: `ACTIVE -> DEPRECATED`
- T3: `DEPRECATED -> ARCHIVED`
- T4: `DRAFT -> ARCHIVED` (только если признано мусором/ошибкой и зафиксировано в логе)

### 5.2 Forbidden transitions
- `ARCHIVED -> anything` (архив не воскресает)
- `DEPRECATED -> ACTIVE` (нельзя “вернуть” без новой сущности/версии; делай новый объект)
- “тишина” (переход без записи в Audit Log)

---

## 6) GATES (QUALITY / READINESS)

### 6.1 Global gate severity
- `OK` — можно переходить
- `WARN` — можно переходить только если риск понятен и записан
- `BLOCK` — нельзя переходить, сначала лечить

### 6.2 Gate dependency
Если `SYS_STATE_SNAPSHOT` имеет `SEVERITY: BLOCK` — любые канон-изменения **запрещены**.

---

## 7) CHECKLISTS (MANDATORY FOR KEY TRANSITIONS)

### 7.1 T1 — DRAFT -> ACTIVE (Canon Promotion Checklist)
MUST:
1) Объект зарегистрирован в каноническом INDEX (existence via index)
2) Название/нумерация/путь соблюдены (naming/numbering rules)
3) Есть UID, VERSION, STATUS, LOCK (и они валидны)
4) Нет дублирующих “точек истины” (не объявляет себя master index если не должен)
5) Есть Mini-Contract (CONSUMES/PRODUCES/DEPENDS_ON/OUTPUT_TARGET)
6) Все ссылки на канон-ресурсы резолвятся (нет битых raw-links / путей)
7) Для файла определены границы (scope & out-of-scope)
8) Добавлена запись в Audit Log (promotion record)
9) Если затрагивает структуру/порядок/канон-правила → Change Control record

SHOULD:
- Есть минимум 1 пример применения
- Есть failure modes / риски
- Есть mapping на слои/реестры (если нужно)

### 7.2 T2 — ACTIVE -> DEPRECATED (Sunset Checklist)
MUST:
1) Указан `REPLACED_BY` (что заменяет) или причина “no replacement”
2) В индексах отмечено состояние (если индекс хранит статусы/заметки)
3) Сохранена совместимость: где применялось — там есть указание миграции
4) Запись в Audit Log
5) Если спор/конфликт → Canon Authority decision

SHOULD:
- Указана дата sunset (SUNSET_DATE)
- Добавлен DEPRECATION_MAP record

### 7.3 T3 — DEPRECATED -> ARCHIVED (Archive Checklist)
MUST:
1) Доказано, что объект больше не нужен для совместимости
2) Везде где ссылались — ссылки обновлены/удалены
3) Объект помечен как `ARCHIVED` и `LOCK: FIXED`
4) Запись в Audit Log
5) Consistency check подтверждает: битых ссылок не осталось

---

## 8) LIFECYCLE RECORDS (STANDARD FORMAT)

### 8.1 Transition Record (audit payload)
Каждый переход создаёт запись (минимум) формата:

TRANSITION_RECORD:
- TIMESTAMP: <ISO>
- TARGET: <path or UID>
- FROM_STATUS: <DRAFT|ACTIVE|DEPRECATED|ARCHIVED>
- TO_STATUS: <...>
- TRIGGER: <who/what инициировал>
- REASON: <short>
- IMPACT: <short>
- REFERENCES:
  - INDEX_CHANGE: <link/path or NONE>
  - CHANGE_CONTROL: <link/path or NONE>
  - CANON_AUTHORITY: <link/path or NONE>
- RESULT: <OK|WARN|BLOCK>

---

## 9) MIGRATION & ALIAS LAW (RENAMES / MOVES)

### 9.1 Rename/move is a lifecycle event
Переименование/перенос = всегда событие жизненного цикла, даже если STATUS не меняется.

MUST:
- `MIGRATION_FROM` + новый канонический путь
- Обновление индексов (старые ссылки не должны жить)
- Audit Log запись “MIGRATION”
- Consistency check (битые ссылки запрещены)

### 9.2 Deprecation Map
Если что-то переехало или заменилось, фиксируется:

DEPRECATION_MAP record:
- OLD: <old path or UID>
- NEW: <new path or UID>
- TYPE: <RENAME|MOVE|REPLACE|MERGE|SPLIT>
- WHY: <short>
- COMPAT: <OK|WARN|BREAK>

---

## 10) ENTITY CLASSES (WHAT THIS APPLIES TO)

Этот lifecycle применяется одинаково к:
- INDEX docs (master indexes, family indexes)
- ENGINE docs (ENG)
- Orchestrators / Specialists / Controllers / Validators / QA entities
- KB entities / KB governance docs
- Project passports / outputs
- Asset passports / asset governance
- DB registries
- Logs (с оговоркой: логи обычно ACTIVE+FIXED как историческая фиксация)

---

## 11) GOVERNANCE INTEGRATION (MANDATORY)

### 11.1 When Change Control is required (HARD)
Change Control обязателен, если переход:
- меняет структуру репозитория (пути/папки/семейства)
- меняет порядок/состав канонических индексов
- меняет “точки истины”
- вводит/удаляет обязательные зависимости
- переводит критический документ в DEPRECATED/ARCHIVED

### 11.2 Canon Authority triggers
Canon Authority подключается, если:
- есть спор о каноне
- есть конфликт индексов
- есть риск “двойной истины”
- нужно разрешить исключение из правил

---

## 12) FAILURE MODES (KNOWN RISKS)

- FM1: “Промоутнули в ACTIVE без регистрации в индексе”
  - EFFECT: сущность “живая”, но не существует по канону
  - FIX: откат/деприк + регистрация + audit

- FM2: “Удалили/переименовали без миграции”
  - EFFECT: битые ссылки, развал навигации
  - FIX: migration record + обновление индексов + consistency run

- FM3: “DEPRECATED без REPLACED_BY”
  - EFFECT: система не знает, куда идти дальше
  - FIX: добавить replacement или объяснение отсутствия, плюс карта миграции

- FM4: “Archive prematurely”
  - EFFECT: ломается совместимость (старые пайпы/проекты)
  - FIX: восстановить как DEPRECATED (если возможно) или создать новый compatibility shim

---

## 13) EXAMPLES (MINIMUM 2)

### Example A — Promotion to ACTIVE
TARGET: новый индекс семейства
- DRAFT -> ACTIVE
- Выполнены пункты T1 checklist
- В audit: запись promotion + ссылка на изменение в индексе

### Example B — Deprecation due to rename
TARGET: файл переехал в другую папку
- ACTIVE -> DEPRECATED (старый путь)
- Новый путь становится ACTIVE
- DEPRECATION_MAP: TYPE= MOVE, COMPAT=WARN (если есть внешние ссылки)
- Consistency check подтверждает отсутствие битых ссылок

---

## FINAL RULE (LOCK)

LOCK: FIXED
