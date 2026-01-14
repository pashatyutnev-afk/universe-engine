# KB — DOMAIN TEMPLATE LIBRARY README (CANON)
FILE: 04_KNOWLEDGE_BASE/40_RELATION_XREF/80__KB_DOMAIN_TEMPLATE_LIBRARY_README.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: KB_MODULE
KB_TYPE: README
LEVEL: L2
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.README.DOMAIN_TPL_LIB.080
OWNER: SYSTEM
ROLE: Explains how domain-level template libraries should be used and maintained: what belongs at domain level vs shared canonical library, how to reference templates (UID-only), and when to promote templates to canon.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created README for domain template libraries and promotion to canonical templates."
- REASON: "Templates exist at different reuse levels; without clarity, teams duplicate or mislabel templates as canon."
- IMPACT: "Cleaner template organization, safer reuse, and controlled promotion to canon."
- CHANGE_ID: UE.CHG.2026-01-14.KB.README.080

---

## 0) PURPOSE (KB)
Domain template libraries store templates that:
- are reused within a single domain
- may later be promoted to canonical shared templates

This README clarifies:
- boundaries between domain templates and shared canon
- referencing rules
- promotion triggers

---

## 1) TEMPLATE LEVELS (RECAP)
- Shared Canon Templates: used across domains and entity classes
- Domain Templates: reused within one domain
- Pack-Embedded Templates: local to one pack

Rule:
- Promote upward (embedded → domain → canon) when reuse grows.

---

## 2) WHAT BELONGS IN DOMAIN TEMPLATE LIBRARIES
Belongs:
- domain-specific gate cards
- domain-specific prompt cards
- domain-specific checklists
- domain-specific scoring rubrics
- domain-specific examples formats

Does NOT belong:
- universal trace blocks
- generic capability/failure-mode cards (those should be canonical)

---

## 3) HOW TO REFERENCE DOMAIN TEMPLATES
- If a domain template is a standalone KB module:
  - reference by UID-only XREF
- Packs may also embed a copy, but must:
  - label it as a variant
  - not contradict the domain template

Forbidden:
- URL/PATH references
- duplicating the same domain template across many packs without declaring a shared UID

---

## 4) WHEN TO PROMOTE A DOMAIN TEMPLATE TO CANON
Promote when:
- template is used by 2+ domains
- template becomes foundational to QA or validation
- template function is generic (not domain-specific)
- divergence between domain copies is detected

Follow the canonical extraction protocol.

---

## 5) MAINTENANCE RULES
- Keep domain template library coherent:
  - clear scope boundaries
  - consistent naming
  - avoid duplicates
- Significant changes require:
  - version bump
  - audit record if wide impact

---

## 6) HARD FAIL CONDITIONS
FAIL IF:
- domain template is treated as shared canon without promotion
- canonical templates are duplicated inside domain library as competing authority
- domain template references use URL/PATH
- multiple domain templates duplicate the same function without deprecation resolution

---

## 7) RELATED (UID-ONLY)
XREF:
- XREF: UE.KB.POL.TEMPLATE_LIBRARY.078 | WHY: overall template library policy
- XREF: UE.KB.PROC.TPL_EXTRACT.079 | WHY: promotion/extraction protocol
- XREF: UE.KB.POL.POINTERS_ALIASES.028 | WHY: aliasing for migrations without duplicate truths

--- END.
