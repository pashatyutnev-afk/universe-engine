# SCENE CONSTRUCTION ENGINE
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/02_DOMAIN_NARRATIVE_ENGINES/04__SCENE_CONSTRUCTION_ENG.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 02_DOMAIN_NARRATIVE_ENGINES
ENGINE: 04__SCENE_CONSTRUCTION_ENG
DOC_TYPE: ENGINE
LEVEL: L2
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.ENG.NARR.SCENE.001
OWNER: SYSTEM
ROLE: Convert story structure + arc + logic into scene-level blueprints (objectives, conflict, turns, outcomes) without stepping into production (camera/editing).

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Scene Construction Engine created: scene blueprint spec, beat-to-scene routing, and scene validity checks."
- REASON: "Needed canonical bridge from structure/arc into executable scene units."
- IMPACT: "Downstream pacing/continuity/tension engines can operate on stable scene units."
- CHANGE_ID: UE.CHG.2026-01-08.ENG.NARR.SCENE.001

---

## 0) PURPOSE (LAW)
Этот движок превращает “скелет истории” в **сценические единицы**:
- каждая сцена = цель + конфликт + изменение (turn) + исход + след
- сцены “прикрепляются” к beats, чтобы история становилась исполнимой
- сценическая логика проверяется на непротиворечивость (в рамках narrative logic)

Важно: это **story-domain сцены**, а не “сценарные страницы” и не постановка/съёмка.

---

## 1) NON-GOALS (HARD)
Движок НЕ делает:
- режиссуру, операторку, свет, звук, монтаж → семья `08_KNOWLEDGE_PRODUCTION_ENGINES`
- “монтажный ритм” → `08_KNOWLEDGE_PRODUCTION_ENGINES/07__EDITING_MONTAGE_ENG`
- тон/атмосферу/символизм как owning-scope → семья `06_GENRE_STYLE_ENGINES`
- диалоги как финальный текст (может дать “диалоговые цели/ключи”, но не пишет литературно) → `03_DOMAIN_CHARACTER_ENGINES/07__DIALOGUE_ENG` (если нужно)
- глубинную музыку → семья `09_SOUND_MUSIC_ENGINES`

---

## 2) MINI-CONTRACT (MANDATORY)

### CONSUMES (1–9)
- `CORE_IDENTITY`
- `CORE_STATE`
- `NARRATIVE_LOGIC_MODEL`
- `STORY_STRUCTURE_BLUEPRINT`
- `BEAT_MAP`
- `DRAMATIC_ARC_SPEC` (optional but recommended)
- `PEAK_RELEASE_PLAN` (optional)
- `CHARACTER_INTENT_SEEDS` (optional)
- `WORLD_LAW_SEEDS` (optional; for plausibility)

### PRODUCES (1–7)
- `SCENE_BLUEPRINT_SET`
- `BEAT_TO_SCENE_MAPPING`
- `SCENE_TURN_CATALOG`

### DEPENDS_ON
- `[02_DOMAIN_NARRATIVE_ENGINES/01__NARRATIVE_LOGIC_ENG, 02_DOMAIN_NARRATIVE_ENGINES/02__STORY_STRUCTURE_ENG, 02_DOMAIN_NARRATIVE_ENGINES/03__DRAMATIC_ARC_ENG]`

### OUTPUT_TARGET
- `PROJECT_ARTIFACTS/<project>/NARRATIVE/SCENES/`

---

## 3) DEFINITIONS (LOCAL)
- **Scene Blueprint** — структурная карта сцены (цель, конфликт, поворот, исход).
- **Scene Turn** — изменение состояния/направления внутри сцены (не обязательно твист).
- **Beat Routing** — правило, как один beat превращается в одну или несколько сцен (или наоборот).

---

## 4) BOUNDARIES (MANDATORY)

### IN SCOPE (OWNS)
- дизайн сцен как story-units (цели/конфликты/повороты/исходы)
- привязка сцен к beats/актовой структуре
- правила “валидной сцены” (что делает сцену рабочей)
- каталог типов поворотов сцены (scene turn types)

### OUT OF SCOPE (HARD)
- постановка сцены (кадры/камера/свет/монтаж)
- стиль/тон/атмосфера как доминирующий слой
- финальная литературная проза/диалоги (может отдать “что должны сказать”, но не пишет художественно как owning-scope)

### COLLISION RULE (ROUTING)
- Если вопрос “как выглядит/снимается” → `08_KNOWLEDGE_PRODUCTION_ENGINES/*`
- Если вопрос “темп и ритм истории” → `05__PACING_RHYTHM_ENG`
- Если вопрос “ставки/угрозы как карта” → `06__TENSION_STAKES_ENG`
- Если вопрос “манера речи/диалоги” → `03_DOMAIN_CHARACTER_ENGINES/07__DIALOGUE_ENG` и `08__SPEECH_NATURALIZATION_ENG`

---

## 5) OUTPUT SCHEMAS (MANDATORY)

### A) `SCENE_BLUEPRINT_SET`
**MUST (fields):**
- `set_id`
- `version`
- `scenes[]` (list; may be empty only if no beats exist)
- `structure_refs` (act/sequence references)
- `logic_refs` (atoms/constraints references)
- `open_unknowns[]`
- `scope_notes`

**Scene Blueprint (minimum):**
- `scene_id` (string)
- `act_ref` (act id)
- `sequence_ref` (optional)
- `beat_refs[]` (beat ids; non-empty unless explicitly “bridge scene”)
- `scene_role` (enum: `SETUP|ESCALATION|REVERSAL|REVEAL|DECISION|CONFRONTATION|PAYOFF|AFTERMATH|TRANSITION`)
- `objective` (string; who wants what)
- `conflict` (string; what blocks it)
- `stakes` (short; what it costs)
- `turn` (see Turn schema)
- `outcome` (enum: `WIN|LOSS|MIXED|SHIFT|STALEMATE`)
- `new_state` (postconditions; list of logic atoms or state statements)
- `hook_to_next` (string; why next scene happens)
- `constraints[]` (hard/soft constraints for the scene)
- `notes`

**Turn (minimum):**
- `turn_type` (enum: `REVEAL|REVERSAL|COMMITMENT|BETRAYAL|SACRIFICE|POWER_SHIFT|TRAP|ESCAPE|MORAL_CHOICE|TIME_PRESSURE|RESOURCE_SHOCK`)
- `trigger` (what causes the turn)
- `effect` (what changes)

**VALIDATION:**
- every `beat_ref` must exist in `BEAT_MAP`
- `new_state` must not violate `NARRATIVE_LOGIC_MODEL`
- if `scene_role=PAYOFF`, it must reference at least one earlier beat (payoff condition) OR mark as `open_unknown`

**STORAGE:**
- `PROJECT_ARTIFACTS/<project>/NARRATIVE/SCENES/SCENE_BLUEPRINT_SET.md`

---

### B) `BEAT_TO_SCENE_MAPPING`
**MUST (fields):**
- `mapping_id`
- `rules[]` (routing rules)
- `beat_to_scene[]` (explicit mapping list)

**Rule (minimum):**
- `rule_id`
- `when` (condition; e.g., beat type, complexity, pressure level)
- `route` (enum: `ONE_BEAT_ONE_SCENE|ONE_BEAT_MULTI_SCENE|MULTI_BEAT_ONE_SCENE`)
- `why` (short)

**Mapping item (minimum):**
- `beat_id`
- `scene_ids[]`
- `route_type`
- `notes`

**VALIDATION:**
- each beat is mapped at least once unless marked `route_to_scene=false` in beat map
- no scene references unknown beats

**STORAGE:**
- `PROJECT_ARTIFACTS/<project>/NARRATIVE/SCENES/BEAT_TO_SCENE_MAPPING.md`

---

### C) `SCENE_TURN_CATALOG`
**MUST (fields):**
- `catalog_id`
- `turn_types[]` (list)
- `recommended_usage[]`
- `anti_patterns[]`

**Turn Type (minimum):**
- `type`
- `definition`
- `best_for` (list: beat types / arc moments)
- `risks` (list)
- `checks` (validation questions)

**VALIDATION:**
- catalog must include at least: `REVEAL`, `REVERSAL`, `COMMITMENT`, `POWER_SHIFT`, `MORAL_CHOICE`

**STORAGE:**
- `PROJECT_ARTIFACTS/<project>/NARRATIVE/SCENES/SCENE_TURN_CATALOG.md`

---

## 6) PROCESS (PIPELINE)
1) Ingest structure + beats + arc.
2) Determine routing rules:
   - default: `ONE_BEAT_ONE_SCENE`
   - upgrade to multi-scene if beat is complex (multiple postconditions or high pressure)
3) For each beat (ordered):
   - assign `scene_role`
   - define objective/conflict/stakes
   - choose turn type aligned with arc pressure
   - define outcome + postconditions
4) Validate:
   - logic constraints (no impossible state)
   - payoff integrity (setup before payoff)
   - continuity handoffs (hook_to_next not empty for non-terminal scenes)
5) Emit outputs.

---

## 7) GATES (S0 BLOCKERS)
S0 (BLOCK) if:
- scene postconditions contradict `NARRATIVE_LOGIC_MODEL` hard constraints
- beats map to zero scenes (and beat is not explicitly “non-scene”)
- “payoff scenes” exist with no referenced setup (unearned payoff) in a way that breaks story coherence

S1 (HIGH) if:
- scenes have objective/conflict but no meaningful turn
- too many transition scenes (structure not dramatized)
- hooks are missing (scenes don’t cause next scenes)

S2/S3: quality warnings.

---

## 8) NOTES FOR DOWNSTREAM ENGINES
- `05__PACING_RHYTHM_ENG` uses scene density and turn spacing (story-time).
- `06__TENSION_STAKES_ENG` can attach stakes metadata per scene.
- `09__NARRATIVE_CONTINUITY_ENG` checks scene-to-scene consistency.

---

LOCK: OPEN
