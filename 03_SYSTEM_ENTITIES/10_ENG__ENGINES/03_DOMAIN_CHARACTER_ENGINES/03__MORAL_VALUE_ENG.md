# Moral & Value Engine
FILE: 03__MORAL_VALUE_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 03_DOMAIN_CHARACTER_ENGINES
CLASS: DOMAIN (L2)
LEVEL: L2
STATUS: ACTIVE
VERSION: 2.0
ROLE: Defines a character’s value system, moral boundaries, taboos, justifications, and dilemma resolution logic; produces a Value Framework that drives believable choices and moral cost across scenes/arcs

---

## PURPOSE

Ценности и мораль — это “почему он считает это правильным/неправильным”.
Движок нужен, чтобы:
- решения были последовательны
- “границы” были настоящими, а не декором
- моральная цена решений фиксировалась
- дилеммы были честными (нет правильного ответа без цены)

---

## NON-GOALS

- не задаёт мотивации/цели (Motivation engine)
- не делает психику/травмы (Psychology engine)
- не пишет диалоги (Dialogue engine)
Он описывает **компас** персонажа и алгоритм выбора в дилеммах.

---

## MINI-CONTRACT (MANDATORY)

### CONSUMES
- Character Spec (CS)
- Motivation Map (MM) (recommended)
- Theme Map (TM) (optional)
- World ideology/law constraints (optional)

### PRODUCES
- VALUE FRAMEWORK (VF) — canonical artifact
- MORAL BOUNDARIES (lines)
- JUSTIFICATION PATTERNS (how they rationalize)
- DILEMMA MAP (repeatable dilemma templates)
- MORAL COST TRACKING hooks (for evolution/continuity)

### DEPENDS_ON
- 03_DOMAIN_CHARACTER_ENGINES/01__CHARACTER_CORE_ENG.md
- 03_DOMAIN_CHARACTER_ENGINES/02__MOTIVATION_DESIRE_ENG.md (recommended)

### OUTPUT_TARGET
- Feeds:
  - 03__CHARACTER_BEHAVIOR_ENG (choices)
  - 07__DIALOGUE_ENG (moral language)
  - 10__CHARACTER_EVOLUTION_ENG (moral drift/cost)
  - 02__NARRATIVE_CONTINUITY_ENG (cost persistence)

---

## CANON TERMS

### VALUE
То, что считается важным:
- честность, свобода, порядок, семья, власть, милосердие

### PRINCIPLE
Правило поведения, выведенное из ценности:
- “не врать близким”
- “никогда не оставлять своих”

### LINE / BOUNDARY
Граница, которую они не пересекают без огромной цены.

### JUSTIFICATION
Механизм оправдания:
- “это было необходимо”
- “они заслужили”
- “я защищаю…”

### MORAL COST
Цена, которую платит персонаж (вина, деградация, утрата себя, разрыв связи).

---

## VALUE AXES (TOOLBOX)

Ось задаёт направление компаса:
- mercy vs justice
- freedom vs order
- loyalty vs truth
- self vs others
- purity vs pragmatism
- peace vs victory

Rule:
- choose 1–2 dominant axes for VF.

---

## REQUIRED ARTIFACT: VALUE FRAMEWORK (VF)

### VF SCHEMA (CANON)

Header:
- VF_ID:
- CHARACTER_ID:
- SCOPE:
- VERSION:
- STATUS:

Core Values:
- VALUES (3–7):
  - value: meaning
- DOMINANT AXES:
  - axis 1, axis 2
- TOP PRINCIPLES (3–7):
  - principle statements

Boundaries:
- HARD LINES (1–3):
  - “never do X”
- SOFT LINES (1–3):
  - “avoid X unless Y”
- CROSSING PRICE:
  - what cost is required if crossed

Moral Ranking (priority order):
- PRIORITY LIST:
  - e.g., loyalty > truth > mercy
Rule:
- ranking must exist, or dilemmas become random.

Justification Patterns:
- PRIMARY JUSTIFICATION STYLE:
  - duty | care | ideology | survival | honor | revenge
- COMMON RATIONALIZATIONS (list):
- SELF-DECEPTION RISK:
  - what lie they tell themselves

Dilemma Map (templates):
- DILEMMA_01:
  - AXIS:
  - OPTION A (value/principle):
  - OPTION B (value/principle):
  - COST A:
  - COST B:
  - DEFAULT CHOICE (if pressured):
  - WHAT WOULD CHANGE THEIR CHOICE:
    - triggers, stakes, relationships

Moral Cost Tracking:
- COST TOKENS:
  - guilt | shame | numbness | cruelty | faith-crack | self-respect loss
- COST ACCUMULATION RULE:
  - how costs stack
- REDEMPTION CONDITIONS (optional):
  - what would repair them

Language Hooks (optional):
- MORAL VOCAB:
  - words/phrases they use to justify
- MORAL SILENCES:
  - what they avoid saying

---

## MORAL RULES (CANON)

### MV1 — Principles must constrain action
Если принцип declared, он обязан:
- остановить действие, или
- сделать действие дороже (cost),
или это не принцип, а декорация.

### MV2 — Dilemmas must have real cost
Если выбор “и так хорошо, и так хорошо” — это не дилемма.
Должна быть потеря в любом варианте.

### MV3 — Priority list resolves conflicts
Когда ценности конфликтуют, порядок решает.
Если нет порядка — персонаж становится “авторским джойстиком”.

### MV4 — Boundary crossing must scar
Если персонаж пересёк hard line — это событие:
- меняет self-image
- требует continuity entry
- влияет на evolution

### MV5 — Justification must fit persona
Оправдания должны соответствовать:
- архетипу
- культуре мира
- травме/опыту
Иначе звучит как чужой голос.

---

## INCONSISTENCY DETECTOR (HEURISTICS)

Flag if:
- character repeatedly violates declared principles with no cost
- boundary crossed but no scar/continuity update
- dilemmas have no real tradeoff
- justification language inconsistent across scenes
- priority list missing while conflicts occur

Fix options:
- adjust principle into softer line
- add moral cost and track it
- rewrite choice to include tradeoff
- unify moral vocabulary
- set explicit priority list

---

## PROCEDURE (HOW TO RUN)

1) Read CS + MM
2) Select values (3–7) and dominant axes
3) Write principles (3–7) derived from values
4) Define boundaries (hard/soft) + crossing price
5) Build priority list
6) Define justification patterns + moral vocabulary
7) Create dilemma templates (at least 1–3 for key characters)
8) Define moral cost tokens + accumulation rule
9) Run QC checks

---

## QC CHECKLIST (MANDATORY)

- values 3–7 exist?
- principles derived from values exist?
- boundaries (hard/soft) + crossing price defined?
- priority list present?
- at least 1 dilemma template exists?
- moral cost tracking defined?
- justification patterns consistent with character?

---

## VALIDATION RULES

- MVV1: VF complete with values, principles, boundaries, priority list.
- MVV2: Dilemmas include real tradeoffs and costs.
- MVV3: Boundary crossing has defined price + scar logic.
- MVV4: Moral cost tracking hooks exist for continuity/evolution.

---

OWNER: Universe Engine
LOCK: FIXED
