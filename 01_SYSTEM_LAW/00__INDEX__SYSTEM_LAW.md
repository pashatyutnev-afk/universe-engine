# SYSTEM LAW INDEX — MASTER REGISTRY (CANON)
FILE: 01_SYSTEM_LAW/00__INDEX__SYSTEM_LAW.md

SCOPE: Universe Engine
LAYER: 01_SYSTEM_LAW
INDEX_TYPE: MASTER_LAW_REGISTRY
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.1.0
UID: UE.DOC.IDX.LAW.MASTER
OWNER: SYSTEM
ROLE: Canonical navigation law + registry for all system-level laws (mandatory entrypoint)

CHANGE_NOTE:
- DATE: 2026-01-07
- TYPE: MINOR
- SUMMARY: "Нормализован индекс: один реестр + Doc Control поля + единый порядок authority"
- REASON: "Единая точка истины и устранение дублей/противоречий"
- IMPACT: "Навигация слоя 01_SYSTEM_LAW"

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
🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/00__SYSTEM_LAW.md

01 — Naming Rules
🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/01__NAMING_RULES.md

02 — UID Rules
🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/02__UID_RULES.md

03 — Versioning & Change Policy
🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/03__VERSIONING_CHANGE_POLICY.md

04 — Canon Protocol
🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/04__CANON_PROTOCOL.md

05 — Artifact Schema Registry
🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/05__ARTIFACT_SCHEMA_REGISTRY.md

06 — Constraints Registry
🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/06__CONSTRAINTS_REGISTRY.md

07 — Pipeline Registry
🔗 https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/07__PIPELINE_REGISTRY.md

---

## 4) DOC CONTROL RULE (FOR THIS LAYER)
Каждый LAW файл обязан иметь шапку:
SCOPE / LAYER / STATUS / LOCK / VERSION / UID / OWNER / ROLE.
Запрещено дублировать OWNER/LOCK/VERSION внизу файла отдельными строками (одна истина — в шапке).

---

## FINAL RULE (LOCK)
Этот INDEX — единственная точка истины о составе и порядке SYSTEM LAW.
Любая правка INDEX — изменение канона и проходит `04__CANON_PROTOCOL.md`.
--- END.
