FILE: UE_V2/03_ENT/01_TPL_ENT/10__TPL__ENGINE__ENT.md
SCOPE: UE_V2 / 03_ENT / 01_TPL_ENT
DOC_TYPE: TEMPLATE
TEMPLATE_FOR: ENTITY_PASSPORT (ENGINE)
DOMAIN: ENT
UID: UE.V2.ENT.TPL.ENGINE.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-01-31
UPDATED: 2026-01-31
OWNER: SYS
NAV_RULE: Template has no RAW

---

## [M] PURPOSE
Шаблон паспорта сущности типа ENGINE.
ENGINE — исполняемый модуль домена: принимает INPUT_TOKENS, применяет правила/пайп, выдаёт ARTIFACTS.

## [M] HARD_RULES
- Никаких RAW внутри паспорта. Адреса резолвятся через INDEX_MANIFEST.
- Все внешние ссылки только как KEYS (INDEX_MANIFEST KEYS).
- Минимальность: 1–2 строки на секцию, без лирики.
- Любой выход — артефакт (OUTPUT_PACK / PATCH_NOTES / TOKENS), не “голый текст”.
- Трассируемость: каждый прогон фиксирует RESOURCES_USED + MARKER_FOUND + GATES.

## [M] REQUIRED_FIELDS (header)
- FILE
- SCOPE
- DOC_TYPE
- ENTITY_TYPE
- UID
- VERSION
- STATUS
- MODE
- CREATED
- UPDATED
- OWNER

## [M] REQUIRED_SECTIONS
- PURPOSE
- ROLE
- CAPABILITIES
- INPUTS
- OUTPUTS
- DEPENDENCIES (KEYS ONLY)
- EXECUTION_MODEL
- ARTIFACTS
- INTERFACES (KEYS ONLY)
- KB_SCOPE
- GATES
- CHANGELOG

## [M] TOKEN_MODEL
INPUT_TOKENS:
- TASK_TEXT
- CONTEXT_MIN?
- MODE_HINT?

OUTPUT_TOKENS:
- ARTIFACTS
- PATCH_NOTES?
- RUN_SUMMARY

## [M] GATES (canonical)
PASS_IF:
- UID present
- VERSION present
- Required sections present
- Outputs are artifacts (not raw chat)

REWORK_IF:
- Missing CAPABILITIES/INPUTS/OUTPUTS clarity
- Dependencies exceed minimal set
- Over-noise in sections

FAIL_IF:
- RAW embedded
- Key references bypass INDEX_MANIFEST
- Contradicting rules inside passport

## [M] BODY_TEMPLATE

### ENTITY_HEADER
ENTITY_TYPE: ENGINE
ENTITY_NAME: <REPLACE_ME>
ENTITY_KEY: <KEY_FOR_INDEX_MANIFEST>         # e.g. ENT.ENGINE.AUD.MIX.001 (your system decides)
DOMAIN_TAGS: [<LIST>]                         # e.g. [AUD], [VIS], [SYS]
OWNER_TEAM: <SYS|TEAM>
LIFECYCLE: ACTIVE|DRAFT|DEPRECATED

### PURPOSE
<1-2 lines>

### ROLE
Что делает этот ENGINE в системе (одной строкой).

### CAPABILITIES
- <capability 1>
- <capability 2>
- <capability 3>

### INPUTS
- TOKENS: [TASK_TEXT, <OTHER_TOKENS...>]
- REQUIRED_CONTEXT: <one line>
- ASSUMPTIONS: <one line>

### OUTPUTS
- ARTIFACTS: [<OUTPUT_PACK_TYPE>, <OTHER_ARTIFACTS...>]
- TOKENS: [RUN_SUMMARY, PATCH_NOTES?]

### DEPENDENCIES (KEYS ONLY)
- INDEX_KEYS: [<KEYS_ONLY>]                   # references to REG/XREF/KB/LAW/STD as KEYS
- OPTIONAL_KEYS: [<KEYS_ONLY>]

### EXECUTION_MODEL
- EXEC_MODE: FAST|RELEASE_READY|MASTERPIECE
- STEP_STYLE: STEP-RUN
- DEFAULT_STRATEGY: <one line>

### ARTIFACTS
- OUTPUT_PACK: <OUTPUT_PACK_TYPE>
- STRUCTURE:
  - SUMMARY: <1-3 bullets>
  - MAIN: <core result>
  - CHECKS: <gate results>
  - NEXT: <go / next step>

### INTERFACES (KEYS ONLY)
- INPUT_INTERFACES: [<KEYS_ONLY>]
- OUTPUT_INTERFACES: [<KEYS_ONLY>]
- NOTES: "Resolve via INDEX_MANIFEST only"

### KB_SCOPE
KB_INPUTS:
- <what knowledge is allowed/needed>

KB_OUTPUTS:
- <what gets written/produced>

KB_BOUNDARIES:
- No guessing
- No RAW inside entity
- Only sources resolved via INDEX_MANIFEST keys

### GATES
PASS_IF:
- <list>

REWORK_IF:
- <list>

FAIL_IF:
- <list>

### CHANGELOG (append-only)
- DATE: 0000-00-00
  CHANGE_ID: <REPLACE_ME>
  TYPE: CREATE|UPDATE|DEPRECATE
  NOTES: <one line>
