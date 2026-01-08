# KNOWLEDGE PRODUCTION ENGINE (ENG) — TEMPLATE — CANON
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/08_KNOWLEDGE_PRODUCTION_ENGINES/00__TEMPLATE__ENGINE__KNOWLEDGE_PRODUCTION_ENGINES.md

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
UID: UE.ENG.PROD.KP.TPL.ENGINE.001
OWNER: SYSTEM
ROLE: Canonical template for any engine in Knowledge Production family. Defines strict boundaries (implementation vs meaning), mandatory mini-contract, output specs, quality gates, and integration rules.

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Knowledge Production engine template standardized: execution-only ownership, artifact schemas, quality gates, safety blockers, and cross-family boundaries."
- REASON: "Stop mixing content meaning with production implementation; prevent overlap with Style and Deep Music families."
- IMPACT: "All production engines become auditable, comparable, and pipeline-compatible."
- CHANGE_ID: UE.CHG.2026-01-08.PROD.KP.TPL.ENGINE.001

---

## 0) ENGINE IDENTITY (FILL REQUIRED)

ENGINE_NAME: <NN__ENGINE_NAME_ENG.md>
ENGINE_NUMBER: <NN>
ENGINE_TITLE: <Human-readable title>
ENGINE_FAMILY: 08_KNOWLEDGE_PRODUCTION_ENGINES
ENGINE_CLASS: PRODUCTION (L3)

CANONICAL_PATH:
- 03_SYSTEM_ENTITIES/10_ENG__ENGINES/08_KNOWLEDGE_PRODUCTION_ENGINES/<NN__ENGINE_NAME_ENG.md>

ENGINE_UID:
- <UE.ENG.PROD.KP.<ENGINE_KEY>.NNN>

OWNER:
- SYSTEM

STATUS:
- DRAFT | ACTIVE | DEPRECATED | ARCHIVED

LOCK:
- OPEN | FIXED

ROLE (one line):
- <What this engine does in the system in one sentence>

---

## 1) PURPOSE (LAW)

This engine exists to implement (execute) production decisions in its domain:
- visual composition / art style / camera / lighting
- image/video generation
- editing/montage
- production audio layer (sync/design/clarity/placement — NOT deep composition)

Golden rule:
- Knowledge Production engines produce **implementation artifacts** (how to make the media), not meaning.

---

## 2) HARD BOUNDARIES (ANTI-DUPLICATION)

This engine MUST NOT:
- decide narrative meaning as primary (belongs to Domain Narrative engines)
- rewrite character psychology/dialogue as primary (Character engines)
- invent world law/economy/tech as primary (World engines)
- own tone/mood/atmosphere/symbolism as primary (Style engines)
- own deep music composition/harmony/arrangement/mix as primary (Sound & Music family)

Allowed:
- consume constraints from those families and convert them into execution plans.

Critical boundary reminders:
- Story-time rhythm = `02_DOMAIN_NARRATIVE_ENGINES/05__PACING_RHYTHM_ENG`
- Screen-time rhythm (cut/tempo) = `08_KNOWLEDGE_PRODUCTION_ENGINES/07__EDITING_MONTAGE_ENG`
- Production audio (sync/design/placement) = `08_KNOWLEDGE_PRODUCTION_ENGINES/08__SOUND_MUSIC_ENG`
- Deep music (composition/harmony/mix) = `09_SOUND_MUSIC_ENGINES/*`

---

## 3) MINI-CONTRACT (MANDATORY)

CONSUMES:
- <1–5 input artifact types + optional constraints>
- Example: SCENE_PACK, STYLE_GUIDE, CAMERA_RULES, AUDIO_CONSTRAINTS

PRODUCES:
- <1–5 output artifact types (implementation artifacts)>

DEPENDS_ON:
- <List engines required as prerequisites, or []>
- Use canonical references: 08_KNOWLEDGE_PRODUCTION_ENGINES/NN__...

OUTPUT_TARGET:
- <Where project outputs go>
- Example:
  - 05_PROJECTS/<project>/05_PROJECT__L3/ART.md
  - 06_ASSETS/<project>/... (if applicable)
  - 05_PROJECTS/<project>/06_OUTPUT/<format>.md

---

## 4) INPUT SPEC (WHAT IT ACCEPTS)

### 4.1 Required Inputs
- INPUT_A: <type> — minimum fields:
  - <field list>

### 4.2 Optional Inputs
- INPUT_B?: <type> — used when:
  - <conditions>

### 4.3 Constraints it MUST respect
- Narrative constraints:
  - <list>
- Style constraints:
  - <list>
- Format constraints:
  - <list>
- Technical constraints:
  - <list>

If a constraint conflicts:
- do NOT override silently
- escalate through governance (Change Control / Rule Hierarchy) or output a Conflict Report artifact.

---

## 5) OUTPUT SPEC (WHAT IT PRODUCES)

### 5.1 Primary Outputs (implementation artifacts)
Define exact artifact names/types this engine emits, for example:
- CAMERA_PLAN
- SHOT_LIST
- LIGHTING_PLAN
- EDIT_DECISIONS (EDL-like)
- VISUAL_STYLE_GUIDE (implementation version)
- GENERATION_PROMPT_PACK (image/video)
- AUDIO_PLACEMENT_PLAN (production layer)

For each output:
- Output Name:
- Artifact Type:
- Schema/fields (minimum):
  - <fields>
- Acceptance criteria:
  - <criteria>

### 5.2 Forbidden Outputs (S0 if primary)
- storyline meaning changes
- character arc rewrites
- deep music composition sheets
- world lawsets
- unstructured “just text” without schema for a production plan

---

## 6) PROCESS (HOW IT WORKS)

Describe deterministic steps:

Step 1 — Intake & validation
- verify required inputs exist
- verify constraints are present
- reject if ambiguous target format or missing style/format budgets

Step 2 — Translation (constraints → execution)
- convert style constraints to production parameters
- convert narrative beats to shot/edit requirements (without changing meaning)

Step 3 — Planning / generation packaging
- produce structured plans OR prompt packs OR technical sheets

Step 4 — QA checks
- run quality gates (Section 7)
- produce issue list if failing

Step 5 — Publish
- write outputs to OUTPUT_TARGET locations

---

## 7) QUALITY GATES (MANDATORY)

### GATE Q1 — Schema Gate
- All outputs conform to declared schema
- No “freeform plans” where schema is required

### GATE Q2 — Boundary Gate
- Engine does not own meaning decisions
- Any meaning change triggers S0 blocker

### GATE Q3 — Constraint Compliance Gate
- style/format constraints applied
- if not possible → explicit exception record required

### GATE Q4 — Consistency Gate
- internal naming/UID/version rules satisfied
- references are canonical and non-duplicate

### GATE Q5 — Handoff Gate
- outputs are consumable by downstream engines/ORC steps
- no missing required fields

---

## 8) FAILURE MODES (KNOWN FAILURES)

- FM1: Missing constraints → stop and request missing artifact
- FM2: Conflicting constraints → produce CONFLICT_REPORT, do not override silently
- FM3: Output not schema-valid → reject
- FM4: Engine tries to edit meaning (narrative/character/world) → S0 breach

---

## 9) S0 BLOCKERS (ABSOLUTE STOP)

S0-1: Primary output modifies story meaning / plot structure (domain ownership breach)  
S0-2: Primary output defines tone/mood as meaning authority (Style breach)  
S0-3: Engine outputs deep music composition/mix sheets as primary (Sound family breach)  
S0-4: Outputs have no schema where required  
S0-5: Hidden dependencies not listed in DEPENDS_ON  
S0-6: Engine numbering/filename mismatch vs index  
S0-7: Two engines compete as “single owner” for same execution capability without tiering

---

## 10) INTEGRATION (SYSTEM FIT)

Upstream (typical):
- Domain Narrative engines (beats/scene intent)
- Style engines (tone/atmosphere constraints)
- Production Format engines (budgets/segment limits)

Downstream (typical):
- Assets layer or Output layer assembly
- ORC pipelines that sequence production steps

This engine is an implementation bridge:
Meaning/constraints → production instructions/artifacts.

---

## 11) DEPENDENCY + XREF RULES

- Any dependency must be:
  - listed in DEPENDS_ON
  - registered in Dependency Registry Engine when introduced/changed

- Any cross-layer links required by standards must be raw-links (if index requires).

---

## 12) CHANGE CONTROL & VERSIONING

- If STATUS ACTIVE and/or LOCK FIXED:
  - changes must follow Change Control pipeline
  - audit + memory entries required for canon changes
- Version changes must follow repo versioning policy:
  - PATCH/MINOR/MAJOR semantics as defined by standards

---

## 13) REFERENCES (RAW ONLY)

- Family README (realm):
  - <raw link to 08_KNOWLEDGE_PRODUCTION_ENGINES/00__README__KNOWLEDGE_PRODUCTION_ENGINES.md>

- Global ENG index:
  - <raw link to 03_SYSTEM_ENTITIES/10_ENG__ENGINES/02__INDEX_ALL_ENGINES.md>

- Related boundaries:
  - <raw link to 02_DOMAIN_NARRATIVE_ENGINES/05__PACING_RHYTHM_ENG.md>
  - <raw link to 08_KNOWLEDGE_PRODUCTION_ENGINES/07__EDITING_MONTAGE_ENG.md>
  - <raw link to 08_KNOWLEDGE_PRODUCTION_ENGINES/08__SOUND_MUSIC_ENG.md>
  - <raw link to 09_SOUND_MUSIC_ENGINES/13__MIX_MASTER_ENG.md>

--- END.
