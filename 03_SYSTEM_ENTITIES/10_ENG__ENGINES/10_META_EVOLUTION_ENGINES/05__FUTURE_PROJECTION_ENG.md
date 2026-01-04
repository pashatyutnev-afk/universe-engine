# Future Projection Engine
FILE: 05__FUTURE_PROJECTION_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 10_META_EVOLUTION_ENGINES
LEVEL: L3
STATUS: ACTIVE
VERSION: 1.0
ROLE: Projects future states via scenarios, forecasts, and risk maps; outputs actionable guidance and monitoring signals

---

## PURPOSE

Прогноз — это не гадание, а карта сценариев.
Движок:
- строит 3–5 сценариев будущего
- фиксирует допущения (assumptions)
- оценивает риски и возможности
- задаёт “monitoring signals” (что отслеживать)
- выдаёт рекомендации действий

---

## INPUTS

- Current state + trends (signals)
- Constraints and goals
- Known risks and dependencies
- External factors (если есть)

---

## OUTPUTS

- Scenario set (best/base/worst/black swan)
- Assumptions list
- Risk/opportunity map
- Monitoring dashboard spec (signals)
- Action guidance (what to do now)

---

## PROJECTION SPEC (CANON)

- TIME HORIZON (near/mid/far)
- KEY ASSUMPTIONS (list)
- SCENARIOS (3–5):
  - NAME
  - DESCRIPTION
  - PROBABILITY (low/med/high)
  - IMPACT (low/med/high)
  - EARLY SIGNALS (what we would see)
  - RISKS
  - OPPORTUNITIES
  - RECOMMENDED ACTIONS
- NO-REGRET MOVES (safe actions across scenarios)
- MONITORING SIGNALS (what to track weekly)

---

## PROCEDURE

1) Define horizon and key assumptions
2) Generate base scenario (most likely)
3) Generate best/worst + wildcard
4) Identify early signals for each
5) Define no-regret moves
6) Schedule monitoring and update cycle

---

## VALIDATION RULES

- FP1: Прогноз содержит допущения (они явные).
- FP2: Есть несколько сценариев, а не один.
- FP3: Есть ранние сигналы для отслеживания.
- FP4: Есть действия “прямо сейчас”, не только размышления.

---
OWNER: Universe Engine
STATUS: FIXED
