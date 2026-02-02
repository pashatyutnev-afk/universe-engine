FILE: UE_V2/03_ENT/50_VAL_ENT/00_TEMPLATES_VAL_ENT/02__TPL__VAL_VIOLATION__VAL__ENT.md
SCOPE: UE_V2 / 03_ENT / 50_VAL_ENT / 00_TEMPLATES_VAL_ENT
DOC_TYPE: TPL
DOMAIN: TPL_VAL_ENT
UID: UE.V2.ENT.TPL.VAL_VIOLATION.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: VAL_ENT
NAV_RULE: Template doc contains no RAW

---

## [M] TEMPLATE_NAME
VAL_VIOLATION_TEMPLATE

## [M] PURPOSE
Шаблон записи нарушения (violation): что обнаружено, доказательство, влияние, требуемый фикс, severity и fail code.

---

# [T] VIOLATION RECORD (copy and fill)
- VIOLATION_ID: <V.DOMAIN.TYPE.CODE>
- TITLE: <short title>
- SEVERITY: BLOCK|HIGH|MED|LOW
- EVIDENCE: <what was observed (facts only)>
- IMPACT: <one line>
- REQUIRED_FIX: <one line actionable fix>
- FAIL_CODE: <code>
- NOTES: <optional, short>

## [M] SEVERITY GUIDELINE
- BLOCK: нельзя продолжать до фикса
- HIGH: продолжать только с явным решением/эскалацией
- MED: можно продолжать, но вернуть REQUIRED_FIXES
- LOW: замечание, не блокирует

## [M] FAIL CODE GUIDELINE
- UE.FAIL.RULE_VIOLATION — правило нарушено
- UE.FAIL.GATE_FAIL — гейт не пройден
- UE.FAIL.INPUT_ABSENT — не хватает входных данных
