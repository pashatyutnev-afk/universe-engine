# CONTROLLERS (CTL) — REALM README (CANON)

FILE: 03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/00__README__CTL_REALM.md
SCOPE: Universe Engine (Games volume) / System Entities / Controllers (CTL)
SERIAL: C425-B513
LAYER: 03_SYSTEM_ENTITIES
DOC_TYPE: README (REALM)
ENTITY_GROUP: CONTROLLERS (CTL)
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.CTL.REALM.001
OWNER: SYSTEM
ROLE: Canonical boundaries + navigation law + CTL contract meaning (RAW-only).

CHANGE_NOTE:
- DATE: 2026-01-20
- TYPE: MAJOR
- SUMMARY: "Rebuilt CTL realm README to DOC CONTROL + RAW-only interfaces; removed legacy non-RAW SoT pointers; clarified CTL boundaries + outputs + gate behavior."
- REASON: "Old README referenced non-canon paths and mixed role semantics."
- IMPACT: "CTL realm becomes deterministic and compatible with START_UNIVERSE_ENGINE runtime."
- CHANGE_ID: UE.CHG.2026-01-20.CTL.REALM.001

---

## 0) PURPOSE (LAW)
CTL (Controller) — сущность принудительного контроля (enforcement), которая:
- ставит checkpoints / gates в пайплайне
- проверяет наличие обязательных артефактов/полей/регистраций
- возвращает состояние: READY / BLOCKED / DONE / SKIP
- формирует blockers в едином формате
- запрещает скрытые зависимости (hidden dependencies), если это политика CTL

CTL не принимает доменных решений (SPC/ENG).
CTL не валидирует законы/структуру (VAL).
CTL не оценивает художественное качество/естественность (QA).

---

## 1) SCOPE
Этот realm применяется ко всем файлам внутри:
- `03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/**`

Source of truth (SoT) для состава/существования CTL:
- `03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/02__INDEX_ALL_CONTROLLERS.md` (GLOBAL REGISTRY)

---

## 2) ROLE BOUNDARIES (HARD)
### 2.1 CTL OWNS
- enforcement политик/лимитов/обязательных требований в точке gate
- readiness проверки: “есть ли минимальные входы/артефакты”
- формирование blockers (S0–S3)
- финальный verdict на gate: READY/BLOCKED/DONE/SKIP

### 2.2 CTL DOES NOT OWN
- генерация контента/решения “как правильно сделать” (SPC/ENG)
- проверка соответствия законам/стандартам как PASS/FAIL по канону (VAL)
- оценка качества восприятия, естественности, художественных критериев (QA)
Нарушение границ роли = S0 (role contamination).

---

## 3) WHAT CTL PRODUCES (OUTPUTS)
Типовые выходы CTL:
- CHECKPOINT_STATUS (READY/BLOCKED/DONE/SKIP)
- BLOCKERS (list) — строго по `CTL_BLOCKER` template
- REQUIRED_ARTIFACTS_CHECK (сводка чего не хватает)
- CONTROL_NOTE (опционально): краткий лог/причина (если OUTPUT_TARGET включает LOG/PRJ)

---

## 4) HOW CTL IS USED IN PIPELINES
- ORC step может иметь `GATE: CTL` или комбинированный gate (CTL+VAL+QA).
- Если CTL возвращает BLOCKED:
  - ORC обязан остановиться (для S0/S1 blockers)
  - для S2/S3 — поведение определяется ORC/policy (но blockers фиксируются)

---

## 5) EXISTENCE LAW (ABSOLUTE)
CTL контроллер существует в каноне только если:
- имеет UID (по UID rules)
- оформлен по `00__TEMPLATE__CTL_ENTITY.md` (или допускаемой base-template ссылке)
- зарегистрирован в `02__INDEX_ALL_CONTROLLERS.md` (RAW link)

Файл в репо без регистрации → NON-CANON / ignored.

---

## 6) KNOWLEDGE BASE (KB) SCOPE
KB INPUTS:
- playbooks по контролю (как писать checkpoints, как формулировать blockers)
- примеры корректных CTL gate отчётов

KB OUTPUTS:
- none (CTL сам по себе не KB модуль)

BOUNDARIES:
- KB не обязателен для выполнения CTL gate; CTL обязан работать по собственному контракту и входам пайплайна.

---

## 7) INTERFACES (RAW ONLY)
- CTL RULESET:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/01__RULES__CTL.md
- CTL GLOBAL REGISTRY (SoT):
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/02__INDEX_ALL_CONTROLLERS.md
- CTL CREATE FLOW:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/03__CREATE_FLOW__CTL.md
- CTL ENTITY TEMPLATE:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/00__TEMPLATES/00__TEMPLATE__CTL_ENTITY.md
- CTL BLOCKER TEMPLATE:
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/00__TEMPLATES/00__TEMPLATE__CTL_BLOCKER.md
- CTL LEGACY BASE TEMPLATE (reference only):
  - RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/00__TEMPLATE__CONTROLLER.md

--- END.
