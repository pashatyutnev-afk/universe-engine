FILE: UE_V2/03_ENT/90_XREF/03__MAP__VALIDATION_MATRIX__XREF.md
SCOPE: Universe Engine (UE_V2)
DOC_TYPE: XREF_MATRIX
DOMAIN: XREF
UID: UE.V2.XREF.VALIDATION_MATRIX.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-01-30
OWNER: SYS

---

# XREF — VALIDATION MATRIX

PURPOSE:
Матрица обязательных проверок по шагам. Используется роутером/пайпом, чтобы не пропускать REG/XREF/KB/PIPE/NAV/LOG.

---

## CHECK DEFINITIONS

| CHECK_ID | TYPE | DESCRIPTION |
|---|---|---|
| V.REG_UID | VAL | UID format + collision check (REG.UID_REGISTRY) |
| V.NAV_ACCESS | VAL | доступ к NAV_ROOT и требуемым IDX |
| V.PIPE_EXISTS | VAL | наличие PIPE_DEFAULT или доменного PIPE |
| V.KB_SCOPE | VAL | KB_SCOPE boundaries are declared |
| V.NOISE_POLICY | VAL | соблюдение anti-noise policy |
| Q.OUTPUT_FORMAT | QA | формат артефакта соответствует шаблону |
| Q.CONTENT_QUALITY | QA | качество по доменным критериям |
| Q.SAFETY | QA | запреты/ограничения (если есть) |

---

## MATRIX (by phase)

| PHASE | MUST_CHECKS | OPTIONAL_CHECKS |
|---|---|---|
| BOOT | V.NAV_ACCESS, V.PIPE_EXISTS | V.NOISE_POLICY |
| ROUTE | V.NOISE_POLICY | V.KB_SCOPE |
| EXEC | V.REG_UID, V.KB_SCOPE | Q.OUTPUT_FORMAT |
| FINAL | Q.OUTPUT_FORMAT | Q.CONTENT_QUALITY, Q.SAFETY |

RULE:
- MUST_CHECKS missing mapping → GAP (если можно временно пропустить), но:
- V.NAV_ACCESS и V.PIPE_EXISTS missing → STOP
