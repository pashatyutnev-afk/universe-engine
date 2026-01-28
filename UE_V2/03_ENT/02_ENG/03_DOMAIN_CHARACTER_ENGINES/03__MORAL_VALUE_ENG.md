# MORAL & VALUE ENGINE
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/03_DOMAIN_CHARACTER_ENGINES/03__MORAL_VALUE_ENG.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 03_DOMAIN_CHARACTER_ENGINES
ENGINE: 03__MORAL_VALUE_ENG
DOC_TYPE: ENGINE
LEVEL: L2
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.ENG.CHAR.VALUES.001
OWNER: SYSTEM
ROLE: Produce a deterministic moral/value model for a character: value hierarchy, moral boundaries, taboo lines, rationalizations, and decision constraints compatible with character core and motivation.

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Moral & Value Engine created: value hierarchy, moral boundaries, taboo map, and moral conflict resolution rules."
- REASON: "Motivations alone do not determine choices; value system defines what a character will or will not do."
- IMPACT: "Behavior, dialogue, and growth engines get consistent moral constraints."
- CHANGE_ID: UE.CHG.2026-01-08.ENG.CHAR.VALUES.001

---

## 0) PURPOSE (LAW)
Этот движок фиксирует **ценности и моральные границы персонажа**:
- иерархия ценностей (что важнее чего)
- табу и “красные линии” (что нельзя)
- оправдания и самообман (как персонаж объясняет себе выбор)
- моральные дилеммы (когда ценности конфликтуют)
- правила разрешения конфликтов (что побеждает и при каких триггерах)

Выход — моральный контракт персонажа, который ограничивает мотивации и поведение.

---

## 1) NON-GOALS (HARD)
Движок НЕ делает:
- мотивации/желания как первичный двигатель (это `02__MOTIVATION_DESIRE_ENG`)
- психологические состояния/травмы как источник морали (это `04__CHARACTER_PSYCHOLOGY_ENG` / `09__GROWTH_TRAUMA_ENG`)
- алгоритмы выбора в конкретной ситуации (это `05__CHARACTER_BEHAVIOR_ENG`)
- сюжетную структуру (narrative family)
- стилевую “подачу морали” (genre/style family)
- production (актёрская игра/монтаж)

---

## 2) MINI-CONTRACT (MANDATORY)

### CONSUMES (1–10)
- `CORE_IDENTITY`
- `CORE_STATE`
- `CHARACTER_CORE_PASSPORT`
- `CHARACTER_INVARIANTS`
- `CHARACTER_TRAIT_PROFILE`
- `MOTIVATION_DESIRE_STACK` (optional but recommended)
- `FEAR_AVOIDANCE_MAP` (optional)
- `WORLD_LAW_SEEDS` (optional)
- `NARRATIVE_PREMISE` (optional)
- `STAKE_CONTEXT` (optional)

### PRODUCES (1–7)
- `VALUE_HIERARCHY`
- `MORAL_BOUNDARY_MAP`
- `DILEMMA_RULESET`

### DEPENDS_ON
- `[03_DOMAIN_CHARACTER_ENGINES/01__CHARACTER_CORE_ENG, 03_DOMAIN_CHARACTER_ENGINES/02__MOTIVATION_DESIRE_ENG]`

### OUTPUT_TARGET
- `PROJECT_ARTIFACTS/<project>/CHARACTERS/VALUES/`

---

## 3) DEFINITIONS (LOCAL)
- **Value** — то, что персонаж считает важным (свобода, правда, семья, порядок).
- **Moral Boundary** — линия, которую персонаж не пересекает (или пересекает при “break event”).
- **Taboo** — запрет с высокой эмоциональной/идентификационной ценой нарушения.
- **Rationalization** — оправдание, позволяющее нарушить ценность “не разрушая” самообраз.
- **Dilemma** — ситуация, где одновременно нельзя сохранить две ценности.

---

## 4) BOUNDARIES (MANDATORY)

### IN SCOPE (OWNS)
- иерархия ценностей (ranked)
- красные линии/табу + условия “сломов”
- правила моральных конфликтов
- типичные оправдания и когнитивные “обходы”
- совместимость с инвариантами персонажа

### OUT OF SCOPE (HARD)
- эмоциональная динамика (психология)
- поведенческая реализация (behavior)
- развитие ценностей во времени (это `10__CHARACTER_EVOLUTION_ENG`, а “слом” через 09)

### COLLISION RULE (ROUTING)
- Если ценность меняется из-за травмы/перелома → `09__GROWTH_TRAUMA_ENG` → затем обновление через `10__CHARACTER_EVOLUTION_ENG`
- Если вопрос “как выбирает в конкретной сцене” → `05__CHARACTER_BEHAVIOR_ENG`
- Если конфликт морали связан с законами мира/культуры → `04_DOMAIN_WORLD_ENGINES/*` (как внешняя норма), но внутренняя позиция остаётся здесь

---

## 5) OUTPUT SCHEMAS (MANDATORY)

### A) `VALUE_HIERARCHY`
**MUST (fields):**
- `character_id`
- `version`
- `values[]` (ranked list)
- `priority_rules[]`
- `conflict_pairs[]`
- `identity_claims[]` (what they believe about themselves)
- `open_unknowns[]`
- `scope_notes`

**Value (minimum):**
- `value_id`
- `name`
- `rank` (int; 1 = highest)
- `definition` (short)
- `what_it_demands` (actions)
- `what_it_forbids` (actions)
- `evidence` (optional: seed/scene notes)
- `stability` (`STABLE|FRAGILE|CONDITIONAL`)

**Priority rule (minimum):**
- `id`
- `rule_text` (e.g., "Truth outranks Loyalty unless child safety is threatened")
- `strength` (`HARD|SOFT`)

**Conflict pair (minimum):**
- `value_A`
- `value_B`
- `default_winner` (A/B/SITUATIONAL)
- `trigger_that_flips` (short)

**VALIDATION:**
- ranks must be unique and contiguous (1..N)
- if any value forbids an action that motivations require, mark a dilemma route (not hidden)

**STORAGE:**
- `PROJECT_ARTIFACTS/<project>/CHARACTERS/VALUES/<character_id>/VALUE_HIERARCHY.md`

---

### B) `MORAL_BOUNDARY_MAP`
**MUST (fields):**
- `character_id`
- `boundaries[]`
- `taboos[]`
- `break_conditions[]`
- `rationalizations[]`
- `severity_model` (how boundary violations are classified)
- `open_unknowns[]`

**Boundary (minimum):**
- `boundary_id`
- `statement` (e.g., "will not kill innocents")
- `type` (enum: `HARM|BETRAYAL|LIE|ABANDON|THEFT|CRUELTY|CONTROL|SACRIFICE`)
- `strength` (`HARD|SOFT`)
- `why` (short)
- `violation_cost` (what it costs internally/externally)
- `break_requires` (enum: `TRAUMA|REVELATION|DESPERATION|IDEAL_SHATTER|NONE`)
- `notes`

**Taboo (minimum):**
- `taboo_id`
- `topic`
- `trigger_signals[]`
- `avoidance_behavior` (short)
- `why_taboo` (short)

**Rationalization (minimum):**
- `id`
- `when` (trigger)
- `story` (self-justification text)
- `what_value_it_protects` (value_id)

**VALIDATION:**
- if `strength=HARD` then `break_requires` cannot be `NONE`
- boundary violations must be classifiable via severity_model

**STORAGE:**
- `PROJECT_ARTIFACTS/<project>/CHARACTERS/VALUES/<character_id>/MORAL_BOUNDARY_MAP.md`

---

### C) `DILEMMA_RULESET`
**MUST (fields):**
- `character_id`
- `dilemmas[]`
- `resolution_rules[]`
- `anti_patterns[]`
- `checks[]`

**Dilemma (minimum):**
- `dilemma_id`
- `setup` (short)
- `values_in_conflict[]` (value ids)
- `options[]` (at least 2)
- `default_choice` (option id or `UNKNOWN`)
- `costs[]` (cost per option)
- `notes`

**Resolution rule (minimum):**
- `id`
- `rule_text`
- `strength` (`HARD|SOFT`)
- `when_applies`

**VALIDATION:**
- every dilemma must reference existing value ids
- options must include at least one “moral cost” (otherwise it’s not a dilemma)

**STORAGE:**
- `PROJECT_ARTIFACTS/<project>/CHARACTERS/VALUES/<character_id>/DILEMMA_RULESET.md`

---

## 6) PROCESS (PIPELINE)
1) Read character core + invariants + traits.
2) Draft value list (5–10) and rank them.
3) Define boundaries:
   - 2–5 HARD (requires break event)
   - 2–6 SOFT (situational)
4) Define taboo topics (0–5).
5) Define rationalizations:
   - what they say to themselves when violating a value
6) Generate dilemmas:
   - conflict pairs that will appear in story contexts
7) Validate:
   - no hidden contradiction with invariants/motivation
8) Emit outputs.

---

## 7) GATES (S0 BLOCKERS)
S0 (BLOCK) if:
- a declared HARD boundary has `break_requires=NONE`
- value hierarchy contradicts a HARD invariant without routing (identity collapse without mechanism)
- core role requires actions forbidden by values with no dilemma or break path

S1 (HIGH) if:
- values are generic and non-actionable (“be good”) with no demands/forbids
- too many values have `stability=CONDITIONAL` without rules (incoherent)

S2/S3: quality warnings.

---

## 8) NOTES FOR DOWNSTREAM ENGINES
- Behavior engine uses boundaries + priority rules to simulate choices.
- Dialogue engine uses rationalizations to generate self-justification and subtext.
- Growth/Trauma engine uses boundary breaks as potential break events.
- Evolution engine updates values across time with explicit events, not silently.

---

LOCK: OPEN
