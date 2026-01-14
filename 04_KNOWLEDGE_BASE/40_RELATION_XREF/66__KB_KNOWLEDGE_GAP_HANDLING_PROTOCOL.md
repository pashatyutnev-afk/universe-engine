# KB — KNOWLEDGE GAP HANDLING PROTOCOL (CANON)
FILE: 04_KNOWLEDGE_BASE/40_RELATION_XREF/66__KB_KNOWLEDGE_GAP_HANDLING_PROTOCOL.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: KB_MODULE
KB_TYPE: PROTOCOL
LEVEL: L2
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.PROC.GAP_HANDLING.066
OWNER: SYSTEM
ROLE: Deterministic protocol for handling knowledge gaps during execution: detect gap, decide stop vs ingest, create gap record, prioritize, and prevent invention. Ensures missing knowledge never becomes hallucinated “facts.”

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created knowledge gap handling protocol: detect→classify→stop/ingest→record→plan."
- REASON: "Gaps are inevitable; without a protocol they lead to invented content and inconsistent outputs."
- IMPACT: "Safer execution, clearer TODOs, and directed KB expansion."
- CHANGE_ID: UE.CHG.2026-01-14.KB.PROC.066

---

## 0) PURPOSE (KB)
When required knowledge is missing:
- do not invent
- choose a deterministic action:
  - STOP
  - INGEST (create/update KB module)
  - RUN WITH LIMITS (only if allowed and clearly labeled)

---

## 1) GAP TYPES (ENUM)
GAP_TYPE:
- GOVERNANCE_MISSING
- MODULE_MISSING
- PACK_SLOT_UNSATISFIED
- SKILL_TAG_MISSING
- PROVENANCE_MISSING
- CONTRADICTION_UNRESOLVED
- TOOLING_MISSING (templates/checklists absent)
- CLARITY_MISSING (task definition insufficient)

---

## 2) DETECT GAP (TRIGGERS)
A gap is detected if:
- required module UID not found/registered
- required slot cannot be satisfied (no packs cover tags)
- required tags missing from taxonomy
- provenance required but missing
- contradictions unresolved for critical claims
- run needs precise method but only vague guidance exists

---

## 3) DECISION: STOP vs INGEST vs RUN-WITH-LIMITS
### 3.1 HARD STOP (mandatory)
STOP if any:
- GOVERNANCE_MISSING
- CONTRADICTION_UNRESOLVED (CRITICAL/MAJOR)
- PROVENANCE_MISSING for claims treated as FACT in ACTIVE context
- PACK_SLOT_UNSATISFIED for required slot in certified/ACTIVE runs

### 3.2 INGEST (preferred when building KB)
Choose INGEST if:
- gap is recurring
- gap affects P1/P2 quality
- the method can be captured deterministically
- reliable sources exist (tier-first)

### 3.3 RUN WITH LIMITS (allowed only for non-critical)
Allowed only if:
- output can be produced as HEURISTIC/HYPOTHESIS
- user accepts provisional output
- trace explicitly labels limits
- no governance/certification claims rely on it

---

## 4) GAP RECORD (MANDATORY OUTPUT)
When a gap is detected, create a GAP record (copy):

GAP_RECORD:
- GAP_ID: GAP-YYYYMMDD-001
- GAP_TYPE: <enum>
- CONTEXT: <what task/run>
- MISSING_ITEM:
  - UID (if expected) / SKILL_TAG / SLOT / MODULE
- IMPACT:
  - what breaks / what quality loss occurs
- DECISION: STOP | INGEST | RUN_WITH_LIMITS
- PRIORITY: P1/P2/P3 (use gap priority policy)
- NEXT_ACTION:
  - create/update module/pack
  - run ingest workflow
  - update scorecard/bindings
- NOTES:

---

## 5) INGEST PATH (WHEN DECISION = INGEST)
Follow:
- create source records
- synthesize module/pack
- add provenance block
- QA gate
- register in master index
- update scorecard
- audit record if impactful

---

## 6) VALIDATION
PASS IF:
- gap is detected and recorded
- decision follows rules (hard stop vs ingest)
- no invented facts introduced
- priority assigned for P1/P2 gaps

FAIL IF:
- gap is silently ignored
- invention used to “fill” missing knowledge
- critical gaps proceed without stop or ingest
- gap record missing

---

## 7) HARD FAIL CONDITIONS
FAIL IF:
- any critical gap proceeds as if solved
- output states FACT without required knowledge/provenance
- no gap record created when gap exists
- decision contradicts this protocol

---

## 8) RELATED (UID-ONLY)
XREF:
- XREF: UE.KB.POL.GAP_PRIORITY.042 | WHY: prioritization rules for gap fill
- XREF: UE.KB.PROC.WORLD_INGEST.034 | WHY: ingest workflow to convert world knowledge into KB
- XREF: UE.KB.PROC.CONTRADICTIONS.065 | WHY: contradiction handling protocol
- XREF: UE.KB.RULE.NO_FANTASY_EXEC.063 | WHY: no invention rule baseline

--- END.
