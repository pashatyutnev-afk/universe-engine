# KB — COMPETENCE PACK QA GATES STANDARD (CANON)
FILE: 04_KNOWLEDGE_BASE/40_RELATION_XREF/45__KB_COMPETENCE_PACK_QA_GATES_STANDARD.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: KB_MODULE
KB_TYPE: STANDARD
LEVEL: L2
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.STD.COMP_PACK_QA.045
OWNER: SYSTEM
ROLE: Defines deterministic QA gates for Professional Competence Packs: required components, L1/L2/L3 strength criteria, anti-water checks, and PASS/REWORK/FAIL rules for pack quality.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created QA gates standard for competence packs (structure completeness + strength levels + anti-water)."
- REASON: "Packs are the backbone of specialist skill; without QA gates they become vague and unusable."
- IMPACT: "Packs become measurable and improvable; promotion to ACTIVE becomes safe."
- CHANGE_ID: UE.CHG.2026-01-14.KB.STD.045

---

## 0) PURPOSE (KB)
Ensure competence packs are:
- operational (procedures + templates)
- testable (gates)
- non-vague (anti-water)
- consistently labeled by strength level (L1/L2/L3)

---

## 1) REQUIRED COMPONENTS (MUST)
A competence pack MUST include:
- Capability list (C01..Cn) with definitions
- For each capability:
  - Inputs/Outputs
  - Deterministic procedure
  - At least one template/card
  - QA gate (pass/rework/fail)
- Checklists (pre/execution/post)
- Failure modes (at least 3)
- Vocabulary/definitions (domain terms)
- Scope boundary (included/excluded)
- Provenance (if non-trivial world knowledge is used)
- Registered in master index (existence)

---

## 2) STRENGTH LEVELS (L1/L2/L3)
### L1 — Baseline
A capability is L1 if it has:
- procedure (step-by-step)
- one template
- one basic QA gate

### L2 — Strong
A capability is L2 if it has L1 plus:
- failure modes specific to capability
- QA gate includes measurable checks (not vague)
- at least one example of PASS and FAIL

### L3 — Expert
A capability is L3 if it has L2 plus:
- edge cases and constraints
- drills/practice tasks
- stronger QA: thresholds, multi-environment tests, regression guards (when applicable)
- “anti-collision/anti-drift” checks if domain needs uniqueness

Pack-level strength is the median capability strength.

---

## 3) ANTI-WATER RULES (VAGUENESS DETECTION)
A pack FAILS anti-water if it contains:
- advice without steps ("be creative", "make it better")
- untestable claims without criteria
- long theory blocks without operationalization
- repeated statements with no new instructions
- missing templates ("do X" but no copyable form)

---

## 4) QA CHECKLIST (RUN ORDER)
Q1 Schema completeness
- header fields present, change note present
- scope boundary present

Q2 Capability completeness
- at least 5 capabilities (recommended for SPC)
- each capability has I/O + procedure + template + gate

Q3 Failure modes
- at least 3 failure modes with symptoms+fix

Q4 Strength classification
- each capability has L1/L2/L3 level with justification (implicit via content)

Q5 Tags and coverage
- each capability tagged with 1–3 canonical skill tags
- tags exist in taxonomy

Q6 Provenance (if needed)
- provenance block present when external knowledge used

Q7 Registration
- pack registered in KB master index

---

## 5) PASS / REWORK / FAIL
PASS IF:
- Q1..Q7 pass
- anti-water passes
- majority capabilities ≥ L2 (recommended for ACTIVE)

REWORK IF:
- structure ok, but:
  - some capabilities only L1
  - examples missing
  - failure modes weak
  - templates incomplete

FAIL IF:
- any required component missing
- anti-water fails
- non-canonical tags used
- missing master-index registration
- invented facts presented as authoritative

---

## 6) PROMOTION GUIDANCE (TO ACTIVE)
To promote a pack to ACTIVE:
- must PASS
- should have:
  - at least 5 capabilities (or justified smaller for narrow role)
  - majority capabilities ≥ L2
  - clear scope boundary
  - stable UID and version history

---

## 7) HARD FAIL CONDITIONS
FAIL IF:
- pack lacks QA gates
- pack contains mostly vague language
- tags not from taxonomy
- pack not registered in master index
- deprecated pack used as authority

---

## 8) RELATED (UID-ONLY)
XREF:
- XREF: UE.KB.STD.COMP_PACK.036 | WHY: competence pack standard structure
- XREF: UE.KB.DICT.SKILL_TAGS.040 | WHY: canonical tags for capability labeling
- XREF: UE.KB.POL.STATUS_LOCK.029 | WHY: promotion to ACTIVE requires lifecycle discipline
- XREF: UE.KB.STD.MASTER_INDEX_REG.008 | WHY: existence/registration requirement
- XREF: UE.KB.TPL.PROVENANCE_BLOCK.033 | WHY: provenance block for world knowledge

--- END.
