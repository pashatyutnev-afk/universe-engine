# TWIST & REVEAL ENGINE
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/02_DOMAIN_NARRATIVE_ENGINES/08__TWIST_REVEAL_ENG.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 02_DOMAIN_NARRATIVE_ENGINES
ENGINE: 08__TWIST_REVEAL_ENG
DOC_TYPE: ENGINE
LEVEL: L2
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.ENG.NARR.TWIST.001
OWNER: SYSTEM
ROLE: Design and validate twists/reveals: what changes, why it’s logical, how it’s seeded, and how it impacts stakes, arc, and continuity (story-domain, not production).

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Twist & Reveal Engine created: reveal catalog, twist design rules, seed dependency checks, and impact validation."
- REASON: "Needed a canonical mechanism to create logical, seeded reveals and control twist impact."
- IMPACT: "Reveals become deterministic, earned, and continuity-safe."
- CHANGE_ID: UE.CHG.2026-01-08.ENG.NARR.TWIST.001

---

## 0) PURPOSE (LAW)
Этот движок проектирует **раскрытия и твисты** так, чтобы они были:
- логически возможны (не ломают причинность)
- заранее подготовлены (seeded)
- меняют состояние истории измеримо (stakes/pressure/relationships)
- не создают дыр в непрерывности (continuity)

Twist/Reveal = изменение смысла уже известных фактов, или внезапная новая информация, которая
переворачивает траекторию.

---

## 1) NON-GOALS (HARD)
Движок НЕ делает:
- “посев” семян (это `07__FORESHADOWING_ENG`)
- полный дизайн сцен (это `04__SCENE_CONSTRUCTION_ENG`)
- монтаж/режиссёрские способы скрывать информацию (production) → `08_*`
- стиль/жанровую подачу твиста (тон/атмосфера) → `06_*`

---

## 2) MINI-CONTRACT (MANDATORY)

### CONSUMES (1–12)
- `CORE_IDENTITY`
- `CORE_STATE`
- `NARRATIVE_LOGIC_MODEL`
- `STORY_STRUCTURE_BLUEPRINT`
- `BEAT_MAP`
- `DRAMATIC_ARC_SPEC` (optional but recommended)
- `TENSION_STAKES_MAP` (optional but recommended)
- `PAYOFF_OBLIGATIONS` (optional)
- `FORESHADOW_PLAN` (optional but recommended)
- `SEED_CATALOG` (optional but recommended)
- `PROMISE_PAYOFF_MAP` (optional)
- `SCENE_BLUEPRINT_SET` (optional)

### PRODUCES (1–7)
- `REVEAL_CATALOG`
- `TWIST_DESIGN_SPECS`
- `TWIST_IMPACT_REPORT`

### DEPENDS_ON
- `[02_DOMAIN_NARRATIVE_ENGINES/01__NARRATIVE_LOGIC_ENG, 02_DOMAIN_NARRATIVE_ENGINES/07__FORESHADOWING_ENG, 02_DOMAIN_NARRATIVE_ENGINES/06__TENSION_STAKES_ENG]`

### OUTPUT_TARGET
- `PROJECT_ARTIFACTS/<project>/NARRATIVE/TWISTS/`

---

## 3) DEFINITIONS (LOCAL)
- **Reveal** — раскрытие факта/правды, меняющее понимание.
- **Twist** — reveal с сильным изменением траектории (directional reversal), часто ломает ожидание.
- **Truth Payload** — “что именно стало известно”.
- **Recontext** — переосмысление ранее виденного через новый факт.
- **Earned Twist** — твист, который аудитория могла бы сложить по семенам, но не был очевиден.

---

## 4) BOUNDARIES (MANDATORY)

### IN SCOPE (OWNS)
- дизайн reveals/twists (что, где, зачем)
- проверка seededness (есть ли семена, не слишком ли явные)
- проверка логической допустимости (logic constraints)
- оценка влияния на stakes/arc/structure
- обязательства последствий (после твиста должны быть последствия)

### OUT OF SCOPE (HARD)
- чистая постановка “как скрыть” (кадрирование/монтаж/звук)
- переписывание темпа целиком (хотя может выдавать рекомендации для pacing engine)
- художественный стиль подачи (genre/style engines)

### COLLISION RULE (ROUTING)
- Если вопрос “как именно посеять” → `07__FORESHADOWING_ENG`
- Если вопрос “как пересобрать сцены под твист” → `04__SCENE_CONSTRUCTION_ENG`
- Если вопрос “как изменить темп” → `05__PACING_RHYTHM_ENG`
- Если вопрос “как показать в кадре” → `08_*`

---

## 5) OUTPUT SCHEMAS (MANDATORY)

### A) `REVEAL_CATALOG`
**MUST (fields):**
- `catalog_id`
- `version`
- `reveals[]`
- `classification_rules[]`
- `anti_patterns[]`

**Reveal (minimum):**
- `reveal_id`
- `type` (enum: `TRUTH|IDENTITY|MOTIVE|RULE|LOCATION|BETRAYAL|POWER|SECRET_HISTORY|SYSTEM_REALITY`)
- `twist_level` (enum: `LOW|MEDIUM|HIGH`)
- `truth_payload` (string; what becomes known)
- `recontext_targets[]` (what earlier facts get reinterpreted)
- `trigger_ref` (ref_type+ref_id; beat/scene where revealed)
- `required_seeds[]` (seed ids)
- `logic_refs[]` (atoms/constraints)
- `stakes_impacted[]` (stake ids)
- `pressure_delta` (`UP|DOWN|SHIFT|NONE`)
- `expected_audience_question` (what this answers/creates)
- `notes`

**VALIDATION:**
- any reveal with `twist_level=HIGH` must have `required_seeds` non-empty OR explicit `seed_exception_reason`
- `trigger_ref` must exist in beats/scenes if those sets are provided
- reveal must not violate hard plausibility rules

**STORAGE:**
- `PROJECT_ARTIFACTS/<project>/NARRATIVE/TWISTS/REVEAL_CATALOG.md`

---

### B) `TWIST_DESIGN_SPECS`
**MUST (fields):**
- `specs_id`
- `twists[]`
- `design_rules[]`
- `earnedness_checks[]`

**Twist Spec (minimum):**
- `twist_id`
- `reveal_id` (link to catalog)
- `structural_role` (enum: `MIDPOINT_REVERSAL|ALL_IS_LOST|FALSE_VICTORY|FALSE_DEFEAT|CLIMAX_SHIFT|MYSTERY_KEY`)
- `why_it_works` (short)
- `what_changes_now` (state change)
- `who_pays` (stake holders affected)
- `required_follow_through[]` (obligations created)
- `seed_map` (seed ids + where planted)
- `telegraph_risk` (`LOW|MEDIUM|HIGH`)
- `continuity_risks[]`
- `routing_notes[]` (what engine must act next)

**Design Rule (minimum):**
- `id`
- `rule_text`
- `strength` (`HARD|SOFT`)

**Earnedness check (minimum):**
- `id`
- `question`
- `pass_condition`

**VALIDATION:**
- twists must create at least one meaningful consequence obligation (`required_follow_through`)
- `telegraph_risk=HIGH` must include mitigation note (misdirect, subtle seed, delay reminder)

**STORAGE:**
- `PROJECT_ARTIFACTS/<project>/NARRATIVE/TWISTS/TWIST_DESIGN_SPECS.md`

---

### C) `TWIST_IMPACT_REPORT`
**MUST (fields):**
- `report_id`
- `impacts[]` (can be empty)
- `severity_summary`
- `required_repairs[]`
- `recommended_updates[]`

**Impact (minimum):**
- `id`
- `twist_id`
- `impact_area` (enum: `LOGIC|STRUCTURE|PACING|TENSION_STAKES|CONTINUITY|CHARACTER`)
- `description`
- `severity` (`S0|S1|S2|S3`)
- `why`
- `fix_route` (engine pointer)

**VALIDATION:**
- any S0 must have fix_route and cannot be left unresolved for canon execution

**STORAGE:**
- `PROJECT_ARTIFACTS/<project>/NARRATIVE/TWISTS/TWIST_IMPACT_REPORT.md`

---

## 6) PROCESS (PIPELINE)
1) Identify candidate reveals:
   - from mysteries/secrets/stakes obligations
   - from arc/structure reversal needs
2) For each reveal:
   - define truth payload and recontext targets
   - select trigger location (beat/scene)
3) Validate seededness:
   - required seeds exist and are placed early enough
   - telegraph risk evaluated
4) Validate logic:
   - truth payload compatible with world/narrative logic
5) Compute impact:
   - stakes map updates
   - arc pressure delta and pacing consequences
   - continuity risk list
6) Emit outputs.

---

## 7) GATES (S0 BLOCKERS)
S0 (BLOCK) if:
- twist requires facts that contradict hard logic constraints
- high-level twist has no seed path and no explicit exception rationale
- twist creates stakes obligations but provides no follow-through path

S1 (HIGH) if:
- telegraph risk is high with no mitigation
- impact on continuity is severe but not routed

S2/S3: quality warnings.

---

## 8) NOTES
Twist is not a trick; it is a controlled reframe:
- must be possible
- must be prepared
- must have consequences
This engine enforces all three.

---

LOCK: OPEN
