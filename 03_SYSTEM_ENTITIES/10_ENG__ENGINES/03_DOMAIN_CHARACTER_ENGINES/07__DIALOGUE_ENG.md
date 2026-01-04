# Dialogue Engine
FILE: 07__DIALOGUE_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 03_DOMAIN_CHARACTER_ENGINES
CLASS: DOMAIN (L2)
LEVEL: L2
STATUS: ACTIVE
VERSION: 2.0
ROLE: Defines character dialogue as a tactical, psychological, and relational output; produces Dialogue Spec and Voice Rules ensuring consistent voice, subtext, intent, and conflict-driven speech patterns across scenes

---

## PURPOSE

Диалог — это действие, а не “текст”.
Движок нужен, чтобы:
- у каждого персонажа был узнаваемый голос
- реплики были тактикой (добиться цели)
- под-текст работал (что скрыто)
- диалог отражал ценности, страхи и отношения
- сцены говорили конфликтом, а не экспозицией

---

## NON-GOALS

- не пишет “идеальные реплики” без сцены (ему нужен контекст)
- не заменяет Speech Naturalization (это следующий движок)
- не заменяет монтаж/ритм (Editing engine)
Он задаёт **правила голоса и диалоговой тактики**.

---

## MINI-CONTRACT (MANDATORY)

### CONSUMES
- Behavior Spec (BS)
- Motivation Map (MM)
- Value Framework (VF)
- Psychology Profile (PP) (optional but strong)
- Relationship Map/Ledger (RM/RLSL)
- Scene Specs (SS) (recommended)

### PRODUCES
- DIALOGUE SPEC (DS) — canonical artifact
- VOICE RULES (lexicon, rhythm, syntax)
- SUBTEXT MAP (what is meant vs said)
- TACTICAL SPEECH PATTERNS
- CONFLICT DIALOGUE BEATS hooks

### DEPENDS_ON
- 03_DOMAIN_CHARACTER_ENGINES/05__CHARACTER_BEHAVIOR_ENG.md
- 03_DOMAIN_CHARACTER_ENGINES/06__RELATIONSHIP_ENG.md

### OUTPUT_TARGET
- Feeds:
  - 03_DOMAIN_CHARACTER_ENGINES/08__SPEECH_NATURALIZATION_ENG.md
  - Scene construction (dialogue beats)
  - Continuity (who knows what)
  - Production (voice casting, performance notes)

---

## CANON TERMS

### INTENT
Что персонаж хочет получить этой репликой.

### TACTIC (speech tactic)
Как он говорит, чтобы добиться цели:
- ask, accuse, threaten, charm, distract, test, shame, lie, confess

### SUBTEXT
Что он на самом деле имеет в виду/скрывает.

### VOICE
Узнаваемая “формула речи”:
- словарь
- ритм
- длина фраз
- уровень прямоты
- юмор/агрессия/формальность

---

## DIALOGUE PRINCIPLES (CORE)

1) People talk to get something (intent)
2) What matters is what is NOT said (subtext)
3) Dialogue changes relationship state (ledger)
4) Every scene has a speech power balance

---

## REQUIRED ARTIFACT: DIALOGUE SPEC (DS)

### DS SCHEMA (CANON)

Header:
- DS_ID:
- CHARACTER_ID:
- SCOPE:
- VERSION:
- STATUS:

Voice DNA:
- VOCAB LEVEL:
  - simple | normal | technical | poetic
- FORMALITY:
  - low | mid | high
- DIRECTNESS:
  - blunt | mixed | indirect
- TEMPO:
  - slow | medium | fast
- SENTENCE LENGTH:
  - short | mixed | long
- FAVORITE STRUCTURES:
  - questions | commands | stories | metaphors
- HUMOR MODE (optional):
  - none | dry | dark | playful | sarcastic
- SWEAR POLICY (optional):
  - never | rare | normal | heavy (if world allows)
- SIGNATURE WORDS/PHRASES (3–12):
- AVOIDED WORDS/TOPICS (optional):

Truth & Lies:
- TRUTH STYLE:
  - literal | evasive | strategic | performative
- LIE STYLE:
  - denial | misdirection | half-truth | charm-lie
- CONFESSION THRESHOLD:
  - when they finally tell truth

Speech Tactics Set (repeat):
- ST_ID:
- TACTIC NAME:
- WHEN USED (conditions):
  - stakes/opponent/relationship state
- WHAT IT ACHIEVES:
- HOW IT SOUNDS:
  - tone, structure
- COST:
  - relational/moral
- COUNTER:
  - what breaks it

Subtext Rules:
- WHAT THEY NEVER SAY OUT LOUD:
- WHAT LEAKS ANYWAY (tells in speech):
  - pauses, sarcasm, overexplaining
- TOP SUBTEXT THEMES (1–3):
  - control, abandonment, shame, etc.

Relationship-Driven Modifiers:
For each key pair:
- PAIR_ID:
- HOW VOICE CHANGES:
  - softer/harder/faster/more honest
- POWER POSTURE:
  - submit | equal | dominate | test
- TABOO TOPICS IN THIS PAIR:
- REPAIR LANGUAGE:
  - how they apologize/repair if they do

Scene Dialogue Beats (recommended):
For each key scene:
- SCENE_ID:
- GOAL (speech goal):
- OPPONENT GOAL:
- POWER BALANCE START:
- 3–7 BEATS:
  - beat -> tactic -> shift
- SUBTEXT LINE:
  - what the scene is “really about”
- OUTCOME:
  - who got what
- CONTINUITY UPDATES:
  - new knowledge / relationship axis change

---

## DIALOGUE RULES (CANON)

### D1 — Every line must have intent
Если реплика не делает ничего — выкинуть или заменить действием.

### D2 — Subtext must exist in conflict scenes
Особенно если тема — власть/ложь/стыд.
Без subtext сцена становится плоской.

### D3 — Voice is stable, context modifies it
Голос персонажа должен быть узнаваемым,
но отношения и стресс меняют:
- прямоту
- темп
- честность
(это через modifiers)

### D4 — Speech tactics have counters
Если тактика “всегда работает” — не диалог, а магия.

### D5 — Dialogue moves state
Хороший диалог меняет:
- knowledge registry
- relationship axes
- goal stack
Если ничего не поменялось → сцена лишняя.

### D6 — Exposition must be paid for
Если персонаж выдаёт инфу, должна быть причина:
- хвастовство
- манипуляция
- просьба помощи
- паника
Иначе выглядит как “инфодамп”.

---

## INCONSISTENCY DETECTOR (HEURISTICS)

Flag if:
- character voice changes randomly across scenes
- exposition with no intent/cost
- conflict scene has no subtext
- dialogue does not change state (no outcomes)
- tactics used contradict behavior spec without trigger/bridge

Fix options:
- lock Voice DNA and enforce constraints
- add intent to exposition (manipulation/need)
- add subtext line and beats
- force relationship/knowledge update
- add trigger override or rewrite tactic

---

## PROCEDURE (HOW TO RUN)

1) Read BS/MM/VF/PP + RM
2) Define Voice DNA (vocab, formality, directness, tempo)
3) Define truth/lie style and confession threshold
4) Build speech tactics set (5–12 tactics)
5) Add subtext rules (never-say + leaks)
6) Create relationship-driven modifiers
7) For key scenes: write dialogue beats + outcomes
8) Run QC detectors and lock

---

## QC CHECKLIST (MANDATORY)

- Voice DNA filled?
- truth/lie style defined?
- tactics set includes counters?
- subtext rules exist?
- relationship modifiers exist?
- key scenes have beats and outcomes?
- continuity updates declared?

---

## VALIDATION RULES

- DV1: DS complete with Voice DNA + tactics + subtext.
- DV2: Dialogue lines map to intent/tactics.
- DV3: Relationship/knowledge state changes are trackable.
- DV4: Exposition is motivated and paid for.

---

OWNER: Universe Engine
LOCK: FIXED
