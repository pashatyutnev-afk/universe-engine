# ENTITIES KB — RULES (CANON)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/01__ENTITY_KB_RULES.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB
DOC_TYPE: RULE
INDEX_TYPE: REALM_RULESET
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.RULE.ENTITIES.001
OWNER: SYSTEM
ROLE: Operational rules for entity-specific KB packs/connectors: required pack structure, no-domain-content boundary, UID-only crossrefs, no-fantasy execution, sources discipline, and mandatory evaluation gates.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created Entities KB rules: pack minimum requirements, boundaries vs topics, trace/sources, and evaluation discipline."
- REASON: "Entity packs must be deterministic and auditable; without rules they become inconsistent and drift."
- IMPACT: "Stable entity competence, less repetition, and safer certification readiness."
- CHANGE_ID: UE.CHG.2026-01-14.KB.ENT.RULE.001

---

## 0) PURPOSE (LAW)
These rules govern how `20_ENTITIES_KB` is authored and used:
- deterministic competence packs for entities
- strict boundaries (no domain topics inside)
- evaluation/certification-ready structure

---

## 1) ABSOLUTE BOUNDARIES (NO DOMAIN TOPICS HERE)
R1 — Domain knowledge lives in `10_TOPICS`
- `20_ENTITIES_KB` must not store domain craft topics (narrative/visual/sound/world/marketing).
- Entity packs may reference topics via UID-only XREF.

R2 — Shared generic assets live in `30_SHARED_LIBRARIES`
- If something is generic (templates/checklists/patterns/examples) and not entity-specific, it belongs in shared libraries.

---

## 2) REQUIRED PACK MINIMUM (ABSOLUTE)
Any entity competence pack must contain:

P1 — KB_PASSPORT (required)
- identity, scope, owner, version, status, constraints

P2 — SKILL TREE / SCOPE MAP (required)
- what the entity is responsible for
- what it must never do

P3 — GOLDEN PRINCIPLES / POLICY (required)
- operating principles and constraints

P4 — METHOD / PLAYBOOKS (required)
- how to execute typical tasks deterministically

P5 — CHECKLISTS + KB_GATES (required)
- measurable-ish validation (pass/rework/fail)
- at least one core gate for the pack’s main capability

P6 — EXAMPLES / CASE LIBRARY (required)
- examples of good/bad/borderline decisions or outputs

P7 — EVALUATION RUBRIC (required for SPC, recommended for others)
- consistent scoring guidance

P8 — KB_SOURCES (required when knowledge is derived externally)
- provenance discipline (no invented sources)

If any required block is missing → pack is NON-OPERATIONAL.

---

## 3) UID-ONLY LINKING (ABSOLUTE)
R3 — UID-only XREF
- Entity packs must reference other KB modules by UID-only.
- No URL/PATH in operational XREF blocks.

R4 — Navigation authority remains master index
- Existence/navigation remains controlled by KB master index only.

---

## 4) NO-FANTASY EXECUTION (ABSOLUTE)
R5 — No invented competence
- Entity must not claim it “knows” methods not present in:
  - its pack modules, OR
  - referenced topic modules opened via master index.

R6 — Gaps require stop or ingestion
- Missing competence → STOP or GAP handling; never guess.

---

## 5) SOURCES DISCIPLINE (MANDATORY WHEN APPLICABLE)
R7 — External knowledge requires source records
- If a rule/method/heuristic is based on external material, record it in KB_SOURCES.
- Do not copy large chunks; extract operational principles.

R8 — “Best practices” must be framed
- If a practice is generally accepted but context-dependent, mark it as:
  - PRINCIPLE / HEURISTIC (and define boundaries)

---

## 6) EVALUATION DISCIPLINE (MANDATORY)
R9 — Packs must be testable
- Every major capability in a pack must have:
  - at least one gate OR checklist producing PASS/REWORK/FAIL
  - and at least one example for calibration

R10 — Key gates require exemplar sets
- If a gate is used in certification or widely across packs, it becomes KEY and must have exemplar calibration sets.

R11 — Regression guard
- Pack updates that affect behavior should be accompanied by:
  - at least one regression check (sample runs + expected outcomes)

---

## 7) SPC PRO-LEVEL RULE (SPECIAL)
R12 — SPC packs must be “pro”
For SPC:
- must include deep craft knowledge mapping to domain topics
- must include anti-pattern library and edge cases
- must include evaluation rubric with measurable anchors

If SPC pack is shallow → REWORK (not ready).

---

## 8) HARD FAIL CONDITIONS
FAIL IF:
- domain topics are placed inside entity packs
- required pack minimum blocks missing
- UID-only XREF violated (URLs/PATH used as authority)
- entity claims competence without sources/trace
- pack used for certification without gates/examples

---

## 9) RELATED (UID-ONLY)
XREF:
- UE.KB.RULES.GOV.001 | WHY: global KB governance rules apply
- UE.KB.README.ENTITIES_REALM.001 | WHY: entities KB realm orientation
- UE.KB.POL.GATE_LIBRARY.092 | WHY: key gate discipline
- UE.KB.RULE.GATE_EXAMPLE_BIND.090 | WHY: exemplar binding rule for key gates
- UE.KB.STD.QA_RUBRIC.096 | WHY: scoring rubric standard
- UE.KB.PROC.QA_SCORE_CONSIST.098 | WHY: scoring consistency protocol

--- END.
