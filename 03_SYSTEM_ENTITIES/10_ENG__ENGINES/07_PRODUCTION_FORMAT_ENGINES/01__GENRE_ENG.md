# Genre Engine
FILE: 01__GENRE_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 07_PRODUCTION_FORMAT_ENGINES
CLASS: PRODUCTION (L3)
LEVEL: L3
STATUS: ACTIVE
VERSION: 2.0
ROLE: Defines genre as an audience contract and production standard; produces Genre Bibles, Subgenre Constraints, Promise/Payoff matrices, and Cross-Department translation so narrative, style, pacing, stakes, and output formats remain aligned and reproducible

---

## PURPOSE

GENRE — это “контракт с аудиторией”:
- какие эмоции и опыт мы обещаем
- какие типовые сцены обязательны
- какие табу и ограничения действуют
- какой ритм, ставки, уровень реализма
- как выглядят и звучат истории этого жанра в нашем каноне

Движок нужен, чтобы:
- не дрейфовать между жанрами без причины
- управлять ожиданиями зрителя/читателя/игрока
- давать ясные правила для всех остальных движков
- обеспечивать воспроизводимость результата

---

## NON-GOALS

- не заменяет Tone & Mood (температура внутри жанра)
- не заменяет Story Structure (скелет истории)
- не заменяет Art Style (визуальная подача)
Он задаёт **рамку жанровых ожиданий и производственных норм**.

---

## MINI-CONTRACT (MANDATORY)

### CONSUMES
- Project/World goals
- Target audience + platform constraints
- Theme/Meaning targets
- Existing tone/style locks (if any)
- Format targets (book/series/game/shorts)

### PRODUCES
- GENRE BIBLE (GB) — canonical artifact
- SUBGENRE MATRIX (SMX)
- PROMISE / PAYOFF MATRIX (PPM)
- REQUIRED SCENE TYPES (RST)
- TABOOS & LIMITS (TL)
- CROSS-DEPT TRANSLATION (GDT)
- GENRE CONSISTENCY GATES (GCG)

### DEPENDS_ON
- 06_GENRE_STYLE_ENGINES/01__TONE_MOOD_ENG.md
- 02_DOMAIN_NARRATIVE_ENGINES/02__STORY_STRUCTURE_ENG.md
- 05_EXPRESSION_ENGINES (beats)
- 08_KNOWLEDGE_PRODUCTION_ENGINES (translation)

### OUTPUT_TARGET
- Feeds:
  - narrative beats and stakes selection
  - style engines (mood, atmosphere, symbolism)
  - production engines (camera, lighting, sound, editing)
  - format adaptation (book/series/shorts/game)

---

## CANON TERMS

### GENRE PROMISE
Обещание аудитории:
- “будет страшно”
- “будет загадка и разгадка”
- “будет рост героя”
- “будет жестокая правда”

### GENRE PAYOFF
Вознаграждение:
- победа/проигрыш
- разгадка/обман
- катарсис
- моральный выбор

### REQUIRED SCENES
Сцены, без которых жанр не читается:
- расследование, chase, ritual, duel, confession, etc.

### TABOO
Запрещено/ограничено в данном жанровом контракте:
- случайный юмор
- deus ex machina
- “слишком мило” в grim horror

---

## CORE RULES (CANON)

### G1 — Genre is a contract
Если обещали “mystery”, нельзя закончить без объяснения (или нужно пометить intentional subversion).

### G2 — Subgenre must be explicit
Если смешиваем:
- говорим какой жанр primary
- какой secondary
- и кто чем управляет (stakes, tone, pacing)

### G3 — Genre constrains everything
Жанр задаёт:
- stakes feel
- violence feel
- humor policy
- pacing range
- resolution type
И это должно быть переводимо в департаменты.

### G4 — Required scenes are mandatory (unless subverted intentionally)
Если ты убираешь обязательную сцену, ты обязан:
- дать альтернативу pay-off’а
- зафиксировать subversion

### G5 — No genre drift without governance
Жанр не меняется “сам”.
Сдвиг жанра = каноническое изменение → governance pipeline.

---

## REQUIRED ARTIFACT A: GENRE BIBLE (GB)

### GB SCHEMA (CANON)

Header:
- GB_ID:
- PROJECT_ID / WORLD_ID:
- SCOPE:
  - world | season | arc | project
- VERSION:
- STATUS:
  - draft | canon | deprecated

Definition:
- PRIMARY GENRE:
- SECONDARY GENRES (0–2):
- SUBGENRE TAGS (0–5):
- INTENDED EXPERIENCE (one sentence):
- REALISM LEVEL (0–10):
- SERIOUSNESS (0–10):
- HUMOR POLICY:
- VIOLENCE FEEL:
- HORROR/COMFORT RATIO (if applicable):
- MORAL FEEL:
  - clear | gray | nihilistic | sacred

Audience contract:
- PROMISES (3–7):
- PAYOFFS (3–7):
- WHAT MUST NEVER HAPPEN (taboos list):

Production impact:
- PACE RANGE:
  - slow | medium | fast (+ constraints)
- STAKES DEFAULT:
  - personal | relational | social | existential
- RESOLUTION TYPE:
  - closed | open | bittersweet | cyclical | tragic
- CLARITY FLOOR:
  - how confusing we allow it to be

Locks:
- NON-NEGOTIABLE GENRE TRAITS (3–7):
- ALLOWED VARIATIONS:
- FORBIDDEN DRIFTS:

Rule:
- GB must be readable in 2 minutes and still constrain the pipeline.

---

## REQUIRED ARTIFACT B: SUBGENRE MATRIX (SMX)

### SMX SCHEMA (CANON)

- SMX_ID:
- GB_ID:

Entries (repeat):
- SUBGENRE:
- WHAT IT ADDS:
  - tone, stakes, scene types, visuals
- WHAT IT RESTRICTS:
- DOMINANCE:
  - primary | secondary
- CONFLICT RISKS:
  - where it can break the main contract
- RESOLUTION IMPLICATION:
  - what endings are acceptable

Rule:
- Matrix prevents accidental mixing chaos.

---

## REQUIRED ARTIFACT C: PROMISE / PAYOFF MATRIX (PPM)

### PPM SCHEMA (CANON)

- PPM_ID:
- GB_ID:

Pairs (repeat):
- PROMISE:
- HOW WE SET IT UP:
- EXPECTED PAYOFF:
- PAYOFF MODES:
  - reveal, victory, sacrifice, twist, catharsis
- MINIMUM PAYOFF REQUIREMENT:
- SUBVERSION ALLOWED? (yes/no)
- IF SUBVERTED:
  - alternate satisfaction plan

Rule:
- Every promise must have a payoff path (or explicit subversion plan).

---

## REQUIRED ARTIFACT D: REQUIRED SCENE TYPES (RST)

### RST SCHEMA (CANON)

- RST_ID:
- GB_ID:

Scene types (repeat):
- SCENE TYPE:
- PURPOSE:
- FREQUENCY:
  - once, recurring, per episode
- TONE LIMITS:
- VISUAL/AUDIO IMPLICATIONS:
- COMMON FAILURES:

Rule:
- Include at least 5 scene types for primary genre (unless minimalist).

---

## REQUIRED ARTIFACT E: TABOOS & LIMITS (TL)

### TL SCHEMA (CANON)

- TL_ID:
- GB_ID:

Taboos (repeat):
- TABOO:
- WHY IT BREAKS CONTRACT:
- EXCEPTIONS (if any):
- FIX if happened:
  - rewrite or mark subversion

Limits:
- MAX CONFUSION:
- MAX HUMOR IN TRAGEDY:
- MAX VIOLENCE SHOWN:
- MAX “POWER SPIKE” WITHOUT COST:

Rule:
- Taboos list must exist; otherwise genre is unconstrained.

---

## REQUIRED ARTIFACT F: CROSS-DEPT TRANSLATION (GDT)

### GDT SCHEMA (CANON)

- GDT_ID:
- GB_ID:

Mapping:
- TO TONE/MOOD:
  - temperature and seriousness constraints
- TO ATMOSPHERE:
  - density and threat proximity defaults
- TO CAMERA:
  - movement feel, lens feel, distance rules
- TO LIGHTING:
  - contrast and motivated sources style
- TO EDITING:
  - rhythm mode and clarity rules
- TO SOUND:
  - ambience density and music role
- TO PERFORMANCE:
  - acting energy and speech tempo
- TO WRITING:
  - diction and exposition policy

Rule:
- At least one concrete directive per department.

---

## REQUIRED ARTIFACT G: GENRE CONSISTENCY GATES (GCG)

### GCG SCHEMA (CANON)

- GCG_ID:
- GB_ID:

Gates:
1) Promise gate:
   - promises present and reinforced
2) Payoff gate:
   - payoffs delivered or subverted intentionally
3) Required scenes gate:
   - core scene types appear as expected
4) Taboo gate:
   - no forbidden drifts
5) Pacing gate:
   - pace within allowed range
6) Tone gate:
   - tone aligns with GB + TB
7) Resolution gate:
   - ending type consistent with contract

Rule:
- Fail 2+ gates → output is non-canon until corrected.

---

## STANDARD GENRE “MODES” (OPTIONAL TEMPLATES)

### Mystery mode
- promise: answers
- payoff: reveal + coherence
- taboo: no random solution without setup

### Horror mode
- promise: fear/unease
- payoff: survive/understand/cost
- taboo: comfort dominates too early

### Epic mode
- promise: scale and stakes
- payoff: sacrifice and transformation
- taboo: small trivial endings

### Satire mode
- promise: critique via humor
- payoff: insight and sting
- taboo: moral confusion without intent

---

## INCONSISTENCY DETECTOR (HEURISTICS)

Flag if:
- promises appear but no payoff path exists
- required scene types never happen
- tone drifts outside genre seriousness
- resolution type contradicts contract
- taboo events occur (deus ex, random twist, cute break)
- subgenre elements dominate without being declared

Fix options:
- update GB and SMX and rerun mapping
- add missing required scenes or alternate payoff beats
- mark intentional subversion and add satisfaction plan
- apply governance pipeline for permanent genre shift

---

## PROCEDURE (HOW TO RUN)

1) Pick primary genre and 0–2 secondary genres
2) Draft GB (contract, locks, resolution)
3) Build SMX (subgenres and risks)
4) Build PPM (promise→payoff)
5) Build RST (required scene types)
6) Build TL (taboos and limits)
7) Translate to departments via GDT
8) Apply gates (GCG) to episodes/scenes/artifacts
9) Canonize GB and enforce drift logging

---

## QC CHECKLIST (MANDATORY)

- GB defines promises, payoffs, locks, taboos?
- SMX controls subgenre mixing?
- PPM pairs each promise with payoff path?
- RST lists required scenes with frequency?
- TL caps confusion/humor/violence/power spikes?
- GDT translates genre rules into production and writing?
- GCG gates exist and are used?

---

## VALIDATION RULES

- GV1: Genre contract is explicit and enforceable.
- GV2: Promises have payoffs (or intentional subversions with replacements).
- GV3: Required scenes and taboos keep identity stable.
- GV4: Cross-department translation keeps outputs coherent.

---

OWNER: Universe Engine
LOCK: FIXED
