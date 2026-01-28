# KB — EXAMPLE CURATION CHECKLIST (CANON)
FILE: 04_KNOWLEDGE_BASE/40_RELATION_XREF/83__KB_EXAMPLE_CURATION_CHECKLIST.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: KB_MODULE
KB_TYPE: CHECKLIST
LEVEL: L2
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.CHK.EXAMPLE_CURATE.083
OWNER: SYSTEM
ROLE: Deterministic checklist for curating and maintaining the KB example library: ensures examples are labeled, tagged, tied to gates/standards, minimal, non-duplicative, and up-to-date with current canon.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created curation checklist to keep example library clean and useful."
- REASON: "Without curation, examples become noise, break QA calibration, and drift from canon."
- IMPACT: "High-signal exemplar set that supports training and QA."
- CHANGE_ID: UE.CHG.2026-01-14.KB.CHK.083

---

## 0) PURPOSE (KB)
Keep example library:
- high signal
- tied to current canon gates/standards
- small and focused
- non-duplicative

---

## 1) CURATION CHECKLIST (RUN ORDER)
E1 — Structure present
- [ ] Example uses the Example Card template fields
FAIL if missing.

E2 — Label correctness
- [ ] LABEL is GOOD/BAD/BORDERLINE
FAIL if missing/invalid.

E3 — Canonical tags
- [ ] All SKILL_TAGS exist in taxonomy
FAIL if non-canonical.

E4 — Gate/standard linkage
- [ ] RELATED_UIDS contains at least 1 canon gate/standard/pack UID
FAIL if none.

E5 — Snippet minimality
- [ ] Snippet is short and focused on one point
REWORK if too long; FAIL if huge dump.

E6 — Non-duplication
- [ ] Example is not a near-duplicate of an existing one
REWORK if redundant; FAIL if duplicates inflate library.

E7 — Canon alignment (freshness)
- [ ] Example still matches current canon rules/gates
REWORK if outdated; FAIL if contradicts canon.

E8 — Provenance (if external-derived)
- [ ] If derived from external source, provenance is present and no large verbatim copy exists
FAIL if missing provenance or large copy.

E9 — Balanced set (domain health)
- [ ] For each critical tag cluster, at least one GOOD and one BAD exists (target)
REWORK if unbalanced; not a hard fail for early stages.

---

## 2) RESULT RULES
PASS IF:
- E1..E4 PASS
- E7 PASS
- no critical duplication

REWORK IF:
- snippet too long, redundancy, or missing balance

FAIL IF:
- label/tags invalid
- no linkage to gates/standards
- contradicts canon
- external-derived without provenance + large copy

---

## 3) OUTPUT TEMPLATE (COPY)
EXAMPLE_CURATION_RESULT:
- DATE: YYYY-MM-DD
- EXAMPLE_UID: <id>
- RESULT: PASS/REWORK/FAIL
- ISSUES:
  - <issue>
- ACTION:
  - KEEP / EDIT / DEPRECATE / REMOVE
- NOTES:

---

## 4) HARD FAIL CONDITIONS
FAIL IF:
- examples contradict current canon and remain in library
- library grows with duplicates
- examples are used as authority instead of standards/gates

---

## 5) RELATED (UID-ONLY)
XREF:
- XREF: UE.KB.POL.EXAMPLE_LIBRARY.081 | WHY: example library policy baseline
- XREF: UE.KB.TPL.EXAMPLE_CARD.082 | WHY: example card structure
- XREF: UE.KB.DICT.SKILL_TAGS.040 | WHY: canonical tags
- XREF: UE.KB.STD.COMP_PACK_QA.045 | WHY: examples calibrate QA gates

--- END.
