# SYSTEM LAW — CANON PROTOCOL (CANON)
FILE: 01_SYSTEM_LAW/04__CANON_PROTOCOL.md

SCOPE: Universe Engine
LAYER: 01_SYSTEM_LAW
DOC_TYPE: LAW
LAW_TYPE: CANON
LEVEL: L1
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.LAW.CANON_PROTOCOL.001
OWNER: SYSTEM
ROLE: Canon change workflow: proposal → approval → logging → application; enforces index authority for existence, RAW-only nav determinism, and prohibits silent changes

CHANGE_NOTE:
- DATE: 2026-01-09
- TYPE: MAJOR
- SUMMARY: "Established executable canon protocol: change workflow, index authority enforcement, logging requirements, and mandatory verification steps."
- REASON: "Canon must be deterministic and auditable; changes must not introduce drift or hidden authority."
- IMPACT: "All canon changes become reviewable, reproducible, and registry-consistent."
- CHANGE_ID: UE.CHG.2026-01-09.LAW.CANON_PROTOCOL.001

---

## 0) PURPOSE (LAW)
This law defines the only valid protocol for changing canon artifacts in Universe Engine.
It ensures:
- existence is defined by indexes (not by links or presence)
- navigation remains RAW-only and deterministic
- changes are auditable (no silent changes)
- duplicates are eliminated via SoT + pointer alias policy

---

## 1) DEFINITIONS (STRICT)
- CANON ARTIFACT: Any law, standard, canonical index, system entity registry/definition, KB governance+index, XREF map (and any artifact explicitly marked canon by higher authority).
- CANON CHANGE: Any modification that affects canon artifacts, canon structure, canon navigation, or canon existence.
- CHANGE PROPOSAL: A structured request to apply a canon change with scope, impact, and migration plan.
- APPROVAL: Explicit acceptance of a change proposal by the authority owner(s) for the impacted scope.
- GOVERNANCE RECORD: A required record that logs the change and its justification (audit/change control).
- INDEX AUTHORITY: The rule that indexes define existence and canonical navigation.
- POINTER (ALIAS): A redirect-only file used to preserve navigation after renames/moves and to eliminate duplicate entrypoints.
- BREAKING CHANGE: A change that can break navigation, contracts, or downstream consumers (as defined by versioning policy).

---

## 2) CANON CHANGE WORKFLOW (MANDATORY)
Any canon change MUST follow this workflow.

### 2.1 Change Proposal (REQUIRED INPUT)
A proposal must include, at minimum:
- SCOPE: exact files/paths affected
- TYPE: MAJOR/MINOR/PATCH (per versioning policy)
- SUMMARY: what changes
- REASON: why changes
- IMPACT: who/what breaks or improves
- MIGRATION: required steps (including pointer aliases if paths change)
- OWNERS: who must approve (by role/entity)
- CHANGE_ID: `UE.CHG.<YYYY-MM-DD>.<LAYER>.<DOC_OR_ENTITY>.<NNN>`

If any of the above is missing → proposal is INVALID.

### 2.2 Approval (AUTHORITY GATE)
- The highest authority owner for the impacted scope MUST approve.
- If multiple scopes are impacted, approvals must include all relevant owners.
- Conflicts are resolved strictly by ORDER OF AUTHORITY in `00__SYSTEM_LAW.md`.

Approval outcome must be explicit:
- APPROVED
- REJECTED
- APPROVED WITH CONDITIONS (conditions must be written)

### 2.3 Logging (AUDIT REQUIREMENT)
After approval and before/with applying the change:
- The changed file must contain an updated CHANGE_NOTE.
- A governance record must exist when required (see 2.3.1).

#### 2.3.1 When governance record is REQUIRED
Governance record is required for at least:
- any change to `01_SYSTEM_LAW/*`
- any change to `02_STANDARDS/*`
- any change to any canonical index (NAV/EXISTENCE)
- any breaking change (paths/contracts/schemas)
- any change that introduces/removes entities or families
- any change that modifies XREF maps used by pipelines

If uncertain → treat as REQUIRED.

### 2.4 Application (HOW THE CHANGE IS APPLIED)
When applying a canon change:
1) Apply the change to the target file(s).
2) Update affected canonical index entries (RAW-only links; existence registry).
3) Update XREF maps if the change affects pipelines, ownership, gates, or outputs.
4) If any canonical path/entrypoint changed:
   - create pointer aliases as required by versioning policy
5) Run verification steps (Section 5).
6) Mark any deprecated targets as DEPRECATED (do not silently delete unless policy allows).

---

## 3) INDEX AUTHORITY LAW (EXISTENCE) (ABSOLUTE)
3.1 Index defines existence
- If an entity/document is not listed in its canonical index — it does not exist for the system.
- Existence is not created by internal links, mentions, or folder presence.

3.2 RAW-only navigation is mandatory for canon maps
- Canon maps must use RAW links.
- PATH is human label only.

3.3 Index change = canon change
- Any change to a canonical index is a canon change and must follow this protocol.

---

## 4) NO SILENT CHANGES (ABSOLUTE)
4.1 Every canon change must include:
- updated CHANGE_NOTE in the changed file
- governance record when required

4.2 Silent changes are invalid
- They must be treated as violations until corrected.

---

## 5) VERIFICATION STEPS (MANDATORY)
These steps must be performed (at least mentally/locally) before declaring a canon change complete.

### 5.1 Determinism checks
- Canon index RAW links are valid.
- No duplicate SoT entrypoints introduced.
- Pointer aliases contain no rules and redirect only.

### 5.2 Consistency checks
- Naming rules not violated.
- UID rules not violated (UID stability on rename/move).
- Versioning policy applied correctly (MAJOR/MINOR/PATCH + required CHANGE_ID).

### 5.3 Scope safety checks
- Constraints registry not violated.
- Artifact schemas not silently changed without migration.

If any check fails → change is not complete.

---

## 6) POINTER / ALIAS POLICY (MANDATORY)
6.1 When pointer aliases are required
- Canon entrypoint renamed or moved
- Canon index renamed or moved
- Legacy duplicate entrypoint removed (replace with pointer)

6.2 Pointer content rule (ABSOLUTE)
- Pointer file contains only redirect to canonical target.
- No rules, no extra navigation, no extra existence claims.

---

## 7) BOUNDARIES (ANTI-OVERLAP)
- This law DOES: define canon change workflow, index authority, logging and verification.
- This law DOES NOT: define naming formats, UID format, versioning semantics, artifact schemas, or constraints content.
- CONFLICT RESOLUTION: resolved by ORDER OF AUTHORITY in `00__SYSTEM_LAW.md`.

---

## 8) ENFORCEMENT (MANDATORY)
### 8.1 MANDATORY CHECKS
- Any change to canon artifacts follows workflow (proposal→approval→logging→application).
- Any index change is treated as canon change.
- RAW-only nav preserved.
- Required pointer aliases created when paths/entrypoints change.

### 8.2 FAIL CONDITIONS
- Canon artifact modified without CHANGE_NOTE.
- Index modified without logging/approval pathway.
- Duplicate SoT introduced.
- Pointer alias contains extra content.
- Breaking change applied without migration plan.

### 8.3 FIX PROCEDURE
- Create missing CHANGE_NOTE + required governance record.
- Convert duplicates to pointers or delete non-canon duplicates.
- Restore RAW-only links in canonical indexes.
- Add migration steps and pointer aliases where missing.
- Reclassify version/change type if mis-stamped.

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
Canon changes are valid only when performed through this protocol.  
Any deviation is a violation until fixed.

OWNER: SYSTEM
LOCK: FIXED

--- END.
