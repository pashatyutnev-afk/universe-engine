# XREF CROSSREF INDEX — MASTER REGISTRY (CANON ROADMAP)
CANON FILE: 03_SYSTEM_ENTITIES/90_XREF__CROSSREF/00__INDEX__CROSSREF.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: CROSSREF (XREF)
DOC_TYPE: INDEX
INDEX_TYPE: MASTER_XREF_REGISTRY
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.XREF.IDX.MASTER.001
OWNER: SYSTEM
ROLE: Canonical navigation law + existence registry for all cross-layer maps and matrices (RAW-ONLY NAV)

CHANGE_NOTE:
- DATE: 2026-01-11
- TYPE: MAJOR
- SUMMARY: "Rebuilt XREF master index to match actual folder structure; RAW-only navigation; registered ENG↔ORC, ORC↔SPC, validation matrix, and pipeline map."
- REASON: "Cross-layer determinism: orchestrators must map engines, specialists, validators, and pipelines without ambiguity."
- IMPACT: "XREF layer becomes canon-visible and audit-compatible; unregistered maps are NON-CANON."
- CHANGE_ID: UE.CHG.2026-01-11.XREF.IDX.001

---

## ROOT FILES (XREF LAYER) — RAW ONLY
00 — XREF INDEX (THIS FILE)  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/90_XREF__CROSSREF/00__INDEX__CROSSREF.md

00 — XREF Realm (README)  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/90_XREF__CROSSREF/00__README__CROSSREF.md

00 — TEMPLATE: XREF INDEX  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/90_XREF__CROSSREF/00__TEMPLATE__XREF_INDEX.md

00 — TEMPLATE: XREF RECORD  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/90_XREF__CROSSREF/00__TEMPLATE__XREF_RECORD.md

---

## 0) PURPOSE (LAW)
Этот INDEX — единая точка истины для NAV/EXISTENCE слоя `90_XREF__CROSSREF`.

Он фиксирует:
- канонические карты стыков между слоями (ENG↔ORC↔SPC)
- матрицы валидаций (VAL/QA/CTL)
- карту пайплайнов (процессы/треки выполнения)
- RAW-only навигацию

---

## 1) EXISTENCE RULE (ABSOLUTE)
- Если файла/README/Template нет в CANON MAP ниже — он **не существует** для слоя XREF.
- Если файл есть в репо, но не зарегистрирован здесь — **NON-CANON / ignored**.
- NAV работает **только по RAW** (PATH — метка, не механизм навигации).

---

## 2) BASE PATH
PATH: `03_SYSTEM_ENTITIES/90_XREF__CROSSREF/`

---

## 3) HOW TO USE (ROADMAP)
1) Берёшь нужную MAP по задаче (стык слоёв / матрица валидации / пайплайн).
2) Используешь как каноническую таблицу соответствий:
   - какие ENG вызывают какие ORC
   - какие ORC требуют каких SPC
   - какие VAL/QA/CTL применяются на шаге
3) Любое новое соответствие:
   - добавляется как запись/раздел в соответствующей MAP,
   - затем фиксируется changelog (governance pipeline).

---

## 4) MAP BLOCK STANDARD (MANDATORY)
Каждая MAP обязана иметь:
- PURPOSE
- SCOPE (какие слои/семейства покрывает)
- FORMAT (таблица/правила записи)
- CANON RECORDS (детерминированные строки/таблицы)

---

# CANON MAP — 90_XREF__CROSSREF (RAW-ONLY NAV)

---

01 — MAP: ENG → ORC  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/90_XREF__CROSSREF/01__MAP__ENG_to_ORC.md

02 — MAP: ORC → SPC  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/90_XREF__CROSSREF/02__MAP__ORC_to_SPC.md

03 — MAP: VALIDATION MATRIX  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/90_XREF__CROSSREF/03__MAP__VALIDATION_MATRIX.md

04 — MAP: PIPELINES  
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/90_XREF__CROSSREF/04__MAP__PIPELINES.md

---

## 99) ALIAS RULE (STRICT)
Любые дубли entrypoint/индекса вида:
- `03_SYSTEM_ENTITIES/90_XREF__CROSSREF/01__INDEX__CROSSREF.md`
- любые другие `*INDEX*_*XREF*`, кроме CANON FILE выше
должны быть либо удалены, либо превращены в чистый POINTER на:
`03_SYSTEM_ENTITIES/90_XREF__CROSSREF/00__INDEX__CROSSREF.md`

---

## FINAL RULE (LOCK)
Этот INDEX — единственная точка истины о составе и порядке XREF карт/матриц.  
Любая правка структуры/порядка должна фиксироваться как изменение канона слоя XREF.

OWNER: SYSTEM  
LOCK: FIXED

--- END.
