# ENTITIES KB — ENTITY → KB SCOPE MAP (CANON)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/02__ENTITY_TO_KB_SCOPE_MAP.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB
DOC_TYPE: KB_MODULE
KB_TYPE: MAP
LEVEL: L2
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.MAP.ENTITY_TO_SCOPE.002
OWNER: SYSTEM
ROLE: Deterministic mapping from entity class (SPC/ENG/ORC/CTL/VAL/QA/XREF) to required KB scope: governance minimum, entity packs, and topic subrealms typically needed. Used to select minimal KB load set per run (no navigation authority).

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created entity→KB scope map: required vs optional KB modules by entity class to support minimal deterministic loading."
- REASON: "Without a scope map, entities over-load or under-load knowledge, causing drift and inconsistent performance."
- IMPACT: "Faster runs, less noise, better compliance with minimal-set policy."
- CHANGE_ID: UE.CHG.2026-01-14.KB.MAP.002

---

## 0) PURPOSE (KB)
Provide a deterministic scope selection map:
- entity class → what KB must be loaded first
- what topic realms are typically required
- prevent random loading and domain mixing

This is selection logic, not navigation.

---

## 1) DEFINITIONS
REQUIRED:
- must be loaded for the run (or already in memory) before execution

OPTIONAL:
- load only when the task requires it

DOMAIN TOPICS:
- live in `10_TOPICS/*` and are referenced via UID-only XREF

---

## 2) GLOBAL MINIMUM (APPLIES TO ALL ENTITY CLASSES)
GOVERNANCE_MINIMUM_SET (REQUIRED):
- KB master index (for navigation/existence)
- KB governance rules
- KB XREF rules
- KB REL types
- RUN_TRACE minimum standard (when producing outputs)

Notes:
- If governance minimum is missing → STOP.

---

## 3) ENTITY CLASS → SCOPE MAP

### 3.1 SPC (Specialists)
REQUIRED:
- Governance minimum set
- SPC connector standard (in `20_ENTITIES_KB/10_SPC/...`)
- SPC pack template core blocks (passport/skill tree/principles/method/checklists/gates/examples/rubric)

OPTIONAL (task-dependent):
- Topic realms relevant to specialty:
  - 10_NARRATIVE (for narrative specialists)
  - 20_CHARACTER (for character specialists)
  - 30_WORLD (for world specialists)
  - 40_VISUAL (for visual specialists)
  - 50_SOUND_MUSIC (for sound/music specialists)
  - 60_PRODUCTION (for production specialists)
  - 70_MARKETING (for marketing specialists)
  - 80_META (for meta-execution specialists)
  - 90_REFERENCE (glossaries)

Notes:
- SPC must load minimal topic set required for the specialization (avoid over-loading).

---

### 3.2 ENG (Engines)
REQUIRED:
- Governance minimum set
- ENG connector standard (in `20_ENTITIES_KB/20_ENG/...`)
- Engine KB template blocks:
  - method, parameters, edge cases, examples, gates
OPTIONAL:
- Domain topics needed by the engine’s domain (e.g., narrative logic engine loads narrative topics)

---

### 3.3 ORC (Orchestrators)
REQUIRED:
- Governance minimum set
- ORC connector standard (in `20_ENTITIES_KB/30_ORC/...`)
- Orchestrator KB template blocks:
  - pipeline steps, handoffs, gates placement, failover
OPTIONAL:
- Production topics (60_PRODUCTION) often required
- Domain topics as required by pipeline scope

---

### 3.4 CTL (Controllers)
REQUIRED:
- Governance minimum set
- CTL connector standard (in `20_ENTITIES_KB/40_CTL/...`)
- Controller KB template blocks:
  - policy, limits/thresholds, examples, sources, gates
OPTIONAL:
- Topic realms only as needed to interpret constraints

---

### 3.5 VAL (Validators)
REQUIRED:
- Governance minimum set
- Validator connector standard (in `20_ENTITIES_KB/50_VAL/...`)
- Validation blocks:
  - criteria, violation patterns, examples, gates
OPTIONAL:
- Reference realm (90_REFERENCE) for terminology consistency
- Domain topics for specific validation targets

---

### 3.6 QA (Quality)
REQUIRED:
- Governance minimum set
- QA connector standard (in `20_ENTITIES_KB/60_QA/...`)
- QA blocks:
  - rubrics, gates, exemplar sets, regression guards
OPTIONAL:
- Domain topics for the content under test (visual/sound/narrative/etc.)

---

### 3.7 XREF (Crossref)
REQUIRED:
- Governance minimum set
- XREF connector standard (in `20_ENTITIES_KB/90_XREF/...`)
- Mapping blocks:
  - entity→scope maps, matrix maps, relationship rules
OPTIONAL:
- none (XREF is primarily structural), except when mapping includes topic domain semantics

---

## 4) MINIMAL-SET SELECTION RULE (OPERATIONAL)
Rule:
- Load only REQUIRED items first.
- Add OPTIONAL items only when the task explicitly requires them.
- Prefer reference glossaries only when term ambiguity appears.

---

## 5) HARD FAIL CONDITIONS
FAIL IF:
- entity runs without governance minimum set
- entity loads unrelated topic realms “just in case” (noise/drift)
- this map is treated as navigation authority (adds RAW registry)
- entity claims competence without loading required pack blocks

---

## 6) RELATED (UID-ONLY)
XREF:
- UE.KB.RULES.GOV.001 | WHY: global KB governance rules
- UE.KB.RULE.ENTITIES.001 | WHY: entity pack minimum and boundaries
- UE.KB.README.TOPICS.REALM.001 | WHY: topic realms overview
- UE.KB.README.ENTITIES_REALM.001 | WHY: entities KB realm orientation
- UE.KB.STD.RUN_TRACE_MIN.067 | WHY: trace discipline

--- END.
