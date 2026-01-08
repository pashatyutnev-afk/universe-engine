# GENRE & STYLE ENGINES — ENGINE TEMPLATE (ENG) — CANON
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/06_GENRE_STYLE_ENGINES/00__TEMPLATE__ENGINE__GENRE_STYLE_ENGINES.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
DOC_TYPE: TEMPLATE
FAMILY: 06_GENRE_STYLE_ENGINES
CLASS: STYLE (L3)
LEVEL: L3
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.ENG.STYLE.TPL.ENGINE.001
OWNER: SYSTEM
ROLE: Mandatory template for GENRE & STYLE engines. Enforces canonical header schema, mini-contract law, style-boundary rules, output schemas, and raw-only references. Prevents overlap with Narrative/Character/World (meaning/content) and Production (implementation).

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Style engine template standardized: governance-style header, strict mini-contract, boundaries, output schemas, and S0 blockers."
- REASON: "Stop style engines from turning into narrative/world/production duplicates."
- IMPACT: "Style engines become reusable tone/atmosphere/symbolism constraints usable across formats."
- CHANGE_ID: UE.CHG.2026-01-08.STYLE.TPL.ENGINE.001

---

## 0) HOW TO USE (MANDATORY)

1) Copy this template to create a new engine file in this family.
2) Replace placeholders strictly (title, FILE path, UID, ROLE).
3) Fill MINI-CONTRACT with concrete artifacts (no vague words like “vibe” without schema).
4) Declare boundaries to avoid overlap with:
   - CORE (system identity/state/lifecycle)
   - GOVERNANCE (authority/pipeline/audit)
   - NARRATIVE/CHARACTER/WORLD (content ownership)
   - EXPRESSION (event mechanics)
   - PRODUCTION (camera/editing/sound implementation)
5) Add raw-only references where index navigation requires it.

Rule:
- Missing required sections => engine is incomplete (non-canon).

---

## 1) ENGINE FILE TEMPLATE (COPY FROM HERE)

# <ENGINE TITLE> (ENG) — CANON
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/06_GENRE_STYLE_ENGINES/NN__<ENGINE_NAME>_ENG.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
DOC_TYPE: ENGINE
FAMILY: 06_GENRE_STYLE_ENGINES
CLASS: STYLE (L3)
LEVEL: L3
STATUS: DRAFT
LOCK: OPEN
VERSION: 0.1.0
UID: UE.ENG.STYLE.<ENGINE_KEY>.001
OWNER: SYSTEM
ROLE: <one sentence: what style/tone constraint system this engine defines and guarantees>

CHANGE_NOTE:
- DATE: YYYY-MM-DD
- TYPE: PATCH|MINOR|MAJOR|MIGRATION|EMERGENCY
- SUMMARY: "<what changed / what was defined>"
- REASON: "<why>"
- IMPACT: "<what this affects>"
- CHANGE_ID: UE.CHG.YYYY-MM-DD.STYLE.<ENGINE_KEY>.<SEQ>

---

## 0) PURPOSE (LAW)

- Define the style/tone capability this engine owns (strict).
- Define guarantees (bullets).
- Define non-goals (explicit).

---

## 1) NON-GOALS (HARD)

This engine does NOT:
- define story structure/meaning as primary (NARRATIVE owns)
- define character psyche/motivation as primary (CHARACTER owns)
- define world laws/constraints as primary (WORLD owns)
- define event mechanics primitives (EXPRESSION owns)
- define camera/editing/sound implementation as primary (PRODUCTION owns)
- define governance authority/pipeline/audit (GOVERNANCE owns)
- define system identity/state/lifecycle (CORE owns)

---

## 2) MINI-CONTRACT (MANDATORY)

CONSUMES:
- <1–7 inputs; named artifacts>
  - Example: STORY_STRUCTURE, CHARACTER_CONSTRAINTS, WORLD_RULES, EVENT_MECHANICS

PRODUCES:
- <1–7 outputs; reusable style artifacts>
  - Example: TONE_PROFILE, MOOD_BOARD_SPEC, ATMOSPHERE_RULESET, SYMBOLISM_MAP, SENSORY_PALETTE

DEPENDS_ON:
- <engine paths> or []
  - (Style engines may depend on Narrative/World/Character constraints but cannot replace them)

OUTPUT_TARGET:
MANDATORY:
- <project storage targets, e.g. 05_PROJECTS/...>

OPTIONAL:
- <assistive notes; never overrides canon>

Rule:
- If MINI-CONTRACT is vague → INVALID.

---

## 3) DEFINITIONS (STRICT)

Style engines define:
- tone (emotional direction)
- mood (felt atmosphere)
- atmosphere rules (environmental/scene feeling constraints)
- symbolism/metaphor palettes (interpretation guides)
- sensory detail constraints (what to emphasize)

They do NOT define:
- plot choices, character backstory, world laws, production implementation.

---

## 4) BOUNDARIES (ANTI-DUPLICATION)

IN SCOPE:
- style constraints and evaluatable targets
- reusable profiles/palettes that can be applied across outputs

OUT OF SCOPE (HARD):
- writing the story
- defining the world’s hard rules
- defining character psychology
- editing/camera/sound execution specifics

Collision rule:
- If you need implementation (camera/editing), output a constraint that Production can implement.

---

## 5) RULESET (THE LAW)

Write numbered rules using MUST/FORBIDDEN/ALLOWED:
- R1 (HARD): ...
- R2 (HARD): ...
- R3 (SOFT): ...

Include:
- strict sets (allowed tone tags, allowed palette values, etc.)
- invariants (consistency across scenes/episodes)
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
ARTIFACT: TONE_PROFILE
- MUST: tone_tags[], intensity_scale, forbidden_tags[], reference_examples?
- VALIDATION: empty tone_tags => invalid

---

## 7) PIPELINE (DETERMINISTIC)

1) Input constraints validation
2) Construct style profile/palette
3) Validate invariants (consistency rules)
4) Emit style artifacts with schema
5) Provide integration notes for production implementation (optional)

---

## 8) S0 BLOCKERS (STOP)

- S0-1: Style engine defines plot/meaning as primary.
- S0-2: Style engine defines production implementation instead of constraints.
- S0-3: Output artifacts missing required schema fields.
- S0-4: Hidden dependencies not declared in MINI-CONTRACT.

---

## 9) INTEGRATION (SYSTEM FIT)

- Inputs come from Domain families and Expression mechanics.
- Outputs are consumed by Narrative/Production to keep a consistent feel.
- Production engines implement style constraints into camera/editing/sound/art generation.

---

## 10) REFERENCES (RAW ONLY) (OPTIONAL)

- <raw links>

--- END.

---

## 2) TEMPLATE QUALITY CHECK (FAST)

Before setting a new engine ACTIVE:
- [ ] Header schema correct
- [ ] MINI-CONTRACT concrete
- [ ] Boundaries explicit (Style vs Production separated)
- [ ] Output schemas defined
- [ ] S0 blockers listed
