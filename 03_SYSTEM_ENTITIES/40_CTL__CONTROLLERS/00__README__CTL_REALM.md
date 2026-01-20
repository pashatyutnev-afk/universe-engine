# 00__README__CTL_REALM

FILE: 03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/00__README__CTL_REALM.md
SCOPE: Universe Engine / System Entities / Controllers (CTL)
SERIAL: C425-B513
LAYER: 03_SYSTEM_ENTITIES
DOC_TYPE: README (REALM)
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.CTL.REALM.README.001
OWNER: SYSTEM
ROLE: Realm entrypoint for CTL. Defines purpose, boundaries, existence law, and navigation rules for controllers.

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: MAJOR
- SUMMARY: "Aligned README with DOC CONTROL + RAW-only navigation + canonical SoT pointers. Removed outdated SoT drift."
- REASON: "Prevent CTL layer drift and mismatched standards/indices."
- IMPACT: "CTL realm becomes deterministic: correct pointers, correct boundaries, stable navigation."

---

## 0) PURPOSE (LAW)
Этот документ — входная точка слоя `40_CTL__CONTROLLERS`.
CTL (Controller) — сущность enforcement и управления состоянием выполнения пайплайнов.
CTL:
- ставит обязательные checkpoints и gates
- проверяет готовность и наличие обязательных артефактов
- возвращает состояние (READY / BLOCKED / DONE / SKIP)
- формирует blockers с требуемыми действиями

CTL не делает:
- доменных решений (это SPC/ENG)
- структурной валидации канона (это VAL)
- оценки художественного качества (это QA)

---

## 1) NAVIGATION LAW (ABSOLUTE)
- Навигация по слою CTL выполняется **только по RAW**.
- Source of Truth состава слоя CTL = **единственный канон-индекс**:
  - `03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/02__INDEX_ALL_CONTROLLERS.md`
- Если файл существует в репо, но не зарегистрирован в CTL INDEX — он считается **NON-CANON / ignored** для слоя CTL.

---

## 2) EXISTENCE LAW (ABSOLUTE)
CTL-контроллер считается существующим (CANON) только если выполнено одновременно:
1) Файл контроллера создан по шаблону CTL
2) Контроллер зарегистрирован в `02__INDEX_ALL_CONTROLLERS.md`
3) Указаны UID + VERSION (semver) + STATUS/LOCK
4) Контроллер имеет ясный MINI-CONTRACT (consumes/produces/output_target)

---

## 3) WHAT CTL PRODUCES (OUTPUTS)
Типовые выходы CTL:
- CHECKPOINT_STATE (READY/BLOCKED/DONE/SKIP)
- BLOCKERS_LIST (структурированный список препятствий)
- REQUIRED_ARTIFACTS_REPORT (что отсутствует)
- READINESS_REPORT (PASS/FAIL + missing list)
- CONTROL_NOTE (короткий результат проверки, пригодный для audit trail)

---

## 4) INTERFACES (RAW)
Ссылки ниже используются как канонические опоры (RAW-only).

### Runtime entrypoint
- START: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/00_INDEX/01__START_UNIVERSE_ENGINE.md

### System law
- SYSTEM LAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/00__SYSTEM_LAW.md
- UID RULES: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/02__UID_RULES.md

### Standards
- DOC CONTROL: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/01_SPECIFICATIONS/03__DOC_CONTROL_STANDARD.md
- INDEX STRUCTURE: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/01_SPECIFICATIONS/09__INDEX_STRUCTURE_SPEC.md
- STORAGE MAP: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/01_SPECIFICATIONS/02__STORAGE_MAP_STANDARD.md

### CTL layer SoT
- CTL INDEX (SoT): https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/02__INDEX_ALL_CONTROLLERS.md
- CTL RULES: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/01__RULES__CTL.md
- CTL CREATE FLOW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/03__CREATE_FLOW__CTL.md
- CTL TEMPLATE (ENTITY): https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/00__TEMPLATES/00__TEMPLATE__CTL_ENTITY.md
- CTL TEMPLATE (BLOCKER): https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/00__TEMPLATES/00__TEMPLATE__CTL_BLOCKER.md
- READINESS (DEFAULT): https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/01__READINESS_CHECK_CTL.md

---

## 5) KNOWLEDGE BASE (KB) SCOPE
KB здесь используется как справочник методов/паттернов контроля, но не как источник доменных решений.

KB INPUTS:
- чек-листы контроля, форматы blockers, примеры gate-отчётов (если существуют в KB)

KB OUTPUTS:
- отсутствуют (CTL производит контрольные отчёты и states, не знания)

BOUNDARIES:
- CTL не создаёт новые доменные правила и не переопределяет стандарты
- при конфликте правил CTL обязан ссылаться на стандарты/законы и остановить выполнение (BLOCKED)

---

## 6) QUICK USAGE
1) Открой CTL INDEX (SoT)
2) Выбери FAMILY по задаче
3) Пройди контроллеры по номеру
4) Применяй CTL как gate в ORC шаге (READY/BLOCKED)

--- END.
