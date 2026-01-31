# RELATIONSHIP ENGINE
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/03_DOMAIN_CHARACTER_ENGINES/06__RELATIONSHIP_ENG.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 03_DOMAIN_CHARACTER_ENGINES
ENGINE: 06__RELATIONSHIP_ENG
DOC_TYPE: ENGINE
LEVEL: L2
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.ENG.CHAR.REL.001
OWNER: SYSTEM
ROLE: Produce deterministic relationship models: relationship graph, attachment contracts, trust/debt/tension variables, interaction rules, and change triggers compatible with character cores and behaviors.

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Relationship Engine created: relationship graph schema, trust/debt dynamics, contracts, and change triggers."
- REASON: "Character behavior and dialogue require explicit relational context to remain consistent."
- IMPACT: "Scenes and arcs can track relational shifts deterministically."
- CHANGE_ID: UE.CHG.2026-01-08.ENG.CHAR.REL.001

---

## 0) PURPOSE (LAW)
Этот движок описывает **отношения между персонажами** как систему:
- граф отношений (кто с кем и как связан)
- переменные отношений (trust, fear, attraction, respect, debt, power)
- контракты/границы отношений (что допустимо/недопустимо между ними)
- триггеры изменения (что меняет отношения и на сколько)
- правила взаимодействия (patterns: push/pull, conflict styles)

Цель: отношения становятся измеримыми и проверяемыми на консистентность.

---

## 1) NON-GOALS (HARD)
Движок НЕ делает:
- диалоги как тексты (это `07__DIALOGUE_ENG`, а естественность — `08__SPEECH_NATURALIZATION_ENG`)
- сюжетное владение сценами/битами (narrative family)
- мировые правила общества/геополитики как владелец (world family)
- production “как сыграть химию” (production family)
- долгосрочную эволюцию личности (10) — тут только правила изменения отношений, не “перепрошивка” персонажа

---

## 2) MINI-CONTRACT (MANDATORY)

### CONSUMES (1–16)
- `CORE_IDENTITY`
- `CORE_STATE`
- `CHARACTER_CORE_PASSPORT` (for each involved character)
- `CHARACTER_INVARIANTS` (optional but recommended)
- `CHARACTER_TRAIT_PROFILE` (optional)
- `MOTIVATION_DESIRE_STACK` (optional)
- `VALUE_HIERARCHY` (optional)
- `MORAL_BOUNDARY_MAP` (optional)
- `DECISION_POLICY_MODEL` (optional but recommended)
- `INNER_STATE_MODEL` (optional)
- `TRIGGER_DEFENSE_MAP` (optional)
- `RELATIONSHIP_SEEDS` (optional: initial links)
- `WORLD_LAW_SEEDS` (optional: cultural constraints on relationships)
- `NARRATIVE_PREMISE` (optional)
- `STAKE_CONTEXT` (optional)
- `SCENE_BLUEPRINT_SET` (optional; for mapping shifts)

### PRODUCES (1–7)
- `RELATIONSHIP_GRAPH`
- `RELATIONSHIP_CONTRACTS`
- `RELATIONSHIP_SHIFT_RULESET`

### DEPENDS_ON
- `[03_DOMAIN_CHARACTER_ENGINES/01__CHARACTER_CORE_ENG, 03_DOMAIN_CHARACTER_ENGINES/05__CHARACTER_BEHAVIOR_ENG]`

### OUTPUT_TARGET
- `PROJECT_ARTIFACTS/<project>/CHARACTERS/RELATIONSHIPS/`

---

## 3) DEFINITIONS (LOCAL)
- **Relationship Edge** — связь между двумя узлами (персонажами) с параметрами.
- **Contract** — явные правила границ: что можно/нельзя/что ожидается.
- **Variable** — измеримая величина отношений (trust 0..100).
- **Shift Trigger** — событие/действие, меняющее переменные.
- **Power Balance** — кто доминирует/кто зависит, и почему.

---

## 4) BOUNDARIES (MANDATORY)

### IN SCOPE (OWNS)
- граф отношений + параметры
- контракты границ/ожиданий
- правила изменения отношений (shift rules)
- совместимость отношений с инвариантами/моралью/поведением

### OUT OF SCOPE (HARD)
- “общество/политика/экономика” как владелец (только constraints оттуда)
- написание сцен отношений и диалогов
- режиссёрская “химия” и постановка
- изменение ценностей персонажа (это evolution)

### COLLISION RULE (ROUTING)
- Если правило отношений определяется культурой/законами → `04_DOMAIN_WORLD_ENGINES/*` как источник constraints
- Если требуется пересечение моральных границ → `03__MORAL_VALUE_ENG` или `09__GROWTH_TRAUMA_ENG`
- Если вопрос про голос/реплики → `07__DIALOGUE_ENG` / `08__SPEECH_NATURALIZATION_ENG`

---

## 5) OUTPUT SCHEMAS (MANDATORY)

### A) `RELATIONSHIP_GRAPH`
**MUST (fields):**
- `graph_id`
- `version`
- `nodes[]` (character_ids)
- `edges[]`
- `global_rules[]` (optional)
- `open_unknowns[]`
- `scope_notes`

**Edge (minimum):**
- `edge_id`
- `a_character_id`
- `b_character_id`
- `relationship_type` (enum: `FAMILY|ROMANTIC|FRIEND|ALLY|RIVAL|ENEMY|MENTOR|STUDENT|EMPLOYER|EMPLOYEE|DEBTOR|CREDITOR|STRANGER`)
- `variables` (map of standard variables)
- `power_balance` (enum: `A_OVER_B|B_OVER_A|BALANCED|UNSTABLE`)
- `contract_ref` (optional pointer)
- `tension_sources[]` (optional)
- `notes`

**Standard variables (recommended set):**
- `trust` (0..100)
- `respect` (0..100)
- `affection` (0..100)
- `fear` (0..100)
- `dependence` (0..100)
- `debt` (0..100)
- `attraction` (0..100) (if relevant)
- `conflict_intensity` (0..100)

**VALIDATION:**
- no duplicate edge for same pair unless explicitly multi-edge with rationale
- variables must be within 0..100
- relationship_type must be consistent with invariants if any (e.g., “cannot trust anyone” should cap trust unless broken)

**STORAGE:**
- `PROJECT_ARTIFACTS/<project>/CHARACTERS/RELATIONSHIPS/RELATIONSHIP_GRAPH.md`

---

### B) `RELATIONSHIP_CONTRACTS`
**MUST (fields):**
- `contracts_id`
- `contracts[]`
- `taboos[]` (optional)
- `cultural_constraints_ref` (optional)
- `open_unknowns[]`

**Contract (minimum):**
- `contract_id`
- `a_character_id`
- `b_character_id`
- `rules[]` (list)
- `non_negotiables[]` (hard boundaries)
- `expected_behaviors[]`
- `breach_consequences[]`
- `repair_paths[]`
- `notes`

**Rule (minimum):**
- `rule_id`
- `rule_text`
- `strength` (`HARD|SOFT`)
- `who_enforces` (`A|B|BOTH|SYSTEM`)

**Breach consequence (minimum):**
- `id`
- `breach_type`
- `impact` (variable deltas)
- `severity` (`S0|S1|S2|S3`)
- `route_to` (engine pointer if it forces value/trauma change)

**Repair path (minimum):**
- `id`
- `method` (apology, sacrifice, time, truth, act of care)
- `required_cost`
- `expected_delta` (variable deltas)

**VALIDATION:**
- contract must contain at least one non-negotiable OR explicit “no contract” rationale
- S0 breach consequence must have route_to

**STORAGE:**
- `PROJECT_ARTIFACTS/<project>/CHARACTERS/RELATIONSHIPS/RELATIONSHIP_CONTRACTS.md`

---

### C) `RELATIONSHIP_SHIFT_RULESET`
**MUST (fields):**
- `ruleset_id`
- `shift_triggers[]`
- `default_deltas` (optional)
- `anti_patterns[]`
- `checks[]`

**Shift trigger (minimum):**
- `trigger_id`
- `trigger_type` (enum: `BETRAYAL|SACRIFICE|LIE_REVEALED|TRUTH_SHARED|HELP_GIVEN|HELP_REFUSED|VIOLENCE|CARE|HUMILIATION|PROTECTION|POWER_MOVE`)
- `preconditions[]` (optional)
- `delta` (variable deltas)
- `cooldown` (optional)
- `notes`

**Anti-pattern (minimum):**
- `id`
- `name`
- `symptom`
- `why_bad`
- `fix` (short)

**VALIDATION:**
- each trigger must specify at least one variable delta
- triggers that violate moral boundaries must route to values/growth engine (S1 warning)

**STORAGE:**
- `PROJECT_ARTIFACTS/<project>/CHARACTERS/RELATIONSHIPS/RELATIONSHIP_SHIFT_RULESET.md`

---

## 6) PROCESS (PIPELINE)
1) Collect characters + seeds and determine initial edges.
2) Set baseline relationship variables (trust/respect/etc.).
3) Define contracts:
   - non-negotiables, expectations, breach consequences, repair paths
4) Define shift triggers:
   - what changes variables and by how much
5) Validate consistency:
   - with invariants, values, behavior policies
6) Emit outputs.

---

## 7) GATES (S0 BLOCKERS)
S0 (BLOCK) if:
- relationship contracts demand actions forbidden by HARD moral boundaries with no routing
- breach consequences include S0 with no repair route
- graph contains contradictory duplicates for same pair without rationale (e.g., both “enemy” and “best friend” baseline)

S1 (HIGH) if:
- relationships have no variables (only labels) → not executable
- shift triggers exist but no contracts explain expected behavior baseline

S2/S3: quality warnings.

---

## 8) NOTES FOR DOWNSTREAM ENGINES
- Dialogue engine uses relationship variables to shape subtext and politeness/aggression.
- Narrative engines can track relationship shifts as stakes/turns.
- Continuity can validate variable deltas against actual events.

---

LOCK: OPEN
