# ENGINE TEMPLATE — KNOWLEDGE PRODUCTION ENGINES (ENG)
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/08_KNOWLEDGE_PRODUCTION_ENGINES/00__TEMPLATE__ENGINE__KNOWLEDGE_PRODUCTION_ENGINES.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
DOC_TYPE: TEMPLATE
ENTITY_CLASS: ENG
ENGINE_FAMILY: 08_KNOWLEDGE_PRODUCTION_ENGINES
LEVEL: L3
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.TPL.ENG.PROD.ENGINE.001
OWNER: SYSTEM
ROLE: Canonical template for media production ENG engines (visual, camera, lighting, image/video generation, editing, production audio)

---

## 0) IDENTITY (REQUIRED)
ENGINE_NAME: <DISPLAY_NAME>
ENGINE_CODE: <SHORT_CODE>                       # VISUAL_COMPOSITION | ART_STYLE | CAMERA_CINEMATOGRAPHY | LIGHTING | IMAGE_GENERATION | VIDEO_GENERATION | EDITING_MONTAGE | SOUND_MUSIC_PROD
ENGINE_NUMBER: <NN>                             # must match filename NN__
ENGINE_FILE_NAME: <NN__NAME_ENG.md>
ENGINE_UID: <UE.ENG.PROD.<CODE>.NNN>

PRODUCTION_OBJECT:
- what this engine controls (1 line)
- what it guarantees downstream (1 line)

---

## 1) PURPOSE (LAW)
Зачем этот движок существует:
- какой слой производства он задаёт (визуал/камера/свет/генерация/монтаж/прод-звук)
- какие решения он фиксирует как “контракт”
- какие deliverables выдаёт (шот-листы, промпты, style frames, монтажные карты и т.д.)

---

## 2) DOMAIN BOUNDARY (ANTI-DUP) — REQUIRED
OWNED HERE:
- media production design (visual language, camera grammar, lighting, generation specs)
- editing decisions as screen-time rhythm (not story-time)
- production audio (sync/design/placement/clarity) — NOT deep music composition
- generation prompts/specs + constraints + QA gates for outputs

NOT OWNED HERE:
- narrative structure & story-time pacing (02_DOMAIN_NARRATIVE_ENGINES)
- character psychology/voice (03_DOMAIN_CHARACTER_ENGINES)
- world laws & lore (04_DOMAIN_WORLD_ENGINES)
- deep music composition/harmony/arrangement/vocal/mix-master (09_SOUND_MUSIC_ENGINES)

INTERFACES (REQUIRED):
- FORMAT INTERFACE (07_PRODUCTION_FORMAT_ENGINES): what the format demands from production
- NARRATIVE INTERFACE (02): what story provides as content inputs (scenes/beats)
- OUTPUT INTERFACE (projects/output layer): how deliverables are packaged
- QA/VAL interface: which checks are enforced and where violations go

---

## 3) INPUTS / OUTPUTS (MINI-CONTRACT) — REQUIRED
CONSUMES:
- <ARTIFACT_TYPE or UID>
- ...

PRODUCES:
- <ARTIFACT_TYPE or UID>
- ...

OUTPUT_PACK (REQUIRED):
- PACK_NAME: <name>
- PACK_OBJECT: <what is delivered>
- PACK_SCHEMA (hard):
  - field: <name> | type: <type> | required: <yes/no> | rules: <short>
  - ...
- PACK_INVARIANTS (hard):
  - <invariant 1>
  - <invariant 2>

DEPENDS_ON:
- <ENG_UID>
- ...

OUTPUT_TARGET:
- <where projects store production packs> (descriptive, no path-nav)

---

## 4) DELIVERABLE CONTRACTS (HARD) — REQUIRED
DELIVERABLE SET:
- DELIVERABLE: <name>
  PURPOSE:
  FORMAT:
  REQUIRED FIELDS:
  ACCEPTANCE RULES:

Recommended deliverables by engine code:
- VISUAL_COMPOSITION: shot composition rules, framing grid, lens language, staging notes
- ART_STYLE: style bible, palette rules (conceptual), texture/material language, references
- CAMERA_CINEMATOGRAPHY: camera grammar, movement rules, shot list plan
- LIGHTING: lighting bible, key/fill/back logic, mood mapping, time-of-day mapping
- IMAGE_GENERATION: prompt spec, negative constraints, seed policy, batch policy, upscaling policy
- VIDEO_GENERATION: shot-to-shot continuity policy, motion constraints, duration caps, interpolation rules
- EDITING_MONTAGE: edit map, pacing by screen-time, transitions grammar, montage patterns
- SOUND_MUSIC_PROD: production audio plan, sync rules, dialogue clarity rules, placement rules

---

## 5) PRODUCTION GATES (HARD) — REQUIRED
GATE LIST:
- GATE: <name>
  CHECK: <how to verify>
  FAIL SIGNAL: <what indicates failure>
  FIX STRATEGY: <how to fix>
  SEVERITY: <S0|S1|S2|S3>

MINIMUM FAMILY GATES (default set):
- coherence gate (style/camera/light consistent)
- continuity gate (shot-to-shot / scene-to-scene continuity)
- format compliance gate (respects 07 format constraints)
- technical viability gate (resolution, duration, codec/asset constraints if any)
- naturalness gate (if relevant; coordinate with QA layer)
- anti-dup gate (no deep music composition claims in production audio engine)

---

## 6) WORKFLOW (PIPELINE) — REQUIRED
PIPELINE STEPS:
1) intake inputs
2) produce draft deliverables
3) run gates
4) fix loop
5) output pack
6) handoff to next engine / output layer

---

## 7) EXAMPLES (REQUIRED)
GOOD EXAMPLE:
- <example pack fragment + why passes gates>

BAD EXAMPLE:
- <counterexample>
- fails because: <gate list>

---

## 8) FAILURE MODES & EDGE CASES
FAILURES:
- Failure:
  CAUSE:
  RECOVERY:

EDGE CASES:
- Case:
  Handling:

---

## 9) REL / XREF (UID-FIRST)
REL:
- REL: <REL_TYPE> | TARGET: <UID> | WHY: <reason>

XREF:
- XREF: <UID> | WHY: <reason>

RULE:
- No PATH navigation inside content.
- If clickable references are needed, keep them in registries/indexes as RAW.

---

## 10) CHANGE NOTES (OPTIONAL)
- DATE: YYYY-MM-DD
- TYPE: PATCH|MINOR|MAJOR
- SUMMARY:
- REASON:
- IMPACT:

--- END.
