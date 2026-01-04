# Sound & Music Engine (Production Layer)
FILE: 08__SOUND_MUSIC_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 08_KNOWLEDGE_PRODUCTION_ENGINES
LEVEL: L3
STATUS: ACTIVE
VERSION: 1.1
ROLE: Production-level audio logic (sound palette, ambience, FX rules, music placement, sync, clarity); deep composition lives in 09_SOUND_MUSIC_ENGINES

---

## PURPOSE

Этот движок — про **продакшн-аудио**, а не про композиторскую глубину:
- sound palette (категории звука)
- ambience layers
- fx rules
- music placement (где музыка входит/выходит и зачем)
- sync points (по монтажу)
- ясность/громкость/приоритеты

---

## BOUNDARY (MANDATORY)

### THIS ENGINE OWNS (PRODUCTION AUDIO)
- диалог/амбьенс/FX баланс (приоритеты)
- правила входа/выхода музыки (placement)
- синхронизацию музыки/FX с монтажом (sync markers)
- loudness/clarity, mix target как политика

### THIS ENGINE DOES NOT OWN
- композицию (гармония, мелодия, структура песни, аранж) → это 09 family
- монтажные решения (склейки/ритм кадра) → это 08/07
- “что происходит в истории” → это narrative engines

---

## MINI-CONTRACT (MANDATORY)

- CONSUMES: EDIT RHYTHM MAP (08/07), sync markers, scene emotional map, platform constraints
- PRODUCES: AUDIO PRODUCTION SPEC, sound palette, music placement plan, mix target policy
- DEPENDS_ON: [08_KNOWLEDGE_PRODUCTION_ENGINES/07__EDITING_MONTAGE_ENG.md, 02_DOMAIN_NARRATIVE_ENGINES/05__PACING_RHYTHM_ENG.md]
- OUTPUT_TARGET: 05_PROJECTS/*/05_PROJECT__L3/* (sound spec) + handoff to 09_SOUND_MUSIC_ENGINES/12__MUSIC_TO_SCENE_ENG.md (if composing/scoring)

---

## INPUTS

- Edit rhythm map + sync markers
- Scene emotional intent / arc
- Style bible (world texture)
- Dialogue constraints (if any)
- Delivery format (short/episode/film/game)

---

## OUTPUTS

### 1) AUDIO PRODUCTION SPEC (CANON)
- DIALOGUE PRIORITY (high/med/low)
- AMBIENCE LAYERS (base + detail layers)
- FX CATEGORIES (hits/whooshes/tech/organic)
- MUSIC ROLE (drive/underscore/none)
- MUSIC ENTRY/EXIT RULES (when/why)
- SYNC POINTS (from edit markers)
- SILENCE POLICY (where silence is power)
- MIX TARGET (clean/dirty/cinematic)
- LOUDNESS POLICY (relative, not numeric)

### 2) SOUND PALETTE
- 5–12 categories with examples (text)
- “Do/Don’t” artifacts list (avoid muddy, avoid harsh…)

### 3) MUSIC PLACEMENT PLAN
- per segment: music on/off, intensity curve, entry/exit triggers

---

## PROCEDURE

1) Read edit rhythm map + sync markers
2) Define dialogue priority and clarity rules
3) Build ambience base + detail layers
4) Define FX categories + transition FX policy
5) Define music placement (where and why)
6) Mark silence zones (intentional)
7) Run QC: clarity + meaning + fatigue check
8) Publish production spec

---

## VALIDATION RULES

- SM1: Диалог (если есть) всегда читаем.
- SM2: Звук усиливает смысл, не забивает его.
- SM3: Музыка входит/выходит осознанно (не случайно).
- SM4: Sync markers используются (нет “плавающих” ударов).

---

## HANDOFF (MANDATORY)

### Receives from Editing (08/07)
- EDIT RHYTHM MAP
- SYNC MARKERS LIST
- Transition palette → FX whooshes/hits consistency

### Sends to Music To Scene (09/12) when music needs composition/scoring
- MUSIC PLACEMENT PLAN
- SYNC POINTS + segment intensity curve
- Constraints: silence windows, dialogue priority

### Receives back from Music To Scene (09/12)
- cue list / stems usage notes / intensity plan
(и применяет в production mix policy)

---

## INTEGRATION

- Upstream: Editing & Montage (08/07), Narrative rhythm (02/05)
- Downstream: Music To Scene (09/12), Mix/Master (09/13)

---

OWNER: Universe Engine
LOCK: FIXED
