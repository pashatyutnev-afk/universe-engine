FILE: UE_V2/03_ENT/40_CTL_ENT/90_SHARED_LIB_CTL_ENT/03__LIB__OUTPUT_NAMING_POLICY__CTL__ENT.md
SCOPE: UE_V2 / 03_ENT / 40_CTL_ENT / 90_SHARED_LIB_CTL_ENT
DOC_TYPE: CTL_ENTITY
DOMAIN: LIB_CTL_ENT
UID: UE.V2.ENT.CTL.LIB.OUTPUT_NAMING_POLICY.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: CTL_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: LIB_OUTPUT_NAMING_POLICY_CTL
- ENTITY_CLASS: CTL
- UID: UE.V2.ENT.CTL.LIB.OUTPUT_NAMING_POLICY.001

## [M] PURPOSE
Политика именования выходов: как называть OUTPUT_PACK, варианты, токены, артефакты, чтобы не было коллизий и хаоса.

## [M] SCOPE
- TARGET_DOMAIN: MULTI
- APPLIES_TO: [OUTPUT_PACK, VARIANT_ASSET, TOKEN_FILES, DOC_EXPORTS]
- NON_GOALS: [переименование файлов в репо в MODE REPO]

## [M] INPUTS / OUTPUTS
- Inputs: [PROJECT_TAG?, DOMAIN_TAG?, DATE?, VERSION?]
- Outputs: [CTL_DECISION, CTL_FINDINGS, REQUIRED_FIXES]

## [M] RULESET
- R1: Имена должны быть детерминированными: DOMAIN + ARTIFACT + DATE + VARIANT + VERSION (если применимо).
- R2: Запрещены пробелы, нестабильные символы, лишние спецзнаки.
- R3: Variant label обязателен при множестве вариантов (A/B/C или HookA/HookB).
- R4: Для релизных артефактов сохранять краткий human-title отдельно от file-name.

## [M] DECISION_MATRIX
- IF naming scheme not provided -> WARN (suggest scheme)
- IF name contains forbidden characters -> FAIL
- ELSE -> PASS

## [M] VIOLATIONS
- V.NAME.FORBIDDEN_CHARS
- V.NAME.MISSING_VARIANT
- V.NAME.NONDETERMINISTIC

## [M] FAIL_CODES
- UE.FAIL.GATE_FAIL
- UE.FAIL.RULE_VIOLATION

## [M] KB SCOPE
- KB Inputs: [domain tags and version hints]
- KB Outputs: [naming suggestions + fixes]
- KB Boundaries: [не менять репозиторий]
- KB RAW refs: []

## [M] GATES
- PASS if: имена валидны и стабильны
- FAIL if: запрещённые символы/коллизии

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [ORC_ENT]
- Handoff rules: FAIL -> rename; WARN -> adopt scheme; PASS -> continue
