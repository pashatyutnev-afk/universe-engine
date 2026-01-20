# XREF REALM — CROSSREFERENCES (CANON)

FILE: 03_SYSTEM_ENTITIES/90_XREF__CROSSREF/00__README__CROSSREF.md
SCOPE: Universe Engine (Games volume)
SERIAL: C425-B513
LAYER: 03_SYSTEM_ENTITIES
REALM: 90_XREF__CROSSREF
DOC_TYPE: README (REALM)
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.XREF.REALM.README.001
OWNER: SYSTEM
ROLE: Canonical overview for XREF: deterministic mapping between entities, pipelines, and validation gates (no guessing).

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: PATCH
- SUMMARY: "Initialized canonical XREF README with RAW-only navigation + primary map set (ENG↔ORC, ORC↔SPC, validation matrix, pipelines)."
- REASON: "Make routing and gate placement deterministic and auditable."
- IMPACT: "System can reference stable maps instead of implicit assumptions."
- CHANGE_ID: UE.CHG.2026-01-20.XREF.README.001

---

## 0) WHAT IS XREF (CROSSREF)
XREF — слой карт соответствий.
Он отвечает за детерминизм:
- какая сущность с какой взаимодействует и через что,
- какой пайплайн выбирать под intent,
- где стоят гейты (CTL/VAL/QA) и какие именно,
- как аудитить правильность маршрута.

XREF не производит контент и не заменяет:
- SPC (намерение/решения/упаковка),
- ORC (порядок шагов),
- ENG (методы),
- CTL (политики/гейты),
- VAL (проверки),
- QA (приёмка/скоринг).

---

## 1) ABSOLUTE RULES
### 1.1 RAW-only navigation
Навигация и ссылки только RAW.
Никаких угадываний путей и “примерных” ссылок.

### 1.2 Existence rule (practical)
Если карта или запись не зарегистрирована и не доступна по RAW, она считается несуществующей для рантайма.

### 1.3 Determinism first
Любая неоднозначность маршрута должна быть снята ссылкой на:
- PIPELINE MAP, и/или
- VALIDATION MATRIX, и/или
- ENG↔ORC / ORC↔SPC карты.

---

## 2) DEFAULT USE CASES
Используй XREF, когда нужно:
- выбрать пайплайн под задачу (intent → pipeline),
- определить владельца (primary SPC) и оркестратора (primary ORC),
- расставить обязательные гейты и их порядок,
- понять “какие ENG допускаются в этом ORC”,
- аудитить конфликты, недостающие сущности и недостающие гейты.

---

## 3) CANON ENTRYPOINTS (RAW)
### 3.1 XREF INDEX (registry)
00 — INDEX: CROSSREF  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/90_XREF__CROSSREF/00__INDEX__CROSSREF.md

### 3.2 Templates
00 — TEMPLATE: XREF INDEX  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/90_XREF__CROSSREF/00__TEMPLATE__XREF_INDEX.md

00 — TEMPLATE: XREF RECORD  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/90_XREF__CROSSREF/00__TEMPLATE__XREF_RECORD.md

---

## 4) PRIMARY CANON MAP SET (RAW)
Эти карты считаются базовым минимальным набором для детерминизма.

01 — MAP: ENG → ORC  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/90_XREF__CROSSREF/01__MAP__ENG_to_ORC.md

02 — MAP: ORC → SPC  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/90_XREF__CROSSREF/02__MAP__ORC_to_SPC.md

03 — MAP: VALIDATION MATRIX (where VAL/QA applies)  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/90_XREF__CROSSREF/03__MAP__VALIDATION_MATRIX.md

04 — MAP: PIPELINES (intent → pipeline selection)  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/90_XREF__CROSSREF/04__MAP__PIPELINES.md

---

## 5) HOW TO USE (SHORT PROCEDURE)
1) Определи intent задачи.
2) Открой `04__MAP__PIPELINES.md` и выбери PIPELINE_ID.
3) Из PIPELINE записи возьми:
   - PRIMARY_SPC
   - PRIMARY_ORC
   - REQUIRED_GATES ORDER
   - OUTPUT_TARGETS
4) Уточни допустимый набор сущностей через:
   - `01__MAP__ENG_to_ORC.md` (какие ENG допустимы для ORC)
   - `02__MAP__ORC_to_SPC.md` (какие SPC владеют участками пайплайна)
5) Проверь гейты через:
   - `03__MAP__VALIDATION_MATRIX.md`
6) Если чего-то не хватает:
   - фиксируй GAP,
   - создавай недостающую сущность/карту по шаблону,
   - только потом продолжай выполнение.

---

## 6) CHANGE POLICY (LOCK)
- Изменения карт и README: только PATCH + CHANGE_NOTE.
- Удаление/замена карты: только через deprecation pointer (если используется в процессе).
- README не содержит “исполняемых решений”, только навигацию и правила применения.

---  
END.
