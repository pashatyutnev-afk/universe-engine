# TEMPLATE — KB ENTITY PASSPORT (CANON)
FILE: 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/05__TEMPLATE__KB_ENTITY_PASSPORT.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: TEMPLATE
TEMPLATE_TYPE: KB_ENTITY_PASSPORT
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.1.0
UID: UE.KB.TPL.ENTITY_PASSPORT.015
OWNER: SYSTEM
ROLE: Canonical template for KB entity passports. Defines required entity identity fields, registry binding, and UID-first linkage patterns. Does not replace the base system passport template; it specializes it for KB.

CHANGE_NOTE:
- DATE: 2026-01-07
- TYPE: MINOR
- SUMMARY: "Шаблон KB Entity Passport: разделение DOC_UID vs ENTITY_UID, обязательные поля идентичности, registry-binding, XREF паттерны"
- REASON: "Чтобы сущности KB были строго управляемыми и ссылочными"
- IMPACT: "All KB entities"

---

## XREF (UID-first)
XREF: UE.KB.GOV.RULES.011 | depends_on | entity creation rules | 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/01__RULES__KB.md
XREF: UE.KB.GOV.REGISTRY.012 | depends_on | registry binding required | 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/02__INDEX__KB_GLOBAL_REGISTRY.md
XREF: UE.KB.GOV.ENTITY_TYPES.013 | depends_on | controlled entity typing | 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/03__INDEX__KB_ENTITY_TYPES.md
XREF: UE.STD.TPL.ENTITY_PASSPORT.300 | references | base entity passport template | 02_STANDARDS/03_TECHNICAL/ENTITY_PASSPORT_TEMPLATE.md
XREF: UE.STD.MOD.MARKING.ID.601 | references | UID vs local/human ids | 02_STANDARDS/06_MARKING_STANDARDS/01__ID_STANDARD.md
XREF: UE.STD.SPEC.REL_XREF.104 | depends_on | UID-first linking | 02_STANDARDS/01_SPECIFICATIONS/04__REL_POLICY_XREF_STANDARD.md

---

# KB ENTITY PASSPORT — COPY TEMPLATE (INSTANCE)
> Инструкция: копируй и заполняй.
> Паспорт = SoT о сущности. Realm-файлы не заменяют паспорт.

---

## DOC CONTROL (DOCUMENT HEADER)
FILE: <path-to-passport.md>

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: ARTIFACT
ARTIFACT_TYPE: KB_ENTITY_PASSPORT
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: <DOC_UID>
OWNER: <owner>
ROLE: KB Entity Passport for <ENTITY_NAME>

CHANGE_NOTE:
- DATE: YYYY-MM-DD
- TYPE: PATCH|MINOR|MAJOR
- SUMMARY: "Created/updated KB entity passport"
- REASON: "..."
- IMPACT: "..."

---

## 0) ENTITY IDENTITY (REQUIRED)
ENTITY_UID: <ENTITY_UID>            # immutable primary key for the entity
ENTITY_TYPE: <TYPE_KEY>             # must exist in KB Entity Types registry
ENTITY_NAME: <Name>                 # display name
ENTITY_STATUS: active               # active|draft|deprecated|retired|unknown
PRIMARY_REALM: <optional realm>     # e.g., CHARACTER, LOCATION, etc.

HUMAN_ID: <optional>                # readable alias, not a key
ALIASES: [<optional list>]          # alt names

ONE_LINE_SUMMARY: "<one sentence truth>"

---

## 1) REGISTRY BINDING (MANDATORY)
REGISTRY:
- REGISTRY_UID: UE.KB.GOV.REGISTRY.012
- REGISTRY_PATH: 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/02__INDEX__KB_GLOBAL_REGISTRY.md
- REGISTRY_RECORD: required
- RECORD_STATUS: expected

RULE:
- Эта сущность считается существующей только если есть строка в Global Registry с PASSPORT_PATH на этот файл.

---

## 2) CANON FACTS (SoT)
> Здесь — факты, которые считаются истинными про сущность.
> Пиши структурировано.

FACTS:
- <Fact 1>
- <Fact 2>

CONSTRAINTS:
- <Hard rule 1>
- <Hard rule 2>

UNKNOWN / OPEN QUESTIONS:
- <Unknown 1>
- <Unknown 2>

---

## 3) ATTRIBUTES (STRUCTURED)
> Структурные поля. Заполняй только нужное.

ATTRIBUTES:
- role: <optional>
- era: <optional>
- affiliation: <optional>
- traits: [<optional>]
- capabilities: [<optional>]
- resources: [<optional>]

---

## 4) RELATIONS (UID-FIRST)
> Все связи — через XREF.

XREF:
- XREF: <TARGET_ENTITY_UID> | relates_to | "<why>" | <passport-path(optional)>
- XREF: <TARGET_ENTITY_UID> | member_of | "<why>" | <passport-path(optional)>
- XREF: <TARGET_ENTITY_UID> | located_in | "<why>" | <passport-path(optional)>
- XREF: <TARGET_ENTITY_UID> | opposes | "<why>" | <passport-path(optional)>

NOTE:
- REL типы можешь фиксировать по мере роста, главное — UID-first и смысл в WHY.

---

## 5) APPEARANCES / USAGE (OPTIONAL)
> Где сущность появляется (сцены/ивенты/арки). Только через UID, если это внутренние объекты.

APPEARS_IN:
- UID: <SCENE_UID> | NOTE: "<optional>"

---

## 6) DEPRECATION (ONLY IF ENTITY_STATUS=deprecated)
DEPRECATED_BY_ENTITY_UID: <ENTITY_UID_CANON>
DEPRECATION_REASON: "<why merged/renamed>"
MIGRATION_NOTE: "Use <ENTITY_UID_CANON> instead."

XREF:
- XREF: <ENTITY_UID_CANON> | deprecated_by | "replacement entity" | <path(optional)>

---

## 7) META (OPTIONAL)
TAGS: [<optional tags>]
SOURCES: [<optional sources list>]
NOTES: "<optional>"

--- END OF TEMPLATE
