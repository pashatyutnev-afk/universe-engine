# 🧪 SCIENTIFIC PLAUSIBILITY ENGINE
## Canonical Engine Specification  
**LEVEL: L4 · VALIDATION ENGINE · PHYSICS/BIO/ENG GATES · MACHINE-GRADE**

---

## 0. CANONICAL STATUS

- ENGINE_FILE: 06__SCIENTIFIC_PLAUSIBILITY_ENG.md
- ENGINE_ID: L4-VAL-SCIENTIFIC-PLAUSIBILITY-ENGINE-006
- UID: UE.ENT.ENG.VAL.SCIENTIFIC_PLAUSIBILITY
- NAME: Scientific Plausibility Engine
- CLASS: Validation Engine
- LEVEL: L4
- STATUS: FINAL
- FAILURE_MODE: fail-closed (impossible claims)
- EDITABLE: true

### ABSOLUTE RULE
> If a claim breaks declared physics without a declared override — it is invalid.

---

## 1. PURPOSE

Scientific Plausibility Engine validates whether an artifact:
- is compatible with declared science rules of the world
- does not contain unhandled physical/biological/engineering impossibilities
- declares assumptions when needed
- tags “rule overrides” (magic/tech exceptions) explicitly
- provides repair actions: constrain, justify, or declare divergence

This engine does not require hard science unless the world mode demands it.  
It enforces **consistency with the declared plausibility mode**.

---

## 2. RESPONSIBILITY SCOPE

### IN-SCOPE (ALLOWED)
- Validate claims against declared plausibility mode (hard/soft/fantasy-override)
- Detect violations in:
  - physics (energy, momentum, causality, relativity basics)
  - engineering (materials, structural limits, heat/power)
  - biology/medicine (if present)
  - astronomy/planet environments (if present)
- Require assumptions registry for unsupported claims
- Require explicit override tags for “magic tech” exceptions
- Output verdict, severity, repair plan, recheck gates

### OUT-OF-SCOPE (FORBIDDEN)
- Historical accuracy (Historical Accuracy Engine)
- Cultural framing (Cultural Accuracy Engine)
- Fact truth vs canon (Fact Consistency Engine)
- Writing the science itself (it validates spec discipline)

---

## 3. INPUT / OUTPUT

### 3.1 INPUT — SCIENCE_VALIDATION_REQUEST
Required fields:
- `sv_req_id`
- `timestamp`
- `artifact_ref`
- `artifact_type`
- `artifact_payload`
- `plausibility_mode_profile` (required)
- `world_law_refs` (optional but recommended)
- `assumption_policy_ref` (optional)
- `canon_override_registry_ref` (optional)
- `trace_id` (optional)

Missing plausibility_mode_profile → INVALID (CRITICAL).

### 3.2 OUTPUT — VALIDATION_VERDICT
(uses realm README canonical schema)

---

## 4. PLAUSIBILITY MODE PROFILE (REQUIRED)

### 4.1 PLAUSIBILITY_MODE_PROFILE (required fields)
- `mode_id`
- `mode` = HARD_SCI | SOFT_SCI | FANTASY_OVERRIDE | GAME_LOGIC
- `allowed_overrides` (list)
- `forbidden_overrides` (list)
- `hard_constraints` (list; e.g., “no FTL”, “conservation holds”)
- `soft_constraints` (list; e.g., “handwave allowed if consistent”)
- `evidence_requirement_level` = LOW | MEDIUM | HIGH (optional)
- `notes`

Hard rule:
- mode must be one of allowed enums.

---

## 5. CLAIM EXTRACTION (SCIENCE-SENSITIVE)

The engine extracts science-sensitive claims:
- energy sources
- propulsion
- gravity control
- weapons effects
- healing/biology
- materials and mega-structures
- environment survivability

Each extracted item becomes a **SCI_CLAIM**.

---

## 6. SCI_CLAIM MODEL

### 6.1 SCI_CLAIM (required fields)
- `sci_claim_id`
- `claim_text`
- `domain` = PHYSICS | ENGINEERING | BIOLOGY | ASTRONOMY | CHEMISTRY | OTHER
- `normalized_claim`
- `scope_ref`
- `time_ref` (optional)
- `assumptions_refs` (optional)
- `override_tag_ref` (optional)
- `confidence` (0–1)
- `source_location_ref`
- `status` = PLAUSIBLE | QUESTIONABLE | IMPOSSIBLE | OVERRIDE_DECLARED

Hard rule:
- each sci_claim must have source_location_ref.

---

## 7. GATES BY MODE

### 7.1 HARD_SCI MODE
Rules:
- require explicit assumptions for any non-trivial tech
- forbid violations of declared hard constraints
- questionable claims must be bounded (limits, costs, side effects)
- energy/propulsion must have cost model conceptually (no “free”)

Unhandled hard-constraint violation → CRITICAL.

### 7.2 SOFT_SCI MODE
Rules:
- handwaving allowed, but must remain consistent
- overrides allowed, but must be declared once and reused consistently
- avoid “new power every episode” without registry

Contradictory handwaves → HIGH.

### 7.3 FANTASY_OVERRIDE MODE
Rules:
- physics violations allowed only through declared override system
- override must have rules, limits, and failure modes (even if minimal)
- forbidden: “anything happens because magic” without constraints

Override missing → HIGH/CRITICAL depending on impact.

### 7.4 GAME_LOGIC MODE
Rules:
- allow game abstractions (HP, mana, cooldowns)
- must be internally consistent and numerically coherent if numbers exist
- exploits/edge cases should be flagged as balance risk (optional)

---

## 8. ASSUMPTION REGISTRY (MANDATORY WHEN NEEDED)

### 8.1 ASSUMPTION_POLICY (default)
If a claim is not demonstrably plausible in the chosen mode:
- it must be supported by:
  - assumptions, or
  - declared override tag

### 8.2 ASSUMPTION OBJECT (canonical)
- `assumption_id`
- `statement`
- `domain`
- `scope_ref`
- `limits` (required in HARD_SCI / recommended otherwise)
- `costs` (optional)
- `failure_modes` (optional)
- `evidence_refs` (optional)
- `status` = DECLARED | MISSING | CONTRADICTED

Missing required assumptions → HIGH/CRITICAL depending on mode.

---

## 9. OVERRIDE TAGS (CANONICAL)

### 9.1 OVERRIDE_TAG OBJECT
- `override_id`
- `name`
- `rule_set_ref` (must exist)
- `allowed_effects`
- `forbidden_effects`
- `limits`
- `costs`
- `failure_modes`
- `scope_ref`

Hard rule:
- override without limits in HARD_SCI/SOFT_SCI → HIGH.

---

## 10. COMMON SCIENCE FAILURES (DETECTION)

- free energy (no cost)
- perpetual motion
- reactionless propulsion (without declared override)
- instant travel/communication breaking declared constraints
- gravity control without constraints (in modes that require it)
- biology “instant heal” without limits (if mode requires)
- mega-structures without material/engineering allowances (in hard modes)
- environment survivability mismatch (vacuum, radiation) without mitigation

---

## 11. SEVERITY & VERDICT RULES

CRITICAL:
- violates declared hard constraints without override
- requires override but none declared
- contradictions between two science claims that cannot co-exist in the mode

HIGH:
- missing assumptions registry where required
- override declared but lacks rule set/limits (mode dependent)
- engineering impossibility in hard mode without constraints

MEDIUM:
- questionable claim with weak bounding
- unclear costs/limits in soft modes

LOW:
- minor terminology sloppiness (handled mostly by Language Engine)

Verdict:
- any CRITICAL → INVALID
- multiple HIGH → INVALID/PARTIAL depending on fix locality
- only MEDIUM/LOW → PARTIAL/VALID

---

## 12. OUTPUT: ISSUES + REPAIR PLAN

### 12.1 ISSUE ITEM (science)
- `issue_id`
- `type` = HARD_CONSTRAINT_VIOLATION | IMPOSSIBLE_CLAIM | ASSUMPTION_MISSING | OVERRIDE_MISSING | OVERRIDE_UNBOUNDED | INTERNAL_SCI_CONTRADICTION | COST_MODEL_MISSING
- `location_ref`
- `claim_ids_involved` (list)
- `description`
- `severity`
- `fix`

### 12.2 REPAIR ACTION TYPES
- `DECLARE_PLAUSIBILITY_MODE_PROFILE`
- `ADD_ASSUMPTION_WITH_LIMITS`
- `ADD_OVERRIDE_TAG_AND_RULES`
- `BOUND_CLAIM_WITH_COSTS_AND_LIMITS`
- `REMOVE_OR_DOWNGRADE_CLAIM`
- `ALIGN_WITH_WORLD_LAW`

Hard rule:
- fix must specify exact limits/costs or exact override rule-set reference.

---

## 13. CORE OPERATIONS

- OP_01: INGEST_ARTIFACT_AND_MODE_PROFILE
- OP_02: EXTRACT_SCIENCE_SENSITIVE_CLAIMS
- OP_03: NORMALIZE_SCI_CLAIMS (domain/scope)
- OP_04: APPLY_MODE_GATES (hard/soft/fantasy/game)
- OP_05: CHECK_HARD_CONSTRAINTS (if any)
- OP_06: CHECK_ASSUMPTION_REGISTRY (needed claims)
- OP_07: CHECK_OVERRIDE_TAGS_AND_RULESETS
- OP_08: DETECT_INTERNAL_SCI_CONTRADICTIONS
- OP_09: BUILD_ISSUES_LIST
- OP_10: ASSIGN_SEVERITY_AND_VERDICT
- OP_11: BUILD_REPAIR_PLAN
- OP_12: EMIT_VALIDATION_VERDICT

---

## 14. FAILURE CONDITIONS (ENGINE)

CRITICAL:
- plausibility_mode_profile missing
- artifact payload missing
- world law refs required by policy but not provided

Reaction:
- verdict INVALID (CRITICAL)
- request mode profile and world law refs

---

## 15. NON-GOALS
- Does not fully model physics
- Does not research external sources
- Does not decide canon changes
- Does not validate culture/history

---

## 16. FINAL STATEMENT

Plausibility is not “real science”.
It is rule consistency with declared constraints.
Declare the rules — or the world breaks.

---

**STATUS:** Scientific Plausibility Engine v1.0  
**REALM:** ACTIVE
