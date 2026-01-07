# KB STORAGE MAP (GOVERNANCE)
FILE: 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/04__KB_STORAGE_MAP.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: MAP
MAP_TYPE: STORAGE
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.GOV.STORAGE_MAP.001
OWNER: SYSTEM
ROLE: Canonical storage map for KB: where realm docs, KB system docs, and KB entity passports live (prevents scattering and duplication)

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "KB storage map канонизирован: фиксированы корневые зоны, правила размещения, запрет на хаотичные папки"
- REASON: "Без карты хранения KB расползается по репо и ломает навигацию/реестры"
- IMPACT: "Организация KB, стандартизация путей, будущие паспорта/кейсы/шаблоны"

---

## 0) PURPOSE
Этот документ фиксирует **канонические пути хранения** для KB.

KB хранится в слое:
`04_KNOWLEDGE_BASE/`

---

## 1) ROOT ZONES (CANON)
### 1.1 Governance zone (rules, registries, templates)
PATH:
`04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/`

Здесь живут:
- README, RULES
- registry-indexes
- storage map
- templates
- create flow

Запрещено хранить здесь “контент-практику” (realm knowledge).

### 1.2 Realm zone (content knowledge)
PATH:
`04_KNOWLEDGE_BASE/`

Здесь живут только realm-файлы (контент):
- `01__NARRATIVE_CRAFT.md`
- `02__CHARACTER_CRAFT.md`
- `03__VISUAL_CINEMA.md`
- `04__SOUND_MUSIC.md`
- `05__PRODUCTION_PIPELINE.md`
- `06__MARKETING_DISTRIBUTION.md`
- `07__REFERENCE_GLOSSARY.md`
- `08__RESEARCH_FACT_CHECKING.md`

---

## 2) KB SYSTEM DOCS (HELPERS)
KB system helper docs (например теги) живут в корне KB, но в “высоком диапазоне номеров”:

- PATH RULE:
  `04_KNOWLEDGE_BASE/90__*.md`

Пример:
- `04_KNOWLEDGE_BASE/90__KB_TAGS.md`

Правило:
- системные файлы не должны коллизить по номерам с realm-файлами (01..08)

---

## 3) KB ENTITY PASSPORTS (OBJECTS)
KB сущности оформляются **паспортами**.

### 3.1 Storage rule (canonical)
Новая зона для паспортов (создаём, как начнём паспорта):

`04_KNOWLEDGE_BASE/10_ENTITIES/`

Внутри:
- `04_KNOWLEDGE_BASE/10_ENTITIES/<TYPE_CODE>/`
где `<TYPE_CODE>` — один из типов из `03__INDEX__KB_ENTITY_TYPES.md`

Пример структуры:
- `04_KNOWLEDGE_BASE/10_ENTITIES/KB_PRACTICE/`
- `04_KNOWLEDGE_BASE/10_ENTITIES/KB_PROCESS/`
- `04_KNOWLEDGE_BASE/10_ENTITIES/KB_CHECKLIST/`
- `04_KNOWLEDGE_BASE/10_ENTITIES/KB_CONCEPT/`
- `04_KNOWLEDGE_BASE/10_ENTITIES/KB_METHOD/`
- `04_KNOWLEDGE_BASE/10_ENTITIES/KB_ARTIFACT/`
- `04_KNOWLEDGE_BASE/10_ENTITIES/KB_CASE/`
- `04_KNOWLEDGE_BASE/10_ENTITIES/KB_SYSTEM_REF/`

### 3.2 Passport naming rule
Файл паспорта:
`NN__<NAME>.md`

Где `NN` — порядок внутри папки типа.

UID обязателен.

---

## 4) KB CASES (OPTIONAL ALTERNATIVE)
Если кейсы решим хранить отдельно (не как паспорта), допускается зона:

`04_KNOWLEDGE_BASE/20_CASES/`

Но базовое правило:
- лучше кейс = паспорт типа `KB_CASE`, чтобы всё было единообразно.

---

## 5) PROHIBITIONS (HARD)
Запрещено:
- создавать новые папки в корне KB без регистрации в KB master-index и без правок storage map
- хранить паспорта/кейсы “просто в корне”
- дублировать один и тот же смысл в разных зонах

---

## 6) DEPENDENCY NOTE
Storage map KB обязателен к согласованию с:
- стандартами naming/uid/doc control (02_STANDARDS/01_SPECIFICATIONS/*)
- system law (01_SYSTEM_LAW/*)

---

## FINAL RULE (LOCK)
Этот storage map — SoT по размещению KB артефактов.
LOCK: FIXED
--- END.
