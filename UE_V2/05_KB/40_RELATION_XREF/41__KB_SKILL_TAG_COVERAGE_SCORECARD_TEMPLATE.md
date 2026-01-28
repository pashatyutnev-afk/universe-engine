# KB — SKILL TAG COVERAGE SCORECARD (TEMPLATE) (CANON)
FILE: 04_KNOWLEDGE_BASE/40_RELATION_XREF/41__KB_SKILL_TAG_COVERAGE_SCORECARD_TEMPLATE.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: KB_MODULE
KB_TYPE: TEMPLATE
LEVEL: L2
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.TPL.SKILL_TAG_SCORECARD.041
OWNER: SYSTEM
ROLE: Template scorecard to measure skill-tag coverage for an entity or a domain: covered vs missing tags, strength level, evidence (pack UIDs), and prioritized gap-fill plan.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created skill-tag coverage scorecard template for competence validation and gap planning."
- REASON: "Without measurable coverage, competence packs cannot be audited or improved systematically."
- IMPACT: "Entities can be scored, gaps prioritized, and KB growth becomes directed."
- CHANGE_ID: UE.CHG.2026-01-14.KB.TPL.041

---

## 0) PURPOSE (KB)
Provide a standard way to measure:
- which SKILL_TAGS are covered by available competence packs
- which are missing
- the strength level per tag
- the next actions to close gaps

---

## 1) SCORECARD TEMPLATE (COPY)
SKILL_TAG_COVERAGE_SCORECARD:
- TARGET:
  - ENTITY_UID: <entity uid> (optional)
  - DOMAIN: <music/narrative/...>
  - DATE: YYYY-MM-DD
- INPUTS:
  - REQUIRED_TAGS_SET: <list or reference>
  - AVAILABLE_PACK_UIDS:
    - <pack uid>
    - <pack uid>

COVERAGE_TABLE:
| SKILL_TAG | STATUS (COVERED/MISSING) | STRENGTH (L1/L2/L3) | EVIDENCE_PACK_UIDS | NOTES |
|---|---|---|---|---|
| <tag> | <...> | <...> | <uids> | <short> |

SUMMARY:
- COVERAGE_PERCENT: <0..100>
- CRITICAL_MISSING:
  - <tag>
- NEXT_PRIORITY_GAPS (TOP 5):
  - <tag> | WHY: <impact on outputs>

GAP_FILL_PLAN:
- ACTIONS:
  - CREATE_PACK: <yes/no> | TARGET_PACK: <name> | TAGS: <tags> | PRIORITY: P1/P2/P3
  - EXTEND_PACK: <pack uid> | TAGS: <tags> | PRIORITY: P1/P2/P3
- VALIDATION:
  - re-run scorecard after changes
  - promote packs from DRAFT→ACTIVE after QA

---

## 2) RULES (STRICT)
- SKILL_TAG must exist in the canonical taxonomy.
- STRENGTH levels:
  - L1: baseline method exists (procedure + basic checklist)
  - L2: includes failure modes + QA gates
  - L3: includes edge cases + drills + strong QA

- Evidence must be pack UIDs (not descriptions).
- Missing tags must translate into gap-fill actions.

---

## 3) PASS/FAIL
PASS IF:
- all tags are canonical
- every COVERED tag has evidence pack UIDs
- every MISSING tag appears in plan with priority

FAIL IF:
- non-canonical tags used
- coverage claimed without evidence
- no gap fill plan

---

## 4) HARD FAIL CONDITIONS
FAIL IF:
- scorecard uses tags outside taxonomy
- coverage percent claimed without table evidence
- evidence uses URL/PATH instead of UIDs

---

## 5) RELATED (UID-ONLY)
XREF:
- XREF: UE.KB.DICT.SKILL_TAGS.040 | WHY: canonical skill tag taxonomy
- XREF: UE.KB.STD.COMP_PACK.036 | WHY: packs provide evidence of coverage
- XREF: UE.KB.STD.ENTITY_COMP_BIND.039 | WHY: entities bind to required packs for coverage

--- END.
