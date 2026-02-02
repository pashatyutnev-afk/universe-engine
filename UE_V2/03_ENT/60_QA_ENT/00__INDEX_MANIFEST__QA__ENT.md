# QA QUALITY INDEX — GLOBAL REGISTRY (CANON ROADMAP)
CANON FILE: 03_SYSTEM_ENTITIES/60_QA__QUALITY/02__INDEX_ALL_QA.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: QUALITY (QA)
DOC_TYPE: INDEX
INDEX_TYPE: GLOBAL_QA_REGISTRY
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.QA.IDX.ALL.001
OWNER: SYSTEM
ROLE: Canonical navigation law + existence registry for all QA families and QA checks (RAW-ONLY NAV)

CHANGE_NOTE:
- DATE: 2026-01-11
- TYPE: MAJOR
- SUMMARY: "Rebuilt QA global index to match actual folder structure; RAW-only navigation; registered Music QA checks 01..09 and templates set."
- REASON: "QA layer must be deterministic for music system: viral UX gates, recognition tests, regression guards."
- IMPACT: "QA becomes canon-visible and audit-compatible; unregistered QA checks are NON-CANON."
- CHANGE_ID: UE.CHG.2026-01-11.QA.IDX.ALL.001

---

## ROOT FILES (QA LAYER) — RAW ONLY
00 — QA Layer Realm (README)  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/60_QA__QUALITY/00__README__QA_REALM.md

01 — QA Layer Rules (Ruleset)  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/60_QA__QUALITY/01__RULES__QA.md

02 — QA INDEX_ALL_QA (THIS FILE)  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/60_QA__QUALITY/02__INDEX_ALL_QA.md

03 — QA Create Flow  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/60_QA__QUALITY/03__CREATE_FLOW__QA.md

---

## 0) PURPOSE (LAW)
Этот INDEX — единая точка истины для NAV/EXISTENCE слоя `60_QA__QUALITY`.

Он фиксирует:
- состав папок (семейств) внутри `03_SYSTEM_ENTITIES/60_QA__QUALITY/`
- строгий порядок QA-checks внутри каждого семейства
- RAW-only навигацию

---

## 1) EXISTENCE RULE (ABSOLUTE)
- Если файла/README/Template нет в CANON MAP ниже — он **не существует** для слоя QA.
- Если файл есть в репо, но не зарегистрирован здесь — **NON-CANON / ignored**.
- NAV работает **только по RAW** ссылкам.

---

## 2) BASE PATH
PATH: `03_SYSTEM_ENTITIES/60_QA__QUALITY/`

---

## 3) HOW TO USE (ROADMAP)
1) Выбираешь FAMILY (папку) по задаче.
2) Открываешь `00__README__...` этой FAMILY — рамки, роль и границы.
3) Внутри FAMILY идёшь по QA-checks строго по номеру.
4) Новый QA-check:
   - сначала регистрируется здесь (FAMILY + номер),
   - затем создаётся файл,
   - затем обновляется README семьи (если нужно).

---

## 4) FAMILY BLOCK STANDARD (MANDATORY)
Каждое семейство обязано иметь единый блок:
1) `## <FAMILY_NAME>`
2) `REALM FILE:` (RAW)
3) `Family Path:`
4) `TEMPLATES:` (если применимо)
5) список QA-checks по номерам (RAW)

---

# CANON MAP — 60_QA__QUALITY (RAW-ONLY NAV)

---

## 00__TEMPLATES
REALM FILE:
- (Templates folder; realm is implied by templates themselves)

Family Path: `00__TEMPLATES/`

00 — TEMPLATE: QA CHECK  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/60_QA__QUALITY/00__TEMPLATES/00__TEMPLATE__QA_CHECK.md

01 — TEMPLATE: QA ENTITY  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/60_QA__QUALITY/00__TEMPLATES/00__TEMPLATE__QA_ENTITY.md

02 — TEMPLATE: QA ISSUE  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/60_QA__QUALITY/00__TEMPLATES/00__TEMPLATE__QA_ISSUE.md

---

## 10_MUSIC_QA
REALM FILE:
- 00 — README: MUSIC QA  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/60_QA__QUALITY/10_MUSIC_QA/00__README__MUSIC_QA.md

Family Path: `10_MUSIC_QA/`

01 — SCROLL STOP 5S  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/60_QA__QUALITY/10_MUSIC_QA/01__SCROLL_STOP_5S_QA.md

02 — LOOP 15S  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/60_QA__QUALITY/10_MUSIC_QA/02__LOOP_15S_QA.md

03 — RECOGNITION 10S  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/60_QA__QUALITY/10_MUSIC_QA/03__RECOGNITION_10S_QA.md

04 — CREATOR PANEL  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/60_QA__QUALITY/10_MUSIC_QA/04__CREATOR_PANEL_QA.md

05 — MIX TRANSLATION  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/60_QA__QUALITY/10_MUSIC_QA/05__MIX_TRANSLATION_QA.md

06 — HOOK PANEL  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/60_QA__QUALITY/10_MUSIC_QA/06__HOOK_PANEL_QA.md

07 — CATALOG DIFFERENTIATION  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/60_QA__QUALITY/10_MUSIC_QA/07__CATALOG_DIFFERENTIATION_QA.md

08 — VOICE DIVERSITY AUDIT  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/60_QA__QUALITY/10_MUSIC_QA/08__VOICE_DIVERSITY_AUDIT_QA.md

09 — REGRESSION GUARD  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/60_QA__QUALITY/10_MUSIC_QA/09__REGRESSION_GUARD_QA.md

---

## 99) ALIAS RULE (STRICT)
Любые дубли entrypoint/индекса вида:
- `03_SYSTEM_ENTITIES/60_QA__QUALITY/00__INDEX_ALL_QA.md`
- любые другие `*INDEX*_QA*`, кроме CANON FILE выше
должны быть либо удалены, либо превращены в чистый POINTER на:
`03_SYSTEM_ENTITIES/60_QA__QUALITY/02__INDEX_ALL_QA.md`

---

## FINAL RULE (LOCK)
Этот INDEX — единственная точка истины о составе и порядке QA-checks.  
Любая правка структуры/порядка должна фиксироваться как изменение канона слоя QA.

OWNER: SYSTEM  
LOCK: FIXED

--- END.
