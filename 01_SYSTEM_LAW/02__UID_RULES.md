# UID RULES — CANONICAL IDENTIFIERS & CHANGE IDS (CANON)

FILE: 01_SYSTEM_LAW/02__UID_RULES.md
SCOPE: Universe Engine (All volumes)
LAYER: 01_SYSTEM_LAW
DOC_TYPE: LAW
LAW_TYPE: IDENTIFIERS
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.1.0
UID: UE.LAW.UID.001
OWNER: SYSTEM
ROLE: Defines UID + CHANGE_ID formats and invariants for docs, entities, artifacts, registries, logs, and packs. Guarantees stable identity across snapshot-based RAW navigation.

CHANGE_NOTE:
- DATE: 2026-01-19
- TYPE: MINOR
- SUMMARY: "Formalized UID/CHANGE_ID normalization; added artifact UID blocks; clarified registration + immutability; added volume scope tokens and legacy handling."
- REASON: "System now enforces boot-first + artifact-doc outputs; IDs must be auditable and collision-resistant."
- IMPACT: "New docs/entities/artifacts become uniquely traceable; change logs become deterministic."
- CHANGE_ID: UE.CHG.2026-01-19.UID.001

---

## 0) PURPOSE (LAW)
UID rules exist to:
- uniquely identify every canon object (doc/entity/artifact/registry/log record),
- keep identity stable even when content evolves,
- enable audits, gates, and “no silent changes” enforcement,
- support snapshot-based runtime (RAW-only navigation) without guessing.

This law governs:
- UID format and invariants
- CHANGE_ID format and invariants
- how to assign, register, and reference UIDs
- what can/cannot change after issuance
- collision handling and deprecation pointers
- minimal ID blocks required in documents and artifacts

---

## 1) ABSOLUTE PRINCIPLES (MUST)
1.1 Uniqueness  
A UID must identify exactly one object for its entire lifetime.

1.2 Immutability  
Once issued, a UID never changes. Renames do not imply UID change.

1.3 Non-semantic stability  
UID must not depend on mutable names/titles. Human-readable names can change; UID does not.

1.4 Deterministic issuance  
UID issuance must follow predictable rules so that collisions are rare and detectable.

1.5 Registration required for canon  
Every canon doc/entity/artifact must be registrable in the appropriate registry/DB/log.

---

## 2) UID TYPES (WHAT NEEDS A UID)
### 2.1 Documents (DOC)
Any canon document (LAW/STANDARD/PROTOCOL/SPEC/README/INDEX/TEMPLATE/MAP) must have a UID.

### 2.2 System Entities (ENTITY)
Any entity definition file (SPC/ORC/ENG/CTL/VAL/QA/XREF/REG) must have a UID.

### 2.3 Artifacts (ART)
Any produced deliverable that is an “output artifact doc” must have a UID:
- track docs (track card/prompt/release/output pack)
- scene packs
- release packs
- certified packs (QA exemplar sets, validation records)

### 2.4 Registries / Databases / Logs (REG/DB/LOG)
- DB tables/docs may have their own UIDs (optional if governed elsewhere), but each **record** must reference target UIDs.
- Change entries must have CHANGE_ID.

---

## 3) CANONICAL UID FORMAT
### 3.1 Base format
`UE.<VOLUME>.<CLASS>.<DOMAIN>.<KIND>.<SEQ>`

Where:
- `UE` = Universe Engine root token
- `<VOLUME>` = volume scope token (e.g., `GAMES`, `SAGA`, `MUSIC`, `CORE`, or `ALL`)
- `<CLASS>` = high-level class (`LAW`, `STD`, `PRT`, `SPEC`, `ENT`, `DOC`, `ART`, `DB`, `LOG`, `XREF`)
- `<DOMAIN>` = subsystem/domain (`SYSTEM`, `KB`, `PRJ`, `MUSIC`, `NARRATIVE`, `VISUAL`, etc.)
- `<KIND>` = object kind within domain (e.g., `UID`, `NAMING`, `START`, `SPC`, `ENG`, `TRACK`, `INDEX`)
- `<SEQ>` = zero-padded numeric sequence (3 digits default)

Examples:
- `UE.ALL.LAW.SYSTEM.UID.001`
- `UE.GAMES.DOC.SYSTEM.START.001`
- `UE.ALL.ENT.MUSIC.SPC.012`
- `UE.GAMES.ART.MUSIC.TRACK.145`

### 3.2 Allowed separators
- UID uses dots `.` only.
- No spaces, no underscores inside UID.

### 3.3 Sequence width
- Default: `001`–`999`
- If a domain exceeds 999, introduce a new KIND or a new DOMAIN split (preferred) rather than expanding width.

---

## 4) REQUIRED ID BLOCK (DOC HEADER MINIMUM)
Any canon document must include (in header):
- `UID: <...>`
- `VERSION: x.y.z`
- `STATUS: ACTIVE|DRAFT|DEPRECATED`
- `LOCK: FIXED|OPEN`
- `SCOPE: ...`
- `DOC_TYPE: ...`
- `OWNER: ...`

If missing → document is non-canon and cannot be used as authoritative input.

---

## 5) CHANGE_ID FORMAT (MANDATORY FOR CHANGES)
### 5.1 Base format
`UE.CHG.<YYYY-MM-DD>.<AREA>.<SEQ>`

Where:
- `<AREA>` is a short stable area token (examples: `START`, `UID`, `NAMING`, `KB`, `MUSIC_SYS`, `PRJ_GOV`)
- `<SEQ>` is a 3-digit sequence for that day+area

Example:
- `UE.CHG.2026-01-19.START.001`

### 5.2 CHANGE_ID rules
- Must be present in `CHANGE_NOTE` for any change that increments VERSION.
- Must not be reused.
- Must not encode file paths.
- If multiple docs change in one “batch”, each doc gets its own CHANGE_ID (or a parent change record references multiple docs, if that standard exists).

---

## 6) UID ISSUANCE RULES (HOW TO ASSIGN)
### 6.1 New canon law/standard/protocol/spec
- Set `<VOLUME>` = `ALL` unless explicitly volume-scoped
- `<CLASS>` based on doc type
- `<DOMAIN>` = `SYSTEM` for foundational governance
- `<KIND>` = short semantic type
- `<SEQ>` next available sequence in that KIND

### 6.2 New entity (SPC/ORC/ENG/CTL/VAL/QA)
- `<CLASS>` = `ENT`
- `<DOMAIN>` = domain of responsibility (e.g., `MUSIC`, `SYSTEM`, `NARRATIVE`)
- `<KIND>` = entity class (`SPC`, `ENG`, `ORC`, `CTL`, `VAL`, `QA`, `XREF`)
- `<SEQ>` next available

### 6.3 New artifact doc
- `<CLASS>` = `ART`
- `<DOMAIN>` = subsystem (`MUSIC`, `VISUAL`, `NARRATIVE`, etc.)
- `<KIND>` = artifact type (`TRACK`, `SCENE`, `RELEASE_PACK`, `OUTPUT_PACK`, `QA_SET`, `VAL_RECORD`)
- `<SEQ>` next available (or governed by subsystem standard)

---

## 7) UID REFERENCE RULES (HOW TO CITE)
### 7.1 Canon references prefer UID, not paths
Inside docs, refer to other objects by:
- UID (primary)
- RAW link (when the system requires navigation)
- human name (optional)

Recommended pattern:
- `REF_UID: <UID>`
- `REF_RAW: <RAW URL>`

### 7.2 Snapshot runtime constraint
At runtime:
- navigation uses only RAW links in ROOT snapshot or user-provided messages
- UID is used to **reason**, but cannot be used to “guess” a path

Therefore: if you cite a UID, include RAW link when navigation is required.

---

## 8) COLLISION & DUPLICATE HANDLING (ABSOLUTE)
### 8.1 UID collision
If a newly proposed UID already exists:
- STOP issuing that UID
- increment `<SEQ>` or adjust `<KIND>` split
- log a change note in appropriate log (if governed)

### 8.2 Name collisions are not UID collisions
Two different objects may have similar names, but must not share a UID.

---

## 9) DEPRECATION & REPLACEMENT (ID STABILITY)
### 9.1 Deprecation
When an object is replaced:
- old UID remains and status becomes `DEPRECATED`
- new object gets a new UID
- old object must include:
  - `REPLACED_BY_UID: <new UID>`
  - `REPLACED_BY_RAW: <new RAW link>` (if applicable)

### 9.2 No UID recycling
Deprecated UIDs must never be reissued.

---

## 10) UID + VERSION RELATION (WHAT CHANGES WHEN)
- UID never changes.
- VERSION changes when content changes according to versioning law.
- CHANGE_ID records the change event.

---

## 11) ARTIFACT ID BLOCK (OUTPUT DOCS)
Any output artifact doc must include:
- `UID`
- `ARTIFACT_TYPE`
- `SOURCE_UIDS` (what it was derived from, if applicable)
- `VERSION`
- `STATUS`
- `CHANGE_NOTE` (or `RUN_NOTE` if produced by runtime without repo commit)

Example block:
- `UID: UE.GAMES.ART.MUSIC.TRACK.145`
- `ARTIFACT_TYPE: TRACK_PROMPT`
- `SOURCE_UIDS: UE.ALL.ENT.MUSIC.SPC.012; UE.ALL.LAW.SYSTEM.UID.001`
- `VERSION: 1.0.0`
- `STATUS: DRAFT`

---

## 12) MUSIC SUBSYSTEM UID RULES (MINIMUM)
These rules do not replace music standards; they ensure IDs exist.

### 12.1 Track artifacts
- Track card/prompt/release/output pack must have:
  - one UID per document, or
  - one UID for an OUTPUT_PACK that references sub-docs by UID

### 12.2 Group/Album/Track objects
If the subsystem uses internal IDs:
- they may exist as local IDs (e.g., `T01`), but canon UID still required for the doc/artifact.

---

## 13) REGISTRATION (WHERE IDs MUST APPEAR)
### 13.1 Doc registry
Every canon doc should be registrable in `DB__DOC_REGISTRY` (or successor registry):
- `UID`
- `FILE`
- `DOC_TYPE`
- `STATUS`
- `VERSION`
- `CHANGE_ID (latest)`
- `OWNER`

### 13.2 Entity registry
Every entity should be registrable (entity registry standard governs exact table).

### 13.3 Audit / change log
Every change with VERSION bump must be traceable via CHANGE_ID.

---

## 14) LEGACY & TRANSITION RULES
14.1 Legacy UIDs
If legacy documents already have UIDs that do not match this format:
- do not rewrite UID (immutability)
- add `UID_NORMALIZATION_NOTE` describing deviation
- future docs must follow current format

14.2 Planned normalization
If the system needs future normalization (e.g., UID/CHANGE_ID alignment):
- create a governed protocol under change management
- do not mass-edit without that protocol

---

## 15) INTERFACES (RAW ONLY)
- Naming Rules:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/01__NAMING_RULES.md
- Versioning & Change Policy:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/03__VERSIONING_CHANGE_POLICY.md
- Canon Protocol:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/04__CANON_PROTOCOL.md

---

LOCK: FIXED
--- END.
