# EXPRESSION ENGINES — Realm
FILE: 00__README__EXPRESSION_ENGINES.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 05_EXPRESSION_ENGINES
LEVEL: L3
STATUS: ACTIVE
VERSION: 1.0
ROLE: Realm file for Expression engines (events as executable narrative/world outputs)

---

## WHAT THIS FAMILY IS

**EXPRESSION ENGINES** — это слой, где абстрактные “системы мира/персонажей” превращаются в:
- события
- сцены
- цепочки действий
- изменения состояния

Если DOMAIN-движки отвечают “как устроено”, то EXPRESSION отвечает “как проявляется”.

---

## KEY IDEA

Событие — не “случайный факт”, а **операция над состоянием мира**:
- имеет причины
- имеет триггер
- имеет цену
- оставляет след

---

## INPUT / OUTPUT

### Inputs
- Current world/character state (from CORE_STATE + WORLD engines)
- Conflict drivers (WORLD/CONFLICT_POWER)
- Narrative needs (NARRATIVE family)
- Constraints (WORLD_LAW / continuity)

### Outputs
- Event specs (structured)
- Cause-effect chains
- Escalation ladders
- Turning points, climax specs, resolution plans
- Shock events and aftershock policies
- Event schedule (calendar / ordering)
- Controlled randomness injection

---

## FAMILY CONTENTS

01 — Event Engine  
02 — Cause–Effect Engine  
03 — Conflict Engine  
04 — Turning Point Engine  
05 — Climax Engine  
06 — Resolution Engine  
07 — System Shock Engine  
08 — Event Scheduling Engine  
09 — Randomness & Chaos Engine

---

## CANON FORMAT: EVENT SPEC

Every produced event should be describable as:

- EVENT_ID / NAME
- TYPE (political, personal, disaster, discovery, etc.)
- PRECONDITIONS (state required)
- TRIGGER (what starts it)
- ACTORS (who participates)
- ACTION (what happens)
- COST (resource/time/risk)
- CONSEQUENCES (state changes)
- TRACE (what remains in canon)
- COUNTERS (how it can be stopped/mitigated)

---

## VALIDATION (FAMILY-WIDE)

- E0: Event must change state. If nothing changes → it’s “noise”.
- E1: Cause exists (even if hidden).
- E2: Cost exists (time/risk/resource).
- E3: Consequence must be trackable by CORE_STATE / CONTINUITY.

---
OWNER: Universe Engine
STATUS: FIXED
