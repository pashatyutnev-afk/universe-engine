# Climax Engine
FILE: 05__CLIMAX_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 05_EXPRESSION_ENGINES
CLASS: EXPRESSION (L3)
LEVEL: L3
STATUS: ACTIVE
VERSION: 2.0
ROLE: Defines a CLIMAX as the peak collision where win/lose conditions are tested under maximum constraints; produces Climax Specs, Peak Pressure Maps, Decision Gates, and Irreversible Outcome Deltas to ensure payoff, consequence, and continuity alignment

---

## PURPOSE

CLIMAX — это момент проверки:
- достигнут ли win-condition
- выдержаны ли ограничения
- оплачена ли цена
- выполнен ли “обещанный” конфликтом payoff

Движок нужен, чтобы:
- кульминация была неизбежной (вытекала из причин/конфликта/поворотов)
- ставки были максимальны и ясны
- выбор героя имел реальную цену
- исход фиксировал необратимые изменения мира
- не было “слишком легко” или “слишком случайно”

---

## NON-GOALS

- не делает монтаж/киноязык (это Knowledge Production engines)
- не заменяет Narrative Structure (акты/битовка)
- не заменяет Resolution (последствия после пика)
Он фиксирует **пиковое столкновение + результат**.

---

## MINI-CONTRACT (MANDATORY)

### CONSUMES
- Conflict Spec (CS), Escalation Ladder (EL), Win/Lose Conditions (WLC)
- Turning Point Specs (TPS) and PNR locks
- Causal Chain (CC) and Dependency Graph (DG)
- Event Specs (ES) and State Deltas (SCD)
- World constraints (WLS/ERX), environment cycles/hazards if relevant

### PRODUCES
- CLIMAX SPEC (CLS) — canonical artifact
- PEAK PRESSURE MAP (PPM)
- DECISION GATES (DGX)
- OUTCOME DELTA (OD) — irreversible deltas
- PAYOFF CHECKLIST (PC)

### DEPENDS_ON
- 05_EXPRESSION_ENGINES/03__CONFLICT_ENG.md
- 05_EXPRESSION_ENGINES/04__TURNING_POINT_ENG.md
- 05_EXPRESSION_ENGINES/02__CAUSE_EFFECT_ENG.md

### OUTPUT_TARGET
- Feeds:
  - 05_EXPRESSION_ENGINES/06__RESOLUTION_ENG.md
  - Continuity + registers (locks and deltas)

---

## CANON TERMS

### PEAK PRESSURE
Максимальное давление ограничений:
- времени
- ресурсов
- закона/морали
- среды
- информации
- усталости/травм

### DECISION GATE
Точка выбора, где каждый вариант имеет цену, и “идеального” нет.

### PAYOFF
Выплата обещания конфликта:
- то, что было поставлено на кон, реально проверяется

### IRREVERSIBLE OUTCOME
Исход, который не может быть отменён без огромной цены.

---

## CLIMAX RULES (CANON)

### CL1 — Climax tests win/lose conditions
Кульминация обязана напрямую проверять WLC:
- победа/поражение/ничья должны быть наблюдаемыми

### CL2 — Peak constraints must be visible
Ограничения должны проявиться:
- последний патрон, конец времени, закон, погода, рана, шантаж

### CL3 — Choice must cost
У главного выбора:
- минимум 2 опции
- каждая имеет цену
Если “выбор без цены” — не кульминация.

### CL4 — Outcome must change state irreversibly
После кульминации мир другой:
- контроль, ресурсы, отношения, возможности, легитимность, среда

### CL5 — No deus ex rescue
Нельзя спасать кульминацию:
- внезапной силой, не зарегистрированной ранее
- случайностью, которая решает основной узел без цены

Allowed:
- заранее подготовленный ресурс/союз/контр
- с ценой и последствиями

---

## CLIMAX TYPES (STANDARD)

- confrontation climax (лобовое столкновение)
- sacrifice climax (победа ценой потери)
- revelation climax (правда ломает структуру)
- escape/survival climax (окно закрывается)
- moral climax (выбор идентичности/предательства)
- systemic climax (крах системы: город/режим/армия)

Rule:
- type must match conflict type and stakes.

---

## REQUIRED ARTIFACT A: CLIMAX SPEC (CLS)

### CLS SCHEMA (CANON)

Header:
- CLIMAX_ID:
- PROJECT_ID / WORLD_ID:
- SCOPE:
  - scene | episode | arc | epoch
- VERSION:
- STATUS:
  - draft | canon | deprecated

Links:
- LINKED_CONFLICT_ID:
- LINKED_WLC_ID:
- LINKED_TPS_ID(S):
- KEY_EVENTS:
  - setup events
  - immediate trigger event

Arena:
- WHERE (arena):
- TIME WINDOW:
- ENV CONDITIONS:
- VISIBILITY/INFORMATION:

Peak constraints:
- TIME PRESSURE:
- RESOURCE LIMIT:
- LAW/MORAL LIMIT:
- CAPABILITY LIMIT:
- ENV LIMIT:
- RELATIONSHIP LIMIT (trust/hostage/etc):

Climax core:
- “THE TEST” (1 sentence):
  - what is being tested
- PRIMARY ACTION:
- OPPOSITION RESPONSE:
- MAIN DECISION GATE (DGX_REF):
- RESULT:
  - A wins | B wins | draw | partial
- PROOF SIGNAL:
  - observable proof of result

Cost:
- COST PAID:
- SACRIFICE (if any):
- COLLATERAL DAMAGE:

After:
- OUTCOME DELTA (OD_REF):
- NEW LOCKS:
- OPEN THREADS:
- NEXT REQUIRED RESOLUTION BEATS:

---

## REQUIRED ARTIFACT B: PEAK PRESSURE MAP (PPM)

### PPM SCHEMA (CANON)

- PPM_ID:
- CLIMAX_ID:

Pressures (repeat):
- PRESSURE_TYPE:
  - time | resource | law | environment | capability | information | fatigue | social
- PRESSURE STATEMENT:
- HOW IT SHOWS UP:
- WHAT IT FORCES:
  - constraints on choices
- FAILURE IF IGNORED:
  - consequence

Rule:
- At least 3 pressures for a major climax.

---

## REQUIRED ARTIFACT C: DECISION GATES (DGX)

### DGX SCHEMA (CANON)

- DGX_ID:
- CLIMAX_ID:
- GATE QUESTION:
  - “do we sacrifice X to save Y?”
- OPTIONS:
  - option A:
    - cost
    - win probability shift
    - moral/legal impact
  - option B:
    - cost
    - win probability shift
    - moral/legal impact
  - option C (optional):
- WHY NO PERFECT OPTION:
- CHOSEN OPTION:
- CONSEQUENCE LOCK:
  - what becomes true afterwards

Rule:
- A climax must include at least 1 decision gate.

---

## REQUIRED ARTIFACT D: OUTCOME DELTA (OD)

### OD SCHEMA (CANON)

- OD_ID:
- CLIMAX_ID:
- PRIMARY OUTCOME:
- IRREVERSIBILITY LEVEL:
  - none | partial | high | total

State deltas:
- CONTROL DELTA:
- RESOURCE DELTA:
- RELATIONSHIP DELTA:
- CAPABILITY DELTA:
- LEGITIMACY DELTA:
- ENVIRONMENT DELTA:

Casualty & damage:
- CASUALTIES:
- DAMAGE SUMMARY:
- INJURY/TRAUMA LOCKS:

Resolution hooks:
- WHAT MUST BE ADDRESSED NEXT:
- WHAT CAN BE LEFT AS SCAR:

Rule:
- If result is “major”, OD must include at least 2 delta channels.

---

## REQUIRED ARTIFACT E: PAYOFF CHECKLIST (PC)

### PC SCHEMA (CANON)

- PC_ID:
- CLIMAX_ID:
- PROMISES MADE BY CONFLICT:
  - (stakes, threats, levers)
- WHAT GOT TESTED:
- WHAT GOT PAID:
- WHAT GOT WON/LOST:
- WHAT VIEWER/READER LEARNS:
- WHAT CHANGES FOREVER:

Rule:
- If payoff list is empty — climax is probably fake.

---

## VALIDATION GATES (HARD)

### Gate 1 — Inevitability
Climax must be the logical consequence of:
- DG prerequisites satisfied
- EL escalated to the right level
- TPS created PNR locks

### Gate 2 — Fairness
Any decisive resource used must be:
- introduced earlier or logically available
- not a brand-new deus ex

### Gate 3 — Price
The win must have a cost that persists.

### Gate 4 — Proof
Win/lose/draw must be observable.

---

## INCONSISTENCY DETECTOR (HEURISTICS)

Flag if:
- climax doesn’t test the stated WLC
- pressures are not present (“why not just wait?”)
- the hero wins with no sacrifice/cost
- new power appears without setup
- outcome doesn’t change anything afterwards
- opposition fails to respond logically

Fix options:
- align climax test directly to WLC proof signal
- add pressure (deadline, storm, ammo, law enforcement)
- enforce OD with irreversible deltas
- seed resources earlier (foreshadow, supply, alliance)
- add opponent counterplay and escalation logic
- create a decision gate where every option hurts

---

## PROCEDURE (HOW TO RUN)

1) Choose linked conflict + WLC
2) Confirm preconditions (DG) and turning points (TPS) are in place
3) Declare arena + time window + environment
4) Build PPM (peak pressures)
5) Define decision gate(s) (DGX)
6) Execute test of WLC and define observable proof
7) Write OD (irreversible deltas)
8) Fill payoff checklist and register locks/deltas
9) Handoff to Resolution engine

---

## QC CHECKLIST (MANDATORY)

- linked conflict, WLC, TPS present?
- at least 3 peak pressures for major climax?
- at least 1 decision gate?
- proof signal observable?
- OD contains irreversible deltas?
- no deus ex resources?
- payoff checklist complete?

---

## VALIDATION RULES

- CLV1: Climax directly tests win/lose conditions under peak pressure.
- CLV2: Choice is costly and eliminates perfect options.
- CLV3: Outcome is irreversible and propagates via deltas.
- CLV4: Payoff matches promises set earlier.

---

OWNER: Universe Engine
LOCK: FIXED
