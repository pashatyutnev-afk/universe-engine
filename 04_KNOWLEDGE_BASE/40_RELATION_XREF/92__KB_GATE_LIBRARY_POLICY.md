# KB — GATE LIBRARY POLICY (CANON)
FILE: 04_KNOWLEDGE_BASE/40_RELATION_XREF/92__KB_GATE_LIBRARY_POLICY.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: KB_MODULE
KB_TYPE: POLICY
LEVEL: L2
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.POL.GATE_LIBRARY.092
OWNER: SYSTEM
ROLE: Defines how the KB gate library is organized, curated, and kept canonical: duplicate prevention, key gate criteria, relationships to skill tags, packs, examples, and certification workflows.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created gate library policy: organization, key gate criteria, and duplicate/conflict prevention."
- REASON: "Gates are the backbone of QA and certification; without library policy they duplicate, conflict, and become subjective."
- IMPACT: "Stable gate set, consistent QA across domains, and safer entity certification."
- CHANGE_ID: UE.CHG.2026-01-14.KB.POL.092

---

## 0) PURPOSE (KB)
Define rules for the gate library:
- what a gate is
- what makes a gate “key”
- how gates are stored and referenced
- how to prevent duplicates and conflicts
- how gates link to tags, packs, examples, and certification

---

## 1) ABSOLUTE RULES
R1 — One canon gate per function
- If two gates check the same thing, pick one canon and deprecate the other.

R2 — Gates must be measurable
- Use gate definition standard.

R3 — UID-only references
- Packs and examples link to gates via UIDs only.

R4 — Key gates require exemplars
- Key gates must be calibrated via exemplar sets.

---

## 2) WHAT IS A KEY GATE
A gate is KEY if any:
- used in certification (entity/packs)
- used in readiness gates
- used frequently in domain QA
- has high risk if wrong (quality/safety/regression)

Key gate implications:
- must have exemplar sets (GOOD/BAD/BORDERLINE)
- must be included in calibration protocol
- must be versioned carefully and audited on major changes

---

## 3) ORGANIZATION (ORIENTATION)
Recommend organization by:
- domain
- tag clusters
- gate type:
  - QUALITY (output quality)
  - CONSISTENCY (continuity/contradiction)
  - UNIQUENESS (repeat/collision)
  - TECHNICAL (format/constraints)
  - COMPLIANCE (policy/trace)

No URLs/RAW in policy; navigation is via master index.

---

## 4) DUPLICATE & CONFLICT PREVENTION
Detect duplicates when:
- two gates have same target output and same criteria
- two gates are used interchangeably by entities

Resolution:
- select best-quality gate as canon
- deprecate others pointer-first
- update packs/examples to reference canon gate UID

Conflicts:
- if gates contradict, use contradiction protocol (severity-based)

---

## 5) LINKAGE REQUIREMENTS
Each gate should link to:
- SKILL_TAGS (canonical)
- competence packs that use it (optional record)
- exemplar set template records for calibration (recommended)

Examples must link back to gate UIDs.

---

## 6) MAJOR CHANGE DISCIPLINE
For key gates:
- major changes require audit record
- may require release notes if many entities affected
- recertification may be required

---

## 7) HARD FAIL CONDITIONS
FAIL IF:
- non-measurable vague gates exist as authority
- duplicates exist without deprecation resolution
- key gates used without exemplar calibration
- examples link to gates but gates are not stable/defined

---

## 8) RELATED (UID-ONLY)
XREF:
- XREF: UE.KB.STD.GATE_DEF.088 | WHY: defines canonical gate structure and measurability
- XREF: UE.KB.RULE.GATE_EXAMPLE_BIND.090 | WHY: key gates require exemplar sets
- XREF: UE.KB.PROC.DOMAIN_QA_CALIB.087 | WHY: calibration protocol for consistent judgment
- XREF: UE.KB.PROC.CONTRADICTIONS.065 | WHY: resolve conflicting gate definitions
- XREF: UE.KB.POL.AUDIT_TRAIL.058 | WHY: key gate changes must be auditable

--- END.
