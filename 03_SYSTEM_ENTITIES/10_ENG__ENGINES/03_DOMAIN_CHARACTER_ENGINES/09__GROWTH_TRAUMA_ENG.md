# GROWTH & TRAUMA ENGINE
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/03_DOMAIN_CHARACTER_ENGINES/09__GROWTH_TRAUMA_ENG.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 03_DOMAIN_CHARACTER_ENGINES
ENGINE: 09__GROWTH_TRAUMA_ENG
DOC_TYPE: ENGINE
LEVEL: L2
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.ENG.CHAR.GROWTH.TRAUMA.001
OWNER: SYSTEM
ROLE: Model character transformation events: trauma, breakthroughs, boundary breaks, and growth milestones; produce change events + constraints for evolution updates.

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Growth & Trauma Engine created: break events, trauma signatures, growth milestones, and post-event constraint rules."
- REASON: "Characters need explicit transformation mechanics; otherwise changes are arbitrary and non-canon."
- IMPACT: "Evolution becomes auditable: changes have causes, thresholds, and after-effects."
- CHANGE_ID: UE.CHG.2026-01-08.ENG.CHAR.GROWTH.TRAUMA.001

---

## 0) PURPOSE (LAW)
Этот движок описывает **события трансформации** персонажа:
- травматические события (trauma events)
- переломы морали/границ (boundary break)
- инсайты/прорывы (breakthrough)
- ростовые вехи (growth milestones)
- пост-эффекты и “шрамы” (after-effects)
- требования восстановления (recovery requirements)

Выход — список change-events, которые **разрешают** (или запрещают) изменение внутренних моделей в evolution engine.

---

## 1) NON-GOALS (HARD)
Движок НЕ делает:
- постоянное обновление профиля персонажа (это `10__CHARACTER_EVOLUTION_ENG`)
- поведение в конкретной сцене (05)
- диалоги как намерения/голос (07/08)
- сюжетную структуру глобально (narrative family)
- мировые законы (world family)

---

## 2) MINI-CONTRACT (MANDATORY)

### CONSUMES (1–18)
- `CORE_IDENTITY`
- `CORE_STATE`
- `CHARACTER_CORE_PASSPORT`
- `CHARACTER_INVARIANTS`
- `CHARACTER_TRAIT_PROFILE`
- `MOTIVATION_DESIRE_STACK` (optional)
- `VALUE_HIERARCHY`
- `MORAL_BOUNDARY_MAP`
- `DILEMMA_RULESET` (optional)
- `INNER_STATE_MODEL` (optional)
- `TRIGGER_DEFENSE_MAP` (optional)
- `STRESS_ESCALATION_LADDER` (optional)
- `DECISION_POLICY_MODEL` (optional)
- `RELATIONSHIP_GRAPH` (optional)
- `RELATIONSHIP_CONTRACTS` (optional)
- `EVENT_LOG` (optional: what happened already)
- `SCENE_BLUEPRINT_SET` (optional)
- `STAKE_CONTEXT` (optional)

### PRODUCES (1–7)
- `TRANSFORMATION_EVENT_SET`
- `TRAUMA_SIGNATURES`
- `RECOVERY_CONSTRAINTS`

### DEPENDS_ON
- `[03_DOMAIN_CHARACTER_ENGINES/03__MORAL_VALUE_ENG, 03_DOMAIN_CHARACTER_ENGINES/04__CHARACTER_PSYCHOLOGY_ENG, 03_DOMAIN_CHARACTER_ENGINES/06__RELATIONSHIP_ENG]`

### OUTPUT_TARGET
- `PROJECT_ARTIFACTS/<project>/CHARACTERS/GROWTH_TRAUMA/`

---

## 3) DEFINITIONS (LOCAL)
- **Transformation Event** — событие, которое разрешает изменение внутренних моделей.
- **Trauma Signature** — устойчивые симптомы/паттерны после травмы.
- **Boundary Break** — пересечение HARD moral boundary (с ценой).
- **Breakthrough** — позитивная трансформация (insight, integration).
- **Recovery Constraint** — условие, без которого нельзя “откатить” последствия.

---

## 4) BOUNDARIES (MANDATORY)

### IN SCOPE (OWNS)
- каталог трансформационных событий
- условия запуска (thresholds)
- после-эффекты (what changes temporarily / what becomes possible)
- требования восстановления
- routing в evolution engine

### OUT OF SCOPE (HARD)
- “медленная эволюция” без событий (это evolution engine)
- постановка сцен/битов (narrative)
- терапевтическая реалистичность как исследование (может быть KB/research)

### COLLISION RULE (ROUTING)
- Если нужно обновить значения/инварианты/политики после события → `10__CHARACTER_EVOLUTION_ENG`
- Если нужно расписать сцену травмы → narrative scene engine
- Если триггеры обусловлены миром (война/культура) → world engines как внешние constraints

---

## 5) OUTPUT SCHEMAS (MANDATORY)

### A) `TRANSFORMATION_EVENT_SET`
**MUST (fields):**
- `character_id`
- `version`
- `events[]`
- `timeline_hints[]` (optional)
- `open_unknowns[]`
- `scope_notes`

**Event (minimum):**
- `event_id`
- `event_type` (enum: `TRAUMA|BOUNDARY_BREAK|BREAKTHROUGH|LOSS|BETRAYAL|REVELATION|HUMILIATION|VIOLENCE|RESCUE|FAILURE|SUCCESS`)
- `trigger_conditions[]` (thresholds; can reference ladder/relationship variables)
- `required_context` (optional)
- `core_conflict` (what values/motives collide)
- `what_breaks_or_changes` (short)
- `immediate_effects` (variable deltas, policy switches)
- `long_effects` (new constraints/permissions)
- `cost` (what is paid)
- `witnesses[]` (optional counterpart ids)
- `evidence_ref` (optional: scene/event log)
- `route_to` (usually evolution engine)
- `notes`

**Trigger condition (minimum):**
- `type` (enum: `STRESS_LEVEL|BOUNDARY_PRESSURE|RELATIONSHIP_THRESHOLD|LOSS_THRESHOLD|REPEAT_OFFENSE|POWER_SHIFT|SURVIVAL_THREAT`)
- `expression` (short deterministic condition)

**VALIDATION:**
- boundary break must reference a HARD boundary id
- each event must include cost + route_to
- long_effects must be actionable (constraints/permissions), not “feels different”

**STORAGE:**
- `PROJECT_ARTIFACTS/<project>/CHARACTERS/GROWTH_TRAUMA/<character_id>/TRANSFORMATION_EVENT_SET.md`

---

### B) `TRAUMA_SIGNATURES`
**MUST (fields):**
- `character_id`
- `version`
- `signatures[]`
- `triggers[]`
- `coping_shifts[]`
- `relationship_impacts[]`
- `open_unknowns[]`

**Signature (minimum):**
- `signature_id`
- `origin_event_id`
- `symptoms[]` (observable + internal)
- `avoidances[]`
- `defense_changes[]`
- `speech_changes[]` (optional)
- `behavior_changes[]` (optional)
- `severity` (`LOW|MEDIUM|HIGH`)
- `duration` (enum: `SHORT|MEDIUM|LONG|CHRONIC`)
- `notes`

**VALIDATION:**
- origin_event_id must exist in event set
- symptoms must include at least one observable signal (not all internal)

**STORAGE:**
- `PROJECT_ARTIFACTS/<project>/CHARACTERS/GROWTH_TRAUMA/<character_id>/TRAUMA_SIGNATURES.md`

---

### C) `RECOVERY_CONSTRAINTS`
**MUST (fields):**
- `character_id`
- `version`
- `constraints[]`
- `recovery_paths[]`
- `gates[]`
- `open_unknowns[]`

**Constraint (minimum):**
- `constraint_id`
- `origin_event_id`
- `what_is_limited` (value change, trust rebuild, aggression, intimacy)
- `until` (condition)
- `risk_if_ignored` (`S0|S1|S2|S3`)
- `notes`

**Recovery path (minimum):**
- `path_id`
- `origin_event_id`
- `steps[]` (3..7)
- `required_cost`
- `expected_changes` (what becomes possible again)

**Gate (minimum):**
- `gate_id`
- `name`
- `pass_condition`
- `fail_condition`
- `severity`

**VALIDATION:**
- any S0 risk constraint must have explicit until condition
- recovery path must reference measurable deltas (variables/policies), not vague

**STORAGE:**
- `PROJECT_ARTIFACTS/<project>/CHARACTERS/GROWTH_TRAUMA/<character_id>/RECOVERY_CONSTRAINTS.md`

---

## 6) PROCESS (PIPELINE)
1) Identify pressure points:
   - HARD moral boundaries, fragile values, high-volatility psych variables
2) List candidate transformation events by category:
   - trauma / boundary break / breakthrough
3) Define triggers as deterministic thresholds (stress, relationship, loss).
4) Define immediate + long effects:
   - what changes now vs what becomes possible later
5) Define trauma signatures (symptoms/avoidance/defense shifts).
6) Define recovery constraints + paths.
7) Validate and emit outputs.
8) Route to evolution engine for persistent updates.

---

## 7) GATES (S0 BLOCKERS)
S0 (BLOCK) if:
- boundary break exists without a referenced HARD boundary id
- event declares change without cost
- recovery constraints missing for high-severity trauma
- long effects are non-actionable (“becomes stronger” without rules)

S1 (HIGH) if:
- too many events with identical triggers (non-distinct)
- signatures are all internal (no observable signals)

S2/S3: quality warnings.

---

## 8) NOTES FOR DOWNSTREAM ENGINES
- Evolution engine uses events as authorization to update values/traits/policies.
- Dialogue/speech engines can apply signature speech changes under triggers.
- Continuity engine can track whether recovery gates were satisfied before “healing”.

---

LOCK: OPEN
