# 00__TEMPLATE__CONTROLLER (LEGACY UNIVERSAL BASE)

FILE: 03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/00__TEMPLATE__CONTROLLER.md
SCOPE: Universe Engine (Games volume) / Controllers (CTL) / Universal Controller Template (Legacy Base)
SERIAL: C425-B513
LAYER: 03_SYSTEM_ENTITIES
DOC_TYPE: TEMPLATE
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.1.1
UID: UE.CTL.TPL.CONTROLLER.UNIVERSAL.001
OWNER: SYSTEM
ROLE: Legacy base template for CTL controllers (policy/rules format). Reference only — not a substitute for CTL entity template.

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: PATCH
- SUMMARY: "Fixed broken interface section + aligned formatting to DOC CONTROL; clarified relationship to CTL entity template; added KB scope."
- REASON: "Legacy file had truncated RAW interface and could cause nav drift."
- IMPACT: "Template becomes safe to reference without breaking RAW-only navigation."
- CHANGE_ID: UE.CHG.2026-01-20.CTL.TPL.LEGACY.001

---

## 0) PURPOSE (LAW)
Controller — механизм enforcement.
Он:
- проверяет обязательные артефакты/поля/регистрации (если это политика CTL)
- проверяет корректность уровней/линковки (если домен это использует)
- запрещает hidden dependencies (если политика CTL)
- может блокировать продвижение (BLOCKED) через blockers

ВАЖНО:
- Этот файл — базовый “формат правил” (legacy).
- Для создания нового контроллера использовать `00__TEMPLATE__CTL_ENTITY.md`.

---

## 1) CONTROLLER IDENTITY (MANDATORY)
CTL_NAME:
CTL_ID:
DOMAIN:
APPLIES_TO:
- SCOPE:
- ENTITY_KIND:
- LEVELS: [L0_INTAKE, L1_DRAFT, L2_CANON, L3_OUTPUT]
OWNER: SYSTEM
LOCK: FIXED

---

## 2) POLICY (WHAT THIS CONTROLLER ENFORCES)
POLICY_TYPE:
SEVERITY:
- VIOLATION_LEVEL:
- DEFAULT_ACTION:

---

## 3) RULE SET (MANDATORY)
Каждое правило должно быть явным и проверяемым.

### 3.1 Rule format
RULE:
- RULE_ID:
- NAME:
- CONDITION:
- CHECK:
  - inputs: []
  - logic:
- PASS_ACTION:
- FAIL_ACTION:
- FAIL_MESSAGE:
- FIX_GUIDE:

---

## 4) RECOMMENDED BASE RULES (OPTIONAL)
### 4.1 Level enforcement (example)
- No skip promotion: L2 cannot exist without L1 lineage unless exception logged
- L3 must reference L2 (XREF CANON_REF required)

### 4.2 Registry enforcement (example)
- If OUTPUT_LEVEL == L2 → registry entry required
- If OUTPUT_LEVEL == L3 → registry entry required

### 4.3 Hidden dependency enforcement (example)
- If artifact uses another artifact/entity as prerequisite → XREF record required

---

## 5) EXCEPTIONS (CONTROLLED)
Исключения разрешены только если:
- зафиксированы в governance/audit
- имеют WHY и APPROVER

EXCEPTION_RECORD_FORMAT:
- ITEM:
- RULE_ID:
- WHY:
- APPROVED_BY:
- AT:

---

## 6) SYSTEM INTERFACE (MANDATORY)
INPUTS:
- artifacts: [candidate outputs, pipeline steps]
- sources: [REG entries, XREF indexes, headers]

OUTPUTS:
- decisions: [PASS/FAIL, notes]
- BLOCKERS: (если FAIL) — по `CTL_BLOCKER`

---

## 7) KNOWLEDGE BASE (KB) SCOPE
KB INPUTS:
- примеры policy/rule sets
- типовые blockers и формулировки REQUIRED_ACTION

KB OUTPUTS:
- none

BOUNDARIES:
- template не создаёт доменные решения и не подменяет VAL/QA.

---

## 8) INTERFACES (RAW ONLY)
- DOC CONTROL:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/01_SPECIFICATIONS/03__DOC_CONTROL_STANDARD.md
- UID RULES:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/02__UID_RULES.md
- CTL REALM README:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/00__README__CTL_REALM.md
- CTL RULES:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/01__RULES__CTL.md
- CTL ENTITY TEMPLATE (PRIMARY FOR NEW CONTROLLERS):
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/00__TEMPLATES/00__TEMPLATE__CTL_ENTITY.md
- CTL BLOCKER TEMPLATE:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/00__TEMPLATES/00__TEMPLATE__CTL_BLOCKER.md
- CTL GLOBAL REGISTRY (SoT):
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/02__INDEX_ALL_CONTROLLERS.md
- CTL CREATE FLOW:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/03__CREATE_FLOW__CTL.md
- READINESS CHECK (DEFAULT CTL):
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/01__READINESS_CHECK_CTL.md

--- END.
