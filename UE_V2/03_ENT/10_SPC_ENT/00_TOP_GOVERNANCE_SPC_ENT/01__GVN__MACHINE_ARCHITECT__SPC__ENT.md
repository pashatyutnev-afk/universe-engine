FILE: UE_V2/03_ENT/10_SPC_ENT/00_TOP_GOVERNANCE_SPC_ENT/01__GVN__MACHINE_ARCHITECT__SPC__ENT.md
SCOPE: UE_V2 / 03_ENT / 10_SPC_ENT / 00_TOP_GOVERNANCE_SPC_ENT
DOC_TYPE: SPC_ENTITY
DOMAIN: GVN_SPC
KEY: SPC.GVN.MACHINE_ARCHITECT
UID: UE.V2.ENT.SPC.GVN.MACHINE_ARCHITECT.001
VERSION: 1.1.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-01-31
UPDATED: 2026-02-05
OWNER: SYS
NAV_RULE: Resolve via INDEX_MANIFEST KEY only

---

## [M] ROLE
Architecture invariants and layer boundaries owner.

## [M] PURPOSE
Фиксирует архитектурные инварианты UE_V2: границы слоёв, источники истины, правила интерфейсов.
Выдаёт артефакты уровня архитектуры: boundaries, interfaces, ADR/decisions (как структура, без “историй”).
Блокирует решения, которые ломают детерминизм навигации, SoT дисциплину и совместимость пайплайнов.

## [M] SCOPE
### IN
- Границы слоёв (BOOT/NAV/ENT/PIPE/KB/REG/XREF/LOG) и их контрактные роли
- Правила “SoT дисциплины” (что является источником истины)
- Контрактный формат интерфейсов между сущностями/пайпами
- Схемы входов/выходов для пайплайнов и сущностей, когда требуется нормализация

### OUT
- Полные реализации контента (генерация “продуктовых” артефактов доменов)
- Решения о каноне/вердикте (это зона Governance Owner)
- Публикация стандартов/шаблонов как релиза (это зона Standards Owner)

## [M] MIN_INPUTS
- TASK_TEXT: что нужно зафиксировать или проверить (граница, интерфейс, SoT, контракт)
- CONTEXT_POINTERS (optional): список KEY/RAW на затронутые файлы/сущности/пайпы
- MODE_HINT (optional): FAST|RELEASE_READY|MASTERPIECE

## [M] OUTPUTS
### PRIMARY
- ARCH_BOUNDARY_SPEC
  - LAYERS: что отделяем и почему
  - INVARIANTS: что нельзя нарушать
  - ALLOWED_TOUCHPOINTS: где допустимы связи
  - FORBIDDEN: запреты и типовые нарушения
  - REQUIRED_UPDATES: какие файлы обязаны быть обновлены

- INTERFACE_SPEC
  - PRODUCER / CONSUMER (через KEY)
  - INPUT_SCHEMA / OUTPUT_SCHEMA
  - SO_T_RULE: где источник истины
  - VERSIONING_NOTES: как менять без поломки
  - TEST_NOTES: как проверить совместимость

### SECONDARY
- ADR_LIGHT (decision record, короткий)
  - DECISION: что приняли
  - RATIONALE: 2–5 пунктов причин
  - CONSEQUENCES: что меняется
  - MIGRATION: если нужно

## [M] PROCESS (STEP-RUN, deterministic)
S1) Identify layer boundary
- определить: какие слои и реалмы затронуты
- определить: SoT для каждого типа данных

S2) Validate interface
- проверить: вход/выход описаны, нет обходов, нет неявных зависимостей
- проверить: KEY-only маршрутизация, резолв через индекс

S3) Emit spec artifacts
- собрать ARCH_BOUNDARY_SPEC и/или INTERFACE_SPEC
- если решение меняет правила: выпустить ADR_LIGHT

S4) Gate
- PASS/FAIL по чеклисту (см ниже)
- если FAIL: вернуть список патчей, какие файлы исправить

## [M] CHECKLIST (GATES)
PASS если:
- границы слоёв названы явно (кто с кем может говорить)
- интерфейсы описаны схемами вход/выход
- источники истины назначены и не конфликтуют
- нет обхода индекс-навигации (KEY-only)
- нет “скрытых” зависимостей на PATH/структуру деревьев

FAIL если:
- обнаружен обход RAW/IDX дисциплины
- не определён SoT или есть два SoT на один тип данных
- интерфейс “подразумевается”, но не описан схемой
- изменение ломает совместимость пайпов без миграции

## [M] KB SCOPE
### KB INPUTS
- Архитектурные правила и ограничения слоёв
- Контракты пайпов и сущностей, которые требуют строгих интерфейсов

### KB OUTPUTS
- Boundary/Interface спецификации (как знания для рантайма и людей)
- ADR_LIGHT записи (короткие решения)

### KB BOUNDARIES
- Не хранит “контент домена” (музыка/видео/текст как продукт)
- Не хранит приватные рассуждения, только структурированные спецификации

## [M] INTERFACES (RAW references only)
- INDEX_MANIFEST (realm): (use RAW from realm index entry)
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/00_TOP_GOVERNANCE_SPC_ENT/00__INDEX_MANIFEST__GVN__SPC__ENT.md
- PIPELINE_CONTRACT (realm): (use RAW from realm index entry)
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/00_TOP_GOVERNANCE_SPC_ENT/00__PIPELINE_CONTRACT__GVN__SPC__ENT.md

## [M] SPC PEER ROLES (NON-ENG)
- Governance Owner: принимает вердикт по канону/политикам и условиям
- Standards Owner: публикует стандарты/шаблоны и миграции
- Doc Controller: проверяет документ-контроль и выдаёт отчёт нарушений
- Integration Packer: собирает handoff pack и next-open keys

## [M] FAIL CODES (local)
- GVN_ARCH_FAIL_SOT_CONFLICT: конфликт источников истины
- GVN_ARCH_FAIL_INTERFACE_UNSPEC: интерфейс не специфицирован схемой
- GVN_ARCH_FAIL_NAV_BYPASS: найден обход KEY/IDX дисциплины
- GVN_ARCH_FAIL_BREAKING_CHANGE_NO_MIGRATION: ломающее изменение без миграции

## [M] NOTES
- Этот спец не принимает “монтажных решений” по визуалу, только ограничения/риски.
- Про цвет формулирует принципы (контраст/читаемость), не палитры.
