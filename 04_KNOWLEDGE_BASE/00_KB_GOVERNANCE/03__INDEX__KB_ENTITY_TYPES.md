# KB ENTITY TYPES — INDEX (CANON)
FILE: 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/03__INDEX__KB_ENTITY_TYPES.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: REGISTRY
REGISTRY_TYPE: KB_ENTITY_TYPES
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.1.0
UID: UE.KB.GOV.ENTITY_TYPES.013
OWNER: SYSTEM
ROLE: Canonical controlled registry of KB entity types (enum). KB entities must declare ENTITY_TYPE from this list.

CHANGE_NOTE:
- DATE: 2026-01-07
- TYPE: MINOR
- SUMMARY: "Нормализован реестр типов сущностей KB: controlled enum, правила именования, обязательность для Global Registry и паспортов"
- REASON: "Чтобы типизация была единая и не плодились синонимы"
- IMPACT: "KB passports + KB Global Registry + realm references"

---

## XREF (UID-first)
XREF: UE.KB.GOV.RULES.011 | governs | entity typing is mandatory | 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/01__RULES__KB.md
XREF: UE.KB.GOV.REGISTRY.012 | depends_on | registry requires valid entity types | 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/02__INDEX__KB_GLOBAL_REGISTRY.md
XREF: UE.KB.TPL.ENTITY_PASSPORT.015 | depends_on | passport uses ENTITY_TYPE | 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/05__TEMPLATE__KB_ENTITY_PASSPORT.md

---

## 0) PURPOSE (LAW)
Этот реестр — единая точка истины по типам сущностей KB.

### TYPE EXISTENCE RULE (ABSOLUTE)
> Если типа нет в этом реестре — он **не существует** для KB.  
> Любой `ENTITY_TYPE` в паспорте/реестре обязан быть из этого списка.

---

## 1) NAMING RULES (TYPE KEYS)
Каждый тип имеет:
- TYPE_KEY: UPPER_SNAKE_CASE
- TYPE_NAME: человекочитаемое имя
- SCOPE_NOTE: что входит/не входит

Правила:
- TYPE_KEY уникален
- не использовать синонимы как отдельные типы (делай ALIAS внутри записи)
- если нужно дробить типы — сначала проверить, не решается ли это TAGS/ATTRIBUTES

---

## 2) CONTROLLED ENTITY TYPES (CANON LIST)
> Это базовый набор. Расширения допускаются только через правку этого реестра (canon change).

| TYPE_KEY | TYPE_NAME | SCOPE_NOTE | ALIASES |
|---|---|---|---|
| CHARACTER | Character | Персонажи/акторы мира (люди/существа/индивиды) | PERSON, HERO |
| FACTION | Faction | Группы/организации/ордена/корпорации/армии | ORG, GROUP |
| LOCATION | Location | География: города, зоны, базы, планеты, точки | PLACE |
| EVENT | Event | События мира (исторические/сюжетные), не сцены | INCIDENT |
| SCENE | Scene | Сцена как единица повествования/постановки | SEQUENCE |
| OBJECT | Object | Уникальные предметы/артефакты мира (не ассеты продакшна) | ITEM, ARTIFACT |
| CONCEPT | Concept | Абстрактные понятия/законы/идеи внутри мира | IDEA |
| TECHNOLOGY | Technology | Технологии/системы/устройства мира | TECH |
| SPECIES | Species | Виды/расы/классы существ | RACE |
| CULTURE | Culture | Культурные пласты/традиции/этика | TRADITION |
| LANGUAGE | Language | Языки/диалекты/коды | DIALECT |
| TIMELINE | Timeline | Линии времени/эры/периоды/календарные системы | ERA |
| RELATIONSHIP | Relationship | Отношения между сущностями как отдельный объект (если нужно) | LINK |
| RULESET | Ruleset | Набор правил мира/физики/магии как сущность KB | SYSTEM_RULES |
| DOCUMENT_REF | Document Reference | Ссылочная сущность на внешний/внутренний документ (если нужно как объект) | REF |

---

## 3) WHEN TO CREATE A NEW TYPE (GATES)
Новый TYPE нужен только если:
- это новый класс сущностей, который нельзя выразить комбинацией существующего TYPE + TAGS/ATTRIBUTES
- тип будет использоваться минимум в нескольких сущностях
- тип не дублирует существующий смысл

Если сомневаешься:
- используй существующий TYPE
- добавь TAGS и ATTRIBUTES

---

## 4) TYPE EXTENSIONS VS TAGS
- TYPE = “что это по природе”
- TAG = “какое оно/к чему относится/в какой арке/в каком стиле”
- ATTRIBUTE = структурное свойство

Пример:
- TYPE: CHARACTER
- TAGS: ["Architects", "Season_1", "Antihero"]
- ATTRIBUTES: role="mentor"

---

## 5) CHANGE RULE (CANON)
Любое изменение списка типов:
- проходит governance/change policy
- требует SemVer bump:
  - PATCH: исправление описания/alias
  - MINOR: добавлен новый тип (без breaking)
  - MAJOR: переименование TYPE_KEY или удаление типа (breaking)

---

## FINAL RULE (LOCK)
Этот реестр — SoT для ENTITY_TYPE в KB.
Любые типы вне списка считаются невалидными.
--- END.
