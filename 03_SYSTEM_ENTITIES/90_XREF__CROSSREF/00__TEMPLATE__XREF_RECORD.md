# TEMPLATE — XREF RECORD

FILE: 03_SYSTEM_ENTITIES/90_XREF__CROSSREF/00__TEMPLATE__XREF_RECORD.md
SCOPE: Universe Engine (Games volume)
SERIAL: C425-B513
LAYER: 03_SYSTEM_ENTITIES
DOC_TYPE: TEMPLATE
TEMPLATE_TYPE: XREF_RECORD
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.TPL.XREF.RECORD.001
OWNER: SYSTEM
ROLE: A single mapping record schema (for row keys + normalization rules).

---

## 0) PURPOSE (LAW)
Шаблон описывает ключ записи (как понять “это та же связь” или новая) и какие поля обязательны.

---

## 1) KEY RULE (ANTI-DUP)
Define KEY as:
- MAP_TYPE specific primary key (example):
  - ENG_TO_ORC: (ENG_ID + ORC_ID)
  - ORC_TO_SPC: (ORC_ID + SPC_ID + OWNERSHIP)
  - PIPELINES: (PIPELINE_ID)
  - VALIDATION_MATRIX: (ARTIFACT_TYPE)

Если KEY совпал — это UPDATE, а не новая запись.

---

## 2) REQUIRED FIELDS (MINIMUM)
- MAP_TYPE
- KEY
- FIELDS (dict)
- STATUS
- NOTES

---

## 3) NORMALIZATION
- IDs must be stable and consistent (same casing, same separators).
- Avoid free-form names in KEY; names are descriptive only.

--- END.
