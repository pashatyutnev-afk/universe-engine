# KB CREATE FLOW (GOVERNANCE PIPELINE)
FILE: 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/06__KB_CREATE_FLOW.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: FLOW
FLOW_TYPE: CREATE
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.GOV.FLOW.CREATE.001
OWNER: SYSTEM
ROLE: Canonical pipeline for creating KB artifacts: realm updates, system KB docs, and KB entity passports (prevents duplication and chaos)

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "KB create flow: decision tree (realm vs entity), registry steps, naming/UID gates, storage map compliance"
- REASON: "Нужен единый способ создавать KB, иначе всё ломается на уровне структуры"
- IMPACT: "Все новые KB документы и сущности"

---

## 0) PURPOSE
Этот flow определяет:
- что именно создавать (realm update / entity passport / system ref)
- куда класть (storage map)
- как регистрировать (master-index + global registry)
- какие гейты пройти перед канонизацией

---

## 1) DECISION TREE (WHAT TO CREATE)
### Step 1 — Это “контент домена” без уникальной идентичности?
Да → обновляй соответствующий `KB REALM` файл (01..08)

Примеры:
- общий список приёмов диалога
- чеклист сцены “внутри” Narrative realm
- советы по свету в Visual realm

### Step 2 — Это объект, который должен быть переиспользуемым и иметь UID?
Да → создавай `KB ENTITY PASSPORT`

Примеры:
- конкретный паттерн как самостоятельная сущность
- конкретный процесс пайплайна
- отдельный валидатор/чеклист как объект

### Step 3 — Это системный справочник KB (например теги)?
Да → создавай `KB SYSTEM DOC` в `04_KNOWLEDGE_BASE/90__*.md`

---

## 2) FLOW A — REALM UPDATE (CONTENT)
1) Найди подходящий realm:
- Narrative / Character / Visual / Sound / Production / Marketing / Glossary / Research

2) Проверь anti-dup:
- нет ли уже этого же пункта в другом realm → если есть, добавь XREF вместо копирования

3) Внеси правку:
- добавь секцию или расширь существующую
- не переписывай стандарты/законы, только практику

4) Обнови CHANGE_NOTE внутри файла (если ведёшь историю) или через систему версий — по ruleset.

---

## 3) FLOW B — KB ENTITY PASSPORT (OBJECT)
### B1) Pre-check (anti-dup)
1) Проверь master-index KB: существует ли уже похожая сущность по смыслу
2) Проверь global registry: нет ли похожей сущности/UID

Если дубль найден → делай XREF/REL, НЕ создавай новый паспорт.

### B2) Choose type
Выбери `ENTITY_TYPE` из:
`03__INDEX__KB_ENTITY_TYPES.md`

### B3) Choose storage path
По storage map:
`04_KNOWLEDGE_BASE/10_ENTITIES/<ENTITY_TYPE>/`

Если папки нет — создаём (один раз).

### B4) Naming + UID
- Filename: `NN__<NAME>.md` (NN = следующий свободный номер в папке)
- UID: `UE.KB.ENT.<TYPE>.<NNN>` (NNN = уникальный числовой id, 3 цифры)

Правило:
- номер файла (NN) и UID.NNN не обязаны совпадать,
  но UID обязан быть уникальным в системе.

### B5) Create from template
Копируй:
`05__TEMPLATE__KB_ENTITY_PASSPORT.md`
и заполни.

### B6) Registry updates (MANDATORY)
1) Добавь запись в:
`02__INDEX__KB_GLOBAL_REGISTRY.md`
2) Добавь регистрацию в master-index KB, если сущность канонизируется как “существующая в KB”
(иначе оставь как draft и зарегистрируй позже)

### B7) XREF back to realm (MANDATORY)
Добавь минимум 1 ссылку XREF:
- из паспорта → на realm, где это применяется
- и/или из realm → на паспорт (предпочтительно обе стороны)

---

## 4) FLOW C — KB SYSTEM DOC (HELPER)
1) Имя файла:
`04_KNOWLEDGE_BASE/90__<NAME>.md`
2) Doc Control шапка + UID + SemVer
3) Регистрация:
- master-index KB
- global registry KB

---

## 5) CANONIZATION GATES (BEFORE STATUS ACTIVE)
Перед переводом любого KB объекта в `STATUS: ACTIVE`:

- [ ] зарегистрирован в master-index (если должен “существовать”)
- [ ] Doc Control корректен
- [ ] UID уникален
- [ ] naming соответствует правилам
- [ ] storage map соблюдён
- [ ] нет дубля смысла
- [ ] XREF/REL оформлены

---

## 6) PROHIBITIONS (HARD)
Запрещено:
- создавать KB entity без паспорта
- создавать сущности без регистрации в registry (хотя бы как DRAFT)
- класть паспорта в корень KB
- плодить “ещё один индекс” вместо правки master-index/registry

---

## FINAL RULE (LOCK)
Этот flow обязателен для создания любых KB-артефактов.
LOCK: FIXED
--- END.
