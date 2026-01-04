# Core Lifecycle Engine
FILE: 03__CORE_LIFECYCLE_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 01_CORE_ENGINES
LEVEL: L1
STATUS: ACTIVE
VERSION: 1.0
ROLE: Defines the lifecycle process: how entities are created, stabilized, evolved, migrated, and archived

---

## PURPOSE

Описывает **жизненный цикл сущности** как процесс:
- создание
- стабилизация
- публикация (активация)
- поддержка и эволюция
- замена и миграция
- деприкация и архив

Lifecycle — это “как мы живём”, State — это “в каком статусе мы сейчас”.

---

## LIFECYCLE PHASES (CANONICAL)

### Phase 0 — Intake / Drafting
- создание сущности
- первичное заполнение
- минимальная структура
**STATE:** DRAFT

### Phase 1 — Stabilization
- приведение к стандартам
- добавление owner/версии/путей
- внесение в индексы (если требуется)
**STATE:** DRAFT → готовность к ACTIVE

### Phase 2 — Activation (Publish)
- прохождение gates (Identity/Index/Ref/Contract)
- фиксация как точки истины
**STATE:** ACTIVE

### Phase 3 — Operation / Maintenance
- исправления, расширения, уточнения
- контроль версий
- аудит изменений
**STATE:** ACTIVE

### Phase 4 — Evolution / Replacement
- появляется новая версия или новая сущность-замена
- формируется миграционный план
**STATE:** ACTIVE → DEPRECATED (старое)

### Phase 5 — Deprecation & Migration
- система переезжает на replacement
- поддерживаются xref/совместимость
**STATE:** DEPRECATED

### Phase 6 — Archive
- объект исторический, но не используется
- хранится для памяти/разбора
**STATE:** ARCHIVED

### Exception Phase — Repair
- если обнаружена поломка/конфликт/битые ссылки
**STATE:** BROKEN → (DRAFT/ACTIVE после ремонта)

---

## REQUIRED ARTIFACTS PER PHASE

- Intake:
  - Identity header
  - минимальный смысл (purpose + роль)
- Stabilization:
  - стандарты формата
  - owner + version
  - индексация
- Activation:
  - gate checklist пройден
  - audit entry создан
- Maintenance:
  - изменения фиксируются
  - версия повышается
- Replacement:
  - replacement указан
  - xref mapping создан
  - migration plan описан
- Archive:
  - пометка архива
  - ссылки только исторические

---

## LIFE GATES (CANONICAL)

- Gate 1: Identity Valid (CORE_IDENTITY_ENG)
- Gate 2: State Valid (CORE_STATE_ENG)
- Gate 3: Consistency Pass (CONSISTENCY_ENG) — для индексируемых сущностей
- Gate 4: Change Control Check (CHANGE_CONTROL_ENG) — если high/critical
- Gate 5: Decision Approval (DECISION_APPROVAL_ENG) — если protected zone / breaking

---

## MECHANICS (HOW IT WORKS)

1) Любая сущность не может “внезапно” стать активной без gates.
2) Любая массовая правка проходит через:
   - impact оценку
   - dependency проверку
   - xref mapping (если переезды)
3) Любая замена требует:
   - фиксации replacement
   - поддержания совместимости до миграции
4) Архив — это финал жизни, но не смерть истории.

---

## FAILURE MODES

- F1: Нет стабилизации → DRAFT притворяется ACTIVE.
- F2: Нет миграции → старые ссылки умирают.
- F3: Нет audit/decision → невозможно понять почему так.
- F4: Ломают историю (удаление/переписывание) → канон теряет доверие.

---

## INTEGRATION

- With AUDIT_LOG_ENG: каждая фаза ключевых изменений должна фиксироваться.
- With CHANGE_CONTROL_ENG: lifecycle запускает governance gates.
- With DEPENDENCY_REGISTRY_ENG: lifecycle учитывает blast radius.
- With XREF__CROSSREF: lifecycle управляет переездами и совместимостью.
- With PROJECTS:
  - проекты используют lifecycle как pipeline производства контента:
    intake(workshop) → stabilize(project level) → publish(canon).

---
OWNER: Universe Engine
STATUS: FIXED
