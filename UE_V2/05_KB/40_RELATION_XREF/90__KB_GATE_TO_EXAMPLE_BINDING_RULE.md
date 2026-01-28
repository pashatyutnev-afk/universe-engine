# KB — GATE ↔ EXAMPLE BINDING RULE (CANON)
FILE: 04_KNOWLEDGE_BASE/40_RELATION_XREF/90__KB_GATE_TO_EXAMPLE_BINDING_RULE.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: KB_MODULE
KB_TYPE: RULE
LEVEL: L2
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.RULE.GATE_EXAMPLE_BIND.090
OWNER: SYSTEM
ROLE: Enforces that key gates are calibrated with a minimum exemplar set (GOOD/BAD/BORDERLINE) linked to the gate/standard UID. Enables consistent QA application and reduces subjective drift.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created rule binding key gates to exemplar sets for QA calibration."
- REASON: "Gates without exemplars are applied inconsistently; exemplars provide calibration for PASS/FAIL judgments."
- IMPACT: "More stable QA outcomes and better training/drills."
- CHANGE_ID: UE.CHG.2026-01-14.KB.RULE.090

---

## 0) PURPOSE (KB)
Ensure each key gate has a calibration set of examples:
- GOOD (passes)
- BAD (fails)
- BORDERLINE (rework zone)

---

## 1) ABSOLUTE RULES
R1 — Key gates must have exemplars
- Any gate used for certification, QA, or common evaluation must be bound to exemplars.

R2 — UID-only binding
- Bindings reference example IDs/UIDs and gate UIDs only (no URLs).

R3 — Exemplar explanations must map to gate criteria
- Examples must explain why they pass/fail in gate terms.

---

## 2) MINIMUM EXEMPLAR SET
For each KEY gate:
- GOOD: at least 2
- BAD: at least 2
- BORDERLINE: at least 1

If domain is early-stage:
- allow minimum:
  - GOOD 1, BAD 1, BORDERLINE 0
but mark as REWORK state until expanded.

---

## 3) BINDING DECLARATION (COPY)
GATE_EXEMPLAR_SET:
- GATE_UID: <uid>
- DOMAIN:
- EXEMPLARS:
  - GOOD:
    - <example uid>
  - BAD:
    - <example uid>
  - BORDERLINE:
    - <example uid>
- COVERED_SKILL_TAGS:
  - <tag>
- STATUS: DRAFT | ACTIVE_READY

Rule:
- Each example listed must include RELATED_UIDS linking back to the gate UID.

---

## 4) VALIDATION
PASS IF:
- minimum exemplar counts exist
- examples are linked to the gate UID
- examples are curated and non-duplicative
- labels align with gate criteria (calibration protocol)

REWORK IF:
- exemplar set is incomplete
- borderline set missing for key gate
- some examples are weakly explained

FAIL IF:
- examples are not linked
- examples contradict current gate definition
- exemplar set is stale and miscalibrates QA

---

## 5) HARD FAIL CONDITIONS
FAIL IF:
- a gate is used for certification without any exemplars
- exemplar set exists but examples lack gate linkage
- examples used are outdated and contradict canon gates

---

## 6) RELATED (UID-ONLY)
XREF:
- XREF: UE.KB.STD.GATE_DEF.088 | WHY: gates must be measurable and definable
- XREF: UE.KB.PROC.DOMAIN_QA_CALIB.087 | WHY: calibration protocol validates label↔gate consistency
- XREF: UE.KB.POL.EXAMPLE_LIBRARY.081 | WHY: example library policy and curation
- XREF: UE.KB.RULE.EXAMPLE_GATE_LINK.084 | WHY: examples must link to gates
- XREF: UE.KB.CHK.EXAMPLE_CURATE.083 | WHY: curate exemplars for quality and freshness

--- END.
