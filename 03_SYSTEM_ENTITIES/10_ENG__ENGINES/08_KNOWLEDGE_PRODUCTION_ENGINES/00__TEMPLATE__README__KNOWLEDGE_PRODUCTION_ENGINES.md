# KNOWLEDGE PRODUCTION ENGINES — README TEMPLATE (ENG) — CANON
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/08_KNOWLEDGE_PRODUCTION_ENGINES/00__TEMPLATE__README__KNOWLEDGE_PRODUCTION_ENGINES.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
DOC_TYPE: TEMPLATE
FAMILY: 08_KNOWLEDGE_PRODUCTION_ENGINES
CLASS: PRODUCTION (L3)
LEVEL: L3
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.ENG.PROD.KP.TPL.README.001
OWNER: SYSTEM
ROLE: Mandatory realm README template for Knowledge Production engines. Defines scope, strict execution boundaries, canonical outputs, navigation order, integration with Domain/Style/Format families, and S0 blockers.

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Knowledge Production family README template standardized: execution-only scope, boundary law, output contracts, engine map skeleton, and S0 blockers."
- REASON: "Prevent overlaps with Style (feel) and Sound/Music (deep composition) and stop meaning edits in production engines."
- IMPACT: "Production engines become predictable, auditable, and safe to compose in ORC pipelines."
- CHANGE_ID: UE.CHG.2026-01-08.PROD.KP.TPL.README.001

---

## 0) PURPOSE (LAW)

This realm README defines the family `08_KNOWLEDGE_PRODUCTION_ENGINES`:
- what this family owns (implementation/execution artifacts)
- what this family forbids (no meaning authority, no deep music authority)
- canonical navigation order
- expected artifact types and schema discipline
- integration rules with Domain/Style/Format families and ORC orchestration

---

## 1) FAMILY DEFINITION (WHAT THIS FAMILY IS)

Knowledge Production engines implement media realization:
- visual composition
- art style implementation
- camera & cinematography execution planning
- lighting implementation planning
- image/video generation packaging (prompt packs / specs)
- editing/montage (screen-time rhythm)
- production audio layer (sync/design/clarity/placement)

This family is execution-only:
> It converts constraints into production instructions/artifacts.  
> It does not own story meaning, world law, character psyche, or deep music composition.

---

## 2) HARD BOUNDARIES (ANTI-DUPLICATION LAW)

This family MUST NOT own:

CORE:
- system identity/state/lifecycle

GOVERNANCE:
- authority/approvals/audit/memory/versioning/change pipeline

DOMAIN (meaning/content):
- narrative meaning/structure/continuity as primary
- character psychology/motivation/dialogue as primary
- world laws/resources/tech/ecology as primary
- event mechanics primitives as primary

STYLE:
- tone/mood/atmosphere/symbolism as meaning authority (Style owns constraints)

SOUND & MUSIC (DEEP):
- composition/harmony/arrangement/vocal/mix/master as primary (09 owns)

Key boundary reminders:
- Story-time rhythm → Narrative pacing/rhythm engine
- Screen-time rhythm → Editing & montage engine (this family)
- Production audio placement → Sound & Music (production layer) engine (this family)
- Deep music creation → Sound & Music family engines (09)

Allowed:
- consume constraints from other families and implement them as execution plans/specs.

---

## 3) CANON OUTPUT CONTRACT (ARTIFACT TYPES)

Primary outputs of this family are structured implementation artifacts, such as:
- CAMERA_PLAN
- SHOT_LIST
- LIGHTING_PLAN
- ART_DIRECTION_IMPLEMENTATION_SPEC
- GENERATION_PROMPT_PACK (image/video)
- EDIT_DECISION_LIST (EDL-like)
- AUDIO_PLACEMENT_PLAN (production layer)
- PRODUCTION_DELIVERABLE_SPEC

Rules:
- Every output must have a schema (fields + validation) inside the producing engine.
- “Just prose” without schema as a primary output is forbidden.

Forbidden as primary outputs:
- plot/meaning decisions
- world lawsets
- character psyche definitions
- deep music composition sheets, harmony charts, full mix session specs

---

## 4) NAVIGATION ORDER (CANON ENGINE MAP SKELETON)

Real family README must list engines in strict order exactly as in `02__INDEX_ALL_ENGINES.md`:

01 — Visual Composition Engine — 🔗 <raw link>
02 — Art Style Engine — 🔗 <raw link>
03 — Camera & Cinematography Engine — 🔗 <raw link>
04 — Lighting Engine — 🔗 <raw link>
05 — Image Generation Engine — 🔗 <raw link>
06 — Video Generation Engine — 🔗 <raw link>
07 — Editing & Montage Engine — 🔗 <raw link>
08 — Sound & Music Engine (Production Layer) — 🔗 <raw link>

Rule:
- Order change = canon change → Change Control required.

---

## 5) USAGE FLOW (DETERMINISTIC)

Recommended pipeline:
1) Consume Domain constraints (Narrative/Character/World/Expression)
2) Consume Style constraints (tone/atmosphere/palettes)
3) Consume Format constraints (budgets/segmentation/platform)
4) Select execution chain:
   - Visual composition → Art style → Camera → Lighting
   - Generation packaging (image/video)
   - Editing & montage (screen-time)
   - Production audio placement (sync/design/clarity)
5) Emit implementation artifacts with schemas
6) Hand off to assets/output assembly or next ORC steps

Hard rule:
- If an engine needs to change meaning, it must escalate; it cannot silently override.

---

## 6) DEPENDENCY RULES (STRICT)

Allowed dependencies:
- may depend on Domain/Style/Format outputs as constraints
- may depend on other production engines in this family

Forbidden dependency direction:
- production engines must not depend on deep music engines to define production scope
- production engines must not depend on governance engines to “invent” policy (they only reference)

Dependency hygiene:
- all deps declared in MINI-CONTRACT
- new deps recorded in Dependency Registry

---

## 7) QUALITY GATES (FAMILY LEVEL)

Family engines must enforce:
- Schema Gate: outputs must match schemas
- Boundary Gate: no meaning authority edits
- Constraint Compliance: apply style/format constraints or emit explicit exception record
- Handoff Gate: outputs are usable downstream (no missing required fields)

If gates fail:
- emit issue list / conflict report
- do not publish incomplete deliverables as canon.

---

## 8) S0 BLOCKERS (FAMILY STOP CONDITIONS)

S0-1: Engine outputs modify narrative meaning as primary  
S0-2: Engine declares tone/mood as meaning authority (Style breach)  
S0-3: Engine outputs deep music composition/mix specs as primary (09 breach)  
S0-4: Outputs have no schemas where required  
S0-5: Hidden dependencies not declared  
S0-6: Engine numbering mismatch vs index/filename  
S0-7: Two engines claim same execution capability as single owner without tiering

---

## 9) TEMPLATE LINKS (RAW ONLY)

ENGINE TEMPLATE (this family):
- <raw link to 00__TEMPLATE__ENGINE__KNOWLEDGE_PRODUCTION_ENGINES.md>

README TEMPLATE (this family):
- <raw link to this file>

Global ENG index:
- <raw link to 03_SYSTEM_ENTITIES/10_ENG__ENGINES/02__INDEX_ALL_ENGINES.md>

--- END.
