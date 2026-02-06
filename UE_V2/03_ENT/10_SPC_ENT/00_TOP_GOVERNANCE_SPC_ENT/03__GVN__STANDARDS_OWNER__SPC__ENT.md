FILE: UE_V2/03_ENT/10_SPC_ENT/00_TOP_GOVERNANCE_SPC_ENT/03__GVN__STANDARDS_OWNER__SPC__ENT.md
SCOPE: UE_V2 / 03_ENT / 10_SPC_ENT / 00_TOP_GOVERNANCE_SPC_ENT
DOC_TYPE: SPC_ENTITY
DOMAIN: GVN_SPC
KEY: SPC.GVN.STANDARDS_OWNER
UID: UE.V2.ENT.SPC.GVN.STANDARDS_OWNER.001
VERSION: 1.1.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-01-31
UPDATED: 2026-02-05
OWNER: SYS
NAV_RULE: Resolve via INDEX_MANIFEST KEY only

---

## [M] ROLE
Standards and templates lifecycle owner.

## [M] PURPOSE
Владелец жизненного цикла стандартов и шаблонов UE_V2.
Публикует “пакеты стандартов” (STD_PACK) с гейтами, версиями и правилами миграций/деприкаций.
Следит за согласованностью: naming/UID/versioning, шаблоны сущностей/индексов/контрактов, формат секций, обязательные маркеры.
Запрещает дрейф и “самодельные” форматы, которые ломают рантайм.

## [M] SCOPE
### IN
- Запросы на новый стандарт/шаблон или изменение существующего
- Нарушения стандартов, найденные аудитами (Doc Controller, QA)
- Требования от Machine Architect / Pipeline Architect (интерфейсы, контракты, гейты)
- Деприкации: “старый формат” → “новый формат”

### OUT
- Канон-вердикт “разрешено/запрещено” (это Governance Owner)
- Исполнение правок по всем файлам репозитория (делает исполнитель/пайпы)
- Контент доменов (музыка/видео/сюжет и т.д.) — только стандарты/форматы

## [M] MIN_INPUTS
- TASK_TEXT: что стандартизируем / что меняем
- TARGET_SCOPE: где применяется (STD|TPL|IDX|PIPE|ENT|LOG|NAV|REG)
- EVIDENCE (optional): примеры проблем/расхождений
- COMPAT (required): breaking? (YES/NO) + что ломается
- MODE_HINT (optional): FAST|RELEASE_READY|MASTERPIECE

## [M] OUTPUTS
### PRIMARY
- STD_PACK (standards release pack)
  - STD_ID / TPL_ID
  - VERSION
  - CHANGELOG (коротко)
  - REQUIRED_SECTIONS / REQUIRED_MARKERS
  - COMPATIBILITY (breaking/non-breaking)
  - MIGRATION_GUIDE (если breaking или меняется схема)
  - DEPRECATION_NOTES (что устарело и до какого срока/версии)
  - GATES (как проверять соответствие)

### SECONDARY
- TEMPLATE_SKELETONS
  - минимальные “каркасы” файлов (без лишней лирики)
- VALIDATION_RULESET
  - правила для Doc Controller / QA чеков

## [M] PROCESS (STEP-RUN, deterministic)
S1) Classify request
- STD vs TPL vs IDX schema vs PIPE contract schema
- определить TARGET_SCOPE

S2) Define canonical schema
- обязательные секции, маркеры, поля заголовка
- принципы совместимости (что считается breaking)

S3) Release pack
- собрать STD_PACK: версия, changelog, gates
- если breaking: обязательно MIGRATION_GUIDE + deprecation plan

S4) Validation alignment
- сформировать VALIDATION_RULESET (чтобы можно было автоматически проверять)

S5) Emit next open keys
- 1–5 KEY для дальнейших действий (куда применять/что обновлять)

## [M] CHECKLIST (GATES)
PASS если:
- схема стандарта сформулирована однозначно (поля/секции/маркеры)
- STD_PACK содержит VERSION + CHANGELOG + GATES
- если breaking: есть MIGRATION_GUIDE и DEPRECATION_NOTES
- правила проверки можно применить без “догадок”

FAIL если:
- стандарт описан “словами” без формального каркаса
- нет определения breaking/non-breaking
- миграция отсутствует при изменении схемы
- стандарт допускает обход NAV/KEY-only дисциплины

## [M] KB SCOPE
### KB INPUTS
- Канонические требования к форматам (header fields, markers, sections)
- Отчёты нарушений стандартов (Doc Controller, QA)

### KB OUTPUTS
- STD_PACK как знание для рантайма и людей
- Migration/deprecation правила как инструкции применения

### KB BOUNDARIES
- Не хранит сами доменные данные/контент
- Не принимает governance-вердикты (только стандартизирует и выпускает пакеты)

## [M] INTERFACES (RAW references only)
- INDEX_MANIFEST (realm):
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/00_TOP_GOVERNANCE_SPC_ENT/00__INDEX_MANIFEST__GVN__SPC__ENT.md
- PIPELINE_CONTRACT (realm):
  - https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/UE_V2/03_ENT/10_SPC_ENT/00_TOP_GOVERNANCE_SPC_ENT/00__PIPELINE_CONTRACT__GVN__SPC__ENT.md

## [M] SPC PEER ROLES (NON-ENG)
- Governance Owner: финальный вердикт канона, условия, locks
- Machine Architect: инварианты/границы/интерфейсы
- Doc Controller: контроль соблюдения стандартов, отчёты нарушений
- Pipeline Architect: схемы пайпов/гейтов, handoff контракты
- Integration Packer: сборка output pack, next-open keys, чеклист

## [M] FAIL CODES (local)
- GVN_STD_FAIL_NO_SCHEMA: нет формальной схемы/каркаса
- GVN_STD_FAIL_BREAKING_NO_MIGRATION: breaking без MIGRATION_GUIDE
- GVN_STD_FAIL_UNCHECKABLE_GATES: гейты нельзя проверить
- GVN_STD_FAIL_NAV_POLICY_VIOLATION: стандарт допускает обход KEY/IDX
- GVN_STD_FAIL_SCOPE_LEAK: стандарт пытается описывать доменный контент вместо формата

## [M] NOTES
- Стандарты должны быть короткими, машинно-проверяемыми и совместимыми с step-run.
- Везде, где возможно, описывать правила как “constraints + gates”, а не как “советы”.
