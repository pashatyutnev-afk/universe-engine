# Optimization Engine
FILE: 03__OPTIMIZATION_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 10_META_EVOLUTION_ENGINES
LEVEL: L3
STATUS: ACTIVE
VERSION: 1.0
ROLE: Produces prioritized optimization moves from patterns and signals, balancing impact vs cost vs risk

---

## PURPOSE

Оптимизация — это “делать лучше системно”.
Движок:
- переводит паттерны в конкретные изменения
- приоритезирует (impact/cost/risk)
- планирует внедрение и тест
- отслеживает побочные эффекты

---

## INPUTS

- Pattern library + triggers
- Current KPIs and pain points
- Constraints (time/budget)
- Dependencies (что трогает что)

---

## OUTPUTS

- Optimization backlog (ranked)
- Change specs (what exactly to modify)
- Test plan + rollback plan
- Expected delta per KPI
- Risk register

---

## OPTIMIZATION MOVE (CANON)

- MOVE ID
- TARGET KPI (what improves)
- PROBLEM STATEMENT
- PROPOSED CHANGE (exact)
- EXPECTED IMPACT (quantified if possible)
- COST (low/med/high)
- RISK (low/med/high)
- DEPENDENCIES
- TEST METHOD (A/B, review, simulation)
- ROLLBACK PLAN
- SUCCESS CRITERIA
- SIDE EFFECTS WATCHLIST

---

## PROCEDURE

1) Select top leverage patterns
2) Generate 3–10 candidate moves
3) Score moves by impact/cost/risk
4) Choose top N and write change specs
5) Define test + rollback
6) Execute and record learning

---

## VALIDATION RULES

- O1: Каждая оптимизация привязана к KPI и сигналам.
- O2: Есть план теста и отката.
- O3: Приоритет обоснован (почему это выше другого).
- O4: Учитываются побочные эффекты.

---
OWNER: Universe Engine
STATUS: FIXED
