# UNIVERSE ENGINE — MASTER INDEX (GLOBAL MAP)
FILE: 02_STANDARDS/00__MASTER_INDEX__UNIVERSE_ENGINE.md

SCOPE: Universe Engine / Global Navigation
LEVEL: L0
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0
OWNER: SYSTEM
ROLE: Единственная точка входа в систему. Карта всех реестров, слоёв, законов и путей навигации.

---

## 0) PURPOSE (LAW)
Этот файл определяет:
- где лежат реестры (SoT) системы
- как система “существует” через регистрацию
- как человек и чат навигируют без путаницы

---

## 1) EXISTENCE LAW (ABSOLUTE)
> Если элемента нет в соответствующем реестре — он не существует в системе.  
> Файл без регистрации считается NON-CANON / ignored.

---

## 2) ONE ID LAW
Единственный язык идентификации системы — UID.

UID FORMAT:
`UE.<GLOBAL>.<CATEGORY>.<FAMILY>.<NAME>`

SoT:
- `02_STANDARDS/01_SPECIFICATIONS/UID_AND_MARKING_SPEC.md`

---

## 3) SYSTEM LAYERS (GLOBAL)
Система разделена на логические слои (GLOBAL):

- STD — Standards (законы/спеки/протоколы)
- ENT — System Entities (ENG/ORC/SPC/CTL/VAL/QA)
- KB  — Knowledge Base (персонажи/места/объекты/события/правила)
- PRJ — Projects (PACK/EP/SCENE/SHOT)
- AST — Assets (IMG/AUD/VID/PRM/REF)
- OUT — Output (STACK/SCRIPT/AUDIO/VIDEO/IMAGE)
- LOG — Logs/Audit (по желанию, позже)

---

## 4) SOURCE OF TRUTH — REGISTRIES (PRIMARY)
### 4.1 Standards (STD)
- UID Law: `02_STANDARDS/01_SPECIFICATIONS/UID_AND_MARKING_SPEC.md`
- Marking Modules (если используются): `02_STANDARDS/06_MARKING_STANDARDS/`
- MASTER INDEX (этот файл): `02_STANDARDS/00__MASTER_INDEX__UNIVERSE_ENGINE.md`

### 4.2 Entities (ENT)
ENG Engines registry:
- `03_SYSTEM_ENTITIES/10_ENG__ENGINES/02__INDEX_ALL_ENGINES.md`
(и аналогично будут ORC/SPC/CTL/VAL/QA реестры)

### 4.3 Knowledge Base (KB)
- KB Realm: `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/00__README__KB_REALM.md`
- KB Rules: `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/01__RULES__KB.md`
- KB Global Registry (SoT): `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/02__INDEX__KB_GLOBAL_REGISTRY.md`
- KB Types: `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/03__INDEX__KB_ENTITY_TYPES.md`
- KB Storage Map: `04_KNOWLEDGE_BASE/00_KB_GOVERNANCE/04__KB_STORAGE_MAP.md`

### 4.4 Projects (PRJ)
- PRJ Realm: `05_PROJECTS/00_PRJ_GOVERNANCE/00__README__PRJ_REALM.md`
- PRJ Rules: `05_PROJECTS/00_PRJ_GOVERNANCE/01__RULES__PRJ.md`
- PRJ Global Registry (SoT): `05_PROJECTS/00_PRJ_GOVERNANCE/02__INDEX__PRJ_GLOBAL_REGISTRY.md`
- PRJ Types: `05_PROJECTS/00_PRJ_GOVERNANCE/03__INDEX__PRJ_ENTITY_TYPES.md`
- PRJ Storage Map: `05_PROJECTS/00_PRJ_GOVERNANCE/04__PRJ_STORAGE_MAP.md`
- Scene Link Law: `05_PROJECTS/00_PRJ_GOVERNANCE/05__SCENE_LINK_LAW.md`
- PRJ Create Flow: `05_PROJECTS/00_PRJ_GOVERNANCE/07__PRJ_CREATE_FLOW.md`

### 4.5 Assets (AST)
- AST Realm: `07_ASSETS/00_AST_GOVERNANCE/00__README__AST_REALM.md`
- AST Rules: `07_ASSETS/00_AST_GOVERNANCE/01__RULES__AST.md`
- AST Global Registry (SoT): `07_ASSETS/00_AST_GOVERNANCE/02__INDEX__AST_GLOBAL_REGISTRY.md`
- AST Types: `07_ASSETS/00_AST_GOVERNANCE/03__INDEX__AST_ENTITY_TYPES.md`
- AST Storage Map: `07_ASSETS/00_AST_GOVERNANCE/04__AST_STORAGE_MAP.md`
- AST Create Flow: `07_ASSETS/00_AST_GOVERNANCE/06__AST_CREATE_FLOW.md`

### 4.6 Output (OUT)
- OUT Realm: `06_OUTPUT/00_OUT_GOVERNANCE/00__README__OUT_REALM.md`
- OUT Global Registry (SoT): `06_OUTPUT/00_OUT_GOVERNANCE/01__INDEX__OUT_GLOBAL_REGISTRY.md`
- OUT Types: `06_OUTPUT/00_OUT_GOVERNANCE/02__INDEX__OUT_ENTITY_TYPES.md`
- OUT Storage Map: `06_OUTPUT/00_OUT_GOVERNANCE/03__OUT_STORAGE_MAP.md`
- OUT Create Flow: `06_OUTPUT/00_OUT_GOVERNANCE/05__OUT_CREATE_FLOW.md`

---

## 5) NAVIGATION FLOW (HOW TO USE)
### 5.1 Если строим мир/логику/персонажей
→ KB (создать сущность) → зарегистрировать в KB Registry → ссылаться из PRJ/OUT

### 5.2 Если делаем производство эпизода/сцены
→ PRJ (PACK/EP/SCENE) → зарегистрировать в PRJ Registry  
→ создать STACK в OUT → зарегистрировать в OUT Registry  
→ привязать STACK_REF обратно в SCENE паспорт  
→ использовать AST как кирпичи (media/prompt/ref)

---

## 6) CONFLICT RULE (ANTI-CHAOS)
Если два файла претендуют на одну истину:
- истина = реестр (SoT)
- всё остальное = производные/копии/представления

---

## 7) FINAL LOCK
> MASTER INDEX — главный вход и карта системы.  
> Любая правка структуры реестров = изменение канона.

---
END.
