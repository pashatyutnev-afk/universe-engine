# Character Behavior Engine
FILE: 05__CHARACTER_BEHAVIOR_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 03_DOMAIN_CHARACTER_ENGINES
CLASS: DOMAIN (L2)
LEVEL: L2
STATUS: ACTIVE
VERSION: 2.0
ROLE: Converts character core/motivation/values/psychology into repeatable behavior patterns; defines decision loops, tactics, habits, and conditional action rules to ensure consistent choices across scenes under varying stakes and stress

---

## PURPOSE

Поведение — это “что он делает”, когда:
- хочет цель
- боится цены
- защищается психикой
- ограничен моралью

Движок нужен, чтобы:
- действия были предсказуемы (в хорошем смысле)
- тактики соответствовали персонажу
- под стрессом поведение деградировало логично
- диалоги и экшен исходили из одной механики

---

## NON-GOALS

- не описывает физиологию движения (это production/animation)
- не пишет реплики (Dialogue engine)
- не отвечает за эволюцию (Evolution engine)
Он переводит внутренности -> внешние паттерны действий.

---

## MINI-CONTRACT (MANDATORY)

### CONSUMES
- Character Spec (CS)
- Motivation Map (MM)
- Value Framework (VF)
- Psychology Profile (PP)
- Scene Specs (SS) (optional but recommended)

### PRODUCES
- BEHAVIOR SPEC (BS) — canonical artifact
- DECISION LOOP (algorithmic model)
- TACTICS SET + CONDITIONS
- HABITS / TELLS (micro-behaviors)
- STRESS BEHAVIOR MODIFIERS
- FAILURE MODES (how they fail)

### DEPENDS_ON
- 03_DOMAIN_CHARACTER_ENGINES/01__CHARACTER_CORE_ENG.md
- 03_DOMAIN_CHARACTER_ENGINES/02__MOTIVATION_DESIRE_ENG.md
- 03_DOMAIN_CHARACTER_ENGINES/03__MORAL_VALUE_ENG.md
- 03_DOMAIN_CHARACTER_ENGINES/04__CHARACTER_PSYCHOLOGY_ENG.md

### OUTPUT_TARGET
- Feeds:
  - 03_DOMAIN_CHARACTER_ENGINES/06__RELATIONSHIP_ENG.md
  - 03_DOMAIN_CHARACTER_ENGINES/07__DIALOGUE_ENG.md
  - 02_DOMAIN_NARRATIVE_ENGINES/04__SCENE_CONSTRUCTION_ENG.md (scene actions)
  - 02_DOMAIN_NARRATIVE_ENGINES/09__NARRATIVE_CONTINUITY_ENG.md (state tracking)

---

## CANON TERMS

### DECISION LOOP
Цикл: воспринимает -> оценивает -> выбирает тактику -> действует -> корректирует.

### TACTIC
Поведенческий метод достижения цели:
- ask, bargain, threaten, charm, lie, withdraw, attack, sabotage, confess

### TELL
Микросигнал, который выдаёт состояние (неосознанный).

### FAILURE MODE
Как персонаж “ломается” и ошибается.

---

## REQUIRED ARTIFACT: BEHAVIOR SPEC (BS)

### BS SCHEMA (CANON)

Header:
- BS_ID:
- CHARACTER_ID:
- SCOPE:
- VERSION:
- STATUS:

Behavior Identity:
- DEFAULT MODE:
  - assertive | passive | strategic | impulsive | nurturing | controlling
- SOCIAL STYLE:
  - warm | cold | formal | teasing | intimidating | distant
- CONFLICT STYLE:
  - confront | avoid | negotiate | dominate | submit

Decision Loop (mandatory):
- STEP 1: PERCEIVE
  - what they notice first
- STEP 2: INTERPRET
  - default assumption bias
- STEP 3: PRIORITIZE
  - goal stack + value priority
- STEP 4: SELECT TACTIC
  - choose from tactic set
- STEP 5: EXECUTE
  - how they do it (tone/body/risk)
- STEP 6: UPDATE
  - when they change plan (threshold)

Tactics Set (repeat):
- TACTIC_ID:
- NAME:
- WHEN USED (conditions):
  - goal type / stakes / opponent type
- WHY IT FITS THEM:
  - link to MM/VF/PP
- COST:
  - relational/moral/physical
- COUNTER (what beats them):
  - how others can counter this
- ESCALATION PATH:
  - what they do if it fails

Habits & Tells:
- HABITS (3–10):
  - repeated behaviors (routine)
- TELLS (3–10):
  - stress tells, lie tells, anger tells
- LIE MODE:
  - how they lie (if they do)

Stress Modifiers (mandatory):
- LOW STRESS MOD:
- MID STRESS MOD:
- HIGH STRESS MOD:
  - how tactics shift, what becomes default
- TRIGGER OVERRIDES:
  - which triggers bypass normal loop

Boundaries Integration:
- HARD LINES (from VF):
  - actions forbidden
- SOFT LINES:
  - actions costly
- CROSSING PRICE:
  - required cost + aftermath behavior

Failure Modes (mandatory):
- FAILURE_01:
  - what mistake they reliably make
- FAILURE_02:
- SELF-SABOTAGE PATTERN:
  - how they sabotage themselves
- REPAIR STYLE:
  - apologize | deny | overcompensate | gift | disappear | violence

Scene Behavior Hooks (optional but recommended):
For key scenes:
- SCENE_ID:
- TARGET GOAL:
- SELECTED TACTIC:
- RISK ACCEPTED:
- EXPECTED OUTCOME:
- ACTUAL OUTCOME:
- UPDATE (goal/tactic shift):

---

## BEHAVIOR RULES (CANON)

### CB1 — Behavior must be derivable
Любой ключевой акт должен выводиться из:
- goal (MM)
- values/boundaries (VF)
- triggers/defenses (PP)
Если нельзя вывести → косяк/авторская рука.

### CB2 — Tactics have counters
Тактика без уязвимости делает персонажа “имбой”.
У каждой ключевой тактики должен быть counter.

### CB3 — Stress changes the loop
Под стрессом:
- выбор тактики сужается
- цена игнорируется
- включаются защиты
Если стресс не меняет поведение → психика не работает.

### CB4 — Boundaries constrain action
Hard lines запрещают, soft lines требуют цену.
Пересечение = aftermath обязательный.

### CB5 — Failure modes repeat
Ошибки персонажа должны повторяться как паттерн,
иначе он “слишком правильный”.

---

## INCONSISTENCY DETECTOR (HEURISTICS)

Flag if:
- character uses tactic that contradicts their default mode with no bridge
- stress scenes show same behavior as calm scenes
- boundaries violated with no cost/aftermath
- tactics always succeed (no counters)
- failures random (no repeat)

Fix options:
- declare exception trigger override
- add bridge beat (learning/support)
- add moral/relational cost and aftermath
- define counters and let them lose sometimes
- lock failure pattern and show it

---

## PROCEDURE (HOW TO RUN)

1) Read CS/MM/VF/PP
2) Define behavior identity (default mode/social/conflict)
3) Build decision loop steps (perceive->update)
4) Define 5–12 tactics with conditions, cost, counters
5) Add habits & tells
6) Add stress modifiers + trigger overrides
7) Integrate boundaries + crossing price
8) Define failure modes + repair style
9) Optional: map to key scenes
10) Run QC detectors and lock

---

## QC CHECKLIST (MANDATORY)

- decision loop exists?
- tactics set has conditions + counters?
- stress modifiers defined?
- boundaries integrated?
- failure modes repeatable?
- habits/tells present?

---

## VALIDATION RULES

- BV1: BS complete with decision loop and tactics set.
- BV2: Stress modifiers change behavior realistically.
- BV3: Boundaries constrain or price behavior.
- BV4: Failures and counters exist and are used.

---

OWNER: Universe Engine
LOCK: FIXED
