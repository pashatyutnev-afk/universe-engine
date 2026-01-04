# Melody / Hook Engine
FILE: 04__MELODY_HOOK_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 09_SOUND_MUSIC_ENGINES
CLASS: PRODUCTION (L3)
LEVEL: L3
STATUS: ACTIVE
VERSION: 1.0
ROLE: Defines reproducible melody and hook design logic (recognizability, contour, anchor notes, rhythmic identity, repetition-with-variation, hook payoff cadence, and harmony compatibility); produces Melody Specs, Hook Maps, Motif-to-Melody Rules, Variation Plans, and QC Gates for songs and cues

---

## PURPOSE

Мелодия — это “лицо музыки”.
Хук — это “крючок узнавания”, который держит внимание.

Движок фиксирует:
- как делать мелодию узнаваемой
- как проектировать хук и частоту его выплат
- как управлять повтором и вариациями
- как держать совместимость с гармонией и ритмом
- как сохранять стиль мира/проекта

---

## NON-GOALS

- не выбирает аккорды (это 03)
- не строит форму песни (это 02)
- не оркеструет (это 08)
Он создаёт **мелодический материал и правила его использования**.

---

## MINI-CONTRACT (MANDATORY)

### CONSUMES
- Composition Spec (09.01) + Theme Library/Motif Bank
- Song Structure Spec (09.02) + hook strategy
- Harmony Spec (09.03) + cadence punctuation
- Genre/style locks + vocal constraints (если вокал)
- Target catchiness vs subtlety (low/med/high)

### PRODUCES
- MELODY SPEC (MS) — canonical artifact
- HOOK MAP (HM)
- ANCHOR NOTE SET (ANS)
- CONTOUR PROFILE (CP)
- VARIATION PLAN (VP)
- MOTIF→MELODY RULES (MMR)
- MELODY QC GATES (MQG)

### DEPENDS_ON
- 09.03 Harmony/Chord (support + cadences)
- 09.05 Rhythm/Groove (rhythmic placement)
- 09.02 Song Structure (section jobs & payoff cadence)
- 09.09 Vocal Performance (range/phrasing)

### OUTPUT_TARGET
- Feeds:
  - lyrics engine (07) for singable phrasing
  - arrangement engine (08) for lead doubling/counter-lines
  - music style consistency (11)

---

## CANON TERMS

### HOOK
Короткий узнаваемый фрагмент (мелодический/ритмический/текстовый/тембровый).
В этом движке — **мелодический хук**.

### ANCHOR NOTES
Якорные ноты/ступени, которые “держат” идентичность темы.

### CONTOUR
Форма движения мелодии:
- rising / falling / arch / wave / static

### RHYTHMIC IDENTITY
Ритм мелодии: синкопы/паузы/длины — часто важнее нот.

### VARIATION
Изменение без потери узнаваемости.

### PAYOFF
Возвращение хука так, чтобы слушатель “получил награду”.

---

## CORE RULES (CANON)

### MH1 — Hook identity is designed
Хук должен иметь:
- 1–2 якоря (ANS)
- уникальный контур (CP)
- ритмическую подпись

### MH2 — Hook placement matches structure
Хук не должен появляться “слишком поздно” для песенного формата.
Частота выплат фиксируется в HM.

### MH3 — Repetition with variation
Повторяем хук так, чтобы:
- узнавалось сразу
- но не надоедало
VP обязателен.

### MH4 — Harmony compatibility
Мелодия обязана:
- попадать в harmony targets HS
- уважать cadence punctuation (CM)

### MH5 — Singability (when vocals)
Если вокал:
- диапазон, дыхание, слоги
- фразы не ломают артикуляцию

### MH6 — Style locks apply
Нельзя мелодией вылететь в другой жанр (интервалы/контуры/ритм).

---

## HOOK TYPES (MELODY-LEVEL)

- PEAK HOOK:
  - хук через пик высоты/энергии (обычно припев)
- RHYTHM HOOK:
  - хук держится на ритме/пауза-удар
- INTERVAL HOOK:
  - узнаваемый интервал/скачок (якорь)
- CONTOUR HOOK:
  - узнаваемая траектория (арка/волна)
- CALL-RESPONSE HOOK:
  - вопрос-ответ внутри мелодии

Rule:
- Primary hook type выбирается и фиксируется.

---

## REQUIRED ARTIFACT A: MELODY SPEC (MS)

### MS SCHEMA (CANON)

Header:
- MS_ID:
- CS_ID:
- SSS_ID (if song):
- HS_ID (harmony):
- TRACK/CUE NAME:
- VOCAL:
  - yes/no
- CATCHINESS TARGET:
  - low | med | high
- VERSION:
- STATUS:
  - draft | canon | deprecated

Identity:
- PRIMARY HOOK TYPE:
- ANCHOR NOTE SET (ANS ref):
- CONTOUR PROFILE (CP ref):
- RHYTHMIC IDENTITY NOTES:
- “SIGNATURE MOVE”:
  - one sentence describing the recognizable move

Per section:
- SECTION ID (V/C/B...):
- MELODY ROLE:
  - setup | build | payoff | contrast | resolve
- RANGE TARGET (low/mid/high register):
- “DO NOT”:
  - forbidden intervals/over-ornamentation
- CADENCE NOTE:
  - how line ends relative to cadence type

Rule:
- MS describes identity and section roles, not full notation.

---

## REQUIRED ARTIFACT B: HOOK MAP (HM)

### HM SCHEMA (CANON)

- HM_ID:
- MS_ID:

Hooks list (1–3 recommended):
For each hook:
- HOOK ID:
- HOOK SECTION(S):
- FIRST APPEARANCE:
- PAYOFF FREQUENCY:
  - every chorus | every N sections | special only
- VARIATION POLICY:
  - what changes on returns
- “NO CHEAT” PAYOFF:
  - what counts as real return (not just hint)

Rule:
- HM must guarantee planned payoff cadence.

---

## REQUIRED ARTIFACT C: ANCHOR NOTE SET (ANS)

### ANS SCHEMA (CANON)

- ANS_ID:
- MS_ID:

Anchors:
- ANCHOR 1:
  - degree role (home/peak/tension note)
- ANCHOR 2 (optional):
- “ANCHOR WINDOW”:
  - where anchors must appear (chorus/ending)

Constraints:
- MAX OUTSIDE-PALETTE NOTES:
  - per phrase (if style requires)
- “FORBIDDEN TONES” (if any)

Rule:
- Anchors are identity locks.

---

## REQUIRED ARTIFACT D: CONTOUR PROFILE (CP)

### CP SCHEMA (CANON)

- CP_ID:
- MS_ID:

Profile:
- PRIMARY CONTOUR:
  - rising | falling | arch | wave | static
- PEAK POSITION:
  - early | mid | late (within hook/phrase)
- PHRASE LENGTH TARGET:
  - short | medium | long
- “REST POLICY”:
  - where pauses live (breath/impact)

Rule:
- CP defines shape and pacing of the melodic line.

---

## REQUIRED ARTIFACT E: VARIATION PLAN (VP)

### VP SCHEMA (CANON)

- VP_ID:
- MS_ID:

Variation layers (choose allowed ones):
- rhythmic variation (keep anchors)
- ornamentation (bounded)
- register shift (octave / partial)
- tail change (ending notes)
- call-response add-on
- harmony-aware variation (sync with reharm RG)

Per hook return:
- RETURN #1:
  - baseline (no change)
- RETURN #2:
  - change (one layer)
- RETURN #3:
  - intensify or strip
- FINAL:
  - strongest payoff (or intentional subversion if allowed)

Rule:
- VP prevents copy-paste choruses.

---

## REQUIRED ARTIFACT F: MOTIF → MELODY RULES (MMR)

### MMR SCHEMA (CANON)

- MMR_ID:
- TL/MB refs:

Rules:
- which motifs can become melodic hooks
- how motif transforms into longer phrase
- what must remain constant (interval/rhythm/timbre)
- what can change (register, tail, harmony)

Rule:
- Maintains continuity with Theme/Motif systems.

---

## REQUIRED ARTIFACT G: MELODY QC GATES (MQG)

### MQG SCHEMA (CANON)

Gates:
1) Recognizability gate:
   - hook is identifiable within seconds
2) Anchor gate:
   - anchors exist and recur by HM rules
3) Contour gate:
   - CP supports purpose and isn’t random
4) Payoff cadence gate:
   - HM ensures returns; no late payoff
5) Variation gate:
   - VP planned; no copy-paste fatigue
6) Harmony gate:
   - melody respects HS cadences and palette
7) Singability gate (if vocal):
   - phrasing and range feasible
8) Style lock gate:
   - interval/rhythm language fits style
9) Reproducibility gate:
   - MS/HM/ANS/CP/VP allow recreation

Rule:
- Fail 2+ gates → rewrite hook identity.

---

## INCONSISTENCY DETECTOR (HEURISTICS)

Flag if:
- chorus doesn’t feel like payoff (melody too flat)
- hook has no anchors (random line)
- hook appears too late or too rarely
- too many ornaments; identity lost
- melody fights harmony cadence endings
- vocal line is unsingable (no breath, too high)
- variation breaks recognizability

Fix options:
- choose 1–2 anchors and repeat them
- simplify contour; design peak position
- introduce hook earlier (pre-chorus/tag)
- reduce ornamentation; keep signature move
- align phrase endings to cadence type
- adjust range; add breaths and rests
- plan variation via VP layers, not rewrites

---

## PROCEDURE (HOW TO RUN)

1) Read CS purpose + SSS hook strategy + HS cadences
2) Select primary hook type
3) Define anchors (ANS) and contour (CP)
4) Build hook map (HM) with payoff cadence
5) Define section roles (setup/build/payoff)
6) Write variation plan (VP)
7) Add motif continuity rules (MMR) if needed
8) Run MQG gates and iterate
9) Hand off to rhythm/arrangement/vocal engines

---

## QC CHECKLIST (MANDATORY)

- hook type chosen and justified?
- anchors defined and scheduled?
- contour profile defined (peak/phrasing)?
- hook map ensures payoff cadence?
- variation plan prevents fatigue?
- harmony compatibility passes cadences/palette?
- singability ok (if vocal)?
- style locks respected?

---

## VALIDATION RULES

- MHV1: Hook is recognizable and paid repeatedly.
- MHV2: Anchors and contour lock identity.
- MHV3: Variation preserves recognizability while avoiding fatigue.
- MHV4: Melody fits harmony cadences and style palette.
- MHV5: Vocal melody is feasible when applicable.
- MHV6: Spec is reproducible from artifacts.

---

OWNER: Universe Engine
LOCK: FIXED
