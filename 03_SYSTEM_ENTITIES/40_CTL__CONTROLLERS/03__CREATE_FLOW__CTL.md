# 03__CREATE_FLOW__CTL

FILE: 03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/03__CREATE_FLOW__CTL.md
SCOPE: Universe Engine / Controllers (CTL) / Create Flow
SERIAL: C425-B513
LAYER: 03_SYSTEM_ENTITIES
DOC_TYPE: RUNBOOK (CREATE_FLOW)
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.CTL.CREATE_FLOW.001
OWNER: SYSTEM
ROLE: Deterministic procedure to create a CTL controller without drift: UID → file → registration → verification.

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: MAJOR
- SUMMARY: "Upgraded CTL create flow to match DOC CONTROL, RAW-only, and CTL index SoT rules."
- REASON: "Old flow did not enforce registration + doc-control parity."
- IMPACT: "No controller exists for CTL layer unless created and registered correctly."

---

## 0) CORE LAW (ABSOLUTE)
CTL контроллер существует (CANON) только после выполнения:
1) создан файл CTL по шаблону
2) добавлена запись в CTL INDEX (SoT)
3) выполнена базовая проверка готовности контроллера (readiness)

---

## 1) REQUIRED INPUTS
- выбранное FAMILY внутри `40_CTL__CONTROLLERS/` (например доменное семейство)
- цель контроллера (что контролирует)
- список обязательных артефактов/полей, которые он проверяет
- куда пишет результат (OUTPUT_TARGET)

---

## 2) STEPS (MANDATORY ORDER)
### Step 1 — Choose FAMILY
- Выбери FAMILY папку по смыслу (GEN / доменные FAMILY).
- Если FAMILY отсутствует, создавай FAMILY по правилам слоя CTL и сразу регистрируй в CTL INDEX.

### Step 2 — Assign UID + VERSION
- Назначь UID по UID rules.
- Задай VERSION (semver), обычно старт: 1.0.0.

### Step 3 — Create file by template
- Создай файл контроллера по `00__TEMPLATE__CTL_ENTITY.md`.
- Заполни PURPOSE + MINI-CONTRACT + CHECKPOINTS.

### Step 4 — Register in CTL INDEX (SoT)
- Добавь контроллер в `02__INDEX_ALL_CONTROLLERS.md`:
  - FAMILY блок
  - номер по порядку
  - RAW ссылка

### Step 5 — Run basic readiness for controller (self-check)
Контроллер обязан пройти минимальную самопроверку:
- DOC CONTROL header присутствует
- UID/STATUS/LOCK/VERSION присутствуют
- MINI-CONTRACT заполнен
- есть минимум один CHECKPOINT
Если не проходит — считаем контроллер недействительным (BLOCKED).

### Step 6 — Optional: record governance trace
Если для задачи требуется audit trail:
- добавь запись в журнал (если включено в процессе проекта)

---

## 3) OUTPUTS
- готовый файл CTL контроллера
- обновлённый CTL INDEX (SoT)
- при необходимости: краткий readiness отчёт

---

## 4) INTERFACES (RAW)
- UID RULES: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/01_SYSTEM_LAW/02__UID_RULES.md
- DOC CONTROL: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/02_STANDARDS/01_SPECIFICATIONS/03__DOC_CONTROL_STANDARD.md
- CTL INDEX (SoT): https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/02__INDEX_ALL_CONTROLLERS.md
- CTL TEMPLATE (ENTITY): https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/00__TEMPLATES/00__TEMPLATE__CTL_ENTITY.md
- READINESS (DEFAULT): https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/01__READINESS_CHECK_CTL.md

---

## 5) KNOWLEDGE BASE (KB) SCOPE
KB может хранить playbooks по контролю, примеры контроллеров и типовые gate-отчёты.
Create flow не требует KB как обязательного входа.

--- END.
