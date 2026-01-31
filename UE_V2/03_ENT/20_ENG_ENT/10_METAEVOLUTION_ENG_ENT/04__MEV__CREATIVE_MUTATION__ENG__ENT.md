# CREATIVE MUTATION ENGINE (ENG) — CANON FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/10_META_EVOLUTION_ENGINES/04__CREATIVE_MUTATION_ENG.md
SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
DOC_TYPE: ENGINE
FAMILY: 10_META_EVOLUTION_ENGINES
CLASS: META (L4)
LEVEL: L4
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.ENG.META.CREATIVE.MUTATION.001
OWNER: SYSTEM
ROLE: Generates bounded creative variants of artifacts and rulesets deterministically: mutation operators, variant sets, novelty constraints, and gates. Produces exploration artifacts routed through learning/optimization/governance (no direct canon changes).

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Creative Mutation Engine created: mutation operator schema, bounded variant generation, novelty constraints, and governance-safe routing."
- REASON: "Need controlled exploration to discover better templates/structures without destabilizing canon."
- IMPACT: "System can explore alternatives deterministically and adopt improvements via governance."
- CHANGE_ID: UE.CHG.2026-01-08.META.CREATIVE.MUTATION.001

---

## 0) PURPOSE (LAW)
This engine owns **CREATIVE MUTATION (bounded exploration)**:
- defines mutation operators (ways to alter artifacts/rules while preserving constraints)
- generates variant sets with controlled novelty and safety bounds
- records what changed and why (diff intent)
- emits gates to prevent canon-breaking mutations and vague variant outputs

Hard rule:
- Mutation outputs are exploratory artifacts. Any canon adoption must be routed via governance.

---

## 1) NON-GOALS (HARD)
This engine does NOT:
- directly change canon files
- replace optimization selection (optimization picks what to adopt)
- replace learning hypotheses (learning turns results into hypotheses)
- generate unrestricted randomness without operators and bounds

FORBIDDEN:
- “mutation” without operator list and novelty constraints
- producing variants that violate system laws (existence, naming, contracts)

---

## 2) MINI-CONTRACT (MANDATORY)
CONSUMES:
- BASE_ARTIFACT (optional)
- PATTERN_LIBRARY (optional)
- CHANGE_CANDIDATE_SET (optional)
- CONSTRAINTS_REGISTRY (optional)
- MUTATION_REQUEST (optional)

PRODUCES:
- MUTATION_OPERATOR_SET
- MUTATED_VARIANT_SET
- NOVELTY_SAFETY_CONSTRAINTS
- MUTATION_EVALUATION_NOTES
- MUTATION_GATES_REPORT

DEPENDS_ON:
- [10_META_EVOLUTION_ENGINES/01__LEARNING_ENG, 10_META_EVOLUTION_ENGINES/03__OPTIMIZATION_ENG]
(soft) [00_GOVERNANCE_ENGINES/04__CHANGE_CONTROL_ENG]

OUTPUT_TARGET:
MANDATORY:
- PROJECT_ARTIFACTS/<project>/META/MUTATION/
OPTIONAL:
- KB/META/MUTATION (if mirrored)

Rule:
- If MINI-CONTRACT is vague → INVALID.

---

## 3) DEFINITIONS (STRICT)
- Mutation Operator: named transformation that changes an artifact within bounds (e.g., reorder sections, tighten schema).
- Variant: mutated artifact candidate with explicit delta notes.
- Novelty: degree of deviation from baseline (0..100 proxy).
- Safety Constraint: rules that prevent violations (naming, mini-contract, boundaries).
- Evaluation Notes: structured scoring or observations (can feed learning/optimization).

Enums (baseline):
- operator_type: REORDER|TIGHTEN_SCHEMA|RELAX_SCHEMA|ADD_GATE|REMOVE_GATE|RENAME_LABELS|PARTITION_SCOPE|MERGE_RULES|SPLIT_RULES
- severity: S0|S1|S2|S3
- status: GENERATED|EVALUATED|REJECTED|PROMOTED

---

## 4) BOUNDARIES (ANTI-DUPLICATION)
IN SCOPE:
- operator definition and bounded variant generation
- novelty + safety constraint specification
- evaluation notes and gates

OUT OF SCOPE (HARD):
- applying changes to canon (governance)
- prioritizing adoption (optimization)
- formal hypothesis testing design (learning can own)

COLLISION RULE:
- If request is “apply mutation into canon” → governance change control + audit
- If request is “rank variants for adoption” → optimization engine

---

## 5) RULESET (THE LAW)
R1 (HARD) MUST: MUTATION_OPERATOR_SET lists operators with allowed targets and constraints.
R2 (HARD) MUST: NOVELTY_SAFETY_CONSTRAINTS define novelty bounds and safety gates.
R3 (HARD) MUST: MUTATED_VARIANT_SET includes explicit delta notes and references baseline.
R4 (HARD) FORBIDDEN: variants that violate system laws (naming, contract, boundaries) unless explicitly flagged FAIL.
R5 (HARD) MUST: evaluation notes exist (even minimal) for generated variants.
R6 (SOFT) SHOULD: keep variant count bounded and deterministic (seed policy).
R7 (HARD) MUST: gates detect missing operators, missing safety constraints, and canon-mod attempts.

---

## 6) REQUIRED OUTPUT SCHEMAS (MINIMUM)

ARTIFACT: MUTATION_OPERATOR_SET
- MUST:
  - operator_set_id
  - version
  - operators[] (non-empty)
  - checks[] (non-empty)
- OPERATOR (minimum):
  - operator_id
  - name
  - operator_type (enum)
  - allowed_targets[] (non-empty; artifact types or file classes)
  - action_description (testable)
  - constraints[] (non-empty)
  - risk_level (S0|S1|S2|S3)
- VALIDATION:
  - operators non-empty
  - allowed_targets non-empty
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/META/MUTATION/MUTATION_OPERATOR_SET.md

---

ARTIFACT: NOVELTY_SAFETY_CONSTRAINTS
- MUST:
  - constraints_id
  - version
  - novelty_bounds (min,max 0..100)
  - safety_rules[] (non-empty)
  - forbidden_actions[] (non-empty)
  - checks[] (non-empty)
- SAFETY RULE (minimum):
  - rule_id
  - statement (testable)
  - severity_if_broken (S0|S1|S2|S3)
- VALIDATION:
  - novelty bounds valid
  - safety_rules non-empty
  - forbidden_actions non-empty
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/META/MUTATION/NOVELTY_SAFETY_CONSTRAINTS.md

---

ARTIFACT: MUTATED_VARIANT_SET
- MUST:
  - variant_set_id
  - version
  - baseline_ref (required)
  - seed_policy (REQUIRED|OPTIONAL)
  - variants[] (non-empty)
  - checks[] (non-empty)
- VARIANT (minimum):
  - variant_id
  - operator_refs[] (non-empty)
  - delta_notes (testable)
  - novelty_score (0..100)
  - expected_effect (testable)
  - risk_level (S0|S1|S2|S3)
  - compliance (PASS|WARN|FAIL)
  - artifacts[] (optional; mutated content references)
- VALIDATION:
  - variants non-empty
  - novelty_score within bounds
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/META/MUTATION/MUTATED_VARIANT_SET.md

---

ARTIFACT: MUTATION_EVALUATION_NOTES
- MUST:
  - evaluation_id
  - version
  - variant_scores[] (non-empty)
  - criteria[] (non-empty)
  - checks[] (non-empty)
- CRITERION (minimum):
  - criterion_id
  - name
  - description (testable)
  - weight (0..100)
- VARIANT SCORE (minimum):
  - variant_id
  - criterion_scores[] (non-empty)
  - overall_score (number)
  - notes (optional)
- VALIDATION:
  - criteria non-empty
  - variant_scores non-empty
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/META/MUTATION/MUTATION_EVALUATION_NOTES.md

---

ARTIFACT: MUTATION_GATES_REPORT
- MUST:
  - report_id
  - version
  - gates[] (non-empty)
  - issues[] (can be empty)
  - overall (PASS|WARN|FAIL)
- Minimum required gates:
  - G1_OPERATORS_EMPTY (S0)
  - G2_SAFETY_CONSTRAINTS_MISSING (S0)
  - G3_VARIANTS_EMPTY (S0)
  - G4_NOVELTY_OUT_OF_BOUNDS (S0)
  - G5_CANON_MOD_ATTEMPT (S0)
  - G6_VAGUE_VARIANTS (S1)
- VALIDATION:
  - FAIL if any S0 fails
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/META/MUTATION/MUTATION_GATES_REPORT.md

---

## 7) PIPELINE (DETERMINISTIC)
1) Load baseline artifact/candidate set and constraints registry.
2) Define mutation operators (allowed targets + constraints).
3) Define novelty and safety constraints (bounds + forbidden actions).
4) Generate bounded variants (seeded/deterministic).
5) Evaluate variants (criteria + scores).
6) Run gates (safety, novelty bounds, canon-mod attempts).
7) Emit artifacts.

---

## 8) S0 BLOCKERS (STOP)
- S0-1: operator set empty.
- S0-2: safety constraints missing.
- S0-3: variant set empty.
- S0-4: novelty out of bounds.
- S0-5: any canon modification attempt detected.

---

## 9) INTEGRATION (SYSTEM FIT)
Upstream:
- learning provides lessons/hypotheses
- pattern extraction provides stable patterns
- optimization provides candidate context and scoring criteria

Downstream:
- learning can convert evaluations into hypotheses
- optimization can promote top variants into backlog
- governance can canonize chosen variants via change control + audit

---

## 10) REFERENCES (RAW ONLY) (OPTIONAL)
- Governance:
  00_GOVERNANCE_ENGINES/04__CHANGE_CONTROL_ENG.md
- Family template:
  10_META_EVOLUTION_ENGINES/00__TEMPLATE__ENGINE__META_EVOLUTION_ENGINES.md
- Family README:
  10_META_EVOLUTION_ENGINES/00__README__META_EVOLUTION_ENGINES.md

--- END.

LOCK: OPEN
