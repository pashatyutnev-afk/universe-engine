# README TEMPLATE — EXPRESSION ENGINES (ENG FAMILY)
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/05_EXPRESSION_ENGINES/00__TEMPLATE__README__EXPRESSION_ENGINES.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
DOC_TYPE: TEMPLATE
ENTITY_CLASS: ENG
ENGINE_FAMILY: 05_EXPRESSION_ENGINES
LEVEL: L3
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.TPL.ENG.EXPR.FAMILY_README.001
OWNER: SYSTEM
ROLE: Canonical template for expression family README (scope, primitive taxonomy, boundaries, gates, engine list policy)

---

## 0) FAMILY IDENTITY (REQUIRED)
FAMILY_NAME: 05_EXPRESSION_ENGINES
FAMILY_CLASS: EXPRESSION
FAMILY_UID: UE.ENG.FAMILY.EXPR.001

---

## 1) PURPOSE (LAW)
Семейство expression движков определяет **примитивы выражения истории**:
- EVENT: что произошло (как объект)
- CAUSE_EFFECT: почему и к чему привело
- CONFLICT: столкновение сил/целей
- TURNING_POINT: изменение траектории
- CLIMAX: пик напряжения/ставок
- RESOLUTION: снятие напряжения/новое состояние
- SYSTEM_SHOCK: событие, меняющее правила игры
- EVENT_SCHEDULING: порядок/тайминг/распределение
- RANDOMNESS_CHAOS: контролируемая случайность

Это **не** сюжет и **не** персонажи — это библиотека “строительных блоков”.

---

## 2) BOUNDARIES (ANTI-DUP) — REQUIRED
OWNED HERE:
- схемы primitives + правила сборки + gates

NOT OWNED HERE:
- сюжетные арки/эпизоды/структуры (02_DOMAIN_NARRATIVE_ENGINES)
- мотивации/психология/речь (03_DOMAIN_CHARACTER_ENGINES)
- мир/эпохи/экономика/законы (04_DOMAIN_WORLD_ENGINES)

---

## 3) FAMILY GATES (MANDATORY)
Каждый движок семейства обязан иметь минимум 5 gates:
- clarity
- causality coherence
- stakes integrity
- reversibility / cost
- continuity compatibility

---

## 4) REQUIRED TEMPLATES
ENGINE TEMPLATE UID: UE.TPL.ENG.EXPR.ENGINE.001
FAMILY README TEMPLATE UID: UE.TPL.ENG.EXPR.FAMILY_README.001

---

## 5) ENGINE LIST POLICY (NUMBERING)
- Engine files: `NN__<NAME>_ENG.md` (NN starts at 01)
- NN in filename MUST match NN in registry / index.
- README is always `00__README__EXPRESSION_ENGINES.md`
- Templates are always `00__TEMPLATE__...`

---

## 6) REL / XREF (UID-FIRST)
REL:
- REL: <REL_TYPE> | TARGET: <UID> | WHY: <reason>

XREF:
- XREF: <UID> | WHY: <reason>

--- END.
