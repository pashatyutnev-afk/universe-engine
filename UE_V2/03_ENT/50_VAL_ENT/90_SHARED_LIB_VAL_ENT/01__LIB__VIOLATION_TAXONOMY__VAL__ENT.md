FILE: UE_V2/03_ENT/50_VAL_ENT/90_SHARED_LIB_VAL_ENT/01__LIB__VIOLATION_TAXONOMY__VAL__ENT.md
SCOPE: UE_V2 / 03_ENT / 50_VAL_ENT / 90_SHARED_LIB_VAL_ENT
DOC_TYPE: VAL_ENTITY
DOMAIN: LIB_VAL_ENT
UID: UE.V2.ENT.VAL.LIB.VIOLATION_TAXONOMY.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: VAL_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: LIB_VIOLATION_TAXONOMY_VAL
- ENTITY_CLASS: VAL
- UID: UE.V2.ENT.VAL.LIB.VIOLATION_TAXONOMY.001

## [M] PURPOSE
Каноническая таксономия нарушений для VAL слоя: единый формат violation_id, severity и минимальные поля.

## [M] SCOPE
- TARGET_DOMAIN: MULTI
- APPLIES_TO: [ALL_VAL_REPORTS, ALL_VALIDATORS]
- NON_GOALS: [полная предметная онтология]

## [M] INPUTS / OUTPUTS
- Inputs: [VALIDATION_FINDINGS?]
- Outputs: [VIOLATION_IDS, SEVERITY_CLASS, REQUIRED_FIELDS]

## [M] FORMAT (violation id)
- Pattern: `V.<DOMAIN>.<TYPE>.<CODE>`
  - DOMAIN: MUS|VID|WEB|DOC|LIB|VAL_ENG|MULTI
  - TYPE: INPUT|FORMAT|POLICY|QUALITY|SAFETY|CONSISTENCY|A11Y|EXPORT|TIMELINE
  - CODE: короткий идентификатор (ASCII, UPPER_SNAKE)

## [M] SEVERITY
- BLOCK: нельзя продолжать, нужно исправление
- HIGH: продолжать только при явном решении/эскалации
- MED: можно продолжать, но REQUIRED_FIXES обязательны
- LOW: замечание

## [M] REQUIRED_VIOLATION_FIELDS
- VIOLATION_ID
- TITLE
- SEVERITY
- EVIDENCE (facts only)
- IMPACT (one line)
- REQUIRED_FIX (one line)
- FAIL_CODE (if BLOCK/HIGH or if validator policy requires)

## [M] CANONICAL VIOLATIONS (minimal set)
- V.MULTI.INPUT.MISSING_REQUIRED — отсутствует обязательный вход
- V.MULTI.FORMAT.MISSING_HEADER_FIELDS — нет полей хедера
- V.MULTI.POLICY.RAW_OUTSIDE_INDEX — RAW найден вне INDEX_MANIFEST
- V.MULTI.POLICY.DIRECT_COPY — признаки прямого копирования
- V.MUS.QUALITY.HOOK_LATE — хук слишком поздний (если применимо)
- V.MUS.CONSISTENCY.NAME_COLLISION — коллизия названия
- V.VID.EXPORT.PARAM_CONFLICT — конфликт параметров экспорта
- V.VID.POLICY.SUBJECT_DRIFT_RISK — риск дрейфа субъекта
- V.WEB.A11Y.KEYBOARD_FAIL — интерактивы недоступны с клавиатуры
- V.WEB.A11Y.NO_FOCUS — нет видимого фокуса
- V.DOC.FORMAT.MISSING_SECTIONS — отсутствуют обязательные секции
- V.VAL_ENG.CONSISTENCY.CONTRADICTION — внутреннее противоречие

## [M] DECISION_MATRIX
- IF violation record missing required fields -> FAIL
- ELSE -> PASS

## [M] FAIL_CODES
- UE.FAIL.GATE_FAIL

## [M] KB SCOPE
- KB Inputs: [validator outputs]
- KB Outputs: [normalized violations]
- KB Boundaries: [не придумывать evidence]
- KB RAW refs: []

## [M] GATES
- PASS if: violations conform to schema
- FAIL if: missing required violation fields
