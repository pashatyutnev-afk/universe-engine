# TENSION & STAKES ENGINE
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/02_DOMAIN_NARRATIVE_ENGINES/06__TENSION_STAKES_ENG.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 02_DOMAIN_NARRATIVE_ENGINES
ENGINE: 06__TENSION_STAKES_ENG
DOC_TYPE: ENGINE
LEVEL: L2
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.ENG.NARR.TENSION.001
OWNER: SYSTEM
ROLE: Produce a story-domain tension & stakes map: what can be lost, who pays, what threats exist, and how pressure escalates across beats/scenes.

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Tension & Stakes Engine created: stakes map, threat catalog, escalation routes, and payoff obligations."
- REASON: "Needed canonical model for stakes escalation separate from pacing and production."
- IMPACT: "Scenes and continuity can validate pressure logic and earned payoffs."
- CHANGE_ID: UE.CHG.2026-01-08.ENG.NARR.TENSION.001

---

## 0) PURPOSE (LAW)
Этот движок делает “каркас давления” истории явным:
- что поставлено на кон (stakes): жизнь/любовь/ресурс/власть/правда/свобода/идентичность
- какие угрозы/препятствия (threats) реально действуют
- как давление эскалирует (escalation routes)
- какие обязательства payoffs возникают (если поднял ставки — обязан закрыть)

Это story-domain модель: она привязана к beats/scenes, но не к монтажу.

---

## 1) NON-GOALS (HARD)
Движок НЕ делает:
- структуру актов/битов (это `02__STORY_STRUCTURE_ENG`)
- сценическое проектирование (это `04__SCENE_CONSTRUCTION_ENG`)
- темп/ритм (это `05__PACING_RHYTHM_ENG`)
- атмосферу/тон (это `06_GENRE_STYLE_ENGINES/*`)
- визуально-звуковую реализацию угроз (production) → `08_*`

---

## 2) MINI-CONTRACT (MANDATORY)

### CONSUMES (1–10)
- `CORE_IDENTITY`
- `CORE_STATE`
- `NARRATIVE_LOGIC_MODEL`
- `STORY_STRUCTURE_BLUEPRINT`
- `BEAT_MAP`
- `DRAMATIC_ARC_SPEC` (optional but recommended)
- `PACING_PROFILE_STORY_TIME` (optional)
- `SCENE_BLUEPRINT_SET` (optional but recommended)
- `CHARACTER_INTENT_SEEDS` (optional)
- `WORLD_LAW_SEEDS` (optional)

### PRODUCES (1–7)
- `TENSION_STAKES_MAP`
- `THREAT_CATALOG`
- `PAYOFF_OBLIGATIONS`

### DEPENDS_ON
- `[02_DOMAIN_NARRATIVE_ENGINES/01__NARRATIVE_LOGIC_ENG, 02_DOMAIN_NARRATIVE_ENGINES/02__STORY_STRUCTURE_ENG, 02_DOMAIN_NARRATIVE_ENGINES/04__SCENE_CONSTRUCTION_ENG, 02_DOMAIN_NARRATIVE_ENGINES/05__PACING_RHYTHM_ENG]`

### OUTPUT_TARGET
- `PROJECT_ARTIFACTS/<project>/NARRATIVE/TENSION/`

---

## 3) DEFINITIONS (LOCAL)
- **Stake** — ценность, которая может быть потеряна/получена.
- **Threat** — источник риска/давления (актор, система, обстоятельство, тайна, время).
- **Escalation Route** — путь, как угроза усиливается и почему это логично.
- **Payoff Obligation** — обязательство истории: если поднял ожидание/ставку, должен дать последствия/развязку.

---

## 4) BOUNDARIES (MANDATORY)

### IN SCOPE (OWNS)
- каталог stakes и threats
- карта “кто что теряет/получает” по сегментам
- правила эскалации (не противоречащие логике мира/истории)
- формирование payoff obligations и проверка “earned/unearned”

### OUT OF SCOPE (HARD)
- монтажное давление (музыка/монтаж/звук как приём продакшна)
- стиль напряжения (хоррор-вайб, нуар-вайб) как владение
- создание событий (что случилось) — здесь мы описываем угрозы/ставки, но не заменяем beats

### COLLISION RULE (ROUTING)
- Если спор “это про темп/ритм” → `05__PACING_RHYTHM_ENG`
- Если спор “это про структуру beats” → `02__STORY_STRUCTURE_ENG`
- Если спор “это про мировые законы/ресурсы/экономику” → `04_DOMAIN_WORLD_ENGINES/*`
- Если спор “как передать напряжение в кадре” → `08_KNOWLEDGE_PRODUCTION_ENGINES/*`

---

## 5) OUTPUT SCHEMAS (MANDATORY)

### A) `TENSION_STAKES_MAP`
**MUST (fields):**
- `map_id`
- `version`
- `stakes[]` (global stake list)
- `stake_owners[]` (who owns/cares about which stake)
- `segment_pressure[]` (act/sequence/scene mapping)
- `escalation_routes[]`
- `logic_refs[]` (constraints and causal links)
- `open_unknowns[]`
- `scope_notes`

**Stake (minimum):**
- `stake_id`
- `name`
- `category` (enum: `LIFE|FREEDOM|LOVE|TRUTH|POWER|RESOURCE|REPUTATION|IDENTITY|SAFETY|FUTURE`)
- `holder` (who is affected; can be `SYSTEM`)
- `value_statement` (why it matters)
- `loss_condition` (what counts as loss)
- `gain_condition` (what counts as gain)
- `hard_or_soft` (`HARD|SOFT`)

**Segment Pressure (minimum):**
- `ref_type` (enum: `ACT|SEQUENCE|SCENE|BEAT`)
- `ref_id`
- `pressure_level` (0..100)
- `active_stakes[]` (stake ids)
- `active_threats[]` (threat ids)
- `pressure_driver` (enum: `TIME|RISK|LOSS|REVEAL|POWER_SHIFT|RESOURCE|MORAL`)
- `notes`

**Escalation Route (minimum):**
- `route_id`
- `threat_id`
- `mechanism` (short: how it escalates)
- `trigger_refs[]` (beat/scene ids)
- `steps[]` (ordered)
- `max_state` (what “worst case” looks like)
- `logic_constraints[]` (atoms/rules it must respect)

**VALIDATION:**
- every stake referenced in segments exists
- pressure_level must align with arc peak (if DRAMATIC_ARC_SPEC exists) or justify mismatch
- escalation steps must not violate `NARRATIVE_LOGIC_MODEL`

**STORAGE:**
- `PROJECT_ARTIFACTS/<project>/NARRATIVE/TENSION/TENSION_STAKES_MAP.md`

---

### B) `THREAT_CATALOG`
**MUST (fields):**
- `catalog_id`
- `threats[]`
- `classification_rules[]`
- `anti_patterns[]`

**Threat (minimum):**
- `threat_id`
- `name`
- `type` (enum: `ANTAGONIST|SYSTEM|ENVIRONMENT|TIME|SECRET|INTERNAL|RESOURCE|RELATIONSHIP`)
- `agency` (enum: `ACTIVE|PASSIVE|EMERGENT`)
- `capabilities` (short list)
- `limits` (short list)
- `visibility` (enum: `KNOWN|PARTIAL|HIDDEN`)
- `stakes_impacted[]` (stake ids)
- `defeat_or_resolution_modes[]` (list of enum: `DEFEAT|ESCAPE|PAYMENT|TRUTH|TRADE|SACRIFICE|TRANSFORMATION`)
- `logic_refs[]`

**VALIDATION:**
- each threat must impact at least one stake OR be marked as `supporting_only=true`
- hidden threats require at least one reveal beat route (else open_unknown)

**STORAGE:**
- `PROJECT_ARTIFACTS/<project>/NARRATIVE/TENSION/THREAT_CATALOG.md`

---

### C) `PAYOFF_OBLIGATIONS`
**MUST (fields):**
- `obligations_id`
- `obligations[]`
- `resolution_tracking[]`
- `unearned_payoff_risks[]`

**Obligation (minimum):**
- `id`
- `created_by_ref` (beat/scene id where stake was raised)
- `stake_id`
- `promise` (what audience expects now)
- `required_resolution_type` (enum: `PAY|ANSWER|PUNISH|REWARD|CLOSE_LOOP|SHOW_COST`)
- `due_by_ref` (act/segment id; can be `UNKNOWN`)
- `severity_if_unpaid` (`S0|S1|S2|S3`)
- `candidate_resolution_refs[]` (beats/scenes that can pay it off)
- `notes`

**VALIDATION:**
- any `S0` obligation must have either:
  - `candidate_resolution_refs` non-empty, or
  - explicit `due_by_ref=UNKNOWN` AND routed decision (open_unknown)
- if a payoff is marked “paid”, there must be an actual ref that performs it

**STORAGE:**
- `PROJECT_ARTIFACTS/<project>/NARRATIVE/TENSION/PAYOFF_OBLIGATIONS.md`

---

## 6) PROCESS (PIPELINE)
1) Extract candidate stakes from premise/character intent/world law.
2) Build threat catalog:
   - identify sources of pressure (actors/systems/time/secrets)
3) Map stakes/threats onto:
   - acts (coarse)
   - beats/scenes (fine) if available
4) Build escalation routes:
   - define triggers and step ladder
5) Derive payoff obligations:
   - whenever stake is raised or threat is revealed → create obligation
6) Validate:
   - logic compatibility
   - payoff “earned” rules (setup before payoff)
7) Emit outputs.

---

## 7) GATES (S0 BLOCKERS)
S0 (BLOCK) if:
- a central stake is raised with no possible resolution path (no candidate and no routed decision)
- escalation route violates a hard plausibility constraint (impossible threat capability)
- a payoff is marked “paid” but no referenced beat/scene exists (false closure)

S1 (HIGH) if:
- threats exist but do not connect to beats/scenes (detached pressure)
- pressure curve contradicts arc peak without justification

S2/S3: quality warnings.

---

## 8) NOTES
This engine is a “pressure truth layer”:
- pacing says “how fast”
- arc says “shape”
- tension/stakes says “what it costs”
All must remain story-domain, not production.

---

LOCK: OPEN
