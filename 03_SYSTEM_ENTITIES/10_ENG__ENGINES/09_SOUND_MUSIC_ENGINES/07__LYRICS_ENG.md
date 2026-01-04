# Lyrics Engine
FILE: 07__LYRICS_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 09_SOUND_MUSIC_ENGINES
CLASS: PRODUCTION (L3)
LEVEL: L3
STATUS: ACTIVE
VERSION: 1.0
ROLE: Defines reproducible lyric writing logic (meaning, narrative, imagery, hook lines, voice/persona, constraints compliance) for songs and cues; produces Lyric Specs, Hook Line Briefs, Section Meaning Maps, Imagery Banks, Do/Don't lists, and QC Gates aligned with rhyme/meter, melody, structure, and universe canon

---

## PURPOSE

Текст песни — это “смысл + голос + образ”.
Движок фиксирует:
- о чём песня (core meaning)
- как строится история/мысль по секциям
- как формируется хук-линия (главная фраза)
- как держать консистентный голос/персонажа
- как не ломать канон мира
- как писать под ограничения рифмы/метра/мелодии

---

## NON-GOALS

- не задаёт рифму/слоговку (это 06)
- не задаёт мелодию (это 04)
- не задаёт гармонию/грув (03/05)
Он создаёт **семантическую архитектуру текста** и “чистый” хук.

---

## MINI-CONTRACT (MANDATORY)

### CONSUMES
- Composition Spec (09.01): purpose, emotion target, theme/motif intent
- Song Structure Spec (09.02): section jobs & payoff cadence
- Rhyme/Meter Spec (09.06): constraints for fit
- Melody Spec (09.04): hook placement + phrasing
- Universe canon constraints (world/character tone)
- Target audience + language

### PRODUCES
- LYRIC SPEC (LS) — canonical artifact
- SECTION MEANING MAP (SMM)
- HOOK LINE BRIEF (HLB)
- IMAGERY BANK (IB)
- VOICE/PERSONA LOCK (VPL)
- CANON COMPLIANCE NOTES (CCN)
- LYRICS QC GATES (LQG)

### DEPENDS_ON
- 09.06 Rhyme/Meter (formal fit)
- 09.04 Melody/Hook (hook line slots)
- 09.02 Song Structure (section meaning roles)
- 06 Genre/Style engines (tone/mood)
- 02 Narrative engines (theme/meaning alignment, if used)

### OUTPUT_TARGET
- Feeds:
  - vocal performance direction (09)
  - music-to-scene alignment (12)
  - style consistency checks (11)

---

## CANON TERMS

### CORE MEANING
Одна фраза: “в чём смысл песни”.

### HOOK LINE
Главная строка/фраза, которую запоминают.

### VOICE/PERSONA
Кто говорит и как (лексика, честность, дистанция).

### IMAGERY
Образы: конкретика вместо абстракции.

### SECTION MEANING ROLE
Функция смысла секции:
- setup | detail | turn | payoff | reflection | resolution

### CANON COMPLIANCE
Текст не должен ломать законы мира/персонажа.

---

## CORE RULES (CANON)

### L1 — One core meaning
Только один центральный смысл.
Если два — это две песни.

### L2 — Hook line is simple and repeatable
Хук обязан быть:
- короткий
- произносимый
- понятный
- “цитируемый”
Сложные метафоры — в куплет, не в хук.

### L3 — Section meaning roles are explicit
Каждая секция знает свою функцию смысла (SMM).

### L4 — Concrete imagery beats abstract statements
“Я одинок” → плохо.
“Телефон молчит третью ночь” → хорошо.
IB обязателен.

### L5 — Persona consistency
VPL фиксирует язык:
- слэнг/формальность
- степень “уязвимости”
- точка зрения

### L6 — Fit is mandatory
LS обязан уважать RMS:
- слоги/ударения/дыхание/рифма

### L7 — Canon compliance
Если проект — часть вселенной:
- CCN обязателен
- запреты/термины мира соблюдаются

---

## REQUIRED ARTIFACT A: LYRIC SPEC (LS)

### LS SCHEMA (CANON)

Header:
- LS_ID:
- CS_ID:
- SSS_ID:
- RMS_ID:
- MS_ID (optional reference):
- LANGUAGE:
- GENRE/STYLE LOCK:
- VERSION:
- STATUS:
  - draft | canon | deprecated

Core:
- CORE MEANING (one sentence):
- THEME TAGS (3–7):
- EMOTION TARGET:
- POV:
  - 1st | 2nd | 3rd
- TIMEFRAME:
  - now | past | timeless
- SETTING (if any):
- “WHAT MUST BE SAID” (1–3 bullets):
- “WHAT MUST NOT BE SAID” (taboos/canon bans):

Hook:
- HOOK LINE BRIEF (HLB ref)
- HOOK WORDS (3–7):
- HOOK CLARITY RULE:
  - no complex metaphors, no tongue-twisters

Voice:
- VOICE/PERSONA LOCK (VPL ref)

Imagery:
- IMAGERY BANK (IB ref)

Canon:
- CANON COMPLIANCE NOTES (CCN ref)

Rule:
- LS is the “law” for lyric writing under constraints.

---

## REQUIRED ARTIFACT B: SECTION MEANING MAP (SMM)

### SMM SCHEMA (CANON)

For each section:
- SECTION ID (V1/C1/B...):
- MEANING ROLE:
  - setup | detail | turn | payoff | reflection | resolution
- MESSAGE (one line):
- IMAGERY ANCHOR (from IB):
- EMOTIONAL INTENSITY (0–10):
- HOOK RELATION:
  - supports | contrasts | foreshadows | pays off
- “DO NOT” (avoid topics/phrases)

Rule:
- SMM prevents “куплеты ни о чём”.

---

## REQUIRED ARTIFACT C: HOOK LINE BRIEF (HLB)

### HLB SCHEMA (CANON)

- HLB_ID:
- LS_ID:

Hook line target:
- PRIMARY HOOK LINE (candidate):
- ALT HOOK LINES (1–3):
- HOOK FUNCTION:
  - anthem | confession | threat | vow | question | mantra
- HOOK WORDS (must-include):
- HOOK TONE:
  - bitter | hopeful | cold | warm | ecstatic | calm
- PHONETIC NOTES (language specific):
  - open vowels for long notes, avoid hard clusters
- “NO CHEAT” RULE:
  - hook must be identical or recognizably same on repeats

Rule:
- HLB must match HM (melody hook map) slots.

---

## REQUIRED ARTIFACT D: IMAGERY BANK (IB)

### IB SCHEMA (CANON)

- IB_ID:
- STYLE_ID / PROJECT_ID:

Buckets:
- OBJECTS (things):
- PLACES:
- WEATHER/LIGHT:
- BODY/SENSATIONS:
- TECHNOLOGY (if any):
- SYMBOLS (style-approved):

Rules:
- “CONCRETE FIRST”:
  - prefer specific nouns/verbs
- “MAX ABSTRACT WORDS”:
  - limit per section type (optional)
- “BANNED CLICHÉS”:
  - list of clichés not allowed

Rule:
- IB provides reusable world-consistent imagery.

---

## REQUIRED ARTIFACT E: VOICE/PERSONA LOCK (VPL)

### VPL SCHEMA (CANON)

- VPL_ID:
- LS_ID:

Persona:
- WHO IS SPEAKING:
- DISTANCE:
  - intimate | neutral | distant
- LANGUAGE REGISTER:
  - street | neutral | poetic | formal
- VULNERABILITY:
  - low | med | high
- HUMOR:
  - none | dry | playful
- LEXICON RULES:
  - allowed words / banned words
- LINE LENGTH FEEL:
  - short punchy | flowing | mixed

Rule:
- VPL prevents “каждый куплет разным человеком”.

---

## REQUIRED ARTIFACT F: CANON COMPLIANCE NOTES (CCN)

### CCN SCHEMA (CANON)

- CCN_ID:
- PROJECT_ID:

Canon locks:
- WORLD TERMS ALLOWED:
- WORLD TERMS FORBIDDEN:
- CHARACTER FACTS LOCKS (if applicable):
- TECHNOLOGY/MAGIC TERMS POLICY:
- “NO CONTRADICTION” CHECKS:
  - list of canon rules to verify

Rule:
- CCN ensures lyrics don’t break the universe.

---

## REQUIRED ARTIFACT G: LYRICS QC GATES (LQG)

### LQG SCHEMA (CANON)

Gates:
1) Core meaning gate:
   - single clear message exists
2) Hook clarity gate:
   - hook line is short, quotable, repeatable
3) Section meaning gate:
   - SMM roles make sense; no filler
4) Imagery gate:
   - concrete imagery present; low abstraction
5) Persona gate:
   - VPL consistent across sections
6) Fit gate:
   - respects RMS constraints (syllables/stress/breath)
7) Canon gate:
   - CCN passes; no contradictions
8) Reproducibility gate:
   - LS artifacts allow rewriting by another writer

Rule:
- Fail 2+ gates → rewrite LS/HLB/SMM.

---

## INCONSISTENCY DETECTOR (HEURISTICS)

Flag if:
- chorus repeats but meaning doesn’t pay off
- verses repeat the same idea without new detail
- hook line is too long or full of consonant clusters
- imagery is generic (“всё было как в кино”)
- persona drifts (сленг → поэзия → канцелярит)
- text violates canon terms/rules
- fit forces awkward word stress

Fix options:
- rewrite core meaning into one sentence
- move complex metaphor to verse; simplify hook
- add concrete objects/time/place details from IB
- lock persona and vocabulary
- run CCN checklist; replace forbidden terms
- adjust phrasing to match stress map (06)

---

## PROCEDURE (HOW TO RUN)

1) Read CS purpose + SSS section jobs + RMS constraints
2) Write core meaning (one sentence) and theme tags
3) Choose POV and persona; lock VPL
4) Draft hook line candidates; finalize HLB
5) Build SMM section-by-section (message + imagery anchor)
6) Build IB (or choose from project IB) and assign imagery anchors
7) Add CCN if universe-bound
8) Draft lyrics inside RMS constraints
9) Run LQG gates and iterate

---

## QC CHECKLIST (MANDATORY)

- one core meaning?
- hook line short/quotable and matches hook slots?
- section meaning map prevents filler?
- imagery concrete and varied?
- persona consistent?
- fit passes syllable/stress/breath?
- canon compliance passes?
- reproducible artifacts exist?

---

## VALIDATION RULES

- LV1: Lyrics communicate one clear meaning and emotional target.
- LV2: Hook line is repeatable, quotable, and paid as designed.
- LV3: Section meaning map creates progression (no filler).
- LV4: Imagery is concrete, style-consistent, and memorable.
- LV5: Persona remains consistent and intentional.
- LV6: Lyrics fit rhyme/meter constraints and melody phrasing.
- LV7: Canon compliance holds when universe-bound.
- LV8: Spec is reproducible.

---

OWNER: Universe Engine
LOCK: FIXED
