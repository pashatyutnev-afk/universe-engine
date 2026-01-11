# REGISTRY — DEPRECATION (CANON)
FILE: 03_SYSTEM_ENTITIES/00_REG__REGISTRIES/91__REG_DEPRECATION.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: REGISTRIES (REG)
DOC_TYPE: REGISTRY
REGISTRY_TYPE: DEPRECATION
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.REG.DEPRECATION.001
OWNER: SYSTEM
ROLE: Canonical deprecation + pointer protocol for `03_SYSTEM_ENTITIES` (how to retire, rename, and alias without breaking RAW navigation)

CHANGE_NOTE:
- DATE: 2026-01-11
- TYPE: MAJOR
- SUMMARY: "Created deprecation registry: statuses, pointer rules, rename protocol, and enforcement."
- REASON: "Prevent broken RAW links and duplicate authorities."
- IMPACT: "Safe evolution with zero navigation breakage."
- CHANGE_ID: UE.CHG.2026-01-11.REG.DEPRECATION.001

---

## 0) PURPOSE (LAW)
This registry defines:
- how to deprecate canon files safely
- how to rename/move files without breaking navigation
- how to create POINTER aliases (pure pointer, no extra rules)
- strict enforcement rules (no duplicate authorities)

---

## 1) STATUS POLICY (STRICT)
Allowed status values for entities and registries:
- `STATUS: ACTIVE`
- `STATUS: DRAFT`
- `STATUS: DEPRECATED`
- `STATUS: ARCHIVED`

Rule:
- ACTIVE = authoritative and used
- DEPRECATED = not authoritative, but kept for compatibility (usually as pointer)
- ARCHIVED = frozen historical artifact; not used operationally
- DRAFT = not final; may change; still must follow structure rules

---

## 2) WHEN TO DEPRECATE
Deprecation is used when:
- file was renamed
- file was moved
- file is replaced by a new canonical file
- file is a duplicate entrypoint that must not exist as authority

If the old file is still needed for compatibility — it becomes a POINTER.

---

## 3) POINTER RULE (ABSOLUTE)
## REG.DEPRECATION.POINTER.PURE — pointer must be pure
- KEY: REG.DEPRECATION.POINTER.PURE
- CLASS: DEPRECATION
- STATUS: ACTIVE
- SCOPE: any deprecated/alias file
- OWNER: SYSTEM
- PRIORITY: P0
- RAW: N/A
- RULE: A POINTER file must contain **only**:
  - a clear pointer statement
  - the target RAW link
  - no additional rules, no extra content, no duplicated authority
- CHECK: Open pointer file; verify it contains only pointer block.
- FAIL: Pointer file contains extra rules/sections or acts as an authority.
- FIX: Remove all content except pointer block; log change.
- LAST_CHANGE_ID: UE.CHG.2026-01-11.REG.DEPRECATION.001

### Canon POINTER block (mandatory format)
Use exactly this minimal block:

POINTER TO CANON:
TARGET PATH: <canonical relative path>
TARGET RAW: <canonical RAW link>

END.

---

## 4) RENAME / MOVE PROTOCOL (MANDATORY)
## REG.DEPRECATION.RENAME_MOVE.PROTOCOL — safe rename/move
- KEY: REG.DEPRECATION.RENAME_MOVE.PROTOCOL
- CLASS: DEPRECATION
- STATUS: ACTIVE
- SCOPE: any indexed/canon file
- OWNER: SYSTEM
- PRIORITY: P0
- RAW: N/A
- RULE: Renaming/moving a canon file must follow the protocol below to avoid broken RAW navigation.
- CHECK: Validate all indexes and super-index RAW links after change.
- FAIL: Any RAW link in canon indexes returns 404 OR duplicates exist.
- FIX (Protocol):
  1) Create the new canonical file/path.
  2) Update all canon indexes and super-index to point to the new RAW link.
  3) Convert the old file into a PURE POINTER to the new canonical file.
  4) Update CHANGE_NOTE in new canonical file.
  5) Add a record into `90__REG_CHANGELOG.md`.
- LAST_CHANGE_ID: UE.CHG.2026-01-11.REG.DEPRECATION.001

---

## 5) DUPLICATE ENTRYPOINT RULE (ABSOLUTE)
## REG.DEPRECATION.NO_DUP_AUTHORITY — single source of truth
- KEY: REG.DEPRECATION.NO_DUP_AUTHORITY
- CLASS: DEPRECATION
- STATUS: ACTIVE
- SCOPE: all entity classes
- OWNER: SYSTEM
- PRIORITY: P0
- RAW: N/A
- RULE: There must not be two authoritative entrypoints for the same entity/index/law/realm.
- CHECK: Search for duplicates: `INDEX*`, `README*`, alternate filenames.
- FAIL: Two files both act as authority for same scope.
- FIX: Choose canonical file; convert others to pure POINTERs or delete; log change.
- LAST_CHANGE_ID: UE.CHG.2026-01-11.REG.DEPRECATION.001

---

## 6) DELETION POLICY (CONTROLLED)
Deletion is allowed only when:
- file is not referenced by any canon index AND
- file is not needed as compatibility pointer

If unsure → keep as POINTER with STATUS: DEPRECATED.

---

## 7) EXAMPLES

### Example A: rename template file
- Old: `00__TEMPLATE_REGISTRY.md`
- New: `00__TEMPLATE__REGISTRY.md`

Actions:
1) Rename/create new canonical file.
2) Update `00__INDEX_ALL_REGISTRIES.md` RAW link.
3) Convert old file into POINTER to new file.
4) Log in `90__REG_CHANGELOG.md`.

### Example B: duplicate index exists
- Found: `00__INDEX_REGISTRIES.md` (duplicate)
Action:
- Convert duplicate into POINTER to `00__INDEX_ALL_REGISTRIES.md` OR delete.
- Log.

---

## FINAL RULE (LOCK)
This deprecation registry is mandatory for safe evolution of canon files.  
Any rename/move/alias must follow this protocol and be logged in `90__REG_CHANGELOG.md`.

OWNER: SYSTEM
LOCK: FIXED

--- END.
