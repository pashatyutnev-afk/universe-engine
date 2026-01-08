# PRODUCTION FORMAT ENGINES — ENGINE TEMPLATE (ENG) — CANON
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/07_PRODUCTION_FORMAT_ENGINES/00__TEMPLATE__ENGINE__PRODUCTION_FORMAT_ENGINES.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
DOC_TYPE: TEMPLATE
FAMILY: 07_PRODUCTION_FORMAT_ENGINES
CLASS: PRODUCTION (L3)
LEVEL: L3
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.ENG.PROD.FORMAT.TPL.ENGINE.001
OWNER: SYSTEM
ROLE: Mandatory template for PRODUCTION FORMAT engines. Defines output-format constraints (book/series/short/youtube/game), enforces canonical header schema, mini-contract law, boundaries, output schemas, and raw-only references.

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Production Format engine template standardized: canonical header, strict mini-contract, format-boundaries, output schemas, and S0 blockers."
- REASON: "Stop mixing format constraints with narrative meaning, world rules, and production implementation."
- IMPACT: "Format engines become stable adapters between story/world/character and production pipelines."
- CHANGE_ID: UE.CHG.2026-01-08.PROD.FMT.TPL.ENGINE.001

---

## 0) HOW TO USE (MANDATORY)

1) Copy this template to create a new engine file in this family.
2) Replace placeholders strictly (title, FILE path, UID, ROLE).
3) Fill MINI-CONTRACT with concrete artifacts (no vague words).
4) Declare boundaries to avoid overlap with:
   - CORE (system identity/state/lifecycle)
   - GOVERNANCE (authority/pipeline/audit)
   - DOMAIN families (Narrative/Character/World/Expression) as content owners
   - Knowledge Production (camera/editing/generation implementation)
   - Deep Music (composition/mix)
5) Add raw-only references where index navigation requires it.

Rule:
- Missing required sections => engine is incomplete (non-canon).

---

## 1) ENGINE FILE TEMPLATE (COPY FROM HERE)

# <ENGINE TITLE> (ENG) — CANON
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/07_PRODUCTION_FORMAT_ENGINES/NN__<ENGINE_NAME>_ENG.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
DOC_TYPE: ENGINE
FAMILY: 07_PRODUCTION_FORMAT_ENGINES
CLASS: PRODUCTION (L3)
LEVEL: L3
STATUS: DRAFT
LOCK: OPEN
VERSION: 0.1.0
UID: UE.ENG.PROD.FORMAT.<ENGINE_KEY>.001
OWNER: SYSTEM
ROLE: <one sentence: what format constraint/adaptation this engine defines and guarantees>

CHANGE_NOTE:
- DATE: YYYY-MM-DD
- TYPE: PATCH|MINOR|MAJOR|MIGRATION|EMERGENCY
- SUMMARY: "<what changed / what was defined>"
- REASON: "<why>"
- IMPACT: "<what this affects>"
- CHANGE_ID: UE.CHG.YYYY-MM-DD.PROD.FMT.<ENGINE_KEY>.<SEQ>

---

## 0) PURPOSE (LAW)

- Define the format capability this engine owns (strict).
- Define guarantees (bullets).
- Define non-goals (explicit).

---

## 1) NON-GOALS (HARD)

This engine does NOT:
- define narrative meaning/structure as primary (NARRATIVE owns)
- define character psychology/motivation/dialogue as primary (CHARACTER owns)
- define world laws/resources/tech as primary (WORLD owns)
- define event mechanics primitives (EXPRESSION owns)
- define camera/editing/lighting/audio implementation (KNOWLEDGE PRODUCTION owns)
- define deep music composition/mix (SOUND & MUSIC owns)
- define authority/pipeline/audit/memory (GOVERNANCE owns)
- define system identity/state/lifecycle (CORE owns)

---

## 2) MINI-CONTRACT (MANDATORY)

CONSUMES:
- <1–7 inputs; named artifacts>
  - Example: STORY_STRUCTURE, CHARACTER_ARCS, WORLD_RULES, EVENT_MECHANICS, STYLE_PROFILE

PRODUCES:
- <1–7 outputs; reusable format artifacts>
  - Example: FORMAT_SPEC, EPISODE_CHAPTER_PLAN, LENGTH_BUDGETS, SCENE_TO_FORMAT_MAP, PLATFORM_CONSTRAINTS

DEPENDS_ON:
- <engine paths> or []
  - (Format engines depend on domain outputs, but do not redefine them)

OUTPUT_TARGET:
MANDATORY:
- <project storage targets, e.g. 05_PROJECTS/...>
- <release/output folders if used>

OPTIONAL:
- <assistive notes; never overrides canon>

Rule:
- If MINI-CONTRACT is vague → INVALID.

---

## 3) DEFINITIONS (STRICT)

Production Format engines define:
- format constraints (chapter/episode cadence, durations, segmentation)
- platform constraints (YouTube/shorts/game loops)
- adaptation rules (how to map story artifacts into format structure)
- budgets (time/length/scene count constraints)

They do NOT define:
- the story’s meaning
- the world’s laws
- the production execution (camera/editing/sound)

---

## 4) BOUNDARIES (ANTI-DUPLICATION)

IN SCOPE:
- mapping constraints from domain artifacts to output-format structure
- deterministic format specs and planners

OUT OF SCOPE (HARD):
- narrative authorship (plot decisions)
- production implementation details
- governance procedures

Collision rule:
- If a decision affects meaning, it must be provided as input from Narrative/Character/World.

---

## 5) RULESET (THE LAW)

Write numbered rules using MUST/FORBIDDEN/ALLOWED:
- R1 (HARD): ...
- R2 (HARD): ...
- R3 (SOFT): ...

Include:
- strict sets (allowed formats/platforms)
- invariants (length budget must balance)
- stop conditions (blockers)

---

## 6) REQUIRED OUTPUT SCHEMAS (MINIMUM)

For each produced artifact:

ARTIFACT: <NAME>
- MUST: <fields list>
- OPTIONAL: <fields list>
- VALIDATION: <how to detect missing/invalid>
- STORAGE: <target path rule>

Example:
ARTIFACT: FORMAT_SPEC
- MUST: format_type, segment_model, duration_budget, cadence_rules, platform_constraints
- VALIDATION: missing format_type => invalid

---

## 7) PIPELINE (DETERMINISTIC)

1) Validate inputs (domain + style constraints)
2) Select/derive format model
3) Allocate budgets (duration/chapters/episodes)
4) Map narrative units to format segments
5) Emit format artifacts with schemas

---

## 8) S0 BLOCKERS (STOP)

- S0-1: Format engine rewrites narrative meaning as primary.
- S0-2: Format engine produces implementation plans (camera/editing/sound) as primary.
- S0-3: Output artifacts missing required schema fields.
- S0-4: Hidden dependencies not declared in MINI-CONTRACT.

---

## 9) INTEGRATION (SYSTEM FIT)

- Inputs from domain + style families.
- Outputs consumed by Narrative (structure alignment) and Production (execution).
- ORC pipelines use Format engines to sequence work by platform requirements.

---

## 10) REFERENCES (RAW ONLY) (OPTIONAL)

- <raw links>

--- END.

---

## 2) TEMPLATE QUALITY CHECK (FAST)

Before setting a new engine ACTIVE:
- [ ] Header schema correct
- [ ] MINI-CONTRACT concrete
- [ ] Boundaries explicit (Format vs Production execution separated)
- [ ] Output schemas defined
- [ ] S0 blockers listed
