FILE: UE_V2/03_ENT/60_QA_ENT/90_SHARED_LIB_QA_ENT/01__LIB__QA_SEVERITY_SCALE__QA__ENT.md
SCOPE: UE_V2 / 03_ENT / 60_QA_ENT / 90_SHARED_LIB_QA_ENT
DOC_TYPE: QA_ENTITY
DOMAIN: LIB_QA_ENT
UID: UE.V2.ENT.QA.LIB.SEVERITY_SCALE.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: QA_ENT
NAV_RULE: No RAW in entity docs

---

## [M] ENTITY_HEADER
- ENTITY_NAME: QA_SEVERITY_SCALE_LIB
- ENTITY_CLASS: QA
- UID: UE.V2.ENT.QA.LIB.SEVERITY_SCALE.001

## [M] PURPOSE
Каноническая шкала severity для QA: как маркировать проблемы и что означает уровень.

## [M] SCOPE
- TARGET_DOMAIN: MULTI
- APPLIES_TO: [QA_REPORTS, QA_ISSUES]
- NON_GOALS: [политические/медицинские выводы]

## [M] SEVERITY LEVELS
- SEV.BLOCK
  - Meaning: продолжать нельзя, нужно исправление
  - Typical: critical format break, unusable artifact, policy break
- SEV.HIGH
  - Meaning: можно продолжать только с явным решением/планом фикса
  - Typical: major quality/clarity failures that still have workaround
- SEV.MED
  - Meaning: не блокирует, но fixes обязательны
  - Typical: notable issues; needs cleanup
- SEV.LOW
  - Meaning: замечание; фикс по желанию
  - Typical: minor stylistic/polish issues

## [M] BINDING TO QA_DECISION
- FAIL -> usually SEV.BLOCK or SEV.HIGH
- WARN -> usually SEV.MED
- PASS -> no issues
- ASK -> missing inputs; severity not applicable

## [M] GATES
- PASS if: reports/issues use this scale consistently
- FAIL if: severity labels mismatch decision
