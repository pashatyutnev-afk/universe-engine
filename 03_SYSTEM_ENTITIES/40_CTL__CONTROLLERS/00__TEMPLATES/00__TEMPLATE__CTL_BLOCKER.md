# 00__TEMPLATE__CTL_BLOCKER

FILE: 03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/00__TEMPLATES/00__TEMPLATE__CTL_BLOCKER.md
SCOPE: Universe Engine / Controllers (CTL) / Blocker Template
SERIAL: C425-B513
LAYER: 03_SYSTEM_ENTITIES
DOC_TYPE: TEMPLATE
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.CTL.TPL.BLOCKER.001
OWNER: SYSTEM
ROLE: Single canonical format for CTL blocker records.

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: MAJOR
- SUMMARY: "Aligned blocker template with DOC CONTROL and severity policy."
- REASON: "Make blockers machine-checkable and consistent across CTL."
- IMPACT: "Blockers become audit-friendly and enforceable."

---

## BLOCKER (MANDATORY)
BLOCKER:
- CODE:
- SEVERITY: S0 | S1 | S2 | S3
- MESSAGE: ""
- REQUIRED_ACTION: ""

Severity guidance:
- S0: закон/канон/навигация нарушены
- S1: критично для корректного результата
- S2: важно, но может быть отложено если ORC разрешает
- S3: уведомление

--- END.
