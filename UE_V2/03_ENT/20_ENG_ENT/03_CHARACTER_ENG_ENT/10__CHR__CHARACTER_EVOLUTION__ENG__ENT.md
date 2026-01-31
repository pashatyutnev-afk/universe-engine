# CHARACTER EVOLUTION ENGINE
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/03_DOMAIN_CHARACTER_ENGINES/10__CHARACTER_EVOLUTION_ENG.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 03_DOMAIN_CHARACTER_ENGINES
ENGINE: 10__CHARACTER_EVOLUTION_ENG
DOC_TYPE: ENGINE
LEVEL: L2
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.ENG.CHAR.EVOLUTION.001
OWNER: SYSTEM
ROLE: Apply authorized transformation events to update character models over time: traits, values, moral boundaries, psychology baselines, behavior policies, relationship variables; produce versioned snapshots and change audit records.

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Character Evolution Engine created: versioned snapshots, authorized change application, and drift checks."
- REASON: "Character change must be deterministic and auditable; otherwise canon drifts."
- IMPACT: "Characters can evolve across seasons/arcs with traceable reasons and constraints."
- CHANGE_ID: UE.CHG.2026-01-08.ENG.CHAR.EVOLUTION.001

---

## 0) PURPOSE (LAW)
Этот движок делает **эволюцию персонажа** детерминированной:
- изменения разрешены только через `TRANSFORMATION_EVENT_SET`
- изменения применяются как patch’и к моделям (values/traits/psy/behavior/relationships)
- каждый апдейт создаёт версионный snapshot и audit запись
- запрещает “тихие” изменения без причины

---

## 1) NON-GOALS (HARD)
Движок НЕ делает:
- создание самих трансформационных событий (это `09__GROWTH_TRAUMA_ENG`)
- генерацию сцен/диалога
- изменение мира/законов мира (world family)
- чисто продакшн-монтаж/видео/аудио

---

## 2) MINI-CONTRACT (MANDATORY)

### CONSUMES (1–20)
- `CORE_IDENTITY`
- `CORE_STATE`
- `CHARACTER_CORE_PASSPORT`
- `CHARACTER_INVARIANTS`
- `CHARACTER_TRAIT_PROFILE`
- `MOTIVATION_DESIRE_STACK` (optional)
- `VALUE_HIERARCHY`
- `MORAL_BOUNDARY_MAP`
- `INNER_STATE_MODEL`
- `TRIGGER_DEFENSE_MAP`
- `STRESS_ESCALATION_LADDER`
- `DECISION_POLICY_MODEL`
- `ACTION_PREFERENCE_MATRIX`
- `STRESS_RESPONSE_POLICIES`
- `RELATIONSHIP_GRAPH` (optional)
- `RELATIONSHIP_CONTRACTS` (optional)
- `RELATIONSHIP_SHIFT_RULESET` (optional)
- `TRANSFORMATION_EVENT_SET` (required)
- `TRAUMA_SIGNATURES` (optional)
- `RECOVERY_CONSTRAINTS` (optional)
- `EVENT_LOG` (optional)
- `TIME_CONTEXT` (optional: where on timeline)

### PRODUCES (1–7)
- `CHARACTER_SNAPSHOT_SET`
- `MODEL_PATCH_LOG`
- `EVOLUTION_AUDIT_RECORDS`

### DEPENDS_ON
- `[03_DOMAIN_CHARACTER_ENGINES/09__GROWTH_TRAUMA_ENG, 00_GOVERNANCE_ENGINES/01__AUDIT_LOG_ENG]`

### OUTPUT_TARGET
- `PROJECT_ARTIFACTS/<project>/CHARACTERS/EVOLUTION/`

---

## 3) DEFINITIONS (LOCAL)
- **Snapshot** — состояние всех моделей персонажа на момент времени (versioned).
- **Patch** — минимальный набор изменений (delta) к конкретной модели.
- **Authorization** — событие трансформации, разрешающее patch.
- **Drift** — изменение без разрешения (неканон).
- **Recovery Gate** — условия восстановления, ограничивающие patch.

---

## 4) BOUNDARIES (MANDATORY)

### IN SCOPE (OWNS)
- применение patch’ей к моделям персонажа
- контроль разрешений и recovery constraints
- версионирование snapshot’ов
- аудит и предотвращение drift

### OUT OF SCOPE (HARD)
- генерация событий трансформации (09)
- сценостроение/диалоги
- дизайн мира

### COLLISION RULE (ROUTING)
- Если изменения касаются “канона системы” и требуют governance пайплайна → governance engines
- Если изменения персонажа обусловлены отношениями, сначала фиксируются shift triggers (06) / event log, потом patch

---

## 5) OUTPUT SCHEMAS (MANDATORY)

### A) `CHARACTER_SNAPSHOT_SET`
**MUST (fields):**
- `character_id`
- `version`
- `snapshots[]` (ordered)
- `latest_snapshot_ref`
- `open_unknowns[]`
- `scope_notes`

**Snapshot (minimum):**
- `snapshot_id`
- `time_ref` (timeline point / episode / chapter / date)
- `source_events[]` (event_ids)
- `models` (refs or embedded summaries):
  - `trait_profile_ref`
  - `value_hierarchy_ref`
  - `moral_boundary_map_ref`
  - `inner_state_model_ref`
  - `behavior_policy_ref`
  - `speech_profile_ref` (optional)
  - `relationships_ref` (optional)
- `summary_changes` (short)
- `constraints_active[]` (recovery constraints still active)
- `notes`

**VALIDATION:**
- snapshots must be ordered by time_ref
- each snapshot must list source_events (or explicitly `[]` for baseline)
- latest_snapshot_ref must exist

**STORAGE:**
- `PROJECT_ARTIFACTS/<project>/CHARACTERS/EVOLUTION/<character_id>/CHARACTER_SNAPSHOT_SET.md`

---

### B) `MODEL_PATCH_LOG`
**MUST (fields):**
- `character_id`
- `version`
- `patches[]`
- `checks[]`
- `open_unknowns[]`

**Patch (minimum):**
- `patch_id`
- `applies_to_model` (enum: `TRAITS|VALUES|MORAL_BOUNDARIES|PSY_BASELINE|BEHAVIOR_POLICY|RELATIONSHIP_VARS|SPEECH_RULES`)
- `operation` (enum: `ADD|REMOVE|UPDATE|CLAMP|SHIFT`)
- `path` (what field changes)
- `from` (optional)
- `to` (new value)
- `reason_event_id`
- `authorization` (how authorized: event + gate passed)
- `cost_paid` (from event)
- `recovery_gate_status` (enum: `PASSED|BLOCKED|NOT_REQUIRED`)
- `severity_if_unapplied` (`S0|S1|S2|S3`)
- `notes`

**Checks (minimum):**
- `check_id`
- `check_text`
- `severity`

**VALIDATION:**
- every patch must reference reason_event_id
- patch cannot violate HARD invariants unless event_type is boundary break and explicitly authorizes it
- if recovery_gate_status=BLOCKED → patch must not apply (S0)

**STORAGE:**
- `PROJECT_ARTIFACTS/<project>/CHARACTERS/EVOLUTION/<character_id>/MODEL_PATCH_LOG.md`

---

### C) `EVOLUTION_AUDIT_RECORDS`
**MUST (fields):**
- `character_id`
- `version`
- `records[]`

**Record (minimum):**
- `record_id`
- `time_ref`
- `snapshot_id`
- `patch_ids[]`
- `event_ids[]`
- `canon_impact` (enum: `NONE|LOCAL|MAJOR`)
- `notes`
- `route_to_audit_log_engine` (pointer)

**VALIDATION:**
- record must link snapshot + patches + events
- MAJOR canon impact must be routed to governance audit log engine

**STORAGE:**
- `PROJECT_ARTIFACTS/<project>/CHARACTERS/EVOLUTION/<character_id>/EVOLUTION_AUDIT_RECORDS.md`

---

## 6) PROCESS (PIPELINE)
1) Load baseline snapshot (or create one from current models).
2) Read transformation events + recovery constraints.
3) Select applicable events for a given time_ref (from event log / plan).
4) For each event:
   - check authorization and gates
   - generate patches (explicit deltas)
   - enforce constraints and clamps
5) Apply patches to produce next snapshot.
6) Run drift checks:
   - any model change without event → S0 fail
7) Emit snapshot set + patch log + audit records.
8) If canon_impact != NONE, route record to Audit Log Engine (governance).

---

## 7) GATES (S0 BLOCKERS)
S0 (BLOCK) if:
- patch lacks reason_event_id
- recovery constraints say BLOCKED but patch still applies
- HARD invariant is violated without explicit boundary-break authorization
- snapshot created without source events (except baseline)

S1 (HIGH) if:
- changes are too large for stated event cost (mismatch)
- repeated oscillation of values (unstable evolution) without explanation

S2/S3: quality warnings.

---

## 8) NOTES FOR DOWNSTREAM ENGINES
- Continuity engine can compare snapshots across scenes/episodes.
- Narrative engines can plan transformations as explicit event cards.
- Dialogue/behavior engines should reference latest snapshot version for consistency.

---

LOCK: OPEN
