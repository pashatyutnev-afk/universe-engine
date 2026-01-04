# Music Composition Engine
FILE: 01__MUSIC_COMPOSITION_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 09_SOUND_MUSIC_ENGINES
CLASS: PRODUCTION (L3)
LEVEL: L3
STATUS: ACTIVE
VERSION: 1.0
ROLE: Defines reproducible music composition logic (themes, motifs, development, tension/release, form selection, and narrative purpose); produces Composition Specs, Theme Libraries, Development Maps, and QC Gates for consistent soundtrack creation across scenes, episodes, and franchises

---

## PURPOSE

Композиция — это “смысл музыки во времени”.
Движок фиксирует, как создавать музыку так, чтобы она:
- служила сцене/арке/миру
- имела узнаваемые темы и мотивы
- развивалась, а не крутилась в петле
- была воспроизводима по спецификации

---

## NON-GOALS

- не заменяет Harmony/Chord engine (аккорды отдельно)
- не заменяет Melody/Hook engine (мелодия отдельно)
- не заменяет Arrangement engine (оркестровка отдельно)
Он задаёт **скелет и драматургию музыкального произведения**.

---

## MINI-CONTRACT (MANDATORY)

### CONSUMES
- Scene / arc emotional targets
- Genre + tone locks
- Character/Location/Force identities (если темы привязываются)
- Editing rhythm map (если под монтаж)
- Platform constraints (duration, loop needs)

### PRODUCES
- COMPOSITION SPEC (CS) — canonical artifact
- THEME LIBRARY (TL)
- MOTIF BANK (MB)
- DEVELOPMENT MAP (DM)
- TENSION/RELEASE PLAN (TRP)
- COMPOSITION QC GATES (CQG)

### DEPENDS_ON
- 06_GENRE_STYLE_ENGINES (tone/mood)
- 02_DOMAIN_NARRATIVE_ENGINES (theme/meaning, pacing)
- 08_KNOWLEDGE_PRODUCTION_ENGINES/08__SOUND_MUSIC_ENG.md (placement/sync constraints)
- 09_SOUND_MUSIC_ENGINES/03..13 (harmony/melody/arrangement/mix)

### OUTPUT_TARGET
- Feeds:
  - song structure (if song)
  - cue sheets / scene cues
  - motif usage across episodes
  - arrangement briefs

---

## CANON TERMS

### THEME
Музыкальная “личность” сущности:
- персонаж / место / фракция / сила / идея.

### MOTIF
Короткий знак (2–8 нот или ритм/тембр), который узнаётся.

### DEVELOPMENT
Изменение темы/мотива:
- ритм, интервалы, регистр, тембр, гармония, плотность.

### TENSION/RELEASE
План напряжения и разрядки во времени.

### FORM
Композиционная форма (не обязательно “куплет/припев”):
- A–A’–B–A, through-composed, theme & variations, etc.

---

## CORE RULES (CANON)

### MC1 — Every piece has a purpose
Музыка обязана отвечать:
- что она делает для сцены/мира?

### MC2 — Recognizability is designed
Если есть “тема”, она должна быть:
- узнаваема
- повторяема
- вариативна через DM

### MC3 — Development is mandatory past short loops
Если длительность > 45–60 сек, нужна эволюция:
- минимум 2 стадии развития

### MC4 — Tension plan must exist
Даже спокойная музыка должна иметь:
- микродвижение
- форму “куда-то”

### MC5 — Form is chosen, not accidental
Форма выбирается исходя из:
- функции (underscore vs main theme vs action cue)
- длительности
- монтажных нужд

### MC6 — Canon style locks apply
Тембры, язык формы, степень “современности” — подчиняются стилю вселенной.

---

## REQUIRED ARTIFACT A: COMPOSITION SPEC (CS)

### CS SCHEMA (CANON)

Header:
- CS_ID:
- PROJECT_ID / WORLD_ID:
- TRACK/CUE NAME:
- TYPE:
  - main theme | character theme | location theme | action cue | ambience music | montage cue | trailer cue
- DURATION TARGET:
- VERSION:
- STATUS:
  - draft | canon | deprecated

Purpose:
- SCENE/ARC PURPOSE:
- EMOTIONAL TARGET (1–3 words):
- “WHAT MUST BE FELT” (one sentence):
- “WHAT MUST NOT HAPPEN” (tone taboo):

Form:
- FORM TYPE:
- SECTION LIST (A/B/C… with timestamps):
- LOOP POLICY:
  - none | soft loop | hard loop

Material:
- PRIMARY THEME (ref to TL):
- SECONDARY THEME (optional):
- MOTIFS USED (refs to MB):
- DEVELOPMENT METHOD (ref to DM):
- TENSION/RELEASE PLAN (ref to TRP):

Constraints:
- STYLE LOCKS:
- INSTRUMENT/TIMBRE CAPS (if any):
- DENSITY CAP:
- SYNC MARKERS (if needed):
- ENDING TYPE:
  - stinger | resolve | fade | cut-ready

Rule:
- CS must be sufficient for another composer/agent to reproduce the intent.

---

## REQUIRED ARTIFACT B: THEME LIBRARY (TL)

### TL SCHEMA (CANON)

- TL_ID:
- PROJECT_ID / WORLD_ID:

For each theme:
- THEME ID:
- OWNER ENTITY (character/location/faction/idea):
- CORE SHAPE:
  - melodic contour / interval idea (text description)
- CORE RHYTHM FEEL:
- CORE TIMBRE SIGNATURE:
- “WHAT IT MEANS” (one sentence):
- USAGE RULES:
  - when allowed / when forbidden
- VARIATION RULES:
  - how it can evolve without losing identity

Rule:
- TL prevents “new theme every time” chaos.

---

## REQUIRED ARTIFACT C: MOTIF BANK (MB)

### MB SCHEMA (CANON)

- MB_ID:
- PROJECT_ID / WORLD_ID:

For each motif:
- MOTIF ID:
- MOTIF TYPE:
  - melodic | rhythmic | timbral | harmonic
- OWNER (optional):
- SIGNAL MEANING:
  - what it signals (danger/hope/arrival)
- INSERTION WINDOWS:
  - where it can appear (acts/turns)
- “DO NOT”:
  - where it must not appear

Rule:
- Motifs are the “language particles” of the score.

---

## REQUIRED ARTIFACT D: DEVELOPMENT MAP (DM)

### DM SCHEMA (CANON)

- DM_ID:
- CS_ID:

Stages (minimum 2 if >60 sec):
- STAGE 1 (baseline):
  - register, density, timbre, rhythm
- STAGE 2 (variation):
- STAGE 3 (intensify) optional:
- STAGE 4 (release/resolve) optional:

Development techniques:
- augmentation/diminution (conceptual)
- register shift
- orchestration shift
- rhythmic displacement
- fragmentation
- inversion (optional)
- harmonic reharmonization (with Harmony engine)

Rule:
- DM describes “how the theme changes” in plain terms.

---

## REQUIRED ARTIFACT E: TENSION/RELEASE PLAN (TRP)

### TRP SCHEMA (CANON)

- TRP_ID:
- CS_ID:

Curve:
- START TENSION (0–10):
- PEAK TENSION (0–10):
- END TENSION (0–10):

Anchors:
- BUILD POINTS (timestamps):
- RELEASE POINTS (timestamps):
- “HOLD ZONES” (if any):
- “SURPRISE SPIKES” (if any):

Rule:
- TRP must align with scene arc or montage rhythm if used.

---

## REQUIRED ARTIFACT F: COMPOSITION QC GATES (CQG)

### CQG SCHEMA (CANON)

Gates:
1) Purpose gate:
   - CS purpose is explicit
2) Identity gate:
   - theme/motif is recognizable
3) Development gate:
   - DM provides evolution (if duration requires)
4) Tension gate:
   - TRP exists and matches intent
5) Form gate:
   - form chosen intentionally; sections make sense
6) Style lock gate:
   - timbre/shape language obeys project style
7) Reproducibility gate:
   - another agent could recreate from CS

Rule:
- Fail 2+ gates → rewrite CS / material.

---

## INCONSISTENCY DETECTOR (HEURISTICS)

Flag if:
- track has no purpose beyond “background”
- “theme” appears once and never returns
- long track with no development (static loop)
- tension curve is flat when scene needs motion
- too many new motifs introduced (noise)
- style locks drift (wrong era/genre suddenly)

Fix options:
- write purpose in one sentence and recompose
- reuse TL themes and evolve via DM
- cut motifs to 1–2 core signals
- enforce TRP anchors and section form
- push variation into arrangement/harmony instead of new themes

---

## PROCEDURE (HOW TO RUN)

1) Determine purpose (scene/arc function)
2) Select or create theme in TL
3) Select motifs in MB (optional)
4) Choose form and section plan
5) Draft TRP curve and anchors
6) Draft DM stages (how it evolves)
7) Create CS artifact (full spec)
8) Run CQG gates
9) Hand off to Harmony/Melody/Arrangement engines for detailed materialization

---

## QC CHECKLIST (MANDATORY)

- CS has purpose + emotion + taboo?
- TL theme exists and has usage rules?
- MB motifs are bounded and meaningful?
- DM stages exist and are clear?
- TRP curve matches arc?
- form is intentional and loop policy declared?
- CQG gates applied?

---

## VALIDATION RULES

- MCV1: Music serves narrative purpose.
- MCV2: Themes/motifs are recognizable and reusable.
- MCV3: Development and tension plan prevent static loops.
- MCV4: Form is intentional and production-friendly.
- MCV5: Spec is reproducible by another agent.

---

OWNER: Universe Engine
LOCK: FIXED
