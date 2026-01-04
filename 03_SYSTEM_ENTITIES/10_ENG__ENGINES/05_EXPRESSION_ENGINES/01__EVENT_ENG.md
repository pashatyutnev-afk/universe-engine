# Event Engine
FILE: 01__EVENT_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 05_EXPRESSION_ENGINES
CLASS: EXPRESSION (L3)
LEVEL: L3
STATUS: ACTIVE
VERSION: 2.0
ROLE: Defines an EVENT as a canonical atomic unit of expression (what happened, where/when, who acted, what changed); produces Event Specs and Event Registers enabling consistent cause-effect chains, conflict escalation, timeline anchoring, and scene construction

---

## PURPOSE

EVENT — это минимальная “единица изменения” в мире/истории/сюжете.

Движок нужен, чтобы:
- любое событие было формализовано (что произошло и что изменилось)
- события можно было связывать в цепочки причин-следствий
- события можно было якорить в таймлайне
- события можно было проверять на правила мира (WLS) и continuity
- не было “событий-дырок”, которые не меняют состояние и не имеют цены

---

## NON-GOALS

- не делает драматургию сцены (это Narrative engines)
- не решает, “круто ли” событие (это Style/Meaning engines)
- не строит войну/геополитику целиком (это World engines)
Он фиксирует **событие как факт + изменение состояния**.

---

## MINI-CONTRACT (MANDATORY)

### CONSUMES
- World Law Spec (WLS) for legality of actions
- Timeline Master (TM) for time anchoring (optional but recommended)
- Civilization/Geopolitics/Power context (optional)
- Scene intent (если событие внутри сцены)

### PRODUCES
- EVENT SPEC (ES) — canonical artifact
- EVENT REGISTER (ER) — list of events for a project/epoch
- STATE CHANGE DELTA (SCD) — what changed, in structured form
- EVENT TAGS (ET) — classification for downstream engines

### DEPENDS_ON
- 04_DOMAIN_WORLD_ENGINES/02__WORLD_LAW_ENG.md (rule-check)
- 04_DOMAIN_WORLD_ENGINES/03__TIMELINE_EPOCH_ENG.md (anchoring)
- 00_GOVERNANCE_ENGINES/05__CONSISTENCY_ENG.md (consistency checks)

### OUTPUT_TARGET
- Feeds:
  - 05_EXPRESSION_ENGINES/02__CAUSE_EFFECT_ENG.md
  - 05_EXPRESSION_ENGINES/03__CONFLICT_ENG.md
  - 05_EXPRESSION_ENGINES/04__TURNING_POINT_ENG.md
  - 02_DOMAIN_NARRATIVE_ENGINES/04__SCENE_CONSTRUCTION_ENG.md
  - 02_DOMAIN_NARRATIVE_ENGINES/09__NARRATIVE_CONTINUITY_ENG.md

---

## CANON TERMS

### EVENT
Факт изменения: “что-то произошло и стало иначе”.

### EVENT OUTCOME
Итог: что стало по-другому (state delta).

### EVENT SCOPE
Масштаб:
- personal (1 персонаж)
- local (локация)
- regional (регион)
- global (мир/эпоха)

### EVENT TYPE
Класс события:
- discovery, accident, attack, meeting, betrayal, collapse, treaty, migration, invention, death, rescue

### STATE
Набор параметров мира:
- кто жив/властвует/контролирует
- что доступно/сломано
- какие правила активны/исключения задействованы

---

## EVENT RULES (CANON)

### E1 — Event must change state
Если после “события” ничего не изменилось — это не событие, а шум.

### E2 — Event must have trigger
Событие не появляется из воздуха:
- причина, решение, случай (но случай тоже должен иметь условия)

### E3 — Rule-check mandatory for power actions
Если событие включает:
- магию/тех-чит
- перемещение/портал
- лечение/воскрешение
- массовое поражение
то обязателен rule-check по WLS/ERX.

### E4 — Every event has cost or risk (by default)
Даже “удача” должна иметь:
- риск, цену, вероятность, компромисс
Иначе мир превращается в казино автора.

### E5 — Events must be indexable
Событие должно иметь:
- ID
- теги
- участников
чтобы downstream движки могли работать.

---

## REQUIRED ARTIFACT A: EVENT SPEC (ES)

### ES SCHEMA (CANON)

Header:
- EVENT_ID:
- PROJECT_ID / WORLD_ID:
- VERSION:
- STATUS:
  - draft | canon | deprecated

Classification:
- EVENT_TYPE:
- SCOPE:
- SEVERITY:
  - low | medium | high | catastrophic
- VISIBILITY:
  - public | limited | secret | unknown
- CANON IMPORTANCE:
  - minor | major | anchor-candidate

Time/Place:
- WHEN:
  - absolute date OR anchor reference (TM)
- EPOCH (optional):
- WHERE:
  - region/layer/node (WMI/CNM reference)

Participants:
- ACTORS:
  - who acted (active)
- AFFECTED:
  - who/what was affected (passive)
- WITNESSES (optional):

Trigger & Intent:
- TRIGGER:
  - what started it (event/cause/decision/accident)
- INTENT:
  - goal of acting party (if any)

Action:
- WHAT HAPPENED (1–3 sentences):
- MECHANISM:
  - how it happened (tech/magic/force/social)

Constraints:
- WLS CHECK:
  - allowed | allowed-with-cost | forbidden | exception-used
- EXCEPTION REF (if used):
  - ERX EXC_ID
- LIMITS APPLIED:
  - what limited the action

Outcome:
- STATE CHANGE DELTA (SCD):
  - what changed (structured)
- COSTS PAID:
- CONSEQUENCES:
  - immediate and delayed
- NEW RISKS:
  - what risks are created

Continuity:
- LOCKS:
  - facts that must remain true now
- OPEN THREADS:
  - unresolved consequences
- REFERENCES:
  - linked events (parents/children)

---

## REQUIRED ARTIFACT B: STATE CHANGE DELTA (SCD)

### SCD SCHEMA (CANON)

- ENTITY CHANGES:
  - deaths, injuries, status shifts
- CONTROL CHANGES:
  - territory/link/node control changes (CM hooks)
- RESOURCE CHANGES:
  - shortages, new supplies, disrupted flows (RL/FM hooks)
- INFORMATION CHANGES:
  - secrets revealed, misinformation spread
- CAPABILITY CHANGES:
  - new tech/magic availability, counters deployed (AM hooks)
- RELATIONSHIP CHANGES:
  - alliances, betrayals, trust shifts
- ENVIRONMENT CHANGES:
  - разрушения, погода, contamination

Rule:
- If EVENT is “major”, it must include at least 2 delta categories.

---

## REQUIRED ARTIFACT C: EVENT REGISTER (ER)

### ER SCHEMA (CANON)

Header:
- ER_ID:
- PROJECT_ID / WORLD_ID:
- SCOPE:
  - scene | episode | arc | epoch | world
- VERSION:
- STATUS:

Entries (repeat):
- EVENT_ID:
- SHORT NAME:
- WHEN:
- WHERE:
- TYPE:
- IMPORTANCE:
- LINKS:
  - parent/child events

Rule:
- Register is the navigation for all events in the scope.
- If an event is canon, it must be in the register.

---

## TAG SYSTEM (ET) (STANDARD)

Core tags:
- violence
- diplomacy
- discovery
- failure
- betrayal
- rescue
- death
- resource-shock
- tech/magic-use
- secrecy
- escalation

World hooks tags:
- WLS-check-required
- timeline-anchor-candidate
- geopolitics-impact
- economy-impact
- continuity-lock

---

## INCONSISTENCY DETECTOR (HEURISTICS)

Flag if:
- no state delta (nothing changed)
- no trigger (event appears from nowhere)
- WLS forbids action but it happened without exception
- repeated “lucky” events with no cost/risk
- severity high but consequences are tiny
- visibility inconsistent (secret but everyone knows next scene)

Fix options:
- define explicit delta categories
- add trigger and prerequisites
- register exception or forbid mechanism
- add costs and delayed consequences
- align visibility and witnesses
- add continuity locks and update registers

---

## PROCEDURE (HOW TO RUN)

1) Declare event type + scope + severity
2) Anchor time/place (absolute or relative)
3) List participants and trigger
4) Describe mechanism and run WLS check
5) Write SCD (what changed) + costs/consequences
6) Add continuity locks + open threads
7) Register event in Event Register
8) Hand off to Cause-Effect engine for chaining

---

## QC CHECKLIST (MANDATORY)

- event has ID + type + scope + severity?
- time/place anchored?
- participants + trigger defined?
- WLS check done if power/tech involved?
- SCD includes real changes?
- costs/consequences present?
- continuity locks/open threads recorded?
- event registered?

---

## VALIDATION RULES

- EV1: Every event is a state change, not flavor text.
- EV2: Events are chainable (trigger + outcomes exist).
- EV3: World laws are respected or exceptions are registered.
- EV4: Registers enable navigation and continuity.

---

OWNER: Universe Engine
LOCK: FIXED
