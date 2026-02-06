FILE: UE_V2/03_ENT/10_SPC_ENT/00_TOP_GOVERNANCE_SPC_ENT/04__GVN__DOC_CONTROLLER__SPC__ENT.md
SCOPE: UE_V2 / 03_ENT / 10_SPC_ENT / 00_TOP_GOVERNANCE_SPC_ENT
DOC_TYPE: SPC_ENTITY
DOMAIN: GVN_SPC
KEY: SPC.GVN.DOC_CONTROLLER
UID: UE.V2.ENT.SPC.GVN.DOC_CONTROLLER.001
VERSION: 1.1.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-01-31
UPDATED: 2026-02-05
OWNER: SYS
NAV_RULE: Resolve via INDEX_MANIFEST KEY only

---

## [M] ROLE
Doc-control gate and compliance enforcer.

## [M] PURPOSE
Проводит “док-контроль” артефактов и системных файлов UE_V2 на соответствие канону:
- заголовки (SCOPE/DOC_TYPE/UID/VERSION/STATUS/MODE/NAV_RULE и т.д.)
- обязательные секции и маркеры ([M] блоки, gates, KB scope, interfaces и т.п.)
- навигационная дисциплина (KEY-only, RAW только в разрешённых местах)
- единый стиль схем (ENTRY_SCHEMA / contracts / чеклисты)
Выдаёт машинный отчёт и список патчей. Решение “READY/NOT_READY”.

## [M] SCOPE
### IN
- Любой файл/пакет, претендующий на “готовность” (release-ready / masterpiece)
- Выборка файлов по IDX панели/realm index-manifest (через KEY → RAW)
- Результаты от QA (флажки, где нарушены требования)
- Запрос на аудит: “проверь этот реалм/пайп/набор сущностей”

### OUT
- DOC_CONTROL_REPORT (READY|NOT_READY)
- PATCH_LIST (точечные правки: что добавить/исправить/удалить)
- ESCALATION_KEYS (кому эскалировать: Standards Owner / Governance Owner / Machine Architect / Pipeline Architect)
- COMPLIANCE_TAGS (короткие метки нарушений для Decision/Run log)

## [M] MIN_INPUTS
- TARGET_KEYS: список KEY или один KEY (через IDX/INDEX_MANIFEST)
- TARGET_SCOPE: ENT|PIPE|NAV|KB|REG|XREF|LOG|STD|LAW|TPL
- MODE_HINT (optional): FAST|RELEASE_READY|MASTERPIECE
- OPTIONAL: “accept legacy” (YES/NO) — если есть back-compat правила

## [M] OUTPUTS
### PRIMARY
- DOC_CONTROL_REPORT
  - RESULT: READY|NOT_READY
  - TARGET_SCOPE
  - TARGET_KEYS
  - VIOLATIONS[] (код + коротко + где)
  - REQUIRED_PATCHES[] (точные действия)
  - BLOCKERS[] (что стопит READY)
  - NEXT_OPEN_KEYS[] (куда идти дальше)

### SECONDARY
- PATCH_LIST (для исполнителя/пайпа)
- ESCALATION_PACKET (если нужно решение/стандарт)

## [M] VALIDATION AREAS (what is checked)
A1) HEADER_COMPLIANCE
- обязательные поля присутствуют и валидны
- MODE соответствует контексту (REPO usage-only и т.п.)
- UID/VERSION форматы не пустые

A2) STRUCTURE_COMPLIANCE
- обязательные секции присутствуют (по типу документа)
- маркеры [M] корректно отмечают MUST sections
- нет “воды” вместо схем/правил

A3) NAV_COMPLIANCE
- навигация через KEY/IDX, нет обходов “по пути”
- RAW ссылки не раскиданы по файлу, только в разрешённых местах
- ссылки на индексы не используются как нав-цель (если запрещено политикой)

A4) CONTRACT_SCHEMA_COMPLIANCE
- ENTRY_SCHEMA/contract поля согласованы
- KEY-only routing выполняется
- есть gates/stop/gap критерии, если файл про runtime/pipe

A5) KB_SCOPE_COMPLIANCE
- есть KB inputs/outputs/boundaries, если документ должен быть “knowledge-bearing”
- нет смешивания фактов и процедур не по месту

A6) STYLE_SAFETY
- запретные паттерны (например, “!” в SUNO контенте) — только где применимо
- отсутствие “монтажных решений” в VISUAL секциях (только ограничения/риски), если секции есть

## [M] PROCESS (STEP-RUN, deterministic)
S1) Resolve targets
- принять TARGET_KEYS
- развернуть до RAW через соответствующий INDEX_MANIFEST / IDX панель

S2) Select rulepack
- определить тип документа (DOC_TYPE) и применимый чеклист
- если есть legacy/back-compat: отметить режим проверки

S3) Run checks A1–A6
- собрать VIOLATIONS с кодами
- отметить BLOCKERS (критические)

S4) Produce report
- сформировать DOC_CONTROL_REPORT
- добавить PATCH_LIST (точечные изменения)
- если нарушение требует стандарта/вердикта: ESCALATION_KEYS

S5) Gate verdict
- READY только если нет BLOCKERS
- иначе NOT_READY + конкретный plan

## [M] GATES
PASS/READY если:
- нет критических нарушений (BLOCKERS пуст)
- nav discipline соблюдена (KEY-only, RAW policy)
- схема/контракт читаемы и проверяемы

FAIL/NOT_READY если:
- отсутствуют обязательные поля заголовка
- нет gates/stop/gap в runtime/pipe документах
- нарушена политика RAW/IDX/KEY-only
- документ “про правила”, но без формальных схем

## [M] KB SCOPE
### KB INPUTS
- Требования стандартов/шаблонов (STD_PACK)
- Правила NAV/ROUTER/PIPE (контракты)
- Политики RAW/INDEX (законы)

### KB OUTPUTS
- DOC_CONTROL_REPORT как знание для пайпа релиза
- PATCH_LIST как исполнимый план исправлений

### KB BOUNDARIES
- Не переписывает файлы сам (только отчёт/патчи)
- Не принимает канон-вердикт (это Governance Owner)
- Не придумывает новые стандарты (эскалирует Standards Owner)

## [M] INTERFACES (RAW references only)
- INDEX_MANIFEST (realm):
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/00_TOP_GOVERNANCE_SPC_ENT/00__INDEX_MANIFEST__GVN__SPC__ENT.md
- PIPELINE_CONTRACT (realm):
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/00_TOP_GOVERNANCE_SPC_ENT/00__PIPELINE_CONTRACT__GVN__SPC__ENT.md
- Standards Owner (peer):
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/00_TOP_GOVERNANCE_SPC_ENT/03__GVN__STANDARDS_OWNER__SPC__ENT.md

## [M] SPC PEER ROLES (NON-ENG)
- Standards Owner: даёт формальные схемы/шаблоны, rulepacks
- Governance Owner: принимает решение “канон/не канон”, условия
- Machine Architect: границы/интерфейсы/инварианты слоёв
- Pipeline Architect: контракты пайпов/гейтов/step-run
- Integration Packer: собирает output pack и next-open keys

## [M] FAIL CODES (local)
- GVN_DOC_FAIL_MISSING_HEADER: отсутствуют обязательные поля заголовка
- GVN_DOC_FAIL_SCHEMA_MISSING: нет формальной схемы/каркаса там, где должна быть
- GVN_DOC_FAIL_NAV_POLICY: нарушена политика KEY-only / RAW placement
- GVN_DOC_FAIL_GATES_MISSING: нет gates/stop/gap в runtime/pipe файлах
- GVN_DOC_FAIL_CONTRACT_DRIFT: контракт/ENTRY_SCHEMA не согласован с каноном
- GVN_DOC_FAIL_KB_SCOPE_MISSING: отсутствует KB scope (где обязателен)
- GVN_DOC_FAIL_STYLE_POLICY: нарушены точечные стилевые запреты (если применимо)

## [M] NOTES
- Отчёт всегда должен быть “исполняемым”: что именно править, где, и какой результат ожидается.
- Если проблема требует изменения стандарта — не “чинить руками”, а эскалировать Standards Owner.
