# ORC ORCHESTRATORS INDEX — GLOBAL REGISTRY (CANON ROADMAP)

FILE: 03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/02__INDEX_ALL_ORCHESTRATORS.md
SCOPE: Universe Engine (Games volume)
SERIAL: C425-B513
LAYER: 03_SYSTEM_ENTITIES
DOC_TYPE: INDEX
INDEX_TYPE: GLOBAL_ORCHESTRATOR_REGISTRY
ENTITY_GROUP: ORCHESTRATORS (ORC)
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.1
UID: UE.ORC.IDX.ALL.001
OWNER: SYSTEM
ROLE: Canonical navigation law + existence registry + roadmap for all ORC orchestrator families and instances (RAW-only navigation).

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: PATCH
- SUMMARY: "DOC CONTROL header normalized; CANON MAP preserved; no content loss."
- REASON: "Make registry auditable and consistent with other realm indexes."
- IMPACT: "Registry remains SoT with stable content and improved readability."
- CHANGE_ID: UE.CHG.2026-01-20.ORC.IDX.ALL.002

---

## ROOT FILES (ORC LAYER) — RAW ONLY
00 — ORC Layer Realm (README)
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/00__README__ORC_REALM.md

01 — ORC Layer Rules (Ruleset)
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/01__RULES__ORC.md

02 — ORC INDEX_ALL_ORCHESTRATORS (THIS FILE)
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/02__INDEX_ALL_ORCHESTRATORS.md

03 — ORC Create Flow
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/03__ORC_CREATE_FLOW.md

---

## 0) PURPOSE (LAW)
Этот INDEX — единая точка истины для NAV/EXISTENCE слоя ORC.

Он фиксирует:
- список семейств (family folders) в `03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/`
- строгий порядок оркестраторов внутри семейств
- RAW-only навигацию

## 1) EXISTENCE RULE (ABSOLUTE)
- Если файла/README/Template нет в CANON MAP ниже — он не существует для ORC слоя.
- Если файл есть в репо, но не зарегистрирован здесь — NON-CANON / ignored.
- NAV работает только по RAW ссылкам.

---

## 2) BASE PATH
PATH: `03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/`

---

## 3) HOW TO USE (ROADMAP)
1) Выбираешь FAMILY (папку) по задаче.
2) Открываешь `00__README__...` этой FAMILY — рамки/роль/границы.
3) Внутри FAMILY идёшь по оркестраторам строго по номеру.
4) Новый ORC:
- сначала регистрируется здесь (FAMILY + номер),
- затем создаётся файл,
- затем фиксируются зависимости (если есть).

---

## 4) FAMILY BLOCK STANDARD (MANDATORY)
Каждое семейство обязано иметь единый блок:
1) `## `
2) `REALM FILE (RAW):`
3) `Family Path:`
4) `TEMPLATES (RAW):` (если применимо)
5) список оркестраторов по номерам (RAW)

---

## 5) QUICK NAV (FAMILY JUMP)
- [00 — Templates](#orc-family-00-templates)
- [01 — Core Orchestrators](#orc-family-01-core)
- [10 — Music Orchestrators](#orc-family-10-music)

---

# CANON MAP — ORC FAMILIES (RAW-ONLY NAV)

<a id="orc-family-00-templates"></a>
## 00__TEMPLATES
**REALM FILE (RAW):** (Templates family; realm implied by templates)  
**Family Path:** `00__TEMPLATES/`  
**TEMPLATES (RAW):**
- ORC ENTITY TEMPLATE: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/00__TEMPLATES/00__TEMPLATE__ORC_ENTITY.md
- ORC PIPELINE STEP TEMPLATE: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/00__TEMPLATES/00__TEMPLATE__ORC_PIPELINE_STEP.md
- ORC README TEMPLATE: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/00__TEMPLATES/00__TEMPLATE__README__ORC.md

---

<a id="orc-family-01-core"></a>
## 01_CORE_ORCHESTRATORS
**REALM FILE (RAW):**
https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/01_CORE_ORCHESTRATORS/00__README__ORCHESTRATORS.md

**Family Path:** `01_CORE_ORCHESTRATORS/`

01 — Narrative Orchestrator  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/01_CORE_ORCHESTRATORS/01__NARRATIVE_ORCHESTRATOR_ORC.md

02 — Character Orchestrator  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/01_CORE_ORCHESTRATORS/02__CHARACTER_ORCHESTRATOR_ORC.md

03 — World Orchestrator  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/01_CORE_ORCHESTRATORS/03__WORLD_ORCHESTRATOR_ORC.md

04 — Production Orchestrator  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/01_CORE_ORCHESTRATORS/04__PRODUCTION_ORCHESTRATOR_ORC.md

05 — Pipeline Orchestrator  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/01_CORE_ORCHESTRATORS/05__PIPELINE_ORCHESTRATOR_ORC.md

---

<a id="orc-family-10-music"></a>
## 10_MUSIC_ORCHESTRATORS
**REALM FILE (RAW):**
https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/00__README__MUSIC_ORCHESTRATORS.md

**Family Path:** `10_MUSIC_ORCHESTRATORS/`

01 — Group to Album Orchestrator  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/01__GROUP_TO_ALBUM_ORC.md

02 — Album to Track Orchestrator  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/02__ALBUM_TO_TRACK_ORC.md

03 — Track Test + Doc Gate Orchestrator  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/03__TRACK_TEST_DOC_GATE_ORC.md

04 — Release Pack Orchestrator  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/04__RELEASE_PACK_ORC.md

05 — Portfolio Planner Orchestrator  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/05__PORTFOLIO_PLANNER_ORC.md

06 — Poet Pack Orchestrator  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/06__POET_PACK_ORC.md

---

## 99) ALIAS RULE (STRICT)
Любые дубли entrypoint/индекса вида:
- `03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/00__INDEX_ALL_ORCHESTRATORS.md`
- любые другие `*INDEX*_ORCHESTRATORS*`, кроме CANON FILE выше
должны быть либо удалены, либо превращены в чистый POINTER на:
`03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/02__INDEX_ALL_ORCHESTRATORS.md`

---

## FINAL RULE (LOCK)
Этот INDEX — единственная точка истины о составе и порядке ORC-оркестраторов.
Любая правка структуры/порядка должна фиксироваться как изменение канона слоя ORC.

OWNER: SYSTEM
LOCK: FIXED

--- END.
