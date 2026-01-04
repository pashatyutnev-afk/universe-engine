# Turning Point Engine
FILE: 04__TURNING_POINT_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 05_EXPRESSION_ENGINES
CLASS: EXPRESSION (L3)
LEVEL: L3
STATUS: ACTIVE
VERSION: 2.0
ROLE: Defines and validates Turning Points as irreversible trajectory changes in conflicts and causal chains; produces Turning Point Specs, Reversal Mechanisms, and Point-of-No-Return locks that ensure pivots are motivated, legible, and consequence-bearing

---

## PURPOSE

TURNING POINT — это не “интересный момент”.
Это **изменение траектории**:
- меняется баланс сил
- меняется цель/ставки
- меняются ограничения
- появляется необратимость (point of no return)

Движок нужен, чтобы:
- поворот был мотивирован (не “автор так захотел”)
- поворот был читаем (понятно, что изменилось)
- поворот имел цену и последствия
- повороты связывались с конфликтом и cause–effect цепями

---

## NON-GOALS

- не заменяет Twist/Reveal (нарративные приёмы)
- не заменяет Climax (пиковое столкновение)
- не заменяет Pacing (ритм)
Он фиксирует **структуру переворота**.

---

## MINI-CONTRACT (MANDATORY)

### CONSUMES
- Conflict Spec (CS), Escalation Ladder (EL), Win/Lose Conditions (WLC)
- Causal Chain (CC) and Dependency Graph (DG)
- Event Specs (ES) and State Change Deltas (SCD)
- World constraints (WLS/ERX) if powers involved

### PRODUCES
- TURNING POINT SPEC (TPS) — canonical artifact
- REVERSAL MECHANISM (RM) — what exactly flipped
- POINT-OF-NO-RETURN LOCK (PNR)
- “BEFORE/AFTER” STATE COMPARISON (BASC)

### DEPENDS_ON
- 05_EXPRESSION_ENGINES/02__CAUSE_EFFECT_ENG.md
- 05_EXPRESSION_ENGINES/03__CONFLICT_ENG.md
- 02_DOMAIN_NARRATIVE_ENGINES/08__TWIST_REVEAL_ENG.md (optional alignment)

### OUTPUT_TARGET
- Feeds:
  - 05_EXPRESSION_ENGINES/05__CLIMAX_ENG.md
  - 05_EXPRESSION_ENGINES/06__RESOLUTION_ENG.md
  - continuity locks and registers

---

## CANON TERMS

### TURNING POINT
Переход, после которого “уже нельзя вернуться как было”.

### REVERSAL
Смена доминирования/инициативы.

### POINT OF NO RETURN (PNR)
Новый факт/действие, делающий возврат невозможным или слишком дорогим.

### PIVOT DRIVER
Источник переворота:
- information, leverage, resource, betrayal, loss, environment, capability, legitimacy

---

## TURNING POINT RULES (CANON)

### TP1 — Must change conflict geometry
После поворота должно быть ясно:
- кто теперь сильнее/слабее
- что теперь возможно/невозможно
- какие win/lose conditions стали ближе/дальше

### TP2 — Must have explicit driver + mechanism
Поворот обязан иметь:
- TRIGGER EVENT (что запустило)
- RM (как именно меняет баланс)

### TP3 — Must have cost
Цена поворота обязательна:
- жертва, риск, раскрытие, компромисс, потеря контроля

### TP4 — Must introduce a new lock
Поворот создаёт новый “замок” в мире:
- новая вражда, новый долг, новый дефицит, новый запрет, новая травма

### TP5 — No fake turns
Если быстро “откатили” и стало как было — это beat, не turning point.

---

## TURNING POINT TYPES (STANDARD)

- INFORMATION TURN (reveal / discovery)
- LEVER TURN (lost/gained leverage)
- RESOURCE TURN (supply shock / scarcity)
- BETRAYAL TURN (ally becomes enemy)
- CAPABILITY TURN (new tech/magic or counter)
- LEGITIMACY TURN (public opinion, sacred legitimacy, scandal)
- ENVIRONMENT TURN (hazard, season shift, catastrophe)
- INTERNAL TURN (actor chooses cost/identity shift)
- TIME TURN (deadline, window closes, irreversible schedule)

Rule:
- Major turns should map to at least one Conflict Ladder threshold.

---

## REQUIRED ARTIFACT A: TURNING POINT SPEC (TPS)

### TPS SCHEMA (CANON)

Header:
- TP_ID:
- PROJECT_ID / WORLD_ID:
- SCOPE:
  - scene | episode | arc | epoch
- VERSION:
- STATUS:
  - draft | canon | deprecated

Context:
- LINKED CONFLICT_ID:
- LINKED EVENTS:
  - TRIGGER_EVENT_ID
  - SUPPORT_EVENTS (optional)
- TURN TYPE:
- CURRENT CONFLICT STAGE:
  - pre | active | escalation | crisis

Before state (B):
- B_POWER BALANCE:
- B_LEVERS:
- B_RESOURCE STATE:
- B_INFORMATION STATE:
- B_RELATIONSHIP STATE:
- B_CONSTRAINTS:

After state (A):
- A_POWER BALANCE:
- A_LEVERS:
- A_RESOURCE STATE:
- A_INFORMATION STATE:
- A_RELATIONSHIP STATE:
- A_CONSTRAINTS:

Core:
- DRIVER:
- REVERSAL MECHANISM (RM_REF):
- PNR LOCK (PNR_REF):
- COST PAID:
- NEW RISKS:
- NEW OPPORTUNITIES:
- EFFECT ON WLC:
  - which win/lose conditions moved

Continuity:
- LOCKS CREATED:
- OPEN THREADS:
- REFERENCES:
  - CC links / DG nodes

---

## REQUIRED ARTIFACT B: REVERSAL MECHANISM (RM)

### RM SCHEMA (CANON)

- RM_ID:
- TP_ID:
- MECHANISM CLASS:
  - info | leverage | resource | capability | legitimacy | environment | internal
- WHAT FLIPPED (1 sentence):
- HOW IT FLIPPED (steps):
  1) ...
  2) ...
- PREREQUISITES:
- COUNTERPLAY OPTIONS:
  - how the other side can respond
- WHY IT’S PLAUSIBLE:
  - tie to world constraints/resources/timeline
- FAILURE MODE (if attempted):
  - what if it fails

Rule:
- RM must not violate WLS or capability availability.

---

## REQUIRED ARTIFACT C: POINT-OF-NO-RETURN LOCK (PNR)

### PNR SCHEMA (CANON)

- PNR_ID:
- TP_ID:
- LOCK TYPE:
  - irreversible_action | public_exposure | destroyed_bridge | oath | death | treaty | contamination | exile | ownership_transfer
- LOCK STATEMENT:
  - the new fact that cannot be undone
- REVERSIBILITY:
  - none | partial | expensive
- WHAT WOULD BE REQUIRED TO UNDO (if partial/expensive):
- COLLATERAL COST IF UNDONE:
- CONTINUITY REQUIREMENT:
  - what must remain true going forward

Rule:
- If TP is “major”, PNR must be “none” or “expensive”.

---

## REQUIRED ARTIFACT D: BEFORE/AFTER STATE COMPARISON (BASC)

### BASC SCHEMA (CANON)

- BASC_ID:
- TP_ID:
- PRIMARY CHANGE:
- SECONDARY CHANGES:
  - resources / control / relations / capability / legitimacy / environment
- WHAT BECAME IMPOSSIBLE:
- WHAT BECAME POSSIBLE:
- NEW DEADLINES / WINDOWS:
- NEXT IMPLIED EVENTS:
  - what events must logically follow

---

## TURNING POINT VALIDATION (GATES)

### Gate 1 — Legibility
- Can a reader state in one sentence what changed?

### Gate 2 — Motivation
- Is there a clear trigger + mechanism?

### Gate 3 — Cost
- Is there a price or risk that persists?

### Gate 4 — Lock
- Is there a PNR lock that shapes the next acts?

### Gate 5 — Continuity
- Are the new locks and deltas registered in continuity/event register?

---

## INCONSISTENCY DETECTOR (HEURISTICS)

Flag if:
- “sudden reversal” with no trigger or prerequisites
- a new capability appears without availability rules
- power balance flips but stakes/levers didn’t change
- PNR is missing (“we can just undo it”)
- cost is zero and everyone is fine
- other side doesn’t respond (no counterplay)

Fix options:
- add prerequisite events (info gathering, resource loss)
- register capability or counter in Tech/Magic
- define PNR lock (exposure, death, treaty, contamination)
- add persistent consequence (injury, distrust, scarcity)
- update conflict ladder and WLC shifts
- add counterplay actions for opposing side

---

## PROCEDURE (HOW TO RUN)

1) Select conflict + current stage
2) Identify threshold that is about to be crossed (EL)
3) Choose TP type and define trigger event
4) Write RM (mechanism) with prerequisites and plausibility
5) Write PNR lock (irreversible fact)
6) Write BASC (before/after comparison)
7) Update WLC shifts (who is closer to win)
8) Register deltas in Event/Continuity, then handoff to Climax/Resolution

---

## QC CHECKLIST (MANDATORY)

- TP has conflict link + trigger event?
- RM exists and respects WLS/capability availability?
- PNR exists and is none/expensive for major turns?
- BASC shows what became possible/impossible?
- cost and new risks are persistent?
- counterplay options exist for opposition?
- WLC shift is explicitly stated?

---

## VALIDATION RULES

- TPV1: A turning point changes conflict geometry and future options.
- TPV2: It is motivated by trigger + mechanism, not author fiat.
- TPV3: It introduces a PNR lock and persistent cost/risk.
- TPV4: Before/after state is legible and registered for continuity.

---

OWNER: Universe Engine
LOCK: FIXED
