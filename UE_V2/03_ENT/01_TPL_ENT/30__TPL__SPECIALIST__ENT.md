FILE: UE_V2/03_ENT/01_TPL_ENT/30__TPL__SPECIALIST__ENT.md
SCOPE: UE_V2 / 03_ENT / 01_TPL_ENT
DOC_TYPE: TEMPLATE
TEMPLATE_FOR: ENTITY_PASSPORT (SPECIALIST)
DOMAIN: ENT
UID: UE.V2.ENT.TPL.SPECIALIST.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-01-31
UPDATED: 2026-01-31
OWNER: SYS
NAV_RULE: Template has no RAW

---

## [M] PURPOSE
Шаблон паспорта SPECIALIST.
SPECIALIST даёт доменное решение/оценку и выпускает ARTIFACT_OUTPUT (не “голый текст”).

## [M] HARD_RULES
- Никаких RAW внутри. Только KEYS и токены.
- Output всегда упакован как ARTIFACT_OUTPUT (мини output pack).
- Обязательны CHECKS и NEXT ("го"/FAIL).
- Минимальность: без воды, 1–2 строки на пункт.

## [M] OUTPUT_PACK_MINI (canonical)
- SUMMARY: 1–3 bullets
- MAIN: core result
- CHECKS: gates results
- RISKS: 0–3 bullets
- NEXT: "го" | FAIL_CODE

## [M] BODY_TEMPLATE

### ENTITY_HEADER
ENTITY_TYPE: SPECIALIST
ENTITY_NAME: <REPLACE_ME>
ENTITY_KEY: <KEY_FOR_INDEX_MANIFEST>
DOMAIN_TAGS: [<LIST>]
OWNER_TEAM: <SYS|TEAM>
LIFECYCLE: ACTIVE|DRAFT|DEPRECATED

### PURPOSE
<1-2 lines>

### ROLE
Одна строка: какую часть задачи закрывает этот SPECIALIST.

### INPUTS
- TOKENS: [TASK_TEXT, CONTEXT_MIN?, <DOMAIN_TOKENS...>]
- REQUIRED: [TASK_TEXT]

### OUTPUTS
- ARTIFACTS: [SPECIALIST_OUTPUT]
- TOKENS: [NOTES?, PATCH_NOTES?]

### METHOD (minimal)
- APPROACH: <one line>
- HEURISTICS: [<0-3 bullets>]
- LIMITS: <one line>

### DEPENDENCIES (KEYS ONLY)
- LAW_KEYS: [LAW_01, LAW_03, LAW_04, LAW_05, LAW_06, LAW_14]
- REG/XREF/KB_KEYS: [<KEYS_ONLY>]

### SPECIALIST_OUTPUT (use this format)
SUMMARY:
- <bullet>
- <bullet>

MAIN:
<core result>

CHECKS:
- <gate>: PASS|REWORK|FAIL

RISKS:
- <risk 1?>
- <risk 2?>

NEXT:
"го" | <FAIL_CODE>

### GATES
PASS_IF:
- output in SPECIALIST_OUTPUT format
REWORK_IF:
- missing checks / too verbose
FAIL_IF:
- RAW inside / contradicting canon / no artifact

### CHANGELOG (append-only)
- DATE: 0000-00-00
  CHANGE_ID: <REPLACE_ME>
  TYPE: CREATE|UPDATE|DEPRECATE
  NOTES: <one line>
