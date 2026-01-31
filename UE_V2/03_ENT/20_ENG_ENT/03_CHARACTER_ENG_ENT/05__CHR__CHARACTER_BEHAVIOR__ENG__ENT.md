# CHARACTER BEHAVIOR ENGINE
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/03_DOMAIN_CHARACTER_ENGINES/05__CHARACTER_BEHAVIOR_ENG.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 03_DOMAIN_CHARACTER_ENGINES
ENGINE: 05__CHARACTER_BEHAVIOR_ENG
DOC_TYPE: ENGINE
LEVEL: L2
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.ENG.CHAR.BEHAVIOR.001
OWNER: SYSTEM
ROLE: Convert character core + motivation + values + psychology into deterministic behavior rules: decision heuristics, action preferences, situational policies, and response patterns under stress.

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Character Behavior Engine created: decision policy, action preference matrix, stress response policies, and consistency checks."
- REASON: "Needed a bridge from internal models to observable actions without writing scenes."
- IMPACT: "Scene construction and event engines can generate believable actions consistently."
- CHANGE_ID: UE.CHG.2026-01-08.ENG.CHAR.BEHAVIOR.001

---

## 0) PURPOSE (LAW)
Этот движок фиксирует **как персонаж выбирает действия**:
- эвристики решений (decision heuristics)
- предпочтения действий (approach/avoid, direct/indirect)
- реакции на давление (stress policies)
- правила взаимодействия (cooperate/compete/withdraw)
- “если-то” политики для типовых ситуаций

Выход — **policy model**, который downstream-движки применяют к сценам/ивентам.

---

## 1) NON-GOALS (HARD)
Движок НЕ делает:
- мотивации/желания (02)
- ценности/мораль (03)
- психология/внутренние переменные (04)
- отношения как отдельная система (06)
- диалог/естественность речи (07/08)
- сюжетную структуру/сценарий (narrative family)
- production постановку/монтаж

---

## 2) MINI-CONTRACT (MANDATORY)

### CONSUMES (1–14)
- `CORE_IDENTITY`
- `CORE_STATE`
- `CHARACTER_CORE_PASSPORT`
- `CHARACTER_INVARIANTS`
- `CHARACTER_TRAIT_PROFILE`
- `MOTIVATION_DESIRE_STACK`
- `FEAR_AVOIDANCE_MAP` (optional)
- `INCENTIVE_MODEL` (optional)
- `VALUE_HIERARCHY`
- `MORAL_BOUNDARY_MAP`
- `DILEMMA_RULESET` (optional)
- `INNER_STATE_MODEL` (optional but recommended)
- `TRIGGER_DEFENSE_MAP` (optional)
- `STRESS_ESCALATION_LADDER` (optional)

### PRODUCES (1–7)
- `DECISION_POLICY_MODEL`
- `ACTION_PREFERENCE_MATRIX`
- `STRESS_RESPONSE_POLICIES`

### DEPENDS_ON
- `[03_DOMAIN_CHARACTER_ENGINES/01__CHARACTER_CORE_ENG, 03_DOMAIN_CHARACTER_ENGINES/02__MOTIVATION_DESIRE_ENG, 03_DOMAIN_CHARACTER_ENGINES/03__MORAL_VALUE_ENG, 03_DOMAIN_CHARACTER_ENGINES/04__CHARACTER_PSYCHOLOGY_ENG]`

### OUTPUT_TARGET
- `PROJECT_ARTIFACTS/<project>/CHARACTERS/BEHAVIOR/`

---

## 3) DEFINITIONS (LOCAL)
- **Policy** — правило выбора действия по входным условиям.
- **Heuristic** — упрощённое правило (“если риск высокий — выбирай контроль”).
- **Preference Matrix** — таблица предпочтений видов действий.
- **Stress Policy** — как изменяются эвристики при росте стресса.
- **Violation** — действие, которое ломает moral boundary или invariant.

---

## 4) BOUNDARIES (MANDATORY)

### IN SCOPE (OWNS)
- перевод внутренних моделей (motives/values/psy) в наблюдаемое поведение
- правила выбора и приоритеты
- анти-поведенческие запреты (что не делает)
- стрессовые переключатели (how rules change under pressure)
- контроль нарушений морали/инвариантов (с routing)

### OUT OF SCOPE (HARD)
- генерация сцены/диалога (narrative/dialogue engines)
- изменение ценностей/психики (growth/evolution)
- “отношения” как двусторонняя система (relationship engine владелец)

### COLLISION RULE (ROUTING)
- Если поведение требует нарушить моральную границу → сначала зафиксировать дилемму/слом через `03__MORAL_VALUE_ENG` или `09__GROWTH_TRAUMA_ENG`
- Если поведение — это речь/манера речи → `07__DIALOGUE_ENG` / `08__SPEECH_NATURALIZATION_ENG`
- Если поведение определяется отношениями (контрактами/статусом) → `06__RELATIONSHIP_ENG`

---

## 5) OUTPUT SCHEMAS (MANDATORY)

### A) `DECISION_POLICY_MODEL`
**MUST (fields):**
- `character_id`
- `version`
- `core_heuristics[]` (5..15)
- `priority_stack[]` (ordered)
- `forbidden_actions[]`
- `dilemma_handlers[]` (optional)
- `consistency_checks[]`
- `open_unknowns[]`
- `scope_notes`

**Heuristic (minimum):**
- `heuristic_id`
- `when` (conditions; short)
- `goal_alignment` (which want/need it serves)
- `value_alignment` (which value it protects)
- `do` (action type)
- `avoid` (action type)
- `strength` (`HARD|SOFT`)
- `cost_acceptance` (what cost is acceptable)
- `notes`

**Priority item (minimum):**
- `rank`
- `rule` (e.g., "Protect HARD boundaries first")
- `strength` (`HARD|SOFT`)

**Forbidden action (minimum):**
- `action_type`
- `because` (invariant/boundary reference)
- `severity_if_forced` (`S0|S1|S2|S3`)
- `route_to` (engine pointer)

**Dilemma handler (minimum):**
- `handler_id`
- `when` (dilemma pattern)
- `default_strategy` (enum: `SACRIFICE_A|SACRIFICE_B|STALL|CONFESS|FLEE|NEGOTIATE`)
- `notes`

**Consistency check (minimum):**
- `check_id`
- `check_text` (e.g., "If action violates HARD boundary -> must emit violation event + route")
- `severity` (`S0|S1|S2|S3`)

**VALIDATION:**
- at least one HARD heuristic must reference HARD invariants/boundaries
- forbidden actions must align with moral boundaries/invariants (no random forbids)

**STORAGE:**
- `PROJECT_ARTIFACTS/<project>/CHARACTERS/BEHAVIOR/<character_id>/DECISION_POLICY_MODEL.md`

---

### B) `ACTION_PREFERENCE_MATRIX`
**MUST (fields):**
- `character_id`
- `version`
- `dimensions` (standard set)
- `matrix[]`
- `notes`

**Standard dimensions (recommended):**
- `DIRECTNESS` (DIRECT vs INDIRECT)
- `AGGRESSION` (LOW..HIGH)
- `RISK` (LOW..HIGH)
- `CONTROL` (LOW..HIGH)
- `SOCIAL` (SEEK vs AVOID)
- `TRUTHFULNESS` (LOW..HIGH)

**Matrix row (minimum):**
- `context` (enum: `BASELINE|TRUSTED_ALLY|STRANGER|AUTHORITY|ENEMY|ROMANTIC|FAMILY|PUBLIC`)
- `directness` (0..100)
- `aggression` (0..100)
- `risk` (0..100)
- `control` (0..100)
- `social` (0..100)
- `truthfulness` (0..100)
- `why` (short)

**VALIDATION:**
- baseline row required
- truthfulness must not contradict HARD boundary “never lies” without route flag (S0)

**STORAGE:**
- `PROJECT_ARTIFACTS/<project>/CHARACTERS/BEHAVIOR/<character_id>/ACTION_PREFERENCE_MATRIX.md`

---

### C) `STRESS_RESPONSE_POLICIES`
**MUST (fields):**
- `character_id`
- `version`
- `stress_levels[]` (align with ladder if present)
- `policy_switches[]`
- `break_behavior[]` (optional)
- `recovery_behavior[]`

**Stress level policy (minimum):**
- `level_ref` (ladder level id or range)
- `heuristics_added[]`
- `heuristics_disabled[]`
- `preference_shifts[]` (dimension deltas)
- `communication_shift` (short)
- `relationship_shift` (short)

**Policy switch (minimum):**
- `when` (trigger or threshold)
- `switch` (what changes)
- `cost` (short)

**Recovery behavior (minimum):**
- `method`
- `what_it_looks_like`
- `time_scale` (`FAST|SLOW`)
- `notes`

**VALIDATION:**
- if break_behavior exists, must reference recovery requirements (else S1)
- disabled heuristics must not disable all moral constraints (S0)

**STORAGE:**
- `PROJECT_ARTIFACTS/<project>/CHARACTERS/BEHAVIOR/<character_id>/STRESS_RESPONSE_POLICIES.md`

---

## 6) PROCESS (PIPELINE)
1) Read core/motives/values/psy.
2) Draft core heuristics:
   - protect invariants/boundaries
   - pursue top wants within acceptable cost
3) Build priority stack (what always wins).
4) Build forbidden actions list (from HARD boundaries/invariants).
5) Build preference matrix for contexts.
6) Add stress switches (from ladder/triggers).
7) Validate violations:
   - detect where motives push against morals
   - add dilemma handlers or route to growth/values
8) Emit outputs.

---

## 7) GATES (S0 BLOCKERS)
S0 (BLOCK) if:
- policy permits violating HARD boundary/invariant with no handler/route
- stress policies remove all moral constraints (“anything goes”) with no break event routing
- preference matrix contradicts declared HARD constraints without a flagged exception path

S1 (HIGH) if:
- heuristics are vague (“acts randomly”) or non-actionable
- stress ladder present but not referenced (no policy switches)

S2/S3: quality warnings.

---

## 8) NOTES FOR DOWNSTREAM ENGINES
- Narrative/Scene engines can use this model to pick actions consistent with motive/value/psy.
- Relationship engine can override context rows via relationship contracts (but must be explicit).
- Dialogue engine uses communication_shift hints (behavior-level, not voice-level).

---

LOCK: OPEN
