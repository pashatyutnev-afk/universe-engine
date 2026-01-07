# KNOWLEDGE BASE INDEX — MASTER REGISTRY (CANON)
FILE: 04_KNOWLEDGE_BASE/00__INDEX__KNOWLEDGE_BASE.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
INDEX_TYPE: MASTER_KB_REGISTRY
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.1.0
UID: UE.DOC.IDX.KB.MASTER
OWNER: SYSTEM
ROLE: Canonical navigation law + registry for Knowledge Base layer (mandatory entrypoint)

CHANGE_NOTE:
- DATE: 2026-01-07
- TYPE: MINOR
- SUMMARY: "Нормализован KB Index: один канонический entrypoint + UID/LOCK + выведены алиасы в NON-CANON блок"
- REASON: "Соблюдение SYSTEM LAW / Naming Rules / Single SoT"
- IMPACT: "KB навигация, регистрация файлов, последующая миграция имен/шапок"

---

## 0) PURPOSE (LAW)
Этот INDEX — единая точка истины для слоя `04_KNOWLEDGE_BASE`.

Он фиксирует:
- состав KB: governance + realms + системные KB-артефакты
- порядок навигации (by folder + number)
- канонические пути (и raw-ссылки, если файл в репо)
- правило существования KB артефактов

### EXISTENCE RULE (ABSOLUTE)
Если KB-артефакта нет в этом INDEX — он не существует для слоя KNOWLEDGE BASE.
Если файл есть в репо, но не зарегистрирован здесь — он считается NON-CANON (ignored).

---

## 1) HOW TO USE (MANDATORY FLOW)
1) Сначала читаешь `00_KB_GOVERNANCE/00__README__KB_REALM.md`.
2) Затем `00_KB_GOVERNANCE/01__RULES__KB.md`.
3) Потом идёшь в нужный realm (Narrative / Character / Visual / Sound / Production / Marketing / Glossary / Research).
4) Любой новый KB-документ:
   - сначала добавляется в этот INDEX,
   - потом создаётся файл,
   - потом фиксируется согласно governance rules + system change policy.

---

## 2) ORDER OF AUTHORITY (PRIORITY)
При конфликте смыслов/правил в KB приоритет такой:
1) `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/*`
2) `04_KNOWLEDGE_BASE/*` (реалмы и контент KB)

---

## 3) CANON MAP — KNOWLEDGE BASE TREE

### 00_KB_GOVERNANCE (Governance / Rules / Maps / Templates)
Folder: `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/`

00 — README: KB Realm (Core)
🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/00__README__KB_REALM.md

01 — RULES: KB (Governance Rules)
🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/01__RULES__KB.md

02 — INDEX: KB Global Registry
🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/02__INDEX__KB_GLOBAL_REGISTRY.md

03 — INDEX: KB Entity Types
🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/03__INDEX__KB_ENTITY_TYPES.md

04 — KB Storage Map
🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/04__KB_STORAGE_MAP.md

05 — TEMPLATE: KB Entity Passport
🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/05__TEMPLATE__KB_ENTITY_PASSPORT.md

06 — KB Create Flow
🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/06__KB_CREATE_FLOW.md

---

### KB REALMS (Canonical knowledge realms)
NOTE: Realm-документы являются каноническими документами и должны соответствовать Doc Control
(шапка STATUS/LOCK/VERSION/OWNER/ROLE + UID). Миграция ниже.

01 — Narrative Craft (Realm)
🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/01_NARRATIVE_CRAFT.md

02 — Character Craft (Realm)
🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/02_CHARACTER_CRAFT.md

03 — Visual Cinema (Realm)
🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/03_VISUAL_CINEMA.md

04 — Sound & Music (Realm)
🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/04_SOUND_MUSIC.md

05 — Production Pipeline (Realm)
🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/05_PRODUCTION_PIPELINE.md

06 — Marketing & Distribution (Realm)
🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/06_MARKETING_DISTRIBUTION.md

07 — Reference Glossary (Realm)
🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/07_REFERENCE_GLOSSARY.md

08 — Research & Fact Checking (Realm)
🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/08_RESEARCH_FACT_CHECKING.md

---

### KB SYSTEM FILES (If used as SoT inside KB)
02 — KB Tags (System)
🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/02__KB_TAGS.md

---

## 4) NO-DUPLICATION RULE (KB)
- Один смысл → один KB-артефакт.
- Если нужно расширение — расширяем существующий артефакт или добавляем паспорт сущности + связи.
- Дубли “одного и того же знания” в разных реальмах запрещены без явного XREF/REL.

---

## 5) NON-CANON ALIASES (INTENTIONALLY UNREGISTERED)
Следующие файлы считаются алиасами/устаревшими именами и НЕ являются каноническими entrypoint.
Они должны быть либо удалены, либо приведены к канону через Canon Protocol:
- `04_KNOWLEDGE_BASE/01__KB_INDEX.md`
- `04_KNOWLEDGE_BASE/00_INDEX_KNOWLEDGE_BASE.md`

---

## 6) MIGRATION PLAN (NEXT STEPS)
S0 (обязательно):
- привести realm-файлы к Doc Control: добавить шапку + UID + VERSION (иначе это неканон)
- нормализовать Naming: привести к формату `NN__NAME.md` (двойное подчёркивание) или зафиксировать исключение в Naming Rules
- устранить коллизии по номерам (`02_CHARACTER_CRAFT.md` vs `02__KB_TAGS.md`) либо через переименование, либо через явное правило

---

## FINAL RULE (LOCK)
Этот INDEX — единственная точка истины о составе и порядке `04_KNOWLEDGE_BASE`.
Любая правка INDEX считается изменением канона и проходит Canon Protocol.
--- END.
