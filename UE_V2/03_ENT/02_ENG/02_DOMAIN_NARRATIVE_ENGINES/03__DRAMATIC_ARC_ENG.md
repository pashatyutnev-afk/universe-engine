# DRAMATIC ARC ENGINE
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/02_DOMAIN_NARRATIVE_ENGINES/03__DRAMATIC_ARC_ENG.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 02_DOMAIN_NARRATIVE_ENGINES
ENGINE: 03__DRAMATIC_ARC_ENG
DOC_TYPE: ENGINE
LEVEL: L2
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.ENG.NARR.ARC.001
OWNER: SYSTEM
ROLE: Build a dramatic arc specification over the story structure: pressure escalation, reversals, peak, and release patterns (story-domain, not editing).

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Dramatic Arc Engine created: arc spec, escalation ladder, peak placement, and release planning."
- REASON: "Needed a canonical layer between structure beats and scene execution for dramatic shaping."
- IMPACT: "Downstream tension/pacing/scenes can align with a stable arc plan."
- CHANGE_ID: UE.CHG.2026-01-08.ENG.NARR.ARC.001

---

## 0) PURPOSE (LAW)
Этот движок формирует **драматическую арку истории** поверх структуры:
- как нарастает давление/цена/риск
- где и почему происходят “реверсы” (перевороты)
- где пик (peak) и как устроен спад/разрядка
- как арка согласуется с beats и логикой (не нарушая причинность)

Арка — это **форма напряжения истории во времени сюжета**, но это НЕ монтаж и не длительности экрана.

---

## 1) NON-GOALS (HARD)
Движок НЕ делает:
- монтажный ритм / склейки / timing screen-time → `08_KNOWLEDGE_PRODUCTION_ENGINES/07__EDITING_MONTAGE_ENG`
- конкретные сцены/диалоги → `04__SCENE_CONSTRUCTION_ENG`
- “ставки и угрозы” как отдельная карта механизмов (это отдельный движок) → `06__TENSION_STAKES_ENG`
- темп как pacing профиль (это отдельный движок) → `05__PACING_RHYTHM_ENG`
- атмосферу/тон/стиль → `06_GENRE_STYLE_ENGINES/*`

---

## 2) MINI-CONTRACT (MANDATORY)

### CONSUMES (1–7)
- `CORE_IDENTITY`
- `CORE_STATE`
- `NARRATIVE_LOGIC_MODEL`
- `STORY_STRUCTURE_BLUEPRINT`
- `BEAT_MAP`
- `STRUCTURE_CONSTRAINTS` (optional)
- `CHARACTER_INTENT_SEEDS` (optional)

### PRODUCES (1–7)
- `DRAMATIC_ARC_SPEC`
- `ESCALATION_LADDER`
- `PEAK_RELEASE_PLAN`

### DEPENDS_ON
- `[02_DOMAIN_NARRATIVE_ENGINES/01__NARRATIVE_LOGIC_ENG, 02_DOMAIN_NARRATIVE_ENGINES/02__STORY_STRUCTURE_ENG]`

### OUTPUT_TARGET
- `PROJECT_ARTIFACTS/<project>/NARRATIVE/ARC/`

---

## 3) DEFINITIONS (LOCAL)
- **Pressure** — суммарный “вес” конфликта: риск, цена, ограничение времени, моральный выбор.
- **Escalation** — увеличение давления/цены/необратимости.
- **Reversal** — структурный момент, где ожидаемая траектория меняется.
- **Peak** — точка максимального давления/необратимости.
- **Release** — снижение давления через последствия, принятие, расплату, решение.

---

## 4) BOUNDARIES (MANDATORY)

### IN SCOPE (OWNS)
- построение арки давления во времени story-time
- привязка арки к beats/актовой структуре
- планирование реверсов, пиков и разрядок
- требования к сценам (как “must-hit” цели), без написания сцен

### OUT OF SCOPE (HARD)
- монтажное ускорение/замедление экрана
- чисто эмоциональный тон/атмосфера (стиль)
- конкретная реализация конфликтов в сценах (сцены)
- механика событий (event engine) если арка пытается заменить “что случается”

### COLLISION RULE (ROUTING)
- Если спор “это про ставки/угрозы/ресурсы как система” → `06__TENSION_STAKES_ENG`
- Если спор “это про скорость событий (темп)” → `05__PACING_RHYTHM_ENG`
- Если спор “это про монтаж/показ” → `08_*`
- Если спор “это про настроение/тон” → `06_*`

---

## 5) OUTPUT SCHEMAS (MANDATORY)

### A) `DRAMATIC_ARC_SPEC`
**MUST (fields):**
- `arc_id`
- `version`
- `arc_curve_type` (enum: `RISING|RISE_FALL|WAVES|SPIRAL|TRAGEDY_DROP|MYSTERY_REVEAL_WAVES|CUSTOM`)
- `act_arc_segments[]` (mapping to acts)
- `pressure_points[]` (ordered)
- `reversals[]` (subset of pressure points)
- `peak` (single point)
- `release_points[]`
- `beat_alignment[]` (map pressure points -> beat ids)
- `logic_constraints_ref` (pointer to constraints from logic model)
- `open_unknowns[]`
- `scope_notes`

**Pressure Point (minimum):**
- `id`
- `position` (`ACT1|ACT2|ACT3|ACT4|ACT5|CUSTOM`)
- `pressure_level` (int 0..100)
- `driver` (enum: `TIME|RISK|LOSS|MORAL|RESOURCE|RELATIONSHIP|REVELATION|POWER_SHIFT`)
- `what_changes` (string)
- `required_preconditions[]` (logic atoms or beat ids)
- `required_postconditions[]` (logic atoms or beat ids)
- `notes`

**VALIDATION:**
- `peak.pressure_level` must be max across points
- every mapped beat must exist
- no pressure point may require a postcondition that violates `NARRATIVE_LOGIC_MODEL`

**STORAGE:**
- `PROJECT_ARTIFACTS/<project>/NARRATIVE/ARC/DRAMATIC_ARC_SPEC.md`

---

### B) `ESCALATION_LADDER`
**MUST (fields):**
- `ladder_id`
- `rungs[]` (ordered escalation steps)
- `escalation_rules[]` (what counts as escalation)
- `anti_patterns[]` (common failure patterns)

**Rung (minimum):**
- `id`
- `from_level` (0..100)
- `to_level` (0..100)
- `mechanism` (short)
- `beat_ids[]` (supporting beats)
- `cost_increase` (string; what gets more expensive)
- `irreversibility_delta` (`UP|NONE|DOWN`)

**VALIDATION:**
- ladder must be non-decreasing in pressure
- each rung must cite at least one beat or be marked as `open_unknown`

**STORAGE:**
- `PROJECT_ARTIFACTS/<project>/NARRATIVE/ARC/ESCALATION_LADDER.md`

---

### C) `PEAK_RELEASE_PLAN`
**MUST (fields):**
- `plan_id`
- `peak_definition` (what makes it peak)
- `peak_beat_ids[]`
- `release_modes[]` (enum list: `VICTORY|LOSS|SACRIFICE|TRUTH|PAYMENT|SEPARATION|UNION|EXILE|TRANSFORMATION`)
- `release_beats[]`
- `aftermath_requirements[]` (what must be resolved)
- `continuity_checks[]`

**VALIDATION:**
- peak must align to structure constraints (cannot happen before required build-up beats)
- release beats must not contradict logic model

**STORAGE:**
- `PROJECT_ARTIFACTS/<project>/NARRATIVE/ARC/PEAK_RELEASE_PLAN.md`

---

## 6) PROCESS (PIPELINE)
1) Read structure: acts + beats + turns.
2) Extract “pressure drivers” from beats (risk/loss/time/moral/power).
3) Select `arc_curve_type` (default `WAVES` for long stories; `RISING` for short).
4) Place:
   - early pressure points (setup constraints)
   - mid reversals (trajectory changes)
   - peak (max irreversibility)
   - release (aftermath obligations)
5) Validate against logic model and structure constraints.
6) Emit outputs.

---

## 7) GATES (S0 BLOCKERS)
S0 (BLOCK) if:
- arc implies a peak that requires impossible preconditions
- escalation demands an outcome prohibited by plausibility/logic constraints
- release contradicts required structure exit conditions (например, финал “не закрывает” обязательные элементы структуры)

S1 (HIGH) if:
- arc has no meaningful reversals (flat line)
- peak exists but no release plan (hanging payoff)
- escalation ladder has gaps (pressure jumps without mechanism)

S2/S3: quality warnings.

---

## 8) NOTES FOR DOWNSTREAM ENGINES
- `06__TENSION_STAKES_ENG` may use this arc to build a formal stakes map.
- `05__PACING_RHYTHM_ENG` may derive pacing from arc density (story-time only).
- `04__SCENE_CONSTRUCTION_ENG` uses pressure points as scene objectives.

---

LOCK: OPEN
