# DOMAIN WORLD ENGINES — ENGINE TEMPLATE (ENG) — CANON
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/04_DOMAIN_WORLD_ENGINES/00__TEMPLATE__ENGINE__DOMAIN_WORLD_ENGINES.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
DOC_TYPE: TEMPLATE
FAMILY: 04_DOMAIN_WORLD_ENGINES
CLASS: DOMAIN (L2)
LEVEL: L2
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.ENG.DOM.WORLD.TPL.ENGINE.001
OWNER: SYSTEM
ROLE: Mandatory template for DOMAIN WORLD engines. Enforces canonical header schema, mini-contract law, world-domain boundaries, output schemas, and raw-only references to prevent drift.

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Domain World engine template standardized: governance-style header, strict mini-contract, boundaries, outputs, and S0 blockers."
- REASON: "Prevent drift and stop overlaps with Narrative/Character/Expression/Production and Governance/CORE."
- IMPACT: "All world engines become uniform, composable, and compatible with CORE + GOVERNANCE."
- CHANGE_ID: UE.CHG.2026-01-08.DOM.WORLD.TPL.ENGINE.001

---

## 0) HOW TO USE (MANDATORY)

1) Copy this template to create a new engine file in this family.
2) Replace placeholders strictly (title, FILE path, UID, ROLE).
3) Fill MINI-CONTRACT with concrete artifacts (no vague words).
4) Declare boundaries to avoid overlap with:
   - CORE (system identity/state/lifecycle)
   - GOVERNANCE (authority/pipeline/audit)
   - NARRATIVE (story structure/continuity as primary)
   - CHARACTER (psychology/motivation/dialogue as primary)
   - EXPRESSION (event mechanics primitives)
   - PRODUCTION (media implementation)
5) Add raw-only references where index navigation requires it.

Rule:
- Missing required sections => engine is incomplete (non-canon).

---

## 1) ENGINE FILE TEMPLATE (COPY FROM HERE)

# <ENGINE TITLE> (ENG) — CANON
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/04_DOMAIN_WORLD_ENGINES/NN__<ENGINE_NAME>_ENG.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
DOC_TYPE: ENGINE
FAMILY: 04_DOMAIN_WORLD_ENGINES
CLASS: DOMAIN (L2)
LEVEL: L2
STATUS: DRAFT
LOCK: OPEN
VERSION: 0.1.0
UID: UE.ENG.DOM.WORLD.<ENGINE_KEY>.001
OWNER: SYSTEM
ROLE: <one sentence: what world capability this engine defines and guarantees>

CHANGE_NOTE:
- DATE: YYYY-MM-DD
- TYPE: PATCH|MINOR|MAJOR|MIGRATION|EMERGENCY
- SUMMARY: "<what changed / what was defined>"
- REASON: "<why>"
- IMPACT: "<what this affects>"
- CHANGE_ID: UE.CHG.YYYY-MM-DD.DOM.WORLD.<ENGINE_KEY>.<SEQ>

---

## 0) PURPOSE (LAW)

- Define the world capability this engine owns (strict).
- Define guarantees (bullets).
- Define non-goals (explicit).

---

## 1) NON-GOALS (HARD)

This engine does NOT:
- define system identity/state/lifecycle (CORE)
- define authority/approvals/pipeline/audit/memory (GOVERNANCE)
- define narrative macro-structure/continuity as primary (NARRATIVE owns)
- define character psychology/motivation/dialogue as primary (CHARACTER owns)
- define event mechanics primitives (EXPRESSION owns)
- define media implementation (camera/editing/sound) as primary (PRODUCTION owns)

---

## 2) MINI-CONTRACT (MANDATORY)

CONSUMES:
- <1–7 inputs; named artifacts>
  - Example: WORLD_CONSTRAINTS, TIMELINE_CONTEXT, FACTION_MAP, TECH_LEVEL_RULES

PRODUCES:
- <1–7 outputs; reusable artifacts>
  - Example: WORLD_RULES, CIVILIZATION_MODEL, ECONOMY_RESOURCE_MODEL, ECOLOGY_MODEL

DEPENDS_ON:
- <engine paths> or []
  - Prefer CORE prereqs where required.

OUTPUT_TARGET:
MANDATORY:
- <project storage targets, e.g. 05_PROJECTS/...>

OPTIONAL:
- <assistive notes; never overrides canon>

Rule:
- If MINI-CONTRACT is vague → INVALID.

---

## 3) DEFINITIONS (STRICT)

- Define only terms this engine owns.
- If a term belongs to another family, reference it (do not redefine).

---

## 4) BOUNDARIES (ANTI-DUPLICATION)

IN SCOPE:
- <owned world domain>

OUT OF SCOPE (HARD):
- <forbidden overlaps>

COLLISION RULE:
- If overlap exists, declare owner family/engine and how to route work.

---

## 5) RULESET (THE LAW)

Write numbered rules using MUST/FORBIDDEN/ALLOWED:
- R1 (HARD): ...
- R2 (HARD): ...
- R3 (SOFT): ...

Include:
- strict sets (allowed values)
- invariants
- stop conditions (blockers)

---

## 6) REQUIRED OUTPUT SCHEMAS (MINIMUM)

For each produced artifact:

ARTIFACT: <NAME>
- MUST: <fields list>
- OPTIONAL: <fields list>
- VALIDATION: <how to detect missing/invalid>
- STORAGE: <target path rule>

---

## 7) PIPELINE (DETERMINISTIC)

1) Input validation
2) Construct models/rulesets
3) Output formatting
4) Integration hooks (dependencies/xrefs if used)

---

## 8) S0 BLOCKERS (STOP)

- S0-1: Output contradicts CORE invariants.
- S0-2: Engine duplicates governance authority/pipeline rules.
- S0-3: Engine claims ownership of character-domain or narrative-structure primitives.
- S0-4: Engine outputs missing required schema fields.

---

## 9) INTEGRATION (SYSTEM FIT)

- Which engines consume these outputs
- How this engine plugs into ORC pipelines (if applicable)
- When governance pipeline is required

---

## 10) REFERENCES (RAW ONLY) (OPTIONAL)

- <raw links>

--- END.

---

## 2) TEMPLATE QUALITY CHECK (FAST)

Before setting a new engine ACTIVE:
- [ ] Header schema correct
- [ ] MINI-CONTRACT concrete
- [ ] Boundaries explicit
- [ ] Output schemas defined
- [ ] S0 blockers listed
