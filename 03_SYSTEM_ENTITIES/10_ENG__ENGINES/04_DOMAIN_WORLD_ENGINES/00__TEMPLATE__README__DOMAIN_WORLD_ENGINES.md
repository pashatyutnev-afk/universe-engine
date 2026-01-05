# ENG FAMILY README — DOMAIN_WORLD_ENGINES (TEMPLATE v2)
FILE: 00__TEMPLATE__README__DOMAIN_WORLD_ENGINES.md

SCOPE: Universe Engine
LAYER: ENG
DOC_TYPE: TEMPLATE
ENTITY_GROUP: ENGINES (ENG)
TEMPLATE_KIND: FAMILY_README_OVERLAY
LEVEL: L2
STATUS: ACTIVE
VERSION: 2.0
ROLE: Family overlay for World (Domain) realm README. Compatible with base family template v2 and base engine template v2. Defines world-law canon boundaries, civilization/economy/tech/ecology constraints, and required world xref indexes.

LOCK: FIXED
OWNER: Universe Engine

---

## 0) PURPOSE (REALM LAW)

Семейство **DOMAIN_WORLD_ENGINES** отвечает за мир как систему:
- структура мира (география/слои/среда)
- законы мира (физика/метафизика/магия)
- таймлайн и эпохи
- цивилизации
- конфликт и власть
- геополитика
- экономика и ресурсы
- технологии и магия
- мифология и вера
- экология и среда

EXISTENCE RULE:
> Любой канон мира (L2) должен иметь: laws + epochs + civilization + resources + ecology связки.

---

## 1) FAMILY IDENTITY (MANDATORY)

FAMILY_NAME: DOMAIN_WORLD_ENGINES
FAMILY_CODE: WLD
FAMILY_CLASS: DOMAIN
FAMILY_LEVEL: L2

FAMILY_PATH:
`03_SYSTEM_ENTITIES/10_ENG__ENGINES/04_DOMAIN_WORLD_ENGINES/`

README_FILE:
`00__README__DOMAIN_WORLD_ENGINES.md`

---

## 2) OWNERSHIP BOUNDARIES (ANTI-DUPLICATION)

### 2.1 OWNS
- world laws (что возможно/невозможно)
- таймлайн/эпохи как фактическая рамка мира
- цивилизации как системные структуры (уровни, принципы)
- экономика/ресурсы как механика обеспечения
- технологии/магия как capabilities мира
- экология как устойчивость среды
- мифология/вера как мировоззренческая система мира

### 2.2 DOES NOT OWN (hard boundaries)
- сюжетные сцены/повороты/дуги → 02 Narrative
- внутренний психопортрет персонажа → 03 Character
- глобальный художественный тон/метафоры произведения → 06 Style (но world может иметь “культуру/эстетику” как факт)
- монтаж/тайминг/план съёмки → 08 Production
- музыка как произведение → 09 Music
Rule:
> World определяет факты и законы. Narrative/Production используют их как ограничения.

---

## 3) WORLD-LAW CONSTRAINTS (MANDATORY)

### 3.1 Currency constraint (project canon law)
Великие цивилизации **не используют валюту**.
- Разрешены механизмы: распределение, доступ, репутация, квоты, энергопакеты, дар/обмен, контракт доступа, логистика ресурсов.
- Если появляется “валюта” — это маркер:
  - либо низкоуровневая/переходная цивилизация
  - либо локальный суррогат
  - либо ошибка канона (фикс через governance)

Rule:
> Любая экономическая модель должна явно указывать: есть ли валюта и почему.

---

## 4) ROLE MAP (MANDATORY)

- FOUNDATION: world structure + world law + epochs
- BUILDER: civilization/conflict/geopolitics/economy/tech/ecology
- VALIDATOR: mythology/belief coherence + eco consistency
- OUTPUT: world bible packs / epoch packs / civ packs

### 4.1 Canonical role map table
| Engine NN | Engine Name | ROLE_IN_FAMILY | PIPELINE_STAGE |
|---|---|---|---|
| 01 | World Structure Engine | FOUNDATION | DEFINE |
| 02 | World Law Engine | FOUNDATION | DEFINE |
| 03 | Timeline & Epoch Engine | FOUNDATION | DEFINE |
| 04 | Civilization Engine | BUILDER | BUILD |
| 05 | Conflict & Power Engine | BUILDER | BUILD |
| 06 | Geopolitics Engine | BUILDER | BUILD |
| 07 | Economy & Resource Engine | BUILDER | BUILD |
| 08 | Technology & Magic Engine | BUILDER | BUILD |
| 09 | Mythology & Belief Engine | VALIDATOR | CHECK |
| 10 | Environment & Ecology Engine | VALIDATOR | CHECK |

---

## 5) FAMILY OUTPUT POLICY (WORKSHOP L0–L3) — MANDATORY

Default root:
`05_PROJECTS/<PROJECT_ID>/01_WORKSHOP/`

Recommended domain folders:
- `04_SYSTEMS/SYS_<NAME>/<LEVEL_FOLDER>/` (world systems / laws packages)
- `02_LOCATIONS/LOC_<NAME>/<LEVEL_FOLDER>/` (geo/world layers)
- `05_FACTIONS/FAC_<NAME>/<LEVEL_FOLDER>/` (civilizations/factions)
- `07_CONCEPTS/CPT_<NAME>/<LEVEL_FOLDER>/` (laws, tech tiers)
- `05_PROJECT__L2/<LEVEL_FOLDER>/` (World Bible)

Rule:
> World canon is entity-scoped (SYS/LOC/FAC/CPT) + project-scoped bible bundles.

---

## 6) REQUIRED REGISTRIES (MANDATORY)

Project-scoped:
- `00_REG__REGISTRIES/REG.PRJ.<PROJECT_ID>.ENTITIES.md`
- `00_REG__REGISTRIES/REG.PRJ.<PROJECT_ID>.CANON_L2.md`
- `00_REG__REGISTRIES/REG.PRJ.<PROJECT_ID>.OUTPUT_L3.md` (if world packs delivered)

---

## 7) REQUIRED XREF INDEXES (MANDATORY)

Project-scoped (core):
- `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__CANON_REFS.md`
- `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__DEPENDENCIES.md`
- `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__PROVENANCE.md`
- `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__ENTITY_GRAPH.md`

World-specific (mandatory):
- `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__WORLD_LAW_GRAPH.md`
- `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__EPOCH_GRAPH.md` (recommended)
- `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__RESOURCE_FLOW_GRAPH.md` (recommended)
- `90_XREF__CROSSREF/PRJ_<PROJECT_ID>/XREF__POWER_GRAPH.md` (recommended)

---

## 8) TEMPLATES (MANDATORY BLOCK)

Base templates:
- ENGINE TEMPLATE (base) — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00__TEMPLATE__ENGINE__ENG.md
- FAMILY README TEMPLATE (base) — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/00__TEMPLATE__README__FAMILY__ENG.md

Family overlays:
- ENGINE TEMPLATE (family) — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/04_DOMAIN_WORLD_ENGINES/00__TEMPLATE__ENGINE__DOMAIN_WORLD_ENGINES.md
- README TEMPLATE (family) — 🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/04_DOMAIN_WORLD_ENGINES/00__TEMPLATE__README__DOMAIN_WORLD_ENGINES.md

---

## 9) CANON ORDER (MANDATORY)

00 — README (Realm)  
01 — World Structure Engine  
02 — World Law Engine  
03 — Timeline & Epoch Engine  
04 — Civilization Engine  
05 — Conflict & Power Engine  
06 — Geopolitics Engine  
07 — Economy & Resource Engine  
08 — Technology & Magic Engine  
09 — Mythology & Belief Engine  
10 — Environment & Ecology Engine  

---

## 10) GOVERNANCE COMPATIBILITY (MANDATORY)

Governance required when:
- world laws are modified (breaking constraints)
- epoch/timeline refactors affect many entities
- economy model violates currency constraint (unless justified as low-tier/local)

---

## 11) RAW LINK (MANDATORY)

RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/04_DOMAIN_WORLD_ENGINES/00__TEMPLATE__README__DOMAIN_WORLD_ENGINES.md

---

## FINAL RULE (LOCK)

> World defines facts and laws; everything else must obey them.

LOCK: FIXED
