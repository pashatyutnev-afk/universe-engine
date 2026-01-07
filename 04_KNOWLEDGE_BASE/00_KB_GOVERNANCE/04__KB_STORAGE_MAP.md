# KB STORAGE MAP (CANON)
FILE: 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/04__KB_STORAGE_MAP.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: SPEC
SPEC_TYPE: SoT
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.KB.GOV.STORAGE_MAP.014
OWNER: SYSTEM
ROLE: Source-of-Truth storage map for the KB layer: defines canonical placement for governance, realms, entity passports, registries, and KB system files. Resolves numbering collisions.

CHANGE_NOTE:
- DATE: 2026-01-07
- TYPE: MAJOR
- SUMMARY: "KB storage map нормализован: разнесены governance/realms/passports/system, введён неймспейс 90+ для KB system files, решена коллизия 02__KB_TAGS"
- REASON: "Убрать двусмысленность навигации и обеспечить масштабирование KB"
- IMPACT: "Paths and naming for KB files; migration required"

---

## XREF (UID-first)
XREF: UE.KB.IDX.MASTER.001 | depends_on | KB existence by master-index | 04_KNOWLEDGE_BASE/00__INDEX__KNOWLEDGE_BASE.md
XREF: UE.KB.GOV.RULES.011 | governs | KB governance rules | 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/01__RULES__KB.md
XREF: UE.STD.SPEC.STORAGE_MAP.102 | references | global storage principles | 02_STANDARDS/01_SPECIFICATIONS/02__STORAGE_MAP_STANDARD.md
XREF: UE.STD.MOD.MARKING.STORAGE_MAP.602 | references | alias pointers policy | 02_STANDARDS/06_MARKING_STANDARDS/02__STORAGE_MAP.md

---

## 0) PURPOSE (LAW)
Эта карта — единая точка истины о том, **где что живёт** внутри слоя KB.

Она определяет:
- канонические папки/файлы
- entrypoints
- размещение паспортов сущностей
- размещение системных справочников (tags/types/registries)
- правила неймспейса номеров

---

## 1) PRIME RULES (ABSOLUTE)
### 1.1 Single entrypoint for KB layer
Единственный entrypoint:
- `04_KNOWLEDGE_BASE/00__INDEX__KNOWLEDGE_BASE.md`

### 1.2 Governance vs Content separation
- Governance = правила/карты/реестры/шаблоны
- Realms = контент-методики/знания
- Passports = сущности (отдельные документы)
Нельзя смешивать эти уровни в одной зоне без причины.

### 1.3 Number namespace rule (CRITICAL)
- `01–08` — закреплены за realm-файлами (root-level realms)
- `00_KB_GOVERNANCE/*` — governance-нумерация (00–99 внутри папки)
- `90–99` в governance — reserved для **KB system references** (tags, controlled lists, shared dictionaries)
- Запрещено создавать root-level файл `NN__*` который коллизит с realm `NN_*`.

---

## 2) CANON PLACEMENT (WHERE THINGS LIVE)

### 2.1 Governance
PATH:
- `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/`

Там живут:
- README/Rules
- registries (global registry, entity types)
- storage map
- templates
- create flow
- KB system references (90+)

### 2.2 Realms (root-level)
PATH:
- `04_KNOWLEDGE_BASE/01_NARRATIVE_CRAFT.md`
- `04_KNOWLEDGE_BASE/02_CHARACTER_CRAFT.md`
- ...
- `04_KNOWLEDGE_BASE/08_RESEARCH_FACT_CHECKING.md`

Реалмы:
- содержат знания/методики/правила домена
- не являются паспортами сущностей
- должны ссылаться на сущности UID-first

### 2.3 Entity Passports (new canonical folder)
Чтобы сущности не смешивались с realm-файлами, вводится каноническая папка:

PATH:
- `04_KNOWLEDGE_BASE/10_ENTITIES/`

Рекомендуемая структура внутри:
- `04_KNOWLEDGE_BASE/10_ENTITIES/CHARACTER/`
- `04_KNOWLEDGE_BASE/10_ENTITIES/LOCATION/`
- `04_KNOWLEDGE_BASE/10_ENTITIES/FACTION/`
- (и т.д. по Entity Types)

Каждая сущность:
- отдельный файл-паспорт
- имя файла: `<ENTITY_UID>__<slug>.md` (рекомендуется)
- внутри: паспорт по KB шаблону

### 2.4 Registries
Основные реестры живут в governance:
- `00_KB_GOVERNANCE/02__INDEX__KB_GLOBAL_REGISTRY.md`
- `00_KB_GOVERNANCE/03__INDEX__KB_ENTITY_TYPES.md`

### 2.5 KB System References (tags/dicts)
Все общие справочники KB (теги, словари, common lists) должны жить здесь:
- `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/90__*.md`

---

## 3) S0 MIGRATION: FIX NUMBER COLLISION (02__KB_TAGS)
### 3.1 Problem
`04_KNOWLEDGE_BASE/02__KB_TAGS.md` коллизит по номеру с `04_KNOWLEDGE_BASE/02_CHARACTER_CRAFT.md`.

### 3.2 Canon solution (MANDATORY)
- Новый канонический путь:
  - `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/90__KB_TAGS.md`
- Старый файл `04_KNOWLEDGE_BASE/02__KB_TAGS.md` превращается в legacy alias pointer (non-canon content) и **не регистрируется** в master-index как канон.

---

## 4) LEGACY / ALIAS POLICY
Если есть legacy файлы типа:
- `00_INDEX_KNOWLEDGE_BASE.md`
- `01__KB_INDEX.md`
то они:
- не являются каноном
- становятся alias pointers на `00__INDEX__KNOWLEDGE_BASE.md`

---

## 5) ADDING NEW KB ARTIFACTS (RULE)
- Новые governance документы → в `00_KB_GOVERNANCE/` и добавляются в master-index
- Новые сущности → в `10_ENTITIES/<TYPE>/` + паспорт + запись в Global Registry
- Новые realm-знания → внутрь соответствующего realm-файла

---

## FINAL RULE (LOCK)
Эта карта хранения — SoT размещения KB.
Любая правка путей/неймспейсов = изменение канона и проходит Canon Protocol.
--- END.
