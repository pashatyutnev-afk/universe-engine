# Rhythm / Groove Engine
FILE: 05__RHYTHM_GROOVE_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 09_SOUND_MUSIC_ENGINES
CLASS: PRODUCTION (L3)
LEVEL: L3
STATUS: ACTIVE
VERSION: 1.0
ROLE: Defines reproducible rhythm and groove logic (tempo strategy, meter, swing, microtiming feel, section-based groove design, density control, accent grids, and energy drive); produces Rhythm Specs, Groove Libraries, Section Rhythm Maps, Sync Marker Sets, and QC Gates compatible with song structure, editing rhythm maps, and style locks

---

## PURPOSE

Ритм и грув — это “двигатель движения”.
Движок фиксирует:
- выбор темпа и метра
- ощущение грува (straight/swing/shuffle/half-time/double-time)
- микротайминг (чуть вперед/чуть назад)
- паттерны ударных и акцентную сетку
- плотность и динамику по секциям
- синхру с монтажом/битами сцены

---

## NON-GOALS

- не пишет мелодию/хук (04)
- не выбирает гармонию (03)
- не делает микс (13)
Он задаёт **ритмическую архитектуру и feel**.

---

## MINI-CONTRACT (MANDATORY)

### CONSUMES
- Composition Spec (09.01) + TRP (tension curve)
- Song Structure Spec (09.02) section jobs & energy
- Melody Spec (09.04) rhythmic identity notes
- Style locks (allowed groove language)
- Editing rhythm map / sync needs (from 08 Editing + 08 production audio)
- Platform constraints (loopable, trailer hits, etc.)

### PRODUCES
- RHYTHM SPEC (RS) — canonical artifact
- GROOVE LIBRARY (GL)
- SECTION RHYTHM MAP (SRM)
- ACCENT GRID (AG)
- MICROTIMING PROFILE (MTP)
- SYNC MARKER SET (SMS)
- RHYTHM QC GATES (RQG)

### DEPENDS_ON
- 09.02 Song Structure (where groove changes)
- 09.04 Melody/Hook (rhythmic identity alignment)
- 06 Genre/Style engines (tone)
- 08 Knowledge Production (editing/sync integration)
- 09.08 Arrangement (implementation)

### OUTPUT_TARGET
- Feeds:
  - arrangement/drum programming
  - vocal performance phrasing
  - music-to-scene (12)
  - mix/master transient handling (13)

---

## CANON TERMS

### TEMPO STRATEGY
Выбор BPM и возможность его изменений.

### METER
Размер (4/4, 3/4, 6/8 …).

### GROOVE FEEL
Как “качает”:
- straight, swing, shuffle, broken, half-time, double-time, triplet feel

### ACCENT GRID
Где лежат основные акценты (удары, кики, снейры, клатчи).

### MICROTIMING
Намеренное смещение ударов:
- ahead (push) / behind (lay back) / tight

### DENSITY
Сколько событий в единицу времени:
- sparse / mid / busy

### HIT / STINGER
Резкий акцент под событие/кадр.

---

## CORE RULES (CANON)

### RG1 — Rhythm serves energy curve
Ритм обязан соответствовать:
- энергии секции (SSS energy curve)
- tension plan (TRP)

### RG2 — Groove language is bounded
Есть допустимые грувы (GL).
Запрещено прыгать между несовместимыми feel без причины.

### RG3 — Section-based groove logic
Каждая секция имеет:
- groove role (setup/build/payoff/contrast/release)

### RG4 — Microtiming is intentional
MTP задаёт feel:
- tight vs laid back vs pushed

### RG5 — Accent grid defines punch
AG обязателен:
- иначе “плывёт”

### RG6 — Sync markers are explicit when needed
Если музыка под монтаж/сцену:
- SMS обязателен (beats/cuts/turns/climax)

---

## GROOVE ROLES (SECTION FUNCTION)

- SETUP GROOVE:
  - мягкий, меньше событий, больше воздуха
- BUILD GROOVE:
  - добавляем движение, поднимаем плотность
- PAYOFF GROOVE:
  - самый уверенный “кач”, читаемый, сильный
- CONTRAST GROOVE:
  - смена feel (например half-time), минимализм или “слом”
- RELEASE GROOVE:
  - разрядка, простор, завершение
- CHASE / ACTION GROOVE (если нужно):
  - агрессивная сетка, сильный forward motion

Rule:
- Каждая секция получает один groove role.

---

## REQUIRED ARTIFACT A: RHYTHM SPEC (RS)

### RS SCHEMA (CANON)

Header:
- RS_ID:
- CS_ID:
- SSS_ID (if song):
- STYLE LOCK:
- VERSION:
- STATUS:
  - draft | canon | deprecated

Tempo + meter:
- BPM TARGET (range):
- TEMPO CHANGE POLICY:
  - none | ramps allowed | switch points
- METER:
- SUBDIVISION FEEL:
  - straight 8ths | swing | triplet | shuffle
- HALF/DOUBLE TIME POLICY:
  - allowed? where?

Groove identity:
- PRIMARY GROOVE (GL ref):
- MICROTIMING PROFILE (MTP ref):
- ACCENT GRID (AG ref):
- DENSITY CAP:
- “DO NOT”:
  - forbidden feels/patterns

Per section:
- SECTION ID:
- GROOVE ROLE:
- DENSITY TARGET:
- ACCENT EMPHASIS:
- BREAK/FILL POLICY:
- TRANSITION OUT:
  - fill/drop/stinger/none

Sync:
- SYNC MARKER SET (SMS ref) if required

Rule:
- RS must allow recreation of the rhythm feel.

---

## REQUIRED ARTIFACT B: GROOVE LIBRARY (GL)

### GL SCHEMA (CANON)

- GL_ID:
- STYLE_ID:

For each groove:
- GROOVE ID:
- FEEL TYPE:
  - straight/swing/shuffle/half-time/etc
- METER + SUBDIVISION:
- BPM COMFORT RANGE:
- KICK/SNARE ANCHORS (text):
- HIHAT/SHAPER ROLE:
- USE CASE:
  - calm/build/action/anthem
- “DO NOT”:
  - when it breaks style

Rule:
- GL is curated; avoids random groove drift.

---

## REQUIRED ARTIFACT C: SECTION RHYTHM MAP (SRM)

### SRM SCHEMA (CANON)

For each section:
- SECTION ID:
- GROOVE ROLE:
- PATTERN SUMMARY (text):
  - kick anchors, snare/clap placement, hat feel
- DENSITY (0–10):
- “GROOVE MOMENT”:
  - signature move (pause, syncopation, drop)
- TRANSITION DEVICE:
  - fill, stop, stinger, reverse, riser

Rule:
- SRM is a section-by-section blueprint.

---

## REQUIRED ARTIFACT D: ACCENT GRID (AG)

### AG SCHEMA (CANON)

- AG_ID:
- RS_ID:

Grid:
- PRIMARY ACCENTS:
  - where the “spine” is (beats)
- SECONDARY ACCENTS:
  - syncopation points
- BACKBEAT POLICY:
  - yes/no + how strong
- OFFBEAT POLICY:
  - allowed? where?
- SILENCE HITS:
  - where silence acts as accent

Rule:
- AG defines punch and readability.

---

## REQUIRED ARTIFACT E: MICROTIMING PROFILE (MTP)

### MTP SCHEMA (CANON)

- MTP_ID:
- STYLE_ID:

Profile:
- FEEL:
  - tight | laid-back | pushed | humanized
- SWING AMOUNT (if any):
  - low/med/high (no numbers needed)
- HUMANIZE POLICY:
  - minimal/medium/heavy + where allowed
- TRANSIENT PRIORITY:
  - punchy | soft | mixed
- “NO DRIFT” RULE:
  - keep anchors tight even if hats float

Rule:
- MTP prevents “random sloppy timing”.

---

## REQUIRED ARTIFACT F: SYNC MARKER SET (SMS)

### SMS SCHEMA (CANON)

- SMS_ID:
- CS_ID:
- USE:
  - trailer hits | montage | scene underscore | cut sync

Markers:
- MARKER ID:
- TYPE:
  - cut | reveal | impact | turn | climax | breath
- TIMESTAMP or BAR:
- REQUIRED ACCENT:
  - stinger, fill, drop, hit
- ALLOWABLE WINDOW:
  - tight | small | loose

Rule:
- SMS is bridge to editing/montage engines.

---

## REQUIRED ARTIFACT G: RHYTHM QC GATES (RQG)

### RQG SCHEMA (CANON)

Gates:
1) Energy alignment gate:
   - RS matches section energy and TRP
2) Groove language gate:
   - GL respected; no incompatible jumps
3) Accent readability gate:
   - AG gives clear punch
4) Microtiming intention gate:
   - MTP specified and consistent
5) Section logic gate:
   - SRM matches section jobs (setup/build/payoff)
6) Sync accuracy gate:
   - SMS exists when needed and is usable
7) Reproducibility gate:
   - RS artifacts allow recreation

Rule:
- Fail 2+ gates → revise RS/AG/MTP.

---

## INCONSISTENCY DETECTOR (HEURISTICS)

Flag if:
- groove changes randomly between sections
- energy curve says “lift” but rhythm stays flat
- accents unclear; kick/snare wander
- microtiming feels inconsistent (sometimes tight, sometimes sloppy)
- fills happen too often (noise) or never (stale)
- sync hits miss cuts/reveals

Fix options:
- choose one primary groove and vary density, not feel
- design 1–2 signature groove moments only
- lock backbeat; simplify kick anchors
- define MTP and enforce anchor tightness
- add fewer, purposeful fills at transitions
- add SMS markers for crucial beats/cuts

---

## PROCEDURE (HOW TO RUN)

1) Read CS purpose + TRP + SSS energy curve
2) Pick meter + tempo strategy
3) Choose primary groove from GL
4) Define microtiming profile (MTP)
5) Define accent grid (AG)
6) Build SRM per section roles
7) Add sync markers (SMS) if scene/monatge needed
8) Output RS and run RQG gates
9) Hand off to arrangement/drums + music-to-scene engine

---

## QC CHECKLIST (MANDATORY)

- tempo/meter chosen intentionally?
- groove role per section defined?
- accent grid readable?
- microtiming profile consistent?
- density changes match energy curve?
- sync markers exist if needed?
- RS reproducible from artifacts?

---

## VALIDATION RULES

- RGV1: Rhythm supports energy/tension plans.
- RGV2: Groove language is coherent and style-locked.
- RGV3: Accents are readable and punchy by design.
- RGV4: Microtiming feel is intentional and consistent.
- RGV5: Section rhythm logic supports structure and transitions.
- RGV6: Sync markers are usable when required.
- RGV7: Spec is reproducible.

---

OWNER: Universe Engine
LOCK: FIXED
