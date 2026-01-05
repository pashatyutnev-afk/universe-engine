# ENG FAMILY README TEMPLATE — UNIVERSAL
FILE: 00__TEMPLATE__README__FAMILY__ENG.md

SCOPE: Universe Engine
LAYER: ENG
DOC_TYPE: TEMPLATE
ENTITY_KIND: GENERIC
PROJECT_SCOPE: GLOBAL
OUTPUT_LEVEL: N/A
ID: ENG.TEMPLATE.FAMILY_README
STATUS: ACTIVE
VERSION: 2.0
ROLE: Universal template for ENG family realm README. Defines boundaries, role map, required registries/xrefs, default output policies, and canon order for engines in the family.

---

## 0) PURPOSE (REALM LAW)

Этот README — **конституция семейства**.
Он фиксирует:
- границы (OWN / DOES NOT OWN)
- роли движков внутри семейства (FOUNDATION / BUILDER / VALIDATOR / BRIDGE / OUTPUT)
- обязательные интерфейсы (input/output артефакты)
- правила вывода в WORKSHOP L0–L3
- обязательные обновления REG и XREF
- канонический порядок движков

### EXISTENCE RULE (FAMILY)
> Движок, не внесённый в семейный CANON ORDER + общий ENG INDEX — считается **non-canon**.

---

## 1) FAMILY IDENTITY (MANDATORY)

FAMILY_NAME: <e.g., DOMAIN_NARRATIVE_ENGINES>
FAMILY_CODE: <e.g., NARR>
FAMILY_CLASS: <GOVERNANCE|CORE|DOMAIN|EXPRESSION|STYLE|PRODUCTION|SOUND|META>
FAMILY_LEVEL: <L1|L2|L3|L4>

FAMILY_PATH: `10_ENG__ENGINES/<FAMILY_FOLDER>/`
README_FILE: `00__README__<FAMILY>_ENGINES.md`

---

## 2) OWNERSHIP BOUNDARIES (ANTI-DUPLICATION)

### 2.1 OWNS (this family owns)
- <list what this family is responsible for>
- <what artifacts are produced here>
- <what decisions belong here>

### 2.2 DOES NOT OWN (belongs elsewhere)
- <explicit exclusions + pointer links to other families/layers>
Examples:
- Narrative rhythm vs Editing rhythm
- Production sound vs Deep music

Rule:
> If something belongs to DOES NOT OWN, it MUST be redirected, not duplicated.

---

## 3) ROLE MAP (MANDATORY)

Каждый движок семьи обязан иметь роль:

- FOUNDATION — определяет базовые правила/модель/язык
- BUILDER — строит артефакты на основе foundation
- VALIDATOR — проверяет и ловит противоречия
- BRIDGE — переводит в следующий слой/формат/пайплайн
- OUTPUT — собирает итоговый пакет артефактов семейства

### 3.1 Family role completeness rule
> В каждой семье должен существовать минимум:
> - 1 FOUNDATION
> - 1 OUTPUT
> - 1 VALIDATOR (если семья производит L2_CANON)
> При отсутствии — семья считается incomplete.

### 3.2 Role map table (fill)
| Engine NN | Engine Name | ROLE_IN_FAMILY | PIPELINE_STAGE |
|---|---|---|---|
| 01 | <...> | FOUNDATION | DEFINE |
| 02 | <...> | BUILDER | BUILD |
| 03 | <...> | VALIDATOR | CHECK |
| 04 | <...> | BRIDGE | PACKAGE |
| 05 | <...> | OUTPUT | PRODUCE |

PIPELINE_STAGE standard:
- DEFINE / BUILD / CHECK / PACKAGE / PRODUCE

---

## 4) FAMILY OUTPUT POLICY (WORKSHOP L0–L3) — MANDATORY

DEFAULT_ENTITY_KIND: <CHR|LOC|...|GENERIC>
DEFAULT_OUTPUT_LEVEL: <L0_INTAKE|L1_DRAFT|L2_CANON|L3_OUTPUT>
DEFAULT_PROJECT_OUTPUT_ROOT:
- `05_PROJECTS/<PROJECT_ID>/01_WORKSHOP/`

DEFAULT_CATEGORY_PATH (choose one or more):
- `01_CHARACTERS/`
- `02_LOCATIONS/`
- `03_OBJECTS/`
- `04_SYSTEMS/`
- `05_FACTIONS/`
- `06_EVENTS/`
- `07_CONCEPTS/`
- `08_RELATIONSHIPS/`
- `09_ARCS/`
- `10_STYLES/`
- `11_EXPERIMENTS/`
- `05_PROJECT__L3/` (media outputs)

### 4.1 Level routing rules (strict)
- L0_INTAKE: raw notes, fragments, references
- L1_DRAFT: structured drafts, not approved
- L2_CANON: only after validator + QA + REG/XREF updates
- L3_OUTPUT: must reference L2_CANON via XREF (CANON_REF)

---

## 5) REQUIRED REGISTRIES (MANDATORY)

This family MUST declare which registries it updates.

REQUIRED_REGISTRIES:
- Entities: <REG ids/paths>
- Artifacts (L2/L3): <REG ids/paths>
- Engines (optional): <REG ids/paths>

Rule:
> If a family produces L2_CANON or L3_OUTPUT, registries are mandatory.

---

## 6) REQUIRED XREF INDEXES (MANDATORY)

This family MUST declare xref indexes it writes to.

REQUIRED_XREF:
- Dependency graph: <xref index path/id>
- Canon refs: <xref index path/id>
- Entity graph (if relevant): <xref index path/id>
- Change/replacement (if relevant): <xref index path/id>

Rule:
> Any DEPENDS_ON in engines must be mirrored in XREF dependency index.

---

## 7) INTERFACES (INPUT / OUTPUT ARTIFACT TYPES)

Define the standard artifact “language” for this family.

### 7.1 INPUT ARTIFACT TYPES
- <type 1>
- <type 2>

### 7.2 OUTPUT ARTIFACT TYPES
- <type 1>
- <type 2>

### 7.3 OUTPUT_ARTIFACT_TYPE STANDARD
Engines in this family must label their main output:
- CANON_SPEC / CANON_MODEL / CANON_CARD / STYLE_BIBLE / FORMAT_SPEC / SHOTLIST / EDIT_PLAN / MUSIC_STEMS / ...

---

## 8) TEMPLATES (MANDATORY BLOCK)

Every family must expose template links.

- ENGINE TEMPLATE — 🔗 <raw link or canonical path to engine template used>
- README TEMPLATE — 🔗 <raw link or canonical path to this readme template>

Optional overlays:
- OVERLAY TEMPLATE(S) — 🔗 <links>

---

## 9) CANON ORDER (MANDATORY)

List engines in strict order. README (00) is not an engine.

00 — README (Realm) — 🔗 <raw link>
01 — <Engine name> — 🔗 <raw link>
02 — <Engine name> — 🔗 <raw link>
...

Rule:
> Engine NN in filename MUST match NN in this order list.

---

## 10) GOVERNANCE COMPATIBILITY (MANDATORY)

Any change to:
- this README
- engine order
- required registries/xrefs
- output policy
must go through governance pipeline:
- `ENG.GOV.04.CHANGE_CONTROL`
- `ENG.GOV.01.AUDIT_LOG`
- `ENG.GOV.10.VERSIONING_MEMORY`

---

## FINAL RULE (LOCK)

> Этот README является законом конкретного семейства.  
> Несоответствие движков этому README = non-canon.

OWNER: Universe Engine  
LOCK: FIXED
