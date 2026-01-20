# ENG CREATE FLOW — BOOTSTRAP (CANON)

FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/03__ENG_CREATE_FLOW.md
SCOPE: Universe Engine (Games volume) / System Entities / ENGINES (ENG)
SERIAL: C425-B513
LAYER: 03_SYSTEM_ENTITIES
DOC_TYPE: WORKFLOW
ENTITY_GROUP: ENGINES (ENG)
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.ENG.CREATE_FLOW.001
OWNER: SYSTEM
ROLE: Canonical creation workflow for a new ENG engine: family → UID → file → index registration → dependency visibility → gate checks.

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: MINOR
- SUMMARY: "Created canonical ENG create flow to prevent non-indexed engines and missing contracts."
- REASON: "ENG layer has rules and index, but no single creation runbook in-layer."
- IMPACT: "New engines become deterministic to create and easy to audit."
- CHANGE_ID: UE.CHG.2026-01-20.ENG.CREATEFLOW.001

---

## 0) CORE LAW
ENG engine считается существующим в каноне только если:
1) создан файл engine по template
2) добавлен RAW link в `02__INDEX_ALL_ENGINES.md`

Если (2) отсутствует → NON-CANON.

---

## 1) STEPS (CANON ORDER)
1) Select FAMILY:
- выбрать семейство движков, соответствующее задаче

2) Assign UID:
- назначить UID по UID rules

3) Create Engine File:
- использовать template (семейный или общий TPL)
- заполнить header + purpose + boundaries + mini-contract + output schemas

4) Register in ENG Global Index (SoT):
- добавить в правильный FAMILY block
- номер `NN__` в имени файла совпадает с порядком внутри FAMILY

5) Dependency visibility:
- заполнить DEPENDS_ON (или [])
- если зависимость на governance registry — добавить запись туда (если это правило применимо в текущем томе)

6) Gate check (self-check):
- G0 header
- G1 contract
- G2 boundaries
- G3 schemas
- G4 canon (index)

7) Canon-impact changes:
- если изменение влияет на канон (порядок, статусы, lock, контракты) — фиксировать через change management + audit.

---

## 2) STOP CONDITIONS (ONLY THESE)
- RAW missing (нет ссылки на нужный индекс/шаблон)
- marker not confirmed (шаги не удовлетворяют gates)
- input absent (нет task / нет выбранного family / нет UID)

---

## 3) INTERFACES (RAW ONLY)
- ENG GLOBAL REGISTRY (SoT):
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/02__INDEX_ALL_ENGINES.md
- ENG RULESET:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/01__RULES__ENGINES.md
- ENGINE TEMPLATE (global TPL):
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/01_TPL__TEMPLATES/10__TPL__ENGINE.md

--- END.
