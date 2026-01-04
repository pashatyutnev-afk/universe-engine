# Conflict Engine
FILE: 03__CONFLICT_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 05_EXPRESSION_ENGINES
CLASS: EXPRESSION (L3)
LEVEL: L3
STATUS: ACTIVE
VERSION: 2.0
ROLE: Defines conflict as a structured collision of goals under constraints; produces Conflict Specs, Stake Maps, Escalation Ladders, and Win/Lose Conditions that keep tension, agency, and consequence consistent across scenes, arcs, and world systems

---

## PURPOSE

Конфликт — это не “драка”.
Конфликт — это:
- две (или больше) стороны
- несовместимые цели
- ограниченные ресурсы
- цена выбора
- риск потери контроля

Движок нужен, чтобы:
- конфликт был логичным (из причин и ограничений)
- ставки были ясны и росли
- действия имели последствия
- эскалация была ступенчатой, а не “сразу ядерка”
- была проверяемая структура: win/lose conditions

---

## NON-GOALS

- не заменяет Cause–Effect (цепочки причин)
- не заменяет Turning Point (точка переворота)
- не заменяет Character Psychology (мотивации глубже)
Он строит **конфликтную рамку**, пригодную для сцен и арок.

---

## MINI-CONTRACT (MANDATORY)

### CONSUMES
- Event Specs (ES) and causal chains (CC/DG)
- Actor goals (Character engines) / Faction goals (if any)
- Resource/control constraints (RL/FM, CM)
- World Law constraints (WLS/ERX) if powers involved
- Environment hazards (HR/SCS) if relevant

### PRODUCES
- CONFLICT SPEC (CS) — canonical artifact
- STAKE MAP (SM)
- ESCALATION LADDER (EL)
- WIN/LOSE CONDITIONS (WLC)
- PRESSURE & LEVER LIST (PLL)
- “DE-ESCALATION PATHS” notes

### DEPENDS_ON
- 05_EXPRESSION_ENGINES/02__CAUSE_EFFECT_ENG.md
- 02_DOMAIN_CHARACTER_ENGINES/02__MOTIVATION_DESIRE_ENG.md
- 04_DOMAIN_WORLD_ENGINES/07__ECONOMY_RESOURCE_ENG.md (optional hooks)
- 04_DOMAIN_WORLD_ENGINES/06__GEOPOLITICS_ENG.md (optional hooks)

### OUTPUT_TARGET
- Feeds:
  - 05_EXPRESSION_ENGINES/04__TURNING_POINT_ENG.md
  - 05_EXPRESSION_ENGINES/05__CLIMAX_ENG.md
  - Pacing/Rhythm and Scene Construction

---

## CANON TERMS

### SIDE
Сторона конфликта:
- персонаж, группа, фракция, государство, система

### GOAL
Чего сторона хочет добиться (конкретно).

### CONSTRAINT
Ограничение:
- закон, ресурс, время, мораль, среда, последствия

### STAKES
Что будет потеряно/получено:
- внешнее (жизнь, власть, ресурс)
- внутреннее (идентичность, мораль)
- реляционное (любовь, доверие)

### LEVER
Рычаг:
- точка давления на противника (ресурс, репутация, заложник, bottleneck)

### ESCALATION
Переход на более опасный уровень:
- больше риск
- больше необратимость
- больше цена

---

## CONFLICT RULES (CANON)

### C1 — Goals must be incompatible
Если цели совместимы — это переговоры, не конфликт.

### C2 — Each side must have agency
Стороны должны:
- выбирать
- ошибаться
- менять стратегию
Иначе конфликт “бутафория”.

### C3 — Constraints create tension
Если у героя “всё можно” — нет конфликта.
Ограничения обязаны быть явными.

### C4 — Stakes must be legible
Зритель/читатель должен понимать:
- что на кону
- почему нельзя просто уйти

### C5 — Escalation must be stepwise
Эскалация должна идти по лестнице:
- угрозы -> действия -> жертвы -> необратимость
Без “перепрыгивания” уровней без причины.

### C6 — Win/Lose must be definable
Конфликт должен иметь:
- условия победы
- условия поражения
- условия выхода/компромисса

---

## REQUIRED ARTIFACT A: CONFLICT SPEC (CS)

### CS SCHEMA (CANON)

Header:
- CONFLICT_ID:
- PROJECT_ID / WORLD_ID:
- SCOPE:
  - scene | episode | arc | epoch
- VERSION:
- STATUS:
  - draft | canon | deprecated

Core:
- CONFLICT TYPE:
  - physical | political | social | ideological | survival | internal | mixed
- SIDES:
  - SIDE_A:
  - SIDE_B:
  - SIDE_C (optional)
- GOALS:
  - A_GOAL:
  - B_GOAL:
- WHY INCOMPATIBLE:
- START TRIGGER EVENT_ID:
- CURRENT STAGE:
  - pre | active | escalation | crisis | resolution

Constraints:
- TIME PRESSURE:
- RESOURCE LIMITS:
- LAW/MORAL LIMITS:
- ENV LIMITS:
- CAPABILITY LIMITS (tech/magic):
- INFORMATION ASYMMETRY:
  - who knows what

Battlefield (where conflict happens):
- ARENA:
  - physical location / social space / institution / mind
- CONTROL NODES:
  - chokepoints, authorities, key people

Output expectations:
- EXPECTED COSTS:
- EXPECTED CONSEQUENCES:
- CONTINUITY LOCKS:
- OPEN THREADS:

---

## REQUIRED ARTIFACT B: STAKE MAP (SM)

### SM SCHEMA (CANON)

For each side:
- SIDE:
- WHAT THEY CAN GAIN:
- WHAT THEY CAN LOSE:
- FEAR:
- DESIRE:
- RED LINE:
  - what they will not accept
- SACRIFICE WILLINGNESS:
  - low/med/high

Global:
- SHARED STAKES:
  - collateral damage
- FALSE STAKES CHECK:
  - if removed, does conflict still matter?

Rule:
- At least one stake must be irreversible for “major” conflicts.

---

## REQUIRED ARTIFACT C: ESCALATION LADDER (EL)

### EL SCHEMA (CANON)

- EL_ID:
- CONFLICT_ID:
- LEVELS (ordered):

For each level:
- LEVEL_ID:
- THRESHOLD TRIGGER:
- ACTION TYPES:
- COST BAND:
- RISK BAND:
- REVERSIBILITY:
  - reversible | semi | irreversible
- EXIT OPTIONS:
  - negotiate, retreat, trade, surrender
- COUNTERS:
  - how the other side can respond

Rule:
- A conflict cannot jump from L1 to L5 without an explicit causal link.

---

## REQUIRED ARTIFACT D: WIN/LOSE CONDITIONS (WLC)

### WLC SCHEMA (CANON)

- WLC_ID:
- CONFLICT_ID:

WIN for A:
- CONDITIONS:
- PROOF/OBSERVABLE SIGNAL:
- COST ACCEPTANCE:

WIN for B:
- CONDITIONS:
- PROOF/OBSERVABLE SIGNAL:
- COST ACCEPTANCE:

DRAW / COMPROMISE:
- CONDITIONS:
- PRICE:
- WHO CLAIMS VICTORY (propaganda):

LOSS STATES (failure modes):
- A_LOSS:
- B_LOSS:
- COLLATERAL LOSS:

Rule:
- Conditions must be observable, not “they feel it”.

---

## REQUIRED ARTIFACT E: PRESSURE & LEVER LIST (PLL)

### PLL SCHEMA (CANON)

Entries (repeat):
- LEVER_ID:
- LEVER TYPE:
  - resource | reputation | hostage | legal | tech | territory | belief
- HOLDER:
- TARGET:
- HOW IT PRESSURES:
- COUNTERPLAY:
- COLLATERAL RISK:

Rule:
- Major conflicts require at least 2 levers in play.

---

## CONFLICT TYPES (QUICK GUIDES)

### Physical conflict
- logistics, terrain, fatigue, injuries
- visibility, noise, time

### Political conflict
- legitimacy, alliances, institutions, propaganda
- treaties, veto power, choke points

### Social conflict
- reputation, belonging, shame, status
- network pressure

### Ideological conflict
- symbols, taboos, sacred legitimacy
- conversion, heresy, schism

### Internal conflict
- two goals inside one actor
- cost of self-betrayal

---

## INCONSISTENCY DETECTOR (HEURISTICS)

Flag if:
- one side is omnipotent (no constraints/counters)
- stakes are vague (“bad will happen”)
- escalation is instant with no ladder
- characters don’t adapt after losing
- conflict resolution happens with no cost
- win condition is “they decide to stop” with no trigger

Fix options:
- add constraints (law, resource, time, environment)
- define clear irreversible stake
- build escalation ladder with thresholds
- define levers and counterplay
- define observable win/lose signals
- enforce costs in Event/Continuity deltas

---

## PROCEDURE (HOW TO RUN)

1) Define sides and incompatible goals
2) Declare constraints and arena
3) Build stake map (gain/lose/red lines)
4) Register levers (pressure points)
5) Build escalation ladder (levels + exits)
6) Define win/lose/draw conditions
7) Link to causal chain and timeline anchors
8) Lock continuity and open threads for later engines

---

## QC CHECKLIST (MANDATORY)

- incompatible goals explicitly stated?
- each side has agency + levers?
- constraints are explicit (time/resource/law/etc)?
- stakes are legible and at least one irreversible?
- escalation ladder exists (no jumps)?
- win/lose conditions observable?
- expected costs/consequences recorded?

---

## VALIDATION RULES

- CV1: Conflict is goal-collision under constraints, not noise.
- CV2: Stakes are clear and escalation is stepwise.
- CV3: Win/lose is definable and produces consequences.
- CV4: Levers/counterplay preserve agency for both sides.

---

OWNER: Universe Engine
LOCK: FIXED
