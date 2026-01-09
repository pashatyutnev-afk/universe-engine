# SYSTEM LAW — CORE CONSTITUTION (CANON)
FILE: 01_SYSTEM_LAW/00__SYSTEM_LAW.md

SCOPE: Universe Engine
LAYER: 01_SYSTEM_LAW
DOC_TYPE: LAW
LAW_TYPE: CORE
LEVEL: L1
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.LAW.CORE.CONSTITUTION.001
OWNER: SYSTEM
ROLE: Supreme law defining authority order, existence rules, RAW-only navigation, anti-duplication, lock semantics, and audit discipline for the entire Universe Engine

CHANGE_NOTE:
- DATE: 2026-01-09
- TYPE: MAJOR
- SUMMARY: "Established executable constitution: authority order, global existence rule, RAW-only navigation law, anti-duplication SoT enforcement, lock semantics, and audit discipline."
- REASON: "System requires deterministic governance to prevent drift, duplicates, and non-auditable canon changes."
- IMPACT: "All layers become audit-compatible and deterministic; canon changes are routed through canon protocol."
- CHANGE_ID: UE.CHG.2026-01-09.LAW.CORE.001

---

## 0) PURPOSE (LAW)
This law is the supreme constitution of Universe Engine.
It defines:
- ORDER OF AUTHORITY (conflict resolution)
- GLOBAL EXISTENCE RULE (what “exists”)
- NAVIGATION LAW (RAW-only determinism)
- ANTI-DUPLICATION LAW (single sources of truth)
- LOCK SEMANTICS (what FIXED actually means)
- NO SILENT CHANGES (audit discipline)
- ROLE BOUNDARIES (who may change what)

---

## 1) DEFINITIONS (STRICT)
- CANON: The authoritative truth of the system governed by ORDER OF AUTHORITY.
- SINGLE SOURCE OF TRUTH (SoT): The only authoritative document for a scope. All duplicates are non-canon or pointer aliases.
- EXISTENCE: A file/entity exists only if registered in the canonical index governing its scope.
- CANON INDEX: An index that defines NAV/EXISTENCE for a scope.
- POINTER (ALIAS): A file that contains only a redirect to the canonical target and adds no rules.
- RAW-ONLY NAVIGATION: Canon navigation must use RAW links; PATH is a human label only.
- SILENT CHANGE: A change made without required CHANGE_NOTE and required governance record (when applicable).
- LAYER: A governed folder scope (LAW, STANDARDS, SYSTEM_ENTITIES, KB, PROJECTS, etc.).
- ENTITY: A governed object (ENG, SPC, ORC, CTL, VAL, QA, REGISTRY, TEMPLATE, INDEX).
- PIPELINE: A deterministic ORC-driven execution sequence producing artifacts under required gates.
- GOVERNANCE RECORD: A required record of change routed through canon protocol/audit log/change control (where required).

---

## 2) ORDER OF AUTHORITY (ABSOLUTE)
If two statements conflict, the higher authority wins.

Authority order:
1) `01_SYSTEM_LAW/00__SYSTEM_LAW.md` (this file)
2) `01_SYSTEM_LAW/04__CANON_PROTOCOL.md`
3) `01_SYSTEM_LAW/03__VERSIONING_CHANGE_POLICY.md`
4) `01_SYSTEM_LAW/02__UID_RULES.md`
5) `01_SYSTEM_LAW/01__NAMING_RULES.md`
6) `01_SYSTEM_LAW/06__CONSTRAINTS_REGISTRY.md`
7) `01_SYSTEM_LAW/05__ARTIFACT_SCHEMA_REGISTRY.md`
8) `01_SYSTEM_LAW/07__PIPELINE_REGISTRY.md`
9) `02_STANDARDS/*`
10) Canon layer indexes (SoT for NAV/EXISTENCE inside their layers)
11) System entities definitions (ENG/SPC/ORC/CTL/VAL/QA/REG/XREF)
12) Knowledge Base content
13) Projects content and outputs

If multiple documents claim to be SoT for the same scope → ANTI-DUPLICATION VIOLATION.

---

## 3) GLOBAL EXISTENCE RULE (ABSOLUTE)
3.1 Existence is created only by canonical indexes.
- If a file/entity is not registered in its governing canonical index — it does not exist for the system.
- If a file exists in the repository but is not registered — it is NON-CANON / ignored.

3.2 Existence cannot be created by:
- links inside content documents
- folder presence alone
- references from non-index documents
- “common knowledge” or external assumptions

---

## 4) NAVIGATION LAW (RAW-ONLY)
4.1 Canon navigation must use RAW links.
- All canonical indexes must provide RAW links for entries.
- PATH is optional and never used as navigation.

4.2 Broken RAW navigation is a system failure.
- Any missing/invalid RAW link in a canonical index is FAIL.
- Fix requires restoring the canonical target or updating canonical RAW link.

---

## 5) ANTI-DUPLICATION LAW (SoT ENFORCEMENT)
5.1 One scope → one SoT.
- Every governed scope must have exactly one SoT index/entrypoint.
- Any additional entrypoint-like file must be either:
  - removed, OR
  - converted into a POINTER to the SoT

5.2 Pointer alias rule (ABSOLUTE)
- A pointer contains no rules, no extra navigation, no extra existence claims.
- Pointer exists only to redirect to canonical file.

5.3 One-index mode (ABSOLUTE where declared)
- If a layer declares one-index mode, sub-indexes are forbidden unless explicitly allowed by law/standard.

---

## 6) LOCK SEMANTICS (MANDATORY)
- `LOCK: FIXED` means:
  - changes are allowed only via canon protocol + required logs
  - “ad-hoc edits” are forbidden
- `LOCK: OPEN` means:
  - changes are allowed without extra restriction,
  - but still must comply with higher laws/standards and must not create silent changes for canon artifacts.

LOCK does not replace versioning. LOCK defines the allowed pathway.

---

## 7) NO SILENT CHANGES (AUDIT DISCIPLINE)
7.1 Any change to canon artifacts must include:
- CHANGE_NOTE in the modified file (mandatory)
- governance record when required by canon protocol (mandatory)

7.2 Canon artifacts include (minimum):
- System laws (01_SYSTEM_LAW)
- Standards (02_STANDARDS)
- Canon indexes of any layer
- System entities indexes and definitions (ENG/SPC/ORC/CTL/VAL/QA/XREF/REG)
- KB governance + KB master index

7.3 Changes without required records are invalid.
- They must be treated as violations until corrected via canon protocol.

---

## 8) ROLE BOUNDARIES (WHO MAY CHANGE WHAT)
- System laws: change only through canon protocol under SYSTEM ownership.
- Standards: change through standards workflow under canon protocol.
- Indexes: must preserve RAW-only nav, existence rules, and must be logged.
- Entities: must preserve naming/UID rules and required contracts.
- KB content: may evolve, but cannot claim canon authority or create existence.

No role may expand authority by editing higher-level documents without protocol.

---

## 9) SYSTEM CUBE PRINCIPLE (HIGH-LEVEL)
Universe Engine operates as a cube of governed roles:
- ENG: transformation engines (contracts, steps, dependencies)
- SPC: specialist owners (domain decisions, boundaries, output packs)
- ORC: orchestrators (pipelines: task→steps→gates→output)
- VAL: validators (consistency, plausibility, factual integrity)
- QA: quality gates (naturalness, readability, production quality)
- CTL: controllers (readiness/blockers/enforcement)
- REG: registries (IDs/paths/changelog/deprecation)
- XREF: cross-layer maps (deterministic stitching of the cube)
- KB: knowledge base (methods/terminology; not canon truth)

Execution spine is ORC:
TASK → ORC → ENG steps (with SPC owners) → VAL/QA/CTL gates → Output.

---

## 10) ENFORCEMENT (MANDATORY)
### 10.1 MANDATORY CHECKS
- Canon indexes are RAW-only navigable.
- Each scope has exactly one SoT.
- Any canon change includes CHANGE_NOTE.
- LOCK: FIXED changes follow canon protocol pathway.
- Unregistered files are never treated as existing canon.

### 10.2 FAIL CONDITIONS
- Broken RAW links inside canonical indexes.
- Duplicate entrypoints for the same scope.
- Silent changes to canon artifacts (missing change note and/or missing required governance record).
- Treating non-registered files as existing canon.

### 10.3 FIX PROCEDURE
- Duplicate SoT: delete duplicates or convert to pure POINTER; keep only canonical SoT.
- Broken RAW links: restore target or update canonical index entry.
- Silent change: add required CHANGE_NOTE and create required governance record per canon protocol.
- Unregistered authority: register properly via protocol (if approved) or mark/remove as NON-CANON usage.

---

## 11) INTERFACES (RAW ONLY)
- System Law index (SoT for LAW existence):  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/00__INDEX__SYSTEM_LAW.md
- Canon Protocol:  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/04__CANON_PROTOCOL.md
- Versioning & Change Policy:  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/03__VERSIONING_CHANGE_POLICY.md
- Standards master index:  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/00__MASTER_INDEX__UNIVERSE_ENGINE.md
- System Entities master index:  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/02__INDEX__SYSTEM_ENTITIES.md

---

## FINAL RULE (LOCK)
This constitution is the highest authority of Universe Engine.  
Any deviation is a violation until corrected via canon protocol.

OWNER: SYSTEM
LOCK: FIXED

--- END.
