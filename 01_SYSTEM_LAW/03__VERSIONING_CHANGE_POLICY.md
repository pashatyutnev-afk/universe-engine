# VERSIONING & CHANGE POLICY — SEMVER + CHANGE_ID (CANON)

FILE: 01_SYSTEM_LAW/03__VERSIONING_CHANGE_POLICY.md
SCOPE: Universe Engine (All volumes)
LAYER: 01_SYSTEM_LAW
DOC_TYPE: LAW
LAW_TYPE: VERSIONING_CHANGE
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.1.0
UID: UE.ALL.LAW.SYSTEM.VERSIONING.001
OWNER: SYSTEM
ROLE: Defines how versions change, how changes are logged, what is a breaking change, and how runtime outputs are treated under snapshot-based RAW navigation.

CHANGE_NOTE:
- DATE: 2026-01-19
- TYPE: MINOR
- SUMMARY: "Aligned with START boot discipline + mandatory CHANGE_ID; added runtime RUN_NOTE vs repo CHANGE_NOTE; clarified artifact-doc versioning; clarified LOCK/FIXED policy and deprecation pointer rules."
- REASON: "System now enforces entrypoint routing, gates, and artifact-doc outputs; versioning must be auditable and deterministic."
- IMPACT: "Any change becomes traceable; output artifacts have stable lifecycle; no silent changes."
- CHANGE_ID: UE.CHG.2026-01-19.VER.001

---

## 0) PURPOSE (LAW)
This policy exists to guarantee:
- predictable evolution of documents and entities,
- auditable change history (CHANGE_ID),
- stable references under RAW-only snapshot navigation,
- clear rules for when a change is allowed, blocked, or requires deprecation + replacement.

This policy governs:
- VERSION increments (SEMVER)
- CHANGE_NOTE + CHANGE_ID requirements
- STATUS/LOCK behavior
- deprecation and replacement rules
- runtime “outputs as artifact docs” versioning

---

## 1) ABSOLUTE LAWS (MUST)
1.1 No silent changes  
If content changes and the doc is canon, VERSION must be updated and CHANGE_NOTE must be present.

1.2 UID immutability  
UID never changes. Version changes are tracked with VERSION + CHANGE_ID.

1.3 Lock discipline  
If `LOCK: FIXED`, content cannot be changed except via an approved change procedure (governance may require a replacement doc).  
If `LOCK: OPEN`, edits are allowed but must obey this policy.

1.4 Deprecation is explicit  
Replacing a doc never deletes identity. The old doc becomes `DEPRECATED` and points to the replacement.

1.5 Snapshot reality  
Runtime uses a snapshot of RAW links. Updating a doc version does not mean the runtime “sees it” unless the user refreshes the ROOT link base snapshot.

---

## 2) DEFINITIONS
### 2.1 VERSION (SEMVER)
`MAJOR.MINOR.PATCH`
- MAJOR: breaking change (interfaces/meaning/requirements change)
- MINOR: backward-compatible extension or clarification
- PATCH: typo fixes, small clarifications, no behavior/meaning change

### 2.2 CHANGE_NOTE (Repo change record)
A structured block in the document header describing a committed change that increments VERSION.

Minimum fields:
- DATE
- TYPE (MAJOR|MINOR|PATCH)
- SUMMARY
- REASON
- IMPACT
- CHANGE_ID

### 2.3 CHANGE_ID (Unique change identifier)
Every VERSION change must have a unique `CHANGE_ID` (see UID rules).

### 2.4 RUN_NOTE (Runtime output record)
For outputs generated during chat/runtime without repo commit:
- keep `VERSION` for the artifact doc,
- include `RUN_NOTE` instead of `CHANGE_NOTE` if it is not committed into repo.

Minimum RUN_NOTE:
- DATE
- RUN_ID (local)
- SUMMARY
- INPUTS (brief)
- OUTPUT_UIDS (if assigned)

### 2.5 COMPATIBILITY
A change is “compatible” if existing users of the doc/entity can continue without edits.

---

## 3) WHAT REQUIRES VERSION CHANGE
### 3.1 Always requires VERSION bump
- adding/removing/renaming required sections
- changing constraints, gates, stop conditions
- changing required output formats
- changing entity responsibilities or routing rules
- changing UID/CHANGE_ID formats or required fields
- changing how artifacts must be packaged

### 3.2 Usually PATCH only
- typo fixes
- formatting fixes that do not change meaning
- clarifying examples without changing rules

### 3.3 Breaking changes (MAJOR)
Any change that:
- invalidates previously compliant docs/artifacts,
- changes the meaning of compliance,
- changes required gates or ordering,
- changes a mandatory interface contract.

If unsure: treat as MAJOR or create a replacement doc and deprecate the old one.

---

## 4) VERSION BUMP RULES (SEMVER LAW)
### 4.1 PATCH (x.y.Z)
Allowed when:
- meaning is unchanged,
- no new requirements,
- no removed requirements,
- no changes to mandatory headers/IDs.

### 4.2 MINOR (x.Y.z)
Allowed when:
- adds optional capabilities,
- adds new non-mandatory sections,
- clarifies ambiguous wording without changing constraints,
- adds examples, checklists, or mappings that do not change compliance.

### 4.3 MAJOR (X.y.z)
Required when:
- any compliance rule changes,
- any gate ordering changes,
- any mandatory section changes,
- any stop condition changes,
- any required output contract changes.

---

## 5) STATUS & LOCK POLICY
### 5.1 STATUS values
- `DRAFT`: not authoritative
- `ACTIVE`: authoritative and used by runtime
- `DEPRECATED`: replaced; must include replacement pointers
- `ARCHIVED`: frozen historical artifact (rare; must be governed)

### 5.2 LOCK values
- `FIXED`: stable law/spec; changes are exceptional and controlled
- `OPEN`: allowed to evolve under versioning policy

### 5.3 FIXED rule (absolute)
If a `FIXED` doc needs a MAJOR change:
- prefer creating a new doc with a new UID,
- mark old doc `DEPRECATED`,
- include replacement pointers (UID + RAW).

---

## 6) DEPRECATION & REPLACEMENT PROTOCOL (MANDATORY)
When replacing a doc/entity:
1) Create the replacement with new UID + VERSION 1.0.0
2) Mark old doc as `DEPRECATED`
3) Add pointers in old doc header:
   - `REPLACED_BY_UID: <new UID>`
   - `REPLACED_BY_RAW: <raw link to new doc>`
4) Add change log entry (CHANGE_ID) to old doc if permitted by LOCK
5) Update registries if governed (doc registry, entity registry)

No deletion, no UID reuse.

---

## 7) RUNTIME OUTPUT VERSIONING (ARTIFACT DOCS)
### 7.1 Artifact docs are versioned too
Any produced artifact doc must include:
- UID (if canonized or tracked)
- VERSION
- STATUS
- RUN_NOTE (or CHANGE_NOTE if committed)

### 7.2 Default artifact version lifecycle
- First produced draft: `VERSION: 1.0.0` + `STATUS: DRAFT`
- Rework that changes meaning/inputs: bump MINOR or PATCH as appropriate
- Final accepted for release: `STATUS: ACTIVE` (or `READY` if subsystem uses it)

### 7.3 “One axis change” discipline (if subsystem requires)
If an artifact is being iterated:
- change only one major axis per iteration (e.g., voice, tempo, structure)
- document what axis changed in RUN_NOTE/CHANGE_NOTE
(Subsystem controllers may enforce this.)

---

## 8) CHANGE MANAGEMENT MINIMUM (WHEN CHANGES ARE ALLOWED)
When changing LAW/STANDARD/PROTOCOL:
- must include CHANGE_NOTE + CHANGE_ID
- must not contradict higher-level laws (rule hierarchy)
- if contradictions appear: create a governed resolution (or replacement doc)

Runtime must not “assume” updated docs unless the user refreshes ROOT link base snapshot.

---

## 9) REGISTRY & LOGGING (AUDITABILITY)
### 9.1 Minimum traceability requirement
A change must be traceable by:
- UID (object identity)
- VERSION (state)
- CHANGE_ID (change event)

### 9.2 Where changes get recorded
Depending on governance:
- document header (CHANGE_NOTE)
- change log (LOG__CHANGES)
- audit log (LOG__AUDIT)
- doc registry (DB__DOC_REGISTRY)

This policy does not redefine registry schemas; it requires that versioned objects are traceable.

---

## 10) DEFAULT VERSIONING RULES BY DOC TYPE (GUIDE)
- LAW / PROTOCOL / STANDARD: prefer FIXED; MAJOR changes should create replacements
- SPEC / TEMPLATE: evolves more; MINOR/PATCH common
- INDEX: MINOR when adding links/sections; PATCH for formatting; MAJOR if navigation rules change
- ENTITY docs: MINOR for added capabilities; MAJOR if responsibilities/routing/gates change
- ARTIFACT docs: version per output lifecycle; subsystem controllers define stricter rules

If doc type is unclear → treat as SPEC and apply conservative bumps.

---

## 11) INTERFACES (RAW ONLY)
- UID Rules:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/02__UID_RULES.md
- Naming Rules:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/01__NAMING_RULES.md
- Canon Protocol:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/04__CANON_PROTOCOL.md
- Start Entrypoint (boot discipline reference):
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01__START_UNIVERSE_ENGINE.md

---

LOCK: FIXED
--- END.
