# VERSIONING & MEMORY ENGINE (ENG) — CANON
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/10__VERSIONING_MEMORY_ENG.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
DOC_TYPE: ENGINE
FAMILY: 00_GOVERNANCE_ENGINES
CLASS: GOVERNANCE (L1)
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.ENG.GOV.VERSIONING_MEMORY.001
OWNER: SYSTEM
ROLE: Canon versioning law + memory system. Defines how versions are bumped, how canon states are snapshotted, and how changes become a durable, navigable history without breaking compatibility.

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Versioning & Memory promoted to full canonical policy: SemVer-like rules, compatibility windows, snapshot records, memory packs, deprecation bridges."
- REASON: "Prevent silent drift and make canon evolution reversible, traceable, and readable via raw-links."
- IMPACT: "All canon entities become version-governed; snapshots become standard."
- CHANGE_ID: UE.CHG.2026-01-08.GOV.VM.001

---

## 0) PURPOSE (LAW)

Versioning & Memory Engine отвечает:
> “Что именно изменилось, насколько это ломает совместимость, какую версию ставим, и как это навсегда запомнить так, чтобы можно было откатиться/понять/воспроизвести.”

Он превращает изменения в:
- **VERSION POLICY DECISION** (какой bump и почему)
- **COMPATIBILITY CONTRACT** (что ломается, что поддерживается)
- **SNAPSHOT RECORD** (состояние канона на дату/версию)
- **MEMORY PACK** (ссылки на ключевые артефакты изменений)

Non-goals:
- не решает “можно ли менять” (это Risk Safety + Canon Authority)
- не строит индексы (это Change Control + Scope Impact)
- не проверяет консистентность всего репо (это Consistency)
- не заменяет Audit Log — а формализует, когда и как туда пишем

---

## 1) MINI-CONTRACT (MANDATORY)

CONSUMES:
- CHANGE_PROPOSAL
- DIFF_SUMMARY
- SCOPE_IMPACT_REPORT
- SAFETY_DECISION?                      # optional but recommended
- REQUIRED_UPDATES_LIST
- MIGRATION_MAP?                        # mandatory for IC3/IC4/IC6
- AUDIT_LOG_ENTRY_PLAN?                 # planned record(s)

PRODUCES:
- VERSION_DECISION_RECORD
- COMPATIBILITY_CONTRACT
- SNAPSHOT_RECORD?                      # mandatory for major canon milestones
- MEMORY_PACK_RECORD
- RELEASE_NOTE_ENTRY?                   # optional, but recommended for major/minor

DEPENDS_ON:
- 00_GOVERNANCE_ENGINES/01__AUDIT_LOG_ENG
- 00_GOVERNANCE_ENGINES/04__CHANGE_CONTROL_ENG
- 00_GOVERNANCE_ENGINES/08__SCOPE_IMPACT_ENG
- 00_GOVERNANCE_ENGINES/09__RISK_SAFETY_ENG

OUTPUT_TARGET:
- 99_LOGS/LOG__AUDIT.md
- 99_LOGS/LOG__CHANGES.md
- 99_LOGS/LOG__RELEASES.md?             # optional future log (allowed)

---

## 2) VERSION FORMAT (STRICT)

### 2.1 Canonical Version format
VERSION must use:
`MAJOR.MINOR.PATCH`

- MAJOR: breaks compatibility / changes canon structure meaningfully
- MINOR: adds compatible capability / expands without breaking
- PATCH: fixes, clarifies, refactors without behavior change

Hard rule:
- VERSION must be present exactly once in header.
- No duplicated VERSION at end.

---

## 3) COMPATIBILITY MODEL (CANON)

Compatibility is not “code API”, it’s **navigation + meaning + contracts**.

We define compatibility layers:

C1 — Navigation compatibility
- raw-links still resolve
- canonical entrypoints still exist
- indexes still represent reality

C2 — Contract compatibility
- mini-contract fields still present
- required sections still exist
- schema expectations preserved

C3 — Semantic compatibility
- meaning of entities and rules doesn’t invert unexpectedly
- renames/moves are bridged with migration maps

A change is **breaking** if it breaks any of:
- C1 in canonical layer
- C2 for required doc types
- C3 without explicit deprecation bridge

---

## 4) BUMP RULES (MANDATORY)

### 4.1 PATCH bump triggers (non-breaking)
Allowed triggers:
- typo fixes, clarifications
- formatting normalization
- internal examples improved
- refactor that does not change policy meaning
- adding missing but expected details that do not change rules

Forbidden for PATCH:
- renaming canonical paths
- changing required schema fields
- changing law statements meaningfully

### 4.2 MINOR bump triggers (compatible expansion)
Allowed triggers:
- adding new OPTIONAL sections
- adding new engines/entities without breaking existing ones
- expanding index with new family/engine while preserving numbering rules
- adding new validators/QA checks (non-breaking) that don’t invalidate existing canon

### 4.3 MAJOR bump triggers (breaking)
MAJOR required if any:
- IC3 structural move/rename/delete of canonical docs without full bridge
- index structure rule changes
- existence rule / canon protocol changes
- schema changes that require rewriting existing files
- re-numbering families/engines in a way that changes canonical identity

Hard rule:
- If change includes IC4 (architecture change) => MAJOR.
- If Risk Safety decision is UNSAFE => do not version-bump; stop.

---

## 5) MIGRATION & BRIDGES (MANDATORY FOR BREAKING)

If MAJOR or any IC3/IC6 exists:
- MIGRATION_MAP must exist.
- Compatibility bridges must exist.

Bridge types:
- PATH_BRIDGE: old raw-link -> new raw-link mapping
- NAME_BRIDGE: old name -> new name mapping
- DEPRECATION_POINTER: deprecate old doc, point to replacement
- INDEX_BRIDGE: index update that preserves discoverability

Hard rule:
- No breaking change can be “silent”.
- Every bridge must be raw-link navigable.

---

## 6) MEMORY SYSTEM (CANON)

We store memory in 3 layers:

M1 — Audit memory (atomic)
- every canon change creates an audit entry

M2 — Change memory (grouped)
- related changes form a CHANGE PACK (bundle)

M3 — Snapshot memory (state)
- a snapshot describes the canon state at a moment/version

Snapshots are not “copies of all files”.
Snapshots are **records** that reference:
- root indexes
- key registries
- change packs
- migration maps

---

## 7) SNAPSHOT POLICY (MANDATORY CONDITIONS)

Snapshot is mandatory when any:
- MAJOR bump
- restructure of indexes or entrypoints
- introduction of new layer-wide standard that affects many docs
- “milestone” release of system (explicitly named)

Snapshot is recommended when:
- MINOR bump affecting multiple families
- new governance law added

---

## 8) OUTPUT FORMATS (CANON)

### 8.1 VERSION_DECISION_RECORD (mandatory)
Format:

VERSION_DECISION_RECORD:
- RECORD_ID: UE.VER.YYYY-MM-DD.NNN
- DATE: YYYY-MM-DD
- CHANGE_ID:
- PREV_VERSION:
- NEW_VERSION:
- BUMP_TYPE: MAJOR|MINOR|PATCH
- WHY:
- BREAKS: [C1|C2|C3] or []
- BRIDGES_REQUIRED: YES|NO
- REQUIRED_ARTIFACTS:
  - MIGRATION_MAP: REQUIRED|NA
  - REQUIRED_UPDATES_LIST: REQUIRED|NA
  - AUDIT_ENTRY: REQUIRED
- NOTES:

### 8.2 COMPATIBILITY_CONTRACT (mandatory)
Format:

COMPATIBILITY_CONTRACT:
- CONTRACT_ID: UE.CMP.YYYY-MM-DD.NNN
- VERSION_RANGE_SUPPORTED:
  - MIN_SUPPORTED:
  - MAX_SUPPORTED:
- GUARANTEES:
  - raw-links stable? YES|NO
  - index entrypoints stable? YES|NO
  - schema stable? YES|NO
- BREAKING_POINTS:
  - what breaks + how to migrate
- MIGRATION_ENTRY:
  - raw-link to MIGRATION_MAP or NA

### 8.3 SNAPSHOT_RECORD (conditional mandatory)
Format:

SNAPSHOT_RECORD:
- SNAPSHOT_ID: UE.SNP.YYYY-MM-DD.NNN
- DATE: YYYY-MM-DD
- VERSION:
- NAME: (short)
- ENTRYPOINTS:
  - ROOT_INDEX: (raw-link)
  - SYSTEM_LAW_INDEX: (raw-link)
  - SYSTEM_ENTITIES_INDEX: (raw-link)
  - ENG_INDEX_ALL_ENGINES: (raw-link)
- CHANGE_PACKS:
  - list of raw-links or IDs
- MIGRATION_MAPS:
  - list of raw-links or []
- NOTES:

### 8.4 MEMORY_PACK_RECORD (mandatory)
Format:

MEMORY_PACK_RECORD:
- PACK_ID: UE.MEM.YYYY-MM-DD.NNN
- CHANGE_ID:
- VERSION_DECISION_RECORD: (raw-link or ID)
- SCOPE_IMPACT_REPORT: (raw-link or ID)
- SAFETY_ASSESSMENT_REPORT: (raw-link or ID) or NA
- MIGRATION_MAP: (raw-link) or NA
- AFFECTED_INDEXES:
  - list raw-links
- AFFECTED_FAMILIES:
  - list
- AUDIT_LOG_ENTRY_POINTER:
  - line reference / record id

---

## 9) PRACTICAL CHECKLISTS

### 9.1 Checklist — any canon edit
- [ ] Change has CHANGE_ID
- [ ] Scope Impact exists with impact classes
- [ ] Version bump decision recorded
- [ ] Audit entry planned
- [ ] Raw-links remain resolvable

### 9.2 Checklist — structural edit (IC3/IC4/IC6)
- [ ] MIGRATION_MAP exists
- [ ] Bridges defined (path/name/index)
- [ ] Rollback requirements defined (from Risk Safety)
- [ ] Snapshot planned (if MAJOR or milestone)
- [ ] Compatibility contract filled

### 9.3 Checklist — index edits
- [ ] No phantom references (index -> missing file)
- [ ] No hidden files (file exists but not in canon index)
- [ ] Ordering and numbering rules preserved
- [ ] Raw-links updated everywhere

---

## 10) “VERSION OWNERSHIP” (WHO BUMPS WHAT)

Hard rule:
- Each canon document owns its VERSION field.
- Cross-cutting changes may require coordinated bumps.

Coordination rule:
- If a governance law changes, dependent engines should get MINOR or PATCH bump if impacted.

Recommended minimal policy:
- Changes limited to one file => bump that file only (unless it breaks system contract)
- Changes that alter rules used by many => bump the rules file + note affected families

---

## 11) EXAMPLES

### Example A — fix typo in engine (PATCH)
- NEW_VERSION: x.y.(z+1)
- No migration, no snapshot, audit required

### Example B — add new optional section to template (MINOR)
- NEW_VERSION: x.(y+1).0
- Compatibility remains, audit required

### Example C — rename canonical index file (MAJOR)
- NEW_VERSION: (x+1).0.0
- MIGRATION_MAP mandatory
- Snapshot mandatory
- Bridges mandatory

---

## 12) REFERENCES (RAW ONLY)

Audit Log Engine:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/01__AUDIT_LOG_ENG.md

Change Control Engine:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/04__CHANGE_CONTROL_ENG.md

Scope Impact Engine:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/08__SCOPE_IMPACT_ENG.md

Risk Safety Engine:
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/09__RISK_SAFETY_ENG.md

Logs (targets):
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/99_LOGS/LOG__AUDIT.md
- https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/99_LOGS/LOG__CHANGES.md

--- END.
