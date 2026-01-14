# KB TAGS — CANON TAG SYSTEM (KB)
FILE: 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/05__KB_TAGS.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: SPEC
INDEX_TYPE: TAG_REGISTRY (KB)
LEVEL: L1
STATUS: DRAFT
LOCK: OPEN
VERSION: 1.0.0
UID: UE.KB.SPEC.TAGS.001
OWNER: SYSTEM
ROLE: Define canonical tags for KB modules to enable deterministic search, coverage tracking, and entity KB scope mapping

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created KB tag registry: domain tags + type tags + skill tags + gate tags + maturity tags."
- REASON: "KB must be searchable and enforceable; tags support one-index navigation and coverage dashboards."
- IMPACT: "All KB modules can be tagged consistently; entity scope maps and audits become deterministic."
- CHANGE_ID: UE.CHG.2026-01-14.KB.TAGS.001

---

## 0) PURPOSE (LAW)
Теги KB нужны для:
- быстрого поиска (в master-index и в модулях),
- карты “какие знания нужны сущности” (entity→scope),
- контроля покрытия (coverage),
- сборки модулей по задаче/пайплайну.

Теги не заменяют типы KB-единиц и не являются NAV/EXISTENCE индексом.

---

## 1) TAGGING RULES (ABSOLUTE)
### 1.1 Where tags live
Каждый KB модуль (TOPIC/LIBRARY ITEM/PILLAR/CONNECTOR/MAP) должен содержать секцию:
`TAGS:`
со списком тегов (одна строка или список).

### 1.2 Tag format
- Тег — `lowercase_with_underscores`
- Без пробелов, без спецсимволов.
- Не использовать “свободные теги” вне реестра, кроме временных `tmp_*` (см. 6.3).

### 1.3 Minimal tags (mandatory)
Любой модуль должен иметь минимум:
- один `domain_*`
- один `type_*`

### 1.4 No-dup / no-synonyms
- Синонимы запрещены (один смысл → один тег).
- Если нужен новый смысл — добавляется новый тег через KB change control.

---

## 2) DOMAIN TAGS (MANDATORY)
Используется ровно один доменный тег:

- `domain_narrative`
- `domain_character`
- `domain_world`
- `domain_visual`
- `domain_sound_music`
- `domain_production`
- `domain_marketing`
- `domain_research`
- `domain_reference`
- `domain_governance` (только для KB governance файлов)

---

## 3) TYPE TAGS (MANDATORY)
Используется ровно один типовой тег:

- `type_pillar`
- `type_topic`
- `type_checklist`
- `type_rubric`
- `type_template`
- `type_pattern`
- `type_anti_pattern`
- `type_example`
- `type_prompt_lib`
- `type_entity_connector`
- `type_connector_standard`
- `type_scope_map`
- `type_rel_map`
- `type_xref_map`
- `type_glossary_terms`

---

## 4) SKILL / PROFESSIONAL TAGS (RECOMMENDED)
Эти теги описывают компетенции (для “SPC супер-профи”):

- `skill_principles`
- `skill_procedure`
- `skill_decision_making`
- `skill_quality_control`
- `skill_debug_fix`
- `skill_planning`
- `skill_review`
- `skill_consistency`
- `skill_creativity`
- `skill_research`

Можно использовать несколько.

---

## 5) GATE / ENFORCEMENT TAGS (RECOMMENDED)
Теги для модулей, которые являются обязательными проверками:

- `gate_required`
- `gate_quality`
- `gate_policy`
- `gate_validation`
- `gate_qa`
- `gate_source_lock`
- `gate_usage_required`

---

## 6) MATURITY / STATE TAGS (RECOMMENDED)
Теги зрелости содержимого (параллельно module state system):

- `maturity_seed`      (набросок)
- `maturity_working`   (рабочая версия)
- `maturity_verified`  (подтверждено применением)
- `maturity_deprecated` (устарело)

---

## 7) TASK / PIPELINE TAGS (OPTIONAL)
Если модуль применяется в конкретных пайплайнах/задачах, допускается:

- `task_scene_build`
- `task_track_generation`
- `task_story_outline`
- `task_character_design`
- `task_visual_prompting`
- `task_mix_master`
- `task_release_pack`

Правило:
- task-теги вводим только когда есть карта `TASK_TO_KB_SCOPE_MAP` (иначе дрейф).

---

## 8) TEMP TAGS (CONTROLLED EXCEPTION)
### 8.1 Allowed temporary tags
Разрешены временные теги только формата:
- `tmp_<something>`

### 8.2 Expiration rule
Любой `tmp_*` тег должен быть:
- либо удалён,
- либо заменён на канонический тег
в ближайшей итерации KB change control.

---

## 9) EXAMPLE TAG SETS (FAST)
### Example: TOPIC in sound/music
TAGS:
- domain_sound_music
- type_topic
- skill_procedure
- gate_quality
- maturity_working

### Example: RUBRIC
TAGS:
- domain_sound_music
- type_rubric
- skill_quality_control
- gate_qa
- gate_required
- maturity_verified

### Example: SPC PRO PACK file (playbooks)
TAGS:
- domain_governance
- type_entity_connector
- skill_procedure
- gate_usage_required
- maturity_working

--- END.
