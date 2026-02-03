FILE: UE_V2/03_ENT/30_ORC_ENT/00_GOVERNANCE_ORC_ENT/02__GVN__RULE_ENFORCER__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 00_GOVERNANCE_ORC_ENT
DOC_TYPE: ORC_MODULE
DOMAIN: GVN_ORC_ENT
MODULE: GVN.RULE_ENFORCER
UID: UE.V2.ENT.ORC.GVN.RULE_ENFORCER.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-03
OWNER: ORC_ENT
NAV_RULE: Use KEYS only (RAW resolved via INDEX_MANIFEST)

---

## [M] ROLE
Enforces governance hard rules.
Этот модуль блокирует любые некомплаентные операции и выдаёт:
- FAIL_CODE (детерминированный)
- REQUIRED_FIXES (что конкретно исправить)
- COMPLIANCE_DECISION (ALLOW | BLOCK)

Важно: в MODE REPO (USAGE-ONLY, NO-EDIT) любые действия записи трактуются как запрещённые. Разрешён только план/описание шагов (dry-run).

---

## [M] INPUT
- GOVN_TASK_TOKEN (required): object
  - token_id
  - domain
  - mode
  - task_text
  - constraints
  - exec_policy
  - run_intent
- ROUTE_TOKEN (optional but strongly recommended): object|string
- NAV_CONFIRM (optional): object
  - nav_root_confirmed: boolean
  - required_idx_confirmed: boolean
  - reg_access_confirmed: boolean
  - xref_access_confirmed: boolean
  - kb_access_confirmed: boolean
  - pipe_access_confirmed: boolean
  - log_access_confirmed: boolean
- REQUESTED_ACTIONS (optional): array of strings
  - examples: ["open_doc", "summarize", "create_file", "write_log", "edit_file"]

---

## [M] OUTPUT
- COMPLIANCE_DECISION: "ALLOW" | "BLOCK"
- FAIL_CODE: <string or empty>
- REQUIRED_FIXES: object|array
- COMPLIANCE_FLAGS: array
- NOTES: short string (one paragraph max)

---

## [M] GOVERNANCE HARD RULESET (v1)

### R0 — Mode lock (absolute)
If GOVN_TASK_TOKEN.exec_policy.repo_mode == "USAGE-ONLY":
- writes_allowed must be false
- any requested "create/edit/write/log" actions => BLOCK

### R1 — No bypass navigation (absolute)
raw_navigation must be "KEY_ONLY".
If any step implies:
- open by PATH when RAW exists
- or mass loading folders/trees
=> BLOCK

### R2 — Anti-noise load policy (absolute)
If planned load exceeds:
- ALWAYS: START + MANIFEST + ROUTER + NAV_ROOT
- THEN: 1 domain IDX + 1–3 target files
Anything beyond is non-compliant => BLOCK

### R3 — Determinism (absolute)
If ROUTE_TOKEN present:
- must include (at least): DOMAIN, ARTIFACT_TYPE, MODE, REQUIRED_IDX, REQUIRED_CHECKS, EXEC_MODE
If missing required fields => BLOCK
If ROUTE_TOKEN absent => allow only for pre-routing stage (notes-only), otherwise BLOCK

### R4 — Traceability (required)
If run_intent.action_class is "governance_run":
- must be dry_run true in MODE REPO
If dry_run is false => BLOCK

### R5 — Input integrity (required)
- token.domain must equal "GVN_ORC_ENT"
- token.task_text must be non-empty
Else => BLOCK

### R6 — Safety (required)
If request intent is to conceal wrongdoing or explicitly evade laws/rights/systems:
- BLOCK (high severity)
Note: This rule is about intent, not about normal governance operations.

---

## [M] DETERMINISTIC EVALUATION ORDER
Evaluate rules in this fixed order and stop on first BLOCK:
1) R5 Input integrity
2) R0 Mode lock
3) R4 Traceability
4) R1 No bypass navigation
5) R2 Anti-noise
6) R3 Determinism
7) R6 Safety (intent filter)

---

## [M] COMPLIANCE FLAGS (emitted on ALLOW)
- FLAG.REPO_MODE_DRY_RUN
- FLAG.KEY_ONLY_NAV
- FLAG.ANTI_NOISE
- FLAG.DETERMINISTIC_ROUTE (if ROUTE_TOKEN ok)
- FLAG.NAV_CONFIRM_PARTIAL (if NAV_CONFIRM missing)

---

## [M] FAIL CODES (BLOCK)
- UE.FAIL.INPUT_ABSENT
- UE.FAIL.DOMAIN_MISMATCH
- UE.FAIL.REPO_WRITE_FORBIDDEN
- UE.FAIL.NAV_BYPASS
- UE.FAIL.NOISE_OVERLOAD
- UE.FAIL.ROUTE_TOKEN_INVALID
- UE.FAIL.DRY_RUN_REQUIRED
- UE.FAIL.SAFETY_BLOCK

---

## [M] REQUIRED_FIXES (templates)

### UE.FAIL.INPUT_ABSENT
REQUIRED_FIXES:
- invalid_fields: ["GOVN_TASK_TOKEN.task_text"]
- next_step: "Provide TASK_TEXT; re-run entry guard to regenerate GOVN_TASK_TOKEN."

### UE.FAIL.DOMAIN_MISMATCH
REQUIRED_FIXES:
- invalid_fields: ["GOVN_TASK_TOKEN.domain"]
- next_step: "Set domain to GVN_ORC_ENT (this realm only) or route to correct realm."

### UE.FAIL.REPO_WRITE_FORBIDDEN
REQUIRED_FIXES:
- invalid_fields: ["REQUESTED_ACTIONS"]
- next_step: "Remove any create/edit/write/log actions. Convert to dry-run plan only."

### UE.FAIL.NAV_BYPASS
REQUIRED_FIXES:
- invalid_fields: ["exec_policy.raw_navigation"]
- next_step: "Use KEY_ONLY navigation. Resolve RAW via INDEX_MANIFEST; do not open by PATH when RAW exists."

### UE.FAIL.NOISE_OVERLOAD
REQUIRED_FIXES:
- invalid_fields: ["planned_load_set"]
- next_step: "Reduce loads to: START+MANIFEST+ROUTER+NAV_ROOT, then 1 IDX and 1–3 target files."

### UE.FAIL.ROUTE_TOKEN_INVALID
REQUIRED_FIXES:
- invalid_fields: ["ROUTE_TOKEN"]
- next_step: "Re-run ROUTER to produce ROUTE_TOKEN with required fields: DOMAIN, ARTIFACT_TYPE, MODE, REQUIRED_IDX, REQUIRED_CHECKS, EXEC_MODE."

### UE.FAIL.DRY_RUN_REQUIRED
REQUIRED_FIXES:
- invalid_fields: ["GOVN_TASK_TOKEN.run_intent.dry_run"]
- next_step: "Set dry_run=true for MODE REPO (USAGE-ONLY)."

### UE.FAIL.SAFETY_BLOCK
REQUIRED_FIXES:
- invalid_fields: ["task_intent"]
- next_step: "Rewrite task to a compliant governance purpose (documentation, validation, navigation, compliance)."

---

## [M] EXAMPLES

### Example A — ALLOW (dry-run plan)
REQUESTED_ACTIONS: ["open_doc","summarize"]
Result:
- COMPLIANCE_DECISION: ALLOW
- FLAGS: [FLAG.REPO_MODE_DRY_RUN, FLAG.KEY_ONLY_NAV, FLAG.ANTI_NOISE]

### Example B — BLOCK (attempt to write)
REQUESTED_ACTIONS: ["write_log","edit_file"]
Result:
- COMPLIANCE_DECISION: BLOCK
- FAIL_CODE: UE.FAIL.REPO_WRITE_FORBIDDEN

---

## [M] CHANGELOG
- 2026-02-03: v1.0.0 rule enforcer finalized (repo-mode lock, key-only nav, anti-noise, deterministic order)
