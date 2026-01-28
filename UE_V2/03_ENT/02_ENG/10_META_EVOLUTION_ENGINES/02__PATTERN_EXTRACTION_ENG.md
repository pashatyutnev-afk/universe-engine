# PATTERN EXTRACTION ENGINE (ENG) — CANON FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/10_META_EVOLUTION_ENGINES/02__PATTERN_EXTRACTION_ENG.md
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
UID: UE.ENG.META.PATTERN.EXTRACTION.001
OWNER: SYSTEM
ROLE: Extracts reusable patterns from executed artifacts deterministically: pattern library, pattern schemas, applicability rules, and gates. Produces stampable patterns without directly changing canon; routes improvements via governance.

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Pattern Extraction Engine created: pattern library schema, pattern templates, applicability rules, and governance-safe packaging."
- REASON: "System needs a deterministic way to capture what works and turn it into reusable stamped patterns."
- IMPACT: "Best practices become repeatable artifacts and can be applied across engines/projects."
- CHANGE_ID: UE.CHG.2026-01-08.META.PATTERN.EXTRACTION.001

---

## 0) PURPOSE (LAW)
This engine owns **PATTERN extraction artifacts**:
- identifies recurring successful structures across outputs
- packages them as reusable pattern entries (pattern library)
- defines pattern schemas (inputs/outputs) and applicability rules
- emits gates for pattern quality (testable, non-vague)
- keeps canon safe: extracted patterns do not auto-modify canon

Hard rule:
- Pattern extraction produces reusable patterns; adoption into canon uses governance pipeline.

---

## 1) NON-GOALS (HARD)
This engine does NOT:
- automatically rewrite engine files, templates, or laws
- replace learning engine (learning owns hypotheses/change candidates)
- replace optimization engine (optimization chooses changes)
- create narrative/music/visual content as primary output

FORBIDDEN:
- storing vague “tips” as patterns without schema and applicability conditions

---

## 2) MINI-CONTRACT (MANDATORY)
CONSUMES:
- ARTIFACT_SET (executed outputs) (optional)
- EXECUTION_REPORT (optional)
- QA_REPORT (optional)
- CONSISTENCY_REPORT (optional)
- LESSON_LOG (optional)

PRODUCES:
- PATTERN_LIBRARY
- PATTERN_SCHEMA_REGISTRY
- APPLICABILITY_RULESET
- PATTERN_GATES_REPORT

DEPENDS_ON:
- [10_META_EVOLUTION_ENGINES/01__LEARNING_ENG]
(soft) [00_GOVERNANCE_ENGINES/04__CHANGE_CONTROL_ENG]

OUTPUT_TARGET:
MANDATORY:
- PROJECT_ARTIFACTS/<project>/META/PATTERNS/
OPTIONAL:
- KB/META/PATTERNS (if mirrored)

Rule:
- If MINI-CONTRACT is vague → INVALID.

---

## 3) DEFINITIONS (STRICT)
- Pattern: reusable structure/solution with defined inputs, outputs, and when-to-use conditions.
- Pattern Library: catalog of patterns with IDs and metadata.
- Pattern Schema: minimal contract for a pattern (consumes/produces + fields).
- Applicability: conditions under which a pattern applies.
- Anti-pattern: pattern explicitly forbidden in some contexts.

Enums (baseline):
- pattern_type: STRUCTURE|RULESET|CHECKLIST|TEMPLATE_FRAGMENT|PIPELINE
- maturity: EXPERIMENTAL|STABLE|CANON_CANDIDATE
- severity: S0|S1|S2|S3

---

## 4) BOUNDARIES (ANTI-DUPLICATION)
IN SCOPE:
- extraction and packaging of patterns
- schema registry for patterns
- applicability and anti-applicability rules
- validation gates for pattern quality

OUT OF SCOPE (HARD):
- selecting optimizations (optimization engine)
- applying changes to canon (governance)
- generating domain content

COLLISION RULE:
- If request is “approve and apply pattern to canon templates” → governance + learning change candidates
- If request is “optimize system performance” → optimization engine

---

## 5) RULESET (THE LAW)
R1 (HARD) MUST: PATTERN_LIBRARY entries are testable and include inputs/outputs.
R2 (HARD) MUST: PATTERN_SCHEMA_REGISTRY defines required schema fields per pattern type.
R3 (HARD) MUST: APPLICABILITY_RULESET defines when-to-use and when-forbidden per pattern.
R4 (HARD) FORBIDDEN: patterns without explicit applicability conditions.
R5 (HARD) MUST: gates detect vague patterns and missing schema fields.
R6 (SOFT) SHOULD: include evidence refs showing pattern effectiveness.
R7 (HARD) MUST: no direct canon modification actions inside patterns.

---

## 6) REQUIRED OUTPUT SCHEMAS (MINIMUM)

ARTIFACT: PATTERN_LIBRARY
- MUST:
  - library_id
  - version
  - patterns[] (non-empty)
  - checks[] (non-empty)
- PATTERN (minimum):
  - pattern_id
  - name
  - pattern_type (STRUCTURE|RULESET|CHECKLIST|TEMPLATE_FRAGMENT|PIPELINE)
  - maturity (EXPERIMENTAL|STABLE|CANON_CANDIDATE)
  - summary (testable)
  - consumes[] (0..N artifact types)
  - produces[] (0..N artifact types)
  - steps[] (non-empty; testable)
  - applicability_ref (required)
  - anti_applicability_ref (optional)
  - evidence_refs[] (optional but recommended)
  - severity_if_misused (S0|S1|S2|S3)
- VALIDATION:
  - patterns non-empty
  - each pattern has steps non-empty and applicability_ref
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/META/PATTERNS/PATTERN_LIBRARY.md

---

ARTIFACT: PATTERN_SCHEMA_REGISTRY
- MUST:
  - registry_id
  - version
  - schema_defs[] (non-empty)
  - checks[] (non-empty)
- SCHEMA DEF (minimum):
  - schema_id
  - pattern_type
  - required_fields[] (non-empty)
  - optional_fields[] (optional)
  - validation_rules[] (non-empty)
- VALIDATION:
  - schema_defs non-empty
  - required_fields non-empty
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/META/PATTERNS/PATTERN_SCHEMA_REGISTRY.md

---

ARTIFACT: APPLICABILITY_RULESET
- MUST:
  - ruleset_id
  - version
  - rules[] (non-empty)
  - checks[] (non-empty)
- RULE (minimum):
  - rule_id
  - pattern_id
  - type (APPLIES_WHEN|FORBIDDEN_WHEN)
  - condition (testable)
  - severity_if_violated (S0|S1|S2|S3)
- VALIDATION:
  - rules non-empty
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/META/PATTERNS/APPLICABILITY_RULESET.md

---

ARTIFACT: PATTERN_GATES_REPORT
- MUST:
  - report_id
  - version
  - gates[] (non-empty)
  - issues[] (can be empty)
  - overall (PASS|WARN|FAIL)
- Minimum required gates:
  - G1_LIBRARY_EMPTY (S0)
  - G2_SCHEMA_REGISTRY_EMPTY (S0)
  - G3_APPLICABILITY_RULES_EMPTY (S0)
  - G4_VAGUE_PATTERN (S1)
  - G5_CANON_MOD_ACTION_PRESENT (S0)
- VALIDATION:
  - FAIL if any S0 fails
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/META/PATTERNS/PATTERN_GATES_REPORT.md

---

## 7) PIPELINE (DETERMINISTIC)
1) Collect artifact sets and reports.
2) Extract candidate patterns (recurring structures with positive outcomes).
3) Normalize into pattern entries (steps + inputs/outputs).
4) Define schema definitions and applicability rules.
5) Run gates (vague patterns, missing applicability, canon-mod action).
6) Emit artifacts.

---

## 8) S0 BLOCKERS (STOP)
- S0-1: pattern library empty.
- S0-2: schema registry empty.
- S0-3: applicability rules empty.
- S0-4: any pattern includes direct canon modification instruction.
- S0-5: produced artifacts missing schemas/storage targets.

---

## 9) INTEGRATION (SYSTEM FIT)
Upstream:
- learning outputs (lessons) and executed artifact sets

Downstream:
- optimization engine can choose which patterns to adopt
- governance pipeline can canonize patterns into templates/rules via change control + audit

---

## 10) REFERENCES (RAW ONLY) (OPTIONAL)
- Governance routing:
  00_GOVERNANCE_ENGINES/04__CHANGE_CONTROL_ENG.md
- Family template:
  10_META_EVOLUTION_ENGINES/00__TEMPLATE__ENGINE__META_EVOLUTION_ENGINES.md
- Family README:
  10_META_EVOLUTION_ENGINES/00__README__META_EVOLUTION_ENGINES.md

--- END.

LOCK: OPEN
