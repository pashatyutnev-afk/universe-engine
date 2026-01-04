# Atmosphere Engine
FILE: 02__ATMOSPHERE_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 06_GENRE_STYLE_ENGINES
CLASS: STYLE (L3)
LEVEL: L3
STATUS: ACTIVE
VERSION: 2.0
ROLE: Defines the atmosphere layer as a reproducible “presence system” (air, texture, ambient life, micro-risks, sensory density, and environmental storytelling); produces Atmosphere Bibles, Scene Atmosphere Profiles, Sensory Budgets, and Consistency Gates to keep the world feeling alive and coherent

---

## PURPOSE

ATMOSPHERE — это “воздух мира”.
Она отвечает за:
- ощущение пространства и присутствия
- плотность деталей
- микрожизнь (звуки, движения, мелкие события)
- ощущение угрозы/безопасности
- “environmental storytelling” (история через среду)

Движок нужен, чтобы:
- мир не был пустой декорацией
- сцены не выглядели одинаково “стерильно”
- атмосфера была воспроизводима (не случайная)
- атмосфера усиливала тон и смысл, а не спорила

---

## NON-GOALS

- не заменяет Environment & Ecology (физика/экология мира)
- не заменяет Lighting/Art Style (рендер и свет)
- не заменяет Sound engine (продакшн-аудио)
Он фиксирует **атмосферные параметры**, которые потом переводятся в визуал/звук/текст.

---

## MINI-CONTRACT (MANDATORY)

### CONSUMES
- Tone Bible (TB) + Mood Curve (MC)
- World constraints (climate/tech/culture)
- Location specs (if any)
- Threat model (hazards, conflict proximity)
- Format constraints (shot length, scene duration)

### PRODUCES
- ATMOSPHERE BIBLE (AB) — canonical artifact
- SCENE ATMOSPHERE PROFILE (SAP)
- SENSORY BUDGET (SBG)
- AMBIENT LIFE PACK (ALP)
- ENVIRONMENTAL STORY CUES (ESC)
- CONSISTENCY GATES (AG)

### DEPENDS_ON
- 06_GENRE_STYLE_ENGINES/01__TONE_MOOD_ENG.md
- 04_DOMAIN_WORLD_ENGINES/10__ENVIRONMENT_ECOLOGY_ENG.md (constraints)
- 08_KNOWLEDGE_PRODUCTION_ENGINES/08__SOUND_MUSIC_ENG.md (translation)

### OUTPUT_TARGET
- Feeds:
  - scene writing (sensory detail)
  - sound palette and ambience layers
  - visual set dressing and micro-motion notes
  - prompt packs for image/video generation

---

## CANON TERMS

### SENSORY DENSITY
Сколько ощущений/сигналов в единицу времени:
- низкая (пустота)
- средняя (нормальная жизнь)
- высокая (перегруз, рынок, война)

### AMBIENT LIFE
Фоновая жизнь:
- люди, звери, механизмы, вода, ветер, реклама, молитвы

### MICRO-RISK
Мелкая опасность:
- скользко, яд в воздухе, патруль рядом, напряжение толпы

### ENVIRONMENTAL STORY CUE
Сигнал истории в среде:
- следы пожара, заколоченные окна, свежая кровь, новые плакаты

### ATMOSPHERE LOCK
Набор параметров, которые нельзя нарушать без отметки.

---

## ATMOSPHERE RULES (CANON)

### A1 — Atmosphere must serve tone, not fight it
Если тон “холодный ужас”, атмосфера не должна быть “уютная сказка”.

### A2 — Atmosphere must be reproducible
Должен существовать AB + SAP + бюджеты, иначе “оно просто так чувствуется”.

### A3 — Sensory budget prevents overload
Слишком много деталей = шум.
Бюджет ограничивает плотность, чтобы смысл читался.

### A4 — Atmosphere is local, but bounded globally
У каждой локации свой профиль, но в рамках общих мировых правил.

### A5 — Micro-risks make world feel real
Даже в “мирной” сцене может быть микро-риск (социальный/средовой).

---

## REQUIRED ARTIFACT A: ATMOSPHERE BIBLE (AB)

### AB SCHEMA (CANON)

Header:
- AB_ID:
- PROJECT_ID / WORLD_ID:
- SCOPE:
  - world | season | arc
- VERSION:
- STATUS:
  - draft | canon | deprecated

Global atmosphere:
- AIR FEEL:
  - clean | dusty | humid | icy | smoky | sacred | sterile
- TEXTURE FEEL:
  - smooth | gritty | worn | decayed | lush
- AMBIENCE DENSITY:
  - low | mid | high
- MICRO-MOTION LEVEL:
  - still | subtle | constant
- THREAT PROXIMITY DEFAULT:
  - safe | uneasy | dangerous
- SOCIAL TEMPERATURE:
  - warm | neutral | hostile | paranoid
- TECHNO-AURA (if any):
  - silent | humming | noisy | glitchy

Locks:
- NON-NEGOTIABLE ATMOSPHERE TRAITS (3–7):
- FORBIDDEN FEELS:
- ALLOWED VARIATIONS:

---

## REQUIRED ARTIFACT B: SCENE ATMOSPHERE PROFILE (SAP)

### SAP SCHEMA (CANON)

- SAP_ID:
- AB_ID:
- SCENE_ID:
- LOCATION_ID:

Profile:
- SENSORY DENSITY (0–10):
- AIR FEEL:
- SOUND BED TYPE:
  - quiet | city hum | market | industrial | nature | ritual
- MICRO-MOTION:
  - none | subtle | active
- THREAT PROXIMITY:
  - safe | uneasy | imminent
- VISIBILITY:
  - clear | fog | dust | darkness | glare
- SOCIAL SIGNAL:
  - friendly | watching | hostile | indifferent
- MICRO-RISKS (1–3):
- ATMOSPHERE STORY CUES (1–5):
- “ONE ANCHOR DETAIL”:
  - 1 деталь, которая делает сцену узнаваемой

Rule:
- Every key scene must have one anchor detail and at least one story cue.

---

## REQUIRED ARTIFACT C: SENSORY BUDGET (SBG)

### SBG SCHEMA (CANON)

- SBG_ID:
- AB_ID:
- SCOPE:
  - per scene | per episode

Budget:
- MAX NEW SENSORY ELEMENTS PER MINUTE:
- MAX STORY CUES PER SCENE:
- MAX AMBIENT SOUND LAYERS (design-level):
- MAX MICRO-RISKS:
- SILENCE / EMPTY SPACE QUOTA:
  - how much “air” we allow

Rule:
- Budget must include an “empty space” quota, иначе сцены будут перегружены.

---

## REQUIRED ARTIFACT D: AMBIENT LIFE PACK (ALP)

### ALP SCHEMA (CANON)

- ALP_ID:
- AB_ID:
- LOCATION TYPE:
  - street | market | forest | ship | station | ruin | temple

Elements (repeat):
- ELEMENT:
- CATEGORY:
  - human | animal | machine | weather | ritual | traffic | signage
- FREQUENCY:
  - rare | occasional | constant
- SOUND SIGNATURE:
- VISUAL SIGNATURE:
- STORY UTILITY:
  - tension, comfort, worldbuilding

Rule:
- Each location type must have at least 5 ambient life elements.

---

## REQUIRED ARTIFACT E: ENVIRONMENTAL STORY CUES (ESC)

### ESC SCHEMA (CANON)

- ESC_ID:
- AB_ID:

Cues (repeat):
- CUE:
- WHAT IT IMPLIES:
- TIME DEPTH:
  - fresh | recent | old
- WHO WOULD NOTICE:
- HOW IT CONNECTS TO CANON:
  - event/war/ritual/poverty

Rule:
- At least 10 cues for a world/season AB.

---

## CONSISTENCY GATES (AG)

### AG SCHEMA (CANON)

- AG_ID:
- AB_ID:

Gates:
1) Tone alignment:
   - atmosphere traits match Tone Bible locks
2) Density control:
   - sensory budget respected
3) Location signature:
   - each location has unique anchor detail
4) Micro-risk realism:
   - micro-risks plausible for place/time
5) Story cues:
   - cues imply something concrete (not generic “it’s old”)
6) Drift detection:
   - if atmosphere becomes sterile/empty/overloaded unexpectedly

Rule:
- Fail 2+ gates → scene/art is non-canon until corrected.

---

## ATMOSPHERE PATTERNS (STANDARD)

### Pattern 1: Oppressive air
- high threat proximity + low visibility + constant hum

### Pattern 2: False safety
- warm ambient life + subtle micro-risk cues

### Pattern 3: Sacred stillness
- low sensory density + high meaning cues + silence policy

### Pattern 4: Market overload
- high density + strict budget + one anchor detail to keep clarity

---

## INCONSISTENCY DETECTOR (HEURISTICS)

Flag if:
- scenes feel “samey” despite different locations
- atmosphere contradicts tone (cozy when dread is required)
- too many cues create noise and reduce clarity
- no micro-motion (world feels dead) where life should exist
- micro-risks are constant and exhausting (no breath)
- cues do not imply anything actionable

Fix options:
- enforce SBG limits and add empty space
- require anchor detail per scene
- adjust threat proximity and social temperature
- create ALP for location type
- rewrite cues to imply concrete history
- add controlled micro-motion (flags, dust, distant voices)

---

## PROCEDURE (HOW TO RUN)

1) Import tone locks (TB) and world constraints
2) Write AB (global atmosphere + locks)
3) For each scene: create SAP (anchor + cues + micro-risk)
4) Set SBG (density caps + empty space)
5) Build ALP per location type
6) Build ESC list for world/season
7) Run gates (AG) on scenes and artifacts
8) Canonize AB and enforce drift logging

---

## QC CHECKLIST (MANDATORY)

- AB has global traits + non-negotiables?
- each key scene has SAP with anchor detail + story cues?
- SBG limits density and includes empty space?
- ALP exists per location type?
- ESC cues are concrete and imply history?
- AG gates defined and used?
- drift detection policy exists?

---

## VALIDATION RULES

- AV1: Atmosphere is reproducible via AB/SAP/SBG.
- AV2: Locations feel alive through ambient life and micro-motion.
- AV3: Sensory density is controlled; clarity preserved.
- AV4: Story cues embed history and consequences into the environment.

---

OWNER: Universe Engine
LOCK: FIXED
