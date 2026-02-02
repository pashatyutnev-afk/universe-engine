FILE: UE_V2/03_ENT/50_VAL_ENT/11_VALIDATION_ENGINES/01__VAL_ENG__ERROR_DETECTION__ENG__VAL__ENT.md
SCOPE: UE_V2 / 03_ENT / 50_VAL_ENT / 11_VALIDATION_ENGINES
DOC_TYPE: VAL_ENTITY
DOMAIN: VAL_ENG_VAL_ENT
UID: UE.V2.ENT.VAL_ENG.ERROR_DETECTION.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: VAL_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: VAL_ENG_ERROR_DETECTION
- ENTITY_CLASS: VAL_ENG
- UID: UE.V2.ENT.VAL_ENG.ERROR_DETECTION.001

## [M] PURPOSE
Выявляет структурные ошибки артефактов: отсутствующие поля, неправильные секции, недетерминированный формат, нарушенные правила “RAW only in index”.

## [M] SCOPE
- TARGET_DOMAIN: MULTI
- APPLIES_TO: [DOC_TEXT, TOKEN_PACKS, PROMPT_PACK, METADATA_PACK]
- NON_GOALS: [смысловая оценка, художественная критика]

## [M] INPUTS / OUTPUTS
- Inputs: [ARTIFACT_TEXT?, ARTIFACT_HINTS?]
- Outputs: [VAL_DECISION, VAL_FINDINGS, REQUIRED_FIXES, VIOLATIONS]

## [M] CHECKS
- C1: Обязательные заголовки/поля присутствуют для данного DOC_TYPE.
- C2: Нет RAW ссылок в non-index документах.
- C3: Секции не перепутаны (например, CONTRACT без RAW).
- C4: UID/VERSION/STATUS присутствуют и валидны по формату (как строка).
- C5: Есть SELF в INDEX_MANIFEST (если проверяется индекс).

## [M] EVIDENCE_REQUIREMENTS
- E1: PASS требует, чтобы ошибки формата не найдены.
- E2: Если вход пустой -> ASK.
- E3: При нарушении правила RAW -> FAIL.

## [M] DECISION_MATRIX
- IF ARTIFACT_TEXT отсутствует -> ASK
- IF RAW найден в non-index -> FAIL (UE.FAIL.RULE_VIOLATION)
- IF отсутствуют критические поля -> FAIL (UE.FAIL.GATE_FAIL)
- IF есть некритичные несоответствия -> WARN
- ELSE -> PASS

## [M] VIOLATIONS
- V.ERR.NO_INPUT
- V.ERR.RAW_OUTSIDE_INDEX
- V.ERR.MISSING_REQUIRED_FIELDS
- V.ERR.SECTION_MISORDER

## [M] FAIL_CODES
- UE.FAIL.INPUT_ABSENT
- UE.FAIL.RULE_VIOLATION
- UE.FAIL.GATE_FAIL

## [M] KB SCOPE
- KB Inputs: [artifact text and hints]
- KB Outputs: [format error list]
- KB Boundaries: [не придумывать отсутствующие поля]
- KB RAW refs: []

## [M] GATES
- PASS if: формат валиден
- FAIL if: RAW вне индекса или отсутствуют обязательные поля

## [M] SPC PEER ROLES (NON-ENG)
- Works with: [ORC_ENT, CTL_ENT, QA_ENT]
- Handoff rules: FAIL -> fix format; WARN -> patch; ASK -> provide artifact
