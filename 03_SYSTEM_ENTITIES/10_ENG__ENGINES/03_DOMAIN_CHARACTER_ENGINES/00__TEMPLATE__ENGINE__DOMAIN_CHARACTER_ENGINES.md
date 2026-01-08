# DOMAIN CHARACTER ENGINES — ENGINE TEMPLATE (ENG) — CANON
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/03_DOMAIN_CHARACTER_ENGINES/00__TEMPLATE__ENGINE__DOMAIN_CHARACTER_ENGINES.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
DOC_TYPE: TEMPLATE
FAMILY: 03_DOMAIN_CHARACTER_ENGINES
CLASS: DOMAIN (L2)
LEVEL: L2
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.ENG.DOM.CHARACTER.TPL.ENGINE.001
OWNER: SYSTEM
ROLE: Mandatory template for DOMAIN CHARACTER engines. Enforces canonical header schema, mini-contract law, character-domain boundaries, output schemas, and raw-only references to prevent drift.

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Domain Character engine template standardized: governance-style header, strict mini-contract, boundaries, outputs, and S0 blockers."
- REASON: "Prevent template drift and stop overlaps with Narrative/World/Expression/Production and Governance/CORE."
- IMPACT: "All character engines become uniform, composable, and compatible with CORE + GOVERNANCE."
- CHANGE_ID: UE.CHG.2026-01-08.DOM.CHR.TPL.ENGINE.001

---

## 0) HOW TO USE (MANDATORY)

1) Copy this template to create a new engine file in this family.
2) Replace placeholders strictly (title, FILE path, UID, ROLE).
3) Fill MINI-CONTRACT with concrete artifacts (no vague words).
4) Declare boundaries to avoid overlap with:
   - CORE (identity/state/lifecycle)
   - GOVERNANCE (authority/pipeline/audit)
   - NARRATIVE (structure/continuity)
   - WORLD (laws/economy/tech/ecology)
   - EXPRESSION (event mechanics)
   - PRODUCTION (media implementation)
5) Add raw-only references where index navigation requires it.

Rule:
- Missing required sections => engine is incomplete (non-canon).

---

## 1) ENGINE FILE TEMPLATE (COPY FROM HERE)

# <ENGINE TITLE> (ENG) — CANON
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/03_DOMAIN_CHARACTER_ENGINES/NN__<ENGINE_NAME>_ENG.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
DOC_TYPE: ENGINE
FAMILY: 03_DOMAIN_CHARACTER_ENGINES
CLASS: DOMAIN (L2)
LEVEL: L2
STATUS: DRAFT
LOCK: OPEN
VERSION: 0.1.0
UID: UE.ENG.DOM.CHARACTER.<ENGINE_KEY>.001
OWNER: SYSTEM
ROLE: <one sentence: what character capability this engine defines and guarantees>

CHANGE_NOTE:
- DATE: YYYY-MM-DD
- TYPE: PATCH|MINOR|MAJOR|MIGRATION|EMERGENCY
- SUMMARY: "<what changed / what was defined>"
- REASON: "<why>"
- IMPACT: "<what this affects>"
- CHANGE_ID: UE.CHG.YYYY-MM-DD.DOM.CHR.<ENGINE_KEY>.<SEQ>

---

## 0) PURPOSE (LAW)

- Define the character capability this engine owns (strict).
- Define guarantees (bullets).
- Define non-goals (explicit).

---

## 1) NON-GOALS (HARD)

This engine does NOT:
- define system identity/state/lifecycle (CORE)
- define authority/approvals/pipeline/audit/memory (GOVERNANCE)
- define narrative macro-structure or continuity as primary (NARRATIVE owns)
- define world laws/economy/tech/ecology as primary (WORLD owns)
- define event mechanics primitives (EXPRESSION owns)
- define media implementation (acting/camera/editing/sound) as primary (PRODUCTION owns)

---

## 2) MINI-CONTRACT (MANDATORY)

CONSUMES:
- <1–7 inputs; named artifacts>
  - Example: CHARACTER_PROFILE, ARC_CONSTRAINTS, RELATIONSHIP_MAP, SCENE_BLUEPRINT

PRODUCES:
- <1–7 outputs; reusable artifacts>
  - Example: MOTIVATION_MODEL, BEHAVIOR_RULESET, DIALOGUE_STYLE_GUIDE, RELATIONSHIP_TENSIONS

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
- <owned character domain>

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
4) Integration hooks

---

## 8) S0 BLOCKERS (STOP)

- S0-1: Output contradicts CORE invariants.
- S0-2: Engine duplicates governance authority/pipeline rules.
- S0-3: Engine claims ownership of narrative continuity or world-law primitives.
- S0-4: Outputs missing required schema fields.

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
