FILE: UE_V2/03_ENT/30_ORC_ENT/00_GOVERNANCE_ORC_ENT/03__GVN__DEPENDENCY_RESOLVER__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 00_GOVERNANCE_ORC_ENT
DOC_TYPE: ORC_MODULE
DOMAIN: GVN_ORC_ENT
MODULE: GVN.DEPENDENCY_RESOLVER
UID: UE.V2.ENT.ORC.GVN.DEPENDENCY_RESOLVER.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-03
OWNER: ORC_ENT
NAV_RULE: Use KEYS only (RAW resolved via INDEX_MANIFEST)

---

## [M] ROLE
Resolves dependencies for governance actions.
Вычисляет:
- какие документы/сущности/панели обязательны
- минимальный порядок загрузки (anti-noise)
- набор REQUIRED_KEYS для NAV подтверждения
- список REQUIRED_CHECKS для ROUTE_TOKEN

Модуль не пишет файлы. В MODE REPO отдаёт только план загрузки и список KEYS.

---

## [M] INPUT
- GOVN_TASK_TOKEN (required): object
  - token_id
  - domain (must be GVN_ORC_ENT)
  - mode
  - task_text
  - constraints
  - exec_policy
  - run_intent
- ROUTE_TOKEN (optional): object
  - DOMAIN
  - ARTIFACT_TYPE
  - MODE
  - PIPE_SELECTED
  - REQUIRED_IDX
  - REQUIRED_CHECKS
  - EXEC_MODE
- REQUESTED_ACTIONS (optional): array[string]
- AVAILABLE_INDEX_KEYS (optional): array[string]
  - list of KEYS already known/confirmed from INDEX_MANIFEST

---

## [M] OUTPUT
- REQUIRED_KEYS: array[string]
- REQUIRED_CHECKS: array[string]
- MIN_LOAD_ORDER: array[object]
  - step_id
  - key
  - kind
  - why
- TARGET_KEYS: array[string]
- NOTES: short string

---

## [M] CORE POLICY (ANTI-NOISE)
Resolver всегда строит минимальный набор.

### Always-set (fixed)
These are mandatory every run:
- BOOT.START
- BOOT.RUNTIME_MANIFEST
- BOOT.TASK_ROUTER
- NAV.NAV_ROOT
- PIPE.PIPE_DEFAULT
- LOG.LOG_RULES

### Then (domain)
- DOMAIN.IDX_MANIFEST (current realm)
- DOMAIN.PIPELINE_CONTRACT (current realm)

### Then (targets)
- 1–3 target files max for current step-run iteration

---

## [M] DEPENDENCY GRAPH (GVN_ORC_ENT)

### Realm anchors (must exist as KEYS in INDEX_MANIFEST)
- INDEX_MANIFEST
- PIPELINE_CONTRACT
- GVN.ENTRY_GUARD
- GVN.RULE_ENFORCER
- GVN.DEPENDENCY_RESOLVER
- GVN.CHANGE_CONTROL
- GVN.RISK_SAFETY
- GVN.DECISION_APPROVAL
- GVN.AUDIT_LOG_BRIDGE
- GVN.COMPLIANCE_REPORTER

### Cross-realm anchors (validated via NAV_ROOT + REQUIRED_IDX)
Resolver expects these categories to be accessible via NAV:
- REG access
- XREF access
- KB access
- PIPE access
- LOG access

---

## [M] REQUIRED_CHECKS (resolver emits)
- CHECK.KEY_ONLY_NAV
- CHECK.REPO_MODE_DRY_RUN
- CHECK.ANTI_NOISE_MAXLOAD
- CHECK.ROUTE_TOKEN_FIELDS
- CHECK.NAV_ACCESS_REG
- CHECK.NAV_ACCESS_XREF
- CHECK.NAV_ACCESS_KB
- CHECK.NAV_ACCESS_PIPE
- CHECK.NAV_ACCESS_LOG

---

## [M] TARGET SELECTION RULES (deterministic)
Given GOVN_TASK_TOKEN.task_text and REQUESTED_ACTIONS:

1) If task mentions "rules / enforcement / violation / compliance"
   -> TARGET_KEYS add: GVN.RULE_ENFORCER, GVN.COMPLIANCE_REPORTER

2) If task mentions "dependencies / required docs / minimal load / resolve"
   -> TARGET_KEYS add: GVN.DEPENDENCY_RESOLVER

3) If task mentions "change / update / version / edit / replace"
   -> TARGET_KEYS add: GVN.CHANGE_CONTROL, GVN.AUDIT_LOG_BRIDGE

4) If task mentions "risk / safety / block / dangerous"
   -> TARGET_KEYS add: GVN.RISK_SAFETY

5) If task mentions "approval / escalation / decision"
   -> TARGET_KEYS add: GVN.DECISION_APPROVAL, GVN.AUDIT_LOG_BRIDGE

If none matched:
- default TARGET_KEYS: [GVN.ENTRY_GUARD, GVN.RULE_ENFORCER]

Tie-breaker order (stable):
ENTRY_GUARD > RULE_ENFORCER > DEPENDENCY_RESOLVER > CHANGE_CONTROL > RISK_SAFETY > DECISION_APPROVAL > AUDIT_LOG_BRIDGE > COMPLIANCE_REPORTER

---

## [M] MIN_LOAD_ORDER (template)
Resolver returns steps in this exact order:

S1) BOOT.START
- key: BOOT.START
- kind: BOOT
- why: entrypoint + anti-bypass policy

S2) BOOT.RUNTIME_MANIFEST
- key: BOOT.RUNTIME_MANIFEST
- kind: BOOT
- why: MUST_LOAD_SET

S3) BOOT.TASK_ROUTER
- key: BOOT.TASK_ROUTER
- kind: BOOT
- why: deterministic routing

S4) NAV.NAV_ROOT
- key: NAV.NAV_ROOT
- kind: NAV
- why: confirm access to required realms

S5) DOMAIN.IDX_MANIFEST
- key: INDEX_MANIFEST
- kind: INDEX
- why: resolve RAW via KEYS for this realm

S6) DOMAIN.PIPELINE_CONTRACT
- key: PIPELINE_CONTRACT
- kind: PIPE
- why: realm-level execution contract

S7) TARGETS (1–3)
- key: <from TARGET_KEYS, limited to 3>
- kind: FILE
- why: step-run focus

S8) PIPE.PIPE_DEFAULT
- key: PIPE.PIPE_DEFAULT
- kind: PIPE
- why: step-run handoff, routing, protocols

S9) LOG.LOG_RULES
- key: LOG.LOG_RULES
- kind: LOG
- why: ensure logging rules are known (even if no writes)

---

## [M] HARD LIMITS
- MAX_TARGET_FILES_PER_STEP: 3
- MAX_TOTAL_LOAD_KEYS_PER_STEP: 9 (anchors + idx + contract + targets)
If exceeded:
- Resolver must trim TARGET_KEYS to fit limits (deterministically by tie-breaker order)

---

## [M] NOTES ON "GAP"
Этот модуль не вводит отдельный статус "GAP" как результат.
Если чего-то нет, он возвращает:
- missing_required_keys: [..]
и предлагает next_required_key (что нужно добавить/подтвердить),
без отдельной сущности статуса.

---

## [M] EXAMPLE (typical output)
Input:
- task_text: "Finish governance orc ent modules and ensure compliance"
Output:
- REQUIRED_KEYS: [INDEX_MANIFEST, PIPELINE_CONTRACT, GVN.ENTRY_GUARD, GVN.RULE_ENFORCER, GVN.DEPENDENCY_RESOLVER]
- REQUIRED_CHECKS: [CHECK.KEY_ONLY_NAV, CHECK.REPO_MODE_DRY_RUN, CHECK.ANTI_NOISE_MAXLOAD, CHECK.ROUTE_TOKEN_FIELDS, CHECK.NAV_ACCESS_REG, ...]
- TARGET_KEYS: [GVN.RULE_ENFORCER, GVN.DEPENDENCY_RESOLVER, GVN.COMPLIANCE_REPORTER]
- MIN_LOAD_ORDER: (S1..S9 as above)

---

## [M] CHANGELOG
- 2026-02-03: v1.0.0 dependency resolver finalized (anti-noise + deterministic target selection + no GAP status)
