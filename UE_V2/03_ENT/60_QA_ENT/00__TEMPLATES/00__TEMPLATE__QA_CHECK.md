# QA CHECK — TEMPLATE (UNIVERSAL QUALITY GATE)

FILE: 03_SYSTEM_ENTITIES/60_QA__QUALITY/00__TEMPLATES/00__TEMPLATE__QA_CHECK.md
SCOPE: Universe Engine (Games volume) / Quality (QA) / Universal QA gate template
SERIAL: C425-B513
LAYER: 03_SYSTEM_ENTITIES
DOC_TYPE: TEMPLATE
ENTITY_GROUP: QUALITY (QA)
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.1.0
UID: UE.GAMES.TPL.QA.CHECK.001
OWNER: SYSTEM
ROLE: Universal QA gate template for usability, completeness, navigation integrity, anti-stub rules, and production readiness.

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: MINOR
- SUMMARY: "DOC CONTROL alignment: normalized header, removed duplicate meta, enforced RAW-only interfaces. Preserved checklist logic."
- REASON: "Keep universal QA gate usable as canon template under runtime rules."
- IMPACT: "Template becomes auditable and consistent with other entity templates."
- CHANGE_ID: UE.CHG.2026-01-20.QA.TPL.CHECK.001

---

## 0) PURPOSE (LAW)
QA Check — это gate качества:
- документ может быть формально валиден (VAL PASS), но быть непригоден по восприятию или по usability
- QA проверяет читабельность, полноту, навигацию, пригодность к выпуску и базовые red flags

## 1) ANTI-STUB LAW (HARD)
Запрещены документы уровня canon/output, которые являются заглушками.
Если документ заявлен ACTIVE и канонический, он обязан иметь применимый контент (пример, правило, запись, контракт, рабочую навигацию).

## 2) QA CHECK IDENTITY (MANDATORY)
QA_NAME:
QA_ID:
DOMAIN:
APPLIES_TO:
- SCOPE:
- ENTITY_KIND:
- LEVELS: [L0_INTAKE, L1_DRAFT, L2_CANON, L3_OUTPUT, N/A]
- DOC_TYPES: [ENGINE, README, REGISTRY, XREF_INDEX, ORCHESTRATOR, CONTROLLER, VALIDATOR, QA_CHECK, ENTITY, INDEX, TEMPLATE]

## 3) INPUT / OUTPUT (MANDATORY)
INPUTS:
- artifacts: []
- validation_results: []
- references: []

OUTPUTS:
- RESULT: PASS | PASS_WITH_NOTES | FAIL
- NOTES: []
- REQUIRED_FIXES: []

## 4) QA NOTE SCHEMA (MANDATORY)
QA_NOTE:
- NOTE_ID:
- SEVERITY: S0|S1|S2|S3
- CATEGORY:
- TARGET:
- MESSAGE:
- REQUIRED_FIX:
- ACCEPTANCE:

Policy:
- any S0 → FAIL
- S1 → FAIL if the pipeline forbids continuation
- S2/S3 → PASS_WITH_NOTES or PASS (depending on level)

## 5) CORE QUALITY CHECKLIST (MANDATORY)
### 5.1 Readability
- структура заголовков не сломана
- документ не является “одной строкой”
- секции и списки читаемы

BLOCKER (S0) if:
- документ технически нечитабелен или невозможно поддерживать

### 5.2 Completeness (minimum per doc type)
ENGINE:
- есть MINI-CONTRACT + интерфейсы + фейлы/края + примеры (если применимо)

README (realm/family):
- есть границы роли (owns/does not own)
- есть ссылки на SoT index/registry и порядок использования

INDEX/REGISTRY:
- есть existence rule (если SoT)
- есть формат записей и рабочая навигация

ORC:
- есть шаги пайплайна + handoffs + gates

CTL:
- есть enforceable policy + fail policy + exceptions

VAL:
- есть checks + violation schema + pass/fail

QA:
- есть checks + issue schema + pass/fail

BLOCKER (S0) if:
- обязательные секции типа документа отсутствуют

### 5.3 Navigation (RAW-only)
- если документ требует ссылок — они должны быть RAW
- не должно быть PATH-подсказок, которые заставляют угадывать дерево

BLOCKER (S0) if:
- без угадывания невозможно пройти маршрут использования

### 5.4 Link integrity
- RAW ссылки корректные
- нет placeholder-имен, которые не существуют

BLOCKER (S0) if:
- ключевая RAW ссылка отсутствует или сломана

### 5.5 Traceability (when required)
- если документ уровня L2/L3 и канонический, он должен быть совместим с регистрацией и аудитом (по стандартам слоя)

BLOCKER (S0) if:
- заявлена каноничность, но отсутствуют базовые требования контроля

## 6) PASS/FAIL POLICY (MANDATORY)
PASS:
- нет S0 и нет блокирующих S1

PASS_WITH_NOTES:
- есть только S2/S3 (или разрешённые S1 на низких уровнях)

FAIL:
- есть S0
- или есть S1, который запрещён политикой пайплайна

## 7) INTERFACES (RAW ONLY)
- QA Global Registry (SoT):
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/60_QA__QUALITY/02__INDEX_ALL_QA.md
- DOC CONTROL Standard:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/01_SPECIFICATIONS/03__DOC_CONTROL_STANDARD.md
- UID Rules:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/02__UID_RULES.md
