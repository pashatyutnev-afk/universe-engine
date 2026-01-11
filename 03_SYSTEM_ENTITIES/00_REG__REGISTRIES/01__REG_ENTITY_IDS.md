# REGISTRY — ENTITY IDS (CANON)
FILE: 03_SYSTEM_ENTITIES/00_REG__REGISTRIES/01__REG_ENTITY_IDS.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: REGISTRIES (REG)
DOC_TYPE: REGISTRY
REGISTRY_TYPE: ENTITY_IDS
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.REG.IDS.001
OWNER: SYSTEM
ROLE: Canonical UID/ID namespaces + collision rules for all entity classes in 03_SYSTEM_ENTITIES

CHANGE_NOTE:
- DATE: 2026-01-11
- TYPE: MAJOR
- SUMMARY: "Created entity ID registry: UID namespace rules, uniqueness checks, and collision fix protocol."
- REASON: "Prevent ID drift and duplicated entities across classes."
- IMPACT: "IDs become deterministic and audit-friendly."
- CHANGE_ID: UE.CHG.2026-01-11.REG.IDS.001

---

## 0) PURPOSE (LAW)
This registry defines:
- canonical UID format rules for entities
- namespace separation between entity classes
- required uniqueness constraints
- collision detection and fix protocol

If an entity violates this registry — it is NON-CANON until fixed.

---

## 1) DEFINITIONS
- **UID**: Unique identifier for a document/entity (stable).
- **CHANGE_ID**: Identifier for a specific change event (versioned).
- **ENTITY CLASS**: One of ENG/ORC/SPC/CTL/VAL/QA/XREF/REG/TPL.

---

## 2) CORE RULES (ABSOLUTE)

## REG.ID.UID.REQUIRED — UID is mandatory
- KEY: REG.ID.UID.REQUIRED
- CLASS: ID
- STATUS: ACTIVE
- SCOPE: all entity files in `03_SYSTEM_ENTITIES/*`
- OWNER: SYSTEM
- PRIORITY: P0
- RAW: N/A
- RULE: Every entity file must contain exactly one `UID:` field in its header.
- CHECK: Open file header; ensure one and only one UID field.
- FAIL: UID missing OR multiple UID fields.
- FIX: Add/normalize to a single UID; remove duplicates; log change.
- LAST_CHANGE_ID: UE.CHG.2026-01-11.REG.IDS.001

## REG.ID.UID.UNIQUE — UID must be globally unique
- KEY: REG.ID.UID.UNIQUE
- CLASS: ID
- STATUS: ACTIVE
- SCOPE: all entity classes
- OWNER: SYSTEM
- PRIORITY: P0
- RAW: N/A
- RULE: UID must be unique across the whole repository scope (no duplicates anywhere).
- CHECK: Search repo for the UID string; must have exactly one match.
- FAIL: UID appears in 2+ files.
- FIX: Choose canonical owner file; re-issue new UID(s) for the others; update indexes and crossrefs; log change.
- LAST_CHANGE_ID: UE.CHG.2026-01-11.REG.IDS.001

## REG.ID.UID.STABLE — UID is stable across versions
- KEY: REG.ID.UID.STABLE
- CLASS: ID
- STATUS: ACTIVE
- SCOPE: all entity files
- OWNER: SYSTEM
- PRIORITY: P1
- RAW: N/A
- RULE: UID must not change when content changes (UID is identity). Only CHANGE_ID changes per update.
- CHECK: Review changelog; ensure UID unchanged across versions.
- FAIL: UID changed without explicit deprecation/migration protocol.
- FIX: Restore original UID; if truly new entity, create a new file and deprecate old via pointer; log change.
- LAST_CHANGE_ID: UE.CHG.2026-01-11.REG.IDS.001

---

## 3) UID FORMAT (STANDARD)
### 3.1 Canon structure (recommended)
`UE.<CLASS>.<DOC_TYPE>.<SCOPE>.<NNN>`

Examples:
- `UE.ENG.IDX.ALL.001`
- `UE.SPC.IDX.ALL.001`
- `UE.CTL.MUSIC.DURATION.001`
- `UE.VAL.MUSIC.UGC.002`
- `UE.QA.MUSIC.LOOP.003`

### 3.2 Allowed CLASS tokens (strict)
- `ENG` (Engines)
- `ORC` (Orchestrators)
- `SPC` (Specialists)
- `CTL` (Controllers)
- `VAL` (Validators)
- `QA`  (Quality)
- `XREF` (Crossref maps)
- `REG` (Registries)
- `TPL` (Templates)

### 3.3 Numbering
- Use `001`, `002`, … as stable sequence within the UID family.
- Do not reuse numbers once issued.

---

## 4) CHANGE_ID FORMAT (STANDARD)
## REG.ID.CHANGE_ID.REQUIRED — change id is mandatory on edits
- KEY: REG.ID.CHANGE_ID.REQUIRED
- CLASS: ID
- STATUS: ACTIVE
- SCOPE: any doc update that changes content/structure/links
- OWNER: SYSTEM
- PRIORITY: P0
- RAW: N/A
- RULE: Any update must include a new `CHANGE_ID` inside CHANGE_NOTE.
- CHECK: Verify CHANGE_NOTE includes CHANGE_ID and date.
- FAIL: No CHANGE_ID on updated doc.
- FIX: Add CHANGE_NOTE entry with new CHANGE_ID; log in relevant changelog if required.
- LAST_CHANGE_ID: UE.CHG.2026-01-11.REG.IDS.001

Recommended format:
`UE.CHG.YYYY-MM-DD.<AREA>.<DOC>.NNN`

Examples:
- `UE.CHG.2026-01-11.REG.IDS.001`
- `UE.CHG.2026-01-09.SPC.IDX.ALL.002`
- `UE.CHG.2026-01-11.ENT.IDX.ALL.001`

---

## 5) COLLISION PROTOCOL (MANDATORY)

## REG.ID.COLLISION.PROTOCOL — how to resolve UID collisions
- KEY: REG.ID.COLLISION.PROTOCOL
- CLASS: ID
- STATUS: ACTIVE
- SCOPE: global
- OWNER: SYSTEM
- PRIORITY: P0
- RAW: N/A
- RULE: UID collision is a P0 incident and must be resolved immediately using this protocol.
- CHECK: Search results show duplicated UID.
- FAIL: Collision exists and is not resolved.
- FIX:
  1) Identify canonical file (the intended owner of that UID).
  2) For every other file using that UID: issue new UID(s).
  3) Update any indexes and XREF maps that point to the changed file(s).
  4) Add CHANGE_NOTE entries for affected files.
  5) Append a record to `90__REG_CHANGELOG.md`.
- LAST_CHANGE_ID: UE.CHG.2026-01-11.REG.IDS.001

---

## 6) OPTIONAL: HUMAN LABEL IDS
- Titles/names can change, UID cannot.
- Do not encode volatile info (year, version, random words) into UID.

---

## FINAL RULE (LOCK)
This registry is authoritative for UID / CHANGE_ID behavior inside `03_SYSTEM_ENTITIES`.  
Any deviation is NON-CANON until fixed.

OWNER: SYSTEM
LOCK: FIXED

--- END.
