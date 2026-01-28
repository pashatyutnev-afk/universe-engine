# KB — INDEX DUPLICATE PREVENTION RULE (CANON)
FILE: 04_KNOWLEDGE_BASE/40_RELATION_XREF/72__KB_INDEX_DUPLICATE_PREVENTION_RULE.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: KB_MODULE
KB_TYPE: RULE
LEVEL: L2
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.RULE.INDEX_NO_DUPES.072
OWNER: SYSTEM
ROLE: Enforces single-source-of-truth for KB navigation/existence: prevents duplicate entrypoints and duplicate “same meaning” modules; defines when pointer/alias is allowed and how duplicates must be resolved.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created rule to prevent duplicate KB index entrypoints and duplicate truths; mandates pointer-only aliasing."
- REASON: "Duplicates break determinism and cause conflicting behavior across entity runs."
- IMPACT: "One truth, stable navigation, and safe aliasing for convenience."
- CHANGE_ID: UE.CHG.2026-01-14.KB.RULE.072

---

## 0) PURPOSE (KB)
Ensure KB remains deterministic:
- one master index for navigation/existence
- one canonical module per meaning/function
- aliases are pointer-only

---

## 1) ABSOLUTE RULES
R1 — Single master index
- Only one file is the navigation/existence SoT for KB.

R2 — No duplicate meaning modules
- Do not create a second module that repeats the same rules/function as an existing canon.

R3 — Alias allowed only as pointer-only
- If you need a numbered slot or backward compatibility, create a POINTER/ALIAS module that references the canon UID.

R4 — No “shadow indexes”
- Sub-indexes must not carry RAW link registries as navigation authority.

---

## 2) DUPLICATE TYPES
DUP_TYPE.A — Duplicate entrypoint
- Multiple master-like indexes exist.

DUP_TYPE.B — Duplicate navigation link
- Same file registered multiple times with different labels.

DUP_TYPE.C — Duplicate meaning (two rulesets)
- Two modules describe the same function with slight variations.

DUP_TYPE.D — Duplicate authority via pointer misuse
- Pointer contains rules or is treated as canon.

---

## 3) DETECTION RULES
A suspected duplicate exists if:
- two files share same ROLE/purpose
- two modules are used interchangeably
- multiple entries point to same RAW target
- “helper index” begins behaving as navigation SoT

---

## 4) RESOLUTION PROCEDURE (DETERMINISTIC)
### 4.1 Duplicate entrypoint (Type A)
- Choose the canonical master index.
- Convert others to POINTER-only (or delete).

### 4.2 Duplicate navigation link (Type B)
- Keep one canonical entry.
- Remove redundant entries.
- If needed, keep pointer module, not duplicate registration.

### 4.3 Duplicate meaning modules (Type C)
- Pick one canon module (best quality).
- Deprecate the other(s) and point to canon.
- Update bindings/scorecards if needed.

### 4.4 Pointer misuse (Type D)
- Strip content to pointer-only.
- Ensure pointer is labeled POINTER in index.

---

## 5) PASS/FAIL
PASS IF:
- only one master index exists
- no duplicate meaning modules are ACTIVE simultaneously
- pointers are pointer-only and labeled
- sub-indexes are orientation-only

FAIL IF:
- two “master” entrypoints exist
- duplicate meaning modules both treated as canon
- pointer contains executable rules

---

## 6) HARD FAIL CONDITIONS
FAIL IF:
- KB navigation depends on more than one index file
- duplicate meaning modules exist with competing authority
- pointer/alias module contains rules or procedures
- RAW link registries appear outside master index as navigation authority

---

## 7) RELATED (UID-ONLY)
XREF:
- XREF: UE.KB.POL.POINTERS_ALIASES.028 | WHY: defines pointer-only constraints and marking
- XREF: UE.KB.STD.DEPRECATION_POINTER.007 | WHY: deprecating duplicates requires replacement flow
- XREF: UE.KB.CHK.MASTER_INDEX_INTEGRITY.071 | WHY: integrity checklist detects duplicates/entrypoint drift

--- END.
