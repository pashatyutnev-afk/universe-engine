# SYSTEM LAW — CORE CONSTITUTION (CANON)

FILE: 01_SYSTEM_LAW/00__SYSTEM_LAW.md
SCOPE: Universe Engine (All volumes)
LAYER: 01_SYSTEM_LAW
DOC_TYPE: LAW
LAW_TYPE: CORE
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.1
UID: UE.LAW.CORE.CONSTITUTION.001
OWNER: SYSTEM
ROLE: Supreme constitution defining authority order, existence rules, RAW-only navigation, snapshot link-base runtime, anti-duplication, lock semantics, audit discipline, and output-as-artifact law for the entire Universe Engine.

CHANGE_NOTE:
- DATE: 2026-01-19
- TYPE: PATCH
- SUMMARY: "Aligned constitution with runtime snapshot link-base + single task entrypoint + output-as-artifact + boot-first discipline."
- REASON: "Runtime must be deterministic and auditable: navigation restricted to ROOT snapshot; tasks must enter via START; outputs must be artifact-docs."
- IMPACT: "System becomes strict about entrypoint routing, link refresh, and artifact packaging; reduces drift and hidden navigation."
- CHANGE_ID: UE.CHG.2026-01-19.LAW.CORE.002

---

## 0) PURPOSE (LAW)
This law is the supreme constitution of Universe Engine.

It defines:
- ORDER OF AUTHORITY (conflict resolution)
- GLOBAL EXISTENCE RULE (what “exists”)
- NAVIGATION LAW (RAW-only determinism + snapshot runtime)
- SINGLE ENTRYPOINT LAW (how tasks may start)
- BOOT-FIRST DISCIPLINE (no execution before core loading)
- OUTPUT-AS-ARTIFACT LAW (no “naked content”)
- ANTI-DUPLICATION LAW (single sources of truth)
- LOCK SEMANTICS (what FIXED actually means)
- NO SILENT CHANGES (audit discipline)
- ROLE BOUNDARIES (who may change what)

---

## 1) DEFINITIONS (STRICT)
- CANON: The authoritative truth of the system governed by ORDER OF AUTHORITY.
- SINGLE SOURCE OF TRUTH (SoT): The only authoritative document for a scope. Duplicates are non-canon or pointer aliases.
- EXISTENCE: A file/entity exists for the system only if registered in the canonical index governing its scope.
- CANON INDEX: An index that defines NAV/EXISTENCE for a scope.
- POINTER (ALIAS): A file that contains only a redirect to the canonical target and adds no rules.
- RAW-ONLY NAVIGATION: Canon navigation must use RAW links; PATH is a human label only.
- LINK BASE SNAPSHOT: A user-provided ROOT index that contains a fixed set of RAW links used by runtime.
- MANUAL REFRESH: The only allowed way to update the LINK BASE SNAPSHOT (user replaces/sends updated ROOT index).
- ENTRYPOINT (RUNTIME): The only allowed start document/command for tasks (`START_UNIVERSE_ENGINE`).
- BOOT SEQUENCE: Mandatory reading of core laws/standards before any task execution (defined by entrypoint runbook).
- ARTIFACT DOCUMENT: Any output packaged as a governed doc using templates + doc control + UID/versioning rules.
- SILENT CHANGE: A change made without required CHANGE_NOTE and required governance record (when applicable).

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
9) `START_UNIVERSE_ENGINE` runtime entrypoint (runbook) — governs execution order, not canon authority over laws
10) `02_STANDARDS/*`
11) Canon layer indexes (SoT for NAV/EXISTENCE inside their layers)
12) System entities definitions (ENG/SPC/ORC/CTL/VAL/QA/REG/XREF)
13) Knowledge Base content
14) Projects content and outputs

If multiple documents claim to be SoT for the same scope → ANTI-DUPLICATION VIOLATION.

---

## 3) GLOBAL EXISTENCE RULE (ABSOLUTE)
### 3.1 Existence is created only by canonical indexes
- If a file/entity is not registered in its governing canonical index — it does not exist for the system.
- If a file exists in the repository but is not registered — it is NON-CANON / ignored.

### 3.2 Existence cannot be created by
- links inside content documents
- folder presence alone
- references from non-index documents
- “common knowledge” or external assumptions

### 3.3 ROOT link-base snapshot does NOT create existence
- The ROOT LINK BASE is a navigation snapshot for runtime convenience.
- It does not grant canon existence by itself.
- Existence remains governed by each layer’s canonical index.

---

## 4) NAVIGATION LAW (RAW-ONLY + SNAPSHOT RUNTIME)
### 4.1 Canon navigation must use RAW links
- Canon indexes should provide RAW links for entries.
- PATH is optional and never used as navigation.

### 4.2 Runtime navigation is restricted to the snapshot (ABSOLUTE)
During any task run, the system may use RAW links only if they are:
- present in the user-provided ROOT LINK BASE snapshot, OR
- explicitly provided by the user in the chat as RAW links.

No guessing of paths/URLs outside the snapshot.

### 4.3 Broken RAW navigation is a system failure
- Any missing/invalid RAW link used for canon navigation is FAIL.
- Fix requires restoring the canonical target or updating the canonical RAW link (via canon protocol).

---

## 5) LINK BASE SNAPSHOT & MANUAL REFRESH (ABSOLUTE)
- The ROOT LINK BASE is a snapshot.
- The snapshot is not auto-updated.
- The only way to refresh is manual user replacement / user-sent updated ROOT index (or explicit extra RAW links).

Until user refreshes:
- the link set is treated as fixed,
- the system must not assume newer files/paths exist.

---

## 6) SINGLE ENTRYPOINT LAW (TASK ENTRY)
### 6.1 Entry command
Any task must be started via the runtime entrypoint command:
- `START_UNIVERSE_ENGINE`

### 6.2 ROOT index is not a task runner
- ROOT-INDEX is a link-base snapshot only.
- It must not be treated as a runbook or executor.

---

## 7) BOOT-FIRST DISCIPLINE (ABSOLUTE)
- No task execution is allowed before boot completion markers are confirmed by the entrypoint runbook.
- If any required boot marker is not confirmed → STOP (marker not confirmed).

---

## 8) OUTPUT-AS-ARTIFACT LAW (ABSOLUTE)
### 8.1 No “naked content”
Any outgoing result (content/decision/plan/track/cover/scene/entity passport) must be packaged as an artifact document.

### 8.2 Template + doc control required
Artifact documents must comply with:
- DOC CONTROL (structure, required headers/fields)
- UID rules
- versioning/change policy
- relevant templates for the domain

### 8.3 Missing entity/template duty
If a required artifact template, entity role, or route component is missing:
- declare GAP (what is missing and why it’s required),
- propose creation,
- provide the full entity/template file per the relevant TEMPLATE standard,
- only then resume the original task.

---

## 9) ANTI-DUPLICATION LAW (SoT ENFORCEMENT)
### 9.1 One scope → one SoT
- Every governed scope must have exactly one SoT index/entrypoint.
- Any additional entrypoint-like file must be either:
  - removed, OR
  - converted into a POINTER to the SoT

### 9.2 Pointer alias rule (ABSOLUTE)
- A pointer contains no rules, no extra navigation, no extra existence claims.
- Pointer exists only to redirect to canonical file.

---

## 10) LOCK SEMANTICS (MANDATORY)
- `LOCK: FIXED` means:
  - changes are allowed only via canon protocol + required logs
  - ad-hoc edits are forbidden
- `LOCK: OPEN` means:
  - changes are allowed without extra restriction,
  - but still must comply with higher laws/standards and must not create silent changes for canon artifacts.

LOCK does not replace versioning. LOCK defines the allowed pathway.

---

## 11) NO SILENT CHANGES (AUDIT DISCIPLINE)
### 11.1 Required minimum for canon changes
Any change to canon artifacts must include:
- CHANGE_NOTE in the modified file (mandatory)
- governance record when required by canon protocol (mandatory)

### 11.2 Canon artifacts include (minimum)
- System laws (01_SYSTEM_LAW)
- Standards (02_STANDARDS)
- Canon indexes of any layer
- System entities indexes and definitions (ENG/SPC/ORC/CTL/VAL/QA/XREF/REG)
- KB governance + KB master index

### 11.3 Silent changes are invalid
- They must be treated as violations until corrected via canon protocol.

---

## 12) ROLE BOUNDARIES (WHO MAY CHANGE WHAT)
- System laws: change only through canon protocol under SYSTEM ownership.
- Standards: change through standards workflow under canon protocol.
- Indexes: must preserve RAW-only nav and existence rules and must be logged.
- Entities: must preserve naming/UID rules and required contracts.
- KB content: may evolve, but cannot claim canon authority or create existence.

No role may expand authority by editing higher-level documents without protocol.

---

## 13) SYSTEM CUBE PRINCIPLE (HIGH-LEVEL)
Universe Engine operates as a cube of governed roles:
- ENG: transformation engines (contracts, steps, dependencies)
- SPC: specialist owners (domain decisions, boundaries, output packs)
- ORC: orchestrators (pipelines: task→steps→gates→output)
- VAL: validators (consistency, plausibility, integrity)
- QA: quality gates (acceptance, exemplars, regression)
- CTL: controllers (readiness/blockers/enforcement)
- REG: registries (IDs/paths/changelog/deprecation)
- XREF: cross-layer maps (deterministic stitching)
- KB: knowledge base (methods/terminology; not canon truth)

Execution spine is ORC:
TASK → ORC → ENG steps (with SPC owners) → CTL/VAL/QA gates → Artifact outputs.

---

## 14) ENFORCEMENT (MANDATORY)
### 14.1 Mandatory checks
- Canon navigation is RAW-only.
- Runtime navigation uses only the ROOT snapshot + user-provided RAW links.
- Each scope has exactly one SoT.
- Any canon change includes CHANGE_NOTE.
- LOCK: FIXED changes follow canon protocol pathway.
- Unregistered files are never treated as existing canon.
- No task runs before boot markers are confirmed.
- No naked content outputs: artifacts only.

### 14.2 Fail conditions
- Broken RAW links used for canon navigation.
- Duplicate SoT for the same scope.
- Silent changes to canon artifacts (missing change note and/or missing required governance record).
- Treating non-registered files as existing canon.
- Running tasks without `START_UNIVERSE_ENGINE`.
- Executing without boot completion markers.

### 14.3 Fix procedure
- Duplicate SoT: delete duplicates or convert to pure POINTER; keep only canonical SoT.
- Broken RAW links: restore target or update canonical index entry.
- Silent change: add required CHANGE_NOTE and create required governance record per canon protocol.
- Unregistered authority: register properly via protocol (if approved) or mark/remove as NON-CANON usage.
- Missing template/entity: GAP → create via templates → register → resume.

---

## 15) INTERFACES (RAW ONLY)
- System Law index (SoT for LAW existence):
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/00__INDEX__SYSTEM_LAW.md
- Canon Protocol:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/04__CANON_PROTOCOL.md
- Versioning & Change Policy:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/03__VERSIONING_CHANGE_POLICY.md
- Standards master index:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/00_STANDARDS%20%E2%80%94%20MASTER%20INDEX.md
- System Entities master index:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/02__INDEX__SYSTEM_ENTITIES.md
- Runtime entrypoint:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01__START_UNIVERSE_ENGINE.md

---

## FINAL RULE (LOCK)
This constitution is the highest authority of Universe Engine.
Any deviation is a violation until corrected via canon protocol.

OWNER: SYSTEM
LOCK: FIXED

--- END.
