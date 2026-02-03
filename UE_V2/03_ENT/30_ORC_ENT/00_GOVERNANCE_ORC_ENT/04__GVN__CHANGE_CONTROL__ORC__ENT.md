FILE: UE_V2/03_ENT/30_ORC_ENT/00_GOVERNANCE_ORC_ENT/04__GVN__CHANGE_CONTROL__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 00_GOVERNANCE_ORC_ENT
DOC_TYPE: ORC_MODULE
DOMAIN: GVN_ORC_ENT
MODULE: GVN.CHANGE_CONTROL
UID: UE.V2.ENT.ORC.GVN.CHANGE_CONTROL.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-03
OWNER: ORC_ENT
NAV_RULE: Use KEYS only (RAW resolved via INDEX_MANIFEST)

---

## [M] ROLE
Change Control router for governance actions.

Функции:
- классифицирует запрос на изменение (тип, зона риска, затрагиваемые реалмы)
- определяет допустимость изменения в текущем MODE (особенно REPO)
- назначает обязательные проверки (REQUIRED_CHECKS)
- определяет обязательные лог-артефакты (REQUIRED_LOG_KEYS)
- формирует CHANGE_PLAN (что менять, где, какой контракт, какие ограничения)

В MODE REPO модуль не меняет файлы и не создаёт записи.
Он возвращает детерминированный план: что *должно* быть сделано и какие гейты должны пройти.

---

## [M] INPUT
- GOVN_TASK_TOKEN (required): object
  - token_id
  - domain (must be GVN_ORC_ENT)
  - mode (REPO|EDIT|…)
  - task_text
  - constraints (optional)
  - exec_policy (optional)
  - run_intent (optional)

- ROUTE_TOKEN (optional): object
  - DOMAIN
  - ARTIFACT_TYPE
  - MODE
  - PIPE_SELECTED
  - REQUIRED_IDX
  - REQUIRED_CHECKS
  - EXEC_MODE

- PROPOSED_CHANGE (optional): object
  - change_type (see CHANGE_TYPES)
  - target_keys (array[string])
  - target_paths (array[string])  # reference only, not for nav
  - scope_tags (array[string])
  - notes

---

## [M] OUTPUT
- CHANGE_CLASS: object
  - change_type
  - change_level (LOW|MED|HIGH|CRITICAL)
  - touches_realms: array[string]  # e.g. [ENT, PIPE, NAV, KB, REG, XREF, LOG]
  - can_execute_now: true|false
  - reason_if_blocked: string

- REQUIRED_CHECKS: array[string]
- REQUIRED_LOG_KEYS: array[string]
- CHANGE_PLAN: object
  - plan_id
  - target_keys: array[string]
  - operations: array[object]
    - op_id
    - op_kind (ADD|UPDATE|DEPRECATE|RENAME|MOVE|LINK|UNLINK|AUDIT_ONLY)
    - target_key
    - constraints
    - required_checks
    - required_logs
  - ordering_rule: string
  - rollback_rule: string

- NOTES: short string

---

## [M] CHANGE_TYPES (canonical)
- DOC_CREATE
- DOC_UPDATE
- DOC_DEPRECATE
- DOC_MOVE_RENAME
- INDEX_UPDATE
- NAV_RULE_CHANGE
- PIPE_CONTRACT_CHANGE
- KB_SCOPE_CHANGE
- REG_ENTRY_CHANGE
- XREF_LINK_CHANGE
- LOG_POLICY_CHANGE
- SAFETY_POLICY_CHANGE
- AUDIT_ONLY

---

## [M] HARD RULES (non-negotiable)
1) KEY-ONLY NAV
- Любая операция должна ссылаться на KEY, а не на PATH.
- PATH может быть упомянут только как справка.

2) REPO MODE = NO-WRITE
- В MODE REPO любые операции (кроме AUDIT_ONLY) помечаются как can_execute_now=false.
- Возвращается план и required checks/logs.

3) Deterministic routing
- При одинаковом входе модуль отдаёт одинаковый CHANGE_PLAN (без рандома).

4) Minimal blast radius
- По умолчанию изменения ограничиваются минимальным набором сущностей.
- Любое расширение scope требует change_level поднять минимум до MED.

---

## [M] REQUIRED_CHECKS (base set)
Модуль всегда добавляет:
- CHECK.KEY_ONLY_NAV
- CHECK.CHANGE_CLASSIFIED
- CHECK.REPO_MODE_GUARD
- CHECK.ANTI_NOISE_MAXLOAD

И по типу изменения добавляет специфичные (ниже).

---

## [M] REQUIRED_LOG_KEYS (base set)
Даже в REPO (no-write) модуль требует доступность лог-реалма:
- LOG.LOG_RULES
- LOG.RUN_LOG
- LOG.DECISION_LOG
- LOG.TOKEN_ARCHIVE

Примечание: в REPO это “must be accessible”, но не “must be written”.

---

## [M] CHANGE LEVEL CLASSIFICATION (deterministic)
Rules (top-down, first match wins):

### CRITICAL
- NAV_RULE_CHANGE
- SAFETY_POLICY_CHANGE
- PIPE_CONTRACT_CHANGE (realm-level)
- LOG_POLICY_CHANGE
- Массовые операции: target_keys count > 10

### HIGH
- INDEX_UPDATE (touches multiple realms)
- KB_SCOPE_CHANGE (boundaries/outputs change)
- DOC_MOVE_RENAME (breaks references)
- REG_ENTRY_CHANGE (affects registry validity)

### MED
- DOC_UPDATE (content rules / schema / markers)
- XREF_LINK_CHANGE (introduces new link edges)
- INDEX_UPDATE (single realm, <= 10 entries)

### LOW
- AUDIT_ONLY
- DOC_CREATE (new leaf doc with no external dependencies)

---

## [M] REALM TOUCH MAP (by change type)
- DOC_CREATE / DOC_UPDATE / DOC_DEPRECATE:
  touches_realms: [ENT, LOG]
- DOC_MOVE_RENAME:
  touches_realms: [ENT, XREF, NAV, LOG]
- INDEX_UPDATE:
  touches_realms: [ENT, NAV, LOG]
- NAV_RULE_CHANGE:
  touches_realms: [NAV, PIPE, ENT, LOG]
- PIPE_CONTRACT_CHANGE:
  touches_realms: [PIPE, NAV, ENT, LOG]
- KB_SCOPE_CHANGE:
  touches_realms: [KB, XREF, LOG]
- REG_ENTRY_CHANGE:
  touches_realms: [REG, NAV, LOG]
- XREF_LINK_CHANGE:
  touches_realms: [XREF, NAV, LOG]
- LOG_POLICY_CHANGE:
  touches_realms: [LOG, NAV, PIPE]
- SAFETY_POLICY_CHANGE:
  touches_realms: [GVN, NAV, PIPE, LOG]
- AUDIT_ONLY:
  touches_realms: [LOG]

---

## [M] TYPE-SPECIFIC CHECKS
### DOC_CREATE / DOC_UPDATE
- CHECK.MARKERS_PRESENT
- CHECK.UID_FORMAT
- CHECK.VERSION_BUMP_POLICY
- CHECK.NO_ENGINE_WORDING_PUBLIC (if branding/public fields exist)

### DOC_DEPRECATE
- CHECK.DEPRECATION_NOTICE
- CHECK.XREF_BACKLINKS_SCANNED

### DOC_MOVE_RENAME
- CHECK.XREF_REWRITE_PLAN
- CHECK.NAV_KEY_STABILITY

### INDEX_UPDATE
- CHECK.INDEX_SCHEMA_V1
- CHECK.RAW_ONLY_IN_INDEX_MANIFEST
- CHECK.NO_INDEX_LINKS_INSIDE_INDEX (guard rail)

### NAV_RULE_CHANGE
- CHECK.NAV_ROOT_COMPAT
- CHECK.NO_BYPASS_PATH

### PIPE_CONTRACT_CHANGE
- CHECK.PIPE_DEFAULT_ROUTING
- CHECK.ROUTE_TOKEN_FIELDS
- CHECK.STEP_RUN_PROTOCOL_ENABLED

### KB_SCOPE_CHANGE
- CHECK.KB_BOUNDARIES_DEFINED
- CHECK.KB_INPUTS_OUTPUTS_DEFINED

### REG_ENTRY_CHANGE
- CHECK.REG_KEY_VALID
- CHECK.REG_NON_CONFLICT

### XREF_LINK_CHANGE
- CHECK.XREF_EDGE_VALID
- CHECK.CYCLE_RISK_EVAL

### LOG_POLICY_CHANGE
- CHECK.LOG_KEYS_AVAILABLE
- CHECK.LOG_RETENTION_RULES (if exists)

### SAFETY_POLICY_CHANGE
- CHECK.RISK_SAFETY_REQUIRED
- CHECK.DECISION_APPROVAL_REQUIRED

### AUDIT_ONLY
- CHECK.LOG_KEYS_AVAILABLE

---

## [M] CAN_EXECUTE_NOW (MODE gate)
Deterministic rule:
- if GOVN_TASK_TOKEN.mode == "REPO (USAGE-ONLY, NO-EDIT)" OR contains "REPO":
  can_execute_now = true only when change_type == AUDIT_ONLY
  else false
- otherwise:
  true (subject to other modules: RISK_SAFETY / DECISION_APPROVAL)

---

## [M] CHANGE_PLAN BUILD (deterministic)
Inputs used:
- PROPOSED_CHANGE.change_type (if provided)
- else infer from task_text (keyword map)
- targets:
  - if PROPOSED_CHANGE.target_keys provided: use it
  - else infer: default [PIPELINE_CONTRACT] for governance runs, or [INDEX_MANIFEST] for index tasks

### Keyword inference (minimal)
- "index / manifest / entries / key" -> INDEX_UPDATE
- "nav rule / bypass / raw only" -> NAV_RULE_CHANGE
- "pipeline contract / pipe" -> PIPE_CONTRACT_CHANGE
- "kb scope / knowledge base" -> KB_SCOPE_CHANGE
- "registry / reg" -> REG_ENTRY_CHANGE
- "xref / link" -> XREF_LINK_CHANGE
- "log rules / retention" -> LOG_POLICY_CHANGE
- "safety / risky / block" -> SAFETY_POLICY_CHANGE
- "audit / review / check" -> AUDIT_ONLY
Fallback -> DOC_UPDATE

### Ordering rule
- Always: (1) INDEX_UPDATE prerequisites, (2) target docs, (3) xref/nav adjustments, (4) log finalize

### Rollback rule (planning only)
- If change_level >= HIGH: require rollback note + previous version pointers
- If REPO: rollback_rule = "N/A (planning only)"

---

## [M] NOTES ON "GAP"
Этот модуль не создаёт отдельный статус “GAP”.
Если не хватает обязательных ключей/панелей:
- CHANGE_CLASS.can_execute_now=false
- reason_if_blocked="missing_required_keys"
и в NOTES перечисляется недостающее через KEYS.

---

## [M] EXAMPLE OUTPUT (for current thread)
Context:
- task_text: "полностью завершим говеров"
Inference:
- change_type: DOC_UPDATE (modules)
- targets: [GVN.ENTRY_GUARD, GVN.RULE_ENFORCER, GVN.DEPENDENCY_RESOLVER, GVN.CHANGE_CONTROL, GVN.RISK_SAFETY, GVN.DECISION_APPROVAL, GVN.AUDIT_LOG_BRIDGE, GVN.COMPLIANCE_REPORTER]
Mode:
- REPO => can_execute_now=false (planning only)

---

## [M] CHANGELOG
- 2026-02-03: v1.0.0 created. Deterministic change classification + checks + REPO no-write guard.
