# SYSTEM LAW INDEX — MASTER REGISTRY (CANON)
FILE: 01_SYSTEM_LAW/00__INDEX__SYSTEM_LAW.md

SCOPE: Universe Engine
LAYER: 01_SYSTEM_LAW
DOC_TYPE: INDEX
INDEX_TYPE: MASTER_LAW_REGISTRY
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.1.1
UID: UE.DOC.IDX.LAW.MASTER
OWNER: SYSTEM
ROLE: Canonical navigation law + registry for all system-level laws (mandatory entrypoint)

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: PATCH
- SUMMARY: "Doc Control compliance: added DOC_TYPE to header; expanded layer doc-control rule (FILE+DOC_TYPE); normalized CANON MAP to PATH/RAW."
- REASON: "Убрать формальные конфликты со стандартом Doc Control и сделать индекс машиночитаемым."
- IMPACT: "Слой 01_SYSTEM_LAW полностью совместим со стандартами и валидаторами."

---

## 0) PURPOSE (LAW)
Этот INDEX — единая точка истины для слоя `01_SYSTEM_LAW`.

Он фиксирует:
- полный список LAW файлов
- строгий порядок применения (by number)
- канонические пути и raw-ссылки
- правило существования

### EXISTENCE RULE (ABSOLUTE)
Если закона нет в этом INDEX — он не существует для слоя SYSTEM LAW.
Если файл есть, но не зарегистрирован здесь — NON-CANON (ignored).

---

## 1) HOW TO USE (MANDATORY FLOW)
1) Любой спор по системе сначала сверяется с `00__SYSTEM_LAW.md`.
2) Затем открывается нужный LAW по номеру (01..07).
3) Любые новые LAW:
   - сначала добавляются в этот INDEX,
   - потом создаётся файл,
   - потом фиксируется по `03__VERSIONING_CHANGE_POLICY.md` и `04__CANON_PROTOCOL.md`.

---

## 2) ORDER OF AUTHORITY (PRIORITY)
При конфликте законов приоритет такой (строго):

0) `00__SYSTEM_LAW.md` (Core Law)
1) `04__CANON_PROTOCOL.md` (что такое канон и как он меняется)
2) `03__VERSIONING_CHANGE_POLICY.md` (как изменения фиксируются)
3) `02__UID_RULES.md` (как система идентифицирует сущности)
4) `01__NAMING_RULES.md` (как вещи называются и где живут)
5) `06__CONSTRAINTS_REGISTRY.md` (жёсткие ограничения)
6) `05__ARTIFACT_SCHEMA_REGISTRY.md` (форматы артефактов)
7) `07__PIPELINE_REGISTRY.md` (пайплайны)

---

## 3) CANON MAP — SYSTEM LAW FILES (REGISTERED)

00 — System Law (Core)
PATH: `01_SYSTEM_LAW/00__SYSTEM_LAW.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/00__SYSTEM_LAW.md

01 — Naming Rules
PATH: `01_SYSTEM_LAW/01__NAMING_RULES.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/01__NAMING_RULES.md

02 — UID Rules
PATH: `01_SYSTEM_LAW/02__UID_RULES.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/02__UID_RULES.md

03 — Versioning & Change Policy
PATH: `01_SYSTEM_LAW/03__VERSIONING_CHANGE_POLICY.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/03__VERSIONING_CHANGE_POLICY.md

04 — Canon Protocol
PATH: `01_SYSTEM_LAW/04__CANON_PROTOCOL.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/04__CANON_PROTOCOL.md

05 — Artifact Schema Registry
PATH: `01_SYSTEM_LAW/05__ARTIFACT_SCHEMA_REGISTRY.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/05__ARTIFACT_SCHEMA_REGISTRY.md

06 — Constraints Registry
PATH: `01_SYSTEM_LAW/06__CONSTRAINTS_REGISTRY.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/06__CONSTRAINTS_REGISTRY.md

07 — Pipeline Registry
PATH: `01_SYSTEM_LAW/07__PIPELINE_REGISTRY.md`
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/07__PIPELINE_REGISTRY.md

---

## 4) DOC CONTROL RULE (FOR THIS LAYER)
Каждый LAW/REGISTRY файл обязан иметь шапку (минимум):
FILE / SCOPE / LAYER / DOC_TYPE / LEVEL / STATUS / LOCK / VERSION / UID / OWNER / ROLE.

Запрещено:
- дублировать OWNER/LOCK/VERSION/STATUS отдельными строками внизу файла
- иметь “вторую истину” метаданных вне шапки

Одна истина метаданных — в шапке.

---

## FINAL RULE
Этот INDEX — единственная точка истины о составе и порядке SYSTEM LAW.
Любая правка INDEX — изменение канона и проходит `04__CANON_PROTOCOL.md`.

--- END.
