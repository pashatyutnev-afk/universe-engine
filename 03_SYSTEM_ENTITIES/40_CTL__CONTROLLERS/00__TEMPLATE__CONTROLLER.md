# 00__TEMPLATE__CONTROLLER

FILE: 03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/00__TEMPLATE__CONTROLLER.md
SCOPE: Universe Engine / Controllers (CTL) / Universal Controller Template (Legacy Base)
SERIAL: C425-B513
LAYER: 03_SYSTEM_ENTITIES
DOC_TYPE: TEMPLATE
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.1.0
UID: UE.CTL.TPL.CONTROLLER.UNIVERSAL.001
OWNER: SYSTEM
ROLE: Universal template for CTL controllers. Defines enforcement policy structure and a canonical rule format. Used as a base reference, not as a substitute for CTL entity template.

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: PATCH
- SUMMARY: "Wrapped legacy template into DOC CONTROL, clarified relationship to CTL entity template and RAW-only interfaces."
- REASON: "Legacy header drift conflicted with DOC CONTROL standard."
- IMPACT: "Template becomes compatible with current documentation system."

---

## 0) PURPOSE (LAW)
Controller — механизм enforcement.
Он:
- проверяет, что артефакт создан в правильном месте (path rules if applicable)
- проверяет корректность уровня (L0/L1/L2/L3) если это часть домена
- проверяет, что обязательные REG/XREF обновления выполнены
- запрещает hidden dependencies
- может блокировать продвижение (REJECT / BLOCKED)

Enforcement rule:
Если CTL правило нарушено — результат считается invalid и не может быть promoted без контролируемого исключения.

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
Этот блок — примеры и базовые направления. Применять только если домен это использует.

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
- REGISTRY_UPDATES:
  - required: NO (обычно CTL не регистрирует, он требует)
- XREF_UPDATES:
  - required: NO (обычно CTL не пишет, он требует)

GATES:
- validators: []
- qa_checks: []

ORCHESTRATION:
- orc_owner: []
- ctl_enforcers: [self]

---

## 7) RAW LINK (MANDATORY)
RAW:

---

## 8) INTERFACES (RAW)
- DOC CONTROL: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/01_SPECIFICATIONS/03__DOC_CONTROL_STANDARD.md
- CTL ENTITY TEMPLATE: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/00__TEMPLATES/00__TEMPLATE__CTL_ENTITY.md
- CTL RULES: https
