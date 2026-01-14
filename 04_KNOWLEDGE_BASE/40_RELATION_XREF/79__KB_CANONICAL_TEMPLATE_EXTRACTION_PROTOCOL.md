# KB — CANONICAL TEMPLATE EXTRACTION PROTOCOL (CANON)
FILE: 04_KNOWLEDGE_BASE/40_RELATION_XREF/79__KB_CANONICAL_TEMPLATE_EXTRACTION_PROTOCOL.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: KB_MODULE
KB_TYPE: PROTOCOL
LEVEL: L2
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.PROC.TPL_EXTRACT.079
OWNER: SYSTEM
ROLE: Deterministic protocol for extracting reusable templates from packs into the shared canonical template library: selection criteria, UID assignment, migration steps, deprecation/pointer handling, and audit/validation requirements.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created protocol to extract canonical templates from packs and migrate usage safely."
- REASON: "Templates should be reused and standardized; extraction must be controlled to prevent duplication and drift."
- IMPACT: "Cleaner template library, fewer duplicates, and consistent artifacts across domains."
- CHANGE_ID: UE.CHG.2026-01-14.KB.PROC.079

---

## 0) PURPOSE (KB)
Extract a template into the shared library without breaking:
- determinism
- bindings
- indexing
- auditability

---

## 1) TRIGGERS (WHEN TO EXTRACT)
Extract if:
- template is used by 2+ packs or entity classes
- template is generic (capability card, gate, checklist, failure mode)
- template affects quality gates or trace discipline
- divergence between pack copies is appearing

Do not extract:
- highly domain-specific templates that are unlikely to be reused

---

## 2) INPUTS / OUTPUTS
INPUTS:
- Source pack UID(s) where template lives
- Template function name (what it does)
- Domain impact analysis (who uses it)

OUTPUTS:
- New canonical template module (with UID)
- Updated packs referencing it (UID-only)
- Deprecated old duplicates or reduced to pointer-only
- Audit record (if high impact)
- Release notes (if many packs affected)

---

## 3) EXTRACTION FLOW (DETERMINISTIC)
### Step 1 — Identify template function
- Define what the template produces and how it is used.
- Confirm it is generic enough.

### Step 2 — Check for existing canon template
- If canon exists:
  - align pack usage to canon
  - do not create a duplicate
- If no canon:
  - continue

### Step 3 — Create canonical template module
- Choose a stable name
- Assign UID (per naming/uid conventions)
- Include:
  - purpose
  - copy block
  - rules and hard fails (when applicable)
  - related UIDs (pack QA, template library policy)

### Step 4 — Register new template in master index
- Add it to the KB master index.
- Mark as TEMPLATE type.

### Step 5 — Update packs
For each affected pack:
- Replace embedded copy with:
  - XREF to canonical template UID
  - or a minimal pointer label referencing it
- Keep pack internal template index consistent.

### Step 6 — Resolve old duplicates
If packs still contain old copies:
- either remove them, or
- mark them as embedded variants with explicit scope boundaries
If a standalone duplicate template module exists:
- deprecate it pointer-first to the canonical template UID

### Step 7 — Validate
- Run pack QA gates (template completeness still passes)
- Run master index integrity checks
- Run trace review if outputs change

### Step 8 — Audit & Release Notes
Audit is mandatory if:
- canon template affects many packs
- the template changes behavior (gates/fields)
Release notes required if wide impact.

---

## 4) MIGRATION RULES
- Do not break entity bindings: packs remain the bound units; templates are referenced.
- Canon template changes should be versioned.
- If template change affects many outputs, recertification may be required.

---

## 5) HARD FAIL CONDITIONS
FAIL IF:
- extraction creates a second canon template for same function
- packs are updated with URL/PATH references instead of UID-only XREF
- template is moved without index registration
- old duplicates remain authoritative and conflicting
- audit is skipped for high-impact extraction

---

## 6) RELATED (UID-ONLY)
XREF:
- XREF: UE.KB.POL.TEMPLATE_LIBRARY.078 | WHY: defines what is canonical and reuse rules
- XREF: UE.KB.STD.COMP_PACK_TPL_INDEX.049 | WHY: packs must keep template index consistent
- XREF: UE.KB.CHK.MASTER_INDEX_INTEGRITY.071 | WHY: index must remain stable after extraction
- XREF: UE.KB.CHK.TRACE_REVIEW.068 | WHY: trace integrity after behavior changes

--- END.
