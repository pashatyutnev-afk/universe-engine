# ENGINE TEMPLATE — META EVOLUTION ENGINES (ENG)
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/10_META_EVOLUTION_ENGINES/00__TEMPLATE__ENGINE__META_EVOLUTION_ENGINES.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
DOC_TYPE: TEMPLATE
ENTITY_CLASS: ENG
ENGINE_FAMILY: 10_META_EVOLUTION_ENGINES
LEVEL: L4
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.TPL.ENG.META.ENGINE.001
OWNER: SYSTEM
ROLE: Canonical template for meta-evolution ENG engines (learning, pattern extraction, optimization, creative mutation, future projection)

---

## 0) IDENTITY (REQUIRED)
ENGINE_NAME: <DISPLAY_NAME>
ENGINE_CODE: <SHORT_CODE>                         # LEARNING | PATTERN_EXTRACTION | OPTIMIZATION | CREATIVE_MUTATION | FUTURE_PROJECTION
ENGINE_NUMBER: <NN>                               # must match filename NN__
ENGINE_FILE_NAME: <NN__NAME_ENG.md>
ENGINE_UID: <UE.ENG.META.<CODE>.NNN>

META_OBJECT:
- what system layer it modifies (1 line)
- what outcome it guarantees (1 line)

---

## 1) PURPOSE (LAW)
Зачем этот мета-движок существует:
- что он улучшает в системе (правила/процессы/качество/масштабирование)
- какие типовые ошибки/просадки он предотвращает
- какие изменения он считает допустимыми (boundary)

---

## 2) CRITICAL BOUNDARY (ANTI-DUP) — ABSOLUTE
OWNED HERE (META):
- learning from history / logs / outputs
- extracting reusable patterns from work
- optimizing pipelines, constraints, ordering, checklists
- proposing controlled mutations (experiments) without breaking canon
- future projection: forecasts, scenarios, capacity/risks
- improving consistency and reducing friction

NOT OWNED HERE (DOMAIN CONTENT):
- writing scenes, lore, characters, worlds, music, visuals as final deliverables
Those belong to DOMAIN / EXPRESSION / PRODUCTION families.

If it outputs “final story/music/visual” — it must be treated as an INPUT to domain engines, not a final artifact.

---

## 3) INPUTS / OUTPUTS (MINI-CONTRACT) — REQUIRED
CONSUMES:
- <log artifacts / audit records / outputs / metrics / QA reports>
- ...

PRODUCES:
- <system improvement pack / optimization plan / pattern library / experiment proposal>
- ...

META_OUTPUT (REQUIRED):
- OUTPUT_OBJECT: <Improvement Proposal | Pattern Pack | Optimization Plan | Mutation Experiment | Forecast Pack>
- OUTPUT_SCHEMA (hard):
  - field: <name> | type: <type> | required: <yes/no> | rules: <short>
  - ...
- OUTPUT_INVARIANTS (hard):
  - traceability to evidence (must reference inputs)
  - non-destructive default (safe-by-default)
  - boundary compliance (no domain deliverables)

DEPENDS_ON:
- <ENG_UID>
- ...

OUTPUT_TARGET:
- <where governance/system stores meta outputs> (descriptive, no path-nav)

---

## 4) META METHOD (REQUIRED)
METHOD:
- Evidence sources:
- Pattern extraction approach:
- Optimization objective:
- Risk model:
- Rollout strategy (safe):
  - propose → test → validate → adopt
- Backout plan:
  - how to revert if it hurts system

DEFAULT SAFE MODE:
- If uncertainty high → output must be “proposal / options”, not “forced change”.

---

## 5) META GATES (HARD) — REQUIRED
GATE LIST:
- GATE: <name>
  CHECK:
  FAIL SIGNAL:
  FIX STRATEGY:

MINIMUM META GATES (default set):
- evidence grounded (inputs exist and referenced)
- scope safety (doesn’t break canon by default)
- reversibility (has rollback/backout)
- impact clarity (what changes + why + expected result)
- boundary compliance (no domain final output)

---

## 6) EXAMPLES (REQUIRED)
GOOD EXAMPLE:
- <example improvement pack snippet + why passes gates>

BAD EXAMPLE:
- <counterexample>
- why fails: <gate list>

---

## 7) FAILURE MODES & EDGE CASES
FAILURES:
- Failure:
  CAUSE:
  RECOVERY:

EDGE CASES:
- Case:
  Handling:

---

## 8) REL / XREF (UID-FIRST)
REL:
- REL: <REL_TYPE> | TARGET: <UID> | WHY: <reason>

XREF:
- XREF: <UID> | WHY: <reason>

RULE:
- No PATH navigation inside content.
- If clickable references are needed, keep them in registries/indexes as RAW.

---

## 9) CHANGE NOTES (OPTIONAL)
- DATE: YYYY-MM-DD
- TYPE: PATCH|MINOR|MAJOR
- SUMMARY:
- REASON:
- IMPACT:

--- END.
