# Scene Construction Engine
FILE: 04__SCENE_CONSTRUCTION_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 02_DOMAIN_NARRATIVE_ENGINES
CLASS: DOMAIN (L2)
LEVEL: L2
STATUS: ACTIVE
VERSION: 2.0
ROLE: Converts structure + dramatic arc + constraints into a reproducible Scene Spec; defines beat grammar, turn/climax resolution logic, and continuity payload required for downstream engines

---

## PURPOSE

Сцена — это минимальная “единица истории”, которая обязана:
- иметь цель
- содержать конфликт/напряжение
- менять состояние (до/после)
- двигать дугу и структуру

Этот движок создаёт **Scene Spec**, по которому:
- Character engines понимают мотивации/поведение/диалог
- World engines фиксируют место/время/ограничения
- Production engines (camera/lighting/editing/sound) строят выпуск

---

## NON-GOALS

- не делает художественный стиль (Genre/Style)
- не делает монтаж (Editing engine)
- не пишет музыку (Sound/Music)
Он делает структуру и смысл сцены, как данные.

---

## MINI-CONTRACT (MANDATORY)

### CONSUMES
- Narrative Logic Spec (NLS)
- Story Structure Spec (SSS)
- Dramatic Arc Spec (DAS)
- World constraints (laws/timeline/location) if known
- Character constraints (goals/limits/relationships) if known

### PRODUCES
- SCENE SPEC (SS) — canonical payload
- BEAT LIST (ordered)
- TURN + CLIMAX + RESOLUTION mapping
- CONTINUITY NOTES (required)
- HOOKS for production (visual/audio cues as tags)

### DEPENDS_ON
- 02_DOMAIN_NARRATIVE_ENGINES/01__NARRATIVE_LOGIC_ENG.md
- 02_DOMAIN_NARRATIVE_ENGINES/02__STORY_STRUCTURE_ENG.md
- 02_DOMAIN_NARRATIVE_ENGINES/03__DRAMATIC_ARC_ENG.md

### OUTPUT_TARGET
- Feeds: Pacing (05), Tension/Stakes (06), Continuity (09), Theme (10)
- Handoff to: Character family (03_*), World family (04_*), Production families (07/08/09)

---

## CANON TERMS

### SCENE GOAL
Что зритель/читатель должен понять/почувствовать/увидеть как изменение.

### SCENE QUESTION
Вопрос сцены: “получится ли X?” — держит внимание.

### BEAT
Мини-движение сцены, которое меняет положение сил/информации/эмоции.

### TURN
Поворот: сцена меняет направление/смысл (“не так как ожидали”).

### CLIMAX
Точка максимального давления, где решение неизбежно.

### RESOLUTION
Разрешение конфликта сцены (не обязательно “хэппи”).

### CONSEQUENCES
Что становится истинным после сцены (state after).

---

## BEAT GRAMMAR (CANON)

Типы битов (tag per beat):
- SETUP: вводит контекст/позиции
- PROBE: попытка/проверка
- OBSTACLE: препятствие усиливает давление
- REVEAL: новая информация меняет смысл
- SHIFT: изменение власти/инициативы
- CHOICE: выбор героя (или системы)
- COLLISION: столкновение сил
- PAYOFF: возврат setup
- RELEASE: короткая разрядка (редко в середине)
- EXIT: выход/переход в следующее состояние

Правило:
- каждый beat должен иметь function tag
- не более 2 “texture beats” подряд (иначе сцена вязнет)

---

## REQUIRED CANON ARTIFACT: SCENE SPEC (SS)

### SCENE_SPEC SCHEMA (CANON PAYLOAD)

Header:
- SCENE_ID:
- TITLE:
- SCOPE_UNIT:
  - episode | arc | season | book
- LOCATION:
- TIME:
- POV (if applicable):
- STATUS:
  - draft | active | locked
- VERSION:

Intent:
- SCENE GOAL (1 line):
- SCENE QUESTION:
- PRIMARY EMOTION TARGET:
- THEME HOOK (pointer or line):

State:
- BEFORE STATE (facts):
- AFTER STATE (facts):

Cast/Forces:
- ACTIVE CHARACTERS:
- OPPOSING FORCE:
  - person | system | nature | self | society
- RESOURCES AT PLAY:
- INFORMATION ASYMMETRY:
  - who knows what

Conflict:
- CONFLICT TYPE:
  - internal | interpersonal | systemic | survival | moral
- STAKES:
  - what is at risk if fail
- PRESSURE SOURCE:
  - time | threat | scarcity | exposure | relationship

Beats (ordered):
- BEAT 01:
  - TAG:
  - WHAT HAPPENS:
  - WHY (cause):
  - EFFECT:
  - STATE CHANGE (micro):
- BEAT 02...
(typical: 5–12 beats; may vary)

Turn/Climax/Resolution:
- TURN:
  - what flips + why
- CLIMAX:
  - peak pressure moment
- RESOLUTION:
  - what is decided / outcome
- CONSEQUENCES:
  - list (must align with AFTER STATE)

Continuity:
- CONTINUITY NOTES:
  - props, injuries, knowledge, relationships, time
- CANON CONSTRAINTS USED:
  - world law pointers (if any)
  - character constraints pointers (if any)

Production Hooks (tags only, optional but helpful):
- VISUAL HOOKS:
  - symbols, key objects, composition hints
- AUDIO HOOKS:
  - silence moment, impact beat, motif entry
- EDITING HOOKS:
  - “payoff cut”, match cut opportunity, J/L cut moment

Validation:
- CHECKS PASSED:
  - list of checks
- RISKS/FLAGS:
  - list (if any)
- NEXT HANDOFF:
  - which engine consumes next (pacing/continuity/etc)

---

## SCENE RULES (CANON)

### SC1 — Scene changes state
AFTER != BEFORE (минимум 1 факт меняется).
Если не меняется — это interlude и так должно быть помечено.

### SC2 — Scene has a question
Если нет вопроса → нет удержания внимания.

### SC3 — Conflict is explicit
Даже тихая сцена обязана иметь “pressure”.
Без давления — это описание, не сцена.

### SC4 — Stakes are paid
Если stakes заявлены, последствия должны быть.
Нулевые последствия при высоких stakes запрещены.

### SC5 — Turn is expected (often)
Не каждая сцена обязана иметь большой turn,
но если turn нет — должен быть хотя бы micro-shift.

### SC6 — Beats are functional
Каждый beat имеет TAG и делает работу.
Beat без функции = мусор или “texture” (и это помечается).

### SC7 — Continuity notes are mandatory
Без continuity notes сцена не может считаться канонической.

---

## PROCEDURE (HOW TO BUILD A SCENE)

1) Choose scene position (from SSS) + arc target (from DAS)
2) Write SCENE GOAL + QUESTION
3) Define BEFORE/AFTER state
4) Define opposing force + stakes + pressure source
5) Draft beats (5–12) with tags
6) Identify turn + climax + resolution
7) Fill continuity notes + constraints pointers
8) Add production hooks (tags)
9) Run QC checklist
10) Output Scene Spec

---

## QC CHECKLIST (MANDATORY)

- does AFTER differ from BEFORE?
- is the scene goal one clear line?
- is there a scene question?
- is conflict/pressure explicit?
- do beats have tags and cause/effect?
- is there a turn or at least a micro-shift?
- do stakes match consequences?
- are continuity notes present (>=1–3)?
- does it align with NLS/SSS/DAS?

---

## VALIDATION RULES

- SCV1: Scene Spec schema complete (no missing mandatory fields).
- SCV2: Beat list ordered, each beat tagged, with cause/effect.
- SCV3: Turn/climax/resolution exist and align with AFTER state.
- SCV4: Continuity notes exist and are actionable.
- SCV5: No contradictions with narrative logic constraints.

---

OWNER: Universe Engine
LOCK: FIXED
