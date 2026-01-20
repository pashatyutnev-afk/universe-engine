# SPC ENTITY — TEMPLATE (CANON)

FILE: 03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/00__TEMPLATES/00__TEMPLATE__SPC_ENTITY.md
SCOPE: Universe Engine (Games volume) / System Entities / Specialists (SPC)
SERIAL: C425-B513
LAYER: 03_SYSTEM_ENTITIES
DOC_TYPE: TEMPLATE
TEMPLATE_TYPE: SPC_ENTITY
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.1.0
UID: UE.TPL.SPC.ENTITY.001
OWNER: SYSTEM
ROLE: Canonical template to create any SPC entity file (scope + boundaries + mini-contract + packaging outputs).

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: MINOR
- SUMMARY: "Normalized template: strict mini-contract + boundaries + packaging outputs + RAW-only interfaces."
- REASON: "Prevent incomplete specialists and role contamination."
- IMPACT: "SPC creation becomes consistent across families."
- CHANGE_ID: UE.CHG.2026-01-20.TPL.SPC.ENTITY.001

---

## 0) HEADER (REQUIRED)
UID:
FAMILY:
LEVEL: L2
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
OWNER: SYSTEM
ROLE: "<one line: what this SPC owns>"

---

## 1) PURPOSE (REQUIRED)
- кратко: зачем SPC существует
- какую часть пайплайна обслуживает
- какие решения принимает

---

## 2) SCOPE & BOUNDARIES (HARD)
### 2.1 In scope
- <hard statements>

### 2.2 Out of scope
- <hard statements>

### 2.3 Collision rule
- если пересечение с другим SPC/ENG/ORC → куда маршрутизировать и где остановиться

---

## 3) MINI-CONTRACT (MANDATORY)
SPECIALIZATION_SCOPE:
- <what this SPC owns>

CONSUMES:
- <1..N concrete inputs>

PRODUCES:
- <1..N concrete artifacts/documents>

DEPENDS_ON:
- [] OR
- <explicit dependencies (uids/roles)>

OUTPUT_TARGET:
- PRJ | OUT | AST | LOG | KB (если реально создаётся KB модуль)

---

## 4) PACKAGING LAW (MANDATORY)
- SPC никогда не отдаёт голый контент
- каждый PRODUCES должен быть оформлен документом-артефактом
- если шаблон отсутствует → GAP → создать шаблон → продолжить

---

## 5) DEFAULT WORKFLOW (OPTIONAL)
1) intake
2) decision
3) packaging
4) handoff to governance chain

---

## 6) KNOWLEDGE BASE (KB) SCOPE
KB INPUTS:
- <what this SPC uses from KB>

KB OUTPUTS:
- none (unless explicitly producing KB module)

BOUNDARIES:
- SPC не хранит знания как SoT

---

## 7) INTERFACES (RAW ONLY)
- SPC GLOBAL REGISTRY (SoT):
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/02__INDEX_ALL_SPECIALISTS.md
- SPC RULESET:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/01__RULES__SPC.md
- SPC OUTPUT PACK TEMPLATE:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/30_SPC__SPECIALISTS/00__TEMPLATES/00__TEMPLATE__SPC_OUTPUT_PACK.md

--- END.
