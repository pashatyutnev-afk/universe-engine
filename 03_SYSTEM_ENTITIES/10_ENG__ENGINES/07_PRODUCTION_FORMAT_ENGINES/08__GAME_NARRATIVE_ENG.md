# Game Narrative Engine
FILE: 08__GAME_NARRATIVE_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 07_PRODUCTION_FORMAT_ENGINES
CLASS: PRODUCTION (L3)
LEVEL: L3
STATUS: ACTIVE
VERSION: 2.0
ROLE: Defines reproducible rules for interactive storytelling (player agency, quest/mission loops, objective design, reward cadence, fail states, diegetic exposition, and cutscene caps); produces Game Narrative Bibles, Quest Specs, Agency Maps, and QC Gates that preserve canon and genre contract while translating beats into playable mechanics

---

## PURPOSE

Игра — это формат, где:
- игрок действует, а не только смотрит
- “история” должна быть совместима с механикой
- экспозицию лучше показывать диэгетически
- награды и фейлы — часть драматургии

Движок нужен, чтобы:
- переводить канон/сцены в миссии/квесты
- сохранять жанр и смысл при агентности игрока
- управлять лупами (gameplay ↔ narrative)
- избегать “катсцена-симулятора”
- контролировать ясность и мотивацию игрока

---

## NON-GOALS

- не проектирует боевую/экономическую механику глубоко
- не заменяет World/Character engines
- не заменяет UI/UX специфику
Он задаёт **нарративную структуру игры** и правила перевода beats → gameplay.

---

## MINI-CONTRACT (MANDATORY)

### CONSUMES
- Canon world laws + timeline facts
- Character goals/values and arcs
- Narrative beats (events/turning points/climax)
- Genre + tone locks
- Target game type (linear, open world, roguelike, etc.)

### PRODUCES
- GAME NARRATIVE BIBLE (GNB) — canonical artifact
- AGENCY MAP (AM)
- QUEST / MISSION SPEC (QMS)
- REWARD CADENCE MAP (RCM)
- FAIL STATE POLICY (FSP)
- DIEGETIC EXPO RULES (DER)
- CUTSCENE CAP POLICY (CCP)
- GAME QC GATES (GQG)

### DEPENDS_ON
- 07_PRODUCTION_FORMAT_ENGINES/03__FORMAT_ADAPTATION_ENG.md
- 04_DOMAIN_WORLD_ENGINES (laws/timeline/tech)
- 03_DOMAIN_CHARACTER_ENGINES (motivation/behavior)
- 05_EXPRESSION_ENGINES (turning points, resolution)
- 06_GENRE_STYLE_ENGINES (tone/atmosphere)

### OUTPUT_TARGET
- Feeds:
  - quest trees / mission flows
  - dialogue and encounter beats
  - cutscene list (bounded)
  - narrative QA checklist

---

## CANON TERMS

### AGENCY
Степень свободы игрока, которая реально влияет на результат.

### QUEST LOOP
Цикл: goal → obstacles → action → feedback → reward → next goal.

### DIEGETIC
Встроенное в мир:
- таблички, предметы, поведение NPC, окружение

### FAIL STATE
Состояние провала:
- смерть, потеря ресурса, потеря репутации, срыв дедлайна

### NARRATIVE-MECHANIC ALIGNMENT
Когда механика выражает смысл:
- “драма через геймплей”, а не текстом.

---

## CORE RULES (CANON)

### GN1 — Player agency is real or removed
Если выбор ни на что не влияет — его не должно быть.

### GN2 — Beats translate into objectives
События и повороты превращаются в:
- цели
- препятствия
- условия успеха
- последствия

### GN3 — Rewards are narrative punctuation
Награды — это:
- “точки смысла”
- не только лут, но и:
  - доступ, знания, отношения, власть

### GN4 — Fail states must be meaningful
Фейл должен:
- быть понятным
- иметь последствия (или reset policy)
- усиливать stakes, а не просто раздражать

### GN5 — Exposition must be diegetic-first
Сначала:
- окружение/действия/объекты
Потом:
- диалоги
Последнее:
- лор-лекции.

### GN6 — Cutscenes are capped
Катсцены — строго по CCP.
Игра должна быть “игрой”.

### GN7 — Canon cannot be broken by gameplay
Если gameplay требует “нарушить канон”:
- меняется gameplay
- или вводится каноническое объяснение (через governance)

---

## REQUIRED ARTIFACT A: GAME NARRATIVE BIBLE (GNB)

### GNB SCHEMA (CANON)

Header:
- GNB_ID:
- PROJECT_ID / WORLD_ID:
- GAME TYPE:
  - linear | hub-based | open world | roguelike | sandbox | hybrid
- TARGET PLAYTIME:
- VERSION:
- STATUS:
  - draft | canon | deprecated

Locks:
- GENRE LOCK:
- TONE LOCK:
- CANON FACTS LOCK (critical):
- TABOOS:
- CLARITY FLOOR:

Narrative operating rules:
- PLAYER ROLE (who you are):
- CORE FANTASY (why it feels good):
- MAIN GOAL:
- MAIN THREAT:
- WORLD TRUTH (3–7 laws/facts):
- CHARACTER RELATIONSHIP CORE:
- “WHAT PLAYERS DO MOST” (primary loop)

Rule:
- GNB is the narrative OS of the game.

---

## REQUIRED ARTIFACT B: AGENCY MAP (AM)

### AM SCHEMA (CANON)

- AM_ID:
- GNB_ID:

Agency domains:
- CHOICE TYPES allowed:
  - moral | tactical | social | exploration | resource
- BRANCHING DEPTH CAP:
- “ILLUSION OF CHOICE” BAN:
  - if no outcome change → remove

For each major choice:
- CHOICE ID:
- CONTEXT:
- OPTIONS:
- OUTCOME TYPES:
  - world state | relationship | resources | access | ending flag
- CANON SAFETY:
  - allowed outcomes within canon
- PAYOFF WINDOW:
  - when player sees consequence

Rule:
- Every choice must have payoff window.

---

## REQUIRED ARTIFACT C: QUEST / MISSION SPEC (QMS)

### QMS SCHEMA (CANON)

- QMS_ID:
- GNB_ID:

For each quest/mission:
- QUEST ID:
- QUEST PURPOSE (narrative function):
  - setup | escalation | reveal | reversal | climax | resolution | world texture
- ENTRY CONDITIONS:
- GOAL STATEMENT (clear):
- OBJECTIVES (ordered):
- OBSTACLES:
- SUCCESS CONDITIONS:
- FAIL CONDITIONS:
- CONSEQUENCES (success/fail):
- REQUIRED NPCs / LOCATIONS / PROPS:
- DIALOGUE/EXPO NOTES (diegetic-first):
- REWARD (narrative + mechanical):
- “STATE CHANGE LOG”:
  - what changed in world/relationships

Rule:
- Every quest must have state change log.

---

## REQUIRED ARTIFACT D: REWARD CADENCE MAP (RCM)

### RCM SCHEMA (CANON)

- RCM_ID:
- GNB_ID:

Cadence:
- MICRO REWARDS:
  - every N minutes/objectives
- QUEST COMPLETION REWARDS:
  - always
- ARC MILESTONE REWARDS:
  - major
- “KNOWLEDGE REWARDS”:
  - reveals, truths, access

Reward types:
- loot/resource
- access (new area/tool)
- relationship shift
- story reveal
- power/status
- aesthetic/collection

Rule:
- Reward cadence must align with tension waves.

---

## REQUIRED ARTIFACT E: FAIL STATE POLICY (FSP)

### FSP SCHEMA (CANON)

- FSP_ID:
- GNB_ID:

Fail model:
- HARD FAIL:
  - game over / restart segment
- SOFT FAIL:
  - loss with continuation (preferred where possible)
- TIME FAIL:
  - missed deadline → world changes

Rules:
- FAIL CLARITY:
  - player understands why failed
- FAIL FAIRNESS:
  - no cheap gotcha
- FAIL CONSEQUENCE:
  - must matter (or be clearly reset)
- CHECKPOINT POLICY:
- RETRY FATIGUE CONTROL:
  - reduce repetition loops

Rule:
- Fail state is part of drama and pacing, not punishment.

---

## REQUIRED ARTIFACT F: DIEGETIC EXPO RULES (DER)

### DER SCHEMA (CANON)

- DER_ID:
- GNB_ID:

Expo priority:
1) environment storytelling
2) player actions and mechanics
3) NPC behavior
4) short dialogue
5) lore logs (optional)
6) exposition dump (banned unless emergency)

Rules:
- MAX EXPO IN ONE NODE:
- EXPO MUST PAY:
  - new ability, new path, or new consequence
- “SHOW LAW” requirement:
  - world laws demonstrated via gameplay

Rule:
- Lore is earned and paid, not dumped.

---

## REQUIRED ARTIFACT G: CUTSCENE CAP POLICY (CCP)

### CCP SCHEMA (CANON)

- CCP_ID:
- GNB_ID:

Caps:
- MAX CUTSCENE LENGTH:
- MAX CUTSCENE COUNT per hour:
- MAX UNINTERRUPTED NON-PLAY time:
- “CUTSCENE PURPOSES allowed”:
  - major reveal | arc milestone | emotional climax | world transformation
- “CUTSCENE BAN”:
  - explaining mechanics
  - repeating what player already did

Rule:
- Cutscenes exist only for high-value beats.

---

## REQUIRED ARTIFACT H: GAME QC GATES (GQG)

### GQG SCHEMA (CANON)

- GQG_ID:
- GNB_ID:

Gates:
1) Agency gate:
   - AM choices have real outcomes
2) Objective clarity gate:
   - QMS goals are clear and trackable
3) Narrative-mechanic alignment gate:
   - mechanics express beat meaning
4) Reward cadence gate:
   - RCM satisfied; no dead zones
5) Fail state gate:
   - FSP fair, clear, meaningful
6) Diegetic expo gate:
   - DER followed; no lore dumps
7) Cutscene cap gate:
   - CCP respected
8) Canon gate:
   - no canon breaks; world laws obeyed
9) Tone/genre gate:
   - locks respected across gameplay

Rule:
- Fail 2+ gates → quest flow rewrite required.

---

## INCONSISTENCY DETECTOR (HEURISTICS)

Flag if:
- choices have no consequences
- quests feel like errands (no state change)
- rewards are random and not meaningful
- fail states feel unfair or repetitive
- lore delivered as long text lectures
- cutscenes too many/too long
- gameplay requires canon contradiction

Fix options:
- remove fake choices; add real state flags
- rewrite quests around beats and consequences
- align rewards with reveals/access/relationships
- convert hard fails to soft fails where possible
- move expo into environment and mechanics
- cap cutscenes and shift into playable moments
- adjust gameplay to obey world laws (or run governance)

---

## PROCEDURE (HOW TO RUN)

1) Define GNB (role, fantasy, locks, loops)
2) Build AM (choices + payoff windows)
3) Translate beats into QMS quests/missions
4) Define RCM (reward cadence)
5) Define FSP (fail model, checkpoints)
6) Define DER (diegetic exposition rules)
7) Define CCP (cutscene caps)
8) Run GQG gates across quest tree
9) Canonize and log via governance

---

## QC CHECKLIST (MANDATORY)

- GNB locks canon facts and genre/tone?
- AM maps real choices with payoff windows?
- QMS defines objectives, fail/success, consequences, state change logs?
- RCM avoids reward dead zones?
- FSP ensures fair meaningful fail states?
- DER prevents lore dumps and shows world laws via play?
- CCP caps non-play time?
- GQG gates applied?

---

## VALIDATION RULES

- GNV1: Agency is real, choices are paid.
- GNV2: Quests translate beats into clear objectives with consequences.
- GNV3: Reward cadence supports tension and motivation.
- GNV4: Fail states are fair, meaningful, and controlled.
- GNV5: Exposition is diegetic-first; cutscenes are capped.
- GNV6: Canon and genre/tone remain stable across gameplay.

---

OWNER: Universe Engine
LOCK: FIXED
