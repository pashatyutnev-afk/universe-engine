# Vocal Performance Engine
FILE: 09__VOCAL_PERFORMANCE_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 09_SOUND_MUSIC_ENGINES
CLASS: PRODUCTION (L3)
LEVEL: L3
STATUS: ACTIVE
VERSION: 1.0
ROLE: Defines reproducible vocal performance logic (persona delivery, tone, range, breath planning, articulation, dynamics, stacking, harmonies, adlibs, and recording takes policy); produces Vocal Specs, Delivery Maps, Breath/Articulation Plans, Harmony/Stack Plans, Take Lists, and QC Gates aligned with melody, rhyme/meter, arrangement, and mix-readiness

---

## PURPOSE

Вокал — это “лицо песни” (и главный носитель смысла).
Движок фиксирует:
- как звучит голос (tone)
- как он подаёт эмоцию
- диапазон и комфортные регистры
- дыхание и артикуляцию
- правила дубляжей/стеков/гармоний
- правила адлибов и украшений
- политику тейков и контроль качества

Цель: чтобы другой исполнитель/продюсер мог повторить **тот же вокальный характер**.

---

## NON-GOALS

- не пишет текст (07)
- не задаёт рифму/метр (06)
- не пишет мелодию (04)
- не делает финальный микс/автотюн настройки (13, но тут — требования к подготовке)
Он задаёт **перформанс-спеку**.

---

## MINI-CONTRACT (MANDATORY)

### CONSUMES
- Lyrics Spec (09.07) + persona lock
- Rhyme/Meter Spec (09.06) + stress maps + breath slots
- Melody Spec (09.04) + hook map + phrasing windows
- Rhythm Spec (09.05) + microtiming feel
- Arrangement Spec (09.08) + lead pocket rules
- Style locks (genre vocal norms)

### PRODUCES
- VOCAL SPEC (VS) — canonical artifact
- DELIVERY MAP (DM)
- BREATH + ARTICULATION PLAN (BAP)
- RANGE + REGISTER PLAN (RRP)
- STACK/HARMONY PLAN (SHP)
- TAKE LIST (TL)
- VOCAL QC GATES (VQG)

### DEPENDS_ON
- 09.04 Melody/Hook
- 09.06 Rhyme/Meter
- 09.08 Arrangement (pockets/space)
- 09.13 Mix/Master (readiness requirements)

### OUTPUT_TARGET
- Feeds:
  - recording direction
  - arrangement tweaks
  - mix/master decisions (clarity vs texture)

---

## CANON TERMS

### DELIVERY
Манера подачи: агрессия/нежность/шёпот/крик и т.д.

### REGISTER
Регистр:
- chest / mixed / head / falsetto (или эквиваленты)

### STACK
Дубли/слои вокала для толщины.

### HARMONY STACK
Гармонические партии (3rds/5ths/octaves).

### ADLIB
Спонтанные фразы/вставки, поддержка эмоции.

### TAKE
Одна запись прохода/фрагмента.

### COMP
Сборка из лучших тейков (на уровне политики, не техники).

---

## CORE RULES (CANON)

### VP1 — Persona consistency in delivery
Манера вокала обязана соответствовать:
- VPL (persona lock) из Lyrics engine
- tone/mood из Style engines

### VP2 — Fit to stress and melody
Ударные слоги обязаны совпадать с:
- SM (stress map)
- мелодическими anchors/peaks

### VP3 — Breath is planned
BAP обязателен:
- иначе фразы будут неисполняемыми.

### VP4 — Hook must be the cleanest
Хук-партия:
- самая читаемая
- минимум перегруза адлибами/гармониями
- максимум цитируемости

### VP5 — Stacks and harmonies are intentional
SHP:
- где дубли
- где гармонии
- где оставить “голый” голос

### VP6 — Microtiming respects groove feel
Если грув laid-back → вокал не должен быть впереди (если не intentional).

### VP7 — Mix-ready by performance
Перформанс должен быть:
- ровным по дикции в хук местах
- без лишней “грязи”, если стиль не требует

---

## REQUIRED ARTIFACT A: VOCAL SPEC (VS)

### VS SCHEMA (CANON)

Header:
- VS_ID:
- LS_ID:
- RMS_ID:
- MS_ID:
- RS_ID:
- AS_ID:
- LANGUAGE:
- VERSION:
- STATUS:
  - draft | canon | deprecated

Voice identity:
- DELIVERY STYLE:
  - intimate | neutral | aggressive | airy | gritty | clean | spoken
- EMOTION PROFILE:
  - baseline + peak moments
- TONE TARGET:
  - warm | bright | dark | nasal | breathy | clean
- VIBRATO POLICY:
  - none/light/med/heavy + where
- ORNAMENT POLICY:
  - none/light/med (runs, slides, etc.)

Range:
- RANGE + COMFORT ZONE (RRP ref)

Clarity rules:
- DICTION PRIORITY:
  - high/med/low
- CONSONANT POLICY:
  - crisp/soft
- “NO MUMBLE” ZONES:
  - hook lines, key story lines

Stacking:
- STACK/HARMONY PLAN (SHP ref)
- ADLIB POLICY:
  - none/light/med/heavy + forbidden zones

Takes:
- TAKE LIST (TL ref)
- COMP POLICY:
  - strict best-of / preserve human / raw allowed

Rule:
- VS is the “voice bible” for this track.

---

## REQUIRED ARTIFACT B: DELIVERY MAP (DM)

### DM SCHEMA (CANON)

For each section:
- SECTION ID:
- DELIVERY INTENSITY (0–10):
- TEXTURE:
  - clean | gritty | airy | whisper | shout
- MICROTIMING:
  - ahead | on | behind (relative to groove)
- PHRASE EMPHASIS:
  - which words get weight
- “EMOTION NOTE”:
  - one line acting direction

Rule:
- DM ties performance to song structure and payoff.

---

## REQUIRED ARTIFACT C: BREATH + ARTICULATION PLAN (BAP)

### BAP SCHEMA (CANON)

For each section/phrase group:
- REQUIRED BREATH SLOTS:
  - where breaths happen (before/after key words)
- FORCED CONTINUATION:
  - where not to breathe (to keep urgency)
- ARTICULATION MODE:
  - staccato | legato | mixed
- SPEED LIMIT:
  - max fast syllable run allowed (from SB)
- TONGUE-TWISTER BANS:
  - problematic clusters to avoid in lyrics edits

Rule:
- BAP ensures singability and prevents fatigue.

---

## REQUIRED ARTIFACT D: RANGE + REGISTER PLAN (RRP)

### RRP SCHEMA (CANON)

- RRP_ID:
- VS_ID:

Range:
- LOW LIMIT (comfortable):
- HIGH LIMIT (comfortable):
- “SAFE HOOK RANGE”:
  - where hook should stay for repeatability

Registers:
- PRIMARY REGISTER:
- ALTERNATE REGISTER:
- “PEAK POLICY”:
  - where you allow pushing range (final chorus, bridge)

Rule:
- RRP prevents burning the vocalist and ruining repeatability.

---

## REQUIRED ARTIFACT E: STACK/HARMONY PLAN (SHP)

### SHP SCHEMA (CANON)

Per section:
- SECTION ID:
- LEAD:
  - single | double | triple
- DOUBLES:
  - tight/unison/wide
- HARMONIES:
  - none | 3rd | 5th | octave | cluster (if style)
- ADLIBS:
  - none/light/med + where
- “HOOK CLEAN RULE”:
  - keep hook line lead dominant; harmonies controlled

Rule:
- SHP controls density and clarity.

---

## REQUIRED ARTIFACT F: TAKE LIST (TL)

### TL SCHEMA (CANON)

- TL_ID:
- VS_ID:

Take plan:
- LEAD TAKES COUNT (target):
- DOUBLES TAKES COUNT:
- HARMONY TAKES COUNT:
- ADLIB TAKES COUNT:
- SAFETY TAKES:
  - extra takes for hook lines

Naming convention:
- SECTION_TAKE_ROLE_INDEX
  - e.g., C1_LEAD_01, C1_DOUBLE_01, C1_HARM3RD_01

Rule:
- TL ensures clean production pipeline and easy comping.

---

## REQUIRED ARTIFACT G: VOCAL QC GATES (VQG)

### VQG SCHEMA (CANON)

Gates:
1) Persona delivery gate:
   - delivery matches VPL and style locks
2) Fit gate:
   - stresses align; no forced syllables
3) Breath feasibility gate:
   - BAP makes phrases performable
4) Hook clarity gate:
   - hook is clean, readable, repeatable
5) Dynamics gate:
   - DM matches section energy curve
6) Groove alignment gate:
   - microtiming matches MTP feel intentionally
7) Stack control gate:
   - SHP supports clarity (no clutter)
8) Mix-ready performance gate:
   - diction and consistency sufficient
9) Reproducibility gate:
   - VS+DM+BAP+RRP+SHP+TL allow recreation

Rule:
- Fail 2+ gates → adjust delivery/lyrics fit/stack plan.

---

## INCONSISTENCY DETECTOR (HEURISTICS)

Flag if:
- hook line is hard to understand
- vocalist runs out of breath frequently
- delivery switches persona between sections
- chorus is weaker than verse (energy drop)
- vocal timing fights groove feel
- too many harmonies/adlibs masking hook
- range pushes too high too early

Fix options:
- simplify hook phrasing; increase diction priority
- add breath slots; shorten lines (feed back to 06/07)
- lock delivery mode and intensity curve in DM
- redesign chorus stack (doubles for thickness)
- align timing to groove (choose ahead/on/behind)
- reduce harmonies to last word only or tags
- move peak to final chorus/bridge

---

## PROCEDURE (HOW TO RUN)

1) Read LS persona + RMS fit constraints + MS hook map
2) Define voice identity (VS voice bible)
3) Define range/register plan (RRP)
4) Build delivery map (DM) per section energy
5) Build breath/articulation plan (BAP) per phrase windows
6) Build stack/harmony plan (SHP) with hook clarity rule
7) Build take list (TL) and naming convention
8) Run VQG gates and iterate
9) Hand off to arrangement and mix/master with constraints

---

## QC CHECKLIST (MANDATORY)

- voice identity locked?
- hook clarity guaranteed?
- breath plan makes it performable?
- stresses align with accent grid and melody peaks?
- delivery intensity curve matches structure?
- stack plan supports clarity?
- take list ready for recording workflow?
- reproducible artifacts present?

---

## VALIDATION RULES

- VPV1: Vocal delivery matches persona and style locks.
- VPV2: Fit to melody and stress maps is clean.
- VPV3: Breath and articulation are planned and feasible.
- VPV4: Hook lines are clear, repeatable, and dominant.
- VPV5: Stacks/harmonies/adlibs are intentional and controlled.
- VPV6: Groove microtiming aligns with rhythm feel.
- VPV7: Performance is mix-ready by design.
- VPV8: Spec is reproducible.

---

OWNER: Universe Engine
LOCK: FIXED
