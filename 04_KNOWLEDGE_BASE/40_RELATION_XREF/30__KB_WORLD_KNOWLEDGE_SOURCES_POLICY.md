# KB — WORLD KNOWLEDGE SOURCES POLICY (CANON)
FILE: 04_KNOWLEDGE_BASE/40_RELATION_XREF/30__KB_WORLD_KNOWLEDGE_SOURCES_POLICY.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: KB_MODULE
KB_TYPE: POLICY
LEVEL: L2
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.POL.WORLD_SOURCES.030
OWNER: SYSTEM
ROLE: Define how "world knowledge" (internet, standards, books, courses) is used to build the Knowledge Base while keeping entity execution deterministic, non-fiction, and audit-compatible.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Established policy for acquiring and embedding world knowledge into KB (source tiers, capture rules, verification, and hard fails)."
- REASON: "Quality of entities depends on best-known human knowledge, but must be transformed into stable KB modules (not live web guessing)."
- IMPACT: "Entities get high-quality expertise via KB modules with controlled provenance and deterministic usage."
- CHANGE_ID: UE.CHG.2026-01-14.KB.POL.030

---

## 0) PURPOSE (KB)
This policy makes world knowledge usable without breaking determinism:
- World knowledge is allowed and encouraged for KB construction.
- Entities should execute from KB modules, not from ad-hoc web browsing.
- No fantasy: facts must be sourced, uncertain items must be labeled.

---

## 1) CORE PRINCIPLE (ABSOLUTE)
P1 — World knowledge is "ingested" into KB
- External knowledge must be converted into KB modules (standards/dictionaries/playbooks) before being treated as operational knowledge.

P2 — Determinism over improvisation
- Live browsing may be used for research, but final operational guidance must exist as KB modules registered in the KB master index.

P3 — Non-fiction rule
- No invented facts, no made-up citations, no fabricated standards.

---

## 2) SOURCE TIERS (ORDER OF TRUST)
T0 — Internal Canon (RAW)
- System Law / Standards / System Entities (RAW-indexed) override everything.

T1 — KB ACTIVE modules
- Default operational source for entities.

T2 — Primary external sources
- Official standards bodies, official documentation, academic papers, authoritative handbooks.

T3 — Secondary external sources
- High-quality textbooks, reputable industry references, curated courses.

T4 — Tertiary / community sources
- Blogs, forums, social media: allowed only to discover leads, not as authority.

Rule:
- Prefer highest tier available for the claim.

---

## 3) ALLOWED WORLD KNOWLEDGE TYPES
Allowed:
- Official specs/standards (e.g., ISO/IEC/W3C, vendor docs)
- Peer-reviewed papers / academic texts
- Professional handbooks / well-known reference works
- High-quality technical tutorials (only if verifiable)

Not allowed as authority:
- Unverifiable claims
- Anonymous “leaks”
- Low-credibility content used to assert facts

---

## 4) INGEST RULE (HOW TO TURN WEB INTO KB)
External knowledge must be captured as:
- KB standard / playbook / dictionary / checklist
and must include:
- a clear scope boundary (what it covers and what it does not)
- canonical definitions and procedures
- assumptions / constraints
- verification notes (how to confirm)

Entities MUST prefer the ingested KB module over re-browsing.

---

## 5) PROVENANCE WITHOUT URL-DRIFT (STABLE SOURCE RECORDS)
Problem:
- URLs change, pages disappear, and "live web" is not deterministic.

Solution:
- External sources are recorded via stable SOURCE RECORDS (registry approach).

Policy:
- KB modules that rely on external knowledge should reference:
  - SOURCE_RECORD_UID (stable ID)
  - claim-level confidence if needed (HIGH/MED/LOW)

Forbidden:
- fabricated sources
- "I remember reading..." as attribution

Note:
- Exact implementation of SOURCE RECORD storage can be a separate KB standard (not defined here).

---

## 6) FACT VS. HEURISTIC VS. OPINION LABELING (MANDATORY)
Every knowledge item must be classified as one of:
- FACT: verifiable, stable
- HEURISTIC: best practice / rule of thumb
- OPINION: subjective guidance (must be explicitly labeled)
- HYPOTHESIS: uncertain, requires validation

Entities must not output HYPOTHESIS as FACT.

---

## 7) COPYRIGHT & SAFE USE (MANDATORY)
Rules:
- Do not copy large verbatim text from external sources.
- Prefer paraphrase + synthesis + procedure extraction.
- Small quotations are allowed only when necessary and must be minimal.

KB goal:
- convert knowledge into actionable structure, not mirror external pages.

---

## 8) LIVE WEB USAGE POLICY (WHEN ALLOWED)
Live browsing is allowed for:
- freshness (rapidly changing facts)
- niche technical details not present in KB yet
- verifying contradictions

But:
- live results must be converted into KB modules for repeated future use.
- operational runs should minimize live web dependence.

If live web was used for a run:
- it must be explicitly declared as "External lookup used" in the run trace (outside this file’s scope; enforced by entity protocol).

---

## 9) CONTRADICTION RESOLUTION (DETERMINISTIC)
If sources disagree:
- prefer higher tier (Section 2)
- record the conflict as:
  - competing claims
  - decision rationale
  - validation path
- if unresolved, label as HYPOTHESIS and block promotion to ACTIVE.

---

## 10) PROMOTION RULE (WORLD KNOWLEDGE → ACTIVE KB)
A module may be promoted to ACTIVE only if:
- scope boundaries are explicit
- claims are labeled (FACT/HEURISTIC/etc.)
- provenance exists (source record IDs)
- contradictions handled
- module passes QA checks (separate standard)

---

## 11) HARD FAIL CONDITIONS
FAIL IF:
- any invented fact is presented as sourced truth
- missing provenance for non-trivial claims in an ACTIVE module
- large verbatim copy from external sources
- community/tertiary sources used as sole authority for critical claims
- contradictions ignored or hidden

---

## 12) RELATED (UID-ONLY)
XREF:
- XREF: UE.KB.POL.STATUS_LOCK.029 | WHY: lifecycle controls promotion of modules built from world knowledge
- XREF: UE.KB.POL.POINTERS_ALIASES.028 | WHY: migration/aliasing of knowledge modules must not create duplicate truth
- XREF: UE.KB.TOPIC.META.QA_AUDIT.005 | WHY: audit and QA gates for knowledge quality (if present)

--- END.
