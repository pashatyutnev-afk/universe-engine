# ORCHESTRATORS (ORC) — REALM README

FILE: 03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/00__README__ORC_REALM.md
SCOPE: Universe Engine (Games volume) / System Entities / Orchestrators (ORC)
SERIAL: C425-B513
LAYER: 03_SYSTEM_ENTITIES
DOC_TYPE: README (REALM)
ENTITY_GROUP: ORCHESTRATORS (ORC)
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.1.0
UID: UE.GAMES.DOC.ORC.REALM.001
OWNER: SYSTEM
ROLE: Defines ORC realm boundaries, responsibilities, outputs, and integration points (RAW-only navigation compatible).

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: MINOR
- SUMMARY: "DOC CONTROL alignment: normalized header, removed legacy SoT pointers, added strict role boundaries + RAW-only interfaces + KB scope."
- REASON: "Prevent drift and mixed-role contamination; keep ORC usable in boot-first runtime."
- IMPACT: "ORC realm becomes auditable and deterministic for routing/gates/handoffs."
- CHANGE_ID: UE.CHG.2026-01-20.ORC.REALM.001

---

## 0) PURPOSE (LAW)
Этот README задаёт рамки слоя `20_ORC__ORCHESTRATORS`:
- кто такой ORC и где его границы
- какие типы артефактов ORC производит
- как ORC подключается к SPC/ENG/CTL/VAL/QA
- какие документы являются SoT (NAV/EXISTENCE) для слоя ORC

## 1) SCOPE
Применяется ко всем файлам внутри:
- `03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/**`

SoT для NAV/EXISTENCE слоя ORC:
- `03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/02__INDEX_ALL_ORCHESTRATORS.md` (GLOBAL REGISTRY)

## 2) ROLE BOUNDARIES (HARD)
### 2.1 ORC OWNS
ORC отвечает за пайплайн как порядок и маршрутизацию:
- ORDER: последовательность шагов
- ROUTING: кто выполняет шаг (SPC/ENG/CTL/VAL/QA)
- INPUT/OUTPUT: что нужно на входе и что считается завершением
- HANDOFFS: куда класть результат (PRJ/OUT/AST/LOG), и когда
- GATES: где обязательны CTL/VAL/QA проверки

### 2.2 ORC DOES NOT OWN
ORC запрещено:
- принимать доменные решения/контент-решения (это SPC/ENG)
- валидировать законы/структуры (это VAL)
- оценивать качество восприятия/естественность (это QA)
- задавать политики/лимиты/блокировки (это CTL)
- хранить знания/контент как SoT (это KB/PRJ/AST/OUT/DB/LOG)

Нарушение границ роли = S0 (role contamination).

## 3) OUTPUTS (WHAT ORC PRODUCES)
ORC производит только артефакты пайплайна:
- PIPELINE_PLAN (список шагов + handoffs + gates)
- ROUTING_MAP (назначение исполнителей на шаги)
- CHECKPOINTS (контрольные точки)
- FAILURE_POLICY_MAP (что считать стопом и где допускаются предупреждения)

## 4) INTEGRATION (HOW ORC IS USED)
### 4.1 Default lifecycle placement
ORC включается после INTAKE и до EXECUTION:
- INTAKE: MACHINE_ARCHITECT_SPC
- ROUTING: ORC выбирает пайплайн и назначает исполнителей
- EXECUTION: шаги выполняют SPC/ENG
- CONTROL/VALIDATION: CTL + VAL
- QA: QA gate
- PACKAGING + SIGNOFF: governance SPC chain

### 4.2 Gate discipline
Если шаг требует gate:
- `GATE: CTL` — enforce policy/limits
- `GATE: VAL` — formal compliance PASS/FAIL + violations
- `GATE: QA` — quality PASS/FAIL + issues
ORC обязан явно указывать gate в шаге и порядок gate (если более одного).

## 5) MINIMUM FILE SET (REALM)
Минимальный набор для слоя ORC:
- realm README (этот файл)
- ruleset
- global registry (index)
- create flow
- templates (entity + pipeline step + family readme)

## 6) INTERFACES (RAW ONLY)
- ORC Global Registry (SoT):
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/02__INDEX_ALL_ORCHESTRATORS.md
- ORC Rules:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/01__RULES__ORC.md
- ORC Create Flow:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/03__ORC_CREATE_FLOW.md
- ORC Templates Index (family):
  - ORC ENTITY TEMPLATE:
    - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/00__TEMPLATES/00__TEMPLATE__ORC_ENTITY.md
  - ORC PIPELINE STEP TEMPLATE:
    - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/00__TEMPLATES/00__TEMPLATE__ORC_PIPELINE_STEP.md
  - ORC FAMILY README TEMPLATE:
    - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/00__TEMPLATES/00__TEMPLATE__README__ORC.md

## 7) KNOWLEDGE BASE (KB) SCOPE
KB INPUTS:
- system laws/standards needed to design pipelines (naming/uid/doc-control/index-structure)
- domain standards if the pipeline is domain-specific

KB OUTPUTS:
- none (ORC outputs are pipeline artifacts, not KB modules)

BOUNDARIES:
- ORC не создаёт доменные знания и не “улучшает” контент, только маршрутизирует и фиксирует gates/handoffs
