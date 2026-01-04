# Event Scheduling Engine
FILE: 08__EVENT_SCHEDULING_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 05_EXPRESSION_ENGINES
LEVEL: L3
STATUS: ACTIVE
VERSION: 1.0
ROLE: Orders events by constraints, pacing, causality, readiness, and resource/time windows

---

## PURPOSE

Упорядочивает события:
- по причинности
- по готовности условий (preconditions)
- по окнам ресурсов/сезонов/логистики
- по напряжению (если нужно)

---

## INPUTS

- Event specs + preconditions
- Cause-effect chain
- World constraints (seasons, travel time)
- Optional narrative pacing requirements

---

## OUTPUTS

- Event Timeline (ordered list)
- Calendar windows (if applicable)
- Dependency violations report
- Schedule variants (A/B)

---

## SCHEDULING HEURISTICS

- S1: Preconditions first.
- S2: Respect delays (travel, logistics, institutions).
- S3: Avoid “everything happens at once” unless shock.
- S4: Allocate recovery time after high-cost events.
- S5: If narrative mode: tension waves (build → peak → release).

---

## PROCEDURE

1) Build dependency graph (events + prerequisites)
2) Topological order (base)
3) Apply delays and windows (season, travel)
4) Insert recovery buffers
5) Output:
   - Primary schedule
   - Variant schedule (optional) with tradeoffs

---

## VALIDATION RULES

- ES1: No event starts without its preconditions satisfied.
- ES2: Delays must be explicit.
- ES3: High-cost events must have aftermath time.
- ES4: If shock event exists, schedule must include cascade period.

---
OWNER: Universe Engine
STATUS: FIXED
