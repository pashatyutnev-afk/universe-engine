# Series & Episode Engine
FILE: 05__SERIES_EPISODE_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 07_PRODUCTION_FORMAT_ENGINES
LEVEL: L3
STATUS: ACTIVE
VERSION: 1.0
ROLE: Defines episodic structure, season arcs, hooks, recaps, and cliffhanger logic

---

## PURPOSE

Сериал — это:
- повторяющийся цикл: hook → build → payoff → cliff
- сезонная дуга
- эпизодные мини-дуги

Движок задаёт:
- модель эпизода
- правила сезона
- баланс “episode plot” vs “season plot”
- управление клиффхенгерами и рекапами

---

## INPUTS

- Genre + blending rules
- Main arcs (character/world)
- Platform constraints (runtime, censorship)
- Release cadence

---

## OUTPUTS

- Season format spec
- Episode template
- Hook/cliff rules
- Recap policy

---

## EPISODE TEMPLATE (CANON)

- COLD OPEN (hook)
- SETUP (goal/stakes)
- COMPLICATION (worse)
- MID TURN (shift)
- ESCALATION (pressure)
- PAYOFF (mini-resolution or reveal)
- CLIFF (new question / danger)

---

## SEASON STRUCTURE (CANON)

- Season question (главный вопрос сезона)
- Midpoint reversal episode
- Two “peak episodes” (near end)
- Finale payoff + next-seed

---

## VALIDATION RULES

- SE1: Каждый эпизод имеет закрытие хотя бы одной подсетки.
- SE2: Клифф создаёт вопрос, но не должен быть дешёвым.
- SE3: Рекап не повторяет, а подсвечивает нужное.

---
OWNER: Universe Engine
STATUS: FIXED
