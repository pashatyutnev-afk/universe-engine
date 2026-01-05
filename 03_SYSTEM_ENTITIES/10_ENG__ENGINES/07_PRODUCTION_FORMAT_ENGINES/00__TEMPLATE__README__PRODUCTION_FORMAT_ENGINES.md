# ENG FAMILY README — PRODUCTION_FORMAT_ENGINES (TEMPLATE v2)
FILE: 00__TEMPLATE__README__PRODUCTION_FORMAT_ENGINES.md

SCOPE: Universe Engine
LAYER: ENG
DOC_TYPE: TEMPLATE
ENTITY_GROUP: ENGINES (ENG)
TEMPLATE_KIND: FAMILY_README_OVERLAY
LEVEL: L3
STATUS: ACTIVE
VERSION: 2.0
ROLE: Family overlay for Production Format realm README. Compatible with base family template v2 and base engine template v2. Defines format laws, deliverable specs, and routing to L3 outputs.

LOCK: FIXED
OWNER: Universe Engine

---

## 0) PURPOSE (REALM LAW)

Семейство **PRODUCTION_FORMAT_ENGINES** отвечает за форму выпуска:
- жанр как упаковка ожиданий аудитории
- смешение жанров
- адаптация формата под носитель
- формат книги
- формат сериала/эпизодов
- формат короткого контента
- формат YouTube longform
- формат игры (нарратив)

EXISTENCE RULE:
> Пока формат не выбран и не зафиксирован — production не имеет валидного target deliverable.

---

## 1) FAMILY IDENTITY (MANDATORY)

FAMILY_NAME: PRODUCTION_FORMAT_ENGINES
FAMILY_CODE: FMT
FAMILY_CLASS: PRODUCTION
FAMILY_LEVEL: L3

FAMILY_PATH:
`03_SYSTEM_ENTITIES/10_ENG__ENGINES/07_PRODUCTION_FORMAT_ENGINES/`

README_FILE:
`00__README__PRODUCTION_FORMAT_ENGINES.md`

---

## 2) OWNERSHIP BOUNDARIES (ANTI-DUPLICATION)

### 2.1 OWNS
- форматные ограничения (длина, эпизодность, структура deliverables)
- требования к “пакету выпуска” (что должно быть на выходе)
- mapping format → production pipeline targets

### 2.2 DOES NOT OWN (hard boundaries)
- сюжетная логика/арки/сцены → 02 Narrative
- стиль/атмосфера → 06 Style
- монтаж/кадры/съёмка/звук как процесс → 08 Production
Rule:
> Format задаёт требования к deliverables; Production реализует.

---

## 3) ROLE MAP (MANDATORY)

- FOUNDATION: genre + blending + adaptation
- OUTPUT: book/series/short/youtube/game specs

### 3.1 Canonical role map table
| Engine NN | Engine Name | ROLE_IN_FAMILY | PIPELINE_STAGE |
|---|---|---|---|
| 01 | Genre Engine | FOUNDATION | DEFINE |
| 02 | Genre Blending Engine | FOUNDATION | DEFINE |
| 03 | Format Adaptation Engine | FOUNDATION | DEFINE |
| 04 | Book Format Engine | OUTPUT | PRODUCE |
| 05 | Series & Episode Engine | OUTPUT | PRODUCE |
| 06 | Short Content Engine | OUTPUT | PRODUCE |
| 07 | YouTube Longform Engine | OUTPUT | PRODUCE |
| 08 | Game Narrative Engine | OUTPUT | PRODUCE |

---

## 4) FAMILY OUTPUT POLICY (WORKSHOP L0–L3) — MANDATORY

Default root:
`05_PROJECTS/<PROJECT_ID>/01_WORKSHOP/`

Format-spec storage (project-scoped):
- `05_PROJECT__L2/<LEVEL_FOLDER>/FORMAT_SPECS/`

Deliverables routing (L3 outputs):
- `05_PROJECTS/<PROJECT_ID>/02_OUTPUT/<FORMAT>/...`
or if staying inside Workshop:
- `05_PROJECTS/<PROJECT_ID>/01_WORKSHOP/05_PROJECT__L3/04_OUTPUT_L3/<FORMAT>/...`

Rule:
> Format specs live in L2. Actual release artifacts live in L3 Output.

---

## 5) REQUIRED REGISTRIES (MANDATORY)

Project-scoped:
- `00_REG__REGISTRIES/REG.PRJ.<PROJECT_ID>.CANON_L2.md` (format spec as canon)
- `00_REG__REGISTRIES/REG.PRJ.<PROJECT_ID>.OUTPUT_L3.md` (deliverables)

---

## 6) REQUIRED XREF INDEXES (MANDATORY)

Project-scoped:
- `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__CANON_REFS.md`
- `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__DEPENDENCIES.md`
- `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__PROVENANCE.md`

Format-specific (recommended):
- `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__DELIVERABLE_MAP.md`

---

## 7) TEMPLATES (MANDATORY BLOCK)

Base templates:
- ENGINE TEMPLATE (base) — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00__TEMPLATE__ENGINE__ENG.md
- FAMILY README TEMPLATE (base) — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00__TEMPLATE__README__FAMILY__ENG.md

Family overlays:
- ENGINE TEMPLATE (family) — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/07_PRODUCTION_FORMAT_ENGINES/00__TEMPLATE__ENGINE__PRODUCTION_FORMAT_ENGINES.md
- README TEMPLATE (family) — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/07_PRODUCTION_FORMAT_ENGINES/00__TEMPLATE__README__PRODUCTION_FORMAT_ENGINES.md

---

## 8) CANON ORDER (MANDATORY)

00 — README (Realm)  
01 — Genre Engine  
02 — Genre Blending Engine  
03 — Format Adaptation Engine  
04 — Book Format Engine  
05 — Series & Episode Engine  
06 — Short Content Engine  
07 — YouTube Longform Engine  
08 — Game Narrative Engine  

---

## 9) GOVERNANCE COMPATIBILITY (MANDATORY)

Governance required when:
- changing format spec after L3 production started
- changing episode length rules that impact editing pipeline
- switching primary format mid-project

---

## 10) RAW LINK (MANDATORY)

RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/07_PRODUCTION_FORMAT_ENGINES/00__TEMPLATE__README__PRODUCTION_FORMAT_ENGINES.md

---

## FINAL RULE (LOCK)

> Format defines deliverables and constraints. It does not create story content and does not edit media.

LOCK: FIXED
