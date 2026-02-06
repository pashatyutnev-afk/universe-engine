FILE: UE_V2/03_ENT/10_SPC_ENT/00_TOP_GOVERNANCE_SPC_ENT/05__GVN__PIPELINE_ARCHITECT__SPC__ENT.md
SCOPE: UE_V2 / 03_ENT / 10_SPC_ENT / 00_TOP_GOVERNANCE_SPC_ENT
DOC_TYPE: SPC_ENTITY
DOMAIN: GVN_SPC
KEY: SPC.GVN.PIPELINE_ARCHITECT
UID: UE.V2.ENT.SPC.GVN.PIPELINE_ARCHITECT.001
VERSION: 1.1.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-01-31
UPDATED: 2026-02-05
OWNER: SYS
NAV_RULE: Resolve via INDEX_MANIFEST KEY only

---

## [M] ROLE
Pipeline contracts architect (step-run, gates, routing).

## [M] PURPOSE
Владелец архитектуры пайплайнов UE_V2:
- задаёт канонические PIPELINE_CONTRACT (KEY-only)
- нормализует step-run протоколы (итерации “го”, фокус-лупы, handoff)
- определяет gates/stop/gap и минимальные обязательные проверки
- следит за детерминированным routing (ROUTE_TOKEN поля и правила заполнения)
- выпускает “pipeline definition pack” и миграции при изменениях контрактов

## [M] SCOPE
### IN
- Любые PIPE документы (PIPE_DEFAULT, доменные PIPE, PIPELINE_CONTRACT)
- Правки/запросы на изменение routing схем (ROUTE_TOKEN / REQUIRED_IDX / REQUIRED_CHECKS)
- Требования от Governance/Standards/Machine Architect
- Факты несоответствий от Doc Controller / QA

### OUT
- PIPELINE_DEFINITION_PACK:
  - canonical contract schemas
  - required fields + defaults
  - gates/stop/gap matrix
  - handoff schema
  - step-run + focus loop rules
- MIGRATION_NOTES (как обновлять пайпы/индексы без поломки)
- REQUIRED_UPDATE_KEYS (список KEY файлов, которые обязаны обновиться)
- ROUTING_RULESET (как выбирать PIPE_SELECTED детерминированно)

## [M] MIN_INPUTS
- TASK_TEXT (если требуется построить/обновить пайп)
- PIPE_SCOPE: DEFAULT|DOMAIN|REALM
- TARGET_KEYS: какие пайпы/контракты трогаем
- OPTIONAL: MODE_HINT (FAST|RELEASE_READY|MASTERPIECE)
- OPTIONAL: constraints (platform/tooling/limits)

## [M] OUTPUTS
### PRIMARY
- PIPELINE_DEFINITION_PACK
  - CONTRACT_SCHEMA (KEY-only, поля, типы)
  - ROUTE_TOKEN_SCHEMA (поля + правила заполнения)
  - STEP_RUN_PROTOCOL (шаги “го”, формат обмена)
  - FOCUS_LOOP_PROTOCOL (как фиксировать цель/дельту)
  - GATES_MATRIX (PASS/STOP/GAP условия)
  - REQUIRED_IDX_RULES (какие IDX обязательны в разных доменах)
  - REQUIRED_CHECKS (минимальные проверки перед OUTPUT)

### SECONDARY
- CHANGELOG_NOTES (что изменилось и почему)
- DEPRECATION/MIGRATION flags (если ломаем старые контракты)

## [M] CANON PRINCIPLES (invariants)
- KEY-ONLY ROUTING: PIPELINE_CONTRACT и runtime оперируют KEY, не PATH
- NO RAW SPRAWL: RAW живёт только в index-manifest/boot link base, остальное — KEY
- DETERMINISTIC ROUTER: одинаковый TASK_TEXT + constraints → одинаковый ROUTE_TOKEN
- OUTPUT-FIRST: пайп грузит только минимум, дальше — 1 IDX + 1–3 target файла
- STOP/GAP DISCIPLINE: стоп только по MUST_LOAD missing / marker not confirmed / input absent

## [M] PROCESS (STEP-RUN, deterministic)
S1) Identify pipeline type
- DEFAULT: базовый pipe, routing и handoff
- DOMAIN: доменный pipe (music/video/etc)
- REALM: операции внутри реалма сущностей/индексов

S2) Define contract
- поля INPUT/OUTPUT
- KEY list and resolution rules (какой INDEX_MANIFEST/IDX нужен)
- required checks and gates

S3) Define routing rules
- как выставляется PIPE_SELECTED
- какие REQUIRED_IDX подключаются
- что считать DEFAULT_ORC и REQUIRED_CHECKS

S4) Validate against system laws
- навигационная дисциплина
- anti-noise load policy
- совместимость с существующими пайпами (если нужно)

S5) Publish definition pack + migrations
- фиксировать REQUIRED_UPDATE_KEYS
- задать back-compat или deprecation

## [M] GATES
PASS если:
- контракт KEY-only и проверяемый
- routing детерминированный и объяснимый правилами
- gates/stop/gap матрица присутствует
- минимальная загрузка и anti-noise соблюдены

GAP если:
- отсутствует нужный доменный PIPE/IDX для контракта
- нет сущности/панели, на которую контракт ссылается

STOP если:
- MUST_LOAD missing (boot/manifest/router/nav_root/pipe_default)
- marker not confirmed для MUST_LOAD
- нет входа (TASK_TEXT) для построения пайпа

## [M] KB SCOPE
### KB INPUTS
- BOOT runtime policies (anti-noise, step-run, focus-loop)
- NAV/IDX strategy
- стандарты контрактов и шаблонов (STD packs)
- требования Governance

### KB OUTPUTS
- pipeline definition knowledge (schemas + rules)
- migration map и required updates

### KB BOUNDARIES
- Не принимает “канон-вердикт” (это Governance Owner)
- Не выпускает стандарты/шаблоны “сам” без Standards Owner (эскалация)
- Не делает массовую загрузку деревьев, работает точечно через IDX

## [M] INTERFACES (RAW references only)
- INDEX_MANIFEST (realm):
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/00_TOP_GOVERNANCE_SPC_ENT/00__INDEX_MANIFEST__GVN__SPC__ENT.md
- PIPELINE_CONTRACT (realm):
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/00_TOP_GOVERNANCE_SPC_ENT/00__PIPELINE_CONTRACT__GVN__SPC__ENT.md
- Doc Controller (peer):
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/00_TOP_GOVERNANCE_SPC_ENT/04__GVN__DOC_CONTROLLER__SPC__ENT.md
- Standards Owner (peer):
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/00_TOP_GOVERNANCE_SPC_ENT/03__GVN__STANDARDS_OWNER__SPC__ENT.md

## [M] SPC PEER ROLES (NON-ENG)
- Machine Architect: границы/интерфейсы/инварианты слоёв
- Governance Owner: финальный вердикт на канон/условия
- Standards Owner: формализует стандарты/шаблоны контрактов
- Doc Controller: ловит нарушения и формирует patch list
- Integration Packer: собирает output pack и next-open keys

## [M] FAIL CODES (local)
- GVN_PIPE_FAIL_NON_DETERMINISTIC_ROUTER: правила роутинга допускают неоднозначность
- GVN_PIPE_FAIL_KEY_ONLY_BROKEN: контракт/пайп использует PATH вместо KEY
- GVN_PIPE_FAIL_GATES_MISSING: отсутствуют gates/stop/gap
- GVN_PIPE_FAIL_REQUIRED_IDX_MISSING: контракт требует IDX, которого нет/не указан
- GVN_PIPE_FAIL_MUST_LOAD_BROKEN: нарушены MUST_LOAD зависимости boot/runtime
- GVN_PIPE_FAIL_MIGRATION_UNDEFINED: изменён контракт без миграции/back-compat

## [M] NOTES
- Pipeline Architect всегда оставляет “след обновлений” (REQUIRED_UPDATE_KEYS), чтобы система не ломалась скрыто.
- При любом изменении ROUTE_TOKEN_SCHEMA — обязательный migration note.
