# Cause–Effect Engine
FILE: 02__CAUSE_EFFECT_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 05_EXPRESSION_ENGINES
LEVEL: L3
STATUS: ACTIVE
VERSION: 1.0
ROLE: Builds causal chains, dependencies, and consequence propagation across systems

---

## PURPOSE

Делает причинность строгой:
- событие A вызывает B
- последствия распространяются по системам
- “невидимые причины” фиксируются как скрытые узлы

---

## INPUTS

- Event specs
- World systems map (power/resources/belief/tech/ecology)
- Timeline constraints

---

## OUTPUTS

- Causal Chain graph (nodes + edges)
- Propagation table (что куда ударит)
- Secondary consequences reminder list
- Hidden causes list (если нужно интригу)

---

## CAUSAL LINK (CANON)

For each edge A → B:
- MECHANISM (почему)
- DELAY (сразу/через время)
- MEDIATORS (кто/что проводит эффект)
- AMPLIFIERS (что усиливает)
- DAMPENERS (что гасит)
- FAILURE POINTS (как цепь может оборваться)

---

## PROCEDURE

1) Select primary event(s)
2) Identify direct effects (1 hop)
3) Expand to secondary effects (2 hops)
4) For each link, write mechanism + delay
5) Add dampeners/amplifiers
6) Produce “blowback” list:
   - неожиданные, но логичные последствия

---

## VALIDATION RULES

- CE1: Every link must have mechanism.
- CE2: Delays must be realistic (логистика/институты).
- CE3: Secondary consequences must touch at least one other system (power/resources/belief/etc.)
- CE4: Chains must allow interruption (иначе детерминизм ломает драму).

---

## INTEGRATION

- With TIMELINE_EPOCH: последствия в историю
- With SYSTEM_SHOCK: каскадные аварии
- With NARRATIVE_CONTINUITY: чтобы не забыть следы

---
OWNER: Universe Engine
STATUS: FIXED
