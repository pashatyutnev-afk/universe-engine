# CHARACTER CORE ENGINE
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/03_DOMAIN_CHARACTER_ENGINES/01__CHARACTER_CORE_ENG.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 03_DOMAIN_CHARACTER_ENGINES
ENGINE: 01__CHARACTER_CORE_ENG
DOC_TYPE: ENGINE
LEVEL: L2
STATUS: ACTIVE
LOCK: OPEN
VERSION: 1.0.0
UID: UE.ENG.CHAR.CORE.001
OWNER: SYSTEM
ROLE: Define a deterministic character core model (identity, invariants, traits, boundaries) to be consumed by motivation/values/psychology/behavior/relationships/dialogue engines.

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Character Core Engine created: character core passport schema, invariants, trait model, and validation gates."
- REASON: "Character family required a foundational identity engine before motivations, values, and speech."
- IMPACT: "All downstream character engines can consume a stable character core and remain consistent across narrative and production."
- CHANGE_ID: UE.CHG.2026-01-08.ENG.CHAR.CORE.001

---

## 0) PURPOSE (LAW)
Этот движок создаёт **ядро персонажа** (Character Core) — стабильную модель “кто это”:
- идентичность (identity)
- инварианты (что не меняется без особого события)
- ключевые черты (traits) и ограничения
- базовые роли и функции в истории (без владения структурой сюжета)
- “контракт персонажа” для всех последующих движков персонажей

Цель: чтобы мотивации/психология/поведение/диалоги не дрейфовали и не противоречили друг другу.

---

## 1) NON-GOALS (HARD)
Движок НЕ делает:
- мотивации/желания как система (это `02__MOTIVATION_DESIRE_ENG`)
- мораль/ценности (это `03__MORAL_VALUE_ENG`)
- психология/внутренние состояния как динамика (это `04__CHARACTER_PSYCHOLOGY_ENG`)
- поведенческие правила выбора (это `05__CHARACTER_BEHAVIOR_ENG`)
- отношения (это `06__RELATIONSHIP_ENG`)
- диалоги/естественность речи (это `07__DIALOGUE_ENG` и `08__SPEECH_NATURALIZATION_ENG`)
- сюжетную структуру/сцены (narrative family)
- мировые законы/социологию/экономику (world family)
- постановку/актёрскую игру/монтаж (production family)

---

## 2) MINI-CONTRACT (MANDATORY)

### CONSUMES (1–7)
- `CORE_IDENTITY`
- `CORE_STATE`
- `CHARACTER_SEED_NOTES` (optional: rough notes, sketches, archetypes)
- `WORLD_LAW_SEEDS` (optional: constraints that affect identity)
- `NARRATIVE_PREMISE` (optional: who the protagonist/antagonist is, if known)

### PRODUCES (1–7)
- `CHARACTER_CORE_PASSPORT`
- `CHARACTER_INVARIANTS`
- `CHARACTER_TRAIT_PROFILE`

### DEPENDS_ON
- `[01_CORE_ENGINES/01__CORE_IDENTITY_ENG, 01_CORE_ENGINES/02__CORE_STATE_ENG]`

### OUTPUT_TARGET
- `PROJECT_ARTIFACTS/<project>/CHARACTERS/CORE/`

---

## 3) DEFINITIONS (LOCAL)
- **Character Core** — минимальный набор свойств, делающих персонажа узнаваемым и непротиворечивым.
- **Invariant** — свойство, которое не меняется без явного “break event” (травма, откровение, трансформация).
- **Trait** — черта (поведенческая/когнитивная/социальная), которая влияет на решения.
- **Boundary** — что персонаж не делает/не может делать (hard/soft).
- **Role Tag** — метка роли (не структура сюжета, а функция: witness, catalyst, mirror).

---

## 4) BOUNDARIES (MANDATORY)

### IN SCOPE (OWNS)
- идентичность персонажа (имя/архетип/роль-теги)
- инварианты и границы поведения (что “невозможно/нехарактерно”)
- стабильные черты и базовые компетенции
- “контракт” на консистентность для всех последующих движков

### OUT OF SCOPE (HARD)
- динамическая психология и эмоциональные кривые
- мотивационные системы и ценностные выборы (в деталях)
- развитие/эволюция (это отдельные движки 09/10)
- события/сцены/монтаж/стиль

### COLLISION RULE (ROUTING)
- Если требуется изменить инвариант → `09__GROWTH_TRAUMA_ENG` + `10__CHARACTER_EVOLUTION_ENG` (и потом обновить core через controlled update)
- Если спор про “мир запрещает/разрешает” → `04_DOMAIN_WORLD_ENGINES/*`
- Если спор про “что происходит в сюжете” → `02_DOMAIN_NARRATIVE_ENGINES/*`
- Если спор про “как сыграть/показать” → `08_KNOWLEDGE_PRODUCTION_ENGINES/*`

---

## 5) OUTPUT SCHEMAS (MANDATORY)

### A) `CHARACTER_CORE_PASSPORT`
**MUST (fields):**
- `character_id` (string; stable within project)
- `name` (string; can be placeholder)
- `aliases[]` (optional)
- `archetype_tags[]` (optional)
- `role_tags[]` (optional; e.g., `PROTAGONIST|ANTAGONIST|CATALYST|WITNESS|MIRROR`)
- `core_identity_statement` (1–3 sentences)
- `background_stub` (short; non-canon details allowed but marked)
- `capabilities[]` (skills/advantages)
- `limits[]` (constraints)
- `invariants_ref` (pointer)
- `traits_ref` (pointer)
- `boundaries_ref` (pointer or embedded)
- `world_constraints_ref` (optional)
- `open_unknowns[]`
- `scope_notes`

**VALIDATION:**
- `character_id` unique
- `core_identity_statement` cannot contradict `WORLD_LAW_SEEDS` if provided
- if `name` placeholder, mark in `open_unknowns`

**STORAGE:**
- `PROJECT_ARTIFACTS/<project>/CHARACTERS/CORE/<character_id>/CHARACTER_CORE_PASSPORT.md`

---

### B) `CHARACTER_INVARIANTS`
**MUST (fields):**
- `character_id`
- `hard_invariants[]` (non-empty for canon characters)
- `soft_invariants[]` (optional)
- `break_conditions[]` (what must happen to change them)
- `verification_questions[]`

**Invariant (minimum):**
- `id`
- `statement`
- `type` (enum: `MORAL|IDENTITY|CAPABILITY|RELATIONSHIP|WORLD_BOUND`)
- `strength` (`HARD|SOFT`)
- `why` (short)
- `break_requires` (enum: `TRAUMA|REVELATION|SACRIFICE|TRANSFORMATION|NONE`)
- `notes`

**VALIDATION:**
- hard invariants must have explicit `why`
- if `break_requires=NONE` then invariant cannot be HARD (else contradiction)

**STORAGE:**
- `PROJECT_ARTIFACTS/<project>/CHARACTERS/CORE/<character_id>/CHARACTER_INVARIANTS.md`

---

### C) `CHARACTER_TRAIT_PROFILE`
**MUST (fields):**
- `character_id`
- `traits[]`
- `trait_conflicts[]` (optional)
- `trait_expression_notes[]` (optional)
- `anti_patterns[]`

**Trait (minimum):**
- `id`
- `name`
- `domain` (enum: `COGNITIVE|EMOTIONAL|SOCIAL|PHYSICAL|MORAL`)
- `polarity` (enum: `STRENGTH|WEAKNESS|MIXED`)
- `default_expression` (how it shows)
- `stress_expression` (how it shows under pressure)
- `edge_case` (when it fails)
- `confidence` (`LOW|MEDIUM|HIGH`)

**VALIDATION:**
- each trait must specify both default and stress expression
- if too many traits (>12) → warning (S2) for over-specified character

**STORAGE:**
- `PROJECT_ARTIFACTS/<project>/CHARACTERS/CORE/<character_id>/CHARACTER_TRAIT_PROFILE.md`

---

## 6) PROCESS (PIPELINE)
1) Ingest seeds + world constraints + premise.
2) Draft `core_identity_statement` (minimal, stable).
3) Define invariants:
   - 2–5 HARD invariants (who they are)
   - 2–6 SOFT invariants (habits/preferences) if needed
4) Define trait profile:
   - 5–10 traits with default + stress expression
5) Define boundaries/limits:
   - what they won’t do (moral/identity)
   - what they can’t do (capability/world)
6) Validate:
   - no hard invariant can be casually broken
   - no trait set contradicts invariants
7) Emit outputs.

---

## 7) GATES (S0 BLOCKERS)
S0 (BLOCK) if:
- character core contradicts hard world constraints (if provided)
- hard invariants are missing for a canon character
- invariants declare “break requires NONE” while marked HARD
- character_id is unstable/duplicated

S1 (HIGH) if:
- identity statement is vague (“just a guy”) with no differentiator
- traits conflict with each other with no explanation (e.g., “always honest” + “constant liar”)

S2/S3: quality warnings.

---

## 8) NOTES FOR DOWNSTREAM ENGINES
- Motivation engine consumes invariants + traits to avoid generating incompatible desires.
- Values engine anchors moral choices to invariants/boundaries.
- Behavior engine uses stress expression for decision heuristics.
- Dialogue engine uses identity statement and traits to constrain voice.

---

LOCK: OPEN
