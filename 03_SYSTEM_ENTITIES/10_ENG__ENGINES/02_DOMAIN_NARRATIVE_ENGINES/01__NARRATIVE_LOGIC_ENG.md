# Narrative Logic Engine
FILE: 01__NARRATIVE_LOGIC_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 02_DOMAIN_NARRATIVE_ENGINES
CLASS: DOMAIN (L2)
LEVEL: L2
STATUS: ACTIVE
VERSION: 2.0
ROLE: Ensures narrative causality and state transitions; converts story intent into explicit logic constraints so scenes/events remain coherent and reproducible

---

## PURPOSE

Нарративная логика — это “скелет правдоподобия”.
Движок гарантирует:
- причинно-следственную связность
- явные состояния “до/после”
- отсутствие случайностей без мотивации
- воспроизводимость истории по спецификации

---

## NON-GOALS

- не пишет стиль/тон (это Genre/Style family)
- не раскрывает психологию персонажа (Character family)
- не строит мир (World family)
Он отвечает только за логическую связность и переходы состояния.

---

## MINI-CONTRACT (MANDATORY)

### CONSUMES
- Story intent (high-level)
- World constraints (laws/timeline) if known
- Character constraints (motivations/limits) if known
- Any existing scene/event list

### PRODUCES
- NARRATIVE LOGIC SPEC (NLS)
- CAUSAL CHAIN map (event -> consequence)
- STATE TRANSITION statements (before -> after)
- LOGIC VIOLATIONS list (if found)

### DEPENDS_ON
- 01_CORE_ENGINES/03__CORE_LIFECYCLE_ENG.md (status discipline)
- 00_GOVERNANCE_ENGINES/03__RULE_HIERARCHY_ENG.md (conflict precedence)

### OUTPUT_TARGET
- Feeds Scene Construction (04), Continuity (09)
- Provides constraints to Character/World families
- Used as “logic gate” before production specs are generated

---

## CANON CONCEPTS

### STATE
Состояние — это набор фактов, которые важны для истории.
Примеры: “герой свободен/в плену”, “ресурс есть/нет”, “отношение доверие/вражда”.

### TRANSITION
Переход состояния должен иметь причину.
Если переход без причины — это ошибка или intentional (должно быть помечено).

### CAUSAL CHAIN
Цепочка: событие -> эффект -> новое состояние.

---

## REQUIRED ARTIFACT: NARRATIVE LOGIC SPEC (NLS)

### NLS SCHEMA (CANON)

- NLS_ID:
- STORY_SCOPE:
  - scene | episode | arc | season
- GOAL:
  - what must land
- INITIAL STATE (BEFORE):
  - facts list
- FINAL STATE (AFTER):
  - facts list
- EVENTS (ORDERED):
  - E1:
    - event summary
    - cause (why it happens)
    - immediate effect
    - state change
  - E2...
- CAUSAL LINKS:
  - E1 -> E2 (why E2 follows)
  - E2 -> E3 ...
- CONSTRAINTS:
  - world laws constraints
  - character constraints
- RANDOMNESS POLICY:
  - none | controlled | intentional chaos
  - if randomness used: how it is justified
- LOGIC CHECKS:
  - list of checks performed (see checklist)
- VIOLATIONS (if any):
  - what breaks and why
- FIX STRATEGY:
  - how to repair logic (if violations exist)

---

## LOGIC RULES (CANON)

### NL1 — Every event changes state
Если событие не меняет состояние:
- либо это “texture beat” (должно быть помечено)
- либо удалить/объединить

### NL2 — No effect without cause
Любой эффект обязан иметь причину.
Если “просто так” — это:
- ошибка, или
- intentional mystery (must be tagged and paid off later)

### NL3 — Constraints are binding
Если world law запрещает — сцена не может нарушать,
пока не введено:
- разрешение (изменение закона),
- исключение (waiver), или
- объяснение (technology/magic/circumstance) как новый закон.

### NL4 — Stakes must be consistent
Если ставки заявлены высокие, последствия не могут быть “нулевые”.
Иначе: stakes inflation.

### NL5 — No teleportation of info/resources
Информация/ресурс/персонаж не “появляется” без передачи/пути.

### NL6 — Chekhov discipline
Любая сильная установка должна иметь:
- payoff, или
- intentional non-payoff (тоже помечается, но редко)

---

## PROCEDURE (HOW TO RUN)

1) Define scope (scene/episode/arc)
2) Write BEFORE/AFTER state
3) List events in order
4) For each event:
   - cause
   - effect
   - state change
5) Build causal links between events
6) Apply constraints (world/character)
7) Run logic checklist
8) Output NLS + violations (if any)

---

## LOGIC CHECKLIST (QC)

- does BEFORE explain first event trigger?
- does each event have cause and effect?
- does each event change state?
- are transitions motivated (no “magic jumps”)?
- are stakes consistent with consequences?
- are resources/info transfer accounted for?
- do constraints (world/character) hold?
- any mystery tags without payoff plan?

---

## VALIDATION RULES

- NLV1: NLS has explicit BEFORE/AFTER.
- NLV2: Event list is ordered and linked.
- NLV3: Violations are either fixed or explicitly tagged intentional with payoff plan.
- NLV4: Constraints are referenced (even if “unknown yet”, it must be stated).

---

OWNER: Universe Engine
LOCK: FIXED
