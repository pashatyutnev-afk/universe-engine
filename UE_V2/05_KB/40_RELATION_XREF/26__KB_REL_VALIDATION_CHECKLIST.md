# KB — REL VALIDATION CHECKLIST (SEMANTIC EDGES) (CANON)
FILE: 04_KNOWLEDGE_BASE/40_RELATION_XREF/26__KB_REL_VALIDATION_CHECKLIST.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: KB_MODULE
KB_TYPE: CHECKLIST
LEVEL: L2
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.CHK.REL_VALIDATE.026
OWNER: SYSTEM
ROLE: Deterministic checklist to validate REL blocks (semantic edges) across KB modules: canonical rel types, correct directionality, WHY, minimality, and deprecation pairing rules.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created REL validation checklist with directionality and deprecation pairing rules."
- REASON: "REL errors break dependency graphs and cause wrong execution order; checklist prevents semantic drift."
- IMPACT: "KB relation graph becomes auditable and consistent."
- CHANGE_ID: UE.CHG.2026-01-14.KB.CHK.026

---

## 0) PURPOSE (KB)
Validate that any REL block:
- uses canonical relation types only
- uses correct direction for meaning
- includes WHY for each edge
- is minimal and relevant
- handles deprecation/supersession correctly

---

## 1) CHECKLIST (RUN ORDER)
### R1 — REL block presence (optional)
- [ ] REL block exists only when semantics are needed
PASS if absent and no semantics required.
REWORK if semantics required but REL missing.

### R2 — Canonical rel types only
For every edge:
- [ ] rel_type is from canonical dictionary (no custom inventions)

FAIL triggers:
- unknown type (e.g., `uses`, `needs`, `related`, `important_for`)

### R3 — Correct directionality
- [ ] Edge direction matches meaning

Direction rules (examples):
- depends_on: A depends_on -> B (A requires B)
- governed_by: A governed_by -> B (A is controlled by B)
- validated_by: A validated_by -> B (A is checked by B)
- constrained_by: A constrained_by -> B (A is limited by B)
- maps_to: A maps_to -> B (A corresponds to B)
- supersedes: A supersedes -> B (A replaces older B)
- deprecated_by: A deprecated_by -> B (A is replaced by newer B)

FAIL if inverted (e.g., dependency flipped).

### R4 — WHY present on each edge
- [ ] Each REL line includes `| WHY: ...`
FAIL if missing.

### R5 — Target format sanity
- [ ] Target is UID when available; otherwise stable canonical label (only if UID truly unavailable)

FAIL triggers:
- using RAW URLs as REL targets
- using repo paths as REL targets

### R6 — Minimality and relevance
- [ ] REL list is minimal (usually 0–10)
- [ ] Each edge is necessary and non-redundant
REWORK if too verbose.

### R7 — Deprecation pairing correctness
If any deprecation is used:
- [ ] If NEW supersedes OLD, then OLD must have deprecated_by NEW
- [ ] OLD must also include XREF replacement UID (per xref checklist)

FAIL if only one side exists.

### R8 — No REL used as XREF substitute
- [ ] REL edges are not used as a “see also list”
FAIL if REL is abused for non-semantic linking.

---

## 2) COMMON FAIL PATTERNS
FP1: Custom rel types
- REL: uses -> ... => FAIL

FP2: Flipped dependencies
- REL: depends_on -> ... but actually reverse => FAIL

FP3: Missing WHY
- REL: governed_by -> UID (no WHY) => FAIL

FP4: URL/PATH as target
- REL: governed_by -> https://raw... => FAIL
- REL: depends_on -> 04_KNOWLEDGE_BASE/... => FAIL

FP5: Broken deprecation pairing
- NEW has supersedes, OLD missing deprecated_by => FAIL

---

## 3) PASS/REWORK/FAIL RULES
PASS IF:
- R2..R5 all PASS
- direction is correct
- no URL/PATH targets
- deprecation pairing correct when used

REWORK IF:
- only minimality/relevance issues (R6) OR
- REL missing but semantics clearly needed (R1)

FAIL IF:
- any of R2..R5 FAIL
- any inverted directionality (R3)
- deprecation pairing broken (R7)
- REL abused as link list (R8)

---

## 4) QUICK FIX PROCEDURE
If FAIL:
- replace rel_type with canonical type
- fix arrow direction
- replace URL/PATH targets with UID
- add WHY to each line
- enforce deprecation pairing both sides

If REWORK:
- remove redundant edges
- keep only essential semantics

---

## 5) RELATED (UID-ONLY)
XREF:
- XREF: UE.KB.DICT.REL_TYPES.004 | WHY: canonical relation type dictionary (source of allowed rel_type)
- XREF: UE.KB.STD.RELATION_MODEL.024 | WHY: relation model (REL + XREF coexistence)
- XREF: UE.KB.CHK.XREF_VALIDATE.025 | WHY: complementary checklist for XREF block

--- END.
