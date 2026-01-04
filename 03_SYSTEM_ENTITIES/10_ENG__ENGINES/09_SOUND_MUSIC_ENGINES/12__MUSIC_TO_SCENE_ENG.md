# Music To Scene Engine
FILE: 12__MUSIC_TO_SCENE_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 09_SOUND_MUSIC_ENGINES
CLASS: PRODUCTION (L3)
LEVEL: L3
STATUS: ACTIVE
VERSION: 1.0
ROLE: Defines reproducible logic for scoring music to scene (beat mapping, emotional timeline, sync markers, hit points, cut-aware structure, dialogue-safe planning, and adaptive variations); produces Music-To-Scene Specs, Sync Marker Sheets, Emotional Time Maps, Hit Point Lists, Cue Structure Maps, and QC Gates aligned with editing/montage and audio production requirements

---

## PURPOSE

Музыка к сцене — это “точное попадание во время и смысл”.
Движок фиксирует:
- эмоциональную карту по времени (что чувствует зритель когда)
- где монтажные/сюжетные точки (sync markers)
- hit points (удары/входы/переходы)
- структуру кью (cue) по таймкоду
- требования “не мешать диалогу”
- варианты/адаптации (если игра/интерактив)

Цель: сделать спецификацию, по которой можно **собрать** музыку к сцене без гадания.

---

## NON-GOALS

- не заменяет монтаж (08_KP/07 Editing & Montage)
- не заменяет звук-пост (08_KP/08 Sound production layer)
- не пишет конкретные аккорды/мелодию (09.03/09.04)
Он задаёт **каркас привязки музыки к сцене**.

---

## MINI-CONTRACT (MANDATORY)

### CONSUMES
- Scene spec / narrative beats (02-domain narrative engines)
- Shot list & montage rhythm (08_KP: 03 Camera, 07 Editing)
- Audio production plan (08_KP: 08 Sound & Music production layer)
- Platform constraints (07 Production formats)
- Style locks (09.11 Music Style Consistency)
- Dialogue needs (if any): priority zones

### PRODUCES
- MUSIC-TO-SCENE SPEC (MTS) — canonical artifact
- SYNC MARKER SHEET (SMS)
- EMOTIONAL TIME MAP (ETM)
- HIT POINT LIST (HPL)
- CUE STRUCTURE MAP (CSM)
- DIALOGUE SAFE PLAN (DSP)
- VARIATION PLAN (VP) (optional for interactive)
- MUSIC-TO-SCENE QC GATES (MQG)

### DEPENDS_ON
- 08_KP/07 Editing & Montage (timing + cut rhythm)
- 09.11 Style consistency (don’t drift)
- 09.08 Arrangement + 09.10 Sound design (hit point tools)
- 09.13 Mix/Master (dialogue safety constraints)

### OUTPUT_TARGET
- Feeds:
  - composition decisions (09.01–09.05)
  - arrangement transitions (09.08)
  - sound design hits (09.10)
  - final mix/master decisions (09.13)

---

## CANON TERMS

### CUE
Музыкальный кусок, который покрывает сцену/фрагмент.

### SYNC MARKER
Точка, куда музыка должна попасть: cut, reveal, удар, взгляд, титр.

### HIT POINT
Маркер “подчеркнуть событие” (impact, chord change, drop).

### ETM
Emotional Time Map — эмоциональная функция во времени.

### DIALOGUE SAFE ZONE
Интервал, где музыка обязана быть “внизу” и не конкурировать.

### CUT-AWARE
Структура учитывает монтажные склейки и ритм планов.

---

## CORE RULES (CANON)

### M1 — Music serves scene meaning
Музыка отвечает смыслу сцены, не “красивости”.

### M2 — Markers first, notes second
Сначала SMS/ETM/HPL, потом композиция.

### M3 — Hit points are bounded
HPL не превращается в “удар каждые 2 секунды”.
Есть бюджет hit points.

### M4 — Dialogue is sacred when present
DSP обязателен, если есть речь:
- музыка не маскирует диалог
- события подчёркиваются вне речевых пиков

### M5 — Cut-aware structure
CSM обязателен:
- совпадение музыкальных фаз с монтажными фазами
- “payoff” попадает туда, где сцена этого требует

### M6 — Style locks apply
Стиль-локи (09.11) обязательны: сцена не оправдывает дрейф.

### M7 — Reproducibility
MTS должен позволить другому композитору/продюсеру повторить схему.

---

## REQUIRED ARTIFACT A: MUSIC-TO-SCENE SPEC (MTS)

### MTS SCHEMA (CANON)

Header:
- MTS_ID:
- SCENE_ID:
- EDIT_ID / CUT_VERSION:
- STYLE_ID (09.11 MSB_ID):
- FORMAT TARGET:
  - film/series/youtube/game
- DURATION (timecode):
- VERSION:
- STATUS:
  - draft | canon | deprecated

Global intent:
- SCENE PURPOSE (one line):
- EMOTION ARC (one line):
- MUSIC ROLE:
  - drive | underscore | suspense | reveal | grief | triumph | none
- DIALOGUE PRESENT:
  - yes/no
- “DO NOT”:
  - forbidden emotions/gestures (e.g., no heroism)

Maps:
- SYNC MARKER SHEET (SMS ref)
- EMOTIONAL TIME MAP (ETM ref)
- HIT POINT LIST (HPL ref)
- CUE STRUCTURE MAP (CSM ref)
- DIALOGUE SAFE PLAN (DSP ref if dialogue)
- VARIATION PLAN (VP ref if interactive)

Budgets:
- HIT POINT BUDGET:
  - max hits or max per minute
- ENERGY CAP:
  - avoid overpowering scene

Rule:
- MTS is the master document for the cue.

---

## REQUIRED ARTIFACT B: SYNC MARKER SHEET (SMS)

### SMS SCHEMA (CANON)

For each marker:
- MARKER ID:
- TIME (timecode or timestamp):
- TYPE:
  - cut | reveal | action hit | gaze | title | door slam | etc.
- PRIORITY:
  - P1 (must hit) / P2 (nice) / P3 (optional)
- MUSIC ACTION:
  - chord change | impact | drop | entry | silence | swell
- NOTE:
  - what happens in scene

Rule:
- P1 markers are non-negotiable.

---

## REQUIRED ARTIFACT C: EMOTIONAL TIME MAP (ETM)

### ETM SCHEMA (CANON)

Timeline segments:
- START–END:
- EMOTION:
  - fear, awe, hope, tension, calm, etc.
- INTENSITY (0–10):
- COLOR NOTE (optional):
  - warm/cold emotional color
- MUSIC GESTURE:
  - sustain, pulse, build, release, stop

Rule:
- ETM prevents “ровную” музыку без драматургии.

---

## REQUIRED ARTIFACT D: HIT POINT LIST (HPL)

### HPL SCHEMA (CANON)

For each hit:
- HIT ID:
- TIME:
- PURPOSE:
  - emphasize event / transition / payoff
- INTENSITY (0–10):
- TOOL TYPE:
  - arrangement change | impact | drum fill | silence | motif
- SAFE CHECK:
  - does not fight dialogue? yes/no
- BUDGET NOTE:
  - counts against hit budget

Rule:
- HPL must be sparse enough to keep meaning.

---

## REQUIRED ARTIFACT E: CUE STRUCTURE MAP (CSM)

### CSM SCHEMA (CANON)

- CUE SECTIONS (ordered):
For each cue section:
- NAME:
  - intro / bed / build / peak / tail / button
- START–END:
- ENERGY (0–10):
- HARMONIC STATE:
  - stable / tension / resolve (no chord specifics required)
- RHYTHM MODE:
  - static / pulse / drive
- TRANSITION OUT:
  - cut / tail / stinger / silence

Rule:
- CSM aligns musical structure to editorial structure.

---

## REQUIRED ARTIFACT F: DIALOGUE SAFE PLAN (DSP)

### DSP SCHEMA (CANON)

- DIALOGUE PRIORITY:
  - high/med/low
- SAFE ZONES:
  - list time ranges where music must be minimal
- “NO LEAD COMPETITION” RULE:
  - no lead synth lines under dialogue peaks
- FREQUENCY/SPACE POLICY (high-level):
  - keep midrange sparse; reduce busy textures
- EMPHASIS STRATEGY:
  - emphasize between lines, not during

Rule:
- DSP protects intelligibility and narrative.

---

## OPTIONAL ARTIFACT G: VARIATION PLAN (VP) — INTERACTIVE

### VP SCHEMA (CANON)

Variation types:
- intensity layers (low/med/high)
- adaptive stems (drums/bass/pads)
- transition stingers
- loop points

Rules:
- LOOP POINTS:
  - where cue can loop seamlessly
- EXIT POINTS:
  - safe cut points
- STATE RULES:
  - when to escalate/de-escalate

Rule:
- VP makes cue game-ready.

---

## REQUIRED ARTIFACT H: MUSIC-TO-SCENE QC GATES (MQG)

### MQG SCHEMA (CANON)

Gates:
1) Meaning gate:
   - music role matches scene purpose and emotion
2) Marker gate:
   - P1 markers are hit reliably
3) ETM gate:
   - emotional curve matches scene arc
4) Hit budget gate:
   - hits are bounded and meaningful
5) Cut-aware gate:
   - CSM respects montage rhythm
6) Dialogue gate (if dialogue):
   - DSP rules obeyed; speech intelligible
7) Style lock gate:
   - no style drift vs 09.11
8) Reproducibility gate:
   - MTS artifacts allow rebuild

Rule:
- Fail 2+ gates → revise maps or budgets.

---

## INCONSISTENCY DETECTOR (HEURISTICS)

Flag if:
- music peaks before the scene peaks
- too many hits (everything becomes “important”)
- dialogue feels buried or tense to understand
- cue sections ignore cut rhythm (cuts feel “off”)
- emotion mismatch (sad scene, heroic music)
- style drift (sudden genre change)

Fix options:
- move peak later; align with ETM intensity curve
- reduce HPL; keep only P1/P2 hits
- thin arrangement in DSP zones; remove busy leads
- match cue section boundaries to cut clusters
- rewrite MTS intent; adjust music role
- enforce style locks; keep palette consistent

---

## PROCEDURE (HOW TO RUN)

1) Read scene beat sheet + edit timeline
2) Create SMS (markers) with P1/P2/P3
3) Create ETM (emotion timeline) with intensities
4) Select hit budget and define HPL
5) Build CSM (cue structure) aligned to montage rhythm
6) If dialogue: create DSP safe zones
7) Optional: define VP for interactive
8) Compile MTS and run MQG gates
9) Hand off to composition/arrangement/sound design

---

## QC CHECKLIST (MANDATORY)

- markers first, notes second done?
- ETM matches scene arc?
- hit budget respected?
- cue structure matches cut rhythm?
- dialogue protected if present?
- style locks obeyed?
- reproducible spec complete?

---

## VALIDATION RULES

- MTV1: Music supports scene meaning and emotional arc.
- MTV2: Sync markers (P1) are hit consistently.
- MTV3: Hit points are meaningful and bounded.
- MTV4: Cue structure respects montage rhythm and transitions.
- MTV5: Dialogue intelligibility is protected when present.
- MTV6: Style consistency holds across cues and tracks.
- MTV7: Spec is reproducible and actionable.

---

OWNER: Universe Engine
LOCK: FIXED
