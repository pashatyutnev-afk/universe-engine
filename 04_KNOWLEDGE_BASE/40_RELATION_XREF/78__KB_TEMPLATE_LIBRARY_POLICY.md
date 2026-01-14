# KB — TEMPLATE LIBRARY POLICY (CANON)
FILE: 04_KNOWLEDGE_BASE/40_RELATION_XREF/78__KB_TEMPLATE_LIBRARY_POLICY.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: KB_MODULE
KB_TYPE: POLICY
LEVEL: L2
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.POL.TEMPLATE_LIBRARY.078
OWNER: SYSTEM
ROLE: Defines how KB templates are stored, reused, and kept canonical: prevents duplication across competence packs, sets rules for template extraction into the shared library, and enforces pointer-only aliasing where needed.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created template library policy: canonical templates, reuse rules, and duplication prevention."
- REASON: "Templates are core operational artifacts; without a library policy, packs duplicate and drift, hurting consistency."
- IMPACT: "Higher reuse, fewer duplicates, more consistent outputs across entities."
- CHANGE_ID: UE.CHG.2026-01-14.KB.POL.078

---

## 0) PURPOSE (KB)
Define how to manage templates:
- what should be a shared canonical template
- what can stay embedded inside a pack
- how to migrate templates into the library
- how to prevent duplicate templates

---

## 1) ABSOLUTE RULES
R1 — Prefer reuse over duplication
- If a canonical template exists, packs should reference it (or embed a pointer label), not rewrite it.

R2 — Canonical templates are shared and stable
- Canonical templates should be ACTIVE + FIXED when mature.

R3 — Embedded templates are allowed for domain-specific needs
- But they should follow canonical structure and naming.

R4 — No “two canon templates” for the same function
- If duplicates arise, pick one canon and deprecate the other.

---

## 2) WHAT QUALIFIES AS A CANONICAL TEMPLATE
A template should be extracted to the library if:
- used by 2+ packs or entity classes
- is generic (capability card, gate card, checklist card, failure mode card)
- is foundational to QA/validation/trace
- benefits from being standardized across domains

Domain-specific templates may remain in packs.

---

## 3) TEMPLATE STORAGE STRATEGY
Three levels:
- Level A: Shared Canon Templates (library)
- Level B: Domain Templates (domain folder)
- Level C: Pack-Embedded Templates (inside pack)

Rule:
- Promote upward (C→B→A) when reuse increases.

---

## 4) MIGRATION PROCESS (DETERMINISTIC)
When a pack contains a reusable template:
Step 1: Identify the template function.
Step 2: Check if canon template already exists.
- If yes: align pack template to canon (or replace with reference).
- If no: extract into library as a new template module.
Step 3: Update packs to reference the canon template.
Step 4: Audit + release notes if many packs change.

---

## 5) REFERENCING RULES
- If template is standalone KB module:
  - reference via UID-only XREF
- If template is embedded:
  - label as TPL-XX and keep consistent structure

Forbidden:
- URLs/PATH in template references
- copying canonical template into many packs without declaring the canon UID

---

## 6) QA RULES (PASS/FAIL)
PASS IF:
- shared templates are stable and reused
- packs do not duplicate generic templates unnecessarily
- canonical template changes are versioned and audited when high impact

FAIL IF:
- multiple templates exist for the same function without deprecation resolution
- packs diverge from canonical template structure without reason
- template references use URL/PATH

---

## 7) HARD FAIL CONDITIONS
FAIL IF:
- two ACTIVE canonical templates exist for the same function
- canonical template is edited without version/change note
- mass template drift occurs without audit trail

---

## 8) RELATED (UID-ONLY)
XREF:
- XREF: UE.KB.STD.COMP_PACK_TPL_INDEX.049 | WHY: packs must maintain template index and categories
- XREF: UE.KB.POL.POINTERS_ALIASES.028 | WHY: aliases/pointers for template migration and numbering slots
- XREF: UE.KB.POL.AUDIT_TRAIL.058 | WHY: canonical template changes may require audit events

--- END.
