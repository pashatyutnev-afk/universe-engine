# KB — ENTITY → KB SCOPE MAP (CANON)
FILE: 04_KNOWLEDGE_BASE/40_RELATION_XREF/02__ENTITY_TO_KB_SCOPE_MAP.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: KB_MODULE
KB_TYPE: MAP
LEVEL: L2
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.MAP.ENTITY_SCOPE.002
OWNER: SYSTEM
ROLE: Deterministic map that tells any operational entity class (SPC/ENG/ORC/CTL/VAL/QA/XREF) which KB scopes are REQUIRED vs OPTIONAL for its work; prevents “random browsing” and prevents invention

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Introduced canonical ENTITY→KB scope selection map for all entity classes."
- REASON: "Entities must know what knowledge to load before acting; without a map they drift and hallucinate."
- IMPACT: "Entity execution becomes consistent: governance first, then domain scope, then optional deepening packs."
- CHANGE_ID: UE.CHG.2026-01-14.KB.MAP.002

---

## 0) PURPOSE (KB)
This MAP defines deterministic KB scope selection for entities:
- choose entity class
- load mandatory KB governance scope (always)
- load mandatory domain scope (by entity class + assignment)
- load optional deepening scopes only when needed

This is a MAP, not an index. It must not contain URLs or PATH navigation.
All navigation is performed via the KB master index (RAW-only) outside of this module.

---

## 1) ABSOLUTE RULES (NO-FANTASY)
1.1 KB GOVERNANCE FIRST (ABSOLUTE)
Every entity run MUST align with KB governance scope before doing domain work.

1.2 NO INVENTION (ABSOLUTE)
If a knowledge module wasn’t opened via the KB master index (RAW), the entity MUST NOT invent missing details.
Memory reuse is allowed only if the module was previously opened and meaning is unchanged.

1.3 NO URL / NO PATH INSIDE MAPS (ABSOLUTE)
This MAP uses only scope labels and deterministic rules.
It does not embed navigation links.

---

## 2) DEFINITIONS (STRICT)
### Entity class
Operational class of executor:
- SPC / ENG / ORC / CTL / VAL / QA / XREF

### KB scope
A named bucket of knowledge modules.
Scopes are referenced by labels (not links).

### Required vs Optional
- REQUIRED: must be loaded for correctness
- OPTIONAL: may be loaded to improve quality, only if needed

---

## 3) KB SCOPE LABELS (STANDARD)
### 3.1 Governance scope (always required)
KB_SCOPE.GOVERNANCE includes:
- KB minimum rules (how KB works)
- Relation vocabulary (what relations exist)
- XREF rules (how references are expressed; UID-only policy if used)

### 3.2 Domain scopes (Topics)
KB_SCOPE.TOPICS.NARRATIVE
KB_SCOPE.TOPICS.CHARACTER
KB_SCOPE.TOPICS.WORLD
KB_SCOPE.TOPICS.VISUAL
KB_SCOPE.TOPICS.SOUND_MUSIC
KB_SCOPE.TOPICS.PRODUCTION
KB_SCOPE.TOPICS.MARKETING
KB_SCOPE.TOPICS.META
KB_SCOPE.TOPICS.REFERENCE

### 3.3 Maps / XREF scopes
KB_SCOPE.MAPS.TASK_SCOPE
KB_SCOPE.MAPS.ENTITY_SCOPE
KB_SCOPE.MAPS.PIPELINES (if present)

---

## 4) SCOPE MATRIX — REQUIRED BY ENTITY CLASS

### 4.1 SPC (SPECIALISTS)
REQUIRED:
- KB_SCOPE.GOVERNANCE
- KB_SCOPE.MAPS.ENTITY_SCOPE (this map)
- One domain scope matching the SPC assignment:
  - Narrative SPC → KB_SCOPE.TOPICS.NARRATIVE
  - Character SPC → KB_SCOPE.TOPICS.CHARACTER
  - World SPC → KB_SCOPE.TOPICS.WORLD
  - Visual SPC → KB_SCOPE.TOPICS.VISUAL
  - Sound/Music SPC → KB_SCOPE.TOPICS.SOUND_MUSIC
  - Production SPC → KB_SCOPE.TOPICS.PRODUCTION
  - Marketing SPC → KB_SCOPE.TOPICS.MARKETING
  - Meta SPC → KB_SCOPE.TOPICS.META
OPTIONAL:
- KB_SCOPE.TOPICS.REFERENCE (definitions/toolbox)
- KB_SCOPE.TOPICS.META (if the SPC output must include governance/trace)

### 4.2 ENG (ENGINES)
REQUIRED:
- KB_SCOPE.GOVERNANCE
- Domain scope that the engine implements (match by family):
  - Narrative engines → KB_SCOPE.TOPICS.NARRATIVE
  - Character engines → KB_SCOPE.TOPICS.CHARACTER
  - World engines → KB_SCOPE.TOPICS.WORLD
  - Visual engines → KB_SCOPE.TOPICS.VISUAL
  - Sound/Music engines → KB_SCOPE.TOPICS.SOUND_MUSIC
  - Production format engines → KB_SCOPE.TOPICS.PRODUCTION
OPTIONAL:
- KB_SCOPE.TOPICS.META (if output affects system rules or needs strict trace)
- KB_SCOPE.TOPICS.REFERENCE

### 4.3 ORC (ORCHESTRATORS)
REQUIRED:
- KB_SCOPE.GOVERNANCE
- KB_SCOPE.TOPICS.PRODUCTION (workflows, handoffs, delivery, QA gates)
- Domain scope of the pipeline being orchestrated:
  - Story pipeline → KB_SCOPE.TOPICS.NARRATIVE (+ optional CHARACTER/WORLD)
  - Music pipeline → KB_SCOPE.TOPICS.SOUND_MUSIC (+ optional MARKETING)
OPTIONAL:
- KB_SCOPE.MAPS.TASK_SCOPE (if the orchestrator is mapping tasks to scopes)
- KB_SCOPE.TOPICS.MARKETING (if planning release/distribution)

### 4.4 CTL (CONTROLLERS)
REQUIRED:
- KB_SCOPE.GOVERNANCE
- KB_SCOPE.TOPICS.PRODUCTION (gates, policies, readiness checks)
OPTIONAL:
- Domain scope relevant to what is being controlled:
  - Sound/music controls → KB_SCOPE.TOPICS.SOUND_MUSIC
  - Marketing controls → KB_SCOPE.TOPICS.MARKETING
  - Visual controls → KB_SCOPE.TOPICS.VISUAL

### 4.5 VAL (VALIDATORS)
REQUIRED:
- KB_SCOPE.GOVERNANCE
- KB_SCOPE.TOPICS.PRODUCTION (PASS/REWORK/FAIL policies, rubric patterns)
- Domain scope to validate:
  - narrative → KB_SCOPE.TOPICS.NARRATIVE
  - sound/music → KB_SCOPE.TOPICS.SOUND_MUSIC
  - marketing → KB_SCOPE.TOPICS.MARKETING
OPTIONAL:
- KB_SCOPE.TOPICS.REFERENCE (definitions, checklists)

### 4.6 QA (QUALITY)
REQUIRED:
- KB_SCOPE.GOVERNANCE
- KB_SCOPE.TOPICS.PRODUCTION (QA gate logic)
- Domain scope under test (same mapping as VAL)
OPTIONAL:
- KB_SCOPE.TOPICS.META (if audit/trace is enforced)

### 4.7 XREF (CROSSREF)
REQUIRED:
- KB_SCOPE.GOVERNANCE
- KB_SCOPE.MAPS.TASK_SCOPE (if building task relations)
- KB_SCOPE.MAPS.ENTITY_SCOPE (this map)
OPTIONAL:
- Any domain scope only if mapping requires domain semantics (rare)

---

## 5) SELECTION ALGORITHM (DETERMINISTIC)
Step 1: Identify entity class (SPC/ENG/ORC/CTL/VAL/QA/XREF).  
Step 2: Load KB_SCOPE.GOVERNANCE (always).  
Step 3: Use Section 4 matrix to select REQUIRED domain scope(s).  
Step 4: Load OPTIONAL scopes only if:
- task explicitly requires it, OR
- a gate fails and needs deepening knowledge, OR
- output is governance/canon-critical.

Step 5: Produce output only after REQUIRED scopes are loaded.

---

## 6) FAIL CONDITIONS (HARD STOP)
- Entity starts domain work without KB_SCOPE.GOVERNANCE
- Entity uses knowledge not loaded (RAW not opened) and invents details
- Entity class mismatch (e.g., QA acting as Creator without loading domain scope)
- Any attempt to treat this MAP as a navigation index (URLs/PATH embedded)

---

## 7) EXAMPLES (STRICT)
Example A — SPC: Vocal Director
- Entity class: SPC
- REQUIRED:
  - KB_SCOPE.GOVERNANCE
  - KB_SCOPE.TOPICS.SOUND_MUSIC
  - KB_SCOPE.TOPICS.PRODUCTION (optional but recommended for QA gates)

Example B — ORC: Album to Track pipeline
- Entity class: ORC
- REQUIRED:
  - KB_SCOPE.GOVERNANCE
  - KB_SCOPE.TOPICS.PRODUCTION
  - KB_SCOPE.TOPICS.SOUND_MUSIC
- OPTIONAL:
  - KB_SCOPE.TOPICS.MARKETING (release window)

Example C — VAL: Repeat guard validation for track
- Entity class: VAL
- REQUIRED:
  - KB_SCOPE.GOVERNANCE
  - KB_SCOPE.TOPICS.PRODUCTION
  - KB_SCOPE.TOPICS.SOUND_MUSIC

---

## 8) RELATED (MAPS ONLY; NO NAV LINKS)
- MAP: UE.KB.MAP.TASK_SCOPE.001  (task → scope selection)
- MAP: UE.KB.MAP.ENTITY_SCOPE.002 (this module)

--- END.
