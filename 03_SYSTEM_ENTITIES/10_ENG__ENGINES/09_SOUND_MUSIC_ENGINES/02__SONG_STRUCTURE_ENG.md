# Song Structure Engine
FILE: 02__SONG_STRUCTURE_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 09_SOUND_MUSIC_ENGINES
CLASS: PRODUCTION (L3)
LEVEL: L3
STATUS: ACTIVE
VERSION: 1.0
ROLE: Defines reproducible song form logic (section types, section order templates, payoff cadence, energy shaping, hook placement, and repetition control); produces Song Structure Specs, Section Maps, Template Libraries, and QC Gates for consistent writing of songs that remain clear, engaging, and style-locked across a universe or series

---

## PURPOSE

Структура песни — это “путь внимания” слушателя.
Движок фиксирует:
- какие секции бывают и зачем
- порядок и длины секций
- где ставится хук и как часто он платится
- управление энергией и контрастом
- контроль повторов (чтобы не надоело и не развалилось)

---

## NON-GOALS

- не пишет мелодию/хук (это 04)
- не пишет гармонию (это 03)
- не делает аранжировку (это 08)
Он задаёт **архитектуру песни**.

---

## MINI-CONTRACT (MANDATORY)

### CONSUMES
- Composition Spec (09.01) purpose + theme/motif intent
- Genre/style locks (what song types are allowed)
- Target duration and platform (radio/short/streaming)
- Hook strategy (melodic/rhythmic/lyric/timbral)

### PRODUCES
- SONG STRUCTURE SPEC (SSS) — canonical artifact
- SECTION MAP (SecMap)
- TEMPLATE LIBRARY (TLIB)
- PAYOFF CADENCE (PC)
- STRUCTURE QC GATES (SQG)

### DEPENDS_ON
- 09_SOUND_MUSIC_ENGINES/01__MUSIC_COMPOSITION_ENG.md
- 09_SOUND_MUSIC_ENGINES/04__MELODY_HOOK_ENG.md
- 09_SOUND_MUSIC_ENGINES/05__RHYTHM_GROOVE_ENG.md
- 09_SOUND_MUSIC_ENGINES/08__ARRANGEMENT_INSTRUMENTATION_ENG.md

### OUTPUT_TARGET
- Feeds:
  - lyric plan (07)
  - arrangement plan (08)
  - vocal performance plan (09)
  - mix/master plan (13)

---

## CANON TERMS

### SECTION
Функциональный блок песни (Intro/Verse/Chorus…).

### PAYOFF
“Оплата” обещания: хук/идея возвращается и удовлетворяет.

### ENERGY CURVE
План энергии по секциям (0–10).

### CONTRAST
Разница между секциями (текстура/гармония/динамика/мелодия).

### REPETITION CONTROL
Контроль повторов: сколько и как повторять, чтобы:
- узнавалось
- не надоедало

---

## CORE RULES (CANON)

### SS1 — Every section has a job
Секция обязана иметь функцию:
- setup, build, release, contrast, resolution

### SS2 — Chorus must pay
Если есть припев — он должен быть payoff’ом.
Если нет payoff — это не chorus, это “ещё один куплет”.

### SS3 — Hook strategy is explicit
Хук может быть:
- melodic (главный)
- rhythmic
- lyric phrase
- timbral signature
Но стратегия выбирается и фиксируется.

### SS4 — Repetition with variation
Повторы допустимы только с контролем вариаций:
- текст/мелодия/подача/аранж
“копипаста” снижает ценность.

### SS5 — Energy curve must be designed
Даже спокойная песня имеет движение:
- микро-рост / микро-спад / контраст

### SS6 — Bridge exists only if needed
Бридж нужен для:
- контраста
- “переворота смысла”
- подготовки финального припева
Если этого нет — бридж запрещён.

### SS7 — Ending is intentional
Концовка фиксируется:
- resolve / fade / stinger / loop-ready

---

## SECTION TYPES (CANON)

Allowed section set:
- INTRO (I)
- VERSE (V)
- PRE-CHORUS (P) optional
- CHORUS (C)
- POST-CHORUS / TAG (T) optional (hook repeat)
- BRIDGE (B) optional
- BREAKDOWN (D) optional (drop, texture reset)
- OUTRO (O)

Rule:
- Не обязаны быть все секции.
- Но каждая используемая секция обязана иметь job.

---

## TEMPLATE LIBRARY (TLIB) — CANON FORMS

### TLIB SCHEMA
- TEMPLATE ID:
- USE CASE:
- ORDER:
- NOTES:

Canonical templates:
1) POP STANDARD:
   - I – V – P – C – V – P – C – B – C – O
2) NO PRE-CHORUS:
   - I – V – C – V – C – B – C – O
3) SHORT FORM (streaming/viral):
   - I(0–4s) – C – V – C – B/Drop – C – O
4) STORY SONG (lyric-driven):
   - I – V – V – C – V – C – B – C – O
5) ANTHEM (chorus-centric):
   - I – C – V – C – V – C – B – C – C – O
6) MINIMAL / LOOP SONG:
   - I – V – C – V – C – O (loop-ready ending)

Rule:
- Template chosen must match purpose and genre locks.

---

## REQUIRED ARTIFACT A: SONG STRUCTURE SPEC (SSS)

### SSS SCHEMA (CANON)

Header:
- SSS_ID:
- CS_ID (from 09.01):
- TRACK NAME:
- GENRE/STYLE LOCK:
- TARGET DURATION:
- BPM RANGE (optional; actual in rhythm engine):
- VERSION:
- STATUS:
  - draft | canon | deprecated

Hook strategy:
- PRIMARY HOOK TYPE:
- HOOK FIRST APPEARANCE (timestamp/section):
- HOOK PAYOFF FREQUENCY:
- “HOOK MUST”:
- “HOOK MUST NOT”:

Section map:
- ORDER (template or custom):
- SECTION LENGTHS (bars or seconds):
- SECTION JOBS:
  - each section has a one-line job
- ENERGY CURVE (0–10 per section):
- CONTRAST NOTES:
- REPETITION CONTROL NOTES:
  - what repeats and what varies

Ending:
- ENDING TYPE:
- LOOP READY:
  - yes/no + how

Rule:
- SSS must enable another writer to reproduce the same form.

---

## REQUIRED ARTIFACT B: SECTION MAP (SecMap)

### SecMap SCHEMA (CANON)

For each section:
- SECTION ID (I/V1/P1/C1…):
- PURPOSE (job):
- LYRICAL FUNCTION:
  - setup | detail | turn | payoff | reflection
- MELODIC ROLE:
  - low contour | rising | peak
- HARMONIC ROLE:
  - stable | build | release
- ARRANGEMENT DENSITY:
  - sparse | mid | full
- VOCAL INTENSITY:
  - low | mid | high
- TRANSITION OUT:
  - how it moves to next section

Rule:
- SecMap is “blueprint per section”.

---

## REQUIRED ARTIFACT C: PAYOFF CADENCE (PC)

### PC SCHEMA (CANON)

- PC_ID:
- SSS_ID:

Payoff schedule:
- MICRO PAYOFFS:
  - hooks, fills, lyric tags (by section)
- MAJOR PAYOFFS:
  - chorus returns, bridge-to-final lift
- FINAL PAYOFF:
  - last chorus/outro resolution

Rule:
- No long stretch without payoff marker.

---

## REQUIRED ARTIFACT D: STRUCTURE QC GATES (SQG)

### SQG SCHEMA (CANON)

Gates:
1) Section job gate:
   - every section has a clear job
2) Chorus payoff gate:
   - chorus pays hook/meaning
3) Hook strategy gate:
   - hook type + placement explicit
4) Energy curve gate:
   - energy planned; no unintended flatline
5) Contrast gate:
   - sections are distinguishable where required
6) Repetition control gate:
   - repeats have planned variations
7) Bridge justification gate:
   - if bridge exists, it has purpose
8) Ending intention gate:
   - ending type declared and fits purpose
9) Reproducibility gate:
   - another agent could rebuild form from SSS

Rule:
- Fail 2+ gates → restructure.

---

## INCONSISTENCY DETECTOR (HEURISTICS)

Flag if:
- verse and chorus feel identical (no payoff)
- too many sections without reason
- energy stays the same all song
- hook appears too late or too rarely
- bridge exists but adds nothing
- repetitive copy-paste choruses (no variation)
- ending just “stops” with no design

Fix options:
- redefine chorus job to be payoff
- add pre-chorus build or remove it
- adjust energy curve: sparse → full
- move hook earlier; add tag/post-chorus
- replace bridge with breakdown or remove
- plan small variations: adlibs, harmony, rhythm switch
- choose ending type and design it

---

## PROCEDURE (HOW TO RUN)

1) Identify song purpose (from CS)
2) Choose template (TLIB) or custom order
3) Define hook strategy and first appearance
4) Map section jobs and energy curve
5) Set section lengths and contrast rules
6) Define repetition control (what varies)
7) Choose ending type (loop/resolve/fade/stinger)
8) Produce SSS + SecMap + PC
9) Run SQG gates and iterate

---

## QC CHECKLIST (MANDATORY)

- template chosen matches purpose/genre?
- every section has job and transition logic?
- chorus pays and is distinct?
- hook appears early enough and repeats with intent?
- energy curve has movement?
- repetition control prevents boredom?
- bridge is justified or removed?
- ending is designed?

---

## VALIDATION RULES

- SSV1: Structure is clear and serves purpose.
- SSV2: Chorus (if used) delivers payoff.
- SSV3: Hook strategy is explicit and effective.
- SSV4: Energy and contrast are designed, not accidental.
- SSV5: Repetition is controlled with planned variation.
- SSV6: Output is reproducible from spec.

---

OWNER: Universe Engine
LOCK: FIXED
