# TECHNOLOGY & MAGIC ENGINE (ENG) — CANON FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/04_DOMAIN_WORLD_ENGINES/08__TECHNOLOGY_MAGIC_ENG.md
SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
DOC_TYPE: ENGINE
FAMILY: 04_DOMAIN_WORLD_ENGINES
CLASS: DOMAIN (L2)
LEVEL: L2
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.ENG.DOM.WORLD.TECH.MAGIC.001
OWNER: SYSTEM
ROLE: Defines deterministic technology and/or magic systems: capabilities, constraints, costs, prerequisites, failure modes, and epoch-scoped availability, fully compliant with WORLD_LAWSET.

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Technology & Magic Engine created: capability catalog, constraint/cost model, prerequisites, safety/failure modes, and epoch availability map."
- REASON: "World needs explicit capability rules; 'magic/tech' cannot be handwaved under canon constraints."
- IMPACT: "Narrative and production can use tech/magic consistently without breaking world laws."
- CHANGE_ID: UE.CHG.2026-01-08.DOM.WORLD.TECH.MAGIC.001

---

## 0) PURPOSE (LAW)
This engine owns **technology and/or magic** as deterministic systems:
- capability catalog (what can be done)
- prerequisites (what is required)
- constraints (limits, laws, conditions)
- costs (resources, time, risk, side effects)
- failure modes (what breaks and how)
- availability over epochs/civilizations/regions

Hard rule:
- Tech/magic MUST comply with `WORLD_LAWSET` and causality constraints; no “because magic”.

---

## 1) NON-GOALS (HARD)
This engine does NOT:
- redefine world laws or add hard exceptions silently (02 owns law; exceptions must follow protocol)
- define economy/resource allocation as primary (07 owns)
- define civilization governance as primary (04 owns)
- define narrative beats/scenes that use tech/magic (narrative family)
- define production implementation of VFX/audio (production family)

---

## 2) MINI-CONTRACT (MANDATORY)
CONSUMES:
- WORLD_STRUCTURE_MODEL
- WORLD_LAWSET
- CAUSALITY_CONSTRAINTS
- TIMELINE_EPOCH_MODEL
- CIVILIZATION_MODEL_SET (optional but recommended)
- ECONOMY_RESOURCE_MODEL (optional)
- TECHNOLOGY_MAGIC_SEEDS (optional)

PRODUCES:
- TECHNOLOGY_MAGIC_MODEL
- CAPABILITY_CATALOG
- PREREQUISITE_CONSTRAINT_MAP
- COST_FAILURE_MODEL
- AVAILABILITY_MAP

DEPENDS_ON:
- [04_DOMAIN_WORLD_ENGINES/02__WORLD_LAW_ENG, 04_DOMAIN_WORLD_ENGINES/03__TIMELINE_EPOCH_ENG, 04_DOMAIN_WORLD_ENGINES/07__ECONOMY_RESOURCE_ENG]

OUTPUT_TARGET:
MANDATORY:
- PROJECT_ARTIFACTS/<project>/WORLD/TECH_MAGIC/
OPTIONAL:
- KB/TECH_MAGIC (if mirrored)

Rule:
- If MINI-CONTRACT is vague → INVALID.

---

## 3) DEFINITIONS (STRICT)
- Capability: an action or effect the system enables (move, transform, sense, create, destroy).
- Prerequisite: required condition/input before capability can execute.
- Constraint: rule limiting capability (range, time, energy, legality, rarity).
- Cost: resource/time/risk/side effect paid per use or per maintenance.
- Failure Mode: how the capability fails and what consequence results.
- Availability: which civilizations/epochs/regions can access or reproduce it.
- Tech/Magic Medium: the substrate enabling the capability (energy, materials, information, “magic medium” if canon allows).

---

## 4) BOUNDARIES (ANTI-DUPLICATION)
IN SCOPE:
- tech/magic capability definitions
- prerequisites and constraints
- costs and failure modes
- availability mapping by epoch/region/civ
- compliance checks vs world laws

OUT OF SCOPE (HARD):
- changing world laws (02) without protocol
- narrative usage planning (narrative)
- production depiction (VFX/audio/lighting)
- detailed manufacturing economy (07 owns) — this engine references resource prerequisites only

COLLISION RULE:
- If a capability violates world laws → either:
  - mark as impossible, or
  - create explicit exception type via law protocol (not owned here)
- If a capability depends on resources/logistics → route prerequisites to economy engine references
- If a capability depends on civilization institutions → reference civ/institution outputs

---

## 5) RULESET (THE LAW)
R1 (HARD) MUST: CAPABILITY_CATALOG exists; each capability has prerequisites, constraints, costs, and failure modes.
R2 (HARD) MUST: PREREQUISITE_CONSTRAINT_MAP binds every capability to world laws/causality constraints.
R3 (HARD) MUST: COST_FAILURE_MODEL makes costs explicit and testable (no “it is tiring” without proxy).
R4 (HARD) MUST: AVAILABILITY_MAP declares who/where/when has access.
R5 (HARD) FORBIDDEN: “magic solves anything” — capabilities must have limits and costs.
R6 (HARD) FORBIDDEN: introducing hidden exception to world laws.
R7 (HARD) MUST: epoch variants declared or explicitly invariant.
R8 (SOFT) SHOULD: include safety and misuse constraints (risk safety).
R9 (HARD) MUST: outputs must reference world law ids for compliance.

---

## 6) REQUIRED OUTPUT SCHEMAS (MINIMUM)

ARTIFACT: TECHNOLOGY_MAGIC_MODEL
- MUST:
  - model_id
  - version
  - system_type (enum: TECHNOLOGY|MAGIC|HYBRID)
  - mediums[] (non-empty)
  - capability_catalog_ref
  - availability_ref
  - compliance_checks_ref
  - open_unknowns[] (optional)
- MEDIUM (minimum):
  - medium_id
  - name
  - category (enum: ENERGY|MATTER|INFORMATION|BIOLOGY|MAGIC_MEDIUM)
  - constraints[] (law ids)
  - measurement_proxy
  - notes
- VALIDATION:
  - system_type consistent with mediums (MAGIC requires MAGIC_MEDIUM or explicit rationale)
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/WORLD/TECH_MAGIC/TECHNOLOGY_MAGIC_MODEL.md

ARTIFACT: CAPABILITY_CATALOG
- MUST:
  - catalog_id
  - version
  - capabilities[] (non-empty)
  - anti_patterns[] (optional)
  - checks[] (non-empty)
- CAPABILITY (minimum):
  - capability_id
  - name
  - category (enum: MOVE|SENSE|TRANSFORM|CREATE|DESTROY|HEAL|SHIELD|COMMUNICATE|CONTROL)
  - description (testable)
  - prerequisites[] (non-empty)
  - constraints[] (non-empty)
  - costs[] (non-empty)
  - failure_modes[] (non-empty)
  - law_refs[] (non-empty)
  - epoch_variants[] (optional)
  - notes
- VALIDATION:
  - each capability lists law_refs and at least one constraint
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/WORLD/TECH_MAGIC/CAPABILITY_CATALOG.md

ARTIFACT: PREREQUISITE_CONSTRAINT_MAP
- MUST:
  - map_id
  - version
  - entries[] (non-empty)
  - checks[] (non-empty)
- ENTRY (minimum):
  - capability_id
  - prerequisites[] (structured)
  - constraints[] (structured)
  - causality_refs[] (optional)
  - forbidden_conditions[] (optional)
  - notes
- PREREQUISITE (minimum):
  - type (RESOURCE|MEDIUM|SKILL|INSTITUTION|LOCATION|TIME_WINDOW|RITUAL|DEVICE)
  - ref (resource_id/medium_id/etc.)
  - amount_proxy (optional)
  - condition (optional)
- CONSTRAINT (minimum):
  - type (RANGE|DURATION|ENERGY|FREQUENCY|LEGAL|RARITY|ENVIRONMENT|ALIGNMENT)
  - expression (testable)
  - severity (S0|S1|S2|S3)
- VALIDATION:
  - every capability has an entry
  - any S0 constraint must cite a law_ref or causality constraint
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/WORLD/TECH_MAGIC/PREREQUISITE_CONSTRAINT_MAP.md

ARTIFACT: COST_FAILURE_MODEL
- MUST:
  - cf_id
  - version
  - cost_types[] (non-empty)
  - failure_types[] (non-empty)
  - mappings[] (non-empty)
  - checks[] (non-empty)
- COST TYPE (minimum):
  - cost_id
  - type (RESOURCE|TIME|RISK|SIDE_EFFECT|MAINTENANCE|SOCIAL|ENVIRONMENTAL)
  - measurement_proxy
  - notes
- FAILURE TYPE (minimum):
  - failure_id
  - type (MISFIRE|BACKLASH|DEGRADATION|EXHAUSTION|CONTAMINATION|ESCALATION|EXPOSURE)
  - consequence (testable)
  - severity (S0|S1|S2|S3)
- MAPPING (minimum):
  - capability_id
  - costs[] (cost_id with amounts/proxies)
  - failure_modes[] (failure_id with triggers)
  - mitigation_options[] (optional)
- VALIDATION:
  - each capability mapped
  - any S0 failure has mitigation or explicit “unmitigable” rationale
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/WORLD/TECH_MAGIC/COST_FAILURE_MODEL.md

ARTIFACT: AVAILABILITY_MAP
- MUST:
  - availability_id
  - version
  - entries[] (non-empty)
  - checks[] (non-empty)
- ENTRY (minimum):
  - capability_id
  - scope (GLOBAL|REGIONAL|LOCAL)
  - epoch_ids[] (non-empty or explicit ALL)
  - civ_refs[] (optional)
  - region_refs[] (optional)
  - access_mode (enum: COMMON|RESTRICTED|SECRET|RITUAL|INSTITUTIONAL|WILD)
  - reproduction_difficulty (0..100)
  - notes
- VALIDATION:
  - epoch ids exist
  - if restricted, must specify civ or institution owner
- STORAGE:
  - PROJECT_ARTIFACTS/<project>/WORLD/TECH_MAGIC/AVAILABILITY_MAP.md

---

## 7) PIPELINE (DETERMINISTIC)
1) Validate inputs:
   - world laws + epochs exist
2) Define mediums:
   - list substrates + measurement proxies
3) Define capabilities:
   - per capability: prerequisites, constraints, costs, failure modes
4) Bind compliance:
   - map capability → law_refs + causality constraints
5) Define availability:
   - per epoch and civ/region
6) Run checks:
   - contradictions, missing costs, hidden exceptions
7) Emit artifacts

---

## 8) S0 BLOCKERS (STOP)
- S0-1: capability violates hard world law with no exception protocol.
- S0-2: capability missing prerequisites/constraints/costs/failure modes.
- S0-3: any S0 constraint lacks law_ref/cause.
- S0-4: availability map references unknown epoch ids.
- S0-5: “unbounded” capability (no limits) is declared.

---

## 9) INTEGRATION (SYSTEM FIT)
Upstream:
- world law + causality (02)
- epochs (03)
- economy/resources (07) (for prerequisites and maintenance)
- civ institutions (04) (for access mode)

Downstream consumers:
- conflict/power (05) (capabilities as power sources)
- geopolitics (06) (movement/communication constraints)
- ecology (10) (environment constraints and side effects)
- narrative engines (use capabilities as allowed tools, not as plot hacks)

Governance:
- if adding a capability implies changing hard laws → governance change control + audit must occur (outside this engine).

---

## 10) REFERENCES (RAW ONLY) (OPTIONAL)
- Family template:
  04_DOMAIN_WORLD_ENGINES/00__TEMPLATE__ENGINE__DOMAIN_WORLD_ENGINES.md

--- END.

LOCK: OPEN
