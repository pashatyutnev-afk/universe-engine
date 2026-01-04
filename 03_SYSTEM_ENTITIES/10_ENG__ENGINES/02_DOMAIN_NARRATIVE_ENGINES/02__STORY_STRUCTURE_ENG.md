# Story Structure Engine
FILE: 02__STORY_STRUCTURE_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 02_DOMAIN_NARRATIVE_ENGINES
CLASS: DOMAIN (L2)
LEVEL: L2
STATUS: ACTIVE
VERSION: 2.0
ROLE: Defines reproducible story macro-structure (acts/episodes/turns) and produces a Story Structure Spec that maps major beats, reversals, reveals, and payoffs across a defined scope

---

## PURPOSE

Story Structure — это “каркас” истории на уровне:
- эпизода
- арки
- сезона
- книги

Движок нужен, чтобы:
- история имела понятную прогрессию
- поворотные точки были распределены осознанно
- setup/payoff работали системно
- можно было масштабировать сюжет без потери контроля

---

## NON-GOALS

- не пишет конкретные сцены покадрово (это Scene Construction)
- не делает темп/ритм (это Pacing & Rhythm)
- не занимается стилем (Genre/Style)
Он определяет структурную сетку, на которую потом “надеваются” сцены.

---

## MINI-CONTRACT (MANDATORY)

### CONSUMES
- Narrative Logic Spec (NLS) constraints
- Theme hook (from Theme & Meaning)
- Scope definition (episode/arc/season/book)
- Key characters list (optional)
- World timeline anchors (optional)

### PRODUCES
- STORY STRUCTURE SPEC (SSS)
- ACT/EPISODE MAP
- TURN MAP (major turns + their purpose)
- SETUP/PAYOFF MAP (what is introduced and where it pays)

### DEPENDS_ON
- 02_DOMAIN_NARRATIVE_ENGINES/01__NARRATIVE_LOGIC_ENG.md
- 02_DOMAIN_NARRATIVE_ENGINES/10__THEME_MEANING_ENG.md

### OUTPUT_TARGET
- Feeds Dramatic Arc (03) and Scene Construction (04)
- Provides structure constraints for Twist/Reveal (08) and Continuity (09)

---

## CANON TERMS

### SCOPE UNIT
- EPISODE: 1-contained structure
- ARC: multiple episodes/scenes around one primary change
- SEASON: collection of arcs with season-level turn points
- BOOK: long-form analogous to season/arc mapping

### STRUCTURAL TURN
Поворот, который меняет направление истории:
- goal flips
- stakes escalate
- new truth revealed
- ally becomes enemy, etc.

### SETUP/PAYOFF
Любая сильная установка должна иметь точку возврата (payoff) или осознанный отказ.

---

## STRUCTURE PATTERNS (TOOLBOX)

(Не догма. Выбираешь 1 как “основной”.)

### Pattern A: 3-Act
- Act I: setup + inciting + commitment
- Act II: escalation + complications + midpoint turn
- Act III: climax + resolution + consequences

### Pattern B: 5-Act
- intro / rising / midpoint / falling / finale

### Pattern C: Episodic loop with season spine
- episodes have mini-acts
- season has 3–5 big turns across episodes

Rule:
- Pattern must be declared in SSS (иначе структура “случайная”).

---

## REQUIRED ARTIFACT: STORY STRUCTURE SPEC (SSS)

### SSS SCHEMA (CANON)

- SSS_ID:
- SCOPE:
  - episode | arc | season | book
- PATTERN:
  - 3-act | 5-act | episodic-spine | custom
- PREMISE (1–2 lines):
- CENTRAL QUESTION:
  - what question drives the structure
- THEME HOOK:
  - pointer or short statement

### STRUCTURE MAP
- SECTION 1 (Act/Ep block):
  - PURPOSE:
  - START STATE:
  - END STATE:
  - KEY TURNS:
    - T1 (what flips + why)
  - SETUP ITEMS:
  - PAYOFF TARGETS:

(repeat for sections)

### TURN INVENTORY (GLOBAL)
- T1:
  - type: inciting | midpoint | reversal | reveal | climax-turn | consequence-turn
  - effect: what changes
  - dependency: what must be set up before this

### SETUP/PAYOFF MAP
- S1: setup item -> payoff target (where/how)
- S2...

### RISK FLAGS (OPTIONAL)
- pacing risk
- too many turns
- weak midpoint
- payoff missing

---

## STRUCTURE RULES (CANON)

### SS1 — State progression must exist
Каждый act/episode должен менять глобальное состояние.
Если “ничего не изменилось” → структура не работает.

### SS2 — Turns are intentional
Ключевые повороты не появляются случайно.
Каждый turn имеет:
- purpose
- dependency (что надо подготовить)

### SS3 — Setup discipline
Если setup сильный → он в карте payoff.
Если payoff отсутствует → пометить intentional and rare.

### SS4 — Scale consistency
Если scope = season, структура должна включать:
- season inciting
- mid-season turn
- finale turn
(минимум 3 крупных turn)

### SS5 — Structural clarity beats complexity
Слишком много turn points ломают читаемость.
Если >7 major turns на episode → риск перегруза (flag).

---

## PROCEDURE (HOW TO RUN)

1) Declare scope + pattern
2) Write premise + central question
3) Build sections (acts/episodes) with start/end states
4) Place major turns (inciting/midpoint/climax)
5) Fill setup/payoff map
6) Run checklist (below)
7) Output SSS

---

## STRUCTURE CHECKLIST

- is scope declared clearly?
- is pattern declared and followed?
- does each section have start/end state?
- do major turns exist and are spaced plausibly?
- are stakes rising across structure?
- are setup items mapped to payoff?
- does structure align with theme hook?

---

## VALIDATION RULES

- SSV1: SSS has scope + pattern + structure map.
- SSV2: Major turns are explicit and purposeful.
- SSV3: Setup/payoff map exists (>=1 item unless declared none).
- SSV4: Structure is compatible with NLS (no logical contradictions).

---

OWNER: Universe Engine
LOCK: FIXED
