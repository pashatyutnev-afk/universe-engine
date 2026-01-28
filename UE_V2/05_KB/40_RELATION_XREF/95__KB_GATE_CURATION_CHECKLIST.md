# KB — GATE CURATION CHECKLIST (CANON)
FILE: 04_KNOWLEDGE_BASE/40_RELATION_XREF/95__KB_GATE_CURATION_CHECKLIST.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: KB_MODULE
KB_TYPE: CHECKLIST
LEVEL: L2
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.CHK.GATE_CURATE.095
OWNER: SYSTEM
ROLE: Deterministic checklist for curating gates: measurability, canonical tags, examples, key-gate exemplar calibration, duplicate/conflict detection, and versioning discipline.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created gate curation checklist to maintain gate library quality and determinism."
- REASON: "Gates drift and duplicate over time; curation ensures they stay measurable, calibrated, and consistent."
- IMPACT: "More reliable QA and safer certifications."
- CHANGE_ID: UE.CHG.2026-01-14.KB.CHK.095

---

## 0) PURPOSE (KB)
Keep gate library:
- measurable and operational
- calibrated with exemplars when key
- free from duplicates and conflicts
- correctly versioned and audited

---

## 1) CURATION CHECKLIST (RUN ORDER)
G1 — Gate structure compliance
- [ ] Gate follows gate definition standard (test method + criteria + examples)
FAIL if missing.

G2 — Measurability
- [ ] PASS/REWORK/FAIL are measurable and testable
FAIL if vague.

G3 — Canonical tags
- [ ] SKILL_TAGS are canonical and domain-consistent
FAIL if non-canonical/mismatch.

G4 — Examples present
- [ ] Gate includes at least one PASS and one FAIL example snippet
REWORK if weak; FAIL if absent.

G5 — Key gate determination
- [ ] Gate is classified as KEY or not (per gate library policy)
REWORK if unknown for frequently used gate.

G6 — Exemplar calibration for key gates
If gate is KEY:
- [ ] Exemplar set exists (GOOD/BAD/BORDERLINE)
- [ ] Calibration protocol run result is PASS/REWORK/FAIL recorded
FAIL if key gate has no exemplars.

G7 — Duplicate detection
- [ ] No other gate duplicates the same function
REWORK if suspected; FAIL if duplicates coexist as authority.

G8 — Conflict/contradiction handling
- [ ] No unresolved contradictions with other gates/standards
FAIL if contradictions ignored.

G9 — Versioning discipline
- [ ] Version type matches change impact (patch/minor/major)
- [ ] Major semantic changes use replacement flow if key gate
FAIL if mismatched.

G10 — Deprecation discipline
- [ ] Deprecated gates have replacement UIDs and migrated dependents
FAIL if deprecated without replacement or still used as authority.

---

## 2) RESULT RULES
PASS IF:
- G1..G3 PASS
- G4 PASS (or strong enough)
- key gates have exemplars + calibration
- no duplicates/conflicts

REWORK IF:
- examples weak, key classification unclear, or potential duplicates need resolution

FAIL IF:
- vague criteria
- non-canonical tags
- key gate without exemplars
- duplicates/conflicts unresolved
- versioning/deprecation violations

---

## 3) OUTPUT TEMPLATE (COPY)
GATE_CURATION_RESULT:
- DATE: YYYY-MM-DD
- GATE_UID: <uid>
- RESULT: PASS/REWORK/FAIL
- ISSUES:
  - <issue>
- ACTION:
  - KEEP / EDIT / DEPRECATE / REPLACE
- NOTES:

---

## 4) HARD FAIL CONDITIONS
FAIL IF:
- key gate used for certification lacks exemplars
- gates are duplicated without deprecation resolution
- gate criteria are untestable
- gate changes shipped without proper versioning/audit

---

## 5) RELATED (UID-ONLY)
XREF:
- XREF: UE.KB.STD.GATE_DEF.088 | WHY: gate definition structure compliance
- XREF: UE.KB.POL.GATE_LIBRARY.092 | WHY: key gate discipline and library rules
- XREF: UE.KB.RULE.GATE_EXAMPLE_BIND.090 | WHY: exemplar sets for key gates
- XREF: UE.KB.PROC.DOMAIN_QA_CALIB.087 | WHY: calibration protocol for judgement consistency
- XREF: UE.KB.POL.GATE_VERSIONING.094 | WHY: versioning discipline for gates
- XREF: UE.KB.RULE.GATE_DEPRECATE.093 | WHY: deprecation/replacement flow

--- END.
