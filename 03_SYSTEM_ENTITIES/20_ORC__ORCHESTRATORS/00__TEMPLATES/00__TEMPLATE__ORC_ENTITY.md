# ORC ENTITY — TEMPLATE

FILE: 03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/00__TEMPLATES/00__TEMPLATE__ORC_ENTITY.md
SCOPE: Universe Engine (Games volume) / Orchestrators (ORC) / Template
SERIAL: C425-B513
LAYER: 03_SYSTEM_ENTITIES
DOC_TYPE: TEMPLATE
ENTITY_GROUP: ORCHESTRATORS (ORC)
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.1.0
UID: UE.GAMES.TPL.ORC.ENTITY.001
OWNER: SYSTEM
ROLE: Canonical template for an ORC orchestrator entity (contract + ordered pipeline steps + gates + handoffs).

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: MINOR
- SUMMARY: "DOC CONTROL alignment + normalized mandatory sections + hardened step schema reference + RAW-only interfaces."
- REASON: "Prevent incomplete ORC files and mixed schemas."
- IMPACT: "ORC entities become consistently usable by runtime routing."
- CHANGE_ID: UE.CHG.2026-01-20.ORC.TPL.ENTITY.001

---

## 0) HEADER (REQUIRED)
UID:
FAMILY:
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
OWNER: SYSTEM
ROLE: "<one line: what this ORC orchestrates>"

## 1) PURPOSE (REQUIRED)
- что именно оркестрируется
- какие типы задач/артефактов обслуживает
- где ожидается handoff (PRJ/OUT/AST/LOG)

## 2) MINI-CONTRACT (MANDATORY)
CONSUMES:
- []

PRODUCES:
- []

DEPENDS_ON:
- []

OUTPUT_TARGET:
- PRJ | OUT | AST | LOG

## 3) PIPELINE (MANDATORY)
### 3.1 Pipeline intent
- коротко: “какой маршрут” и “какие gates обязательны”

### 3.2 STEPS (ordered)
Используй формат шага из `00__TEMPLATE__ORC_PIPELINE_STEP.md`.

Пример каркаса:

- STEP:
  - STEP_ID: 01
  - NAME:
  - EXECUTOR_UID:
  - CONSUMES: []
  - PRODUCES: []
  - GATE: NONE
  - FAIL_SEVERITY: S0
  - HANDOFF_TARGET: NONE
  - NOTES: ""

- STEP:
  - STEP_ID: 02
  - NAME:
  - EXECUTOR_UID:
  - CONSUMES: []
  - PRODUCES: []
  - GATE: CTL+VAL+QA
  - FAIL_SEVERITY: S0
  - HANDOFF_TARGET: PRJ
  - NOTES: ""

(добавляй шаги по аналогии)

## 4) CHECKPOINTS (REQUIRED)
- CHECKPOINT_01: "<where CTL must enforce>"
- CHECKPOINT_02: "<where VAL must validate>"
- CHECKPOINT_03: "<where QA must accept>"
(если не применимо, явно укажи NONE)

## 5) HANDOFF POLICY (REQUIRED)
- INTERMEDIATE HANDOFFS:
  - <what> → <where> → <when>
- FINAL HANDOFF:
  - <artifact> → <where>

## 6) FAIL POLICY (REQUIRED)
- S0: stop pipeline
- S1: allow continue only if explicitly permitted by step notes
- S2: non-blocking but must be fixed
- S3: note/improvement

## 7) INTERFACES (RAW ONLY)
- ORC Rules:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/01__RULES__ORC.md
- ORC Step Template:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/00__TEMPLATES/00__TEMPLATE__ORC_PIPELINE_STEP.md
- ORC Registry (SoT):
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/02__INDEX_ALL_ORCHESTRATORS.md
