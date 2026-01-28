# THEME & MEANING ENGINE
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/02_DOMAIN_NARRATIVE_ENGINES/10__THEME_MEANING_ENG.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 02_DOMAIN_NARRATIVE_ENGINES
ENGINE: 10__THEME_MEANING_ENG
DOC_TYPE: ENGINE
LEVEL: L2
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.ENG.NARR.THEME.001
OWNER: SYSTEM
ROLE: Define and validate theme/meaning: thematic thesis, value conflicts, motif-to-beat mapping, and meaning payoffs (story-domain, not style-symbolism owning).

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Theme & Meaning Engine created: thesis, value conflict map, motif plan, and meaning payoff checks."
- REASON: "Needed deterministic thematic layer so narrative doesn't drift into empty events."
- IMPACT: "Themes become auditable and align with structure, stakes, and character change."
- CHANGE_ID: UE.CHG.2026-01-08.ENG.NARR.THEME.001

---

## 0) PURPOSE (LAW)
Этот движок формирует **смысловой слой истории**:
- тематический тезис (что история утверждает/исследует)
- ценностные конфликты (какие ценности сталкиваются и где)
- карту мотивов/смысловых сигналов (на уровне story-domain)
- “оплату смысла” (meaning payoff): где тезис проверяется и чем заканчивается

Важно: это НЕ стилистический символизм как художественная подача (это в стиле), а смысл как логика идеи.

---

## 1) NON-GOALS (HARD)
Движок НЕ делает:
- художественные метафоры/символизм как владеющий слой → `06_GENRE_STYLE_ENGINES/04__SYMBOLISM_ENG` и `05__METAPHOR_ENG`
- дизайн сцен (это `04__SCENE_CONSTRUCTION_ENG`)
- развитие персонажей как психология/арки травмы (это `03_DOMAIN_CHARACTER_ENGINES/*`)
- монтаж/визуальные приёмы “смысла” (production) → `08_*`

---

## 2) MINI-CONTRACT (MANDATORY)

### CONSUMES (1–12)
- `CORE_IDENTITY`
- `CORE_STATE`
- `NARRATIVE_LOGIC_MODEL`
- `STORY_STRUCTURE_BLUEPRINT`
- `BEAT_MAP`
- `SCENE_BLUEPRINT_SET` (optional but recommended)
- `DRAMATIC_ARC_SPEC` (optional)
- `TENSION_STAKES_MAP` (optional)
- `PAYOFF_OBLIGATIONS` (optional)
- `CHARACTER_INTENT_SEEDS` (optional)
- `CHARACTER_CORE_NOTES` (optional)
- `WORLD_LAW_SEEDS` (optional)

### PRODUCES (1–7)
- `THEMATIC_THESIS_SPEC`
- `VALUE_CONFLICT_MAP`
- `MEANING_PAYOFF_TRACKER`

### DEPENDS_ON
- `[02_DOMAIN_NARRATIVE_ENGINES/02__STORY_STRUCTURE_ENG, 02_DOMAIN_NARRATIVE_ENGINES/06__TENSION_STAKES_ENG, 02_DOMAIN_NARRATIVE_ENGINES/04__SCENE_CONSTRUCTION_ENG]`

### OUTPUT_TARGET
- `PROJECT_ARTIFACTS/<project>/NARRATIVE/THEME/`

---

## 3) DEFINITIONS (LOCAL)
- **Theme** — вопрос/идея, которую история исследует.
- **Thesis** — формулировка позиции/гипотезы (“если X, то Y”), которая проверяется событиями.
- **Value Conflict** — столкновение ценностей (свобода vs безопасность, правда vs любовь).
- **Meaning Payoff** — момент, когда история “платит” за поднятый смысл: показывает цену/вывод/переворот ценности.

---

## 4) BOUNDARIES (MANDATORY)

### IN SCOPE (OWNS)
- тезис и набор под-тем (theme stack)
- карта ценностных конфликтов по структуре/битам/сценам
- смысловые обязательства (что должно быть доказано/опровергнуто)
- проверки: “смысл не висит”, “смысл не заявлен без проверки”

### OUT OF SCOPE (HARD)
- художественная символика как техника подачи
- психотерапевтическая глубина персонажей как владеющий слой
- стиль/тон/атмосфера как владение

### COLLISION RULE (ROUTING)
- Если спор про символы/метафоры/образы → `06_GENRE_STYLE_ENGINES/04__SYMBOLISM_ENG` / `05__METAPHOR_ENG`
- Если спор про мотивацию/ценности персонажа как психология → `03_DOMAIN_CHARACTER_ENGINES/*`
- Если спор про “как показать смысл в кадре” → `08_*`

---

## 5) OUTPUT SCHEMAS (MANDATORY)

### A) `THEMATIC_THESIS_SPEC`
**MUST (fields):**
- `thesis_id`
- `version`
- `primary_theme_question` (question form)
- `thesis_statement` (testable claim)
- `anti_thesis` (opposing claim)
- `subthemes[]` (optional)
- `proof_requirements[]` (what must be demonstrated)
- `disproof_requirements[]` (what would disprove it)
- `scope_notes`
- `open_unknowns[]`

**VALIDATION:**
- thesis must be testable (not “life is complex”)
- proof requirements must map to at least one beat/scene candidate (else open_unknown with route)

**STORAGE:**
- `PROJECT_ARTIFACTS/<project>/NARRATIVE/THEME/THEMATIC_THESIS_SPEC.md`

---

### B) `VALUE_CONFLICT_MAP`
**MUST (fields):**
- `map_id`
- `conflicts[]`
- `alignment[]` (mapping to beats/scenes)
- `escalation_notes[]`
- `anti_patterns[]`

**Conflict (minimum):**
- `conflict_id`
- `value_A` (e.g., TRUTH)
- `value_B` (e.g., LOVE)
- `who_represents_A` (actor/system)
- `who_represents_B`
- `what_is_at_stake` (stake ids or short)
- `resolution_modes[]` (enum: `A_WINS|B_WINS|SYNTHESIS|TRAGIC_COST|UNRESOLVED`)
- `notes`

**Alignment item (minimum):**
- `ref_type` (enum: `ACT|SEQUENCE|SCENE|BEAT`)
- `ref_id`
- `conflict_ids[]`
- `pressure_level` (0..100; optional)
- `what_is_tested_here` (short)

**VALIDATION:**
- each conflict must appear at least twice (setup + test), unless explicitly “single-beat theme”
- conflicts must not contradict logic model (e.g., value choice impossible due to missing options)

**STORAGE:**
- `PROJECT_ARTIFACTS/<project>/NARRATIVE/THEME/VALUE_CONFLICT_MAP.md`

---

### C) `MEANING_PAYOFF_TRACKER`
**MUST (fields):**
- `tracker_id`
- `meaning_obligations[]`
- `payoff_events[]`
- `links[]`
- `unpaid_meaning[]`
- `unearned_meaning[]`

**Meaning Obligation (minimum):**
- `id`
- `created_by_ref` (beat/scene where theme is stated/test begins)
- `theme_ref` (thesis_id or conflict_id)
- `promise` (what meaning is promised)
- `due_by_ref` (act/segment or `UNKNOWN`)
- `severity_if_unpaid` (`S0|S1|S2|S3`)
- `notes`

**Payoff Event (minimum):**
- `payoff_id`
- `ref_type` (enum: `ACT|SEQUENCE|SCENE|BEAT`)
- `ref_id`
- `what_is_shown` (short: proof/disproof/cost/synthesis)
- `result` (enum: `PROVES_THESIS|DISPROVES_THESIS|COMPLICATES|SYNTHESIS|TRAGIC_CONFIRMATION`)
- `notes`

**Link (minimum):**
- `obligation_id`
- `payoff_id`
- `quality` (enum: `CLEAN|OK|WEAK|MISALIGNED`)
- `notes`

**VALIDATION:**
- any S0 meaning obligation must not remain unpaid
- “meaning payoff” must be demonstrated through story consequences, not only stated (if only stated → unearned_meaning warning)

**STORAGE:**
- `PROJECT_ARTIFACTS/<project>/NARRATIVE/THEME/MEANING_PAYOFF_TRACKER.md`

---

## 6) PROCESS (PIPELINE)
1) Extract candidate themes from:
   - core identity, stakes, character desires, world constraints
2) Formulate thesis + anti-thesis.
3) Build value conflicts:
   - map who embodies which values
4) Align conflicts to beats/scenes:
   - setup tests, escalation tests, final test at/after peak
5) Create meaning obligations:
   - whenever theme is stated or a value conflict becomes explicit
6) Create payoff candidates:
   - where thesis is proven/disproven/paid with cost
7) Validate “earned meaning”:
   - proof via consequence
   - no unpaid critical obligations
8) Emit outputs.

---

## 7) GATES (S0 BLOCKERS)
S0 (BLOCK) if:
- primary thesis is stated but has no possible proof/payoff path
- critical meaning obligation (S0) is unpaid by the ending segment
- thematic resolution contradicts established stakes/logic in an impossible way

S1 (HIGH) if:
- theme exists only as dialogue statements (no consequence proof)
- conflicts appear once and disappear (token theme)

S2/S3: quality warnings.

---

## 8) NOTES
Смысл — это не лозунг, а проверяемая гипотеза:
история обязана “показать” цену и вывод.
Этот движок делает смысл измеримым.

---

LOCK: OPEN
