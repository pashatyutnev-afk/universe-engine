# REGISTRY — NAMING RULES (CANON)
FILE: 03_SYSTEM_ENTITIES/00_REG__REGISTRIES/02__REG_NAMING_RULES.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: REGISTRIES (REG)
DOC_TYPE: REGISTRY
REGISTRY_TYPE: NAMING_RULES
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.REG.NAMING.001
OWNER: SYSTEM
ROLE: Canonical naming rules for folders/files inside 03_SYSTEM_ENTITIES (tokens, numbering, underscores, and alias policy)

CHANGE_NOTE:
- DATE: 2026-01-11
- TYPE: MAJOR
- SUMMARY: "Created naming rules registry: numeric prefixes, underscore rules, tokens, and safe rename/alias protocol."
- REASON: "Stop drift and make navigation deterministic."
- IMPACT: "All entity naming becomes consistent and enforceable."
- CHANGE_ID: UE.CHG.2026-01-11.REG.NAMING.001

---

## 0) PURPOSE (LAW)
This registry defines the canonical naming rules for `03_SYSTEM_ENTITIES`.

It enforces:
- numeric ordering via prefixes
- strict underscore usage
- canonical tokens for entity classes
- safe rename protocol (alias/pointer) without breaking canon

If a file violates this registry — it is NON-CANON until fixed.

---

## 1) CORE NAMING FORMAT (MANDATORY)

## REG.NAMING.NUM_PREFIX — numeric prefix required
- KEY: REG.NAMING.NUM_PREFIX
- CLASS: NAMING
- STATUS: ACTIVE
- SCOPE: all files intended to be ordered or indexed
- OWNER: SYSTEM
- PRIORITY: P1
- RAW: N/A
- RULE: Ordered files must start with a numeric prefix: `NN__` where `NN` is 2 digits (00..99).
- CHECK: Inspect filename start.
- FAIL: Missing numeric prefix OR prefix not 2 digits.
- FIX: Rename to `NN__...` and update indexes; log change.
- LAST_CHANGE_ID: UE.CHG.2026-01-11.REG.NAMING.001

## REG.NAMING.DOUBLE_UNDERSCORE_PLACEMENT — double underscore only after number
- KEY: REG.NAMING.DOUBLE_UNDERSCORE_PLACEMENT
- CLASS: NAMING
- STATUS: ACTIVE
- SCOPE: repo-wide filenames
- OWNER: SYSTEM
- PRIORITY: P0
- RAW: N/A
- RULE: Double underscore `__` is allowed **only** immediately after the numeric prefix (e.g. `04__SOMETHING`). Everywhere else use single underscore `_`.
- CHECK: Scan filenames for `__` occurrences.
- FAIL: Any `__` appears after the initial `NN__` segment.
- FIX: Rename to single `_` in the rest of name; update indexes; log change.
- NOTES: This matches your operational rule: "двойное подчеркивание только после номера".
- LAST_CHANGE_ID: UE.CHG.2026-01-11.REG.NAMING.001

## REG.NAMING.NO_EXTENSION_MENTION — extension is not part of naming references
- KEY: REG.NAMING.NO_EXTENSION_MENTION
- CLASS: NAMING
- STATUS: ACTIVE
- SCOPE: docs and human-facing references
- OWNER: SYSTEM
- PRIORITY: P2
- RAW: N/A
- RULE: Extensions are hidden in human-facing naming references; do not mention `.md` in prose. RAW links include it automatically.
- CHECK: Review docs for `.md` mentions in name-only contexts.
- FAIL: Human naming references include `.md` as if it is part of the filename identity.
- FIX: Remove extension mention from prose; keep it only in RAW links.
- LAST_CHANGE_ID: UE.CHG.2026-01-11.REG.NAMING.001

---

## 2) TOKEN CODING (MANDATORY)
Tokens act as “type codes” inside names.

### 2.1 Allowed primary tokens (recommended set)
- `README` — realm/entry explanation
- `RULES` — ruleset for a folder/class
- `INDEX` — index/registry list (existence + nav)
- `TEMPLATE` or `TPL` — templates
- `MAP` — cross maps
- `REG` — registries
- `ENG` — engines
- `ORC` — orchestrators
- `SPC` — specialists
- `CTL` — controllers
- `VAL` — validators
- `QA` — QA checks/quality layer
- `XREF` — cross references

### 2.2 Token placement rule (recommended)
- Folder class token is embedded in folder name (e.g. `10_ENG__ENGINES`)
- File type token is embedded after numeric prefix (e.g. `02__INDEX_ALL_ENGINES`)

---

## 3) FOLDER NAMING (STANDARD)
## REG.NAMING.FOLDER.CLASS_PREFIX — class folder names are fixed
- KEY: REG.NAMING.FOLDER.CLASS_PREFIX
- CLASS: NAMING
- STATUS: ACTIVE
- SCOPE: top-level folders in 03_SYSTEM_ENTITIES
- OWNER: SYSTEM
- PRIORITY: P0
- RAW: N/A
- RULE: Entity class folders use fixed canonical names (examples):
  - `00_REG__REGISTRIES`
  - `01_TPL__TEMPLATES`
  - `10_ENG__ENGINES`
  - `20_ORC__ORCHESTRATORS`
  - `30_SPC__SPECIALISTS`
  - `40_CTL__CONTROLLERS`
  - `50_VAL__VALIDATORS`
  - `60_QA__QUALITY`
  - `90_XREF__CROSSREF`
- CHECK: Compare folder names against canon list.
- FAIL: Folder name deviates (typos, different token order, missing underscores).
- FIX: Rename folder only via controlled migration; update all RAW links; log change.
- LAST_CHANGE_ID: UE.CHG.2026-01-11.REG.NAMING.001

---

## 4) SAFE RENAME / MIGRATION RULE (MANDATORY)
## REG.NAMING.RENAME.PROTOCOL — rename without breaking canon
- KEY: REG.NAMING.RENAME.PROTOCOL
- CLASS: NAMING
- STATUS: ACTIVE
- SCOPE: any rename of indexed/canon file
- OWNER: SYSTEM
- PRIORITY: P0
- RAW: N/A
- RULE: Renaming a canon file must not break navigation: use a migration protocol.
- CHECK: Verify indexes and super-index raw links remain resolvable.
- FAIL: Rename causes broken RAW links or duplicate entrypoints.
- FIX:
  1) Decide new canonical name/path.
  2) Update all relevant indexes/XREF/super-index.
  3) If old name must remain for compatibility, convert old file into a pure POINTER (no extra rules).
  4) Log change in `90__REG_CHANGELOG.md`.
- NOTES: Prefer POINTER instead of keeping two authoritative copies.
- LAST_CHANGE_ID: UE.CHG.2026-01-11.REG.NAMING.001

---

## 5) ANTI-PATTERNS (FORBIDDEN)
## REG.NAMING.FORBIDDEN.PATTERNS — strict forbidden list
- KEY: REG.NAMING.FORBIDDEN.PATTERNS
- CLASS: NAMING
- STATUS: ACTIVE
- SCOPE: repo-wide
- OWNER: SYSTEM
- PRIORITY: P1
- RAW: N/A
- RULE: Forbidden naming patterns:
  - `__` used in the middle of a name (outside `NN__` prefix)
  - mixed casing chaos in tokens (must be consistent)
  - ambiguous duplicates like `INDEX_ALL_*` variants without alias pointer
  - adding “extra meaning” via random suffixes instead of using proper tokens
- CHECK: scan folder for naming anomalies.
- FAIL: any forbidden pattern exists.
- FIX: rename via protocol; pointer if needed; log change.
- LAST_CHANGE_ID: UE.CHG.2026-01-11.REG.NAMING.001

---

## FINAL RULE (LOCK)
This registry is authoritative for naming inside `03_SYSTEM_ENTITIES`.  
All canon indexes must follow these rules.

OWNER: SYSTEM
LOCK: FIXED

--- END.
