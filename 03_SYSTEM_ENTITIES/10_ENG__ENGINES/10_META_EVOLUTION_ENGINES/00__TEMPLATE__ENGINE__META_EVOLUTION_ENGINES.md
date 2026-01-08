# META EVOLUTION ENGINES — ENGINE TEMPLATE (ENG) — CANON
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/10_META_EVOLUTION_ENGINES/00__TEMPLATE__ENGINE__META_EVOLUTION_ENGINES.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
DOC_TYPE: TEMPLATE
FAMILY: 10_META_EVOLUTION_ENGINES
CLASS: META (L4)
LEVEL: L4
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.ENG.META.TPL.ENGINE.001
OWNER: SYSTEM
ROLE: Mandatory template for META EVOLUTION engines. Defines how the system learns, extracts patterns, optimizes, mutates creatively, and projects futures WITHOUT violating governance canon rules. Enforces strict boundaries and output schemas.

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Meta Evolution engine template standardized: governance-safe meta layer, strict boundaries, mini-contract, output schemas, and S0 blockers."
- REASON: "Prevent meta engines from silently rewriting canon or becoming a second governance layer."
- IMPACT: "Meta engines become safe advisors/optimizers with deterministic integration."
- CHANGE_ID: UE.CHG.2026-01-08.META.TPL.ENGINE.001

---

## 0) HOW TO USE (MANDATORY)

1) Copy this template to create a new engine file in this family.
2) Replace placeholders strictly (title, FILE path, UID, ROLE).
3) Fill MINI-CONTRACT with concrete artifacts.
4) Declare boundaries: meta engines propose/optimize but do NOT change canon directly.
5) Any canon change must route through governance pipeline (Change Control).

Rule:
- Missing required sections => engine is incomplete (non-canon).

---

## 1) ENGINE FILE TEMPLATE (COPY FROM HERE)

# <ENGINE TITLE> (ENG) — CANON
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/10_META_EVOLUTION_ENGINES/NN__<ENGINE_NAME>_ENG.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
DOC_TYPE: ENGINE
FAMILY: 10_META_EVOLUTION_ENGINES
CLASS: META (L4)
LEVEL: L4
STATUS: DRAFT
LOCK: OPEN
VERSION: 0.1.0
UID: UE.ENG.META.<ENGINE_KEY>.001
OWNER: SYSTEM
ROLE: <one sentence: what meta capability this engine defines and guarantees>

CHANGE_NOTE:
- DATE: YYYY-MM-DD
- TYPE: PATCH|MINOR|MAJOR|MIGRATION|EMERGENCY
- SUMMARY: "<what changed / what was defined>"
- REASON: "<why>"
- IMPACT: "<what this affects>"
- CHANGE_ID: UE.CHG.YYYY-MM-DD.META.<ENGINE_KEY>.<SEQ>

---

## 0) PURPOSE (LAW)

Meta engines exist to improve the system itself:
- learning from outputs, constraints, failures
- extracting reusable patterns
- optimizing workflows and artifact schemas
- proposing safe mutations and alternatives
- projecting future outcomes/risks

Meta engines do NOT directly rewrite canon. They produce proposals and reports.

---

## 1) NON-GOALS (HARD)

This engine does NOT:
- approve canon changes (Decision Approval / Canon Authority)
- execute canon changes (Change Control governs)
- redefine authority hierarchy (Rule Hierarchy governs)
- bypass audit/memory/versioning (governance owns)
- replace domain families (narrative/character/world/expression/style/production)
- act as “second single source of truth” for any layer

---

## 2) MINI-CONTRACT (MANDATORY)

CONSUMES:
- <1–7 inputs; named artifacts>
  - Example: AUDIT_LOG_ENTRY, CHANGE_PACKAGE, QUALITY_REPORTS, OUTPUT_PACKS, PIPELINE_RUN_SUMMARY

PRODUCES:
- <1–7 outputs; meta artifacts>
  - Example: PATTERN_REPORT, OPTIMIZATION_PROPOSAL, MUTATION_CANDIDATES, FUTURE_RISK_FORECAST, LEARNING_NOTES

DEPENDS_ON:
- <engine paths> or []
  - Meta engines often depend on governance engines as reference/inputs (not authority).

OUTPUT_TARGET:
MANDATORY:
- <where meta outputs are stored in project/system logs>
  - Example: 99_LOGS/LOG__CHANGES.md, 99_LOGS/LOG__AUDIT.md, or a dedicated meta report file path

OPTIONAL:
- <assistive notes; never overrides canon>

Rule:
- If MINI-CONTRACT is vague → INVALID.

---

## 3) DEFINITIONS (STRICT)

Meta artifacts must be explicit:

- PROPOSAL: a suggested change (never applied automatically)
- PATTERN: reusable observation with evidence
- OPTIMIZATION: a change that improves efficiency/quality without changing meaning unless stated
- MUTATION: a controlled variant candidate with risk and rollback plan
- FORECAST: a prediction with assumptions and confidence bounds

Meta outputs must always include:
- evidence basis (inputs used)
- assumptions
- risk level
- recommended next action (route)

---

## 4) BOUNDARIES (ANTI-DUPLICATION)

IN SCOPE:
- analysis of system behavior and artifact quality
- proposal generation and comparison
- pattern extraction from outputs/logs
- optimization suggestions (schema, workflow, ordering)

OUT OF SCOPE (HARD):
- enforcing approvals
- changing indexes/laws directly
- writing domain content as primary (stories, world laws, character dossiers)

Collision rule:
- If a meta output implies a canon change, it must produce a CHANGE_PROPOSAL and route to Change Control.

---

## 5) RULESET (THE LAW)

Write numbered rules using MUST/FORBIDDEN/ALLOWED:

- R1 (HARD): Meta engines MUST NOT modify canon artifacts directly.
- R2 (HARD): Any proposed canon change MUST be packaged as a change proposal with targets and impact.
- R3 (HARD): Meta outputs MUST include evidence + assumptions.
- R4 (SOFT): Prefer reversible optimizations unless justified.

Add family-specific rules as needed.

---

## 6) REQUIRED OUTPUT SCHEMAS (MINIMUM)

For each produced artifact:

ARTIFACT: <NAME>
- MUST: evidence[], assumptions[], recommendation, risk_level, affected_targets?
- OPTIONAL: confidence, alternatives[], rollback_hint
- VALIDATION: missing evidence => invalid

Example:
ARTIFACT: OPTIMIZATION_PROPOSAL
- MUST: proposal_id, targets[], summary, reason, impact, compatibility, risk_level, next_action_route
- VALIDATION: missing targets => invalid

---

## 7) PROCESS (DETERMINISTIC)

1) Intake + validation of inputs
2) Extract signals (patterns, failures, repetitions)
3) Generate candidate improvements (proposals/mutations)
4) Score candidates (risk/impact/compatibility)
5) Emit meta artifacts with schemas
6) Route:
   - if canon change suggested → Change Control pipeline
   - if local improvement → recommended action only

---

## 8) QUALITY GATES (MANDATORY)

G1 — Governance Safety Gate:
- no direct canon writes
- no hidden “auto-approve” logic

G2 — Evidence Gate:
- evidence and assumptions must exist

G3 — Clarity Gate:
- outputs must be actionable (next action route)

G4 — Compatibility Gate:
- must declare backward/breaking/mixed when relevant

---

## 9) S0 BLOCKERS (STOP)

S0-1: Meta engine modifies canon artifacts directly  
S0-2: Meta engine claims authority to approve or override governance  
S0-3: Output has no evidence/assumptions fields  
S0-4: Hidden dependencies not declared  
S0-5: Engine numbering mismatch vs index/filename  

---

## 10) INTEGRATION (SYSTEM FIT)

Inputs from:
- governance logs (audit/memory/change packages)
- quality/validation reports
- pipeline outcomes

Outputs consumed by:
- governance change control (as proposals)
- owners of families (as recommendations)
- future projection planning (as forecasts)

Meta layer is advisory + optimization layer, not authority.

---

## 11) REFERENCES (RAW ONLY) (OPTIONAL)

- <raw links>

--- END.

---

## 2) TEMPLATE QUALITY CHECK (FAST)

Before setting a meta engine ACTIVE:
- [ ] Header schema correct
- [ ] MINI-CONTRACT concrete
- [ ] Governance-safety boundaries explicit
- [ ] Output schemas defined
- [ ] S0 blockers listed
