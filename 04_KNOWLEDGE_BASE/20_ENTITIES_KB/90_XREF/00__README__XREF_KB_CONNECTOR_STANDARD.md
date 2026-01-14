# XREF — KB CONNECTOR STANDARD (CANON)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/90_XREF/00__README__XREF_KB_CONNECTOR_STANDARD.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 90_XREF
DOC_TYPE: KB_MODULE
KB_TYPE: STANDARD
LEVEL: L3
STATUS: DRAFT
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.XREF.STD.CONNECTOR.001
OWNER: SYSTEM
ROLE: Canonical connector standard for Cross-Reference (XREF) entities: how to build and maintain mapping artifacts (entity→scope, ENG↔ORC↔SPC, validation matrices, pipeline maps) using UID-only references, deterministic update discipline, and anti-drift rules. Not navigation authority.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created XREF connector standard: mapping artifact types, UID-only linking rules, update discipline, and hard boundaries against link dumps."
- REASON: "XREF is the nervous system of the KB/entity layer; without standards, mappings drift and become unusable."
- IMPACT: "Deterministic navigation-of-meaning between entities/pipelines/criteria with audit-ready updates."
- CHANGE_ID: UE.CHG.2026-01-14.KB.XREF.STD.001

---

## 0) PURPOSE (KB)
XREF exists to:
- map relationships between entities, packs, topics, gates, and pipelines
- provide deterministic “meaning navigation” via UID-only references
- prevent drift by maintaining up-to-date mapping artifacts

XREF does not store domain craft; it stores maps and relationships.

---

## 1) SCOPE (BOUNDARY)
COVERS:
- mapping artifacts (maps, matrices, registries-of-meaning)
- UID-only linking discipline
- update discipline and anti-duplication rules

EXCLUDES:
- RAW navigation authority (master index only)
- domain craft topics (live in `10_TOPICS`)
- governance law authoring (lives in `00_KB_GOVERNANCE`)

---

## 2) ABSOLUTE RULES (XREF LAW)
R1 — UID-only
- Operational cross-references are UID-only.
- Never use URL/PATH inside authority blocks.

R2 — Not navigation authority
- XREF is not allowed to become a second index of RAW links.
- Existence/navigation remains controlled by KB master index only.

R3 — Deterministic semantics
- Each mapping artifact must define:
  - INPUTS
  - OUTPUTS
  - MAPPING RULES (deterministic)
  - VERSION + CHANGE_NOTE

R4 — No duplication
- Do not create multiple maps that mean the same thing.
- If a map is superseded, deprecate it and point to replacement (pointer-only).

R5 — Update discipline
- When any dependency changes (entity, pack, topic, gate), impacted maps must be reviewed.

---

## 3) REQUIRED LOAD SET (MINIMAL)
XREF runs require:
- governance minimum set
- the specific map(s) being used/updated
- dependency UIDs referenced by that map

Do not load unrelated domains.

---

## 4) XREF ARTIFACT TYPES (CANON)
### T1 — ENTITY → KB SCOPE MAP
- Maps entity class or entity UID to required KB scope load set.

### T2 — ENG ↔ ORC ↔ SPC MAP
- Maps which engines support which orchestrators and which SPC specialists are needed.

### T3 — VALIDATION MATRIX
- Maps output types to validators/QA gates/checklists/rubrics.

### T4 — PIPELINE MAP
- Maps pipelines to steps, handoffs, gates placement.

### T5 — SKILL TAG ↔ TOPIC MAP
- Maps skill tags to topics and reference modules (future-ready).

### T6 — DEPENDENCY IMPACT MAP
- Maps “if X changes, what must be reviewed”.

---

## 5) MAPPING ARTIFACT MINIMUM STRUCTURE
Every mapping file must include:
- PURPOSE
- INPUTS / OUTPUTS
- MAPPING RULES
- HARD FAIL CONDITIONS
- RELATED_UIDS (UID-only)
- CHANGE_NOTE + VERSION

---

## 6) UPDATE WORKFLOW (DETERMINISTIC)
When updating a map:
1) Identify trigger:
   - new entity / new pack / renamed UID / new gate
2) Collect dependencies (UID list)
3) Update mapping rules
4) Run consistency checks:
   - no broken UIDs
   - no duplicates
   - no orphan mappings
5) Record change note and bump version if meaningful

---

## 7) QA FOR MAPS (FAST CHECKLIST)
MAP_QA_FAST:
- [ ] INPUTS and OUTPUTS defined
- [ ] mapping rules deterministic (no “usually/likely”)
- [ ] UIDs valid and consistent
- [ ] no duplicate map meaning exists elsewhere
- [ ] hard fail conditions listed
- [ ] change note updated

Result:
- PASS if all items OK
- REWORK if deterministic rules exist but minor cleanup needed
- FAIL if UID discipline broken or map meaning is ambiguous

---

## 8) HARD FAIL CONDITIONS
FAIL IF:
- a map contains URL/PATH as authority references
- a map becomes a RAW registry / second navigation index
- mapping rules are ambiguous (“sometimes”)
- map changes are made without change note/version discipline
- duplicate map meaning is created instead of superseding/deprecating

---

## 9) RELATED (UID-ONLY)
XREF:
- UE.KB.RULES.GOV.001 | WHY: governance rules for KB usage
- UE.KB.RULE.ENTITIES.001 | WHY: entity pack boundaries and minimums
- UE.KB.MAP.ENTITY_TO_SCOPE.002 | WHY: entity class scope map (existing)
- UE.KB.COV.ENTITY_STATUS.003 | WHY: coverage dashboard
- UE.KB.STD.GATE_DEF.088 | WHY: criteria mapping often references gate definitions

--- END.
