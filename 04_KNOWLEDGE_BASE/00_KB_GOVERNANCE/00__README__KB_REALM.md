# KNOWLEDGE BASE (KB) — REALM README (CANON)
FILE: 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/00__README__KB_REALM.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: GUIDE
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.1.0
UID: UE.KB.GOV.README.REALM.010
OWNER: SYSTEM
ROLE: Core README for the KB realm: what KB is, what it is not, how KB is structured, and how knowledge becomes canon.

CHANGE_NOTE:
- DATE: 2026-01-07
- TYPE: MINOR
- SUMMARY: "Нормализован KB README: Doc Control header, чёткое разделение KB files vs KB entities, правила канона и ссылки на governance"
- REASON: "KB должен быть управляемым как слой канона"
- IMPACT: "KB onboarding, создание сущностей, реестры, навигация"

---

## XREF (UID-first)
XREF: UE.KB.IDX.MASTER.001 | depends_on | KB existence is defined by KB master-index | 04_KNOWLEDGE_BASE/00__INDEX__KNOWLEDGE_BASE.md
XREF: UE.STD.SPEC.DOC_CONTROL.103 | depends_on | canonical header & change note | 02_STANDARDS/01_SPECIFICATIONS/03__DOC_CONTROL_STANDARD.md
XREF: UE.STD.SPEC.REL_XREF.104 | depends_on | UID-first linking rules | 02_STANDARDS/01_SPECIFICATIONS/04__REL_POLICY_XREF_STANDARD.md

---

## 0) WHAT IS KB (DEFINITION)
KB (Knowledge Base) — это **каноническое хранилище знаний** о вселенной/системе:
- сущности мира (персонажи, локации, объекты, события, фракции, технологии…)
- определения, таксономии, справочники
- правила мира и “истина” (в пределах домена KB)

KB — это **не производство** и не проектная папка.
KB отвечает на вопрос: “что истинно в мире/системе”.

---

## 1) WHAT KB IS NOT
KB не хранит:
- черновой продакшн-контент (монтаж, рабочие промпты, версии сцен “на вынос”)
- выходные файлы (видео/аудио/рендеры)
- производственные пайплайны как артефакты проекта

Это живёт в PRJ/OUT/ASSETS (в соответствующих слоях/областях), а KB хранит только **знание/истину**.

---

## 2) KB HAS TWO “EXISTENCE” LEVELS (CRITICAL)
### 2.1 Existence of KB FILES (layer canon)
Существование файлов слоя `04_KNOWLEDGE_BASE` определяется **только**:
- `04_KNOWLEDGE_BASE/00__INDEX__KNOWLEDGE_BASE.md` (master-index)

Если файла нет в master-index — он NON-CANON для слоя KB.

### 2.2 Existence of KB ENTITIES (world canon)
Сущность (персонаж/объект/событие) считается существующей “в системе KB” только если:
1) у неё есть `ENTITY_UID`
2) у неё есть паспорт (entity passport) по шаблону KB
3) она зарегистрирована в KB Global Registry

Если сущности нет в глобальном реестре — она NON-CANON (ignored), даже если где-то описана текстом.

---

## 3) KB CORE LAW (ABSOLUTE)
- Любая KB-сущность обязана иметь `ENTITY_UID`.
- Любая KB-сущность обязана быть зарегистрирована в **KB Global Registry**.
- Любые связи между сущностями/доками делаются **UID-first** (XREF).
- Один смысл → одна сущность/один SoT-артефакт (no-dup).

---

## 4) KB STRUCTURE (HOW IT IS ORGANIZED)
KB состоит из двух частей:

### 4.1 KB Governance (управление)
Папка `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/` хранит:
- правила, реестры, типы, карты хранения, шаблоны

Это “верхний уровень управления” KB, не контент-реалмы.

### 4.2 KB Realms (контент-реалмы)
Файлы realм-ов (Narrative / Character / Visual / Sound / Production / Marketing / Glossary / Research) — это
- методики, справочники, правила и знания по домену,
- НЕ заменяют паспорта сущностей,
- могут ссылаться на сущности через UID/XREF.

---

## 5) HOW TO USE (MANDATORY FLOW)
1) Определи, что ты добавляешь:
   - новый факт/правило/методика → в соответствующий realm (и с XREF на сущности)
   - новую сущность мира → через паспорт сущности + реестр
2) Если это сущность:
   - создать паспорт сущности по шаблону KB
   - присвоить `ENTITY_UID`
   - зарегистрировать в KB Global Registry
   - добавить ключевые XREF связи
3) Если это знание в realm:
   - добавить секцию/правило
   - при необходимости создать/обновить сущности и сослаться на них UID-first

---

## 6) LINKS (GOVERNANCE ENTRYPOINTS)
- KB Rules: `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/01__RULES__KB.md`
- KB Global Registry: `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/02__INDEX__KB_GLOBAL_REGISTRY.md`
- KB Entity Types: `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/03__INDEX__KB_ENTITY_TYPES.md`
- KB Storage Map: `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/04__KB_STORAGE_MAP.md`
- Template: KB Entity Passport: `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/05__TEMPLATE__KB_ENTITY_PASSPORT.md`
- KB Create Flow: `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/06__KB_CREATE_FLOW.md`

--- END.
