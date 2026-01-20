# XREF MAP — ORC TO SPC (CANON)

FILE: 03_SYSTEM_ENTITIES/90_XREF__CROSSREF/02__MAP__ORC_TO_SPC.md
SCOPE: Universe Engine (Games volume)
SERIAL: C425-B513
LAYER: 03_SYSTEM_ENTITIES
REALM: 90_XREF__CROSSREF
DOC_TYPE: MAP
MAP_TYPE: ORC_TO_SPC
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.XREF.MAP.ORC_TO_SPC.001
OWNER: SYSTEM
ROLE: SoT mapping of ORC pipelines to SPC owners (intent/packaging/approval).

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: CREATE
- SUMMARY: "Created ORC→SPC mapping schema (ownership + artifact type)."
- REASON: "Prevent ambiguous ownership and missing signoffs."
- IMPACT: "Each ORC output has a primary SPC owner and defined artifact class."
- CHANGE_ID: UE.CHG.2026-01-20.XREF.MAP.ORC2SPC.001

---

## 0) PURPOSE (LAW)
Карта фиксирует, какой SPC владеет каким ORC (PRIMARY/SUPPORT) и какой класс артефакта выпускается.

---

## 1) FIELD DICTIONARY
- ORC_ID / ORC_NAME
- SPC_ID / SPC_NAME
- OWNERSHIP: PRIMARY | SUPPORT
- OUTPUT_ARTIFACT_TYPE: README | SPEC | MAP | RULES | RUNBOOK | PACKAGE | OTHER
- STATUS: ACTIVE | DEPRECATED
- NOTES

---

## 2) MAP TABLE (FILL)
| ORC_ID | ORC_NAME | SPC_ID | SPC_NAME | OWNERSHIP | OUTPUT_ARTIFACT_TYPE | STATUS | NOTES |
|---|---|---|---|---|---|---|---|
| TBD | TBD | TBD | TBD | PRIMARY | TBD | ACTIVE |  |

--- END.
