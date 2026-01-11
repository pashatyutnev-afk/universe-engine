# VAL VALIDATORS INDEX — GLOBAL REGISTRY (CANON ROADMAP)
CANON FILE: 03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/02__INDEX_ALL_VALIDATORS.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: VALIDATORS (VAL)
DOC_TYPE: INDEX
INDEX_TYPE: GLOBAL_VALIDATOR_REGISTRY
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.VAL.IDX.ALL.001
OWNER: SYSTEM
ROLE: Canonical navigation law + existence registry for all VAL validator families and instances (RAW-ONLY NAV)

CHANGE_NOTE:
- DATE: 2026-01-11
- TYPE: MAJOR
- SUMMARY: "Rebuilt VAL global index to match actual folder structure; RAW-only navigation; registered Music Validators 01..10 and Validation Engines 01..06."
- REASON: "VAL layer must be deterministic for music system rollout: legality, UGC readiness, collisions, prompt fidelity, credits/rights."
- IMPACT: "VAL layer becomes canon-visible and audit-compatible; unregistered validators are NON-CANON."
- CHANGE_ID: UE.CHG.2026-01-11.VAL.IDX.ALL.001

---

## ROOT FILES (VAL LAYER) — RAW ONLY
00 — VAL Layer Realm (README)  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/00__README__VALIDATORS_REALM.md

01 — VAL Layer Rules (Ruleset)  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/01__RULES__VAL.md

02 — VAL INDEX_ALL_VALIDATORS (THIS FILE)  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/02__INDEX_ALL_VALIDATORS.md

03 — VAL Create Flow  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/03__CREATE_FLOW__VAL.md

---

## 0) PURPOSE (LAW)
Этот INDEX — единая точка истины для NAV/EXISTENCE слоя `50_VAL__VALIDATORS`.

Он фиксирует:
- состав папок (семейств) внутри `03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/`
- строгий порядок валидаторов внутри каждого семейства
- RAW-only навигацию

---

## 1) EXISTENCE RULE (ABSOLUTE)
- Если файла/README/Template нет в CANON MAP ниже — он **не существует** для слоя VAL.
- Если файл есть в репо, но не зарегистрирован здесь — **NON-CANON / ignored**.
- NAV работает **только по RAW** ссылкам.

---

## 2) BASE PATH
PATH: `03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/`

---

## 3) HOW TO USE (ROADMAP)
1) Выбираешь FAMILY (папку) по задаче.
2) Открываешь `00__README__...` этой FAMILY — рамки, роль и границы.
3) Внутри FAMILY идёшь по валидаторам строго по номеру.
4) Новый валидатор:
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
5) список валидаторов по номерам (RAW)

---

# CANON MAP — 50_VAL__VALIDATORS (RAW-ONLY NAV)

---

## 00__TEMPLATES
REALM FILE:
- (Templates folder; realm is implied by templates themselves)

Family Path: `00__TEMPLATES/`

00 — TEMPLATE: VAL ENTITY  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/00__TEMPLATES/00__TEMPLATE__VAL_ENTITY.md

01 — TEMPLATE: VAL VIOLATION  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/00__TEMPLATES/00__TEMPLATE__VAL_VIOLATION.md

---

## 10_MUSIC_VALIDATORS
REALM FILE:
- 00 — README: MUSIC VALIDATORS  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/00__README__MUSIC_VALIDATORS.md

Family Path: `10_MUSIC_VALIDATORS/`

01 — HOOK TIMING  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/01__HOOK_TIMING_VAL.md

02 — UGC READY  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/02__UGC_READY_VAL.md

03 — REPEAT GUARD  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/03__REPEAT_GUARD_VAL.md

04 — PD ONLY  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/04__PD_ONLY_VAL.md

05 — COLLISION BLOCKER  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/05__COLLISION_BLOCKER_VAL.md

06 — RELEASE PACK READY  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/06__RELEASE_PACK_READY_VAL.md

07 — NAMING COLLISION  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/07__NAMING_COLLISION_VAL.md

08 — PROMPT FIDELITY  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/08__PROMPT_FIDELITY_VAL.md

09 — CREDITS RIGHTS  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/09__CREDITS_RIGHTS_VAL.md

10 — VOICE DIVERSITY  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/10__VOICE_DIVERSITY_VAL.md

---

## 11_VALIDATION_ENGINES
REALM FILE:
- 00 — README: VALIDATION ENGINES  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/11_VALIDATION_ENGINES/00__README__VALIDATION_ENGINES.md

Family Path: `11_VALIDATION_ENGINES/`

01 — ERROR DETECTION ENGINE  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/11_VALIDATION_ENGINES/01__ERROR_DETECTION_ENG.md

02 — FACT CONSISTENCY ENGINE  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/11_VALIDATION_ENGINES/02__FACT_CONSISTENCY_ENG.md

03 — LANGUAGE LINGUISTICS ENGINE  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/11_VALIDATION_ENGINES/03__LANGUAGE_LINGUISTICS_ENG.md

04 — CULTURAL ACCURACY ENGINE  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/11_VALIDATION_ENGINES/04__CULTURAL_ACCURACY_ENG.md

05 — HISTORICAL ACCURACY ENGINE  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/11_VALIDATION_ENGINES/05__HISTORICAL_ACCURACY_ENG.md

06 — SCIENTIFIC PLAUSIBILITY ENGINE  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/11_VALIDATION_ENGINES/06__SCIENTIFIC_PLAUSIBILITY_ENG.md

---

## 99) ALIAS RULE (STRICT)
Любые дубли entrypoint/индекса вида:
- `03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/00__INDEX_ALL_VALIDATORS.md`
- любые другие `*INDEX*_VALIDATORS*`, кроме CANON FILE выше
должны быть либо удалены, либо превращены в чистый POINTER на:
`03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/02__INDEX_ALL_VALIDATORS.md`

---

## FINAL RULE (LOCK)
Этот INDEX — единственная точка истины о составе и порядке VAL-валидаторов.  
Любая правка структуры/порядка должна фиксироваться как изменение канона слоя VAL.

OWNER: SYSTEM  
LOCK: FIXED

--- END.
