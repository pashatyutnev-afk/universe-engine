# CANON AUTHORITY ENGINE (ENG) — CANON
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/00_GOVERNANCE_ENGINES/02__CANON_AUTHORITY_ENG.md

SCOPE: Universe Engine
ENTITY_GROUP: ENGINES (ENG)
LAYER: 03_SYSTEM_ENTITIES
FAMILY: 00_GOVERNANCE_ENGINES
DOC_TYPE: ENGINE
CLASS: GOVERNANCE (L1)
LEVEL: L1
STATUS: ACTIVE
VERSION: 1.0.0
UID: <UE.ENG.GOV.CANON_AUTHORITY.001>
OWNER: SYSTEM
ROLE: Final authority to ACCEPT/REJECT canon-impacting changes (decision gatekeeper)
LOCK: FIXED

---

## 0) PURPOSE (LAW)

Этот движок — **ворота канона**: он определяет, может ли изменение стать каноническим.

What this engine is for:
- принимать решение: **ACCEPT / REJECT / ACCEPT_WITH_CONDITIONS**
- фиксировать условия принятия (если есть)
- задавать “политику допуска” для изменений канона (scope & risk driven)
- обеспечивать, что **каждое решение** оставляет след в Audit Log

Primary outcome:
- на каждый change proposal есть decision record, и он зааудичен.

Non-goals (hard):
- НЕ планирует процесс правок (это Change Control)
- НЕ оценивает внутреннюю логическую целостность в деталях (это Consistency Engine + Validators)
- НЕ заменяет Decision Approval Engine (если у вас есть отдельный движок “мульти-апрувов”, он про голоса/процедуру)
- НЕ занимается версионированием и памятью истории (это Versioning & Memory)

---

## 1) BOUNDARY (ANTI-DUPLICATION)

### 1.1 Owned area (this engine owns)
- “final decision gate” для canon-impacting изменений
- стандарт decision record
- правило: “No decision without audit”
- минимальные критерии допуска (hard gates)

### 1.2 Forbidden overlap
- не владеет audit записью (только требует и триггерит её) — это Audit Log Engine
- не владеет реестром зависимостей — это Dependency Registry Engine
- не владеет оценкой риска как процессом — это Risk Safety Engine (но может требовать его вывод)

### 1.3 Interfaces
- Inputs: change proposal + impact + risk notes + affected list + optional validations
- Outputs: decision record (+ conditions)
- Enforcement: decision MUST be logged by Audit Log

---

## 2) MINI-CONTRACT (MANDATORY)

CONSUMES:
- <ARTIFACT: CHANGE_PROPOSAL>          # что хотим изменить, зачем
- <ARTIFACT: CHANGE_NOTE>              # summary/reason/impact
- <ARTIFACT: AFFECTED_FILES_LIST>      # список затронутых объектов
- <ARTIFACT: SCOPE_IMPACT_REPORT?>     # опционально: расчёт влияния (Scope Impact Engine)
- <ARTIFACT: RISK_ASSESSMENT?>         # опционально: оценка рисков (Risk Safety Engine)
- <ARTIFACT: CONSISTENCY_REPORT?>      # опционально: отчёт целостности (Consistency Engine)

PRODUCES:
- <ARTIFACT: DECISION_RECORD>          # ACCEPT/REJECT/ACCEPT_WITH_CONDITIONS
- <ARTIFACT: CONDITIONS_LIST?>         # если есть условия принятия
- <ARTIFACT: AUDIT_RECORD_REF>         # ссылка/указатель на audit record (обязательная связка)

DEPENDS_ON:
- [00_GOVERNANCE_ENGINES/01__AUDIT_LOG_ENG]  # логировать любое решение обязательно

OUTPUT_TARGET:
- `99_LOGS/LOG__CHANGES.md` (decision records) + `99_LOGS/LOG__AUDIT.md` (audit link)

---

## 3) DECISION STATES (STRICT SET)

Allowed DECISION (only):
- DECISION: ACCEPT
- DECISION: REJECT
- DECISION: ACCEPT_WITH_CONDITIONS

Forbidden:
- “maybe”, “later”, “ok but not sure”, “approved kinda”

---

## 4) OPERATION MODEL (HOW IT WORKS)

### 4.1 Trigger (when to run)
Запускается, когда:
- предлагается изменение канона (index/rules/templates/registry/engines/entities)
- предлагается добавление/удаление/переименование канонического файла
- предлагается изменение порядка/состава в индексах (особенно фиксированных)

### 4.2 Steps (deterministic)
1) Intake: принять CHANGE_PROPOSAL + CHANGE_NOTE + AFFECTED_FILES_LIST
2) Classify:
   - CANON_IMPACT: YES/NO
   - CHANGE_TYPE: PATCH/MINOR/MAJOR/...
3) Validate minimum data (Hard Gates G1..)
4) Evaluate (rule-based):
   - impact scope
   - risk severity (если нет — требование/условие)
   - consistency checks (если нет — требование/условие)
5) Emit DECISION_RECORD (+ CONDITIONS if needed)
6) Enforce audit:
   - требовать создания AUDIT_RECORD и связать DECISION_RECORD → AUDIT_RECORD_REF
   - без audit ссылка decision считается незавершённым

---

## 5) HARD GATES (ENFORCEMENT)

> Если HARD gate провален → допускается только REJECT или ACCEPT_WITH_CONDITIONS (с явным условием устранения).

- G1: Affected list exists and concrete  
  REQUIRE: каждый affected item содержит PATH и TYPE  
  FAIL: нет списка → REJECT

- G2: Canon impact declared  
  REQUIRE: CANON_IMPACT = YES/NO  
  FAIL: неизвестно → ACCEPT_WITH_CONDITIONS (указать impact)

- G3: Change rationale present  
  REQUIRE: SUMMARY + REASON + IMPACT не пустые  
  FAIL: “просто так” → REJECT

- G4: No stealth renaming/moving  
  REQUIRE: если есть MOVE/RENAME — явно OLD_PATH → NEW_PATH  
  FAIL: скрытая миграция → REJECT

- G5: Index integrity protection  
  REQUIRE: если меняется LOCK:FIXED индекс/реестр — обязателен Scope Impact Report или условия его предоставить  
  FAIL: нет оценки → ACCEPT_WITH_CONDITIONS (добавить impact report)

- G6: Audit required  
  REQUIRE: decision MUST have AUDIT_RECORD_REF  
  FAIL: audit нет → decision “INCOMPLETE” (не считается действительным)

---

## 6) OUTPUT ARTIFACTS (STANDARD FORMS)

### 6.1 DECISION RECORD (REQUIRED)
FORMAT (Markdown):

- DECISION_ID: <UE.DECISION.YYYY-MM-DD.NNN>
- DATE: YYYY-MM-DD (or ISO timestamp)
- AUTHOR: <name/role>
- DECISION: <ACCEPT|REJECT|ACCEPT_WITH_CONDITIONS>
- CANON_IMPACT: <YES|NO>
- CHANGE_TYPE: <PATCH|MINOR|MAJOR|...>
- SCOPE: <layer/family/subsystem>
- AFFECTED:
  - ITEM: <DOC|INDEX|TEMPLATE|ENGINE|REGISTRY|MAP>
    PATH: <repo path>
    UID: <optional>
- SUMMARY: <one-liner>
- REASON: <why>
- IMPACT: <what changes>
- CONDITIONS: <none|list>
- REQUIRED_CHECKS: <none|list>   # например: “run Consistency Engine”
- AUDIT_RECORD_REF: <record id / pointer>
- NOTES: <optional>

### 6.2 CONDITIONS LIST (OPTIONAL)
Используется если DECISION=ACCEPT_WITH_CONDITIONS.

Condition format:
- C1: <condition text> | TYPE:<HARD|SOFT> | OWNER:<role> | DONE_WHEN:<definition>

---

## 7) DECISION POLICY (DEFAULT RULESET v1)

### 7.1 Default accept
ACCEPT возможен, если:
- изменение маленькое (PATCH/MINOR)
- AFFECTED list полный
- impact описан
- нет конфликта с правилами/иерархией
- audit запись будет создана

### 7.2 Default reject
REJECT, если:
- нет конкретики что изменилось
- попытка “обойти индекс” (файл существует, но не в индексе, и это пытаются сделать каноном задним числом)
- попытка править канон без audit
- переименование/удаление ломает навигацию без миграционной политики

### 7.3 Accept with conditions
ACCEPT_WITH_CONDITIONS, если:
- есть идея, но нужно:
  - scope impact
  - consistency report
  - dependency update
  - migration note для rename/move

---

## 8) EDGE CASES

- “hotfix на живом каноне”  
  → допускается ACCEPT, но CONDITIONS: “добавить полноценный change note и post-audit explanation”

- “rollback / revert”  
  → решение может быть ACCEPT, но обязателен явный REASON и связь с прошлым record id

- “правка fixed индекса ради порядка”  
  → чаще ACCEPT_WITH_CONDITIONS: “обновить dependency registry + audit + consistency pass”

---

## 9) REL / XREF (UID-FIRST)

REL:
- REL: REQUIRES | TARGET_UID: <UE.ENG.GOV.AUDIT_LOG.001> | WHY: every decision must be audited
- REL: COORDINATES | TARGET_UID: <UE.ENG.GOV.CHANGE_CONTROL.###> | WHY: decisions apply to controlled change process
- REL: REQUESTS | TARGET_UID: <UE.ENG.GOV.SCOPE_IMPACT.###> | WHY: impact reports for sensitive changes
- REL: REQUESTS | TARGET_UID: <UE.ENG.GOV.RISK_SAFETY.###> | WHY: risk assessment when needed
- REL: REQUESTS | TARGET_UID: <UE.ENG.GOV.CONSISTENCY.###> | WHY: integrity checks when needed

XREF:
- XREF: Dependency changes must be mirrored in Dependency Registry Engine.

RULE:
- raw-links живут в INDEX_ALL_ENGINES.
- здесь — только стабильные UID-first связи.

--- END.
