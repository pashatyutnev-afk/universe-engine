# KB — EXAMPLE LIBRARY POLICY (CANON)
FILE: 04_KNOWLEDGE_BASE/40_RELATION_XREF/81__KB_EXAMPLE_LIBRARY_POLICY.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: KB_MODULE
KB_TYPE: POLICY
LEVEL: L2
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.POL.EXAMPLE_LIBRARY.081
OWNER: SYSTEM
ROLE: Defines how to build and use a KB example library (good/bad exemplars): labeling, structure, QA usage, provenance rules, and anti-noise controls. Ensures examples improve quality instead of becoming clutter.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created example library policy: exemplar structure, labeling, QA usage, and clutter prevention."
- REASON: "Examples calibrate quality; without policy they become random dumps and stop being useful."
- IMPACT: "Better QA calibration, faster learning, and stronger standards application."
- CHANGE_ID: UE.CHG.2026-01-14.KB.POL.081

---

## 0) PURPOSE (KB)
Examples help:
- calibrate what PASS/FAIL looks like
- teach style and constraints
- accelerate onboarding and QA

This policy defines how examples must be:
- structured
- labeled
- curated
- used in QA

---

## 1) ABSOLUTE RULES
R1 — Examples are not rules
- Examples illustrate; rules live in standards/policies.

R2 — Examples must be labeled
- GOOD / BAD / BORDERLINE
- Domain + skill tags + what they demonstrate

R3 — Examples must be minimal
- Keep them short and focused on one point.
- Do not store massive dumps.

R4 — Provenance required when needed
- If example is derived from external content, store provenance (source record) and avoid large verbatim copying.

---

## 2) EXAMPLE CARD SCHEMA (REQUIRED)
EXAMPLE_CARD:
- EXAMPLE_UID: <unique id>
- DOMAIN: <music/narrative/...>
- LABEL: GOOD | BAD | BORDERLINE
- SKILL_TAGS:
  - <tag>
- WHAT_IT_DEMONSTRATES:
  - <1–2 bullets>
- INPUT_CONTEXT:
  - <scenario/task>
- EXAMPLE_SNIPPET:
  - <short snippet>
- WHY_IT_PASSES_OR_FAILS:
  - <short bullets tied to gates/standards>
- RELATED_UIDS (UID-ONLY):
  - <standard/policy/pack uid> | WHY: gate reference
- NOTES:
- PROVENANCE (optional):
  - SOURCE_RECORD_UID: <uid> (if external)
  - DATE_ACCESSED: YYYY-MM-DD

---

## 3) CURATION RULES (ANTI-NOISE)
- Each example must tie to at least one gate/standard/pack UID.
- Remove or deprecate examples that:
  - no longer match current canon standards
  - are redundant duplicates
  - are too long and unfocused
- Keep a balanced set:
  - at least 1 GOOD and 1 BAD per critical skill tag cluster

---

## 4) USAGE RULES (HOW ENTITIES USE EXAMPLES)
Use examples when:
- calibrating QA judgment
- training drills
- diagnosing failure modes
- aligning output style to standards

Do not use examples when:
- they conflict with current canon modules
- they become the authority instead of standards/gates

---

## 5) QA INTEGRATION
- Examples should be referenced in:
  - competence pack QA gates
  - drills rubric
  - onboarding playbooks
- Example library supports “recognition” and “taste calibration” but must be traceable.

---

## 6) HARD FAIL CONDITIONS
FAIL IF:
- examples are stored without labels/tags
- examples are used as rules/authority
- examples contain large copied external text
- examples have no relation to any canon gate/standard/pack UID
- example dump grows without curation

---

## 7) RELATED (UID-ONLY)
XREF:
- XREF: UE.KB.DICT.SKILL_TAGS.040 | WHY: examples must use canonical tags
- XREF: UE.KB.STD.COMP_PACK_QA.045 | WHY: examples calibrate QA gates
- XREF: UE.KB.TPL.COMP_PACK_DRILLS.048 | WHY: drills can include examples
- XREF: UE.KB.STD.SOURCE_RECORDS.032 | WHY: provenance for external-derived examples

--- END.
