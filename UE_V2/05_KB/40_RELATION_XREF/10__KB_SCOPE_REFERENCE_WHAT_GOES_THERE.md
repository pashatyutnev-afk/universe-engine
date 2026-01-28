# KB — KB_SCOPE.REFERENCE: WHAT GOES THERE (CANON)
FILE: 04_KNOWLEDGE_BASE/40_RELATION_XREF/10__KB_SCOPE_REFERENCE_WHAT_GOES_THERE.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: KB_MODULE
KB_TYPE: STANDARD
LEVEL: L2
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.STD.SCOPE.REFERENCE.010
OWNER: SYSTEM
ROLE: Define the purpose and strict content rules for KB_SCOPE.REFERENCE modules: what is allowed, what is forbidden, and how entities must use reference modules without turning them into knowledge dumps.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Defined KB_SCOPE.REFERENCE content boundaries and usage rules."
- REASON: "REFERENCE must stay lightweight and deterministic; prevents mixing guidelines and domain knowledge, and preserves fast navigation."
- IMPACT: "Cleaner KB separation: standards vs reference vs topics; fewer collisions and less drift."
- CHANGE_ID: UE.CHG.2026-01-14.KB.STD.010

---

## 0) PURPOSE (KB)
KB_SCOPE.REFERENCE is NOT a place for deep knowledge.
Its only purpose is:
- provide pointers, enumerations, taxonomies, and quick lookup rules
- store stable canonical dictionaries (terms, enums, relation types)
- define minimal cross-links by UID-only
- act as a fast reference layer for entities

---

## 1) ABSOLUTE BOUNDARY (NO MIXING)
REFERENCE modules must not contain:
- long-form explanations
- tutorials
- “how to” procedures
- best-practice essays
- domain skill training
Those belong to:
- KB_SCOPE.GOVERNANCE (protocols, rules)
- KB_SCOPE.TOPICS.* (domain knowledge)
- KB_SCOPE.CHECKLISTS / QA (tests and gates) if separated

---

## 2) ALLOWED CONTENT TYPES (REFERENCE)
Allowed:
1) ENUMS / TAXONOMIES
- relation types, statuses, priorities
- naming token dictionaries (if needed)
- classification trees

2) CANON DICTIONARIES
- short definitions (1–3 lines per term)
- disambiguation notes

3) LOOKUP TABLES (TEXT)
- “If X then Y” mapping tables
- short scoring rubrics (no essays)

4) UID-ONLY CROSSREF MAPS
- “XREF: <UID> | WHY: ...”
No raw links inside REFERENCE modules (RAW links live in master index).

---

## 3) FORBIDDEN CONTENT TYPES (REFERENCE)
Forbidden:
- “full knowledge” about a profession
- storytelling, narrative content
- subjective opinion pieces
- large examples bigger than needed for disambiguation
- duplicated standards (if it’s a protocol, it must be a standard module)

If needed:
- create a TOPIC module and keep REFERENCE minimal.

---

## 4) STRUCTURE TEMPLATE (REFERENCE MODULE)
Recommended structure:
- Purpose
- Allowed content types
- Canon dictionary / enum list
- Notes (strictly short)
- Related (UID-only)

The module must remain small and fast to scan.

---

## 5) HOW ENTITIES MUST USE REFERENCE
- Use it as lookup only.
- Do not “derive new rules” beyond what is written.
- If a required dictionary is missing → trigger gap handling: create/extend reference module or hard stop.

---

## 6) QUALITY RULES (REFERENCE)
- Atomicity: one module = one reference asset (one dictionary/enum set).
- No duplicates: if two modules define the same enum → collision → fix.
- Stability: reference should change rarely; changes must be logged/versioned.

---

## 7) EXAMPLES
GOOD:
- Relation types dictionary (REL enum)
- XREF rules dictionary
- Audience segment enum labels

BAD:
- “How to write a great dialogue” (TOPIC)
- “Prompt engineering guide” (GOVERNANCE/PROTOCOL)
- “Composer masterclass” (TOPIC)

---

## 8) RELATED (UID-ONLY)
XREF:
- XREF: UE.KB.STD.SCOPE.GOVERNANCE_MIN.009 | WHY: governance baseline requires reference dictionaries
- XREF: UE.KB.DICT.REL_TYPES.004 | WHY: canonical relation enum is a reference asset
- XREF: UE.KB.DICT.XREF_RULES.005 | WHY: UID-only xref policy is reference asset
- XREF: UE.KB.TOPIC.META.NAV.002 | WHY: master index RAW-only navigation rule

--- END.
