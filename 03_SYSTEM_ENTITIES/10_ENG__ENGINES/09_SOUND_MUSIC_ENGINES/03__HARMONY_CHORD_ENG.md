# Harmony / Chord Engine
FILE: 03__HARMONY_CHORD_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 09_SOUND_MUSIC_ENGINES
CLASS: PRODUCTION (L3)
LEVEL: L3
STATUS: ACTIVE
VERSION: 1.0
ROLE: Defines reproducible harmony and chord logic (progression selection, tension/release control, modal palette, cadences, reharmonization rules, and voice-leading constraints) for songs and cues; produces Harmony Specs, Progression Libraries, Cadence Maps, Reharm Guides, and QC Gates aligned with genre/style locks and scene intent

---

## PURPOSE

Гармония — это “гравитация эмоций”.
Движок задаёт:
- как выбирать аккорды и прогрессии под цель
- как управлять напряжением/разрядкой
- какие каденции и повороты допустимы
- как делать ре-гармонизацию (вариации) без потери идентичности
- минимальные правила голосоведения (чтобы не было грязи)

---

## NON-GOALS

- не пишет мелодию/хук (это 04)
- не делает ритм (это 05)
- не оркеструет (это 08)
Он фиксирует **гармоническую структуру**.

---

## MINI-CONTRACT (MANDATORY)

### CONSUMES
- Composition Spec (09.01): purpose, tension plan
- Song Structure Spec (09.02) or cue form
- Genre/style locks (allowed harmony language)
- Theme/motif identity constraints (TL/MB)
- Target complexity (low/med/high)

### PRODUCES
- HARMONY SPEC (HS) — canonical artifact
- PROGRESSION LIBRARY (PL)
- CADENCE MAP (CM)
- MODAL PALETTE (MP)
- REHARMONIZATION GUIDE (RG)
- VOICE-LEADING RULES (VLR)
- HARMONY QC GATES (HQG)

### DEPENDS_ON
- 09_SOUND_MUSIC_ENGINES/01__MUSIC_COMPOSITION_ENG.md
- 09_SOUND_MUSIC_ENGINES/02__SONG_STRUCTURE_ENG.md
- 06_GENRE_STYLE_ENGINES (tone/mood)
- 09_SOUND_MUSIC_ENGINES/08__ARRANGEMENT_INSTRUMENTATION_ENG.md (voicing implementation)

### OUTPUT_TARGET
- Feeds:
  - melody writing (04)
  - arrangement voicings (08)
  - vocal harmonies (09)
  - mix decisions indirectly (13)

---

## CANON TERMS

### PROGRESSION
Последовательность аккордов (по тактам/секциям).

### CADENCE
Пунктуация гармонии: “точка/запятая/вопрос”.

### MODAL PALETTE
Набор ладовых красок (major/minor/dorian/phrygian и т.д.).

### FUNCTIONALITY
Роли аккордов:
- stable / move / pull / resolve (без академ-воды)

### REHARM
Изменение аккордов при сохранении мелодии/идентичности.

### VOICE-LEADING
Как голоса перемещаются между аккордами (минимизация “скачков” и грязи).

---

## CORE RULES (CANON)

### H1 — Harmony serves purpose + tension plan
Гармония обязана соответствовать CS/TRP:
- где строим
- где отпускаем

### H2 — Palette is bounded
Есть допустимый язык гармонии (MP).
Запрещено “всё подряд”.

### H3 — Cadences are designed
Каждая секция должна иметь:
- каденционную функцию (CM)

### H4 — Progression library prevents chaos
Система хранит PL:
- чтобы сохранять стиль
- чтобы не изобретать каждый раз с нуля

### H5 — Reharm must preserve identity
RG фиксирует:
- что можно менять
- что ломает тему

### H6 — Voice-leading cleanliness floor
Минимальные VLR правила обязательны, даже в “простом” жанре.

---

## HARMONY LANGUAGE (ABSTRACTED FUNCTION MODEL)

To avoid академ-споры, используем 4 роли:

- STABLE (S): опора, “дом”
- MOVE (M): движение, смена цвета
- PULL (P): тянет к разрядке
- RESOLVE (R): разрядка/точка

Rule:
- Любая секция описывается цепочкой ролей (S→M→P→R).
- Это переносимо между жанрами.

---

## REQUIRED ARTIFACT A: HARMONY SPEC (HS)

### HS SCHEMA (CANON)

Header:
- HS_ID:
- CS_ID:
- SSS_ID (if song):
- TRACK/CUE NAME:
- KEY CENTER POLICY:
  - fixed | shifts allowed
- COMPLEXITY:
  - low | med | high
- VERSION:
- STATUS:
  - draft | canon | deprecated

Global palette:
- MODAL PALETTE (MP ref):
- CHORD TYPES ALLOWED:
  - triads | 7ths | sus | add9 | extended (bounded)
- DISSONANCE CAP:
  - low/med/high + notes

Per section (I/V/P/C/B/O...):
- SECTION ID:
- FUNCTION PATH:
  - S/M/P/R sequence
- PROGRESSION (roman or degree-based):
- CADENCE TYPE (CM ref):
- TENSION LEVEL (0–10):
- REHARM ALLOWED (RG ref):
- VOICE-LEADING NOTES (VLR ref)

Rule:
- HS must be enough to rebuild harmony without guessing.

---

## REQUIRED ARTIFACT B: PROGRESSION LIBRARY (PL)

### PL SCHEMA (CANON)

- PL_ID:
- PROJECT_ID / STYLE_ID:

For each progression:
- PL_ITEM ID:
- USE CASE:
  - calm | hopeful | dark | lift | chase | tragedy | mystery | triumph
- FUNCTION PATH (S/M/P/R):
- DEGREE PATTERN (1–6 numbers or roman):
- CADENCE ENDING:
  - what it resolves to
- COMPLEXITY LEVEL:
- “DO NOT”:
  - when it breaks style

Rule:
- PL is curated; not a dump.

---

## REQUIRED ARTIFACT C: CADENCE MAP (CM)

### CM SCHEMA (CANON)

- CM_ID:
- STYLE_ID:

Cadence types (abstract):
- FULL STOP (strong resolve)
- SOFT STOP (gentle resolve)
- SUSPENSE (needs continuation)
- QUESTION (opens loop)
- DROP (energy cut / breakdown entry)

For each cadence:
- NAME:
- FUNCTION ROLE:
- TENSION EFFECT:
- TYPICAL SECTION USE:
  - verse end, pre-chorus, chorus end, bridge
- EXAMPLE PATTERN (degree-based, optional)

Rule:
- Cadence choice defines “punctuation”.

---

## REQUIRED ARTIFACT D: MODAL PALETTE (MP)

### MP SCHEMA (CANON)

- MP_ID:
- STYLE_ID:

Palette:
- PRIMARY MODE(S):
- SECONDARY MODE(S):
- BORROWING POLICY:
  - allowed borrowed chords? how far?
- MODULATION POLICY:
  - none | rare | allowed + constraints

Color notes:
- “BRIGHTNESS RANGE” (low–high):
- “DARKNESS RANGE”:
- “WEIRDNESS CAP”:
  - max amount of modal spice before losing genre

Rule:
- MP keeps the world soundtrack coherent.

---

## REQUIRED ARTIFACT E: REHARMONIZATION GUIDE (RG)

### RG SCHEMA (CANON)

- RG_ID:
- STYLE_ID or THEME_ID:

Allowed reharm moves:
- substitute chord types (sus/add/7)
- relative shift (major/minor color)
- passing chord insertion (bounded)
- pedal tone policy
- borrowed chord policy (from MP)

Forbidden reharm moves:
- breaks melody anchor notes
- changes cadence strength incorrectly
- increases dissonance beyond cap
- changes function path (S/M/P/R) unless intentional

Rule:
- Reharm is variation, not identity replacement.

---

## REQUIRED ARTIFACT F: VOICE-LEADING RULES (VLR)

### VLR SCHEMA (CANON)

Minimal cleanliness floor:
- MAX LEAP PER VOICE (guideline):
  - small/medium (text)
- COMMON TONE POLICY:
  - keep shared notes where possible
- PARALLEL MOTION CAP:
  - avoid obvious “block” if style forbids
- CLASH POLICY:
  - seconds allowed? where?
- LOW-END MUD BAN:
  - no dense voicings below threshold region (arrangement-level note)

Rule:
- VLR is simple and enforceable by ear/logic.

---

## REQUIRED ARTIFACT G: HARMONY QC GATES (HQG)

### HQG SCHEMA (CANON)

Gates:
1) Purpose/tension gate:
   - harmony supports TRP anchors
2) Palette gate:
   - MP respected; borrowing bounded
3) Cadence gate:
   - CM punctuation matches section jobs
4) Progression coherence gate:
   - function paths make sense; no random jumps
5) Reharm gate:
   - RG preserves identity where required
6) Voice-leading gate:
   - VLR passes cleanliness floor
7) Reproducibility gate:
   - HS is sufficient to rebuild

Rule:
- Fail 2+ gates → revise HS.

---

## INCONSISTENCY DETECTOR (HEURISTICS)

Flag if:
- chorus doesn’t feel like release (cadence wrong)
- tension peaks in wrong place vs TRP
- harmony changes style abruptly (palette drift)
- dissonance spikes without purpose
- too many borrowed chords (genre breaks)
- low end becomes muddy (voicing ignored)

Fix options:
- adjust cadence types per CM
- re-align progressions to function paths
- reduce borrowing; enforce MP
- move “spice” to bridge only
- simplify voicings or shift register (arrangement)
- keep identity anchors; reharm within RG

---

## PROCEDURE (HOW TO RUN)

1) Read CS purpose + TRP anchors
2) Choose MP (palette) for style/project
3) Select progressions from PL per section jobs
4) Design cadences via CM per section transitions
5) Write HS per section with tension values
6) Define RG and VLR references
7) Run HQG gates
8) Hand off to Melody/Arrangement engines

---

## QC CHECKLIST (MANDATORY)

- HS defines palette + dissonance cap?
- each section has function path + cadence?
- chorus/major sections have correct release punctuation?
- borrowing/modulations follow MP?
- reharm rules preserve identity?
- voice-leading passes cleanliness floor?
- HS is reproducible?

---

## VALIDATION RULES

- HV1: Harmony supports narrative purpose and tension plan.
- HV2: Palette is coherent and style-locked.
- HV3: Cadences provide clear punctuation and payoff.
- HV4: Reharm creates variation without identity loss.
- HV5: Voice-leading remains clean and implementable.
- HV6: Spec is reproducible from HS + PL/CM/MP/RG/VLR.

---

OWNER: Universe Engine
LOCK: FIXED
