# TEMPLATES REALM (TPL) — README (CANON)
FILE: 03_SYSTEM_ENTITIES/01_TPL__TEMPLATES/00__README_TEMPLATES.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: TEMPLATES (TPL)
DOC_TYPE: README
README_TYPE: REALM
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.TPL.REALM.001
OWNER: SYSTEM
ROLE: Defines scope, boundaries, and usage rules for `01_TPL__TEMPLATES` (templates for all entity classes)

CHANGE_NOTE:
- DATE: 2026-01-11
- TYPE: MAJOR
- SUMMARY: "Created TPL realm README: scope, how-to, mandatory blocks, and anti-sprawl rules."
- REASON: "Templates must be applied consistently to keep entities uniform."
- IMPACT: "Faster creation + fewer structure errors."
- CHANGE_ID: UE.CHG.2026-01-11.TPL.REALM.001

---

## 0) WHAT THIS FOLDER IS
`01_TPL__TEMPLATES` is the **single source of templates** for entity files in `03_SYSTEM_ENTITIES`.

Templates are used to create:
- ENG Engines
- ORC Orchestrators
- SPC Specialists
- CTL Controllers
- VAL Validators
- QA checks/entities/issues
- Index/README realm templates

Goal:
- keep every entity file **structurally identical**
- reduce mistakes
- make system machine-readable

---

## 1) NAVIGATION (RAW-ONLY)
Canonical navigation for this folder is the index:
- `00__INDEX_ALL_TEMPLATES`

NAV works via RAW links only.

---

## 2) WHEN TO USE TEMPLATES
Use templates whenever you:
- create a new entity file (any class)
- create a new family README realm
- create an index for a folder/family/layer
- standardize old files to comply with current laws

---

## 3) TEMPLATE MINIMUM (MANDATORY)
Any template must define the minimum skeleton expected in the target entity.

Every entity template must contain:
1) Canon header block (SCOPE/LAYER/DOC_TYPE/STATUS/LOCK/UID/ROLE)
2) Mandatory sections required for that entity class
3) Final lock statement (OWNER/LOCK)

---

## 4) ANTI-SPRAWL RULE (IMPORTANT)
We do NOT create many templates for small variations.

Rule:
- One template per entity class is default.
- Additional templates are allowed only when:
  - the class has a truly different contract OR
  - a family has a unique mandatory block required everywhere inside that family

If a template exists but is rarely used → it should be deprecated or merged.

---

## 5) TEMPLATE UPGRADE RULE
If the system laws/standards evolve:
- templates must be updated first
- then entities are updated using templates as reference

Templates are the **source of structural truth** (but not law authority).
Law authority is in `01_SYSTEM_LAW` and `02_STANDARDS`.

---

## 6) OUTPUT EXPECTATION
After using templates, each created entity must be:
- readable without extra context
- consistent with the rest of the repository
- immediately indexable (added to the relevant index)
- compatible with RAW-only navigation

---

## 7) FILES IN THIS FOLDER (CANON)
See: `00__INDEX_ALL_TEMPLATES.md`

---

## FINAL RULE (LOCK)
Templates are mandatory for consistent creation.
No uncontrolled template multiplication is allowed.

OWNER: SYSTEM
LOCK: FIXED

--- END.
