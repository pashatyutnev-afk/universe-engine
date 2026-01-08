# STORY STRUCTURE ENGINE
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/02_DOMAIN_NARRATIVE_ENGINES/02__STORY_STRUCTURE_ENG.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 02_DOMAIN_NARRATIVE_ENGINES
ENGINE: 02__STORY_STRUCTURE_ENG
DOC_TYPE: ENGINE
LEVEL: L2
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.ENG.NARR.STRUCTURE.001
OWNER: SYSTEM
ROLE: Convert narrative logic + premise into a deterministic story structure blueprint (acts/sequence/beats) without producing scene-level implementation.

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Story Structure Engine created: structure blueprint, beat map, and act-level continuity constraints."
- REASON: "Needed canonical story-level structure layer above logic and below scenes."
- IMPACT: "Downstream engines (arc/scenes/pacing/tension) get stable structure inputs."
- CHANGE_ID: UE.CHG.2026-01-08.ENG.NARR.STRUCTURE.001

---

## 0) PURPOSE (LAW)
Этот движок создаёт **структурный план истории**:
- актовую/сегментную структуру (acts/parts)
- последовательность “крупных узлов” (sequence units)
- карту битов/поворотов (beats)
- структурные ограничения непрерывности (что должно произойти, чтобы история работала)

Это “скелет” истории, но **не сцены** и **не монтаж**.

---

## 1) NON-GOALS (HARD)
Движок НЕ делает:
- сценическое наполнение (диалоги/мизансцены/кадры) → `04__SCENE_CONSTRUCTION_ENG`
- драматическую арку как аналитическую модель развития (это отдельный движок) → `03__DRAMATIC_ARC_ENG`
- темп как story-time профиль (это отдельный движок) → `05__PACING_RHYTHM_ENG`
- напряжение/ставки как отдельную карту (это отдельный движок) → `06__TENSION_STAKES_ENG`
- “как показать на экране” (production) → `08_*`

---

## 2) MINI-CONTRACT (MANDATORY)

### CONSUMES (1–7)
- `CORE_IDENTITY`
- `CORE_STATE`
- `NARRATIVE_PREMISE` (optional but recommended)
- `NARRATIVE_LOGIC_MODEL`
- `PLAUSIBILITY_RULESET` (optional)
- `CHARACTER_INTENT_SEEDS` (optional)

### PRODUCES (1–7)
- `STORY_STRUCTURE_BLUEPRINT`
- `BEAT_MAP`
- `STRUCTURE_CONSTRAINTS`

### DEPENDS_ON
- `[02_DOMAIN_NARRATIVE_ENGINES/01__NARRATIVE_LOGIC_ENG]`

### OUTPUT_TARGET
- `PROJECT_ARTIFACTS/<project>/NARRATIVE/STRUCTURE/`

---

## 3) DEFINITIONS (LOCAL)
- **Act** — крупный структурный блок истории (часть/акт).
- **Sequence Unit** — средний блок внутри акта, объединяющий несколько сцен.
- **Beat** — минимальная структурная единица изменения (новая информация/решение/поворот/сдвиг).
- **Structural Turn** — beat, который меняет направление/цель/условия (turning point на уровне структуры, не на уровне сцены).

---

## 4) BOUNDARIES (MANDATORY)

### IN SCOPE (OWNS)
- выбор структурной модели (акт/части/петли/фреймы) как “контейнер”
- порядок ключевых изменений (beats) и их роль
- структурные зависимости (без которых история не работает)
- структурные точки “поворота направления” (на уровне акта/сегмента)

### OUT OF SCOPE (HARD)
- конкретные события-сцены (это уже сцены)
- эмоциональная арка и аналитика роста/падения (драматическая арка)
- темп/ритм (отдельный движок)
- монтажные решения (production editing)

### COLLISION RULE (ROUTING)
- Если про “как выглядит сцена” → `04__SCENE_CONSTRUCTION_ENG`
- Если про “как развивается напряжение” → `06__TENSION_STAKES_ENG`
- Если про “что именно меняется в кульминации/развязке на уровне события” → `05_EXPRESSION_ENGINES/*` (если чистая механика события)
- Если про “арка персонажа” → `03_DOMAIN_CHARACTER_ENGINES/*`

---

## 5) OUTPUT SCHEMAS (MANDATORY)

### A) `STORY_STRUCTURE_BLUEPRINT`
**MUST (fields):**
- `blueprint_id` (string)
- `version` (string)
- `structure_model` (enum: `THREE_ACT|FIVE_ACT|HERO_JOURNEY|TRAGEDY|MYSTERY_GRID|EPISODIC|CUSTOM`)
- `acts[]` (list; non-empty if premise exists)
- `sequence_units[]` (list; can be empty at first pass)
- `structural_turns[]` (list; can be empty)
- `logic_links[]` (references to `NARRATIVE_LOGIC_MODEL` atoms/links)
- `constraints_ref` (pointer to `STRUCTURE_CONSTRAINTS`)
- `open_unknowns[]` (list)
- `scope_notes` (string)

**Act (minimum):**
- `id`
- `name`
- `goal_state` (what the act must achieve)
- `entry_condition` (required pre-state)
- `exit_condition` (required post-state)
- `required_beats[]` (ids)
- `risk_if_missing` (`S0|S1|S2|S3`)

**VALIDATION:**
- all `required_beats` exist in `BEAT_MAP`
- `entry_condition` and `exit_condition` do not violate `NARRATIVE_LOGIC_MODEL`
- if `structure_model=CUSTOM`, must include `custom_model_notes`

**STORAGE:**
- `PROJECT_ARTIFACTS/<project>/NARRATIVE/STRUCTURE/STORY_STRUCTURE_BLUEPRINT.md`

---

### B) `BEAT_MAP`
**MUST (fields):**
- `beat_map_id`
- `beats[]` (list; can be empty if no premise)
- `turns[]` (list; subset of beats that are structural turns)
- `dependencies[]` (beat-to-beat requirements)
- `logic_refs[]` (links to logic atoms/constraints)

**Beat (minimum):**
- `id`
- `type` (enum: `INFO_REVEAL|DECISION|REVERSAL|COMMITMENT|LOSS|GAIN|ARRIVAL|DEPARTURE|CONFLICT_START|CONFLICT_SHIFT|CONFLICT_RESOLVE|THEME_SIGNAL`)
- `function` (short text: what changes)
- `preconditions[]` (logic atoms or prior beats)
- `postconditions[]` (logic atoms or new state)
- `stakes_delta` (`UP|DOWN|SHIFT|NONE`)
- `route_to_scene` (bool; default true)
- `notes` (string)

**VALIDATION:**
- no beat has both incompatible postconditions (else route to contradiction report)
- beats should be topologically orderable by `dependencies` (cycles allowed only with explicit `cycle_reason`)

**STORAGE:**
- `PROJECT_ARTIFACTS/<project>/NARRATIVE/STRUCTURE/BEAT_MAP.md`

---

### C) `STRUCTURE_CONSTRAINTS`
**MUST (fields):**
- `constraints_id`
- `hard_constraints[]`
- `soft_constraints[]`
- `continuity_rules[]`
- `prohibited_moves[]`
- `s0_blockers[]` (structure-level blockers)
- `routing_notes[]` (where to resolve out-of-scope issues)

**VALIDATION:**
- every `hard_constraint` is compatible with `PLAUSIBILITY_RULESET` if provided
- every `s0_blocker` has a resolution path (engine route or decision)

**STORAGE:**
- `PROJECT_ARTIFACTS/<project>/NARRATIVE/STRUCTURE/STRUCTURE_CONSTRAINTS.md`

---

## 6) PROCESS (PIPELINE)
1) Read `NARRATIVE_LOGIC_MODEL` → extract constraints & causal necessities.
2) Select `structure_model`:
   - default `THREE_ACT` unless project format forces otherwise (handled later by format engines).
3) Generate candidate acts:
   - Act 1: setup + commitment pivot
   - Act 2: escalation + reversals
   - Act 3: confrontation + resolution
4) Generate beats:
   - each beat must map to a logical change (pre/postconditions).
5) Validate:
   - contradictions routed back to `CONTRADICTION_REPORT` (logic engine) or flagged as `open_unknowns`.
6) Emit outputs.

---

## 7) GATES (S0 BLOCKERS)
S0 (BLOCK) if:
- structure requires a beat that violates a hard plausibility rule
- act exit condition cannot be achieved given logic constraints
- the blueprint contains a necessary causal gap (“must happen” but no allowed path)

S1 (HIGH) if:
- beats are present but under-specified (too many open_unknowns)
- missing structural turns (story has no direction change)

S2/S3: quality warnings.

---

## 8) DEPENDENCY NOTES
Downstream engines consume:
- `STORY_STRUCTURE_BLUEPRINT` and `BEAT_MAP` as primary inputs.
This engine must stay “structure-only”: no scene micro-detail.

---

LOCK: OPEN
