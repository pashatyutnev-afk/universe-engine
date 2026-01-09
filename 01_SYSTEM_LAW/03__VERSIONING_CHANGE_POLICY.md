# SYSTEM LAW — VERSIONING & CHANGE POLICY (CANON)
FILE: 01_SYSTEM_LAW/03__VERSIONING_CHANGE_POLICY.md

SCOPE: Universe Engine
LAYER: 01_SYSTEM_LAW
DOC_TYPE: LAW
LAW_TYPE: VERSIONING
LEVEL: L1
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.LAW.VERSIONING.001
OWNER: SYSTEM
ROLE: Defines MAJOR/MINOR/PATCH semantics, required CHANGE_NOTE format, breaking change classification, migration requirements, and strict CHANGE_ID rules

CHANGE_NOTE:
- DATE: 2026-01-09
- TYPE: MAJOR
- SUMMARY: "Established executable versioning and change policy with strict change classification, mandatory change note fields, breaking change rules, migration and pointer alias requirements, and CHANGE_ID format + enum."
- REASON: "System needs deterministic change discipline to prevent drift, broken navigation, and non-auditable updates."
- IMPACT: "All canon artifacts become consistently stamped; migrations are mandatory for breaking structural changes."
- CHANGE_ID: UE.CHG.2026-01-09.LAW.VERSIONING.001

---

## 0) PURPOSE (LAW)
This law defines how versions and changes are classified and recorded across Universe Engine.
It ensures:
- changes are correctly labeled (MAJOR/MINOR/PATCH)
- breaking changes are never hidden as PATCH
- migrations and pointer aliases exist when needed
- CHANGE_NOTE is mandatory and consistent
- CHANGE_ID is deterministic and searchable

---

## 1) DEFINITIONS (STRICT)
- VERSION: A semantic label describing compatibility impact of a change.
- CHANGE TYPE: One of MAJOR, MINOR, PATCH.
- BREAKING CHANGE: Any change that can break navigation, contracts, schemas, or deterministic interpretation of canon.
- MIGRATION: A documented and enforced process to preserve compatibility after a breaking change.
- POINTER ALIAS: A redirect-only file preserving navigation after rename/move or SoT consolidation.
- CANON ARTIFACT: Any LAW, STANDARD, canonical INDEX, entity registry/definition, KB governance+index, XREF maps used by pipelines.
- CHANGE_NOTE: A required block describing the change and providing traceability.
- CHANGE_ID: A required unique identifier for a change event.

---

## 2) VERSIONING RULES (ABSOLUTE)
### 2.1 MAJOR (Breaking / Contract or Structure Change)
Use MAJOR when:
- canonical navigation structure changes (index structure, SoT entrypoints)
- canonical paths change in a way that can break references (move/rename of canon entrypoints)
- required fields in schemas/contracts change (artifact schema registry)
- authority/role boundaries change
- “existence rules” change
- any change that forces downstream updates or migrations

### 2.2 MINOR (Backward-Compatible Feature / Expansion)
Use MINOR when:
- new sections are added without breaking existing interpretation
- new entities/files are added in a way that does not break existing links/contracts
- new optional fields are added to schemas (optional only)
- new pipeline types are added without changing existing pipeline behavior

### 2.3 PATCH (Non-breaking Fix / Clarification)
Use PATCH when:
- typo fixes, wording clarifications without semantic change
- RAW link corrections (target unchanged)
- formatting/unification without changing meaning
- adding examples, improving readability, tightening wording without changing obligations

PATCH must never include any breaking change.

---

## 3) CHANGE_NOTE RULES (MANDATORY)
### 3.1 Required fields (ABSOLUTE)
Every canon change MUST include a CHANGE_NOTE with:
- DATE: YYYY-MM-DD
- TYPE: MAJOR|MINOR|PATCH
- SUMMARY: short statement of what changed
- REASON: why the change was needed
- IMPACT: what it affects (navigation/contracts/entities/pipelines)
- CHANGE_ID: as defined below (mandatory for MAJOR and for any canon-structure change; recommended for all)

### 3.2 Placement rules
- CHANGE_NOTE must appear near the top of the file (header section).
- A file must not contain multiple contradictory CHANGE_NOTE blocks for the same version.
- A file must not contain multiple `STATUS:` or multiple `LOCK:` fields.

---

## 4) CHANGE_ID RULES (ABSOLUTE)
### 4.1 CHANGE_ID format (ABSOLUTE)
`UE.CHG.<YYYY-MM-DD>.<LAYER>.<DOC_OR_ENTITY>.<NNN>`

Where:
- `YYYY-MM-DD` is the change date
- `LAYER` is a stable short token of the impacted layer/scope
- `DOC_OR_ENTITY` is a strict enum (see 4.2)
- `NNN` is a 3-digit sequence for that date+scope (001..999)

### 4.2 DOC_OR_ENTITY ENUM (STRICT)
Allowed values (initial canonical set):
- `LAW.CORE`
- `LAW.INDEX`
- `LAW.NAMING`
- `LAW.UID`
- `LAW.VERSIONING`
- `LAW.CANON_PROTOCOL`
- `LAW.ARTIFACT_SCHEMA`
- `LAW.CONSTRAINTS`
- `LAW.PIPELINE`

(Extension of this enum to STD/ENG/SPC/ORC/CTL/VAL/QA/XREF is allowed only via canon protocol change.)

### 4.3 LAYER tokens (recommended)
Recommended stable layer tokens:
- `LAW`
- `STD`
- `ENT`
- `KB`
- `PRJ`
- `AST`
- `OUT`
- `LOG`
- `XREF`

(Actual LAYER token used must reflect the primary scope impacted.)

---

## 5) BREAKING CHANGE CLASSIFICATION (MANDATORY)
A change is breaking if it includes ANY of:
- change to canonical index structure or SoT scope
- rename/move of canon entrypoints without pointer alias guarantee
- change to required fields in artifact schemas/contracts
- change to allowed enums (STATUS/LOCK/CHANGE types) that affects validity
- change to existence rules or authority order
- change that makes prior compliant documents become non-compliant without migration path

If uncertain → classify as BREAKING (MAJOR) and require migration.

---

## 6) MIGRATION RULES (MANDATORY)
### 6.1 When migration is required
Migration is required for any MAJOR change and for any breaking structural change.

### 6.2 Minimum migration content
A migration record must describe:
- What changed (from → to)
- What is preserved via pointer aliases
- What downstream documents must update
- How to validate completion (checks)

### 6.3 Pointer alias requirement (ABSOLUTE)
If a canon entrypoint is moved or renamed:
- a pointer alias MUST exist at the previous canonical location, redirecting to the new target,
- unless policy explicitly allows removal (rare; must be documented in migration).

Pointer aliases must contain no additional rules.

---

## 7) CHANGE APPLICATION RULES (MANDATORY)
When applying a canon change:
1) Update the changed file header (VERSION, CHANGE_NOTE, CHANGE_ID)
2) Update governing canonical index entries (RAW-only)
3) Update XREF maps if pipelines/ownership/gates change
4) Add pointer aliases if paths/entrypoints changed
5) Run enforcement checks (Section 8)

---

## 8) ENFORCEMENT (MANDATORY)
### 8.1 MANDATORY CHECKS
- Change TYPE matches actual change semantics (MAJOR/MINOR/PATCH).
- CHANGE_NOTE includes all required fields.
- CHANGE_ID matches format and enum.
- Breaking changes include migration and pointer alias plan.
- Canon indexes remain RAW-only navigable.

### 8.2 FAIL CONDITIONS
- Breaking change labeled as PATCH or MINOR.
- Missing CHANGE_ID where required (MAJOR or canon structure change).
- Invalid DOC_OR_ENTITY value.
- Canon entrypoint moved/renamed without pointer alias and migration note.
- Canon index updated without corresponding change trace.

### 8.3 FIX PROCEDURE
- Reclassify change type and bump version correctly.
- Add missing CHANGE_NOTE fields and assign valid CHANGE_ID.
- Add migration section/record and pointer aliases as required.
- Update canonical indexes and XREF maps to restore determinism.

---

## 9) INTERFACES (RAW ONLY)
- System Law index (SoT):  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/00__INDEX__SYSTEM_LAW.md
- Core constitution:  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/00__SYSTEM_LAW.md
- Canon protocol:  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/04__CANON_PROTOCOL.md
- Standards master index:  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/00__MASTER_INDEX__UNIVERSE_ENGINE.md

---

## FINAL RULE (LOCK)
Versioning and change discipline are mandatory for canon artifacts.  
Any misclassified change is invalid until corrected with proper version, change note, and migration steps.

OWNER: SYSTEM
LOCK: FIXED

--- END.
