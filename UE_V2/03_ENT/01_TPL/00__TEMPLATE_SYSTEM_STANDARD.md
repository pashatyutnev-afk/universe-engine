# TEMPLATE SYSTEM STANDARD — TPL LAYER (CANON)
FILE: 03_SYSTEM_ENTITIES/01_TPL__TEMPLATES/00__TEMPLATE_SYSTEM_STANDARD.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: TEMPLATES (TPL)
DOC_TYPE: STANDARD
STANDARD_TYPE: TEMPLATE_SYSTEM
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.1.0
UID: UE.TPL.STD.SYSTEM.001
OWNER: SYSTEM
ROLE: Defines how templates are written and applied across all entity classes (ENG/ORC/SPC/CTL/VAL/QA/INDEX/README)

CHANGE_NOTE:
- DATE: 2026-01-11
- TYPE: MAJOR
- SUMMARY: "Rebuilt template standard: strict template contract, anti-law rule, RAW-only interface references, and apply workflow."
- REASON: "Templates must stay consistent and not compete with System Law."
- IMPACT: "All new entities become uniform + indexable + audit-friendly."
- CHANGE_ID: UE.CHG.2026-01-11.TPL.STD.SYSTEM.002

---

## 0) PURPOSE (LAW FOR TEMPLATES)
This standard defines:
- what a TEMPLATE is (scope + boundaries)
- mandatory blocks that every template must contain
- how templates are applied when creating new files
- anti-sprawl rules (no template multiplication without reason)

---

## 1) AUTHORITY (IMPORTANT)
Templates are **NOT** laws.

If any template text conflicts with:
- `01_SYSTEM_LAW/*` (system laws)
- `02_STANDARDS/*` (standards)

Then the template must be corrected.  
Templates only **implement** law/standards structure; they do not create new authority.

---

## 2) TEMPLATE TYPES (SUPPORTED)
This folder contains templates for:
- ENTITY templates:
  - `ENG` (engine file)
  - `ORC` (orchestrator file)
  - `SPC` (specialist file)
  - `CTL` (controller file)
  - `VAL` (validator file)
  - `QA` (qa check/entity/issue file)
- META templates:
  - `INDEX` (index file template)
  - `README REALM` (realm/readme template)

---

## 3) UNIVERSAL TEMPLATE HEADER (MANDATORY)
Every template must start with a canonical header block.

Required fields (strict):
- FILE:
- SCOPE:
- LAYER:
- ENTITY_GROUP:
- DOC_TYPE:
- TEMPLATE_TYPE:
- LEVEL:
- STATUS:
- LOCK:
- VERSION:
- UID:
- OWNER:
- ROLE:

Notes:
- STATUS must be one of: `DRAFT | ACTIVE | DEPRECATED | ARCHIVED`
- LOCK must be one of: `OPEN | FIXED`
- Do not duplicate STATUS/LOCK blocks later in the file.

---

## 4) TEMPLATE CONTRACT (MANDATORY SECTIONS)
Every template must contain these sections in this order:

### 4.1 PURPOSE
- What this template creates and why.

### 4.2 TARGET
- TARGET_CLASS: `ENG | ORC | SPC | CTL | VAL | QA | INDEX | README`
- TARGET_FOLDER: canonical base path for that class (label only)
- REQUIRED_INDEX_OWNER: which index must register created files

### 4.3 STRUCTURE SKELETON
- A complete section skeleton the created file must contain.
- Use placeholders with clear markers:
  - `<PLACEHOLDER>` or `[PLACEHOLDER]`
- Do not leave “TODO without meaning”.

### 4.4 SYSTEM INTERFACE (WHEN APPLICABLE)
If the template is for `ENG/ORC/CTL/VAL/QA` (and optionally SPC),
it must include a compact interface contract:

- CONSUMES:
- PRODUCES:
- DEPENDS_ON:
- OUTPUT_TARGET:

IMPORTANT:
- For references, prefer RAW links (operational navigation).
- PATH can be used only as human label.

### 4.5 INDEX + REGISTRATION CHECKLIST
Template must include a checklist that the creator must follow:
- Register in the correct index
- Create/update family README if required
- Add XREF/Dependency records if required by the class

### 4.6 FINAL RULE (LOCK)
A final block declaring:
- OWNER:
- LOCK:

---

## 5) ANTI-SPRAWL TEMPLATE RULE (STRICT)
Do not create “variant templates” for tiny styling changes.

Allowed reasons to create an additional template:
- different entity contract (new mandatory blocks)
- different pipeline requirements (different gates/validators/outputs)
- separate family-level standard that must exist everywhere

Otherwise: update the main template instead.

---

## 6) APPLY WORKFLOW (HOW TO USE TEMPLATES)
When creating a new entity file:
1) Choose correct template by class (ENG/ORC/SPC/CTL/VAL/QA).
2) Copy template content → new file.
3) Fill placeholders.
4) Ensure naming + numbering compliance (by System Law).
5) Register file in the correct index (existence).
6) If dependencies exist → register dependency/xref (where required).

---

## 7) MINIMUM QUALITY BAR (TEMPLATE QA)
A template is considered VALID only if:
- it contains the full mandatory header
- it contains the full mandatory sections (4.*)
- it does not introduce new laws (section 1)
- it produces a file that can be registered immediately

---

## FINAL RULE (LOCK)
This standard is binding for templates in `01_TPL__TEMPLATES`.
Templates must stay consistent with `01_SYSTEM_LAW` and `02_STANDARDS`.

OWNER: SYSTEM
LOCK: FIXED

--- END.
