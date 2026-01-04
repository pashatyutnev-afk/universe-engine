# Symbolism Engine
FILE: 04__SYMBOLISM_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 06_GENRE_STYLE_ENGINES
CLASS: STYLE (L3)
LEVEL: L3
STATUS: ACTIVE
VERSION: 2.0
ROLE: Defines, registers, and governs symbol systems (visual, verbal, sonic, ritual) with explicit meanings, usage contexts, evolution rules, and anti-contradiction gates; produces Symbol Registry, Symbol Packs, Placement Rules, and Consistency Checks to keep symbolism coherent, reusable, and non-random across the canon

---

## PURPOSE

Символизм — это “второй слой смысла”, который:
- усиливает тему
- создаёт узнаваемость вселенной
- связывает сцены через повтор/эхо
- работает даже без прямых слов

Движок нужен, чтобы:
- символы были **не случайными**, а системными
- значения не противоречили друг другу
- символы эволюционировали по правилам
- можно было проверять “правильно ли использован символ”

---

## NON-GOALS

- не заменяет Theme & Meaning (что мы хотим сказать)
- не заменяет Metaphor engine (механика метафорического переноса)
- не заменяет Art Style (визуальный рендер)
Он фиксирует **символы как канонические сущности**.

---

## MINI-CONTRACT (MANDATORY)

### CONSUMES
- Theme/Meaning targets
- Tone/Mood locks
- Emotional anchors (optional)
- World culture/religion constraints
- Visual/audio production constraints

### PRODUCES
- SYMBOL REGISTRY (SR) — canonical artifact
- SYMBOL PACKS (SP) — per arc/location/faction
- PLACEMENT RULES (PR)
- EVOLUTION RULES (ER)
- ANTI-CONTRADICTION GATES (ACG)
- “SYMBOL TO DEPARTMENT” translation map (SDT)

### DEPENDS_ON
- 02_DOMAIN_NARRATIVE_ENGINES/10__THEME_MEANING_ENG.md
- 06_GENRE_STYLE_ENGINES/01__TONE_MOOD_ENG.md
- 06_GENRE_STYLE_ENGINES/03__EMOTIONAL_RESONANCE_ENG.md (anchors overlap control)
- 00_GOVERNANCE_ENGINES/05__CONSISTENCY_ENG.md

### OUTPUT_TARGET
- Feeds:
  - dialogue motifs and phrases
  - set dressing, props, costume motifs
  - sound motifs (bells, drones, alarms)
  - prompt packs and storyboards

---

## CANON TERMS

### SYMBOL
Повторяемый знак (образ/звук/фраза/жест), который несёт смысл.

### PRIMARY MEANING
Основное значение, стабильное для канона.

### SECONDARY MEANINGS
Дополнительные значения, допустимые в контексте.

### SYMBOL CONTEXT
Где и кем символ используется:
- фракция, культура, эпоха, место, ритуал

### SYMBOL COLLISION
Конфликт символов:
- один символ начинает значить противоположное без объяснения

---

## SYMBOLISM RULES (CANON)

### SY1 — Symbol must have explicit meaning
Запрещено: “просто красивый символ”.
У каждого символа есть:
- primary meaning
- contexts
- do/don’t использования

### SY2 — Symbols are scoped
Символы не “везде”.
У символа есть границы:
- культура/фракция/эпоха/место/роль

### SY3 — Repetition requires variation
Повторы без изменения = банализация.
Повтор должен:
- либо усиливать
- либо инвертировать
- либо менять значение по правилам ER

### SY4 — Evolution must be governed
Если значение меняется:
- это фиксируется как evolution event
- и объясняется

### SY5 — No accidental collisions
Если два символа визуально/смыслово похожи:
- либо разводим
- либо объясняем связь (родственные символы)

---

## REQUIRED ARTIFACT A: SYMBOL REGISTRY (SR)

### SR SCHEMA (CANON)

Header:
- SR_ID:
- PROJECT_ID / WORLD_ID:
- SCOPE:
  - world | season | arc
- VERSION:
- STATUS:
  - draft | canon | deprecated

Symbols (repeat):
- SYMBOL_ID:
- NAME (internal):
- FORM:
  - visual | verbal | sonic | gesture | ritual
- PRIMARY MEANING:
- SECONDARY MEANINGS (0–3):
- EMOTIONAL TONE LINK:
  - dread/hope/awe/etc (optional)
- OWNERSHIP / CONTEXT:
  - faction/culture/epoch/location
- APPEARANCE RULES:
  - colors/shapes/materials/sound characteristics
- USAGE RULES:
  - when to use, when not to use
- COLLISION RISKS:
  - what it can be confused with
- EVOLUTION PATH:
  - ER reference (optional)
- FIRST APPEARANCE:
- “DO NOT”:
  - forbidden misuse

Rule:
- Any symbol in canon must be registered here.

---

## REQUIRED ARTIFACT B: SYMBOL PACKS (SP)

### SP SCHEMA (CANON)

- SP_ID:
- SR_ID:
- PACK TYPE:
  - faction | location | ritual | arc | character

Pack contents:
- SYMBOL_ID list (3–12)
- PACK ROLE:
  - identity, warning, comfort, propaganda, sacred
- PRIORITY:
  - primary pack symbols (top 3)

Rule:
- Packs prevent “random symbol spam” and keep selection consistent.

---

## REQUIRED ARTIFACT C: PLACEMENT RULES (PR)

### PR SCHEMA (CANON)

- PR_ID:
- SR_ID:

Rules (repeat):
- SYMBOL_ID:
- PLACEMENT MODES:
  - foreground | background | hidden | audio motif | dialogue
- FREQUENCY:
  - rare | occasional | recurring | constant
- VISIBILITY LEVEL:
  - obvious | subtle | subliminal
- SCENE TYPES:
  - conflict, ritual, quiet, reveal
- WARNING:
  - overuse risks, cliché risks

Rule:
- Each symbol must have at least one frequency + visibility directive.

---

## REQUIRED ARTIFACT D: EVOLUTION RULES (ER)

### ER SCHEMA (CANON)

- ER_ID:
- SR_ID:

Evolution entries (repeat):
- SYMBOL_ID:
- EVOLUTION EVENT:
  - what triggers meaning shift
- OLD MEANING:
- NEW MEANING:
- TRANSITION PHASE:
  - gradual | abrupt | hidden | public
- WHO KNOWS:
  - knowledge distribution
- REQUIRED CONSEQUENCE:
  - what changes in world perception
- REVERSIBILITY:
  - none | partial | full

Rule:
- Meaning shift without ER entry is non-canon.

---

## REQUIRED ARTIFACT E: ANTI-CONTRADICTION GATES (ACG)

### ACG SCHEMA (CANON)

- ACG_ID:
- SR_ID:

Gates:
1) Meaning gate:
   - symbol meaning matches registry context
2) Scope gate:
   - symbol appears only in allowed places/owners
3) Overuse gate:
   - frequency respected
4) Collision gate:
   - no confusion with similar symbols
5) Evolution gate:
   - meaning shifts only via ER
6) Tone gate:
   - symbol usage fits tone/mood locks

Rule:
- Fail 2+ gates → artifact/scene must be corrected.

---

## REQUIRED ARTIFACT F: SYMBOL → DEPARTMENT TRANSLATION (SDT)

### SDT SCHEMA (CANON)

- SDT_ID:
- SR_ID:

Mapping:
- VISUAL:
  - where it shows (props, signage, costume, architecture)
- AUDIO:
  - motif timbre/rhythm placement rules
- DIALOGUE:
  - phrases, taboo words, ritual lines
- EDITING:
  - cut emphasis and reveal pacing
- PERFORMANCE:
  - gestures, posture, ritual behavior

Rule:
- At least one concrete directive for any symbol tagged “primary”.

---

## SYMBOL CLASSES (STANDARD)

- identity symbols (flags, crests)
- warning symbols (hazard marks)
- sacred symbols (ritual geometry)
- propaganda symbols (state imagery)
- taboo symbols (forbidden signs)
- memory symbols (graves, relics)
- tech symbols (interface glyphs)
- nature symbols (cycles, storms)

---

## INCONSISTENCY DETECTOR (HEURISTICS)

Flag if:
- symbol appears but has no meaning in registry
- symbol is used by wrong faction/culture without explanation
- symbol means opposite things without evolution rule
- overuse makes symbol cliché (frequency too high)
- multiple symbols collide visually and confuse identity
- symbol contradicts tone locks (cute icon in grim sacred scene)

Fix options:
- register symbol and define primary meaning
- create pack to constrain selection
- add placement rules and reduce frequency
- add evolution rule or remove contradictory use
- redesign to avoid collision (shape/color/sound)
- restrict scope or explain diffusion (trade, conquest)

---

## PROCEDURE (HOW TO RUN)

1) Import theme and tone locks
2) Draft symbol registry (SR) with explicit meanings + scopes
3) Build symbol packs (SP) for factions/locations/arcs
4) Define placement rules (PR) and frequency caps
5) Define evolution rules (ER) for planned meaning shifts
6) Translate primary symbols to departments (SDT)
7) Run anti-contradiction gates (ACG) on scenes/arts/audio
8) Canonize SR/SP and enforce usage via QC

---

## QC CHECKLIST (MANDATORY)

- SR exists and symbols have primary meanings + scopes?
- SP exists for major factions/locations/arcs?
- PR defines frequency + visibility?
- ER exists for any meaning shifts?
- SDT exists for primary symbols?
- ACG gates are defined and used?
- collision risks addressed?

---

## VALIDATION RULES

- SYV1: Symbols are explicit, scoped, and reusable.
- SYV2: Meaning shifts are governed and traceable.
- SYV3: Placement and frequency prevent cliché and spam.
- SYV4: Symbolism remains coherent across departments and outputs.

---

OWNER: Universe Engine
LOCK: FIXED
