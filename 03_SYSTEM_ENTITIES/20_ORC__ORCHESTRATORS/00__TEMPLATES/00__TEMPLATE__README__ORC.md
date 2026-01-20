# ORC FAMILY — README TEMPLATE

FILE: 03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/00__TEMPLATES/00__TEMPLATE__README__ORC.md
SCOPE: Universe Engine (Games volume) / Orchestrators (ORC) / Family README template
SERIAL: C425-B513
LAYER: 03_SYSTEM_ENTITIES
DOC_TYPE: TEMPLATE
ENTITY_GROUP: ORCHESTRATORS (ORC)
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.1.0
UID: UE.GAMES.TPL.ORC.FAMILY_README.001
OWNER: SYSTEM
ROLE: Canonical README template for an ORC family folder (purpose, boundaries, included orchestrators, default pipeline shape).

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: MINOR
- SUMMARY: "DOC CONTROL alignment + explicit RAW-only interfaces + KB scope section."
- REASON: "Keep family readmes consistent and compatible with runtime navigation."
- IMPACT: "ORC families become auditable, predictable to use."
- CHANGE_ID: UE.CHG.2026-01-20.ORC.TPL.FAMREADME.001

---

## 0) FAMILY PURPOSE (REQUIRED)
Коротко:
- зачем это семейство существует
- какие типы задач маршрутизирует
- какие типы выходов обслуживает (PRJ/OUT/AST/LOG)

## 1) INCLUDED ORCHESTRATORS (REQUIRED)
Строго по номеру:
- 01 — <name> — RAW: <...>
- 02 — <name> — RAW: <...>

## 2) BOUNDARIES (MANDATORY)
### ORC DOES
- маршрутизация
- порядок шагов
- handoff targets
- checkpoints (CTL/VAL/QA gates)

### ORC DOES NOT
- доменные решения (SPC/ENG)
- формальная валидация (VAL)
- quality/естественность (QA)
- политики/лимиты (CTL)
- хранение контента как SoT

## 3) DEFAULT PIPELINE SHAPE (OPTIONAL)
Если в семействе есть типовой маршрут, опиши:
- CONSUMES:
- PRODUCES:
- TYPICAL GATES:
- DEFAULT HANDOFF:

## 4) KNOWLEDGE BASE (KB) SCOPE
KB INPUTS:
- какие стандарты/законы обычно нужны при использовании этого семейства

KB OUTPUTS:
- none (обычно)

BOUNDARIES:
- семейство не создаёт KB модули, только маршрутизирует

## 5) INTERFACES (RAW ONLY)
- ORC Realm:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/00__README__ORC_REALM.md
- ORC Rules:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/01__RULES__ORC.md
- ORC Registry (SoT):
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/02__INDEX_ALL_ORCHESTRATORS.md
