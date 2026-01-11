# TPL TEMPLATES INDEX — GLOBAL REGISTRY (CANON)
CANON FILE: 03_SYSTEM_ENTITIES/01_TPL__TEMPLATES/00__INDEX_ALL_TEMPLATES

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: TEMPLATES (TPL)
DOC_TYPE: INDEX
INDEX_TYPE: GLOBAL_TEMPLATE_REGISTRY
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.TPL.IDX.ALL.001
OWNER: SYSTEM
ROLE: Canonical navigation law + existence registry for all system entity templates (RAW-ONLY NAV)

CHANGE_NOTE:
- DATE: 2026-01-11
- TYPE: PATCH
- SUMMARY: "Rebuilt TPL templates index as executable registry: RAW-only nav, strict existence rule, authority order, alias rule."
- REASON: "Templates layer requires deterministic navigation and strict existence enforcement."
- IMPACT: "TPL templates become audit-compatible and stable."
- CHANGE_ID: UE.CHG.2026-01-11.TPL.IDX.ALL.001

---

## 0) PURPOSE (LAW)
Этот INDEX — единая точка истины для NAV/EXISTENCE папки:
`03_SYSTEM_ENTITIES/01_TPL__TEMPLATES/`

Он фиксирует:
- какие шаблоны существуют
- строгий порядок шаблонов
- RAW-only навигацию (PATH — метка, не механизм)
- анти-дубли entrypoint/индексов

---

## 1) EXISTENCE RULE (ABSOLUTE)
- Если шаблона нет в CANON MAP ниже — он **не существует** для слоя TPL.
- Если файл существует в папке, но не зарегистрирован здесь — **NON-CANON / ignored**.
- NAV работает **только по RAW ссылкам**.

---

## 2) BASE PATH
PATH: `03_SYSTEM_ENTITIES/01_TPL__TEMPLATES/`

---

## 3) ORDER OF AUTHORITY (TPL)
1) `00__README_TEMPLATES` (realm / рамки / смысл)
2) `00__INDEX_ALL_TEMPLATES` (NAV/EXISTENCE SoT)
3) `00__TEMPLATE_SYSTEM_STANDARD` (общий стандарт шаблонов)
4) `10__TPL__ENGINE` (шаблон движка)
5) `20__TPL__ORCHESTRATOR` (шаблон оркестратора)
6) `30__TPL__SPECIALIST` (шаблон специалиста)
7) `40__TPL__CONTROLLER` (шаблон контроллера)
8) `50__TPL__VALIDATOR` (шаблон валидатора)
9) `60__TPL__QA` (шаблон QA)
10) `90__TPL__INDEX` (шаблон индекса)
11) `91__TPL__README_REALM` (шаблон realm/readme)

---

# CANON MAP — 01_TPL__TEMPLATES (RAW-ONLY NAV)

00 — README: Templates Realm  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/01_TPL__TEMPLATES/00__README_TEMPLATES.md

01 — TEMPLATE STANDARD: System Template Standard  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/01_TPL__TEMPLATES/00__TEMPLATE_SYSTEM_STANDARD.md

10 — TEMPLATE: ENG Engine  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/01_TPL__TEMPLATES/10__TPL__ENGINE.md

20 — TEMPLATE: ORC Orchestrator  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/01_TPL__TEMPLATES/20__TPL__ORCHESTRATOR.md

30 — TEMPLATE: SPC Specialist  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/01_TPL__TEMPLATES/30__TPL__SPECIALIST.md

40 — TEMPLATE: CTL Controller  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/01_TPL__TEMPLATES/40__TPL__CONTROLLER.md

50 — TEMPLATE: VAL Validator  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/01_TPL__TEMPLATES/50__TPL__VALIDATOR.md

60 — TEMPLATE: QA Quality  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/01_TPL__TEMPLATES/60__TPL__QA.md

90 — TEMPLATE: INDEX  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/01_TPL__TEMPLATES/90__TPL__INDEX.md

91 — TEMPLATE: README REALM  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/01_TPL__TEMPLATES/91__TPL__README_REALM.md

---

## 4) ALIAS RULE (STRICT)
Любые дубли entrypoint/индексов в этой папке (например `INDEX*`, `*TEMPLATES_INDEX*`)
кроме CANON FILE выше должны быть либо удалены, либо превращены в чистый POINTER на:
`03_SYSTEM_ENTITIES/01_TPL__TEMPLATES/00__INDEX_ALL_TEMPLATES`

---

## FINAL RULE (LOCK)
Этот INDEX — единственная точка истины о составе и порядке шаблонов TPL.  
Любая правка структуры/ссылок должна фиксироваться через governance pipeline.

OWNER: SYSTEM
LOCK: FIXED

--- END.
