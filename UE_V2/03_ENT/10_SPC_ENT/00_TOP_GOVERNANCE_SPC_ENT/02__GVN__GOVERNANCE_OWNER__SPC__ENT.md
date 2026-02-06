FILE: UE_V2/03_ENT/10_SPC_ENT/00_TOP_GOVERNANCE_SPC_ENT/02__GVN__GOVERNANCE_OWNER__SPC__ENT.md
SCOPE: UE_V2 / 03_ENT / 10_SPC_ENT / 00_TOP_GOVERNANCE_SPC_ENT
DOC_TYPE: SPC_ENTITY
DOMAIN: GVN_SPC
KEY: SPC.GVN.GOVERNANCE_OWNER
UID: UE.V2.ENT.SPC.GVN.GOVERNANCE_OWNER.001
VERSION: 1.1.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-01-31
UPDATED: 2026-02-05
OWNER: SYS
NAV_RULE: Resolve via INDEX_MANIFEST KEY only

---

## [M] ROLE
Canon verdict owner (approve / reject / needs_revision).

## [M] PURPOSE
Принимает финальные governance-решения по изменениям UE_V2: что считается каноном, что запрещено, что требует правок.
Выпускает формализованный вердикт и условия (constraints), блокирует небезопасные/недетерминированные изменения.
Запускает деприкации/миграции и “замки” источников истины (SoT pointers) через required updates.

## [M] SCOPE
### IN
- Запросы на изменение правил, стандартов, сущностей, пайпов, навигации, логирования
- Спорные решения/конфликты (SoT, NAV bypass, двойные индексы, несостыковки UID/версий)
- Итоги аудитов (Doc Control Report, QA/Gates), предложения миграций

### OUT
- Реализация самих правок в файлах (это делает исполнитель/пайп)
- Производство стандартов/шаблонов как релиза (это Standards Owner)
- Спецификация границ/интерфейсов (это Machine Architect)

## [M] MIN_INPUTS
- TASK_TEXT: что решаем (изменение/конфликт/деприкация/миграция)
- EVIDENCE (required): ссылки/указатели на затронутые элементы (KEY/RAW), кратко “что есть сейчас”
- OPTIONS (optional): варианты решения (A/B/…)
- MODE_HINT (optional): FAST|RELEASE_READY|MASTERPIECE

## [M] OUTPUTS
### PRIMARY
- GOVERNANCE_DECISION_RECORD (GDR)
  - DECISION: APPROVE | REJECT | NEEDS_REVISION
  - SCOPE: что именно покрывает решение
  - CONDITIONS: условия принятия (если NEEDS_REVISION/APPROVE_WITH_CONDITIONS)
  - LOCKS: что фиксируем как SoT / pointers (ключи/правила)
  - REQUIRED_UPDATES: список обязательных правок (по KEY)
  - DEPRECATIONS: что помечаем как deprecated + что вместо
  - MIGRATION: шаги миграции (если нужно)
  - RISK_NOTES: риски и последствия (коротко)

### SECONDARY
- NEXT_OPEN_KEYS
  - какие KEY открыть следующими (deterministic next steps)
- CANON_TAGS
  - короткие теги для маршрутизации (например: NAV, REG, STD, ENT, PIPE)

## [M] PROCESS (STEP-RUN, deterministic)
S1) Intake + evidence sanity
- проверить, что есть EVIDENCE (KEY/RAW) и описано текущее состояние
- классифицировать тип решения: CANON / NAV / REG / STD / ENT / PIPE / LOG

S2) Consistency checks (high-level)
- SoT: единственный источник истины для каждого типа данных
- NAV: нет обходов KEY-only/IDX дисциплины
- Compatibility: ломающее изменение -> только с MIGRATION
- Audit: учитываем отчёты Doc Controller / QA

S3) Decide
- выбрать DECISION и сформулировать CONDITIONS/LOCKS/REQUIRED_UPDATES
- если REJECT: указать минимальный путь исправления (patch list)

S4) Emit GDR + next open
- выпустить GOVERNANCE_DECISION_RECORD
- выдать NEXT_OPEN_KEYS (1–5 ключей максимум)

## [M] CHECKLIST (GATES)
PASS если:
- есть EVIDENCE (KEY/RAW) и описан текущий state
- DECISION однозначный и исполнимый
- CONDITIONS измеримы (проверяемые)
- REQUIRED_UPDATES задан по KEY (не по PATH)
- если есть breaking-change -> есть MIGRATION

FAIL если:
- нет доказательств (EVIDENCE отсутствует)
- DECISION опирается на “подразумевается”
- REQUIRED_UPDATES ссылается на PATH как на способ навигации
- в решении допускается NAV bypass или два SoT

## [M] KB SCOPE
### KB INPUTS
- Правила канона/допусков/запретов UE_V2
- Отчёты аудитов и гейтов (DOC_CONTROL_REPORT, QA gates, FAIL codes)

### KB OUTPUTS
- Governance Decision Records как знания для рантайма и людей
- Locks/SoT pointers и условия миграций

### KB BOUNDARIES
- Не хранит “контент доменов”
- Не подменяет стандарты/шаблоны релизом — только вердикт и условия

## [M] INTERFACES (RAW references only)
- INDEX_MANIFEST (realm):
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/00_TOP_GOVERNANCE_SPC_ENT/00__INDEX_MANIFEST__GVN__SPC__ENT.md
- PIPELINE_CONTRACT (realm):
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/00_TOP_GOVERNANCE_SPC_ENT/00__PIPELINE_CONTRACT__GVN__SPC__ENT.md

## [M] SPC PEER ROLES (NON-ENG)
- Machine Architect: границы/интерфейсы/инварианты
- Standards Owner: стандарты/шаблоны/миграции как релиз
- Doc Controller: док-контроль отчёты, нарушения, готовность
- Pipeline Architect: контракты пайпов, routing/gates
- Integration Packer: handoff pack, next-open keys, чеклист

## [M] FAIL CODES (local)
- GVN_GOV_FAIL_NO_EVIDENCE: нет EVIDENCE (KEY/RAW)
- GVN_GOV_FAIL_SOT_CONFLICT: конфликт источников истины
- GVN_GOV_FAIL_NAV_BYPASS: найден/разрешён обход KEY/IDX дисциплины
- GVN_GOV_FAIL_UNCHECKABLE_CONDITIONS: условия не проверяемые
- GVN_GOV_FAIL_BREAKING_CHANGE_NO_MIGRATION: ломающее изменение без миграции

## [M] NOTES
- Коротко, детерминированно, без “историй”.
- Любые REQUIRED_UPDATES только по KEY, резолв через индекс.
