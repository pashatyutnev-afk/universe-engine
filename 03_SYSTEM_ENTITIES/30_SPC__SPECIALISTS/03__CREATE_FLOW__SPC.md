# SPC CREATE FLOW — CANON

FILE: 03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/03__CREATE_FLOW__SPC.md
SCOPE: Universe Engine (Games volume) / System Entities / Specialists (SPC)
SERIAL: C425-B513
LAYER: 03_SYSTEM_ENTITIES
DOC_TYPE: WORKFLOW
ENTITY_GROUP: SPECIALISTS (SPC)
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.1.0
UID: UE.SPC.CREATE_FLOW.001
OWNER: SYSTEM
ROLE: Canonical creation workflow for a new SPC entity: family → UID → file → registry entry → readiness.

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: MINOR
- SUMMARY: "Hardened SPC create flow: registry-first discipline, mini-contract requirement, output artifact law, RAW-only interfaces."
- REASON: "Avoid non-registered specialists and incomplete SPC files."
- IMPACT: "SPC creation becomes deterministic and auditable."
- CHANGE_ID: UE.CHG.2026-01-20.SPC.CREATEFLOW.001

---

## 0) CORE LAW
SPC существует в каноне только если:
1) создан файл SPC по template
2) добавлен RAW link в `02__INDEX_ALL_SPECIALISTS.md`

---

## 1) STEPS (CANON ORDER)
1) Select FAMILY:
- выбрать папку семейства внутри `30_SPC__SPECIALISTS/` (или создать новую по правилам слоя)

2) Assign UID:
- назначить UID по UID rules

3) Create SPC file:
- использовать `00__TEMPLATE__SPC_ENTITY.md`
- заполнить: purpose + boundaries + mini-contract + interfaces

4) Define outputs:
- SPC обязан указать типы артефактов, которые он упаковывает (PRODUCES)

5) Register in SPC Global Registry (SoT):
- добавить в правильный раздел
- соблюсти порядок/номер, если семейство нумеруется

6) Readiness check:
- SPC должен быть пригоден для routing (внятный scope + зависимости)

7) If canon-impacting:
- изменения фиксировать через change management + audit

---

## 2) STOP CONDITIONS (ONLY THESE)
- RAW missing (нет ссылки на registry/template)
- marker not confirmed (mini-contract/границы/шаблон не заполнены)
- input absent (нет выбранного family или UID)

---

## 3) INTERFACES (RAW ONLY)
- SPC GLOBAL REGISTRY (SoT):
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/02__INDEX_ALL_SPECIALISTS.md
- SPC RULESET:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/01__RULES__SPC.md
- SPC ENTITY TEMPLATE:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/00__TEMPLATES/00__TEMPLATE__SPC_ENTITY.md

--- END.
