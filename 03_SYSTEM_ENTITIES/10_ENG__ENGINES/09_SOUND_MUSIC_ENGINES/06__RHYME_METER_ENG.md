# Rhyme / Meter Engine
FILE: 06__RHYME_METER_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 09_SOUND_MUSIC_ENGINES
CLASS: PRODUCTION (L3)
LEVEL: L3
STATUS: ACTIVE
VERSION: 1.0
ROLE: Defines reproducible rhyme and meter logic for vocal music (rhyme schemes, syllable counts, stress patterns, flow grids, internal rhymes, and cadence alignment) to ensure lyrics fit melody and groove; produces Rhyme/Meter Specs, Flow Maps, Scheme Libraries, Constraint Sets, and QC Gates compatible with song structure, melody, rhythm, and vocal performance engines

---

## PURPOSE

Рифма и метр — это “скелет текста во времени”.
Движок фиксирует:
- схемы рифмовки (концовки + внутренняя рифма)
- метр/слоговку и ударения
- flow-решётку под грув
- правила читаемости и “посадки” под мелодию
- контроль плотности текста (не задыхаться, не мямлить)

---

## NON-GOALS

- не пишет смысл текста (это 07 Lyrics engine)
- не пишет мелодию (это 04)
- не пишет грув (это 05)
Он задаёт **формальные ограничения и посадку текста**.

---

## MINI-CONTRACT (MANDATORY)

### CONSUMES
- Song Structure Spec (09.02): section jobs, lengths
- Melody Spec (09.04): phrasing + rests + peak positions
- Rhythm Spec (09.05): accent grid + microtiming feel
- Vocal constraints (09.09): range/phrasing/breath rules
- Language constraints (RU/EN etc.)

### PRODUCES
- RHYME/METER SPEC (RMS) — canonical artifact
- RHYME SCHEME LIBRARY (RSL)
- FLOW GRID (FG)
- STRESS MAP (SM)
- SYLLABLE BUDGET (SB)
- INTERNAL RHYME POLICY (IRP)
- RHYME/METER QC GATES (RMG)

### DEPENDS_ON
- 09.02 Song Structure (section boundaries)
- 09.04 Melody/Hook (phrase contour)
- 09.05 Rhythm/Groove (accent grid)
- 09.07 Lyrics (semantic content)
- 09.09 Vocal Performance (delivery constraints)

### OUTPUT_TARGET
- Feeds:
  - lyrics drafting (07)
  - vocal recording direction (09)
  - arrangement pockets (08)

---

## CANON TERMS

### RHYME SCHEME
Схема рифм (AA/ABAB/AABB/ABB…).

### END RHYME
Рифма в конце строки/фразы.

### INTERNAL RHYME
Рифма внутри строки (ускоряет flow, повышает плотность).

### METER
Размер/ритм речи: последовательность ударений и слогов.

### STRESS (ACCENT)
Ударная позиция в слове/фразе.

### FLOW GRID
Сетка размещения слогов по долям (куда “садятся” слова).

### CADENCE (VOCAL CADENCE)
Как фраза заканчивается относительно такта/каденции музыки.

---

## CORE RULES (CANON)

### RM1 — Fit first, poetry second
Главное — посадка в музыку:
- слоги, ударения, дыхание
Потом уже “красота”.

### RM2 — Stress must align with musical accents
Ударные слоги должны попадать в:
- сильные доли (AG)
- “важные” мелодические точки (peaks/anchors)

### RM3 — Syllable budget is bounded per section
SB обязателен:
- иначе будет “не влезло / пусто”.

### RM4 — Scheme is consistent within section type
Куплеты держат одну логику рифм,
припев может иметь другую,
но внутри секции хаоса нет.

### RM5 — Internal rhymes are controlled
IRP:
- разрешено только в пределах плотности
- иначе каша и усталость

### RM6 — Cadence matches section punctuation
Концовки строк/фраз должны совпадать с:
- cadence intent (Harmony CM + melody cadence note)

### RM7 — Breathing is planned
Если вокал — SB и FG обязаны содержать:
- breath slots / rest policy

---

## RHYME SCHEME LIBRARY (RSL) — CANON OPTIONS

### RSL SCHEMA
- SCHEME ID:
- USE CASE:
- FEEL:
- NOTES:

Canonical schemes:
1) AA (anthem/simple)
2) AABB (pop clarity)
3) ABAB (story motion)
4) ABB / AAB (hooky punch)
5) AAAA (chant/loop; only if variation exists)
6) XAXA (loose verse; one anchor rhyme)

Rule:
- Scheme chosen must fit style and tempo.
- Faster tempo → simpler end rhymes.

---

## REQUIRED ARTIFACT A: RHYME/METER SPEC (RMS)

### RMS SCHEMA (CANON)

Header:
- RMS_ID:
- SSS_ID:
- MS_ID (melody):
- RS_ID (rhythm):
- LANGUAGE:
- VERSION:
- STATUS:
  - draft | canon | deprecated

Global policy:
- RHYME DENSITY:
  - low | med | high
- INTERNAL RHYME POLICY (IRP ref):
- MULTISYLLABLE RHYME:
  - allowed? yes/no + where
- SLANT RHYME:
  - allowed? yes/no + where

Per section type:
- SECTION TYPE (V/C/B...):
- RHYME SCHEME (RSL ref):
- SYLLABLE BUDGET (SB ref):
- STRESS MAP (SM ref):
- FLOW GRID (FG ref):
- CADENCE NOTE:
  - how lines end relative to bar/cut
- “DO NOT”:
  - forbidden stress patterns / tongue twisters

Rule:
- RMS must be enough to draft lyrics without breaking fit.

---

## REQUIRED ARTIFACT B: SYLLABLE BUDGET (SB)

### SB SCHEMA (CANON)

For each section:
- SECTION ID:
- LINES COUNT (or phrases count):
- SYLLABLES PER LINE (range):
- MAX FAST SYLLABLE RUN:
  - how many quick syllables allowed consecutively
- REST/BREATH SLOTS:
  - required count and placement rule

Rule:
- SB prevents “overstuffed” verses.

---

## REQUIRED ARTIFACT C: STRESS MAP (SM)

### SM SCHEMA (CANON)

For each section:
- SECTION ID:
- STRONG POSITIONS:
  - beats/subdivisions where stressed syllables must land
- WEAK POSITIONS:
  - where unstressed syllables should land
- “STRESS FORBIDDEN ZONES”:
  - positions that break feel (optional)

Rule:
- SM aligns language stress with groove and melody anchors.

---

## REQUIRED ARTIFACT D: FLOW GRID (FG)

### FG SCHEMA (CANON)

For each section:
- SECTION ID:
- GRID TYPE:
  - half-time | straight | swing-like | triplet-like
- SYLLABLE PLACEMENT RULE:
  - dense on offbeats? sparse on strong beats?
- PAUSE POLICY:
  - where pauses are encouraged (impact, breath)
- END-OF-LINE CUTOFF:
  - tight | loose | laid-back

Rule:
- FG makes delivery consistent and repeatable.

---

## REQUIRED ARTIFACT E: INTERNAL RHYME POLICY (IRP)

### IRP SCHEMA (CANON)

Policy levels:
- NONE:
  - no internal rhymes (clean pop)
- LIGHT:
  - 1 internal rhyme per 2 lines
- MED:
  - 1 internal rhyme per line max
- HEAVY:
  - frequent (only if tempo allows)

Constraints:
- Internal rhyme must not collide with hook clarity
- Do not overload chorus (keep payoff clear)
- If heavy in verse → keep chorus simple

Rule:
- IRP prevents rhyme noise and listener fatigue.

---

## REQUIRED ARTIFACT F: RHYME/METER QC GATES (RMG)

### RMG SCHEMA (CANON)

Gates:
1) Fit gate:
   - SB fits melody phrasing and breath
2) Stress alignment gate:
   - stressed syllables land on accent grid
3) Scheme consistency gate:
   - section scheme coherent; not random
4) Cadence gate:
   - line endings match musical punctuation
5) Density gate:
   - rhyme/internal density matches tempo and style
6) Clarity gate:
   - hook lines are not tongue-twistered
7) Reproducibility gate:
   - RMS artifacts allow consistent drafting

Rule:
- Fail 2+ gates → revise SB/SM/FG.

---

## INCONSISTENCY DETECTOR (HEURISTICS)

Flag if:
- stressed syllables land on weak offbeats unintentionally
- too many syllables to sing in phrase window
- rhyme scheme changes every 2 lines (chaos)
- chorus hook line has complex internal rhymes (kills payoff)
- fast tempo + multi-syllable rhymes everywhere (unperformable)
- no breath slots in long phrases

Fix options:
- simplify scheme (AA / AABB)
- reduce syllables; add rests
- move stresses to strong beats
- shift internal rhymes to verse only
- make chorus clearer; keep hook words open vowels
- plan breath points and phrase breaks

---

## PROCEDURE (HOW TO RUN)

1) Read SSS section lengths + melody phrasing + rhythm accent grid
2) Choose rhyme schemes per section type (RSL)
3) Set syllable budgets (SB) + breath slots
4) Define stress maps (SM) aligned to accents and melodic anchors
5) Define flow grids (FG) aligned to groove feel
6) Choose internal rhyme policy (IRP)
7) Output RMS and run RMG gates
8) Hand off to Lyrics engine for semantic writing under constraints

---

## QC CHECKLIST (MANDATORY)

- SB fits melody windows?
- stresses align with accent grid?
- schemes are stable per section?
- chorus hook stays clear?
- internal rhymes controlled by IRP?
- cadence endings match musical punctuation?
- reproducible constraints present?

---

## VALIDATION RULES

- RMV1: Lyrics fit melody and groove without forcing.
- RMV2: Stress alignment supports rhythm and hook clarity.
- RMV3: Rhyme scheme is consistent and style-appropriate.
- RMV4: Density and internal rhymes are controlled to avoid fatigue.
- RMV5: Cadence and breathing are planned.
- RMV6: Spec is reproducible and usable by writers/performers.

---

OWNER: Universe Engine
LOCK: FIXED
