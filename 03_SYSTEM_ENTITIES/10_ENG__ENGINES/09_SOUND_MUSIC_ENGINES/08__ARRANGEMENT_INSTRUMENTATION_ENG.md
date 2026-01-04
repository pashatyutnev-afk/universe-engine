# Arrangement / Instrumentation Engine
FILE: 08__ARRANGEMENT_INSTRUMENTATION_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 09_SOUND_MUSIC_ENGINES
CLASS: PRODUCTION (L3)
LEVEL: L3
STATUS: ACTIVE
VERSION: 1.0
ROLE: Defines reproducible arrangement and instrumentation logic (instrument roles, layer stacks, register allocation, section-based density, timbre hooks, counterlines, transitions, and mix-ready constraints); produces Arrangement Specs, Layer Maps, Register Plans, Instrument Role Libraries, Transition Devices, and QC Gates aligned with harmony, melody, rhythm, vocals, and mix/master targets

---

## PURPOSE

Аранжировка — это “как музыка звучит физически”.
Она превращает:
гармонию + мелодию + грув + текст
в **слои, инструменты, регистры и динамику**.

Движок фиксирует:
- какой инструмент что делает (роль)
- какие слои в каких секциях
- распределение по регистрам (чтобы не было каши)
- тембровые хуки (sound identity)
- контрмелодии/ответы
- переходы (fills/drops/risers/stingers)
- микс-совместимость (пространство и частоты на уровне правил)

---

## NON-GOALS

- не делает финальный микс/мастер (это 13)
- не пишет ноты мелодии (это 04)
- не выбирает аккорды (это 03)
Он делает **архитектуру звучания и слоёв**.

---

## MINI-CONTRACT (MANDATORY)

### CONSUMES
- Harmony Spec (09.03) + cadences
- Melody Spec (09.04) + hook map
- Rhythm Spec (09.05) + accent grid
- Lyrics constraints (09.06/09.07) if vocal
- Vocal performance constraints (09.09)
- Music style consistency locks (09.11)
- Target platform (cinematic / pop / game / trailer)

### PRODUCES
- ARRANGEMENT SPEC (AS) — canonical artifact
- LAYER STACK MAP (LSM)
- INSTRUMENT ROLE LIBRARY (IRL)
- REGISTER PLAN (RP)
- TRANSITION DEVICE MAP (TDM)
- TIMBRE HOOK BRIEF (THB)
- ARRANGEMENT QC GATES (AQG)

### DEPENDS_ON
- 09.03 Harmony
- 09.04 Melody
- 09.05 Rhythm
- 09.09 Vocal Performance (if vocal)
- 09.13 Mix/Master targets (for constraints)
- 06 Genre/Style engines

### OUTPUT_TARGET
- Feeds:
  - sound design (10) and mix/master (13)
  - music-to-scene alignment (12)
  - style consistency checks (11)

---

## CANON TERMS

### LAYER
Отдельный функциональный слой: kick, bass, pad, lead, fx, etc.

### ROLE
Роль слоя/инструмента:
- FOUNDATION / PULSE / HARMONY / LEAD / COUNTER / TEXTURE / IMPACT / AIR

### REGISTER
Диапазон высот:
- low / low-mid / mid / high / air

### POCKET
“Место” для главного элемента (обычно вокал/лид).

### TIMBRE HOOK
Узнаваемая тембровая подпись (синт-звук, гитара, тембр ударных).

### ARRANGEMENT PAYOFF
Момент, где аранжировка “выплачивает” ожидание (вход слоя, смена регистра, drop).

---

## CORE RULES (CANON)

### A1 — Lead always has a pocket
Главный элемент (вокал/лид) обязан иметь:
- пространство в RP
- “не конкурирующие” слои вокруг

### A2 — Each layer has a job
Ни один слой не существует “для красоты”.
Каждый слой имеет роль (IRL).

### A3 — Section density follows energy curve
Плотность слоёв по секциям:
- setup < build < payoff
и/или намеренный контраст.

### A4 — Low-end is strictly managed
Нельзя:
- 3+ конкурирующих low слоёв
- плотные аккорды внизу
RP + low-end rules обязательны.

### A5 — Timbre hook is fixed
THB фиксирует узнаваемую подпись.
Если меняем — это intentional.

### A6 — Transitions are designed
Переходы не “случайные фифы”.
TDM обязателен для ключевых переходов.

### A7 — Mix-ready constraints exist
Аранжировка не должна заставлять микс “спасать”.
AQG включает проверку конфликтов.

---

## INSTRUMENT ROLES (IRL — CANON)

Roles:
- FOUNDATION: sub/bass + основа
- PULSE: drums/percussion groove
- HARMONY BED: pads/keys/guitars holding chords
- LEAD: main hook carrier (vocal/lead synth)
- COUNTER: call-response, counter-melody
- TEXTURE: noise, ambience, subtle layers
- IMPACT: hits, stingers, risers, drops
- AIR: top sparkle, shimmers, highs

Rule:
- Один слой = одна основная роль (secondary role optional, but bounded).

---

## REQUIRED ARTIFACT A: ARRANGEMENT SPEC (AS)

### AS SCHEMA (CANON)

Header:
- AS_ID:
- HS_ID:
- MS_ID:
- RS_ID:
- (LS_ID if lyrics/vocal):
- STYLE LOCK:
- VOCAL:
  - yes/no
- VERSION:
- STATUS:
  - draft | canon | deprecated

Identity:
- TIMBRE HOOK BRIEF (THB ref)
- PRIMARY LEAD CARRIER:
  - vocal | synth | guitar | other
- “ARRANGEMENT SIGNATURE”:
  - one sentence describing the unique sound identity

Global constraints:
- REGISTER PLAN (RP ref)
- INSTRUMENT ROLE LIBRARY (IRL ref)
- LOW-END RULES:
  - max 1 sub layer, bass+kick relationship policy
- DENSITY CAP (0–10):
- FX POLICY:
  - minimal/med/heavy + where

Per section:
- SECTION ID:
- LAYER STACK (LSM ref item)
- DENSITY TARGET (0–10):
- LEAD POCKET POLICY:
  - what gets out of the way
- TRANSITION OUT (TDM ref item)

Rule:
- AS must allow another producer to rebuild the arrangement.

---

## REQUIRED ARTIFACT B: LAYER STACK MAP (LSM)

### LSM SCHEMA (CANON)

For each section:
- SECTION ← (V1/C1/B...)
- ACTIVE LAYERS (ordered by importance):
  1) Foundation (sub/bass)
  2) Pulse (kick/snare/hats)
  3) Harmony bed
  4) Lead
  5) Counter
  6) Texture
  7) Impact
  8) Air
- ENTRY/EXIT EVENTS:
  - where layers appear/disappear
- “ONE NEW THING” RULE (optional):
  - per section add/remove one core element to create motion

Rule:
- LSM ensures arrangement movement and payoff.

---

## REQUIRED ARTIFACT C: REGISTER PLAN (RP)

### RP SCHEMA (CANON)

- RP_ID:
- AS_ID:

Register allocation:
- LOW (sub/bass):
  - which layer owns it
- LOW-MID:
  - avoid crowding; list allowed layers
- MID:
  - where harmony lives
- HIGH:
  - lead sparkle rules
- AIR:
  - optional; keep minimal if vocal clarity is priority

Conflict rules:
- “NO DOUBLE OWNERSHIP”:
  - only one primary owner per register band at key moments
- “VOCAL POCKET” (if vocal):
  - which layers must thin out under vocal lines
- “CHORD VOICING HEIGHT”:
  - chord instruments stay above mud zone

Rule:
- RP is the main anti-mud system.

---

## REQUIRED ARTIFACT D: INSTRUMENT ROLE LIBRARY (IRL)

### IRL SCHEMA (CANON)

- IRL_ID:
- STYLE_ID:

Instruments list:
For each instrument/layer:
- NAME:
- ROLE (primary):
- REGISTER:
- USE CASE:
  - verse/chorus/bridge
- MOTION:
  - static/pulsing/arpeggio
- “DO NOT”:
  - conflicts, overuse, bad combos

Rule:
- IRL enforces consistency and prevents layer spam.

---

## REQUIRED ARTIFACT E: TRANSITION DEVICE MAP (TDM)

### TDM SCHEMA (CANON)

For each transition (V→C, C→V, C→B, etc.):
- TRANSITION ID:
- FROM SECTION:
- TO SECTION:
- DEVICE TYPE:
  - fill | drum break | stop | riser | downlifter | stinger | drop | reverse
- LENGTH:
  - short/med/long
- IMPACT LEVEL (0–10):
- SYNC MARKER (if scene):
  - link to SMS marker
- “DO NOT”:
  - avoid cliché devices if style forbids

Rule:
- TDM makes transitions intentional and repeatable.

---

## REQUIRED ARTIFACT F: TIMBRE HOOK BRIEF (THB)

### THB SCHEMA (CANON)

- THB_ID:
- STYLE_ID / PROJECT_ID:

Hook timbre:
- PRIMARY TIMBRE SIGNATURE:
  - describe sound in plain terms (texture, brightness, grit)
- SECONDARY SIGNATURE (optional):
- WHERE IT APPEARS:
  - chorus only / throughout / intro+chorus
- REPEAT POLICY:
  - must recur for identity (yes/no)
- “DO NOT”:
  - avoid timbre drift (different synth families etc.)

Rule:
- THB is the audio version of a “logo”.

---

## REQUIRED ARTIFACT G: ARRANGEMENT QC GATES (AQG)

### AQG SCHEMA (CANON)

Gates:
1) Role clarity gate:
   - every layer has a job (IRL)
2) Lead pocket gate:
   - lead/vocal has space (RP)
3) Low-end gate:
   - bass+kick conflicts prevented by rules
4) Density curve gate:
   - LSM matches energy curve by sections
5) Timbre identity gate:
   - THB recurs; no drift
6) Transition design gate:
   - TDM covers major transitions
7) Mix-ready gate:
   - arrangement doesn’t rely on mix “magic” to be clear
8) Reproducibility gate:
   - AS+LSM+RP+IRL+TDM allow recreation

Rule:
- Fail 2+ gates → revise RP/LSM/IRL.

---

## INCONSISTENCY DETECTOR (HEURISTICS)

Flag if:
- chorus doesn’t feel bigger (no new layer, no register lift)
- vocal/lead is masked by mid layers
- low-end muddy (multiple bass owners)
- too many moving layers at once (listener fatigue)
- transitions feel random or too frequent
- timbre signature changes every section (no identity)

Fix options:
- add “one new thing” in chorus (layer/register)
- thin harmony bed under vocal phrases
- choose one sub owner; make bass sidechain or rhythm separation (policy-level)
- reduce counterlines; keep only one hero counter
- design fewer, stronger transitions
- lock timbre family; reuse signature patch

---

## PROCEDURE (HOW TO RUN)

1) Read HS/MS/RS + section energy plan
2) Choose timbre identity (THB) and lead carrier
3) Build IRL for project/style
4) Build register plan (RP) with lead pocket + low-end rules
5) Create LSM per section (roles + entry/exit motion)
6) Design transitions (TDM) for major section moves
7) Output AS and run AQG gates
8) Hand off to sound design (10) and mix/master (13)

---

## QC CHECKLIST (MANDATORY)

- is lead pocket protected?
- does each layer have a role?
- low-end managed (one owner)?
- chorus payoff exists (density/register/timbre)?
- timbre hook recurs?
- transitions designed and not cliché?
- arrangement is mix-ready by design?
- spec reproducible?

---

## VALIDATION RULES

- AV1: Arrangement supports harmony, melody, rhythm, and section energy.
- AV2: Lead is always readable (pocket protected).
- AV3: Layer roles are clear; no redundant layers.
- AV4: Register plan prevents mud and masking.
- AV5: Timbre hook provides identity and recurs intentionally.
- AV6: Transitions are designed and support payoff cadence.
- AV7: Arrangement is mix-ready and reproducible.

---

OWNER: Universe Engine
LOCK: FIXED
