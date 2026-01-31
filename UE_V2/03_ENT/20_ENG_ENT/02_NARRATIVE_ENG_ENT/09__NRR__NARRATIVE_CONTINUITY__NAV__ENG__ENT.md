# NARRATIVE CONTINUITY ENGINE
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/02_DOMAIN_NARRATIVE_ENGINES/09__NARRATIVE_CONTINUITY_ENG.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 02_DOMAIN_NARRATIVE_ENGINES
ENGINE: 09__NARRATIVE_CONTINUITY_ENG
DOC_TYPE: ENGINE
LEVEL: L2
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.ENG.NARR.CONTINUITY.001
OWNER: SYSTEM
ROLE: Validate narrative continuity across beats/scenes: state tracking, causal integrity, promise/payoff integrity, and contradiction detection (story-domain continuity, not production continuity).

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Narrative Continuity Engine created: state ledger, causal checks, contradiction reports, and continuity repair routing."
- REASON: "Needed canonical continuity enforcement so stamping scenes/beats doesn't drift into contradictions."
- IMPACT: "Story becomes auditable and deterministic across iterations."
- CHANGE_ID: UE.CHG.2026-01-08.ENG.NARR.CONTINUITY.001

---

## 0) PURPOSE (LAW)
Этот движок обеспечивает **непрерывность (continuity) истории**:
- непротиворечивость состояний (кто где, что знает, что возможно)
- причинно-следственную целостность (почему это случилось)
- целостность обещаний/оплат (promises/payoffs)
- обнаружение противоречий и маршрутизация “ремонта” в нужные движки

Это continuity story-domain, не про реквизит/монтаж.

---

## 1) NON-GOALS (HARD)
Движок НЕ делает:
- производственную непрерывность (постановка, реквизит, кадры) → production layer
- создание структуры/битов/сцен (он не авторит, он валидирует)
- жанровую/стилевую консистентность (это `06_GENRE_STYLE_ENGINES/*`)

---

## 2) MINI-CONTRACT (MANDATORY)

### CONSUMES (1–14)
- `CORE_IDENTITY`
- `CORE_STATE`
- `NARRATIVE_LOGIC_MODEL`
- `STORY_STRUCTURE_BLUEPRINT`
- `BEAT_MAP`
- `STRUCTURE_CONSTRAINTS` (optional)
- `SCENE_BLUEPRINT_SET` (optional but recommended)
- `BEAT_TO_SCENE_MAPPING` (optional)
- `DRAMATIC_ARC_SPEC` (optional)
- `TENSION_STAKES_MAP` (optional)
- `PAYOFF_OBLIGATIONS` (optional)
- `FORESHADOW_PLAN` (optional)
- `PROMISE_PAYOFF_MAP` (optional)
- `TWIST_DESIGN_SPECS` (optional)

### PRODUCES (1–7)
- `CONTINUITY_STATE_LEDGER`
- `CONTRADICTION_REPORT`
- `CONTINUITY_REPAIR_TASKS`

### DEPENDS_ON
- `[02_DOMAIN_NARRATIVE_ENGINES/01__NARRATIVE_LOGIC_ENG, 02_DOMAIN_NARRATIVE_ENGINES/04__SCENE_CONSTRUCTION_ENG, 02_DOMAIN_NARRATIVE_ENGINES/07__FORESHADOWING_ENG, 02_DOMAIN_NARRATIVE_ENGINES/08__TWIST_REVEAL_ENG]`

### OUTPUT_TARGET
- `PROJECT_ARTIFACTS/<project>/NARRATIVE/CONTINUITY/`

---

## 3) DEFINITIONS (LOCAL)
- **State Ledger** — журнал состояний по ключевым референсам (акты/сцены/биты).
- **Knowledge State** — кто что знает и когда узнал.
- **Causal Link** — причинная связь “A -> B” с условиями.
- **Contradiction** — утверждения/состояния, которые не могут быть одновременно истинны.

---

## 4) BOUNDARIES (MANDATORY)

### IN SCOPE (OWNS)
- формальная проверка непрерывности (state, knowledge, causality)
- проверка promises/payoffs (закрыты ли критические обещания)
- контроль “твист не ломает прошлое” (recontext safe)
- выдача repair tasks с маршрутом на нужные движки

### OUT OF SCOPE (HARD)
- переписывание сцены/битов (это делают соответствующие движки)
- production continuity (ошибки реквизита/монтажа)
- миростроительные изменения (хотя может отправить в world engines)

### COLLISION RULE (ROUTING)
- Если противоречие в причинности/правилах → `01__NARRATIVE_LOGIC_ENG`
- Если проблема в структуре/порядке → `02__STORY_STRUCTURE_ENG`
- Если проблема в сцене (objective/turn/outcome) → `04__SCENE_CONSTRUCTION_ENG`
- Если проблема в обещаниях/оплатах → `07__FORESHADOWING_ENG` и/или `06__TENSION_STAKES_ENG`
- Если проблема из-за твиста → `08__TWIST_REVEAL_ENG`
- Если проблема — мировые правила → `04_DOMAIN_WORLD_ENGINES/*`

---

## 5) OUTPUT SCHEMAS (MANDATORY)

### A) `CONTINUITY_STATE_LEDGER`
**MUST (fields):**
- `ledger_id`
- `version`
- `track_scope` (enum: `BEAT_ONLY|SCENE_ONLY|BEAT_AND_SCENE`)
- `entities_tracked[]` (ids or labels)
- `state_snapshots[]` (ordered)
- `knowledge_snapshots[]` (ordered)
- `causal_links[]`
- `open_unknowns[]`
- `scope_notes`

**State Snapshot (minimum):**
- `ref_type` (enum: `ACT|SEQUENCE|SCENE|BEAT`)
- `ref_id`
- `time_marker` (optional)
- `facts_true[]` (list)
- `facts_false[]` (list)
- `facts_unknown[]` (list)
- `location_states[]` (optional)
- `resource_states[]` (optional)
- `notes`

**Knowledge Snapshot (minimum):**
- `ref_type`
- `ref_id`
- `knowers[]` (who knows what)
- `secrets[]` (who does not know what)
- `reveal_events[]` (links to reveals/twists if present)

**Causal Link (minimum):**
- `id`
- `cause_ref` (beat/scene id)
- `effect_ref` (beat/scene id)
- `conditions[]` (preconditions)
- `why_valid` (short)

**VALIDATION:**
- ledger order must match structure ordering
- a fact cannot be simultaneously in `facts_true` and `facts_false`
- knowledge cannot “jump” without a reveal/ref or explicit rationale

**STORAGE:**
- `PROJECT_ARTIFACTS/<project>/NARRATIVE/CONTINUITY/CONTINUITY_STATE_LEDGER.md`

---

### B) `CONTRADICTION_REPORT`
**MUST (fields):**
- `report_id`
- `contradictions[]` (can be empty)
- `severity_summary`
- `hotspots[]`
- `recommended_routes[]`

**Contradiction (minimum):**
- `id`
- `type` (enum: `STATE_CONFLICT|KNOWLEDGE_CONFLICT|CAUSAL_GAP|PROMISE_UNPAID|PAYOFF_UNEARNED|TIMELINE_CONFLICT|CAPABILITY_CONFLICT`)
- `ref_ids[]` (beats/scenes involved)
- `severity` (`S0|S1|S2|S3`)
- `description`
- `why_it_breaks`
- `fix_route` (engine pointer)
- `candidate_fixes[]` (short)

**VALIDATION:**
- any S0 must have fix_route and at least one candidate fix
- promise/payoff issues must reference promise/obligation ids when available

**STORAGE:**
- `PROJECT_ARTIFACTS/<project>/NARRATIVE/CONTINUITY/CONTRADICTION_REPORT.md`

---

### C) `CONTINUITY_REPAIR_TASKS`
**MUST (fields):**
- `tasks_id`
- `tasks[]` (can be empty)
- `routing_table[]` (optional)
- `execution_order_notes` (optional)

**Task (minimum):**
- `task_id`
- `priority` (`S0|S1|S2|S3`)
- `problem_ref` (contradiction id)
- `assigned_engine` (engine pointer)
- `action` (what to do)
- `expected_result` (what becomes true after fix)
- `blocking` (bool; S0 tasks should be blocking=true)

**VALIDATION:**
- S0 tasks must be blocking
- assigned_engine must exist in canon index (by name)

**STORAGE:**
- `PROJECT_ARTIFACTS/<project>/NARRATIVE/CONTINUITY/CONTINUITY_REPAIR_TASKS.md`

---

## 6) PROCESS (PIPELINE)
1) Determine tracking scope:
   - if scenes exist → `BEAT_AND_SCENE`
   - else → `BEAT_ONLY`
2) Build ledger:
   - step through acts/beats/scenes in order
   - apply postconditions as state updates
3) Check continuity:
   - state conflicts (facts true/false)
   - knowledge jumps (who learned without reveal)
   - causal gaps (effect with no possible cause)
4) Check promises/payoffs:
   - unpaid high-severity promises
   - payoffs without setup
5) Check twist impacts:
   - recontext targets must remain consistent
6) Generate contradiction report + repair tasks.

---

## 7) GATES (S0 BLOCKERS)
S0 (BLOCK) if:
- hard state contradiction exists (cannot be reconciled without changing logic/structure)
- causal gap makes a critical beat/scene impossible
- critical promise/obligation (S0) remains unpaid with no route
- twist creates impossible recontext (contradicts established facts with no repair)

S1 (HIGH) if:
- multiple knowledge inconsistencies
- timeline ordering conflicts (acts/segments mismatch)

S2/S3: quality warnings.

---

## 8) NOTES
Continuity is the “audit engine” of narrative:
- it doesn’t create content
- it enforces consistency
- it routes repairs to the right owners

---

LOCK: OPEN
