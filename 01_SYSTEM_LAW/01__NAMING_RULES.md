# SYSTEM LAW — NAMING RULES (CANON)
FILE: 01_SYSTEM_LAW/01__NAMING_RULES.md

SCOPE: Universe Engine
LAYER: 01_SYSTEM_LAW
DOC_TYPE: LAW
LAW_TYPE: NAMING
LEVEL: L1
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.LAW.NAMING.001
OWNER: SYSTEM
ROLE: Mandatory naming formats for folders/files, numbering integrity, and pure pointer alias constraints to keep navigation deterministic and audit-compatible

CHANGE_NOTE:
- DATE: 2026-01-09
- TYPE: MAJOR
- SUMMARY: "Established executable naming rules: folder/file naming formats, numbering integrity, README conventions, allowed character rules, and pointer alias requirements."
- REASON: "System requires deterministic navigation and stable indexing; naming drift breaks canon maps and auditability."
- IMPACT: "All layers can enforce consistent structures; index entries match filenames; duplicates are redirected via pointers."
- CHANGE_ID: UE.CHG.2026-01-09.LAW.NAMING.001

---

## 0) PURPOSE (LAW)
This law standardizes naming across Universe Engine to ensure:
- canonical indexes are deterministic (index number matches filename number)
- folder structures remain navigable and auditable
- entrypoint duplicates are eliminated via pointer aliases (no rule duplication)
- compatibility with RAW-only navigation

---

## 1) DEFINITIONS (STRICT)
- FAMILY FOLDER: A governed folder that contains a set of related files (e.g., engines family, specialists family).
- NUMBER PREFIX (NN): Two-digit order number used in folder/file names (00..99).
- README FILE: A realm framing document, always numbered `00`.
- CANON ENTRYPOINT: A canonical index/README defined as SoT for a scope.
- POINTER (ALIAS): A redirect-only file pointing to canonical target; contains no rules.
- INDEX NUMBER: The ordinal number used in the canonical index list; must match filename NN.

---

## 2) NAMING RULES (MANDATORY)

### 2.1 Folder naming (MANDATORY)
**Rule (family folders):**
- Format: `NN_<FAMILY_NAME>` or `NN_<FAMILY_NAME>_<SUFFIX>`
- `NN` is two digits (00..99).
- `<FAMILY_NAME>` is `UPPER_SNAKE_CASE` (A–Z, 0–9, `_` only).
- Suffix tokens are allowed for clarity (e.g., `_ENGINES`, `_SPECIALISTS`) using the same style.

**Examples:**
- `00_GOVERNANCE_ENGINES`
- `01_CORE_ENGINES`
- `02_DOMAIN_NARRATIVE_ENGINES`
- `10_MARKETING`
- `00_KB_GOVERNANCE`

**Forbidden:**
- spaces in folder names
- mixed casing (`CamelCase`, `kebab-case`)
- non-ASCII symbols
- missing NN prefix for governed families

---

### 2.2 File naming (MANDATORY)
**Rule (governed files inside families):**
- Format: `NN__<NAME>_<TYPE>.md`
- `NN` is two digits (00..99).
- `<NAME>` is `UPPER_SNAKE_CASE`.
- `<TYPE>` is an agreed suffix token (examples below).

**Common TYPE tokens (recommended):**
- `README` for realm files (but README must still follow 00 rule; see 2.4)
- `ENG` for engines
- `SPC` for specialists
- `ORC` for orchestrators
- `CTL` for controllers
- `VAL` for validators
- `QA` for quality checks/entities
- `IDX` for indexes/registries when used inside a family
- `TEMPLATE` for templates (or `TPL` if you prefer, but be consistent)

**Examples:**
- `01__AUDIT_LOG_ENG.md`
- `04__DOC_CONTROLLER_SPC.md`
- `02__INDEX_ALL_ENGINES.md` (if index naming policy uses this)
- `00__TEMPLATE__SPC_ENTITY.md` (template style allowed if standardized by standards)

**Forbidden:**
- spaces in filenames
- non-ASCII symbols
- mismatched delimiter usage (must use `__` between NN and NAME)
- arbitrary suffix tokens not standardized

---

### 2.3 Allowed characters / casing (ABSOLUTE)
- Allowed characters in governed names: `A–Z`, `0–9`, `_`, `.`, `-` only when explicitly standardized (default: avoid `-`).
- Default casing: `UPPER_SNAKE_CASE` for semantic tokens.
- Separators:
  - Folder: `_`
  - File: `NN__` prefix then `_` within tokens

If a legacy file violates these rules, it must be migrated via canon protocol (rename + pointer alias if needed).

---

### 2.4 README rule (ABSOLUTE)
- README is not an entity instance.
- README must always be numbered `00`.

**Allowed README patterns:**
- `00__README__<SCOPE>.md`
- `00__README_<SCOPE>.md` (legacy allowed only if already used consistently in that family)

**Forbidden:**
- README numbered as 01/02/…
- multiple READMEs competing as entrypoints for the same scope (must be SoT + pointers)

---

### 2.5 Numbering integrity (ABSOLUTE)
- The index number in canonical index must equal the filename `NN`.
- Within each family, numbering starts at `01` for entities; `00` reserved for README/templates when applicable.
- Reordering numbers is a breaking structural change → must follow versioning + canon protocol.

**Example:**
If index says:
`05 — SOME ENGINE` → file must be `05__SOME_ENGINE_ENG.md`

---

### 2.6 Index naming (STANDARDIZED)
For layer-global indexes (recommended stable patterns):
- `00__INDEX__<SCOPE>.md` for layer master index
- `02__INDEX_ALL_<ENTITY_GROUP>.md` for global registries inside a layer (if standardized)
Exact naming may be further constrained by Standards; LAW requires consistency within the layer.

---

### 2.7 Pointer alias rules (ABSOLUTE)
- Any duplicate entrypoint or legacy path MUST be converted to a POINTER or removed.
- Pointer file content rule:
  - contains only a redirect reference to the canonical target (RAW link or canonical path reference per standards)
  - contains no additional rules, lists, or existence claims

When pointer is required:
- moved/renamed canon entrypoint
- duplicate entrypoint removed
- legacy alias kept for compatibility

---

## 3) BOUNDARIES (ANTI-OVERLAP)
- This law DOES: define naming formats, numbering integrity, README conventions, pointer alias constraints.
- This law DOES NOT: define UID issuance, versioning semantics, canon approval workflow.
- CONFLICT RESOLUTION: resolved by ORDER OF AUTHORITY in `00__SYSTEM_LAW.md`.

---

## 4) ENFORCEMENT (MANDATORY)

### 4.1 MANDATORY CHECKS
- Folder names follow `NN_<UPPER_SNAKE...>` pattern.
- File names follow `NN__<UPPER_SNAKE...>_<TYPE>.md` pattern.
- README files are numbered `00`.
- Index number equals filename `NN`.
- No spaces/non-ASCII in governed names.
- Pointer files contain redirect-only content.

### 4.2 FAIL CONDITIONS
- Any mismatch between canonical index numbering and filename numbering.
- README not numbered `00`.
- Multiple competing entrypoints without pointer consolidation.
- Pointer file contains rules/content beyond redirect.

### 4.3 FIX PROCEDURE
- Rename to canonical pattern.
- If rename impacts canon navigation:
  - create pointer alias at old location
  - update governing canonical index RAW links
  - log change note and follow canon protocol if canon artifacts affected
- For numbering fixes:
  - update index + filenames together (never only one side)

---

## 5) INTERFACES (RAW ONLY)
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
Naming integrity is mandatory for deterministic canon navigation.  
Any naming drift is a violation until corrected with proper renames, pointer aliases, and index updates.

OWNER: SYSTEM
LOCK: FIXED

--- END.
