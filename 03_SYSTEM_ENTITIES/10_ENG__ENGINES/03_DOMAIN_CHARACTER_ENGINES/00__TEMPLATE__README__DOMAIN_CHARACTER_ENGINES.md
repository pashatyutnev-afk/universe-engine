# ENG FAMILY README — DOMAIN_CHARACTER_ENGINES (TEMPLATE v2)
FILE: 00__TEMPLATE__README__DOMAIN_CHARACTER_ENGINES.md

SCOPE: Universe Engine
LAYER: ENG
DOC_TYPE: TEMPLATE
ENTITY_GROUP: ENGINES (ENG)
TEMPLATE_KIND: FAMILY_README_OVERLAY
LEVEL: L2
STATUS: ACTIVE
VERSION: 2.0
ROLE: Family overlay for Character (Domain) realm README. Compatible with base family template v2 and base engine template v2. Defines character canon boundaries, relationship/dialogue interfaces, and required xref graphs.

LOCK: FIXED
OWNER: Universe Engine

---

## 0) PURPOSE (REALM LAW)

Семейство **DOMAIN_CHARACTER_ENGINES** отвечает за персонажей как системные сущности:
- ядро персонажа (identity/core)
- мотивация/желания
- мораль/ценности
- психология
- поведение (поведенческие паттерны)
- отношения (relationship graph)
- диалоги (смысл/интенции)
- натурализация речи (язык/интонация/лексика)
- рост/травмы (внутренние шрамы)
- эволюция персонажа (изменения во времени)

EXISTENCE RULE:
> Персонаж не считается “готовым” для канона, пока нет: core + мотивация + поведение + отношения.

---

## 1) FAMILY IDENTITY (MANDATORY)

FAMILY_NAME: DOMAIN_CHARACTER_ENGINES
FAMILY_CODE: CHR
FAMILY_CLASS: DOMAIN
FAMILY_LEVEL: L2

FAMILY_PATH:
`03_SYSTEM_ENTITIES/10_ENG__ENGINES/03_DOMAIN_CHARACTER_ENGINES/`

README_FILE:
`00__README__DOMAIN_CHARACTER_ENGINES.md`

---

## 2) OWNERSHIP BOUNDARIES (ANTI-DUPLICATION)

### 2.1 OWNS
- внутренняя модель персонажа (ядро/ценности/психика)
- мотивации и конфликт интересов (внутри персонажа)
- поведение как устойчивые паттерны
- отношения как граф (кто кому кто)
- речь персонажа как стиль общения (не общий tone мира)

### 2.2 DOES NOT OWN (hard boundaries)
- сюжетные события/сцены/дуги как единицы повествования → 02 Narrative
- стиль произведения (общий тон/атмосфера/символизм) → 06 Style
- законы мира/экономика/цивилизации → 04 World
- монтаж/тайминг/секунды/кадры → 08 Production
Rule:
> Character описывает “как персонаж устроен”, Narrative — “что с ним происходит”.

---

## 3) ROLE MAP (MANDATORY)

- FOUNDATION: core/motivation/value/psychology
- BUILDER: behavior/relationship/dialogue/speech
- VALIDATOR: growth/trauma/evolution consistency
- OUTPUT: character bible packs + relationship maps

### 3.1 Canonical role map table
| Engine NN | Engine Name | ROLE_IN_FAMILY | PIPELINE_STAGE |
|---|---|---|---|
| 01 | Character Core Engine | FOUNDATION | DEFINE |
| 02 | Motivation & Desire Engine | FOUNDATION | DEFINE |
| 03 | Moral & Value Engine | FOUNDATION | DEFINE |
| 04 | Character Psychology Engine | FOUNDATION | DEFINE |
| 05 | Character Behavior Engine | BUILDER | BUILD |
| 06 | Relationship Engine | BUILDER | BUILD |
| 07 | Dialogue Engine | BUILDER | BUILD |
| 08 | Speech Naturalization Engine | BUILDER | BUILD |
| 09 | Growth & Trauma Engine | VALIDATOR | CHECK |
| 10 | Character Evolution Engine | VALIDATOR | CHECK |

---

## 4) FAMILY OUTPUT POLICY (WORKSHOP L0–L3) — MANDATORY

Default root:
`05_PROJECTS/<PROJECT_ID>/01_WORKSHOP/`

Primary domain folder (canonical):
- `01_CHARACTERS/CHR_<NAME>/<LEVEL_FOLDER>/`

Secondary/related:
- `08_RELATIONSHIPS/REL_<NAME>/<LEVEL_FOLDER>/` (если отношения выделены отдельно)
- `05_PROJECT__L2/<LEVEL_FOLDER>/` (Character Bible на проект)

Rule:
> Character outputs по умолчанию entity-scoped (CHR_*). Project-scoped — только сборники/библии.

---

## 5) REQUIRED REGISTRIES (MANDATORY)

Project-scoped:
- `00_REG__REGISTRIES/REG.PRJ.<PROJECT_ID>.ENTITIES.md`
- `00_REG__REGISTRIES/REG.PRJ.<PROJECT_ID>.CANON_L2.md`
- `00_REG__REGISTRIES/REG.PRJ.<PROJECT_ID>.OUTPUT_L3.md` (if character packs are delivered)

---

## 6) REQUIRED XREF INDEXES (MANDATORY)

Project-scoped (core):
- `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__CANON_REFS.md`
- `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__DEPENDENCIES.md`
- `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__PROVENANCE.md`
- `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__ENTITY_GRAPH.md`

Character-specific (mandatory):
- `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__RELATIONSHIP_GRAPH.md`
- `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__DIALOGUE_CONSTRAINTS.md` (recommended)

Rule:
> Relationships must be represented as a graph (edges with types).

---

## 7) TEMPLATES (MANDATORY BLOCK)

Base templates:
- ENGINE TEMPLATE (base) — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00__TEMPLATE__ENGINE__ENG.md
- FAMILY README TEMPLATE (base) — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00__TEMPLATE__README__FAMILY__ENG.md

Family overlays:
- ENGINE TEMPLATE (family) — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/03_DOMAIN_CHARACTER_ENGINES/00__TEMPLATE__ENGINE__DOMAIN_CHARACTER_ENGINES.md
- README TEMPLATE (family) — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/03_DOMAIN_CHARACTER_ENGINES/00__TEMPLATE__README__DOMAIN_CHARACTER_ENGINES.md

---

## 8) CANON ORDER (MANDATORY)

00 — README (Realm)  
01 — Character Core Engine  
02 — Motivation & Desire Engine  
03 — Moral & Value Engine  
04 — Character Psychology Engine  
05 — Character Behavior Engine  
06 — Relationship Engine  
07 — Dialogue Engine  
08 — Speech Naturalization Engine  
09 — Growth & Trauma Engine  
10 — Character Evolution Engine  

---

## 9) GOVERNANCE COMPATIBILITY (MANDATORY)

Character canon impacts many layers.
Governance required when:
- character core or evolution changes break existing arcs/scenes
- relationship graph changes affect multiple entities
- any locked canon is modified

---

## 10) RAW LINK (MANDATORY)

RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/03_DOMAIN_CHARACTER_ENGINES/00__TEMPLATE__README__DOMAIN_CHARACTER_ENGINES.md

---

## FINAL RULE (LOCK)

> Character defines who the person is. Narrative defines what happens to them.

LOCK: FIXED
