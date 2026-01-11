# TPL INDEX — TEMPLATE (CANON)
FILE: 03_SYSTEM_ENTITIES/01_TPL__TEMPLATES/90__TPL__INDEX.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: TEMPLATES (TPL)
DOC_TYPE: TEMPLATE
TEMPLATE_TYPE: INDEX_TEMPLATE
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.TPL.INDEX.001
OWNER: SYSTEM
ROLE: Canonical template for building indexes (RAW-only navigation + existence rule + alias enforcement)

CHANGE_NOTE:
- DATE: 2026-01-11
- TYPE: MAJOR
- SUMMARY: "Created index template: mandatory header, existence rule, RAW-only canon map, alias rule, and lock."
- REASON: "All indexes must be deterministic and compatible with one-file navigation."
- IMPACT: "Indexes become uniform across entity classes."
- CHANGE_ID: UE.CHG.2026-01-11.TPL.INDEX.001

---

## 0) PURPOSE
This template creates an INDEX file for any folder/family/layer.

Index responsibilities:
- single source of truth for existence (within its scope)
- canonical RAW-only navigation list
- strict alias rule (no duplicate entrypoints)

---

## 1) TARGET
TARGET_CLASS: INDEX  
TARGET_FOLDER: <the folder being indexed>  
REQUIRED_PARENT_INDEX: <optional: global index that must include this index>  

---

## 2) STRUCTURE SKELETON (COPY BELOW INTO NEW INDEX FILE)
> IMPORTANT: keep the section order exactly.
> NAV must be RAW-only.

--- CUT HERE ---

# <INDEX TITLE> — INDEX (CANON)
FILE: <PATH>

SCOPE: Universe Engine
LAYER: <LAYER>
ENTITY_GROUP: <GROUP>
DOC_TYPE: INDEX
INDEX_TYPE: <TYPE>
LEVEL: <L1|L2|L3|L0 if super-index>
STATUS: <DRAFT|ACTIVE|DEPRECATED|ARCHIVED>
LOCK: <OPEN|FIXED>
VERSION: <X.Y.Z>
UID: <UID>
OWNER: SYSTEM
ROLE: <one-line: what this index controls>

CHANGE_NOTE:
- DATE: <YYYY-MM-DD>
- TYPE: <MAJOR|MINOR|PATCH>
- SUMMARY: "<what changed>"
- REASON: "<why>"
- IMPACT: "<impact>"
- CHANGE_ID: <UE.CHG.YYYY-MM-DD....>

---

## 0) PURPOSE (LAW)
Explain what this index fixes:
- existence
- ordering
- navigation

---

## 1) EXISTENCE RULE (ABSOLUTE)
- If a file is not registered here — it does not exist for this scope.
- If a file exists in repo but not listed here — NON-CANON / ignored.
- NAV works only via RAW links.

---

## 2) BASE PATH
PATH: `<BASE_PATH>` (label only)

---

## 3) HOW TO USE (OPERATIONAL)
1) Open this index.
2) Copy the needed RAW link into address bar.
3) Follow ordering rules.

---

## 4) CANON MAP (RAW-ONLY NAV)
List files in strict order:

00 — <NAME>
RAW: <RAW LINK>

01 — <NAME>
RAW: <RAW LINK>

...

---

## 5) ALIAS RULE (STRICT)
Any duplicate entrypoint/index file inside scope must be:
- deleted OR
- converted into a PURE POINTER to this canonical index.

Canonical file is:
`<CANON FILE PATH>`

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: <OPEN|FIXED>

--- END.

--- CUT HERE ---

---

## 3) INDEX QA CHECKLIST (MANDATORY)
Before marking index ACTIVE:
- All RAW links are valid (no 404)
- Ordering matches filenames (NN__ match)
- No duplicates exist (alias rule enforced)
- This index is referenced by parent index if required

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED

--- END.
