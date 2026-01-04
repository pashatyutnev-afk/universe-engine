# Sound Design Engine
FILE: 10__SOUND_DESIGN_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 09_SOUND_MUSIC_ENGINES
CLASS: PRODUCTION (L3)
LEVEL: L3
STATUS: ACTIVE
VERSION: 1.0
ROLE: Defines reproducible music-integrated sound design logic (sound palette, impacts, transitions FX, textures, ear-candy, motif sounds, and scene-sync FX) while preserving style consistency and mix headroom; produces Sound Design Specs, Palette Libraries, FX Maps, Impact/Transition Sets, Motif Sound Briefs, and QC Gates aligned with arrangement, editing sync, and mix/master requirements

---

## PURPOSE

Саунд-дизайн в музыке — это “кино внутри трека”:
- impacts и stingers
- whooshes, risers, downlifters
- текстуры и “воздух”
- ear-candy детали
- звуковые мотивы (sound motifs), как “аудио-символы”

Движок фиксирует:
- палитру звуков (что разрешено/запрещено)
- где и зачем применяются FX
- правила громкости/места/чистоты
- синхру с переходами/монтажом (если нужно)

---

## NON-GOALS

- не заменяет аранжировку (08)
- не делает финальный микс/мастер (13)
- не пишет музыку (03/04/05)
Он добавляет **контролируемые звуковые артефакты**.

---

## MINI-CONTRACT (MANDATORY)

### CONSUMES
- Arrangement Spec (09.08): transitions, layer stacks, pockets
- Rhythm Spec (09.05): accent grid + hit points
- Song Structure Spec (09.02): where payoff/turns happen
- Music-to-Scene needs (09.12) if scene sync
- Style consistency locks (09.11)
- Mix target constraints (09.13): headroom, clarity

### PRODUCES
- SOUND DESIGN SPEC (SDS) — canonical artifact
- SOUND PALETTE LIBRARY (SPL)
- FX MAP (FXM)
- IMPACT SET (IS)
- TRANSITION FX SET (TFS)
- MOTIF SOUND BRIEF (MSB)
- SOUND DESIGN QC GATES (SDG)

### DEPENDS_ON
- 09.08 Arrangement (space and transitions)
- 09.05 Rhythm (hit placement)
- 09.13 Mix/Master (headroom and masking constraints)

### OUTPUT_TARGET
- Feeds:
  - mix decisions (13)
  - music-to-scene (12)
  - style consistency (11)

---

## CANON TERMS

### SOUND PALETTE
Набор разрешённых “семейств” звуков (текстуры, механика, органика).

### IMPACT
Сильный одноразовый удар (hit/stinger).

### TRANSITION FX
FX, который объясняет переход:
- riser, downlifter, whoosh, reverse, sweep

### EAR-CANDY
Мелкие детали, которые дают “дорого” и “живое”.

### MOTIF SOUND
Повторяющийся звуковой знак, как логотип.

### HEADROOM
Запас громкости/плотности, чтобы микс не клиппил и не давился.

---

## CORE RULES (CANON)

### SD1 — FX serves structure
FX всегда имеет функцию:
- переход
- усиление кульминации
- подчёркивание хука
- синхра с монтажом/ивентом

### SD2 — Palette is locked
SPL фиксирует:
- allowed families
- forbidden families
Без этого начинается звуковой “зоопарк”.

### SD3 — Do not mask the lead
FX не должны маскировать:
- вокал/лид
- главный ритмический удар (kick/snare) в ключевых местах

### SD4 — Impacts are bounded
IS: impacts используются дозированно.
Слишком много → усталость и потеря значения.

### SD5 — Ear-candy is sparse and intentional
Ear-candy не должен:
- отвлекать
- повторяться хаотично
- забивать хук

### SD6 — Transition FX map is explicit
TFS обязателен для крупных переходов.

### SD7 — Mix-ready constraints exist
SDS содержит правила:
- “оставь место”
- “не лезь в pocket”
- “не перегружай верх/низ”

---

## FX CATEGORIES (CANON)

- IMPACTS: hits, slams, booms, stingers
- WHOOSHES: sweeps, swishes, passes
- RISERS: noise risers, tonal risers, pitch risers
- DOWNLIFTERS: falls, drops, tails
- REVERSALS: reverse cymbal/impact
- TEXTURES: drones, noise beds, vinyl, grit
- EAR-CANDY: glitches, sparkles, ticks
- DIEGETIC-LIKE (optional): footsteps, radio, machine (only if style allows)

Rule:
- Diegetic-like allowed only if style lock permits.

---

## REQUIRED ARTIFACT A: SOUND DESIGN SPEC (SDS)

### SDS SCHEMA (CANON)

Header:
- SDS_ID:
- AS_ID:
- RS_ID:
- SSS_ID:
- STYLE LOCK:
- VERSION:
- STATUS:
  - draft | canon | deprecated

Palette:
- SOUND PALETTE LIBRARY (SPL ref)
- FORBIDDEN LIST (explicit):
  - e.g., “cartoon boings”, “epic trailer braams” if forbidden

Usage rules:
- LEAD SAFE ZONES:
  - where FX must be minimal (hook lines)
- IMPACT BUDGET:
  - max impacts per minute or per section (policy)
- TRANSITION FX POLICY:
  - what devices allowed
- EAR-CANDY POLICY:
  - where allowed (intro only / between phrases)

Placement:
- FX MAP (FXM ref)
- IMPACT SET (IS ref)
- TRANSITION FX SET (TFS ref)

Motifs:
- MOTIF SOUND BRIEF (MSB ref) if used

Mix constraints:
- “POCKET AVOIDANCE”:
  - avoid mid band if vocal heavy (policy-level)
- “LOW-END PROHIBITION”:
  - FX must not add sub unless explicitly intended
- “TOP-END FATIGUE RULE”:
  - avoid constant harsh highs

Rule:
- SDS must be sufficient to recreate sound design approach.

---

## REQUIRED ARTIFACT B: SOUND PALETTE LIBRARY (SPL)

### SPL SCHEMA (CANON)

- SPL_ID:
- STYLE_ID / PROJECT_ID:

Allowed families:
- TEXTURE FAMILY:
- IMPACT FAMILY:
- WHOOSH FAMILY:
- TONAL FX FAMILY:
- EAR-CANDY FAMILY:

Forbidden families:
- list explicit (style-specific)

Texture policy:
- clean | gritty | mixed
- analog | digital | hybrid

Rule:
- SPL is the boundary that prevents style drift.

---

## REQUIRED ARTIFACT C: FX MAP (FXM)

### FXM SCHEMA (CANON)

For each section and key point:
- SECTION ID:
- FX EVENT ID:
- TYPE:
  - impact / riser / whoosh / texture / ear-candy
- PURPOSE:
  - transition / emphasis / tension / payoff / sync
- TIMING:
  - bar/beat (or timestamp)
- INTENSITY (0–10):
- SAFE ZONE CHECK:
  - does it avoid lead pocket? yes/no
- NOTES:
  - e.g., “reverse into chorus drop”

Rule:
- FXM is the placement blueprint.

---

## REQUIRED ARTIFACT D: IMPACT SET (IS)

### IS SCHEMA (CANON)

- IS_ID:
- STYLE_ID:

Impact types:
For each impact:
- IMPACT ID:
- CHARACTER:
  - soft thump | hard slam | metallic | organic | sub boom
- LENGTH:
  - short/med/long
- USE CASE:
  - drop / reveal / cut / ending
- DO NOT:
  - conflicts (e.g., “no sub under vocal”)

Rule:
- IS makes impacts consistent across tracks/scenes.

---

## REQUIRED ARTIFACT E: TRANSITION FX SET (TFS)

### TFS SCHEMA (CANON)

- TFS_ID:
- STYLE_ID:

Devices:
For each device:
- DEVICE ID:
- TYPE:
  - riser / downlifter / whoosh / reverse
- CHARACTER:
  - noise | tonal | hybrid
- LENGTH:
  - short/med/long
- USE CASE:
  - verse→chorus / chorus→verse / bridge→final
- DO NOT:
  - forbidden cliché devices

Rule:
- TFS standardizes transitions and avoids randomness.

---

## REQUIRED ARTIFACT F: MOTIF SOUND BRIEF (MSB)

### MSB SCHEMA (CANON)

- MSB_ID:
- PROJECT_ID:

Motif:
- NAME:
- FUNCTION:
  - identity tag | narrative symbol | warning | nostalgia
- SOUND CHARACTER:
  - describe in plain terms
- PLACEMENT RULE:
  - where it appears (intro+chorus tags etc.)
- REPETITION POLICY:
  - must recur N times (policy)
- DO NOT:
  - overuse; avoid masking hook

Rule:
- MSB is a sound “logo” with discipline.

---

## REQUIRED ARTIFACT G: SOUND DESIGN QC GATES (SDG)

### SDG SCHEMA (CANON)

Gates:
1) Purpose gate:
   - each FX event has a job (SD1)
2) Palette lock gate:
   - all FX belong to SPL allowed families
3) Lead clarity gate:
   - FX do not mask lead/vocal in safe zones
4) Budget gate:
   - impacts and ear-candy not overused
5) Transition coverage gate:
   - major transitions have designed FX (TFS)
6) Style consistency gate:
   - FX character matches style locks (09.11)
7) Mix-ready gate:
   - headroom and pocket rules respected
8) Reproducibility gate:
   - SDS+SPL+FXM+IS+TFS(+MSB) allow recreation

Rule:
- Fail 2+ gates → revise palette/placement/budget.

---

## INCONSISTENCY DETECTOR (HEURISTICS)

Flag if:
- every transition has a big riser (fatigue)
- impacts show up without payoff moments
- ear-candy competes with hook
- FX palette changes wildly between sections
- harsh top-end constant hiss/sweeps
- sub booms everywhere (kills mix and bass clarity)

Fix options:
- reduce FX to “few strong” instead of many
- save big impacts for payoff/cuts only
- keep ear-candy between vocal phrases
- lock palette families and reuse characters
- enforce top-end fatigue rule
- restrict low-end FX to intentional hits only

---

## PROCEDURE (HOW TO RUN)

1) Read structure + arrangement transitions + rhythm hit points
2) Lock palette (SPL) and forbidden list
3) Decide impact budget and safe zones
4) Build TFS for major transitions
5) Build IS for payoff hits
6) Place FX via FXM (with purpose + intensity)
7) Optional: define motif sounds (MSB)
8) Output SDS and run SDG gates
9) Hand off to mix/master constraints

---

## QC CHECKLIST (MANDATORY)

- palette locked and enforced?
- every FX has a purpose?
- lead safe zones respected?
- impacts budget controlled?
- transitions designed (not spam)?
- ear-candy sparse and placed in gaps?
- mix-ready constraints respected?
- reproducible artifacts exist?

---

## VALIDATION RULES

- SDV1: Sound design supports structure and emotion, not random decoration.
- SDV2: Palette is consistent and style-locked.
- SDV3: Lead clarity is protected (no masking in safe zones).
- SDV4: Impacts and ear-candy are bounded to avoid fatigue.
- SDV5: Transitions are intentional and consistent.
- SDV6: Mix-ready constraints preserve headroom and space.
- SDV7: Spec is reproducible and usable.

---

OWNER: Universe Engine
LOCK: FIXED
