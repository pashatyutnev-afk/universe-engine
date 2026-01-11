# REG REGISTRIES INDEX — GLOBAL REGISTRY (CANON)
CANON FILE: 03_SYSTEM_ENTITIES/00_REG__REGISTRIES/00__INDEX_ALL_REGISTRIES

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: REGISTRIES (REG)
DOC_TYPE: INDEX
INDEX_TYPE: GLOBAL_REGISTRY_INDEX
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.REG.IDX.ALL.001
OWNER: SYSTEM
ROLE: Canonical navigation law + existence registry for all REG registries (RAW-ONLY NAV)

CHANGE_NOTE:
- DATE: 2026-01-11
- TYPE: PATCH
- SUMMARY: "Rebuilt REG index in canon format: RAW-only nav, strict existence rule, authority order, alias rule."
- REASON: "REG layer requires deterministic navigation and strict existence enforcement."
- IMPACT: "REG registries become deterministic and audit-compatible."
- CHANGE_ID: UE.CHG.2026-01-11.REG.IDX.ALL.001

---

## 0) PURPOSE (LAW)
Этот INDEX — единая точка истины для NAV/EXISTENCE папки:
`03_SYSTEM_ENTITIES/00_REG__REGISTRIES/`

Он фиксирует:
- какие REG реестры существуют
- строгий порядок реестров
- RAW-only навигацию (PATH — метка, не механизм)
- анти-дубли entrypoint/индексов

---

## 1) EXISTENCE RULE (ABSOLUTE)
- Если реестра нет в CANON MAP ниже — он **не существует** для слоя REG.
- Если файл существует в папке, но не зарегистрирован здесь — **NON-CANON / ignored**.
- NAV работает **только по RAW ссылкам**.

---

## 2) ORDER OF AUTHORITY (REG)
1) `00__README_REGISTRIES` (realm / смысл / рамки)
2) `00__INDEX_ALL_REGISTRIES` (NAV/EXISTENCE SoT)
3) `02__REG_NAMING_RULES` (правила именования)
4) `01__REG_ENTITY_IDS` (ID/UID namespaces)
5) `03__REG_PATH_MAP` (карта путей)
6) `00__TEMPLATE_REGISTRY` (шаблон реестра)
7) `90__REG_CHANGELOG` (история изменений)
8) `91__REG_DEPRECATION` (вывод из канона / deprecations)

---

## 3) BASE PATH
PATH: `03_SYSTEM_ENTITIES/00_REG__REGISTRIES/`

---

## 4) HOW TO USE (ROADMAP)
1) Открываешь `00__README_REGISTRIES` — рамки слоя REG.
2) По этому INDEX выбираешь нужный реестр (IDs / Naming / Path Map).
3) Любые изменения реестров:
   - обязаны сохранять RAW-only навигацию,
   - обязаны фиксироваться в `90__REG_CHANGELOG`,
   - не должны создавать дублей entrypoint.

---

# CANON MAP — 00_REG__REGISTRIES (RAW-ONLY NAV)

00 — README: REG Realm  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/00_REG__REGISTRIES/00__README_REGISTRIES

01 — TEMPLATE: REG Registry Document  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/00_REG__REGISTRIES/00__TEMPLATE_REGISTRY

02 — REGISTRY: Entity IDs / UID Namespaces  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/00_REG__REGISTRIES/01__REG_ENTITY_IDS

03 — REGISTRY: Naming Rules (REG Layer)  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/00_REG__REGISTRIES/02__REG_NAMING_RULES

04 — REGISTRY: Path Map (REG Layer)  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/00_REG__REGISTRIES/03__REG_PATH_MAP

90 — REG ChangeLog  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/00_REG__REGISTRIES/90__REG_CHANGELOG

91 — REG Deprecation Registry  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/00_REG__REGISTRIES/91__REG_DEPRECATION

---

## 5) ALIAS RULE (STRICT)
Любые дубли entrypoint/индексов в этой папке (например `INDEX*`, `*REGISTRIES_INDEX*`)
кроме CANON FILE выше должны быть либо удалены, либо превращены в чистый POINTER на:
`03_SYSTEM_ENTITIES/00_REG__REGISTRIES/00__INDEX_ALL_REGISTRIES`

---

## FINAL RULE (LOCK)
Этот INDEX — единственная точка истины о составе и порядке REG-реестров.  
Любая правка структуры/ссылок обязана фиксироваться в `90__REG_CHANGELOG`.

OWNER: SYSTEM  
LOCK: FIXED

--- END.
