# Motivation & Desire Engine
FILE: 02__MOTIVATION_DESIRE_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 03_DOMAIN_CHARACTER_ENGINES
CLASS: DOMAIN (L2)
LEVEL: L2
STATUS: ACTIVE
VERSION: 2.0
ROLE: Converts Character Core into actionable motivation systems; defines desires, goals, drives, fears, and motivational conflicts across scope and per scene; produces Motivation Map used by behavior/dialogue/evolution engines

---

## PURPOSE

Мотивация — это “почему он действует сейчас”.
Движок нужен, чтобы:
- действия были неизбежны и логичны
- цели не прыгали без причины
- внутренний конфликт проявлялся через решения
- зритель понимал ставки героя

---

## NON-GOALS

- не задаёт моральные принципы (это Moral & Value engine)
- не задаёт психические механизмы (это Psychology engine)
- не пишет поведение по шагам (это Behavior engine)
Он делает **карту мотивов** и их динамику.

---

## MINI-CONTRACT (MANDATORY)

### CONSUMES
- Character Spec (CS) from Character Core
- Scene Specs (SS) (optional but recommended)
- Stakes & Tension Spec (STS) (optional)
- Theme Map (TM) (optional)

### PRODUCES
- MOTIVATION MAP (MM) — canonical artifact
- GOALS STACK (primary/secondary/hidden)
- DRIVE/FEAR matrix
- MOTIVATION CONFLICT table
- SCENE INTENT lines (per scene optional)

### DEPENDS_ON
- 03_DOMAIN_CHARACTER_ENGINES/01__CHARACTER_CORE_ENG.md
- 02_DOMAIN_NARRATIVE_ENGINES/04__SCENE_CONSTRUCTION_ENG.md (if per scene)

### OUTPUT_TARGET
- Feeds:
  - 03__MORAL_VALUE_ENG
  - 03__CHARACTER_PSYCHOLOGY_ENG
  - 05__CHARACTER_BEHAVIOR_ENG
  - 07__DIALOGUE_ENG
  - 10__CHARACTER_EVOLUTION_ENG

---

## CANON TERMS

### DESIRE
То, что притягивает (want). Может быть иллюзией.

### NEED
То, что необходимо внутренне (need). Часто скрыто.

### GOAL
Конкретная задача в текущем scope/сцене.

### DRIVE
Базовый двигатель:
- безопасность
- признание
- контроль
- свобода
- любовь
- смысл
- власть
- принадлежность

### FEAR
То, что тормозит и искажает выбор.

### HIDDEN GOAL
Цель, которую персонаж не признаёт или скрывает.

---

## GOALS STACK MODEL (CANON)

Для любого персонажа существует стек целей:

- PRIMARY GOAL (scope-level):
  - главная цель на арку/эпизод
- SECONDARY GOALS:
  - поддерживающие цели
- SCENE GOAL:
  - цель в конкретной сцене
- HIDDEN GOAL:
  - тайная цель (если есть)
- ANTI-GOAL:
  - чего он избегает любой ценой

Rule:
- сцена должна отражать хотя бы один элемент стека (иначе герой “не живёт”).

---

## MOTIVATION CONFLICT MODEL

Конфликт мотиваций — когда две силы требуют разных действий:
- want vs need
- safety vs love
- control vs freedom
- loyalty vs truth

Rule:
- минимум 1 активный конфликт на арку у ключевого персонажа.

---

## REQUIRED ARTIFACT: MOTIVATION MAP (MM)

### MM SCHEMA (CANON)

Header:
- MM_ID:
- CHARACTER_ID:
- SCOPE:
  - episode | arc | season | book
- VERSION:
- STATUS:
  - draft | active | locked

Core:
- PRIMARY DESIRE (want):
- PRIMARY NEED:
- PRIMARY FEAR:
- PRIMARY DRIVE:
- INTERNAL CONFLICT LINK:
  - from CS (one line)

Goals Stack:
- PRIMARY GOAL (scope):
- SECONDARY GOALS (list):
- HIDDEN GOAL (optional):
- ANTI-GOAL (avoidance):

Motivation Matrix:
- TRIGGERS:
  - what activates them
- REWARDS:
  - what they consider “win”
- COST TOLERANCE:
  - what cost they will accept
- BREAK POINT:
  - what makes them quit/break

Conflict Table:
- CONFLICT_01:
  - FORCE A:
  - FORCE B:
  - WHAT IT PUSHES THEM TO DO:
  - WHAT IT STOPS THEM FROM DOING:
  - RESOLUTION PATH (optional):
    - how it might resolve later

Scene Intent (optional but recommended for production):
For each relevant scene:
- SCENE_ID:
- SCENE GOAL:
- WHAT THEY THINK IS TRUE:
- WHAT THEY WANT FROM OTHER:
- TACTIC:
  - ask | threaten | charm | lie | escape | attack | bargain
- RISK THEY ACCEPT:
- OUTCOME:
  - win/lose/partial + how it changes next goal

---

## MOTIVATION RULES (CANON)

### M1 — Action must map to motive
Если герой сделал ключевое действие,
оно обязано маппиться на:
- goal, или
- fear, или
- drive, или
- conflict
Иначе это “рука автора”.

### M2 — Goals update through outcomes
После каждой важной сцены:
- цель либо подтверждается,
- либо меняется,
- либо усложняется.
Если ничего не меняется 3+ сцен подряд → мотивационный застой.

### M3 — Hidden goals must leak
Если есть hidden goal, он должен проявляться через:
- оговорки
- избегание
- странные решения
Но без прямого признания (до reveal).

### M4 — Fear distorts tactics
Страх не просто “есть”. Он меняет стиль действия:
- более контрольный
- более агрессивный
- более избегательный
Если fear declared, но поведение не меняется → косяк.

### M5 — Cost tolerance must be consistent
Если герой раньше не шёл на цену X,
а теперь идёт без причины → требует “bridge beat/scene”.

---

## MOTIVATION QC (DETECTORS)

Flag if:
- scene action has no motive mapping
- goals do not update across scenes
- fear declared but no behavior distortion
- hidden goal never leaks
- contradictory goals with no conflict table entry

Fix options:
- add explicit goal shift in scene outcome
- add fear-trigger beat
- add conflict escalation beat
- add leak behavior (micro-action)
- adjust cost tolerance and justify with stakes

---

## PROCEDURE (HOW TO RUN)

1) Read Character Spec (want/need/wound/conflict)
2) Declare primary desire/need/fear/drive
3) Build goals stack for scope
4) Add conflict table (at least one)
5) If using scenes:
   - fill scene intent per scene
   - update outcome -> next goal
6) Run QC detectors
7) Output MM

---

## VALIDATION RULES

- MV1: Primary desire/need/fear/drive exist.
- MV2: Goals stack exists (primary + scene-level optional).
- MV3: At least one motivational conflict recorded for key characters.
- MV4: Scene intents (if used) show tactic + outcome + goal update.

---

OWNER: Universe Engine
LOCK: FIXED
