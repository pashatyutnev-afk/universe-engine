# SYSTEM LAW — UID RULES (CANON)
FILE: 01_SYSTEM_LAW/02__UID_RULES.md

SCOPE: Universe Engine
LAYER: 01_SYSTEM_LAW
DOC_TYPE: LAW
LAW_TYPE: UID
LEVEL: L1
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.LAW.UID.001
OWNER: SYSTEM
ROLE: Defines UID format, issuance, scope mapping, stability on rename/move, replacement vs update rules, and absolute uniqueness constraints across Universe Engine

CHANGE_NOTE:
- DATE: 2026-01-09
- TYPE: MAJOR
- SUMMARY: "Established executable UID rules: format, issuance, scope mapping, stability guarantees, replacement vs update semantics, and uniqueness enforcement."
- REASON: "System requires deterministic identity independent of filenames/paths to prevent drift, collisions, and non-auditable entity replacement."
- IMPACT: "All canon documents/entities gain stable identity; renames/moves become safe via stable UID + pointer migrations when needed."
- CHANGE_ID: UE.CHG.2026-01-09.LAW.UID.001

---

## 0) PURPOSE (LAW)
This law defines UID as the stable identity of documents and entities.
It ensures:
- identity is stable across rename/move
- uniqueness is enforced
- replacement of identity is explicit (never silent)
- scope-specific UID families are deterministic

---

## 1) DEFINITIONS (STRICT)
- UID: A stable identifier representing the identity of a governed document/entity.
- IDENTITY: The “same thing” across time; an identity persists through edits, formatting, and path changes.
- UPDATE: A change that keeps the same identity (UID stays the same).
- REPLACEMENT: A change that creates a new identity (new UID), while old identity may be deprecated/archived.
- COLLISION: Two different identities sharing the same UID (forbidden).
- SCOPE: The classification of what the UID is identifying (LAW, STANDARD, INDEX, README, ENTITY, TEMPLATE, REGISTRY, etc.).

---

## 2) UID FORMAT (MANDATORY)
### 2.1 Canon format rule
- UID MUST be present in the header of governed canon artifacts (as required by standards/protocol).
- UID MUST be stable and unique.

### 2.2 UID string pattern (system-level)
Universe Engine allows the following canonical UID families:
- `UE.<LAYER>.<CLASS>.<NAME>.<NNN>`  (recommended for new entities)
- `UE.<CLASS>.<SUBCLASS>.<NAME>.<NNN>` (legacy-compatible if already used)

Where:
- `LAYER` is a stable token (LAW/STD/ENG/SPC/ORC/CTL/VAL/QA/KB/PRJ/XREF/REG/AST/OUT/LOG)
- `CLASS` is the entity/document class (LAW/IDX/README/ENT/TPL/REG/…)
- `NAME` is stable semantic name (UPPER_SNAKE or DOT tokens)
- `NNN` is 3-digit sequence within that UID family

If a subsystem already uses a stricter UID scheme, it is valid as long as:
- uniqueness is preserved
- stability rules in this law are obeyed
- the scheme is documented in its standards/ruleset

---

## 3) UID ISSUANCE RULES (MANDATORY)
### 3.1 When UID is required
UID is mandatory for:
- all LAW files (01_SYSTEM_LAW/*)
- all STANDARDS files (02_STANDARDS/*)
- all canonical layer indexes (SoT NAV/EXISTENCE)
- all SYSTEM ENTITIES definitions (ENG/SPC/ORC/CTL/VAL/QA)
- KB governance + KB master index
- XREF maps used by pipelines (when stamped as canon)

If a file is canon and has no UID → it is INCOMPLETE until fixed.

### 3.2 Who assigns UID
- OWNER: SYSTEM is the authority for UID rule compliance.
- Assignment may be executed by designated governance roles (Doc Controller / Standards Owner / etc.) but must comply with this law.

### 3.3 How to issue a new UID (procedure)
To issue a new UID:
1) Determine the scope (LAW/STD/ENTITY/INDEX/README/etc.)
2) Choose the appropriate UID family prefix
3) Select the next available NNN in that family
4) Stamp UID in header
5) Register/validate in relevant registry (if one exists)
6) Log change if it is canon (change note + canon protocol if needed)

---

## 4) UID STABILITY (ABSOLUTE)
### 4.1 Stability on rename/move (ABSOLUTE)
- UID MUST NOT change when:
  - file is renamed
  - file is moved to a new path
  - formatting changes
  - content changes that do not replace identity

Rename/move safety:
- identity remains stable by UID,
- navigation remains stable by pointer aliases (if entrypoints move), per versioning policy.

### 4.2 Stability across versions
- UID remains stable across PATCH/MINOR/MAJOR updates as long as the identity is the same.
- Version changes do not imply UID changes.

---

## 5) REPLACEMENT VS UPDATE (MANDATORY)
### 5.1 Update (same identity)
An UPDATE is:
- additional rules inside the same law
- clarifications, expansions, fixes
- reorganizing sections without changing identity
- adding new examples
Result: UID stays the same.

### 5.2 Replacement (new identity)
A REPLACEMENT is:
- the original artifact is deprecated and replaced by a new artifact with a different identity
- the semantic meaning changes so strongly that old references must not be treated as the same object
- a split/merge where identity cannot be preserved safely

Result:
- NEW UID is issued for the new artifact/entity
- old UID remains as identity of the old object (typically STATUS: DEPRECATED/ARCHIVED)
- migration notes and pointer policies apply if navigation changes

Replacement must be explicit in CHANGE_NOTE and canon protocol record (when required).

---

## 6) UID SCOPE RULES (MANDATORY MAPPING)
This section defines how UID should be classified per artifact type.

### 6.1 UID for INDEX (registry SoT)
- Must use `CLASS: IDX` (recommended) or a stable equivalent.
- Index UID represents the registry identity, not the content list.

### 6.2 UID for README (realm files)
- Must use `CLASS: README` (recommended).
- README UID represents realm identity and scope framing.

### 6.3 UID for ENTITY (ENG/SPC/ORC/CTL/VAL/QA)
- Must use `CLASS: ENT` (recommended) plus entity group token (ENG/SPC/…).
- Entity UID represents the role/object identity.

### 6.4 UID for TEMPLATE
- Must use `CLASS: TPL` (recommended).
- Template UID represents the template identity independent of copies.

### 6.5 UID for REGISTRY documents
- Must use `CLASS: REG` (recommended).
- Registry UID represents the register identity.

This mapping is a standardization guideline; the absolute requirement is uniqueness + stability.

---

## 7) UNIQUENESS (ABSOLUTE)
### 7.1 Global uniqueness rule
- UID must be globally unique across the entire Universe Engine repository.

### 7.2 Collision handling (procedure)
If a collision is found:
1) Treat as FAIL immediately.
2) Determine which artifact owns the UID legitimately (first canonical assignment or authoritative registry).
3) Reissue a new UID for the conflicting artifact (the one that should not have it).
4) Update all references/registries affected.
5) Log the fix (change note + governance record if required).

Collisions must never be “ignored”.

---

## 8) ENFORCEMENT (MANDATORY)
### 8.1 MANDATORY CHECKS
- UID exists on required canon artifacts.
- UID format matches allowed scheme (Section 2).
- UID is stable across rename/move.
- UID is unique globally.
- Replacement vs update is correctly applied (new UID only on replacement).

### 8.2 FAIL CONDITIONS
- Missing UID where required.
- Duplicate UID across different identities.
- UID changed due to rename/move (violation).
- New UID issued without explicit replacement reasoning and required logs.

### 8.3 FIX PROCEDURE
- Add missing UID using issuance procedure.
- Resolve collisions via reissue + reference updates.
- Revert inappropriate UID changes (restore original UID) and apply pointer migration if navigation changed.
- If replacement is intended: issue new UID, mark old artifact deprecated, add migration notes, log via canon protocol.

---

## 9) INTERFACES (RAW ONLY)
- System Law index (SoT):  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/00__INDEX__SYSTEM_LAW.md
- Core constitution:  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/00__SYSTEM_LAW.md
- Versioning & Change Policy:  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/03__VERSIONING_CHANGE_POLICY.md
- Standards master index:  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/00__MASTER_INDEX__UNIVERSE_ENGINE.md

---

## FINAL RULE (LOCK)
UID is the stable identity of canon artifacts and entities.  
Any UID collision or unstable UID behavior is a system violation until corrected.

OWNER: SYSTEM
LOCK: FIXED

--- END.
