# Dependency Registry Engine
FILE: 06__DEPENDENCY_REGISTRY_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
FAMILY: 00_GOVERNANCE_ENGINES
LEVEL: L1
STATUS: ACTIVE
VERSION: 1.0
ROLE: Single source of truth for ENG engine dependencies (DEPENDS_ON) + cycle governance + sync rules

---

## MINI-CONTRACT (MANDATORY)
CONSUMES:
- Engine files (DEPENDS_ON blocks)
- ENG layer INDEX (registry targets)
- Change proposals that touch deps
- Existing dependency registry entries

PRODUCES:
- Canon dependency registry (this file)
- Dependency violation list (hidden deps / mismatches / cycles)
- Cycle exception notes (allowed cycles + reasons)
- Sync directives for Consistency Engine + Change Control
- Dependency map rules for future engines

DEPENDS_ON:
- 03__RULE_HIERARCHY_ENG
- 04__CHANGE_CONTROL_ENG
- 05__CONSISTENCY_ENG
- 01__AUDIT_LOG_ENG
- 10__VERSIONING_MEMORY_ENG

OUTPUT_TARGET:
- Registry entries used by all ENG engines and governance gating

---

## 0) PURPOSE (LAW)
Этот реестр — **единственная точка истины** для зависимостей ENG-движков.

Он гарантирует:
- отсутствие “скрытых зависимостей”
- синхронность между `DEPENDS_ON` в движках и реестром
- контролируемые циклы (если они нужны — то **явно** и **обоснованно**)
- стабильность pipeline (Change Control / Consistency / Audit)

### ABSOLUTE RULE
> Любая зависимость, которой нет в этом реестре, считается **non-canon** даже если она упомянута в тексте движка.

---

## 1) SCOPE
Реестр охватывает **только ENG слой**:

`03_SYSTEM_ENTITIES/10_ENG__ENGINES/**`

Если зависимость указывает на другой класс сущностей (ORC/SPC/CTL/VAL/QA),
она должна быть оформлена как **cross-layer link** (в отдельном реестре того слоя)
и отражена через governance-стыки (Rule Hierarchy / Change Control).

---

## 2) DEPENDENCY TERMS (DEFINITIONS)
### 2.1 What is a dependency
**Dependency** — это когда движок **не может быть корректно выполнен** без результата другого движка.

### 2.2 Hard vs Soft
- **HARD_DEP**: без него движок невалиден (обязательная предпосылка)
- **SOFT_DEP**: улучшает результат, но движок всё ещё работает (опционально)

### 2.3 Dependency Direction
Запись `A -> B` означает:
- A **depends_on** B
- B должен быть пройден / доступен перед A

---

## 3) REGISTRY FORMAT (CANON)
Каждая запись реестра должна быть в строгом формате.

### 3.1 Record Template (MANDATORY)
ENGINE_ID: <FAMILY>/<NN__ENGINE_FILE_ENG.md>
ENGINE_NAME: <Human readable>
DEPENDS_ON:
  - <FAMILY>/<NN__ENGINE_FILE_ENG.md> [HARD|SOFT]
  - ...
CYCLE_STATUS: NONE | ALLOWED | FORBIDDEN
CYCLE_REASON: <required if ALLOWED>
NOTES: <optional>
LOCK: FIXED

### 3.2 Engine ID rule
- Используем **канонический путь** относительно `10_ENG__ENGINES/`
- Без raw-links (raw-links живут в INDEX)
- Пример:
  `00_GOVERNANCE_ENGINES/04__CHANGE_CONTROL_ENG.md`

---

## 4) SYNC LAW (DEPENDS_ON ↔ REGISTRY)
### 4.1 Sync Rule (ABSOLUTE)
- `DEPENDS_ON` в файле движка **обязан** совпадать с `DEPENDS_ON` в реестре.
- Разрешено только одно: в реестре можно держать отметку HARD/SOFT и цикл-статус.

### 4.2 If mismatch found
Это `S1_CRITICAL` нарушение (блокирует канон), пока не выполнено одно из двух:
1) исправить DEPENDS_ON в движке под реестр
2) провести Change Control и изменить реестр + движок синхронно

---

## 5) HIDDEN DEPENDENCIES (FORBIDDEN)
Скрытая зависимость — когда:
- движок в тексте “опирается на” другой движок,
- но DEPENDS_ON это не отражает,
- и/или в реестре нет записи.

### Enforcement
- Любая скрытая зависимость = `S1_CRITICAL`
- Фикс: добавить в DEPENDS_ON + реестр через Change Control

---

## 6) CYCLE LAW (CYCLES)
### 6.1 Default
Циклы **по умолчанию запрещены**.

### 6.2 When cycle may be allowed
Только если:
- цикл **невозможно** заменить линейной зависимостью без потери смысла
- цикл описан как “итеративная система обратной связи”
- есть чёткий “entry-point engine” (с которого цикл запускается)
- есть правило “когда цикл останавливается” (stop condition)

### 6.3 Mandatory fields for allowed cycles
Если `CYCLE_STATUS: ALLOWED`, то обязательно:
- `CYCLE_REASON`
- `NOTES` с:
  - entry-point
  - stop condition
  - почему нельзя разорвать

---

## 7) CHANGE CONTROL GATE (MANDATORY)
Любое изменение зависимостей — это изменение канона и идёт через:
- `00_GOVERNANCE_ENGINES/04__CHANGE_CONTROL_ENG.md`
- логируется в `01__AUDIT_LOG_ENG.md`
- записывается в `10__VERSIONING_MEMORY_ENG.md`
- проходит `05__CONSISTENCY_ENG.md`

---

# DEPENDENCY REGISTRY — ENG (CANON)

LOCK: FIXED

---

## 00_GOVERNANCE_ENGINES

ENGINE_ID: 00_GOVERNANCE_ENGINES/01__AUDIT_LOG_ENG.md
ENGINE_NAME: Audit Log Engine
DEPENDS_ON:
  - 00_GOVERNANCE_ENGINES/02__CANON_AUTHORITY_ENG.md [HARD]
  - 00_GOVERNANCE_ENGINES/03__RULE_HIERARCHY_ENG.md [HARD]
CYCLE_STATUS: NONE
CYCLE_REASON:
NOTES:
LOCK: FIXED

---

ENGINE_ID: 00_GOVERNANCE_ENGINES/02__CANON_AUTHORITY_ENG.md
ENGINE_NAME: Canon Authority Engine
DEPENDS_ON:
  - 00_GOVERNANCE_ENGINES/03__RULE_HIERARCHY_ENG.md [HARD]
CYCLE_STATUS: NONE
CYCLE_REASON:
NOTES:
LOCK: FIXED

---

ENGINE_ID: 00_GOVERNANCE_ENGINES/03__RULE_HIERARCHY_ENG.md
ENGINE_NAME: Rule Hierarchy Engine
DEPENDS_ON: []
CYCLE_STATUS: NONE
CYCLE_REASON:
NOTES:
LOCK: FIXED

---

ENGINE_ID: 00_GOVERNANCE_ENGINES/04__CHANGE_CONTROL_ENG.md
ENGINE_NAME: Change Control Engine
DEPENDS_ON:
  - 00_GOVERNANCE_ENGINES/02__CANON_AUTHORITY_ENG.md [HARD]
  - 00_GOVERNANCE_ENGINES/03__RULE_HIERARCHY_ENG.md [HARD]
  - 00_GOVERNANCE_ENGINES/01__AUDIT_LOG_ENG.md [HARD]
  - 00_GOVERNANCE_ENGINES/10__VERSIONING_MEMORY_ENG.md [HARD]
CYCLE_STATUS: NONE
CYCLE_REASON:
NOTES:
LOCK: FIXED

---

ENGINE_ID: 00_GOVERNANCE_ENGINES/05__CONSISTENCY_ENG.md
ENGINE_NAME: Consistency Engine
DEPENDS_ON:
  - 00_GOVERNANCE_ENGINES/03__RULE_HIERARCHY_ENG.md [HARD]
  - 00_GOVERNANCE_ENGINES/04__CHANGE_CONTROL_ENG.md [HARD]
  - 00_GOVERNANCE_ENGINES/06__DEPENDENCY_REGISTRY_ENG.md [HARD]
  - 00_GOVERNANCE_ENGINES/10__VERSIONING_MEMORY_ENG.md [SOFT]
CYCLE_STATUS: ALLOWED
CYCLE_REASON: Consistency validates Dependency Registry, while Dependency Registry rules depend on Consistency enforcement.
NOTES:
  entry_point: 00_GOVERNANCE_ENGINES/04__CHANGE_CONTROL_ENG.md
  stop_condition: When registry and engine DEPENDS_ON blocks are synchronized and no S1 violations remain.
LOCK: FIXED

---

ENGINE_ID: 00_GOVERNANCE_ENGINES/06__DEPENDENCY_REGISTRY_ENG.md
ENGINE_NAME: Dependency Registry Engine
DEPENDS_ON:
  - 00_GOVERNANCE_ENGINES/03__RULE_HIERARCHY_ENG.md [HARD]
  - 00_GOVERNANCE_ENGINES/04__CHANGE_CONTROL_ENG.md [HARD]
  - 00_GOVERNANCE_ENGINES/05__CONSISTENCY_ENG.md [HARD]
  - 00_GOVERNANCE_ENGINES/01__AUDIT_LOG_ENG.md [SOFT]
  - 00_GOVERNANCE_ENGINES/10__VERSIONING_MEMORY_ENG.md [SOFT]
CYCLE_STATUS: ALLOWED
CYCLE_REASON: Registry and Consistency are mutually validating in governance loop.
NOTES:
  entry_point: 00_GOVERNANCE_ENGINES/04__CHANGE_CONTROL_ENG.md
  stop_condition: Registry reflects actual canon dependencies and Consistency report has no S1.
LOCK: FIXED

---

ENGINE_ID: 00_GOVERNANCE_ENGINES/07__DECISION_APPROVAL_ENG.md
ENGINE_NAME: Decision Approval Engine
DEPENDS_ON:
  - 00_GOVERNANCE_ENGINES/02__CANON_AUTHORITY_ENG.md [HARD]
  - 00_GOVERNANCE_ENGINES/04__CHANGE_CONTROL_ENG.md [HARD]
CYCLE_STATUS: NONE
CYCLE_REASON:
NOTES:
LOCK: FIXED

---

ENGINE_ID: 00_GOVERNANCE_ENGINES/08__SCOPE_IMPACT_ENG.md
ENGINE_NAME: Scope Impact Engine
DEPENDS_ON:
  - 00_GOVERNANCE_ENGINES/04__CHANGE_CONTROL_ENG.md [HARD]
  - 00_GOVERNANCE_ENGINES/05__CONSISTENCY_ENG.md [SOFT]
CYCLE_STATUS: NONE
CYCLE_REASON:
NOTES:
LOCK: FIXED

---

ENGINE_ID: 00_GOVERNANCE_ENGINES/09__RISK_SAFETY_ENG.md
ENGINE_NAME: Risk Safety Engine
DEPENDS_ON:
  - 00_GOVERNANCE_ENGINES/04__CHANGE_CONTROL_ENG.md [HARD]
  - 00_GOVERNANCE_ENGINES/03__RULE_HIERARCHY_ENG.md [SOFT]
CYCLE_STATUS: NONE
CYCLE_REASON:
NOTES:
LOCK: FIXED

---

ENGINE_ID: 00_GOVERNANCE_ENGINES/10__VERSIONING_MEMORY_ENG.md
ENGINE_NAME: Versioning & Memory Engine
DEPENDS_ON:
  - 00_GOVERNANCE_ENGINES/01__AUDIT_LOG_ENG.md [HARD]
  - 00_GOVERNANCE_ENGINES/03__RULE_HIERARCHY_ENG.md [SOFT]
CYCLE_STATUS: NONE
CYCLE_REASON:
NOTES:
LOCK: FIXED

---

## 01_CORE_ENGINES
# TODO: Fill when CORE engines are finalized with their DEPENDS_ON blocks.
# RULE: Do not add speculative dependencies. Only what is present in engine DEPENDS_ON.

## 02_DOMAIN_NARRATIVE_ENGINES
# TODO

## 03_DOMAIN_CHARACTER_ENGINES
# TODO

## 04_DOMAIN_WORLD_ENGINES
# TODO

## 05_EXPRESSION_ENGINES
# TODO

## 06_GENRE_STYLE_ENGINES
# TODO

## 07_PRODUCTION_FORMAT_ENGINES
# TODO

## 08_KNOWLEDGE_PRODUCTION_ENGINES
# TODO

## 09_SOUND_MUSIC_ENGINES
# TODO

## 10_META_EVOLUTION_ENGINES
# TODO

---

## FINAL RULE (LOCK)
> Dependency Registry — единственный канонический реестр зависимостей ENG слоя.  
> Любая правка зависимостей проходит Change Control и фиксируется в Audit + Versioning.

OWNER: Universe Engine
LOCK: FIXED
