# KNOWLEDGE BASE INDEX — MASTER REGISTRY (CANON)
FILE: 04_KNOWLEDGE_BASE/00__INDEX__KNOWLEDGE_BASE.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: INDEX
INDEX_TYPE: MASTER
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.KB.IDX.MASTER.001
OWNER: SYSTEM
ROLE: Canonical navigation law + master registry for the Knowledge Base layer (mandatory entrypoint)

CHANGE_NOTE:
- DATE: 2026-01-07
- TYPE: MAJOR
- SUMMARY: "KB layer нормализован: один entrypoint master-index, жёстко отделены non-canon алиасы, добавлен план миграции governance/realms под Doc Control"
- REASON: "Single entrypoint + Existence Rule + Doc Control compliance"
- IMPACT: "KB navigation, file naming, registry flow, дальнейшая миграция всех KB файлов"

---

## 0) PURPOSE (LAW)
Этот INDEX — **единая точка истины** для слоя `04_KNOWLEDGE_BASE`.

Он фиксирует:
- полный состав KB (governance + realms + системные KB-артефакты)
- строгий порядок навигации (by folder + number)
- канонические пути (PATH) и reference raw-ссылки (если нужно)
- правило существования KB артефактов

### EXISTENCE RULE (ABSOLUTE)
> Если KB-файла/реалма/шаблона нет в этом INDEX — он **не существует** для слоя KNOWLEDGE BASE.  
> Если файл лежит в репо, но не зарегистрирован здесь — **NON-CANON / ignored**.

---

## 1) HOW TO USE (MANDATORY FLOW)
1) Сначала читаешь governance:
   - `00_KB_GOVERNANCE/00__README__KB_REALM.md`
   - `00_KB_GOVERNANCE/01__RULES__KB.md`
2) Затем смотришь “что существует” только по этому master-index.
3) Потом идёшь в нужный realm-файл (Narrative / Character / Visual / Sound / Production / Marketing / Glossary / Research).
4) Любой новый KB-документ:
   - сначала добавляется в этот INDEX,
   - потом создаётся файл,
   - потом фиксируется по governance rules + system change policy.

---

## 2) ORDER OF AUTHORITY (PRIORITY)
При конфликте правил в KB приоритет такой:

1) `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/*` (законы и карты KB)
2) `04_KNOWLEDGE_BASE/00__INDEX__KNOWLEDGE_BASE.md` (existence + состав)
3) `04_KNOWLEDGE_BASE/*` (реалмы и контент KB)

---

## 3) CANON MAP — KNOWLEDGE BASE TREE

# 00_KB_GOVERNANCE (Governance / Rules / Maps / Templates)
**Folder:** `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/`  
**Rule:** Здесь живут “законы и карты” KB. Это управление, а не контент-реалмы.

00 — README: KB Realm (Core)  
PATH: `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/00__README__KB_REALM.md`  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/00__README__KB_REALM.md

01 — RULES: KB (Governance Rules)  
PATH: `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/01__RULES__KB.md`  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/01__RULES__KB.md

02 — INDEX: KB Global Registry  
PATH: `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/02__INDEX__KB_GLOBAL_REGISTRY.md`  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/02__INDEX__KB_GLOBAL_REGISTRY.md

03 — INDEX: KB Entity Types  
PATH: `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/03__INDEX__KB_ENTITY_TYPES.md`  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/03__INDEX__KB_ENTITY_TYPES.md

04 — KB Storage Map  
PATH: `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/04__KB_STORAGE_MAP.md`  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/04__KB_STORAGE_MAP.md

05 — TEMPLATE: KB Entity Passport  
PATH: `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/05__TEMPLATE__KB_ENTITY_PASSPORT.md`  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/05__TEMPLATE__KB_ENTITY_PASSPORT.md

06 — KB Create Flow  
PATH: `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/06__KB_CREATE_FLOW.md`  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/06__KB_CREATE_FLOW.md

---

# KB REALMS (Canonical knowledge realms)
**Folder:** `04_KNOWLEDGE_BASE/`  
**Rule:** Realm-файлы — канонические документы и обязаны соответствовать Doc Control (шапка + UID + SemVer).

01 — Narrative Craft (Realm)  
PATH: `04_KNOWLEDGE_BASE/01_NARRATIVE_CRAFT.md`  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/01_NARRATIVE_CRAFT.md

02 — Character Craft (Realm)  
PATH: `04_KNOWLEDGE_BASE/02_CHARACTER_CRAFT.md`  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/02_CHARACTER_CRAFT.md

03 — Visual Cinema (Realm)  
PATH: `04_KNOWLEDGE_BASE/03_VISUAL_CINEMA.md`  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/03_VISUAL_CINEMA.md

04 — Sound & Music (Realm)  
PATH: `04_KNOWLEDGE_BASE/04_SOUND_MUSIC.md`  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/04_SOUND_MUSIC.md

05 — Production Pipeline (Realm)  
PATH: `04_KNOWLEDGE_BASE/05_PRODUCTION_PIPELINE.md`  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/05_PRODUCTION_PIPELINE.md

06 — Marketing & Distribution (Realm)  
PATH: `04_KNOWLEDGE_BASE/06_MARKETING_DISTRIBUTION.md`  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/06_MARKETING_DISTRIBUTION.md

07 — Reference Glossary (Realm)  
PATH: `04_KNOWLEDGE_BASE/07_REFERENCE_GLOSSARY.md`  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/07_REFERENCE_GLOSSARY.md

08 — Research & Fact Checking (Realm)  
PATH: `04_KNOWLEDGE_BASE/08_RESEARCH_FACT_CHECKING.md`  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/08_RESEARCH_FACT_CHECKING.md

---

# KB SYSTEM FILES (SoT inside KB if used)
**Rule:** Системные файлы KB не должны коллизить по номерам с realm-ами.

S1 NOTE (collision risk):
- `02__KB_TAGS.md` коллизит по номеру с `02_CHARACTER_CRAFT.md`.

02 — KB Tags (System)  
PATH: `04_KNOWLEDGE_BASE/02__KB_TAGS.md`  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/04_KNOWLEDGE_BASE/02__KB_TAGS.md

---

## 4) NO-DUPLICATION RULE (KB)
- Один смысл → один KB-артефакт.
- Детализация делается внутри существующего realm-файла или через KB Entity Passport + XREF.
- Дубли в разных реальмах запрещены без явного XREF/REL.

---

## 5) NON-CANON ALIASES (INTENTIONALLY UNREGISTERED)
Следующие файлы НЕ являются каноническими entrypoint и должны стать **legacy alias pointers** или быть удалены:

- `04_KNOWLEDGE_BASE/01__KB_INDEX.md`
- `04_KNOWLEDGE_BASE/00_INDEX_KNOWLEDGE_BASE.md`

---

## 6) MIGRATION PLAN (NEXT STEPS)
### S0 (обязательно)
1) Governance файлы привести к Doc Control:
   - добавить шапку, UID, SemVer, LOCK: FIXED
2) Realm-файлы привести к Doc Control:
   - сейчас realm-контент без шапки/UID = NON-CANON по правилам
3) Устранить номерную коллизию:
   - вариант А (рекомендую): перенести KB system файлы в отдельный неймспейс/номер (например `90__KB_TAGS.md`)
   - вариант B: вынести system файлы в `00_KB_GOVERNANCE/` (как управляемые SoT справочники)

### S1 (следом)
- привести naming к единому правилу (и зафиксировать исключения, если оставляем текущие имена)
- сделать alias pointer файлы для legacy entrypoints

---

## FINAL RULE (LOCK)
Этот INDEX — единственная точка истины о составе и порядке `04_KNOWLEDGE_BASE`.
Любая правка состава/порядка = изменение канона и проходит Canon Protocol.
--- END.
