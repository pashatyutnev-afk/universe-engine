# XREF MAP — PIPELINES (CANON)

FILE: 03_SYSTEM_ENTITIES/90_XREF__CROSSREF/04__MAP__PIPELINES.md
SCOPE: Universe Engine (Games volume)
SERIAL: C425-B513
LAYER: 03_SYSTEM_ENTITIES
REALM: 90_XREF__CROSSREF
DOC_TYPE: MAP
MAP_TYPE: PIPELINES
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.XREF.MAP.PIPELINES.001
OWNER: SYSTEM
ROLE: Pipeline registry + minimal routing metadata (owner ORC/SPC, ENG set, gates, targets).

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: CREATE
- SUMMARY: "Created pipelines map schema to make production routes discoverable."
- REASON: "Without pipeline registry routing becomes guesswork."
- IMPACT: "Tasks can be routed by intent: pipeline → orc/spc/eng/gates/targets."
- CHANGE_ID: UE.CHG.2026-01-20.XREF.MAP.PIPELINES.001

---

## 0) PURPOSE (LAW)
Реестр пайплайнов: что существует, кто владеет, какие ENG нужны, какие гейты, куда кладём результат.

---

## 1) FIELD DICTIONARY
- PIPELINE_ID
- PIPELINE_NAME
- PRIMARY_ORC
- PRIMARY_SPC
- ENG_SET (comma ids)
- GATES (CTL/VAL/QA)
- OUTPUT_TARGET (PRJ/OUT/KB/AST path class)
- STATUS (ACTIVE/DEPRECATED)
- NOTES

---

## 2) PIPELINES TABLE (FILL)
| PIPELINE_ID | PIPELINE_NAME | PRIMARY_ORC | PRIMARY_SPC | ENG_SET | GATES | OUTPUT_TARGET | STATUS | NOTES |
|---|---|---|---|---|---|---|---|---|
| TBD | TBD | TBD | TBD | TBD | READINESS_CHECK_CTL + TBD | TBD | ACTIVE |  |

--- END.
