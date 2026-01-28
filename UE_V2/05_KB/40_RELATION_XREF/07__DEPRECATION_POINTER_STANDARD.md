# KB — DEPRECATION & POINTER STANDARD (CANON)
FILE: 04_KNOWLEDGE_BASE/40_RELATION_XREF/07__DEPRECATION_POINTER_STANDARD.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: KB_MODULE
KB_TYPE: STANDARD
LEVEL: L2
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.STD.DEPRECATION_POINTER.007
OWNER: SYSTEM
ROLE: Canonical procedure to deprecate KB modules safely: how to mark old modules, create pointer stubs, update REL graph, and maintain master-index integrity. Prevents duplicate truths and navigation drift.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Introduced canonical deprecation and pointer standard for KB modules."
- REASON: "KB must remain ideal; duplicates and conflicting guidance destroy determinism and entity quality."
- IMPACT: "Safe replacement flow: new canon replaces old, old becomes a pointer; graphs remain consistent."
- CHANGE_ID: UE.CHG.2026-01-14.KB.STD.007

---

## 0) PURPOSE (KB)
Define the only allowed way to replace/retire KB modules:
- choose canonical successor
- deprecate the old module
- keep a pointer for traceability
- update relations and the master index

This standard does not provide navigation links; master-index remains the navigation hub.

---

## 1) ABSOLUTE RULES
1.1 SINGLE SOURCE OF TRUTH
- For any function, there must be exactly one active canonical module.

1.2 NO SILENT REPLACEMENT
- Deprecation must be explicit in the old module and linked to the new module via UID.

1.3 UID-ONLY XREF
- Pointer references must use UID-only rules (no URL/PATH inside XREF blocks).

---

## 2) WHEN TO DEPRECATE
Deprecate when:
- D1: duplicate modules cover the same function
- D2: old module has incorrect/unsafe guidance
- D3: structure changes require a new versioned canonical module
- D4: the module is split into smaller atomic modules

Do not deprecate when:
- the change is a minor edit that fits versioning within the same module

---

## 3) DEPRECATION FLOW (DETERMINISTIC)
Step 1 — Select successor (NEW_CANON)
- Create/identify the replacement module with a new UID.
- Ensure it is complete and registered in master-index.

Step 2 — Mark old module as DEPRECATED
- Keep the file, but convert it into a pointer-first document:
  - add DEPRECATION banner at the top
  - remove/lock the old guidance if it can mislead
  - provide the pointer target UID

Step 3 — Update relationship graph
- New module:
  - REL: supersedes -> <OLD_UID> | WHY: replacement
- Old module:
  - REL: deprecated_by -> <NEW_UID> | WHY: new canon

Step 4 — Update master-index
- Keep both entries (for existence/audit), but mark old as DEPRECATED in the title/notes.

Step 5 — QA audit
- Confirm only one ACTIVE canon exists for the function.

---

## 4) POINTER DOCUMENT STANDARD (OLD MODULE)
A deprecated module must contain (minimum):

### 4.1 Header changes
- STATUS: DEPRECATED
- LOCK: FIXED
- VERSION: increment patch (or set new patch)
- CHANGE_NOTE: describes the deprecation

### 4.2 Deprecation banner (mandatory)
DEPRECATED:
- Replaced by: <NEW_UID>
- Reason: <short>
- Effective date: <date>

### 4.3 Pointer-only body
- Provide:
  - what this used to cover (1–3 lines)
  - where to go now (NEW_UID)
  - migration notes (optional, short)

Prohibited:
- Keeping full old procedures that may be used accidentally.
  (If historical content must remain, move it to an archive realm; the operational module must remain pointer-first.)

---

## 5) TEMPLATE — DEPRECATION BANNER (COPY)
DEPRECATED:
- REPLACED_BY_UID: <NEW_UID>
- REASON: <short>
- EFFECTIVE_DATE: YYYY-MM-DD

---

## 6) TEMPLATE — POINTER BODY (COPY)
THIS MODULE IS DEPRECATED.
- Previous scope: <1–2 lines>
- Use instead: <NEW_UID>
- Migration notes: <optional>

REL:
- REL: deprecated_by -> <NEW_UID> | WHY: new canon module

XREF:
- XREF: <NEW_UID> | WHY: replacement module

---

## 7) QA GATES (PASS/FAIL)
PASS IF:
- new module is ACTIVE and complete
- old module is clearly marked DEPRECATED
- old module points to new via UID
- REL supersedes/deprecated_by pair exists
- master-index lists both with clear deprecation label
- no other ACTIVE module duplicates the same function

FAIL IF:
- two active modules exist for same function
- deprecated module still contains full runnable procedure (risk of accidental use)
- missing pointer UID or missing REL pair
- master-index not updated

---

## 8) EXAMPLES
Example (good):
- New: REL supersedes old
- Old: STATUS DEPRECATED, banner + pointer to NEW_UID, REL deprecated_by, XREF NEW_UID

Example (bad):
- Old and new both ACTIVE with similar content
- No banner, no pointer, no index update

---

## 9) RELATED (UID-ONLY)
XREF:
- XREF: UE.KB.DICT.REL_TYPES.004 | WHY: relation vocabulary (supersedes/deprecated_by)
- XREF: UE.KB.DICT.XREF_RULES.005 | WHY: UID-only reference policy
- XREF: UE.KB.TPL.REL_GRAPH.006 | WHY: relation graph template for consistent linking

--- END.
