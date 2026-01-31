# MOTIVATION & DESIRE ENGINE
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/03_DOMAIN_CHARACTER_ENGINES/02__MOTIVATION_DESIRE_ENG.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 03_DOMAIN_CHARACTER_ENGINES
ENGINE: 02__MOTIVATION_DESIRE_ENG
DOC_TYPE: ENGINE
LEVEL: L2
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.ENG.CHAR.MOTIVE.001
OWNER: SYSTEM
ROLE: Produce a deterministic motivation/desire model for a character: needs, wants, fears, incentives, conflicts, and pursuit rules that remain compatible with the character core and world constraints.

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Motivation & Desire Engine created: desire stack, fear map, incentive model, and pursuit rules."
- REASON: "Character core alone does not explain choices; motivation layer is required for believable action."
- IMPACT: "Behavior/relationships/dialogue can be derived consistently from explicit motivations."
- CHANGE_ID: UE.CHG.2026-01-08.ENG.CHAR.MOTIVE.001

---

## 0) PURPOSE (LAW)
Этот движок фиксирует **почему персонаж действует**:
- желания (wants) и потребности (needs)
- страхи/избегания (fears/avoidance)
- стимулы (incentives) и цены (costs)
- внутренние конфликты мотиваций
- правила преследования цели (pursuit rules) и точки отказа

Выход — модель мотивации, а не “сцены”.

---

## 1) NON-GOALS (HARD)
Движок НЕ делает:
- мораль/ценности как нормы выбора (это `03__MORAL_VALUE_ENG`)
- психологические состояния и травмы как причины мотиваций (это `04__CHARACTER_PSYCHOLOGY_ENG` и `09__GROWTH_TRAUMA_ENG`)
- поведенческие алгоритмы решений (это `05__CHARACTER_BEHAVIOR_ENG`)
- сюжетную структуру (narrative family)
- миростроение (world family)
- постановку/монтаж (production family)

---

## 2) MINI-CONTRACT (MANDATORY)

### CONSUMES (1–9)
- `CORE_IDENTITY`
- `CORE_STATE`
- `CHARACTER_CORE_PASSPORT`
- `CHARACTER_INVARIANTS`
- `CHARACTER_TRAIT_PROFILE`
- `WORLD_LAW_SEEDS` (optional)
- `NARRATIVE_PREMISE` (optional)
- `STAKE_CONTEXT` (optional: what is at stake for this character, if available)
- `RELATIONSHIP_SEEDS` (optional)

### PRODUCES (1–7)
- `MOTIVATION_DESIRE_STACK`
- `FEAR_AVOIDANCE_MAP`
- `INCENTIVE_MODEL`

### DEPENDS_ON
- `[03_DOMAIN_CHARACTER_ENGINES/01__CHARACTER_CORE_ENG]`

### OUTPUT_TARGET
- `PROJECT_ARTIFACTS/<project>/CHARACTERS/MOTIVATION/`

---

## 3) DEFINITIONS (LOCAL)
- **Need** — фундаментальная потребность (без которой “ломается” персонаж).
- **Want** — конкретная цель/объект желания в текущей истории.
- **Fear** — то, что персонаж избегает (потеря, боль, истина, зависимость).
- **Incentive** — стимул, который усиливает/ослабляет преследование цели.
- **Motive Conflict** — конфликт целей (want vs want) или (want vs need) или (want vs invariant).

---

## 4) BOUNDARIES (MANDATORY)

### IN SCOPE (OWNS)
- формализация wants/needs/fears
- правила приоритетов (какая мотивация сильнее и когда)
- мотивационные конфликты и компромиссы
- “что заставит отказаться” (stop conditions)
- совместимость с core invariants

### OUT OF SCOPE (HARD)
- ценностная этика как закон выбора (values)
- психология/травма как источник паттернов (психология/рост)
- детальный алгоритм решений (behavior)
- сюжетные события и сцены

### COLLISION RULE (ROUTING)
- Если конфликт “могу/не могу” из-за мира → `04_DOMAIN_WORLD_ENGINES/*`
- Если конфликт “правильно/неправильно” → `03__MORAL_VALUE_ENG`
- Если конфликт “почему вообще такая мотивация” (травма/психика) → `04__CHARACTER_PSYCHOLOGY_ENG` / `09__GROWTH_TRAUMA_ENG`
- Если конфликт “как выбирает в ситуации” → `05__CHARACTER_BEHAVIOR_ENG`

---

## 5) OUTPUT SCHEMAS (MANDATORY)

### A) `MOTIVATION_DESIRE_STACK`
**MUST (fields):**
- `character_id`
- `version`
- `needs[]` (0..5)
- `wants[]` (1..7)
- `priority_rules[]`
- `conflicts[]`
- `pursuit_rules[]`
- `stop_conditions[]`
- `open_unknowns[]`
- `scope_notes`

**Need (minimum):**
- `id`
- `statement` (e.g., "needs safety")
- `domain` (enum: `SAFETY|BELONGING|CONTROL|FREEDOM|RECOGNITION|LOVE|TRUTH|MEANING|SURVIVAL`)
- `how_it_shows` (behavioral evidence)
- `when_threatened` (typical reaction)

**Want (minimum):**
- `id`
- `goal` (concrete)
- `time_horizon` (enum: `NOW|SHORT|MID|LONG`)
- `stakes_if_fail` (short)
- `compatibility_with_invariants` (`OK|RISK|CONFLICT`)
- `notes`

**Priority rule (minimum):**
- `id`
- `rule_text` (e.g., "When fear X is triggered, want Y drops one tier")
- `strength` (`HARD|SOFT`)

**Conflict (minimum):**
- `id`
- `type` (enum: `WANT_VS_WANT|WANT_VS_NEED|WANT_VS_INVARIANT|NEED_VS_INVARIANT`)
- `items_involved[]` (ids)
- `default_resolution` (enum: `A_WINS|B_WINS|SITUATIONAL|PARALYSIS`)
- `resolution_trigger` (what changes it)
- `notes`

**Pursuit rule (minimum):**
- `id`
- `when` (trigger)
- `do` (pursuit behavior)
- `cost_acceptance` (what cost is acceptable)
- `limit` (what stops the pursuit)

**Stop condition (minimum):**
- `id`
- `condition_text`
- `severity` (`S0|S1|S2|S3`)
- `route_to` (optional engine pointer)

**VALIDATION:**
- every want marked `CONFLICT` with invariants must appear in `conflicts[]`
- must have at least one want (unless explicitly “no-goal character” with rationale)
- stop conditions cannot contradict core invariants

**STORAGE:**
- `PROJECT_ARTIFACTS/<project>/CHARACTERS/MOTIVATION/<character_id>/MOTIVATION_DESIRE_STACK.md`

---

### B) `FEAR_AVOIDANCE_MAP`
**MUST (fields):**
- `character_id`
- `fears[]`
- `avoidance_behaviors[]`
- `fear_triggers[]`
- `deescalation_methods[]` (optional)
- `open_unknowns[]`

**Fear (minimum):**
- `fear_id`
- `fear_of` (short)
- `category` (enum: `LOSS|PAIN|HUMILIATION|ABANDONMENT|CONTROL_LOSS|TRUTH|DEATH|POWERLESSNESS|INTIMACY`)
- `trigger_signals[]`
- `avoidance_pattern` (short)
- `risk` (`LOW|MEDIUM|HIGH`)
- `notes`

**VALIDATION:**
- each fear must have at least one trigger signal
- avoidance must not violate hard invariants (unless routed to growth/trauma)

**STORAGE:**
- `PROJECT_ARTIFACTS/<project>/CHARACTERS/MOTIVATION/<character_id>/FEAR_AVOIDANCE_MAP.md`

---

### C) `INCENTIVE_MODEL`
**MUST (fields):**
- `character_id`
- `incentives[]`
- `costs[]`
- `tradeoff_rules[]`
- `pressure_responses[]`

**Incentive (minimum):**
- `id`
- `type` (enum: `REWARD|THREAT|STATUS|LOVE|TRUTH|FREEDOM|SAFETY|RESOURCE`)
- `what_it_offers` (short)
- `strength` (0..100)
- `conditions[]` (when it applies)

**Cost (minimum):**
- `id`
- `type` (enum: `MORAL|PHYSICAL|SOCIAL|RESOURCE|TIME|IDENTITY`)
- `what_it_costs`
- `tolerance` (0..100)
- `break_point` (when pursuit stops)

**Tradeoff rule (minimum):**
- `id`
- `rule_text`
- `strength` (`HARD|SOFT`)

**VALIDATION:**
- incentive strengths and cost tolerance must be plausible given trait profile (else S1 warning)

**STORAGE:**
- `PROJECT_ARTIFACTS/<project>/CHARACTERS/MOTIVATION/<character_id>/INCENTIVE_MODEL.md`

---

## 6) PROCESS (PIPELINE)
1) Read character core (identity + invariants + traits).
2) Derive candidate needs (0–3) and wants (1–5) consistent with invariants.
3) Identify fears/avoidance that explain “why not”.
4) Build conflicts and priority rules.
5) Build incentives and costs; define tradeoffs.
6) Validate:
   - no hidden invariant breaks
   - conflicts accounted for
7) Emit outputs.

---

## 7) GATES (S0 BLOCKERS)
S0 (BLOCK) if:
- a primary want requires breaking a HARD invariant without routing to growth/trauma
- motivation stack has no actionable want for an active story role (unless explicitly passive role with rationale)
- incentives/costs define impossible behavior under world constraints (if provided)

S1 (HIGH) if:
- wants are generic (“be happy”) with no concrete goal
- fear map contradicts trait stress expression without explanation

S2/S3: quality warnings.

---

## 8) NOTES FOR DOWNSTREAM ENGINES
- Values engine uses wants/needs to test moral tradeoffs.
- Behavior engine turns pursuit rules into decision heuristics.
- Relationship engine uses wants/fears to model attachment and conflict.
- Dialogue engine uses wants/avoidance to drive subtext.

---

LOCK: OPEN
