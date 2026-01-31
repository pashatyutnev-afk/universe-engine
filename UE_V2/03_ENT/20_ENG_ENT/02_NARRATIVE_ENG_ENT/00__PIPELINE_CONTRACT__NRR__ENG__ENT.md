# DOMAIN NARRATIVE ENGINES — REALM (README)
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/02_DOMAIN_NARRATIVE_ENGINES/00__README__DOMAIN_NARRATIVE_ENGINES.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 02_DOMAIN_NARRATIVE_ENGINES
DOC_TYPE: REALM_README
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.ENG.REALM.NARRATIVE.001
OWNER: SYSTEM
ROLE: Family realm boundaries + terminology + output targets for narrative-domain engines.

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Narrative family realm created: boundaries, outputs, and collision routing for all narrative engines."
- REASON: "Family was empty; required for deterministic stamping of 02_DOMAIN_NARRATIVE_ENGINES."
- IMPACT: "Narrative engines can be produced in canon order without scope drift."
- CHANGE_ID: UE.CHG.2026-01-08.ENG.NARR.REALM.001

---

## 0) PURPOSE (LAW)
Семейство `02_DOMAIN_NARRATIVE_ENGINES` отвечает за **внутреннюю логику истории**:
- почему события происходят именно так (causal + motivation fit на уровне сюжета)
- как строится структура, арки, сцены, темп, напряжение
- как держится непрерывность и смысл

Это НЕ “производство” и НЕ “стиль” — это **доменная логика повествования**.

---

## 1) SCOPE (IN / OUT)

### IN SCOPE (OWNS)
- Story logic / narrative causality (логические цепочки внутри истории)
- Story-level structure (акты/арки/сцены как narrative units)
- Pacing как **story-time** (ритм событий истории, не монтаж)
- Stakes / tension на уровне истории
- Foreshadow / twist / reveal как narrative mechanics
- Continuity и смысл/тема

### OUT OF SCOPE (HARD)
- Production editing rhythm (монтаж, длительности кадров, склейки) → `08_KNOWLEDGE_PRODUCTION_ENGINES/07__EDITING_MONTAGE_ENG.md`
- Visual/Audio implementation (камера/свет/звук продакшн) → семья `08_*`
- Deep music composition/arrangement → семья `09_*`
- Tone/mood/style constraints (атмосфера, символизм) → семья `06_*`
- Pure event mechanics без story-meaning (тайминг/рандом) → семья `05_EXPRESSION_ENGINES` (частично)

---

## 2) COLLISION ROUTING (MANDATORY)
Если возникает пересечение:
- "Это про **как ощущается**?" → `06_GENRE_STYLE_ENGINES/*`
- "Это про **как смонтировано/показано на экране**?" → `08_KNOWLEDGE_PRODUCTION_ENGINES/07__EDITING_MONTAGE_ENG.md`
- "Это про **чистую механику события без смысла/структуры истории**?" → `05_EXPRESSION_ENGINES/*`
- "Это про **персонажа (психология/мотивация/речь)**?" → `03_DOMAIN_CHARACTER_ENGINES/*`

---

## 3) FAMILY OUTPUT TARGETS (STANDARD)
Нарративные движки производят **story-domain артефакты** (логические, не продакшн):
- `NARRATIVE_LOGIC_MODEL`
- `STORY_STRUCTURE_BLUEPRINT`
- `DRAMATIC_ARC_SPEC`
- `SCENE_CONSTRUCTION_RULESET`
- `PACING_PROFILE_STORY_TIME`
- `TENSION_STAKES_MAP`
- `FORESHADOW_PLAN`
- `TWIST_REVEAL_PLAN`
- `CONTINUITY_CHECKLIST`
- `THEME_MEANING_STATEMENT`

OUTPUT_TARGET (пока базовый, без привязки к будущим 02_STANDARDS):
- `OUTPUT_TARGET: PROJECT_ARTIFACTS/<project>/NARRATIVE/<artifact_type>/...`

---

## 4) TEMPLATES (CANON)
ENGINE TEMPLATE:
https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/02_DOMAIN_NARRATIVE_ENGINES/00__TEMPLATE__ENGINE__DOMAIN_NARRATIVE_ENGINES.md

README TEMPLATE:
https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/02_DOMAIN_NARRATIVE_ENGINES/00__TEMPLATE__README__DOMAIN_NARRATIVE_ENGINES.md

---

## 5) MINIMUM FAMILY GATES (FAST)
G1 — Contract: каждый движок имеет mini-contract (CONSUMES/PRODUCES/DEPENDS_ON/OUTPUT_TARGET).
G2 — Boundary: каждый движок имеет IN/OUT + collision routing.
G3 — Schemas: каждый PRODUCES имеет минимальную схему output (fields + validation).
G4 — Non-duplication: никакой “монтажной” терминологии как owning-scope.

---

## 6) DEPENDENCY BASELINE (DEFAULT)
Нарративные движки обычно зависят от:
- `01_CORE_ENGINES/*` (идентичность/состояние/жизненный цикл проекта/саги)

Но зависимости должны быть **явными** и **минимальными**: если не нужно — `DEPENDS_ON: []`.

---

## 7) CANON NOTE
Семейство заполняется строго по номеру. Пропуск/перестановка = нарушение порядка канона.

--- END.
