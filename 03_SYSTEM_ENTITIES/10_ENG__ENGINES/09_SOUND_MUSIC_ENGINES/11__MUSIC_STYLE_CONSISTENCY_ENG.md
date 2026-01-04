# Music Style Consistency Engine
FILE: 11__MUSIC_STYLE_CONSISTENCY_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 09_SOUND_MUSIC_ENGINES
CLASS: PRODUCTION (L3)
LEVEL: L3
STATUS: ACTIVE
VERSION: 1.0
ROLE: Defines reproducible music style-lock logic (genre identity, palette constraints, harmony/melody/rhythm/arrangement/sound-design norms, mixing aesthetic targets, and drift detection); produces Music Style Bible, Style Locks, Do/Don't lists, Reference Maps, Cross-Track Consistency Specs, and QC Gates to ensure multiple tracks sound like one coherent universe/brand

---

## PURPOSE

Стиль-консистентность — это “узнаваемость музыки как одной вселенной”.
Движок фиксирует:
- что делает стиль стилем (signature)
- палитру тембров и инструментов
- гармонические и мелодические привычки
- ритмический feel и типичные паттерны
- аранжировочную плотность и формы
- саунд-дизайн привычки
- микс-эстетику на уровне целей (без тех-деталей мастера)

Цель: чтобы **несколько треков подряд** звучали как “одна система”.

---

## NON-GOALS

- не заменяет жанровый выбор (это 07 family, 01 Genre engine)
- не делает мастеринг (13)
- не пишет конкретные ноты
Он задаёт **рамки и проверки**.

---

## MINI-CONTRACT (MANDATORY)

### CONSUMES
- Genre/Style engines (06): tone/mood, symbolism, sensory detail
- Production format constraints (07): platform, duration norms
- Harmony/Melody/Rhythm/Arrangement/SoundDesign specs (09.03–10)
- Target brand/universe identity (if applicable)

### PRODUCES
- MUSIC STYLE BIBLE (MSB) — canonical artifact
- STYLE LOCKS (SL)
- DO/DON’T LIST (DDL)
- REFERENCE MAP (RM)
- DRIFT DETECTION RULESET (DDR)
- CROSS-TRACK CONSISTENCY SPEC (CTC)
- STYLE QC GATES (SCG)

### DEPENDS_ON
- 06 Genre/Style engines
- 07 Production format engines
- 09.08–09.10 (arrangement & sound design)
- 09.13 (mix/master targets for aesthetic goals)

### OUTPUT_TARGET
- Feeds:
  - every music engine as constraint layer
  - QA checks across tracks/scenes
  - pipeline enforcement (governance consistency)

---

## CANON TERMS

### STYLE BIBLE
Короткий документ “как звучим всегда”.

### STYLE LOCK
Неприкасаемые признаки: тембр, feel, гармонический язык, плотность.

### SIGNATURE
Что слушатель узнаёт за 5 секунд.

### DRIFT
Нежелательное “сползание” в другой стиль.

### CTC (Cross-Track Consistency)
Спека, которая делает серию треков единым набором.

---

## CORE RULES (CANON)

### S1 — Style is defined by invariants
MSB обязан иметь 5–12 неизменяемых признаков.

### S2 — Constraints apply across all engines
SL распространяется на:
- harmony/melody/rhythm
- arrangement
- sound design
- mix aesthetic targets

### S3 — References are anchored
RM фиксирует референсы (если есть) и что именно берём:
- groove feel
- timbre palette
- density
Не “просто нравится”.

### S4 — Drift is measurable
DDR даёт “детекторы дрейфа”, иначе стиль = мнение.

### S5 — Cross-track spec is mandatory for packs
Если делаем 3+ трека в одном паке → CTC обязателен.

---

## REQUIRED ARTIFACT A: MUSIC STYLE BIBLE (MSB)

### MSB SCHEMA (CANON)

Header:
- MSB_ID:
- STYLE NAME (internal):
- GENRE LABEL (primary + secondary):
- TARGET USE:
  - scene | album | game | trailer | brand
- VERSION:
- STATUS:
  - draft | canon | deprecated

Identity:
- SIGNATURE (1–2 sentences):
- INVARIANTS (5–12 bullets):
  - e.g., “swing-ish hats”, “dark pads”, “simple hook”
- TEMPO RANGE (if relevant):
- ENERGY PROFILE:
  - low/med/high + typical curve

Harmony norms:
- CHORD LANGUAGE:
  - simple triads / extended / modal / dark minors etc.
- CADENCE STYLE:
  - hard resolves / ambiguous / loop-based
- TENSION POLICY:
  - how much tension allowed

Melody norms:
- HOOK SHAPE:
  - stepwise / leap / chant
- MOTIF POLICY:
  - recurring motifs yes/no + how
- RANGE FEEL:
  - narrow / wide

Rhythm norms:
- FEEL:
  - straight / swing-like / triplet-like / halftime
- DRUM DNA:
  - kick/snare identity rules
- ACCENT CHARACTER:
  - where the groove lives

Arrangement norms:
- DENSITY CAP (0–10):
- LAYER ROLES MUST-HAVES:
  - e.g., “sub+kick”, “pad bed”, “signature lead”
- TRANSITION STYLE:
  - minimal vs cinematic

Sound design norms:
- PALETTE FAMILIES (allowed):
- FX INTENSITY POLICY:
- MOTIF SOUNDS (optional):

Mix aesthetic targets (high-level):
- CLEAN vs GRIT:
- SPACE FEEL:
  - intimate / wide / cinematic
- TRANSIENT SHARPNESS:
  - soft/med/hard

Do/Don’t:
- DDL ref

Rule:
- MSB must be short, operational, and enforceable.

---

## REQUIRED ARTIFACT B: STYLE LOCKS (SL)

### SL SCHEMA (CANON)

- SL_ID:
- MSB_ID:

Locks:
- TIMBRE LOCK:
  - instrument families + signature patches
- RHYTHM FEEL LOCK:
  - straight/swing-like; microtiming preference
- HARMONY LOCK:
  - chord language + cadence policy
- MELODY LOCK:
  - hook shape + motif policy
- DENSITY LOCK:
  - cap + minimal set
- FX LOCK:
  - palette + budget

Rule:
- SL are the non-negotiables.

---

## REQUIRED ARTIFACT C: DO/DON’T LIST (DDL)

### DDL SCHEMA (CANON)

- DDL_ID:
- MSB_ID:

DO:
- 5–15 bullets of encouraged behaviors

DON’T:
- 5–15 bullets of forbidden behaviors
  - include explicit “no clichés” for the style

Rule:
- DDL is the fastest enforcement tool.

---

## REQUIRED ARTIFACT D: REFERENCE MAP (RM)

### RM SCHEMA (CANON)

- RM_ID:
- MSB_ID:

References (optional):
For each ref:
- REF NAME:
- WHAT WE TAKE:
  - groove, timbre, density, transitions
- WHAT WE DO NOT TAKE:
  - to avoid copying blindly

Rule:
- RM prevents “reference soup”.

---

## REQUIRED ARTIFACT E: DRIFT DETECTION RULESET (DDR)

### DDR SCHEMA (CANON)

- DDR_ID:
- MSB_ID:

Detectors:
- TIMBRE DRIFT:
  - new instrument family appears without justification
- FEEL DRIFT:
  - groove feel changes (straight→swing) unintentionally
- HARMONY DRIFT:
  - chord language becomes too complex/simple for style
- DENSITY DRIFT:
  - layer count exceeds cap
- FX DRIFT:
  - cinematic risers appear in minimal style, etc.
- MIX AESTHETIC DRIFT:
  - too bright/too gritty vs target

Scoring:
- DRIFT SCORE (0–10):
  - 0–2 ok, 3–5 warning, 6+ fail

Rule:
- DDR turns “style talk” into pass/fail gates.

---

## REQUIRED ARTIFACT F: CROSS-TRACK CONSISTENCY SPEC (CTC)

### CTC SCHEMA (CANON)

- CTC_ID:
- MSB_ID:
- TRACK COUNT:

Shared assets:
- shared drum kit policy
- shared signature patch list
- shared motif sounds (if any)
- shared mix aesthetic notes

Consistency rules:
- hook identity recurrence policy (if series)
- tempo range for pack
- density profile per track type (A/B/C roles)

Rule:
- CTC ensures pack-level coherence.

---

## REQUIRED ARTIFACT G: STYLE QC GATES (SCG)

### SCG SCHEMA (CANON)

Gates:
1) Invariants gate:
   - MSB has clear invariants; track obeys them
2) Lock gate:
   - SL applied across harmony/melody/rhythm/arrangement/sound design
3) Do/Don’t gate:
   - DDL pass (no forbidden clichés)
4) Reference gate:
   - RM used correctly (not copied blindly)
5) Drift score gate:
   - DDR score <= threshold
6) Cross-track gate (if pack):
   - CTC coherence holds
7) Reproducibility gate:
   - MSB+SL+DDL+DDR(+CTC) allow consistent reproduction

Rule:
- Fail 2+ gates → revise specs or declare intentional deviation.

---

## INCONSISTENCY DETECTOR (HEURISTICS)

Flag if:
- each track uses totally different drum DNA
- harmony complexity varies wildly across tracks
- sound design palette changes every minute
- transitions are inconsistent (big risers then none)
- mix aesthetic swings (super bright vs super dark)
- “signature” is not audible within first 5–10 seconds

Fix options:
- define or tighten SL invariants
- enforce shared kit/patch list (CTC)
- cap density and FX budgets
- unify cadence style and hook shape norms
- specify mix aesthetic targets (clean/grit, space)
- add motif sound or recurring signature layer

---

## PROCEDURE (HOW TO RUN)

1) Define style identity and invariants (MSB)
2) Lock the non-negotiables (SL)
3) Create Do/Don’t list (DDL)
4) Add references with “what we take” (RM) if needed
5) Define drift detectors and thresholds (DDR)
6) If producing multiple tracks → define CTC
7) Run SCG gates on each track/spec
8) Governance: any change to MSB/SL triggers change control

---

## QC CHECKLIST (MANDATORY)

- invariants list exists and is enforceable?
- locks cover all music engines?
- do/don’t list explicit and useful?
- drift detectors defined and scored?
- pack-level CTC exists for multiple tracks?
- spec reproducible?

---

## VALIDATION RULES

- SCV1: Multiple tracks sound like one coherent style/universe.
- SCV2: Invariants are audible and stable across outputs.
- SCV3: Constraints apply across all music subsystems.
- SCV4: Drift is detectable and controlled.
- SCV5: Pack-level consistency holds via CTC when needed.
- SCV6: Spec is reproducible and enforceable.

---

OWNER: Universe Engine
LOCK: FIXED
