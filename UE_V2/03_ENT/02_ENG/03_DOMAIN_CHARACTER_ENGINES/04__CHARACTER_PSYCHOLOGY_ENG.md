# CHARACTER PSYCHOLOGY ENGINE
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/03_DOMAIN_CHARACTER_ENGINES/04__CHARACTER_PSYCHOLOGY_ENG.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 03_DOMAIN_CHARACTER_ENGINES
ENGINE: 04__CHARACTER_PSYCHOLOGY_ENG
DOC_TYPE: ENGINE
LEVEL: L2
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.ENG.CHAR.PSY.001
OWNER: SYSTEM
ROLE: Produce a deterministic psychology model for a character: inner state variables, triggers, coping patterns, defense mechanisms, emotional regulation, and stress responses compatible with core, motivation, and values.

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Character Psychology Engine created: inner state model, triggers, defenses, coping loops, and stress escalation ladder."
- REASON: "Need explicit psychological dynamics so behavior and dialogue can be generated consistently under pressure."
- IMPACT: "Characters gain coherent inner logic: why they react, how they cope, and what breaks them."
- CHANGE_ID: UE.CHG.2026-01-08.ENG.CHAR.PSY.001

---

## 0) PURPOSE (LAW)
Этот движок описывает **внутреннюю динамику персонажа**:
- переменные внутреннего состояния (anxiety, trust, shame, control, etc.)
- триггеры (что запускает реакцию)
- защитные механизмы (defenses)
- копинг/саморегуляция (coping & regulation)
- лестница стресса (как реакции меняются при росте давления)
- точки срыва (meltdown/shutdown) и восстановление

Цель: дать downstream-движкам (behavior/dialogue/relationships) стабильную модель “как он переживает”.

---

## 1) NON-GOALS (HARD)
Движок НЕ делает:
- травму/рост как события трансформации (это `09__GROWTH_TRAUMA_ENG`)
- долгосрочную эволюцию личности (это `10__CHARACTER_EVOLUTION_ENG`)
- мотивации (это `02__MOTIVATION_DESIRE_ENG`)
- ценности/мораль (это `03__MORAL_VALUE_ENG`)
- детальные правила выбора в ситуации (это `05__CHARACTER_BEHAVIOR_ENG`)
- постановку актёрской игры/режиссуры (production)

---

## 2) MINI-CONTRACT (MANDATORY)

### CONSUMES (1–12)
- `CORE_IDENTITY`
- `CORE_STATE`
- `CHARACTER_CORE_PASSPORT`
- `CHARACTER_INVARIANTS`
- `CHARACTER_TRAIT_PROFILE`
- `MOTIVATION_DESIRE_STACK` (optional but recommended)
- `FEAR_AVOIDANCE_MAP` (optional)
- `VALUE_HIERARCHY` (optional)
- `MORAL_BOUNDARY_MAP` (optional)
- `WORLD_LAW_SEEDS` (optional)
- `RELATIONSHIP_SEEDS` (optional)
- `STAKE_CONTEXT` (optional)

### PRODUCES (1–7)
- `INNER_STATE_MODEL`
- `TRIGGER_DEFENSE_MAP`
- `STRESS_ESCALATION_LADDER`

### DEPENDS_ON
- `[03_DOMAIN_CHARACTER_ENGINES/01__CHARACTER_CORE_ENG, 03_DOMAIN_CHARACTER_ENGINES/02__MOTIVATION_DESIRE_ENG, 03_DOMAIN_CHARACTER_ENGINES/03__MORAL_VALUE_ENG]`

### OUTPUT_TARGET
- `PROJECT_ARTIFACTS/<project>/CHARACTERS/PSYCHOLOGY/`

---

## 3) DEFINITIONS (LOCAL)
- **Inner State Variable** — числовая/категориальная переменная, описывающая внутреннее состояние.
- **Trigger** — входной стимул/ситуация, изменяющая переменные.
- **Defense** — автоматическая защита (denial, projection, control, humor).
- **Coping** — сознательный/полусознательный способ справляться (breathing, retreat, attack).
- **Stress Ladder** — уровни реакции при нарастающем давлении.
- **Break Point** — точка, после которой поведение радикально меняется (collapse/violence/freeze).

---

## 4) BOUNDARIES (MANDATORY)

### IN SCOPE (OWNS)
- модель внутренних переменных и их диапазонов
- связи trigger → defense/coping
- лестница стресс-эскалации
- восстановление (recovery patterns) и условия

### OUT OF SCOPE (HARD)
- изменение ценностей/инвариантов во времени (growth/evolution)
- выбор стратегии действия как алгоритм решения (behavior)
- сюжетные события (narrative)
- мир как владелец законов (world)

### COLLISION RULE (ROUTING)
- Если требуется “слом личности”/перепрошивка → `09__GROWTH_TRAUMA_ENG` → `10__CHARACTER_EVOLUTION_ENG`
- Если требуется конкретный decision policy → `05__CHARACTER_BEHAVIOR_ENG`
- Если триггеры обусловлены миром (табу культуры/законы) → `04_DOMAIN_WORLD_ENGINES/*` (как источник внешней нормы)

---

## 5) OUTPUT SCHEMAS (MANDATORY)

### A) `INNER_STATE_MODEL`
**MUST (fields):**
- `character_id`
- `version`
- `variables[]` (3..12)
- `baseline_profile` (default values)
- `regulation_methods[]` (optional)
- `recovery_profile`
- `open_unknowns[]`
- `scope_notes`

**Variable (minimum):**
- `var_id`
- `name`
- `type` (enum: `SCALE_0_100|SCALE_-100_100|ENUM|BOOL`)
- `meaning_high`
- `meaning_low`
- `baseline` (number or enum)
- `volatility` (`LOW|MEDIUM|HIGH`)
- `visibility` (`INTERNAL|LEAKS|EXTERNAL`)  (does it show outwardly)
- `notes`

**Baseline profile (minimum):**
- `values` (map var_id -> baseline)
- `stable_conditions[]` (what keeps baseline stable)

**Recovery profile (minimum):**
- `fast_recovery_methods[]`
- `slow_recovery_methods[]`
- `what_worsens[]`

**VALIDATION:**
- each variable must define meaning_high/low
- baseline must be within valid range
- at least one variable must be `visibility=LEAKS` or `EXTERNAL` (else character unreadable) (S2 warning if none)

**STORAGE:**
- `PROJECT_ARTIFACTS/<project>/CHARACTERS/PSYCHOLOGY/<character_id>/INNER_STATE_MODEL.md`

---

### B) `TRIGGER_DEFENSE_MAP`
**MUST (fields):**
- `character_id`
- `triggers[]`
- `defenses[]`
- `coping_patterns[]`
- `mappings[]`
- `anti_patterns[]`
- `open_unknowns[]`

**Trigger (minimum):**
- `trigger_id`
- `signal` (what happens externally)
- `core_fear_link` (optional fear_id)
- `variables_affected[]` (var_ids)
- `delta` (per variable; short)
- `notes`

**Defense (minimum):**
- `defense_id`
- `name` (enum-like string; e.g., DENIAL, PROJECTION, CONTROL, HUMOR, WITHDRAWAL)
- `function` (what it protects)
- `cost` (what it breaks)

**Coping pattern (minimum):**
- `coping_id`
- `name`
- `type` (enum: `SOOTHING|CONTROL|SEEK_HELP|AVOID|ATTACK|FREEZE`)
- `how_it_looks` (external behavior)
- `effect_on_variables` (short)

**Mapping (minimum):**
- `trigger_id`
- `default_defense_id`
- `backup_defense_id` (optional)
- `coping_id` (optional)
- `when_switches` (condition)

**VALIDATION:**
- each trigger must map to at least one defense
- defenses must list a cost (no free defenses)

**STORAGE:**
- `PROJECT_ARTIFACTS/<project>/CHARACTERS/PSYCHOLOGY/<character_id>/TRIGGER_DEFENSE_MAP.md`

---

### C) `STRESS_ESCALATION_LADDER`
**MUST (fields):**
- `character_id`
- `levels[]` (3..7)
- `break_points[]`
- `deescalation_paths[]`
- `warnings[]`

**Level (minimum):**
- `level_id`
- `stress_range` (e.g., 0-20, 21-50)
- `internal_state_signature` (key variables/values)
- `default_behavior_shift` (short)
- `dialogue_shift` (short)
- `relationship_shift` (short)
- `risk` (`LOW|MEDIUM|HIGH`)

**Break point (minimum):**
- `bp_id`
- `trigger_combo` (conditions)
- `outcome` (enum: `MELTDOWN|SHUTDOWN|VIOLENCE|FLIGHT|CONFESSION|DISSOCIATION`)
- `after_effect` (what remains changed temporarily)
- `recovery_requirement` (what is needed to return)

**Deescalation path (minimum):**
- `from_level`
- `to_level`
- `method` (coping/regulation)
- `cost` (short)

**VALIDATION:**
- ladder must include at least one break point with recovery requirement
- if break point outcome violates moral boundaries, mark routing note to values/growth engines (S1)

**STORAGE:**
- `PROJECT_ARTIFACTS/<project>/CHARACTERS/PSYCHOLOGY/<character_id>/STRESS_ESCALATION_LADDER.md`

---

## 6) PROCESS (PIPELINE)
1) Read core + traits + motivations + values.
2) Choose inner variables (3–9) that explain the character’s reactions.
3) Set baselines + volatility + visibility.
4) Define triggers from fears, boundaries, and social pressure.
5) Define defenses and coping patterns (each must have a cost).
6) Map triggers → defenses/coping + switch conditions.
7) Build stress ladder:
   - low → medium → high → break point
   - define deescalation paths
8) Validate and emit outputs.

---

## 7) GATES (S0 BLOCKERS)
S0 (BLOCK) if:
- psychology model contradicts HARD invariants without routing (e.g., “never lies” but default defense is constant lying as baseline without reason)
- triggers affect variables but variables are undefined (schema breach)
- break points exist with no recovery requirement (non-deterministic)

S1 (HIGH) if:
- all defenses are “free” (no cost)
- stress ladder lacks observable shifts (no dialogue/behavior signals)

S2/S3: quality warnings.

---

## 8) NOTES FOR DOWNSTREAM ENGINES
- Behavior engine uses ladder + mappings to choose actions under pressure.
- Relationship engine uses stress shifts to model push/pull dynamics.
- Dialogue engine uses dialogue_shift to keep voice consistent with stress level.
- Growth/Trauma engine uses break points as candidate transformation events.

---

LOCK: OPEN
