# CROSSREF — INDEX (CANON)

FILE: 03_SYSTEM_ENTITIES/90_XREF__CROSSREF/00__INDEX__CROSSREF.md
SCOPE: Universe Engine (Games volume)
SERIAL: C425-B513
LAYER: 03_SYSTEM_ENTITIES
REALM: 90_XREF__CROSSREF
DOC_TYPE: INDEX (REALM)
INDEX_TYPE: REALM
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.XREF.IDX.REALM.001
OWNER: SYSTEM
ROLE: Single registry snapshot of XREF realm artifacts (names + purpose). No navigation links inside.

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: CREATE
- SUMMARY: "Created realm index without inline navigation links; lists artifacts + intent only."
- REASON: "Avoid fragile links; keep routing via ROOT LINK BASE / user-provided RAW."
- IMPACT: "Index stays stable even when repo paths change; human-readable registry remains."
- CHANGE_ID: UE.CHG.2026-01-20.XREF.IDX.001

---

## 0) PURPOSE (LAW)
Этот INDEX фиксирует состав XREF-реалма и назначение файлов.
Навигация делается через ROOT LINK BASE или RAW, присланные пользователем.

---

## 1) ARTIFACTS REGISTRY (SNAPSHOT)
### CORE
- 00__README__CROSSREF.md
  - Purpose: boundaries + what lives in XREF realm
- 01__RULES__XREF.md
  - Purpose: laws + authoring rules + SoT discipline

### MAPS
- 01__MAP__ENG_TO_ORC.md
  - Purpose: which ORC pipelines consume which ENG units
- 02__MAP__ORC_TO_SPC.md
  - Purpose: which SPC owns which ORC outputs / intents
- 03__MAP__VALIDATION_MATRIX.md
  - Purpose: required CTL/VAL/QA gates by artifact type / realm
- 04__MAP__PIPELINES.md
  - Purpose: pipeline registry + steps/gates/targets overview

### FLOW + TEMPLATES
- 02__CREATE_FLOW__XREF.md
  - Purpose: how to add/update XREF maps safely
- 00__TEMPLATE__XREF_INDEX.md
  - Purpose: template for future XREF indexes (if sub-realms appear)
- 00__TEMPLATE__XREF_RECORD.md
  - Purpose: template for a single XREF record (row/spec)

---

## 2) GOVERNANCE (WHO SIGNS)
- Doc-control gate: DOC_CONTROLLER_SPC
- Standards conflicts: STANDARDS_OWNER_SPC
- Canon disputes: GOVERNANCE_OWNER_SPC
- Architecture boundary conflicts: MACHINE_ARCHITECT_SPC

--- END.
