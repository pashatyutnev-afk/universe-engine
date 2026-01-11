# TEMPLATE — REGISTRY RECORD (CANON)
FILE: 03_SYSTEM_ENTITIES/00_REG__REGISTRIES/00__TEMPLATE__REGISTRY.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: REGISTRIES (REG)
DOC_TYPE: TEMPLATE
TEMPLATE_TYPE: REGISTRY_RECORD
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.REG.TPL.RECORD.001
OWNER: SYSTEM
ROLE: Mandatory template for any registry document and any registry record (standardized fields + examples)

CHANGE_NOTE:
- DATE: 2026-01-11
- TYPE: MAJOR
- SUMMARY: "Created registry record template: strict header, record format, required fields, and examples."
- REASON: "Prevent inconsistent registries and reduce ambiguity."
- IMPACT: "All REG documents become uniform and machine-readable."
- CHANGE_ID: UE.CHG.2026-01-11.REG.TPL.RECORD.001

---

## 0) PURPOSE (LAW)
This TEMPLATE defines:
- how a REGISTRY document must be structured
- how each registry entry (record) must be written
- mandatory fields, allowed values, and enforcement rules

If a registry record does not follow this template — it is NON-CANON.

---

## 1) REGISTRY DOCUMENT HEADER (MANDATORY)
Every registry file must start with a canonical header block:

- `FILE:` <path>
- `SCOPE:` Universe Engine
- `LAYER:` 03_SYSTEM_ENTITIES
- `ENTITY_GROUP:` REGISTRIES (REG)
- `DOC_TYPE:` REGISTRY
- `REGISTRY_TYPE:` <short type, e.g. ENTITY_IDS | NAMING_RULES | PATH_MAP | CHANGELOG | DEPRECATION>
- `LEVEL:` L2
- `STATUS:` ACTIVE | DRAFT | DEPRECATED | ARCHIVED
- `LOCK:` OPEN | FIXED
- `VERSION:` x.y.z
- `UID:` <registry UID>
- `OWNER:` SYSTEM
- `ROLE:` <one-line purpose>
- `CHANGE_NOTE:` <required on any update>

### Minimal Change Note (mandatory on edits)
CHANGE_NOTE:
- DATE: YYYY-MM-DD
- TYPE: MAJOR | MINOR | PATCH
- SUMMARY: "<what changed>"
- REASON: "<why>"
- IMPACT: "<what breaks / what improves>"
- CHANGE_ID: UE.CHG.YYYY-MM-DD.<...>

---

## 2) RECORD FORMAT (MANDATORY)
Each record must be a **single block** with the following structure:

### RECORD BLOCK
`## <RECORD_KEY> — <RECORD_TITLE>`

- `KEY:` <unique key; must match heading>
- `CLASS:` <ID|NAMING|PATH|DEPRECATION|CHANGELOG|OTHER>
- `STATUS:` ACTIVE | DEPRECATED | ARCHIVED
- `SCOPE:` <where it applies>
- `OWNER:` <SYSTEM or role>
- `PRIORITY:` P0 | P1 | P2 | P3
- `RAW:` <raw link if record points to a file; else `RAW: N/A`>
- `RULE:` <the actual rule / statement (1–10 lines)>
- `CHECK:` <how to verify this rule>
- `FAIL:` <what counts as violation>
- `FIX:` <how to fix>
- `NOTES:` <optional>
- `LAST_CHANGE_ID:` <change id when last updated>

---

## 3) REQUIRED FIELDS (STRICT)
Every record must include:
- KEY
- CLASS
- STATUS
- SCOPE
- PRIORITY
- RULE
- CHECK
- FAIL
- FIX
- LAST_CHANGE_ID

If RAW is not applicable, set:
- `RAW: N/A`

---

## 4) ALLOWED VALUES (STRICT)
STATUS:
- ACTIVE
- DEPRECATED
- ARCHIVED

PRIORITY:
- P0 (system-breaking)
- P1 (high impact)
- P2 (medium)
- P3 (low)

CLASS (recommended):
- ID
- NAMING
- PATH
- DEPRECATION
- CHANGELOG
- OTHER

---

## 5) EXAMPLES

## REG.ID.NAMESPACE — UID namespace rule
- KEY: REG.ID.NAMESPACE
- CLASS: ID
- STATUS: ACTIVE
- SCOPE: 03_SYSTEM_ENTITIES/* (all entity classes)
- OWNER: SYSTEM
- PRIORITY: P0
- RAW: N/A
- RULE: UID namespaces are class-scoped (ENG/ORC/SPC/CTL/VAL/QA) and must not overlap.
- CHECK: Compare prefixes across entity families; ensure unique namespace per class.
- FAIL: Two different entity classes share the same UID namespace prefix.
- FIX: Assign unique namespace prefix and update affected docs; log change.
- NOTES: Keep namespaces short but explicit.
- LAST_CHANGE_ID: UE.CHG.2026-01-11.REG.TPL.RECORD.001

## REG.NAMING.DOUBLE_UNDERSCORE — double underscore placement
- KEY: REG.NAMING.DOUBLE_UNDERSCORE
- CLASS: NAMING
- STATUS: ACTIVE
- SCOPE: repo-wide filenames
- OWNER: SYSTEM
- PRIORITY: P1
- RAW: N/A
- RULE: Double underscore `__` is used only after numeric prefix (e.g., `01__NAME`); elsewhere use single `_`.
- CHECK: Scan filenames for `__` positions.
- FAIL: `__` appears in the middle of a filename not directly after numeric prefix.
- FIX: Rename file(s) and create pointer aliases if required by canon rules.
- NOTES: Extensions are hidden; do not include `.md` in human-facing references.
- LAST_CHANGE_ID: UE.CHG.2026-01-11.REG.TPL.RECORD.001

## REG.PATH.CANON_BASE — canonical base paths
- KEY: REG.PATH.CANON_BASE
- CLASS: PATH
- STATUS: ACTIVE
- SCOPE: repo structure
- OWNER: SYSTEM
- PRIORITY: P1
- RAW: N/A
- RULE: All system entity classes must live under `03_SYSTEM_ENTITIES/<CLASS_FOLDER>/...` with fixed class folder names.
- CHECK: Validate that each entity file path matches its class folder.
- FAIL: Entity file stored outside its canonical class folder.
- FIX: Move file to canonical location and update indexes/links; log change.
- NOTES: Only RAW links are used for navigation.
- LAST_CHANGE_ID: UE.CHG.2026-01-11.REG.TPL.RECORD.001

---

## FINAL RULE (LOCK)
This template is mandatory for REG registries.  
Any change must be logged in `90__REG_CHANGELOG.md`.

OWNER: SYSTEM  
LOCK: FIXED

--- END.
