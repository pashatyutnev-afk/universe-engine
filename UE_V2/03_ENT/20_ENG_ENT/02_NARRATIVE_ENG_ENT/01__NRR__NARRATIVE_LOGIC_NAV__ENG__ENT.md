# NARRATIVE LOGIC ENGINE
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/02_DOMAIN_NARRATIVE_ENGINES/01__NARRATIVE_LOGIC_ENG.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 02_DOMAIN_NARRATIVE_ENGINES
ENGINE: 01__NARRATIVE_LOGIC_ENG
DOC_TYPE: ENGINE
LEVEL: L2
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.ENG.NARR.LOGIC.001
OWNER: SYSTEM
ROLE: Produce a deterministic causal narrative logic model: why events happen, what constraints exist, and how contradictions are prevented.

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Narrative Logic Engine created: causal rules, plausibility checks, contradiction prevention, and logic outputs."
- REASON: "Family engines were empty; needed a foundation engine for narrative causality."
- IMPACT: "All downstream narrative engines can depend on a stable logic model."
- CHANGE_ID: UE.CHG.2026-01-08.ENG.NARR.LOGIC.001

---

## 0) PURPOSE (LAW)
Этот движок формирует **логический каркас истории**:
- причинно-следственные связи (что из чего следует)
- правила правдоподобия внутри мира/сеттинга (story-internal plausibility)
- запреты/ограничения (что невозможно или недопустимо)
- выявление противоречий и “дыр” (logic holes)
- минимальный “набор фактов”, на который могут опираться структура, сцены, напряжение и темы

Выход движка — это не “сюжет”, а **модель логики**, которая делает любой сюжет внутри неё непротиворечивым.

---

## 1) NON-GOALS (HARD)
Движок НЕ делает:
- монтаж / экранный ритм / длительности кадров (production)  
- атмосферу/тон/символизм (style)  
- музыку/аранжировки (deep music)  
- полную разработку персонажей (это семья character; тут только логические мотивы на уровне фабулы)
- расписание событий во времени как календарь (это отдельные механики event scheduling; здесь только причинность)

---

## 2) MINI-CONTRACT (MANDATORY)

### CONSUMES (1–7)
- `CORE_IDENTITY` (что это за проект/сага/вселенная, идентификаторы, базовые инварианты)
- `CORE_STATE` (актуальное состояние канона/версии/статуса артефактов)
- `WORLD_LAW_SEEDS` (если есть: базовые законы мира / магии / технологий — черновые)
- `CHARACTER_INTENT_SEEDS` (если есть: намерения/цели ключевых акторов — черновые)
- `NARRATIVE_PREMISE` (если есть: тезис истории / исходная завязка)

### PRODUCES (1–7)
- `NARRATIVE_LOGIC_MODEL`
- `CONTRADICTION_REPORT`
- `PLAUSIBILITY_RULESET`

### DEPENDS_ON
- `[01_CORE_ENGINES/01__CORE_IDENTITY_ENG, 01_CORE_ENGINES/02__CORE_STATE_ENG]`

### OUTPUT_TARGET
- `PROJECT_ARTIFACTS/<project>/NARRATIVE/LOGIC/`

---

## 3) DEFINITIONS (LOCAL)
- **Logic Atom** — минимальный факт/условие (например: “персонаж X не может быть в двух местах одновременно”).
- **Causal Link** — направленная связь `A -> B` с причиной/условием/ограничениями.
- **Plausibility Rule** — правило “что допустимо” внутри истории (в рамках мира/сеттинга).
- **Contradiction** — конфликт логических атомов/связей, который делает историю невозможной без объяснения.

---

## 4) INPUT ASSUMPTIONS (SAFE DEFAULTS)
Если часть входов отсутствует:
- `WORLD_LAW_SEEDS` отсутствует → считаем “реализм по умолчанию” (физика/соц.логика без магии).
- `CHARACTER_INTENT_SEEDS` отсутствует → используем “актор действует в собственных интересах”, но не придумываем мотивации как канон.
- `NARRATIVE_PREMISE` отсутствует → движок выдаёт только общий логический каркас и список “нужных уточнений” в contradiction report (как вопросы-дырки).

---

## 5) BOUNDARIES (MANDATORY)

### IN SCOPE (OWNS)
- причинность и логические следствия событий
- правила правдоподобия (что “может быть” в рамках истории)
- противоречия (поиск и классификация)
- минимальные требования к входам для непротиворечивости

### OUT OF SCOPE (HARD)
- структурирование в акты/эпизоды (это `02__STORY_STRUCTURE_ENG`)
- построение сцен (это `04__SCENE_CONSTRUCTION_ENG`)
- ритм (это `05__PACING_RHYTHM_ENG` для story-time)
- визуальная реализация (семья `08_*`)
- стиль/настроение (семья `06_*`)
- глубокая музыка (семья `09_*`)

### COLLISION RULE (ROUTING)
- Если спор про “реализм мира/магии/технологий” → `04_DOMAIN_WORLD_ENGINES/02__WORLD_LAW_ENG`
- Если спор про “мотивы/психологию персонажа” → `03_DOMAIN_CHARACTER_ENGINES/02__MOTIVATION_DESIRE_ENG`
- Если спор про “как показать/смонтировать” → `08_KNOWLEDGE_PRODUCTION_ENGINES/*`

---

## 6) OUTPUT SCHEMAS (MANDATORY)

### A) `NARRATIVE_LOGIC_MODEL`
**MUST (fields):**
- `model_id` (string; stable within project)
- `version` (string)
- `axioms[]` (list of Logic Atom; non-empty if any premise exists)
- `plausibility_rules[]` (list; can be empty)
- `causal_links[]` (list of Causal Link)
- `constraints[]` (list of hard/soft constraints)
- `open_unknowns[]` (list of required clarifications, if inputs incomplete)
- `scope_notes` (string; family boundary reminder)

**Logic Atom (minimum):**
- `id` (string)
- `statement` (string; declarative)
- `type` (`WORLD|CHARACTER|SITUATION|RESOURCE|RULE`)
- `strength` (`HARD|SOFT`)
- `evidence` (optional string; where it came from)

**Causal Link (minimum):**
- `id` (string)
- `cause_atom_ids[]`
- `effect_atom_ids[]`
- `conditions[]` (list; can be empty)
- `reversibility` (`IRREVERSIBLE|REVERSIBLE|UNKNOWN`)
- `notes` (string; short)

**VALIDATION:**
- no duplicate `axioms.id`
- every referenced atom id exists
- contradictions must be either:
  - resolved (with added rule/condition), or
  - present in `CONTRADICTION_REPORT`

**STORAGE:**
- store as: `NARRATIVE_LOGIC_MODEL.md` or `NARRATIVE_LOGIC_MODEL.json`
- location: `PROJECT_ARTIFACTS/<project>/NARRATIVE/LOGIC/`

---

### B) `CONTRADICTION_REPORT`
**MUST (fields):**
- `report_id` (string)
- `model_id` (string; points to logic model)
- `contradictions[]` (list; can be empty)
- `severity_summary` (counts by S0/S1/S2/S3)
- `required_decisions[]` (list; what must be decided to proceed)
- `recommended_fixes[]` (list; safe proposals, not canon changes)

**Contradiction (minimum):**
- `id`
- `description`
- `atom_ids_involved[]`
- `severity` (`S0|S1|S2|S3`)
- `why_blocking` (string)
- `routes_to` (engine pointer; where to resolve if out-of-scope)

**VALIDATION:**
- `S0` means “story impossible / self-contradictory without explicit exception”
- `routes_to` must be set if the fix is outside this engine’s scope

**STORAGE:**
- `PROJECT_ARTIFACTS/<project>/NARRATIVE/LOGIC/CONTRADICTION_REPORT.md`

---

### C) `PLAUSIBILITY_RULESET`
**MUST (fields):**
- `ruleset_id`
- `rules[]` (list; can be empty)
- `assumptions[]` (list; defaults used)
- `limits[]` (list of hard prohibitions)

**Rule (minimum):**
- `id`
- `rule_text`
- `applies_to` (`WORLD|CHARACTER|BOTH`)
- `strength` (`HARD|SOFT`)
- `examples[]` (optional)

**VALIDATION:**
- no rule contradicts `WORLD_LAW_SEEDS` if those exist (otherwise mark as `open_unknown`)

**STORAGE:**
- `PROJECT_ARTIFACTS/<project>/NARRATIVE/LOGIC/PLAUSIBILITY_RULESET.md`

---

## 7) PROCESS (PIPELINE)
1) Ingest inputs → normalize into candidate atoms.
2) Build default plausibility rules (if missing).
3) Generate causal links from premise/intent seeds.
4) Detect contradictions:
   - direct logical conflict
   - impossible state transitions
   - circular causality without mechanism
5) Classify severity (S0–S3) and route out-of-scope contradictions.
6) Output:
   - logic model
   - plausibility ruleset
   - contradiction report

---

## 8) GATES (S0 BLOCKERS)
S0 (BLOCK) if:
- contradictions of type “impossible world law” with no allowed exception
- identity/core invariants violated (например: канон-правила или базовые инварианты проекта)
- key premise implies mutually exclusive states without bridge rule

S1 (HIGH) if:
- major causal gaps that force deus-ex-machina
- character intent conflicts that break believability (route to character engines)

S2/S3 are warnings/notes.

---

## 9) DEPENDENCY NOTES
Downstream engines typically consume:
- `NARRATIVE_LOGIC_MODEL` (structure, scenes, tension, continuity)
This engine should remain minimal: it defines causality and constraints, not structure.

---

LOCK: OPEN
