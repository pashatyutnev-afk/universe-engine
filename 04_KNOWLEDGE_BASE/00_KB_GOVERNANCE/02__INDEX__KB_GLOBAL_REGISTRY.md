# KB GLOBAL REGISTRY (INDEX)
FILE: 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/02__INDEX__KB_GLOBAL_REGISTRY.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
DOC_TYPE: INDEX
INDEX_TYPE: REGISTRY
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.KB.GOV.IDX.GLOBAL_REGISTRY.001
OWNER: SYSTEM
ROLE: Canonical registry-index for KB entities and KB system artifacts (inventory, status, version, UID, pointers)

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "KB global registry нормализован: Doc Control, назначение как registry (не existence), формат записей"
- REASON: "Нужен учёт KB-сущностей без дублирования master-index"
- IMPACT: "Инвентаризация KB, поиск, контроль версий и статусов"

---

## 0) PURPOSE
Этот реестр фиксирует:
- **учёт** KB-артефактов (realm docs, system KB docs, KB entity passports)
- их UID / VERSION / STATUS / LOCK
- их PATH (куда лежит файл)

Важно:
- Этот реестр **НЕ определяет существование**.
- Existence rule задаёт только `00__INDEX__KNOWLEDGE_BASE.md`.

---

## 1) HOW TO USE
1) Существование проверяешь в master-index KB.
2) Статусы/версии/UID проверяешь здесь.
3) Если нужен новый KB-паспорт:
   - сначала запись здесь (как учёт),
   - потом файл по шаблону,
   - затем регистрация в master-index (если это новый канонический объект).

---

## 2) RECORD FORMAT (STRICT)
Каждая запись в реестре должна быть одной строкой по формату:

`<UID> | <DOC_TYPE> | <STATUS> | <LOCK> | <VERSION> | <PATH> | TAGS:[a,b,c] | NOTE:<short>`

Правила:
- UID обязателен
- VERSION строго `X.Y.Z`
- STATUS/LOCK только из допустимых наборов
- TAGS опциональны, но для паспортов желательны
- NOTE максимум 120 символов

---

## 3) REGISTRY SECTIONS (ORDER)
Реестр делится на секции (чтобы не мешать разные классы):

### A) Governance files (KB)
### B) KB Master index (entrypoint)
### C) KB Realms (content)
### D) KB System files (KB SoT helpers)
### E) KB Entity Passports (objects)

---

## 4) REGISTRY (CANON RECORDS)
> Заполняется и поддерживается по мере канонизации.

### A) Governance files (KB)
UE.KB.GOV.README.001 | README | ACTIVE | FIXED | 1.0.0 | 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/00__README__KB_REALM.md | TAGS:[kb,governance] | NOTE:KB governance realm overview
UE.KB.GOV.RULES.001 | RULESET | ACTIVE | FIXED | 1.0.0 | 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/01__RULES__KB.md | TAGS:[kb,governance] | NOTE:KB governance ruleset
UE.KB.GOV.IDX.GLOBAL_REGISTRY.001 | INDEX | ACTIVE | FIXED | 1.0.0 | 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/02__INDEX__KB_GLOBAL_REGISTRY.md | TAGS:[kb,registry] | NOTE:KB global registry index
UE.KB.GOV.IDX.ENTITY_TYPES.001 | INDEX | DRAFT | OPEN | 0.1.0 | 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/03__INDEX__KB_ENTITY_TYPES.md | TAGS:[kb,types] | NOTE:KB entity type list (to normalize)
UE.KB.GOV.STORAGE_MAP.001 | MAP | DRAFT | OPEN | 0.1.0 | 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/04__KB_STORAGE_MAP.md | TAGS:[kb,storage] | NOTE:KB storage map (to normalize)
UE.KB.GOV.TPL.PASSPORT.001 | TEMPLATE | DRAFT | OPEN | 0.1.0 | 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/05__TEMPLATE__KB_ENTITY_PASSPORT.md | TAGS:[kb,template] | NOTE:KB entity passport template (to normalize)
UE.KB.GOV.FLOW.CREATE.001 | FLOW | DRAFT | OPEN | 0.1.0 | 04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/06__KB_CREATE_FLOW.md | TAGS:[kb,flow] | NOTE:KB create flow (to normalize)

### B) KB Master index (entrypoint)
UE.KB.IDX.MASTER.001 | INDEX | ACTIVE | FIXED | 2.0.0 | 04_KNOWLEDGE_BASE/00__INDEX__KNOWLEDGE_BASE.md | TAGS:[kb,master] | NOTE:KB master registry (existence)

### C) KB Realms (content)
UE.KB.REALM.NARRATIVE.001 | KB_REALM | DRAFT | OPEN | 0.1.0 | 04_KNOWLEDGE_BASE/01__NARRATIVE_CRAFT.md | TAGS:[kb,narrative] | NOTE:realm narrative craft
UE.KB.REALM.CHARACTER.001 | KB_REALM | DRAFT | OPEN | 0.1.0 | 04_KNOWLEDGE_BASE/02__CHARACTER_CRAFT.md | TAGS:[kb,character] | NOTE:realm character craft
UE.KB.REALM.VISUAL.001 | KB_REALM | DRAFT | OPEN | 0.1.0 | 04_KNOWLEDGE_BASE/03__VISUAL_CINEMA.md | TAGS:[kb,visual] | NOTE:realm visual/cinema
UE.KB.REALM.SOUND.001 | KB_REALM | DRAFT | OPEN | 0.1.0 | 04_KNOWLEDGE_BASE/04__SOUND_MUSIC.md | TAGS:[kb,sound] | NOTE:realm sound/music
UE.KB.REALM.PRODUCTION.001 | KB_REALM | DRAFT | OPEN | 0.1.0 | 04_KNOWLEDGE_BASE/05__PRODUCTION_PIPELINE.md | TAGS:[kb,production] | NOTE:realm production pipeline
UE.KB.REALM.MARKETING.001 | KB_REALM | DRAFT | OPEN | 0.1.0 | 04_KNOWLEDGE_BASE/06__MARKETING_DISTRIBUTION.md | TAGS:[kb,marketing] | NOTE:realm marketing/distribution
UE.KB.REALM.GLOSSARY.001 | KB_REALM | DRAFT | OPEN | 0.1.0 | 04_KNOWLEDGE_BASE/07__REFERENCE_GLOSSARY.md | TAGS:[kb,glossary] | NOTE:realm reference glossary
UE.KB.REALM.RESEARCH.001 | KB_REALM | DRAFT | OPEN | 0.1.0 | 04_KNOWLEDGE_BASE/08__RESEARCH_FACT_CHECKING.md | TAGS:[kb,research] | NOTE:realm research/fact checking

### D) KB System files (KB SoT helpers)
UE.KB.SYS.TAGS.001 | KB_SYSTEM | DRAFT | OPEN | 0.1.0 | 04_KNOWLEDGE_BASE/90__KB_TAGS.md | TAGS:[kb,tags] | NOTE:tag vocabulary + rules

### E) KB Entity Passports (objects)
# (пока пусто — появится, когда начнём заводить KB-сущности)
# формат тот же: UID | KB_ENTITY | STATUS | LOCK | VERSION | PATH | TAGS:[...] | NOTE:...

---

## 5) NON-CANON NOTE (ALIASES)
Файлы-алиасы (если существуют) здесь не регистрируются как канон.
Если они нужны — они должны быть явно помечены non-canon и служить только указателями.

---

## FINAL RULE (LOCK)
Этот реестр — SoT по учёту KB-артефактов (UID/версии/статусы).
Existence rule задаёт только master-index KB.
LOCK: FIXED
--- END.
