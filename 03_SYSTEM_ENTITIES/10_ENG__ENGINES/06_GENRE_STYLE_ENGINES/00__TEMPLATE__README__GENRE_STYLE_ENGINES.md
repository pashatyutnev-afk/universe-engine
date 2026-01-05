# ENG FAMILY README — GENRE_STYLE_ENGINES (TEMPLATE v2)
FILE: 00__TEMPLATE__README__GENRE_STYLE_ENGINES.md

SCOPE: Universe Engine
LAYER: ENG
DOC_TYPE: TEMPLATE
ENTITY_GROUP: ENGINES (ENG)
TEMPLATE_KIND: FAMILY_README_OVERLAY
LEVEL: L3
STATUS: ACTIVE
VERSION: 2.0
ROLE: Family overlay for Genre/Style realm README. Compatible with base family template v2 and base engine template v2. Defines project-level style law packs, symbolic rules, and sensory constraints consumed by Narrative/Character/Production.

LOCK: FIXED
OWNER: Universe Engine

---

## 0) PURPOSE (REALM LAW)

Семейство **GENRE_STYLE_ENGINES** отвечает за “как это чувствуется”:
- тон и настроение
- атмосфера
- эмоциональный резонанс
- символизм
- метафоры
- сенсорная детализация (запах/звук/тактильность/температура)

EXISTENCE RULE:
> Проектный стиль считается заданным, когда есть: tone+atmosphere + symbol rules + sensory palette.

---

## 1) FAMILY IDENTITY (MANDATORY)

FAMILY_NAME: GENRE_STYLE_ENGINES
FAMILY_CODE: STY
FAMILY_CLASS: STYLE
FAMILY_LEVEL: L3

FAMILY_PATH:
`03_SYSTEM_ENTITIES/10_ENG__ENGINES/06_GENRE_STYLE_ENGINES/`

README_FILE:
`00__README__GENRE_STYLE_ENGINES.md`

---

## 2) OWNERSHIP BOUNDARIES (ANTI-DUPLICATION)

### 2.1 OWNS
- project-level style laws (tone/atmosphere/symbols/sensory palette)
- constraints packs used by other families

### 2.2 DOES NOT OWN (hard boundaries)
- персонажный “голос”/лексика/паразиты/манера речи → 03 Character
- сюжетная структура/арки/сцены → 02 Narrative
- факты мира/законы/эпохи → 04 World
- монтаж/тайминг, цветокор как техпроцесс, кадры/планы → 08 Production (но Style задаёт intent, Production реализует)
Rule:
> Style = intent law. Production = implementation.

---

## 3) ROLE MAP (MANDATORY)

- FOUNDATION: tone/mood + atmosphere
- BUILDER: resonance/symbolism/metaphor/sensory
- OUTPUT: style pack bundles + anti-style rules

### 3.1 Canonical role map table
| Engine NN | Engine Name | ROLE_IN_FAMILY | PIPELINE_STAGE |
|---|---|---|---|
| 01 | Tone & Mood Engine | FOUNDATION | DEFINE |
| 02 | Atmosphere Engine | FOUNDATION | DEFINE |
| 03 | Emotional Resonance Engine | BUILDER | BUILD |
| 04 | Symbolism Engine | BUILDER | BUILD |
| 05 | Metaphor Engine | BUILDER | BUILD |
| 06 | Sensory Detail Engine | BUILDER | BUILD |

---

## 4) FAMILY OUTPUT POLICY (WORKSHOP L0–L3) — MANDATORY

Default root:
`05_PROJECTS/<PROJECT_ID>/01_WORKSHOP/`

Recommended storage:
- project style packs:
  `05_PROJECT__L2/<LEVEL_FOLDER>/STYLE_PACKS/`
- optional entity-level style overlays (rare):
  `01_CHARACTERS/<CHR_*>/<LEVEL_FOLDER>/STYLE_OVERLAY/`
  `06_EVENTS/<EVT_*>/<LEVEL_FOLDER>/STYLE_OVERLAY/`

Rule:
> Style is project-scoped by default. Entity overlays are exceptions and must be referenced.

---

## 5) REQUIRED REGISTRIES (MANDATORY)

Project-scoped:
- `00_REG__REGISTRIES/REG.PRJ.<PROJECT_ID>.CANON_L2.md` (style packs as canon)
- `00_REG__REGISTRIES/REG.PRJ.<PROJECT_ID>.OUTPUT_L3.md` (if style kit delivered)

---

## 6) REQUIRED XREF INDEXES (MANDATORY)

Project-scoped:
- `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__CANON_REFS.md`
- `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__PROVENANCE.md`
- `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__DEPENDENCIES.md`

Style-specific (recommended):
- `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__STYLE_RULES.md`
- `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__SYMBOL_MAP.md`

---

## 7) TEMPLATES (MANDATORY BLOCK)

Base templates:
- ENGINE TEMPLATE (base) — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00__TEMPLATE__ENGINE__ENG.md
- FAMILY README TEMPLATE (base) — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00__TEMPLATE__README__FAMILY__ENG.md

Family overlays:
- ENGINE TEMPLATE (family) — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/06_GENRE_STYLE_ENGINES/00__TEMPLATE__ENGINE__GENRE_STYLE_ENGINES.md
- README TEMPLATE (family) — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/06_GENRE_STYLE_ENGINES/00__TEMPLATE__README__GENRE_STYLE_ENGINES.md

---

## 8) CANON ORDER (MANDATORY)

00 — README (Realm)  
01 — Tone & Mood Engine  
02 — Atmosphere Engine  
03 — Emotional Resonance Engine  
04 — Symbolism Engine  
05 — Metaphor Engine  
06 — Sensory Detail Engine  

---

## 9) GOVERNANCE COMPATIBILITY (MANDATORY)

Governance required when:
- changing project style law pack (tone shift)
- changing symbol meaning that is referenced across arcs/scenes
- rewriting sensory palette that production already implemented

---

## 10) RAW LINK (MANDATORY)

RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/06_GENRE_STYLE_ENGINES/00__TEMPLATE__README__GENRE_STYLE_ENGINES.md

---

## FINAL RULE (LOCK)

> Style defines “how it feels”. Characters speak (CHR), narrative happens (NAR), production executes (PRD).

LOCK: FIXED
