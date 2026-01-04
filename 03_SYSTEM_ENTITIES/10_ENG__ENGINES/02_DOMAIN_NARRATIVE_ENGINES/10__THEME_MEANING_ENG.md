# Theme & Meaning Engine
FILE: 10__THEME_MEANING_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 02_DOMAIN_NARRATIVE_ENGINES
CLASS: DOMAIN (L2)
LEVEL: L2
STATUS: ACTIVE
VERSION: 2.0
ROLE: Defines theme, meaning, and moral/idea constraints; produces explicit theme maps, questions, and meaning anchors that must manifest through choices and consequences across scenes/arcs

---

## PURPOSE

Theme & Meaning — это “о чём это на самом деле”.
Движок нужен, чтобы:
- история не была набором событий
- смыслы были повторяемыми и управляемыми
- выборы героев отражали тему
- последствия “говорили” (message through outcomes)

---

## NON-GOALS

- не заменяет структуру (Story Structure)
- не заменяет драматическую дугу (Dramatic Arc)
- не заменяет символизм как стиль (Symbolism engine в Genre/Style)
Он определяет **смысловые ограничения и цели**, которые должны проявиться в сюжете.

---

## MINI-CONTRACT (MANDATORY)

### CONSUMES
- Premise + central question (from Story Structure)
- Character values/fears (optional, from character family)
- World ideology/belief (optional, from world family)
- Planned stakes and consequences (from STS / Scene Specs)

### PRODUCES
- THEME MAP (TM) — canonical artifact
- THEME QUESTIONS set
- MEANING ANCHORS registry (choices, costs, symbols)
- THEME CONSISTENCY CHECKS (flags)

### DEPENDS_ON
- 02_DOMAIN_NARRATIVE_ENGINES/02__STORY_STRUCTURE_ENG.md
- 02_DOMAIN_NARRATIVE_ENGINES/04__SCENE_CONSTRUCTION_ENG.md
- 06_GENRE_STYLE_ENGINES/04__SYMBOLISM_ENG.md (optional integration)
- 06_GENRE_STYLE_ENGINES/05__METAPHOR_ENG.md (optional integration)

### OUTPUT_TARGET
- Feeds: Scene Construction, Foreshadowing, Twist/Reveal, Continuity
- Provides targets for production (visual motifs/sound motifs as meaning anchors)

---

## CANON TERMS

### THEME
Повторяющаяся идея/напряжение:
- “свобода vs контроль”
- “правда vs удобная ложь”
- “любовь как риск”
Это не лозунг. Это конфликт смысла.

### THEME QUESTION
Вопрос, который история исследует, а не “отвечает” сразу.

### MEANING ANCHOR
Якорь смысла — конкретная штука в тексте/сцене:
- выбор героя
- цена решения
- повторяющийся образ
- ключевая реплика
- символический объект

### MESSAGE THROUGH CONSEQUENCES
Смысл должен проявляться через последствия, а не через морализаторство.

---

## THEME AXES (TOOLBOX)

Выбираешь 1 главный и 1–2 вторичных:

- freedom / control
- truth / comfort
- love / fear
- order / chaos
- power / responsibility
- identity / mask
- faith / doubt
- survival / humanity

Rule:
- axes must be declared in Theme Map.

---

## REQUIRED ARTIFACT: THEME MAP (TM)

### TM SCHEMA (CANON)

Header:
- TM_ID:
- SCOPE:
  - episode | arc | season | book
- PRIMARY THEME AXIS:
- SECONDARY AXES:
- THEME STATEMENT (1–2 lines):
  - not a slogan; tension phrased as a conflict
- THEME QUESTIONS (3–7):
  - list

Anchors registry (repeat):
- ANCHOR_ID: TA-0001
- TYPE:
  - choice | cost | symbol | line | motif | consequence
- WHERE IT APPEARS:
  - SCENE_ID / segment
- WHAT IT MEANS:
  - interpretation
- HOW IT SUPPORTS THEME:
  - explicit link to axis/question
- STRENGTH:
  - subtle | balanced | explicit
- PAYOFF TARGET (optional):
  - SCENE_ID if it returns
- CONTINUITY REQUIREMENTS:
  - what must remain true

Theme progression (ordered):
For each act/episode block:
- BLOCK_ID:
- THEME PRESSURE:
  - how the theme is tested here
- KEY CHOICE:
  - what choice embodies theme conflict
- OUTCOME / MESSAGE THROUGH CONSEQUENCES:
  - what the result “says” (without preaching)
- NEXT THEME SHIFT:
  - how the theme evolves

Risk flags:
- preachy risk
- theme drift risk
- inconsistent consequences risk
- symbol spam risk

---

## THEME RULES (CANON)

### TM1 — Theme must be testable
Если тема не проявляется через выбор/цену → это декорация.

### TM2 — No preaching
Тема должна проявляться через:
- действия
- последствия
- контраст
Не через “монолог автора”.

### TM3 — Consequences must align with theme
Если герой выбирает “ложь”, последствия должны отражать исследование темы,
иначе тема ломается.

### TM4 — Anchors must be concrete
“Мы про свободу” без якорей — пусто.
Нужно минимум:
- 2–3 anchors на episode
- 5–12 anchors на arc/season segment
(можно иначе, но declared)

### TM5 — Theme survives twists
После reveal/twist тема должна стать:
- глубже, или
- сложнее, или
- болезненнее
Если твист разрушает тему → твист неправильный.

### TM6 — Symbol economy
Символов должно быть мало, но сильно.
Слишком много символов = шум.

---

## THEME CONSISTENCY CHECKS

Flag if:
- theme statement not reflected in any key choice
- consequences contradict theme pressure
- anchors don’t connect to axes/questions
- too many explicit “message lines”
- anchors appear but never pay off (if promised)

Fix options:
- add theme-choice scene beat
- align consequences via STS + continuity
- reduce explicit lines; convert to action/cost
- consolidate symbols/motifs

---

## PROCEDURE (HOW TO RUN)

1) Declare primary axis + secondary axes
2) Write theme statement + theme questions
3) For each structure block:
   - define how theme is tested
   - define key choice + consequence message
4) Create anchors registry (choices/costs/symbols)
5) Link anchors to scenes + continuity requirements
6) Run consistency checks
7) Output Theme Map and lock

---

## QC CHECKLIST (MANDATORY)

- are axes declared?
- do questions exist (3–7)?
- does each block have theme pressure + choice + outcome?
- are anchors concrete and linked to scenes?
- do consequences align with theme?
- any preachy drift?
- do twists deepen theme (not break it)?

---

## VALIDATION RULES

- THV1: TM exists with axes, questions, anchors, and progression blocks.
- THV2: At least one key choice per block embodies the theme conflict.
- THV3: Anchors have concrete appearances and meanings.
- THV4: No unresolved theme drift flags remain without declared intent.

---

OWNER: Universe Engine
LOCK: FIXED
