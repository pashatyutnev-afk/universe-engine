# KB — PROVENANCE BLOCK TEMPLATE (WORLD KNOWLEDGE) (CANON)
FILE: 04_KNOWLEDGE_BASE/40_RELATION_XREF/33__KB_PROVENANCE_BLOCK_TEMPLATE.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: KB_MODULE
KB_TYPE: TEMPLATE
LEVEL: L2
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.TPL.PROVENANCE_BLOCK.033
OWNER: SYSTEM
ROLE: Canonical template to document provenance for KB modules that ingest world knowledge: source record references, claim labeling (FACT/HEURISTIC/etc.), confidence, and refresh notes—without violating UID-only XREF rules.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created standard provenance block template for KB modules using world sources."
- REASON: "To use global human knowledge safely, KB must store stable provenance and claim confidence without leaking URLs into XREF."
- IMPACT: "KB modules become auditable and refreshable; entities can trust what is FACT vs HEURISTIC."
- CHANGE_ID: UE.CHG.2026-01-14.KB.TPL.033

---

## 0) PURPOSE (KB)
Provide a copy-paste provenance section for KB modules that rely on external sources:
- references sources via SOURCE_RECORD_UID
- labels claims as FACT/HEURISTIC/OPINION/HYPOTHESIS
- records confidence and refresh interval
- prevents URL/PATH leakage into XREF

This template is optional unless a module ingests world knowledge.

---

## 1) PROVENANCE BLOCK (COPY)
## PROVENANCE (WORLD KNOWLEDGE)
### Sources (SOURCE_RECORD_UID)
- SRC: <SOURCE_RECORD_UID> | TYPE: <SR_TYPE> | AUTHORITY_TIER: <T0..T4> | DATE_ACCESSED: YYYY-MM-DD | CONF_DEFAULT: <HIGH/MED/LOW>

### Claims (label each)
- CLAIM: <short statement>
  - CLASS: FACT | HEURISTIC | OPINION | HYPOTHESIS
  - CONFIDENCE: HIGH | MED | LOW
  - SUPPORTED_BY: <SOURCE_RECORD_UID list>
  - NOTES: <limits/assumptions>

### Refresh
- REFRESH_INTERVAL_DAYS: <number or NONE>
- NEXT_REVIEW_BY: YYYY-MM-DD (optional)
- STALENESS_TRIGGER: <what makes this outdated>

### Contradictions (if any)
- CONFLICT: <short description>
  - SRC_A: <SOURCE_RECORD_UID>
  - SRC_B: <SOURCE_RECORD_UID>
  - RESOLUTION: <tier-based decision or "UNRESOLVED">
  - ACTION: <what to validate next>

---

## 2) RULES (STRICT)
- Use SOURCE_RECORD_UID, not URLs, inside PROVENANCE.
- Do not place SOURCE_RECORD_UIDs into XREF blocks (XREF is for KB module UIDs).
- PROVENANCE is for external provenance only.
- If claims are HYPOTHESIS, module must not be promoted to ACTIVE for high-stakes usage.

---

## 3) MINIMAL VERSION (IF ONLY ONE SOURCE)
## PROVENANCE (WORLD KNOWLEDGE)
- SRC: <SOURCE_RECORD_UID> | DATE_ACCESSED: YYYY-MM-DD
- CLAIMS: mostly HEURISTIC unless verified FACT
- REFRESH_INTERVAL_DAYS: <number or NONE>

---

## 4) HARD FAIL CONDITIONS
FAIL IF:
- module uses world knowledge but has no provenance block
- claims are presented as FACT without any SOURCE_RECORD_UID support
- URLs are inserted into XREF or used as authority
- contradictions are ignored for critical claims

---

## 5) RELATED (UID-ONLY)
XREF:
- XREF: UE.KB.STD.SOURCE_RECORDS.032 | WHY: defines SOURCE_RECORD schema and registry rules
- XREF: UE.KB.POL.WORLD_SOURCES.030 | WHY: governs ingestion and authority tiers
- XREF: UE.KB.DICT.XREF_RULES.005 | WHY: prevents URL/PATH leakage into XREF

--- END.
