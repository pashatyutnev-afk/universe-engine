# KB — SOURCE RECORDS REGISTRY STANDARD (WORLD KNOWLEDGE) (CANON)
FILE: 04_KNOWLEDGE_BASE/40_RELATION_XREF/32__KB_SOURCE_RECORDS_REGISTRY_STANDARD.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: KB_MODULE
KB_TYPE: STANDARD
LEVEL: L2
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.STD.SOURCE_RECORDS.032
OWNER: SYSTEM
ROLE: Canonical standard for recording and managing external "world knowledge" sources as stable SOURCE RECORDS (registry items) with controlled provenance, confidence labeling, refresh rules, and anti-drift discipline.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Defined SOURCE RECORD schema and registry rules for external sources (papers, standards, docs, books, reputable references)."
- REASON: "World knowledge must be ingested into KB with stable provenance; otherwise entities drift into ad-hoc web guessing."
- IMPACT: "KB modules can cite stable SOURCE_RECORD_UIDs instead of unstable URLs; enables audits and controlled updates."
- CHANGE_ID: UE.CHG.2026-01-14.KB.STD.032

---

## 0) PURPOSE (KB)
Define how external sources are captured as stable SOURCE RECORDS so that:
- KB modules can reference sources deterministically (via SOURCE_RECORD_UID)
- claims can be audited and refreshed
- URL drift does not break provenance
- confidence and verification status are explicit

This standard defines source metadata, not navigation.

---

## 1) ABSOLUTE RULES
R1 — SOURCE_RECORD_UID is the stable key
- External provenance inside KB should be referenced as SOURCE_RECORD_UID (not as raw URLs in XREF).

R2 — Prefer stable identifiers over URLs
- Use DOI/ISBN/standard number/spec version as the primary identifier when available.

R3 — URLs are metadata only (optional)
- If recorded, URLs are for human context only, not for navigation or authority by themselves.
- Never use URLs as XREF targets.

R4 — No large verbatim copying
- Source records store metadata; KB modules store synthesized methods, not copied pages.

---

## 2) SOURCE RECORD TYPES (ENUM)
SR_TYPE:
- STANDARD (ISO/IEC/W3C/vendor specs)
- OFFICIAL_DOC (vendor official documentation)
- PAPER (peer-reviewed paper / preprint)
- BOOK (textbook/handbook)
- COURSE (curated course/material)
- ARTICLE (reputable publication article)
- COMMUNITY (blog/forum; lead discovery only; low authority)

Rule:
- Prefer STANDARD / OFFICIAL_DOC / PAPER when possible.

---

## 3) SOURCE RECORD SCHEMA (REQUIRED FIELDS)
Each SOURCE RECORD must include:

### 3.1 Identity
- SOURCE_RECORD_UID: (unique, stable)
- SR_TYPE: (enum)
- TITLE:
- AUTHORS:
- PUBLISHER_OR_ORG:
- YEAR:

### 3.2 Stable identifiers (as applicable)
- DOI: (if paper)
- ISBN: (if book)
- STANDARD_ID: (e.g., "ISO 9001:2015", "W3C WCAG 2.2")
- DOC_VERSION: (vendor doc version or release tag)
- EDITION: (if applicable)

### 3.3 Retrieval metadata
- DATE_ACCESSED: YYYY-MM-DD
- ACCESS_CONTEXT: (web / pdf / print / repo)
- URL: (optional; metadata only)
- ARCHIVE_METHOD: (optional; e.g., "pdf saved", "snapshot", "hash")
- ARCHIVE_HASH: (optional)

### 3.4 Trust labeling
- AUTHORITY_TIER: T0..T4 (from world-sources policy)
- CLAIM_CLASS: FACT | HEURISTIC | OPINION | HYPOTHESIS (default for this source)
- CONFIDENCE_DEFAULT: HIGH | MED | LOW

### 3.5 Notes
- SHORT_SUMMARY: (1–3 lines what it is)
- SCOPE_LIMITS: (what it does NOT cover)
- LICENSE_NOTES: (if relevant)

---

## 4) REGISTRY FORMAT (TEXT RECORD TEMPLATE)
SOURCE RECORD (TEMPLATE):
- SOURCE_RECORD_UID:
- SR_TYPE:
- TITLE:
- AUTHORS:
- PUBLISHER_OR_ORG:
- YEAR:
- DOI:
- ISBN:
- STANDARD_ID:
- DOC_VERSION:
- EDITION:
- DATE_ACCESSED:
- ACCESS_CONTEXT:
- URL:
- ARCHIVE_METHOD:
- ARCHIVE_HASH:
- AUTHORITY_TIER:
- CLAIM_CLASS:
- CONFIDENCE_DEFAULT:
- SHORT_SUMMARY:
- SCOPE_LIMITS:
- LICENSE_NOTES:

Rule:
- Unknown fields may be left blank, but identity + tier + accessed date must exist.

---

## 5) HOW KB MODULES USE SOURCE RECORDS (POLICY)
KB modules that rely on world knowledge should include a provenance section (format is up to your KB module schema), but must reference:
- SOURCE_RECORD_UID(s)
- claim-level notes when needed (confidence/limitations)

Important:
- This does NOT replace XREF UID-only rules.
- SOURCE_RECORD_UID is not the same as KB module UID.

---

## 6) REFRESH & STALENESS RULES
Some sources change rapidly (official docs, web pages).
Define:
- REFRESH_INTERVAL_DAYS (recommended):
  - STANDARD/PAPER/BOOK: 365+ (or "none")
  - OFFICIAL_DOC: 90–180
  - ARTICLE: 90–180
  - COMMUNITY: 30 (lead-only)
Staleness trigger:
- if DATE_ACCESSED older than interval and source is used in ACTIVE KB module → mark for refresh.

---

## 7) CONTRADICTION HANDLING
If two SOURCE RECORDS disagree:
- record both SOURCE_RECORD_UIDs
- elevate the higher AUTHORITY_TIER source as primary
- mark contested claims as HYPOTHESIS until resolved
- do not promote affected KB module to ACTIVE until resolved (for high-stakes areas)

---

## 8) HARD FAIL CONDITIONS
FAIL IF:
- a KB module claims “sourced” knowledge but no SOURCE_RECORD_UID exists
- SOURCE RECORD lacks DATE_ACCESSED + AUTHORITY_TIER
- COMMUNITY source is treated as sole authority for critical claims
- URLs are used as XREF targets or as authority without identifiers
- large verbatim text is stored in KB instead of a synthesized method

---

## 9) EXAMPLES (GENERIC)
Example A — Paper
- SOURCE_RECORD_UID: UE.SRC.PAPER.0001
- SR_TYPE: PAPER
- DOI: 10.xxxx/xxxx
- AUTHORITY_TIER: T2
- CONFIDENCE_DEFAULT: HIGH

Example B — Vendor official docs
- SOURCE_RECORD_UID: UE.SRC.DOC.0007
- SR_TYPE: OFFICIAL_DOC
- DOC_VERSION: vX.Y
- DATE_ACCESSED: 2026-01-14
- AUTHORITY_TIER: T2
- REFRESH: 180 days

---

## 10) RELATED (UID-ONLY)
XREF:
- XREF: UE.KB.POL.WORLD_SOURCES.030 | WHY: defines tiers and ingestion rules for world knowledge
- XREF: UE.KB.POL.STATUS_LOCK.029 | WHY: promotion to ACTIVE depends on provenance quality
- XREF: UE.KB.TOPIC.META.QA_AUDIT.005 | WHY: audit checks should validate provenance presence

--- END.
