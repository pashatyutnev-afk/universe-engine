# REG REGISTRIES REALM — README (CANON)
FILE: 03_SYSTEM_ENTITIES/00_REG__REGISTRIES/00__README__REGISTRIES.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: REGISTRIES (REG)
DOC_TYPE: README
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.REG.REALM.001
OWNER: SYSTEM
ROLE: Explains REG registries purpose, boundaries, and how to navigate/use them (RAW-ONLY NAV)

CHANGE_NOTE:
- DATE: 2026-01-11
- TYPE: MAJOR
- SUMMARY: "Created REG registries realm README: scope, usage, boundaries, and operational rules."
- REASON: "Folder must be self-explaining and deterministic for operators."
- IMPACT: "Anyone can correctly use REG layer without guessing."
- CHANGE_ID: UE.CHG.2026-01-11.REG.REALM.001

---

## 0) WHAT IS THIS FOLDER
`00_REG__REGISTRIES` is a **service registry folder** for the whole `03_SYSTEM_ENTITIES` layer.

It contains:
- canonical registries that standardize **IDs**, **naming**, **paths**, **deprecation**, and **changelog**
- templates for how a registry record must look
- operational laws to prevent drift, duplicates, and silent divergence

This folder is not “content”.  
It is **infrastructure**: rules + maps that keep the system coherent.

---

## 1) NAV MODE (RAW-ONLY)
- Navigation is **RAW-only**.
- Do not rely on repo browsing or in-file links.
- Open the folder index and copy RAW links into the address bar.

Folder Index (canon):
- `00__INDEX_ALL_REGISTRIES.md`

---

## 2) WHAT LIVES HERE (SCOPE)
This folder defines and maintains:
1) **ENTITY ID registry** (UID schemes, ID namespaces, collision handling)
2) **NAMING rules registry** (file/folder naming, tokens, numbering rules)
3) **PATH map** (where things live in the repository, canonical paths)
4) **CHANGELOG** (audit of changes inside registries)
5) **DEPRECATION** (how to retire, alias, pointer, archive without breaking canon)

---

## 3) WHAT DOES NOT LIVE HERE (BOUNDARIES)
Not allowed in `00_REG__REGISTRIES`:
- new “laws” that belong to `01_SYSTEM_LAW`
- standards that belong to `02_STANDARDS`
- entity definitions that belong to ENG/ORC/SPC/CTL/VAL/QA
- project work artifacts (those belong to `05_PROJECTS`)

This folder is only **registries + templates + governance support**.

---

## 4) HOW TO USE (OPERATOR FLOW)
A) Need correct UID / ID format  
→ open `01__REG_ENTITY_IDS.md`

B) Need correct file/folder naming  
→ open `02__REG_NAMING_RULES.md`

C) Need to know where a thing should live (canonical paths)  
→ open `03__REG_PATH_MAP.md`

D) You changed any registry rule/map  
→ append a record to `90__REG_CHANGELOG.md`

E) You want to retire/replace something without breaking navigation  
→ follow `91__REG_DEPRECATION.md`

---

## 5) ENFORCEMENT RULES (HARD)
### 5.1 Existence (hard)
- Only files listed in `00__INDEX_ALL_REGISTRIES.md` exist for this folder.

### 5.2 No extra files (hard)
- Any extra file must be removed or converted to a pure POINTER.

### 5.3 Alias rule (hard)
- Any duplicate index/readme/template variants must be POINTERs to canon.

### 5.4 Change logging (hard)
- Any change in this folder must create a record in:
  `90__REG_CHANGELOG.md`

---

## 6) TEMPLATE POLICY
Registry records must follow the folder template:
- `00__TEMPLATE__REGISTRY.md` (or `00__TEMPLATE_REGISTRY.md` depending on canon name)

No custom record formats are allowed unless the template is updated and logged.

---

## FINAL RULE (LOCK)
This README defines the operational meaning of REG registries folder.  
Any change must be logged in `90__REG_CHANGELOG.md`.

OWNER: SYSTEM  
LOCK: FIXED

--- END.
