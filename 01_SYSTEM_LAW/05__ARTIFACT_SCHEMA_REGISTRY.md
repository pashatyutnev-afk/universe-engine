# ARTIFACT SCHEMA REGISTRY (CANON)
FILE: 01_SYSTEM_LAW/05__ARTIFACT_SCHEMA_REGISTRY.md

SCOPE: Universe Engine
LAYER: 01_SYSTEM_LAW
DOC_TYPE: REGISTRY
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.1.0
UID: UE.REG.ARTIFACT.SCHEMA.MASTER.005
OWNER: SYSTEM
ROLE: Canonical registry of artifact schemas/types used by the Universe Engine. UID is primary. Type keys are optional human-friendly aliases.

CHANGE_NOTE:
- DATE: 2026-01-07
- TYPE: MINOR
- SUMMARY: "Единый реестр схем артефактов: UID-first, валидные type keys, совместимость с пайплайнами, запрет конфликтующих форматов"
- REASON: "Устранение ART: vs ART. конфликтов и формализация схем"
- IMPACT: "Pipelines, standards, KB governance, validation"

---

## 0) PRIME LAW (ABSOLUTE)
- Любой артефакт, который участвует в пайплайнах/реестрах/каноне, обязан иметь **тип**.
- Тип артефакта определяется **UID схемы** (primary).
- Человеко-читаемый `TYPE_KEY` — вторичен (alias), не заменяет UID.

---

## 1) TERMINOLOGY
**Artifact** — экземпляр выходного объекта (doc/pack/event/passport/registry/scene-pack/etc).  
**Schema** — описание формата артефакта (поля, правила, валидатор).  
**TYPE_UID** — UID схемы (канонический идентификатор типа).  
**TYPE_KEY** — короткий алиас (удобно для людей/папок), но не системный идентификатор.

---

## 2) TYPE_KEY FORMAT (ALIAS, OPTIONAL)
Если используется `TYPE_KEY`, то формат такой:

`UE.<DOMAIN>.<NAME>`

Где:
- `UE` — константа
- `<DOMAIN>` — DOC | KB | STD | PIPE | ART | ENT | PRJ | OUT
- `<NAME>` — UPPER_SNAKE_CASE

Примеры:
- `UE.DOC.MASTER_INDEX`
- `UE.KB.REALM`
- `UE.KB.ENTITY_PASSPORT`
- `UE.STD.SPEC`
- `UE.ART.SCENE_PACK`
- `UE.ART.TRACK_EVENT`
- `UE.REG.TABLE`

Запрещено:
- `ART:...`
- `ART.PRJ....` (смешение доменов без правила)
- точки/двоеточия вразнобой без единого формата

---

## 3) REGISTRY RECORD (MANDATORY FIELDS)
Каждая схема в реестре обязана иметь:

- `TYPE_UID` (primary, required)
- `TYPE_KEY` (optional alias)
- `STATUS` (ACTIVE | DEPRECATED | DRAFT)
- `VERSION` (SemVer)
- `SCOPE/LAYER` (где применяется)
- `ROLE` (что это)
- `SOURCE_DOC` (канонический документ, который описывает схему — путь/raw)
- `VALIDATION` (как валидировать: human/manual/CI/script name)

---

## 4) MASTER REGISTRY (SCHEMAS)
NOTE: Этот список — минимальный старт. Он расширяется только по Canon Protocol.

### A) Core document artifacts
1) MASTER INDEX (Layer Index)
- TYPE_UID: UE.ART.DOC.MASTER_INDEX.001
- TYPE_KEY: UE.DOC.MASTER_INDEX
- STATUS: ACTIVE
- VERSION: 1.0.0
- SCOPE/LAYER: any (all layers)
- ROLE: Entry-point index that defines existence/order for a layer
- SOURCE_DOC: 01_SYSTEM_LAW/00__SYSTEM_LAW.md (defines)
- VALIDATION: CI (index-link validator)

2) REGISTRY TABLE
- TYPE_UID: UE.ART.DOC.REGISTRY_TABLE.002
- TYPE_KEY: UE.REG.TABLE
- STATUS: ACTIVE
- VERSION: 1.0.0
- SCOPE/LAYER: any
- ROLE: Canonical registry listing typed items (schemas/entities/pipelines/etc.)
- SOURCE_DOC: 01_SYSTEM_LAW/05__ARTIFACT_SCHEMA_REGISTRY.md
- VALIDATION: CI/manual

3) LAW DOCUMENT
- TYPE_UID: UE.ART.DOC.LAW.003
- TYPE_KEY: UE.DOC.LAW
- STATUS: ACTIVE
- VERSION: 1.0.0
- SCOPE/LAYER: 01_SYSTEM_LAW
- ROLE: System law document (normative)
- SOURCE_DOC: 01_SYSTEM_LAW/00__SYSTEM_LAW.md
- VALIDATION: manual/CI (doc control lints)

4) STANDARD (SoT / SPEC)
- TYPE_UID: UE.ART.STD.SPEC.010
- TYPE_KEY: UE.STD.SPEC
- STATUS: ACTIVE
- VERSION: 1.0.0
- SCOPE/LAYER: 02_STANDARDS
- ROLE: Source-of-Truth specification
- SOURCE_DOC: 02_STANDARDS/01_SPECIFICATIONS/* (SoT docs)
- VALIDATION: manual/CI (no-dup gates)

5) STANDARD MODULE (detail)
- TYPE_UID: UE.ART.STD.MODULE.011
- TYPE_KEY: UE.STD.MODULE
- STATUS: ACTIVE
- VERSION: 1.0.0
- SCOPE/LAYER: 02_STANDARDS/06_MARKING_STANDARDS
- ROLE: Module that extends a SoT spec (no SoT claims)
- SOURCE_DOC: 02_STANDARDS/06_MARKING_STANDARDS/*
- VALIDATION: manual/CI (must reference SoT)

---

### B) KB artifacts
6) KB REALM DOCUMENT
- TYPE_UID: UE.ART.KB.REALM.020
- TYPE_KEY: UE.KB.REALM
- STATUS: ACTIVE
- VERSION: 1.0.0
- SCOPE/LAYER: 04_KNOWLEDGE_BASE
- ROLE: Realm knowledge doc (domain knowledge)
- SOURCE_DOC: 04_KNOWLEDGE_BASE/00__INDEX__KNOWLEDGE_BASE.md
- VALIDATION: doc control + UID presence

7) KB ENTITY PASSPORT
- TYPE_UID: UE.ART.KB.ENTITY_PASSPORT.021
- TYPE_KEY: UE.KB.ENTITY_PASSPORT
- STATUS: ACTIVE
- VERSION: 1.0.0
- SCOPE/LAYER: 04_KNOWLEDGE_BASE
- ROLE: Passport describing an entity with UID and mappings (local ids -> uid)
- SOURCE_DOC: 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/05__TEMPLATE__KB_ENTITY_PASSPORT.md
- VALIDATION: schema checks (manual/CI)

8) KB TAGS DICTIONARY
- TYPE_UID: UE.ART.KB.TAGS.022
- TYPE_KEY: UE.KB.TAGS
- STATUS: ACTIVE
- VERSION: 1.0.0
- SCOPE/LAYER: 04_KNOWLEDGE_BASE
- ROLE: SoT dictionary of KB tags (if governance chooses tag system)
- SOURCE_DOC: 04_KNOWLEDGE_BASE/02__KB_TAGS.md
- VALIDATION: manual/CI (no duplicates)

---

### C) Scene system artifacts (initial set)
9) SCENE PACK
- TYPE_UID: UE.ART.SCENE.PACK.030
- TYPE_KEY: UE.ART.SCENE_PACK
- STATUS: DRAFT
- VERSION: 0.1.0
- SCOPE/LAYER: 02_STANDARDS (Scene Stack family)
- ROLE: Container describing a scene with tracks/metadata
- SOURCE_DOC: 02_STANDARDS/01_SPECIFICATIONS/05A__TEMPLATE__SCENE_PACK.md
- VALIDATION: to-be-defined

10) TRACK EVENT
- TYPE_UID: UE.ART.SCENE.TRACK_EVENT.031
- TYPE_KEY: UE.ART.TRACK_EVENT
- STATUS: DRAFT
- VERSION: 0.1.0
- SCOPE/LAYER: 02_STANDARDS (Scene Stack family)
- ROLE: Atomic event within a track
- SOURCE_DOC: 02_STANDARDS/01_SPECIFICATIONS/05B__TEMPLATE__TRACK_EVENT.md
- VALIDATION: to-be-defined

---

## 5) CHANGE RULES (REGISTRY GOVERNANCE)
- Добавление нового TYPE_UID или изменение роли/формата существующего — минимум MINOR.
- Несовместимое изменение схемы — MAJOR + миграционный план.
- Удалять тип из registry запрещено без deprecation (сначала DEPRECATED, потом ARCHIVED).

---

## 6) VALIDATION GATES (MUST PASS)
Для каждого зарегистрированного schema record:
- TYPE_UID уникален
- VERSION валиден (SemVer)
- STATUS валиден
- SOURCE_DOC существует и каноничен (registered в соответствующем index)
- TYPE_KEY (если есть) соответствует формату

---

## FINAL RULE (LOCK)
Этот реестр — канонический справочник типов/схем артефактов.
Любая правка — изменение канона и проходит Canon Protocol.
--- END.
