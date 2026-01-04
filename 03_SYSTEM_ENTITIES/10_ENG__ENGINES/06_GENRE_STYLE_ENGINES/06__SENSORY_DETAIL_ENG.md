# Sensory Detail Engine
FILE: 06__SENSORY_DETAIL_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 06_GENRE_STYLE_ENGINES
CLASS: STYLE (L3)
LEVEL: L3
STATUS: ACTIVE
VERSION: 2.0
ROLE: Governs sensory detail as a controlled, reproducible system (sight/sound/smell/touch/taste/temperature/space) with budgets, priority stacks, and tone alignment; produces Sensory Profiles, Detail Packs, Readability Gates, and Anti-Overload rules that keep scenes vivid, coherent, and scalable across text, visuals, and audio

---

## PURPOSE

Сенсорные детали — это “тактильность мира”:
- как пахнет, звучит, ощущается поверхность
- какая температура воздуха
- какой шум фона
- какая плотность пространства

Движок нужен, чтобы:
- детали не были случайными и не спорили с тоном
- сцены не превращались в перегруз
- детали были воспроизводимы (можно повторять стиль)
- детали масштабировались в визуал/звук/промпты

---

## NON-GOALS

- не заменяет Atmosphere Engine (там — воздух мира как слой)
- не заменяет Sound engine (там — продакшн-логика микса)
- не заменяет Art Style (визуальные материалы/рендер)
Этот движок управляет **выбором и дозировкой деталей**.

---

## MINI-CONTRACT (MANDATORY)

### CONSUMES
- Tone Bible + Mood Curve
- Atmosphere Bible + Scene Atmosphere Profiles
- World constraints (materials, tech, ecology)
- Scene goal and primary read (composition)
- Format constraints (word count / shot duration)

### PRODUCES
- SENSORY PROFILE (SP) — per world/arc
- SCENE DETAIL STACK (SDS) — per scene
- DETAIL PACKS (DP) — reusable libraries
- SENSORY BUDGET (SB) — caps and quotas
- READABILITY & CLARITY GATES (RCG)
- CROSS-MEDIA TRANSLATION (CMT) — text→visual→audio

### DEPENDS_ON
- 06_GENRE_STYLE_ENGINES/01__TONE_MOOD_ENG.md
- 06_GENRE_STYLE_ENGINES/02__ATMOSPHERE_ENG.md
- 08_KNOWLEDGE_PRODUCTION_ENGINES (translation)

### OUTPUT_TARGET
- Feeds:
  - writing scene descriptions
  - prop/material notes for visuals
  - ambience and foley targets for audio
  - prompt packs for generation

---

## CANON TERMS

### SENSORY CHANNELS
- sight, sound, smell, touch, taste, temperature, spatial feel

### DETAIL STACK
Иерархия деталей:
- Primary (якорит сцену)
- Secondary (усиливает)
- Tertiary (микро-реализм)

### BUDGET
Лимит на новые детали, чтобы не утонуть в шуме.

### SIGNATURE DETAIL
Одна деталь, которая делает сцену “уникальной”.

### “SENSE-TO-MEANING”
Каждая деталь должна:
- либо усиливать смысл/тон
- либо повышать правдоподобие
Иначе это мусор.

---

## CORE RULES (CANON)

### SD1 — Details must serve meaning or realism
Если деталь не:
- усиливает смысл
- или не добавляет правдоподобие
→ убрать.

### SD2 — One signature detail per key scene
Чтобы сцены не “сливались”, у каждой ключевой сцены:
- минимум 1 signature detail.

### SD3 — Respect the sensory budget
Нельзя постоянно добавлять новые ощущения.
Бюджет обязателен.

### SD4 — Channel balance
Нельзя всё время работать только “картинкой”.
Должно быть распределение по каналам.

### SD5 — Tone alignment
Детали обязаны соответствовать тону:
- “стерильный ужас” ≠ “уютный запах выпечки”.

---

## REQUIRED ARTIFACT A: SENSORY PROFILE (SP)

### SP SCHEMA (CANON)

Header:
- SP_ID:
- PROJECT_ID / WORLD_ID:
- SCOPE:
  - world | season | arc
- VERSION:
- STATUS:
  - draft | canon | deprecated

Profile:
- DOMINANT CHANNELS (2–3):
  - which senses carry the world
- SECONDARY CHANNELS (1–3):
- AVOIDED CHANNELS (optional):
- TEXTURE POLICY:
  - clean | gritty | organic | industrial
- TEMPERATURE FEEL:
  - cold | neutral | hot | mixed
- SOUND TEXTURE FEEL:
  - quiet | hum | roar | ritual | mechanical
- SMELL WORLD NOTE:
  - baseline smell vibe (dust, oil, salt, incense)
- “DETAIL TONE FILTER”:
  - allowed adjectives and forbidden adjectives (list)

Rule:
- SP defines “default sensory palette” of the universe.

---

## REQUIRED ARTIFACT B: SCENE DETAIL STACK (SDS)

### SDS SCHEMA (CANON)

- SDS_ID:
- SP_ID:
- SCENE_ID:
- LOCATION_ID (optional)

Stack:
- SIGNATURE DETAIL (1):
- PRIMARY DETAILS (1–3):
- SECONDARY DETAILS (2–5):
- TERTIARY MICRO DETAILS (0–3):

For each detail:
- CHANNEL:
- DETAIL:
- PURPOSE:
  - meaning | realism | foreshadow | tension | comfort
- TONE TAG:
  - dread | awe | warmth | sterile | etc
- VISIBILITY/NOTICE:
  - obvious | subtle | background

Rule:
- If no signature detail exists → scene is “flat” by definition.

---

## REQUIRED ARTIFACT C: DETAIL PACKS (DP)

### DP SCHEMA (CANON)

- DP_ID:
- SP_ID:
- PACK TYPE:
  - location | faction | technology | nature | ritual
- TONE COMPATIBILITY:
- DOMINANT CHANNELS:

Entries (repeat):
- DETAIL:
- CHANNEL:
- TAGS:
- “WHEN TO USE”:
- “WHEN NOT TO USE”:

Rule:
- Packs enable reuse without repetition fatigue.

---

## REQUIRED ARTIFACT D: SENSORY BUDGET (SB)

### SB SCHEMA (CANON)

- SB_ID:
- SP_ID:
- SCOPE:
  - scene | episode | chapter

Budget:
- MAX NEW DETAILS PER SCENE:
- MAX NEW SMELLS PER EPISODE:
- MAX NEW SOUND SIGNATURES PER EPISODE:
- MAX TEXTURE DESCRIPTORS PER PARAGRAPH (text-mode):
- “EMPTY AIR QUOTA”:
  - required minimalism moments

Rule:
- Budget includes empty air. Always.

---

## REQUIRED ARTIFACT E: READABILITY & CLARITY GATES (RCG)

### RCG SCHEMA (CANON)

- RCG_ID:
- SP_ID:

Gates:
1) Primary read preserved:
   - details do not hide the main action/meaning
2) Budget respected:
   - caps not exceeded
3) Tone alignment:
   - details pass tone filter
4) Channel balance:
   - not 90% visual-only
5) Uniqueness:
   - signature detail exists and is not reused too often
6) Concrete-ness:
   - details are specific (not “приятно пахло” without source)

Rule:
- Fail 2+ gates → rewrite detail stack.

---

## REQUIRED ARTIFACT F: CROSS-MEDIA TRANSLATION (CMT)

### CMT SCHEMA (CANON)

- CMT_ID:
- SP_ID:

Translation rules:
- TEXT → VISUAL:
  - what becomes props/materials/lighting cues
- TEXT → AUDIO:
  - what becomes ambience/foley signatures
- VISUAL → TEXT:
  - how to describe without overload
- AUDIO → EDITING:
  - where to let sound carry instead of words

Rule:
- At least 1 translation rule for dominant channels.

---

## STANDARD DETAIL PATTERNS

### Pattern 1: “One sharp detail”
- 1 signature detail + minimal secondary = strong presence

### Pattern 2: “Layered realism”
- micro details that imply history (scratches, soot, worn handles)

### Pattern 3: “Sensory contrast”
- warm smell in cold scene (only if tone allows) to create tension

### Pattern 4: “Audio carries the room”
- text minimal, sound bed heavy (for film/video outputs)

---

## INCONSISTENCY DETECTOR (HEURISTICS)

Flag if:
- scenes have no signature detail (generic)
- too many adjectives and no concrete sources
- details contradict tone filter
- channel imbalance (only visuals, no sound/touch/space)
- repeated same signature detail across scenes (stale)
- budget constantly exceeded (overwritten prose)

Fix options:
- add one signature detail with purpose tag
- convert adjectives into concrete sources (oil, incense, wet stone)
- enforce budget and add empty air quotas
- redistribute across channels (sound, touch, temperature)
- rotate detail packs and enforce reuse rules

---

## PROCEDURE (HOW TO RUN)

1) Import TB + AB + world constraints
2) Create SP (dominant channels + tone filter)
3) Build DP libraries per location/faction/tech
4) For each scene: create SDS (signature + stack)
5) Apply SB caps and empty-air quotas
6) Run RCG gates
7) Translate via CMT for production (visual/audio/edit)
8) Canonize SP and DP; enforce SDS per key scene

---

## QC CHECKLIST (MANDATORY)

- SP defines dominant channels and tone filter?
- DP exists for main location/faction/tech?
- each key scene has SDS with signature detail?
- SB caps exist + empty air quota?
- RCG gates used?
- CMT translation rules exist?

---

## VALIDATION RULES

- SDV1: Details are purposeful (meaning or realism).
- SDV2: Signature details prevent “samey” scenes.
- SDV3: Budgets prevent overload and preserve clarity.
- SDV4: Sensory palette stays consistent across outputs and departments.

---

OWNER: Universe Engine
LOCK: FIXED
