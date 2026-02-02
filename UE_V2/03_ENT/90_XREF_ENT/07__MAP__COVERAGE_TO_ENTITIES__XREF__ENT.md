FILE: UE_V2/03_ENT/90_XREF/07__MAP__COVERAGE_TO_ENTITIES__XREF.md
SCOPE: Universe Engine (UE_V2)
DOC_TYPE: XREF_MATRIX
DOMAIN: XREF
UID: UE.V2.XREF.COVERAGE_TO_ENTITIES.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-01-30
OWNER: SYS

---

# XREF — COVERAGE TO ENTITIES

PURPOSE:
Матрица "функция → какая сущность отвечает", чтобы ничего не выпадало из процесса.

---

## COVERAGE MATRIX

| FUNCTION | PRIMARY_ROLE | SECONDARY_ROLE |
|---|---|---|
| Route selection | ORC | XREF |
| Anti-noise enforcement | CTL | VAL |
| UID collision check | VAL | REG |
| KB scope enforcement | VAL | KB |
| Artifact assembly | ENG | ORC |
| Quality pass | QA | VAL |
| Decision recording | ORC | LOG |
| Token archiving | ORC | LOG |
