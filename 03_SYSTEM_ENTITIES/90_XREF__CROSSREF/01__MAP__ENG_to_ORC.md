# XREF MAP — ENG TO ORC (CANON)

FILE: 03_SYSTEM_ENTITIES/90_XREF__CROSSREF/01__MAP__ENG_TO_ORC.md
SCOPE: Universe Engine (Games volume)
SERIAL: C425-B513
LAYER: 03_SYSTEM_ENTITIES
REALM: 90_XREF__CROSSREF
DOC_TYPE: MAP
MAP_TYPE: ENG_TO_ORC
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.XREF.MAP.ENG_TO_ORC.001
OWNER: SYSTEM
ROLE: SoT mapping of ENG capabilities to ORC pipelines that consume them.

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: CREATE
- SUMMARY: "Created ENG→ORC mapping schema with routing-ready fields."
- REASON: "Make engine usage explicit and prevent hidden dependencies."
- IMPACT: "ORC routing can choose minimal sufficient ENG set deterministically."
- CHANGE_ID: UE.CHG.2026-01-20.XREF.MAP.ENG2ORC.001

---

## 0) PURPOSE (LAW)
Карта фиксирует: какие ENG используются какими ORC.
Если связь не описана здесь — она не считается поддерживаемой связкой.

---

## 1) FIELD DICTIONARY
- ENG_ID: stable id of engine entity
- ENG_NAME: human name
- ENG_LAYER: which realm/layer it belongs to
- ORC_ID: orchestrator id
- ORC_NAME: orchestrator/pipeline name
- CONTRACT: 1–2 строки что ENG даёт и что ORC ожидает
- STATUS: ACTIVE | DEPRECATED
- NOTES: optional

---

## 2) MAP TABLE (FILL)
| ENG_ID | ENG_NAME | ENG_LAYER | ORC_ID | ORC_NAME | CONTRACT | STATUS | NOTES |
|---|---|---|---|---|---|---|---|
| TBD | TBD | TBD | TBD | TBD | TBD | ACTIVE |  |

---

## 3) CHANGE LOG (LOCAL)
- Use CHANGE_NOTE only in header; per-row changes go to NOTES or separate audit log if required.

--- END.
