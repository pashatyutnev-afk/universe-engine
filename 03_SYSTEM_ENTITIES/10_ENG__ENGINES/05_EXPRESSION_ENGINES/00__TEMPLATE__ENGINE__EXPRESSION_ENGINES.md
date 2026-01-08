# ENGINE TEMPLATE — EXPRESSION ENGINES (ENG)
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/05_EXPRESSION_ENGINES/00__TEMPLATE__ENGINE__EXPRESSION_ENGINES.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
DOC_TYPE: TEMPLATE
ENTITY_CLASS: ENG
ENGINE_FAMILY: 05_EXPRESSION_ENGINES
LEVEL: L3
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.TPL.ENG.EXPR.ENGINE.001
OWNER: SYSTEM
ROLE: Canonical template for expression ENG engines (event primitives, causality, conflict, turning points, climax, resolution, shocks, scheduling, randomness)

---

## 0) IDENTITY (REQUIRED)
ENGINE_NAME: <DISPLAY_NAME>
ENGINE_CODE: <SHORT_CODE>                          # e.g., EVENT, CAUSE_EFFECT, CONFLICT, TURNING_POINT
ENGINE_NUMBER: <NN>                                # must match filename NN__
ENGINE_FILE_NAME: <NN__NAME_ENG.md>
ENGINE_UID: <UE.ENG.EXPR.<CODE>.NNN>

PRIMITIVE_OWNERSHIP:
- Owns primitive type: <EVENT|CAUSE_EFFECT|CONFLICT|TURNING_POINT|CLIMAX|RESOLUTION|SYSTEM_SHOCK|SCHEDULING|RANDOMNESS>
- What it guarantees (1 line)

---

## 1) PURPOSE (LAW)
Этот движок описывает **примитив выражения**: правила формы, минимальные поля, валидность, сборку и проверку.

Ограничение:
- движок НЕ пишет историю и НЕ “придумывает сюжет”
- он даёт **структурированный блок**, который можно вставлять в narrative/scene/character pipelines

---

## 2) DOMAIN BOUNDARY (ANTI-DUP) — REQUIRED
OWNED HERE:
- формальные primitives (структура события, причинность, конфликт и т.д.)
- минимальные правила валидности (gates)
- выходные схемы (output schema)

NOT OWNED HERE:
- сюжетная архитектура / арки / эпизоды (02_DOMAIN_NARRATIVE_ENGINES)
- мотивации/психология/отношения (03_DOMAIN_CHARACTER_ENGINES)
- мир/законы/эпохи/цивилизации (04_DOMAIN_WORLD_ENGINES)
- производство медиа (08_KNOWLEDGE_PRODUCTION_ENGINES)

INTERFACES:
- Narrative interface: как narrative использует primitive
- Character interface: как primitive цепляется к персонажам (только ссылки/поля, без психологии)
- World interface: какие world constraints надо учитывать (как входные ограничения)

---

## 3) INPUTS / OUTPUTS (MINI-CONTRACT) — REQUIRED
CONSUMES:
- <ARTIFACT_TYPE or UID>
- ...

PRODUCES:
- <ARTIFACT_TYPE or UID>
- ...

PRIMITIVE_OUTPUT (REQUIRED):
- OUTPUT_OBJECT: <Primitive name>
- OUTPUT_SCHEMA (hard):
  - field: <name> | type: <type> | required: <yes/no> | rules: <short>
  - ...
- OUTPUT_INVARIANTS (hard):
  - <invariant 1>
  - <invariant 2>

DEPENDS_ON:
- <ENG_UID>
- ...

OUTPUT_TARGET:
- <where projects store these primitives> (descriptive, no path-nav)

---

## 4) PRIMITIVE SPEC (HARD) — REQUIRED
### 4.1 Primitive definition
- Definition (1–2 lines):
- Goal (what it achieves):
- Preconditions (what must already be true):
- Postconditions (what becomes true after):

### 4.2 Minimal fields (required)
- <field list>

### 4.3 Optional fields
- <field list>

### 4.4 Assembly rules
- How this primitive composes with others:
  - compatible with:
  - incompatible with:
  - ordering constraints:

---

## 5) VALIDATION GATES (HARD) — REQUIRED
GATE LIST:
- GATE: <name>
  CHECK: <how to verify>
  FAIL SIGNAL: <what indicates failure>
  FIX STRATEGY: <how to fix>

MINIMUM EXPRESSION GATES (default set):
- clarity (примитив читается однозначно)
- causality coherence (если причинность заявлена — она корректна)
- stakes integrity (если ставки заявлены — они измеримы/понятны)
- reversibility / cost (изменение имеет цену или след)
- continuity compatibility (не ломает continuity при вставке)

---

## 6) EXAMPLES (REQUIRED)
GOOD EXAMPLE:
- <structured example using schema fields>

BAD EXAMPLE:
- <structured counterexample>
- why fails: <gate>

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
