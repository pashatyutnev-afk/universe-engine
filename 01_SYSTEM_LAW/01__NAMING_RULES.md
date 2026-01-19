# NAMING RULES — CANONICAL FILE/FOLDER NAMING (CANON)

FILE: 01_SYSTEM_LAW/01__NAMING_RULES.md
SCOPE: Universe Engine (All volumes)
LAYER: 01_SYSTEM_LAW
DOC_TYPE: LAW
LAW_TYPE: NAMING
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.1.0
UID: UE.LAW.NAMING.001
OWNER: SYSTEM
ROLE: Canon naming rules for files/folders, entities, templates, indexes, packs, and date/version tokens. Ensures deterministic navigation and low-friction RAW-link stability.

CHANGE_NOTE:
- DATE: 2026-01-19
- TYPE: MINOR
- SUMMARY: "Aligned naming rules with snapshot RAW navigation + artifact-doc output law; clarified legacy exceptions; formalized prefixes and reserved tokens."
- REASON: "Naming must support RAW-only runtime and minimize breaking renames; ensure consistent entity naming across layers."
- IMPACT: "New files become predictable; legacy files remain stable; renames require protocol."
- CHANGE_ID: UE.CHG.2026-01-19.NAMING.001

---

## 0) PURPOSE (LAW)
These rules define how the repository is named so that:
- indexes can be deterministic,
- RAW links remain stable,
- entities and artifacts are discoverable,
- renames are controlled and auditable.

This law governs:
- file names
- folder names
- entity file naming for SPC/ORC/ENG/CTL/VAL/QA/XREF/REG/DB/LOG
- templates, indexes, readmes, maps
- date/version tokens in filenames (only when permitted)
- legacy exceptions and portability rules

---

## 1) CORE PRINCIPLES (ABSOLUTE)
1.1 Determinism over aesthetics  
Names must allow a reader (and runtime) to predict placement and purpose.

1.2 RAW-link stability is sacred  
Renaming files/folders breaks RAW links. Therefore:
- avoid renames,
- if rename is required → use canon protocol + deprecation pointer + registry updates.

1.3 Snapshot runtime compatibility  
During runtime, navigation is restricted to the ROOT snapshot and user-provided RAW links.
Naming must not assume hidden paths or “guessed” locations.

1.4 One meaning per token  
A naming token must not be overloaded. If a name is unclear, it is invalid.

---

## 2) UNIVERSAL FILE NAMING SHAPE
### 2.1 Base pattern (recommended)
`<ORDER>__<SUBJECT>__<QUALIFIER>.md`

Where:
- `<ORDER>` is an ordering token like `00`, `01`, `02`, or a domain token like `T01`
- `__` (double underscore) is the canonical separator
- `<SUBJECT>` is UPPER_SNAKE (preferred) or stable legacy form
- `<QUALIFIER>` is optional and uses reserved tokens when possible

Examples:
- `00__README__SYSTEM_ENTITIES.md`
- `02__INDEX__SYSTEM_ENTITIES.md`
- `03__MAP__PIPELINES.md`
- `01__MACHINE_ARCHITECT_SPC.md`
- `05__LAW__CHAT_ENTRYPOINT_PROTOCOL.md`

### 2.2 Extension
- Canon documents use `.md`.
- No other extension is allowed for canon governance/law/standards unless explicitly defined by a higher law.

### 2.3 Separators
- Primary separator: `__`
- Secondary separator inside tokens: `_`
- Avoid spaces in new canon file names.

---

## 3) ORDER TOKENS (SORTING)
### 3.1 Numeric order
- Use `00`, `01`, `02` … for ordered docs in a folder.
- `00` is reserved for: README / INDEX / TEMPLATE / primary entry in a realm.

### 3.2 Typed order tokens (domain-specific)
- Tracks: `T01`, `T02`, … (always 2 digits)
- Chapters/Episodes: `E01`, `E02`, … (if that subsystem defines it)
- Steps: `S01`, `S02`, … (if an ORC step library defines it)

Typed tokens must be defined by the subsystem standard.

---

## 4) RESERVED TOKENS (CANON DICTIONARY)
These tokens are reserved and must keep exact spelling:

- `README`
- `INDEX`
- `TEMPLATE`
- `RULES`
- `LAW`
- `MAP`
- `SPEC`
- `PROTOCOL`
- `REG` / `REGISTRY`
- `DB`
- `LOG`
- `CARD`
- `PASSPORT`
- `BLUEPRINT`
- `PROMPT`
- `RELEASE`
- `OUTPUT_PACK`
- `GATES`
- `CHANGELOG`
- `DEPRECATION`

Use reserved tokens when naming canon governance documents.
If a new token is needed → it must be registered (via standards / registry process).

---

## 5) CHARACTER SET & PORTABILITY
### 5.1 Preferred character set for new canon files
- ASCII letters (A–Z), digits, `_`, `-` are preferred.
- Reason: fewer RAW encoding issues and better cross-platform handling.

### 5.2 Cyrillic (legacy + allowed zones)
Cyrillic names may exist in:
- workshop artifacts,
- user-facing creative content,
- legacy packs already in repo.

Rule:
- Do not rename Cyrillic legacy paths without protocol.
- For new canon governance (LAW/STANDARDS/ENTITIES indexes): prefer ASCII.

### 5.3 Spaces
- Avoid spaces in new canon files.
- Legacy files with spaces are allowed, but renaming them is a breaking change and must follow protocol.

---

## 6) ENTITY FILE NAMING (SYSTEM ENTITIES)
### 6.1 Entity class suffixes (ABSOLUTE)
Entity files must end with one of:
- `_SPC`
- `_ORC`
- `_ENG`
- `_CTL`
- `_VAL`
- `_QA`
- `_XREF` (or `XREF` in reserved token position when used as map/index)
- `_REG` (if used)
If a class is missing → GAP must be declared before creating a new suffix.

### 6.2 Canon entity file pattern
`<ORDER>__<ENTITY_NAME>_<CLASS>.md`

Examples:
- `01__MACHINE_ARCHITECT_SPC.md`
- `05__PIPELINE_ARCHITECT_SPC.md`
- `01__READINESS_CHECK_CTL.md`
- `03__TRACK_TEST_DOC_GATE_ORC.md`
- `04__CHANGE_CONTROL_ENG.md`

### 6.3 Entity name style
- Use `UPPER_SNAKE` for `<ENTITY_NAME>`.
- Keep it short but specific: no vague names like `HELPER`, `GENERAL`, `MISC`.

---

## 7) REALM READMES & REALM INDEXES
### 7.1 Realm README naming
`00__README__<REALM>_REALM.md` (preferred)
or legacy: `00__README__<REALM>.md`

Examples (existing pattern):
- `00__README__SPC_REALM.md`
- `00__README__ORC_REALM.md`
- `00__README__ENGINES_REALM.md`

### 7.2 Realm index naming
- `02__INDEX_ALL_<REALM>.md` (for “all entities” within realm)
- `02__INDEX__<SCOPE>.md` (for master scope index)

Examples:
- `02__INDEX_ALL_SPECIALISTS.md`
- `02__INDEX_ALL_ORCHESTRATORS.md`
- `02__INDEX_ALL_ENGINES.md`

Indexes are the single source of truth for existence within their scope.

---

## 8) TEMPLATE NAMING
### 8.1 Canon template file pattern
`<ORDER>__TEMPLATE__<SUBJECT>.md`

Examples:
- `00__TEMPLATE__ENGINE__CORE_ENGINES.md`
- `00__TEMPLATE__ORC_ENTITY.md`
- `00__TEMPLATE__SPC_ENTITY.md`

### 8.2 Template folders
Use template realms:
- `01_TPL__TEMPLATES/` for system templates
- domain-specific template folders are allowed only when governed by a standard.

---

## 9) MAP / XREF NAMING
### 9.1 Map files
`<ORDER>__MAP__<SUBJECT>.md`

Examples:
- `01__MAP__ENG_to_ORC.md`
- `03__MAP__VALIDATION_MATRIX.md`

### 9.2 XREF indexes/records
- XREF indexes use `INDEX` token.
- XREF records use `RECORD` token if defined; otherwise use `XREF_RECORD` within template constraints.

---

## 10) DATABASES & LOGS NAMING
### 10.1 DB files
`DB__<SUBJECT>.md`  
Examples:
- `DB__DOC_REGISTRY.md`
- `DB__ENTITY_TYPES.md`

### 10.2 LOG files
`LOG__<SUBJECT>.md`  
Examples:
- `LOG__AUDIT.md`
- `LOG__CHANGES.md`

DB/LOG naming is strict; do not invent new prefixes.

---

## 11) DATE TOKENS (WHEN ALLOWED)
### 11.1 Date format
Use ISO:
- `YYYY-MM-DD`

### 11.2 Where dates are allowed in filenames
Dates in filenames are allowed for:
- releases,
- output packs,
- time-stamped logs/records where the standard requires it.

Example:
- `2026-01-10__TRK__SEREBRYANY_PUT__OUTPUT_PACK.md`

Dates are not required for core laws/standards/entities (use VERSION + CHANGE_NOTE instead).

---

## 12) VERSION TOKENS (WHEN ALLOWED)
### 12.1 Canon rule
Version lives in the document header (`VERSION:`). Filenames should not carry versions.

### 12.2 Allowed exceptions
Filename version suffix is allowed only for:
- unpacked/imported packs,
- migration snapshots,
- explicitly versioned external bundles.

Format:
- `_v2`
- `_v2_1` (patch-like)
No dots in filename version tokens.

If a canon file is renamed to include a version → treat as a breaking change and require protocol.

---

## 13) MUSIC SYSTEM NAMING (SUBSYSTEM RULESET)
### 13.1 Group/Album/Track directories (canonical pattern)
- Group folder: `GROUPS/<GROUP_UID>__<GROUP_SLUG>/` (preferred)  
  Legacy variants are allowed but should not expand.

- Album folder: `ALBUMS/<ALBUM_UID>__<ALBUM_SLUG>/`

- Track folder: `TRACKS/T01__<TRACK_TITLE>/`

### 13.2 Track documents (minimum set)
- `00__TRACK__CARD.md`
- `01__TRACK__PROMPT.md`
- `02__TRACK__RELEASE.md`

If subsystem uses a combined pack:
- `__OUTPUT_PACK` is allowed as governed by the music standards.

### 13.3 Track numbering is mandatory
If tracks are in a set/album, track IDs must preserve order:
- `T01`, `T02`, … and titles must match the canonical track list.

---

## 14) PROHIBITIONS (ABSOLUTE)
- No guessing paths or creating “implied” names outside the governing index.
- No duplicate names for two different entities in the same scope.
- No spaces in new canon governance file names.
- No renames without protocol.
- No “fake folders” that mirror canon scopes without being declared as pointers/aliases.

---

## 15) RENAME & DEPRECATION RULE (BREAKING CHANGES)
If a rename is required:
1) Declare reason and impact.
2) Create a deprecation pointer at the old location (if standard permits).
3) Update governing index (SoT).
4) Update registries (DOC_REGISTRY or equivalent).
5) Write CHANGE_NOTE.
6) Log the change (LOG__CHANGES / audit if required).

No silent renames.

---

## 16) EXAMPLES (REFERENCE)
Valid:
- `00__README__KB_REALM.md`
- `02__INDEX__SYSTEM_ENTITIES.md`
- `01__MACHINE_ARCHITECT_SPC.md`
- `03__MAP__PIPELINES.md`
- `DB__DOC_REGISTRY.md`
- `LOG__AUDIT.md`

Invalid:
- `readme.md` (missing ordering + reserved token)
- `Machine Architect.md` (spaces + inconsistent case + missing suffix)
- `01_machine_architect_spc.md` (wrong separator + inconsistent case)
- `01__MACHINEARCHITECT.md` (missing class suffix)

---

## 17) INTERFACES (RAW ONLY)
- UID Rules:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/02__UID_RULES.md
- Versioning & Change Policy:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/03__VERSIONING_CHANGE_POLICY.md
- Canon Protocol:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/04__CANON_PROTOCOL.md

---

LOCK: FIXED
--- END.
