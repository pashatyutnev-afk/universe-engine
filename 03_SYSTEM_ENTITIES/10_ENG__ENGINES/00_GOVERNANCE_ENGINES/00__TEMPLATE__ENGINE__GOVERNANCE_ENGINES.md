# GOVERNANCE ENGINE — TEMPLATE (ETALON)
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/00__TEMPLATE__ENGINE__GOVERNANCE_ENGINES.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
DOC_TYPE: TEMPLATE_ENGINE
FAMILY: 00_GOVERNANCE_ENGINES
CLASS: GOVERNANCE (L1)
LEVEL: L1
STATUS: ACTIVE
LOCK: FIXED
VERSION: 2.0.0
UID: UE.ENG.GOV.TPL.ENGINE.001
OWNER: SYSTEM
ROLE: Canonical template for all governance engines. Forces compatibility with governance pipeline, logs, and artifact vocabulary.

CHANGE_NOTE:
- DATE: 2026-01-08
- TYPE: MAJOR
- SUMMARY: "Etalon engine template: strict header, mini-contract, gates, record formats, storage targets, edge-case policy."
- REASON: "Stop drift. Governance engines must be deterministic and auditable."
- IMPACT: "All governance engines become uniform and compatible."
- CHANGE_ID: UE.CHG.2026-01-08.GOV.TPL.ENGINE.001

---

## 0) HOW TO USE THIS TEMPLATE (LAW)

1) Создай новый файл движка в `00_GOVERNANCE_ENGINES/` по правилу:
   `NN__<ENGINE_NAME>_ENG.md`
2) Полностью скопируй этот шаблон.
3) Заполни все поля `TODO:` и удали подсказочные строки `TEMPLATE NOTE:`.
4) Проверь, что:
   - mini-contract заполнен
   - outputs имеют storage targets
   - есть gate logic + severity mapping
   - есть examples + edge cases
5) Зарегистрируй движок в индексах и зависимостях согласно governance pipeline.

TEMPLATE NOTE:
- Этот файл — шаблон, не движок. Он не “исполняется” и не создаёт записи.

---

# <ENGINE NAME> — GOVERNANCE ENGINE (CANON)
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/NN__<ENGINE_NAME>_ENG.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
DOC_TYPE: ENGINE_SPEC
FAMILY: 00_GOVERNANCE_ENGINES
ENGINE: NN__<ENGINE_NAME>_ENG
CLASS: GOVERNANCE (L1)
LEVEL: L1
STATUS: DRAFT
LOCK: OPEN
VERSION: 0.1.0
UID: UE.ENG.GOV.<ENGINE_KEY>.NNN
OWNER: <OWNER_ROLE_OR_SYSTEM>
ROLE: <one sentence — what decision/report/record this engine guarantees>

CHANGE_NOTE:
- DATE: YYYY-MM-DD
- TYPE: PATCH|MINOR|MAJOR
- SUMMARY: "<what changed>"
- REASON: "<why>"
- IMPACT: "<what is affected>"
- CHANGE_ID: UE.CHG.YYYY-MM-DD.<TAG>.<NNN>

---

## 1) PURPOSE (ONE SENTENCE)

TODO: Одно предложение: “Этот движок обеспечивает … (какой управленческий результат)”.

---

## 2) SCOPE + BOUNDARIES (ANTI-DUPLICATION LAW)

### 2.1 OWNS
TODO: Чётко: что именно этот движок делает (3–7 пунктов).

### 2.2 DOES NOT OWN
TODO: Что запрещено делать этому движку (3–7 пунктов).
Hard rule: Governance engine не создаёт domain-сущности и не “пишет мир/персонажей”.

### 2.3 INPUT VALIDITY DOMAIN
TODO: Что считается валидным входом (без этого движок не стартует).

---

## 3) ENGINE MINI-CONTRACT (MANDATORY)

CONSUMES:
- TODO: <1–5 input artifact types> (из governance vocabulary)
- TODO: ...

PRODUCES:
- TODO: <1–5 output artifacts> (records/reports)
- TODO: ...

DEPENDS_ON:
- TODO: [<FAMILY/NN__ENGINE>, ...] или []
- Example:
  - 00_GOVERNANCE_ENGINES/04__CHANGE_CONTROL_ENG
  - 00_GOVERNANCE_ENGINES/01__AUDIT_LOG_ENG

OUTPUT_TARGET:
- TODO: Где живут outputs (канонические пути/файлы)
- Example:
  - 99_LOGS/LOG__AUDIT.md
  - 99_LOGS/LOG__CHANGES.md

---

## 4) TRIGGERS (WHEN THIS ENGINE RUNS)

TODO: Условия запуска (event-driven):
- Trigger A: ...
- Trigger B: ...

Hard rule:
- Если движок участвует в canon-impacting changes — он обязан быть указан в governance pipeline.

---

## 5) INPUTS (STRICT FORMAT)

Для каждого input опиши:

### 5.1 <INPUT_ARTIFACT_NAME>
REQUIRED: YES|NO  
FORMAT: TODO (минимальный обязательный формат)  
SOURCE: TODO (откуда приходит)  
VALIDATION: TODO (проверки)  
FAILURE: TODO (что делать если отсутствует/битый)

TEMPLATE NOTE:
- Governance inputs должны быть проверяемыми и “плоскими” (без мистики).

---

## 6) OUTPUTS (RECORDS / REPORTS) + STORAGE (MANDATORY)

### 6.1 <OUTPUT_RECORD_NAME>
TYPE: RECORD|REPORT  
STORAGE_TARGET: TODO (точный путь)  
APPEND_ONLY: YES|NO  
RETENTION: TODO (если применимо)  
LINKING: TODO (как связывается с CHANGE_ID / UID / decision)

### 6.2 OUTPUT FORMAT (CANON)
Опиши обязательные поля:

RECORD_SCHEMA:
- RECORD_ID: TODO
- DATE_UTC: TODO
- CHANGE_ID: TODO
- ENGINE_UID: TODO
- INPUT_REFS: TODO
- RESULT: PASS|FAIL|PASS_WITH_WARN|BLOCKED
- SEVERITY: S0|S1|S2|S3
- NOTES: TODO
- ACTIONS_REQUIRED: TODO
- SIGNOFF: TODO (если нужно)

Hard rule:
- Любой output должен иметь связь с CHANGE_ID (если изменение канона).

---

## 7) GATES + SEVERITY POLICY (MANDATORY)

### 7.1 RESULT SET (STRICT)
Allowed:
- PASS
- PASS_WITH_WARN
- FAIL
- BLOCKED

### 7.2 SEVERITY (STRICT)
Allowed:
- S0 — hard blocker (нельзя применять change)
- S1 — высокий риск / нужен approval
- S2 — допустимо с миграцией/планом
- S3 — косметика / инфо

### 7.3 DECISION TABLE (MAPPING)
TODO: Таблица/правила:
- Condition → RESULT → SEVERITY → Required Actions → Next Engine

Example skeleton:
- missing mandatory input → BLOCKED → S0 → provide input → rerun
- inconsistency found → FAIL → S1 → fix + rerun + audit note
- warning only → PASS_WITH_WARN → S2 → create mitigation note

Hard rule:
- Если RESULT != PASS, должен существовать список ACTIONS_REQUIRED.

---

## 8) ENGINE PROCEDURE (DETERMINISTIC STEPS)

Опиши шаги так, чтобы другой человек повторил без интерпретаций.

### 8.1 STEP-BY-STEP
1) TODO
2) TODO
3) TODO

### 8.2 TIME / ORDER RULES
TODO: Что должно происходить ДО/ПОСЛЕ (dependencies).

### 8.3 RE-RUN POLICY
TODO:
- Когда перезапуск допустим
- Что считается “идентичным входом”
- Когда нужно новый CHANGE_ID / новый record

---

## 9) DEPENDENCIES (NO HIDDEN DEPS LAW)

### 9.1 HARD vs SOFT
HARD:
- TODO
SOFT:
- TODO

### 9.2 DEPENDENCY RECORD LINE (STANDARD)
Если движок создаёт/валидирует зависимости — укажи формат:
`<FAMILY>/<ENGINE_A> -> <FAMILY>/<ENGINE_B> | TYPE:<HARD|SOFT> | WHY:<reason>`

---

## 10) FAILURE MODES + SAFETY (MANDATORY)

### 10.1 COMMON FAILURES
- Failure 1: TODO → mitigation
- Failure 2: TODO → mitigation

### 10.2 ABUSE / BYPASS PREVENTION
TODO:
- что запрещено обходить
- как фиксируется попытка обхода (audit note / blocked record)

---

## 11) EXAMPLES (GOOD / BAD) — REQUIRED

### 11.1 GOOD EXAMPLE
INPUT: TODO (минимальный пример)
OUTPUT: TODO (пример record/report)
RESULT: PASS

### 11.2 BAD EXAMPLE
INPUT: TODO
OUTPUT: TODO
RESULT: FAIL/BLOCKED
WHY: TODO

### 11.3 EDGE CASES
- Edge A: TODO
- Edge B: TODO

Hard rule:
- Без examples движок не считается эталонным.

---

## 12) COMPATIBILITY NOTES (WITH THE SYSTEM)

TODO: Куда этот движок “втыкается” в пайплайн:
- upstream engines:
- downstream engines:
- which logs updated:
- which indices touched (если применимо):

---

## 13) COMPLIANCE CHECKLIST (MUST PASS)

- [ ] Header filled (STATUS/LOCK/VERSION/UID/ROLE)
- [ ] Mini-contract filled (CONSUMES/PRODUCES/DEPENDS_ON/OUTPUT_TARGET)
- [ ] Outputs have storage targets
- [ ] Gate mapping exists (RESULT + SEVERITY + actions)
- [ ] Procedure is deterministic
- [ ] No hidden dependencies
- [ ] Examples + edge cases exist
- [ ] Raw-only references (if any)
- [ ] No duplicated STATUS/LOCK fields below header

--- END.

LOCK: <OPEN|FIXED>
