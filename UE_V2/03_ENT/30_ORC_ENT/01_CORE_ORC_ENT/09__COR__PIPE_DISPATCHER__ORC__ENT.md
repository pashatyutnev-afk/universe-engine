FILE: UE_V2/03_ENT/30_ORC_ENT/01_CORE_ORC_ENT/09__COR__PIPE_DISPATCHER__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 01_CORE_ORC_ENT
DOC_TYPE: ORC_ENTITY_MODULE
DOMAIN: COR_ORC_ENT
KEY: COR.PIPE_DISPATCHER
UID: UE.V2.ENT.ORC.COR.PIPE_DISPATCHER.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: RAW-only enforcement (KEY->IDX->RAW)

---

## [M] ROLE
Pipeline dispatcher module.
Takes a selected PIPE_KEY (keys-only) and prepares deterministic dispatch context for PIPE execution.
Does not execute the pipe itself; it builds minimal open-plan + handoff instructions for the step-run controller.

## [M] PURPOSE
- Convert `PIPE_SELECTION_REPORT` into `DISPATCH_CONTEXT` (keys-only).
- Enforce anti-noise load policy: “open only what is required next”.
- Ensure PIPE is reachable via NAV proofs before any further action.
- Produce the next action as a stable prompt: "го".

---

## [M] HARD_RULES
- Keys-only. Never output RAW or PATH.
- No pipe execution here. Only dispatch preparation.
- No invention: PIPE_KEY and required indices/checks must come from inputs.
- Deterministic: same inputs => same dispatch context.
- Anti-noise: `OPEN_PLAN_KEYS` must contain at most:
  - 1 PIPE key
  - 1 PIPE entry key (optional)
  - 1 domain IDX key (optional, only if strictly required by selected pipe)
- Must preserve ROUTE_TOKEN scope; no route drift.

---

## [M] INPUTS
- ROUTE_TOKEN (required)
  - DOMAIN
  - ARTIFACT_TYPE
  - MODE_HINT (optional)
  - REQUIRED_IDX: ["KEY"...]
  - REQUIRED_CHECKS: ["CHECK.*"...]
  - EXEC_MODE
  - NOISE_BUDGET
  - TRACE_FLAGS
- PIPE_SELECTION_REPORT (required, from COR.PIPE_SELECTOR)
  - PIPE_KEY
  - PIPE_KIND
  - SELECTION_REASONS
  - REQUIRED_CHECKS
  - REQUIRED_IDX
  - PIPE_OPEN_PLAN_KEYS (must be single item)
- NAV_ACCESS_PROOF (required)
  - REALM_ACCESS_OK: true|false
  - REACHABLE_KEYS: ["KEY"...]
- OPTIONAL: REG_ACCESS_REPORT / XREF_ACCESS_REPORT / KB_ACCESS_REPORT (forward-only)

---

## [M] OUTPUTS
- DISPATCH_CONTEXT (keys-only)
  - PIPE_KEY: "<PIPE.KEY>"
  - PIPE_KIND: "DEFAULT|DOMAIN|SPECIAL"
  - PIPE_ENTRY_KEY: "<PIPE.ENTRY.KEY_OR_EMPTY>"     # optional, keys-only
  - OPEN_PLAN_KEYS: ["KEY"...]                      # minimal open plan
  - REQUIRED_IDX: ["KEY"...]
  - REQUIRED_CHECKS: ["CHECK.*"...]
  - FORWARD_REPORTS:
      REG: "OK|SKIP|UNKNOWN"
      XREF: "OK|SKIP|UNKNOWN"
      KB: "OK|SKIP|UNKNOWN"
  - DISPATCH:
      TARGET_LAYER: "PIPE"
      NEXT_MODULE_KEY: "COR.STEP_RUN_CONTROLLER"
      NEXT_PROMPT: "го"
- STATUS: PASS | FAIL | GAP
- FAIL_CODE or GAP_CODE
- REQUIRED_FIX (on GAP/FAIL)
- NEXT_MODULE_KEY (on PASS): COR.STEP_RUN_CONTROLLER
- NEXT_PROMPT: "го"

---

## [M] DISPATCH_CONTEXT SCHEMA (v1)
DISPATCH_CONTEXT:
  PIPE_KEY: "PIPE.DEFAULT"
  PIPE_KIND: "DEFAULT"
  PIPE_ENTRY_KEY: ""
  OPEN_PLAN_KEYS: ["PIPE.DEFAULT"]
  REQUIRED_IDX: ["IDX.*", ...]
  REQUIRED_CHECKS: ["CHECK.*", ...]
  FORWARD_REPORTS:
    REG: "OK"
    XREF: "OK"
    KB: "UNKNOWN"
  DISPATCH:
    TARGET_LAYER: "PIPE"
    NEXT_MODULE_KEY: "COR.STEP_RUN_CONTROLLER"
    NEXT_PROMPT: "го"

---

## [M] DETERMINISTIC LOGIC

### D0) Preconditions
FAIL if:
- ROUTE_TOKEN missing
- PIPE_SELECTION_REPORT missing
- NAV_ACCESS_PROOF missing
- NAV_ACCESS_PROOF.REALM_ACCESS_OK != true

### D1) Validate PIPE_SELECTION_REPORT shape
FAIL if:
- PIPE_SELECTION_REPORT.PIPE_KEY empty
- PIPE_SELECTION_REPORT.PIPE_OPEN_PLAN_KEYS not exactly 1 key
- PIPE_SELECTION_REPORT.PIPE_OPEN_PLAN_KEYS[0] != PIPE_SELECTION_REPORT.PIPE_KEY

FAIL_CODE: FAIL.PIPE_REPORT_INVALID

### D2) Reachability gate (index-proven)
Selected PIPE_KEY must be reachable:
- PIPE_KEY in NAV_ACCESS_PROOF.REACHABLE_KEYS

If not reachable:
- GAP_CODE: GAP.PIPE_KEY_NOT_REACHABLE
- REQUIRED_FIX: "Open required IDX so PIPE_KEY becomes reachable via NAV, then re-run selection/dispatch."

### D3) Determine PIPE_ENTRY_KEY (optional, keys-only)
Rule:
- If ROUTE_TOKEN contains an explicit pipe entry key (optional future field):
    ROUTE_TOKEN.PIPE_ENTRY_KEY -> use it (must be reachable)
- Else:
    PIPE_ENTRY_KEY = "" (empty)
Rationale:
- Dispatcher does not guess pipe internals.

If PIPE_ENTRY_KEY provided but not reachable:
- GAP_CODE: GAP.PIPE_ENTRY_NOT_REACHABLE
- REQUIRED_FIX: "Ensure PIPE_ENTRY_KEY is declared in reachable keys via required IDX."

### D4) Build minimal OPEN_PLAN_KEYS (anti-noise)
Base open plan:
- OPEN_PLAN_KEYS = [PIPE_KEY]

If PIPE_ENTRY_KEY not empty:
- OPEN_PLAN_KEYS append PIPE_ENTRY_KEY

No additional keys unless strictly required by REQUIRED_CHECKS:
- If a check explicitly demands a domain IDX (pattern: CHECK.NAV.DOMAIN_IDX_REQUIRED) AND
  ROUTE_TOKEN has DOMAIN_IDX_KEY (optional future field), then:
    append DOMAIN_IDX_KEY (must be reachable)
Otherwise:
- do not add anything.

Clamp:
- OPEN_PLAN_KEYS length must be <= 3

If clamp violated:
- FAIL_CODE: FAIL.NOISE_BUDGET_VIOLATION
- REQUIRED_FIX: "Reduce open-plan keys to <=3; move deeper opens to PIPE layer."

### D5) Forward reports (status-only)
FORWARD_REPORTS:
- If REG_ACCESS_REPORT exists and OK -> REG="OK" else "UNKNOWN"
- If XREF_ACCESS_REPORT exists and OK -> XREF="OK" else "UNKNOWN"
- If KB_ACCESS_REPORT exists and OK -> KB="OK" else "UNKNOWN"
Do not expand contents. Status-only.

### D6) Dispatch decision
On PASS:
- TARGET_LAYER: "PIPE"
- NEXT_MODULE_KEY: COR.STEP_RUN_CONTROLLER
- NEXT_PROMPT: "го"

---

## [M] FAIL CONDITIONS
FAIL.PIPE_INPUT_MISSING:
- Any required input missing

FAIL.PIPE_REPORT_INVALID:
- PIPE_SELECTION_REPORT invalid shape or contradictory

FAIL.NOISE_BUDGET_VIOLATION:
- OPEN_PLAN_KEYS exceeds limits

FAIL.NAV_ACCESS_DENIED:
- NAV_ACCESS_PROOF.REALM_ACCESS_OK != true

---

## [M] GAP CONDITIONS
GAP.PIPE_KEY_NOT_REACHABLE:
- Selected PIPE_KEY not reachable via NAV proofs

GAP.PIPE_ENTRY_NOT_REACHABLE:
- Provided PIPE_ENTRY_KEY not reachable

REQUIRED_FIX (GAP):
- Open required IDX so keys become reachable, then rerun

---

## [M] OUTPUT TEMPLATE

On PASS:
STATUS: PASS
DISPATCH_CONTEXT:
  PIPE_KEY: "<PIPE.KEY>"
  PIPE_KIND: "DEFAULT|DOMAIN|SPECIAL"
  PIPE_ENTRY_KEY: "<KEY_OR_EMPTY>"
  OPEN_PLAN_KEYS: ["<PIPE.KEY>", "<OPTIONAL_ENTRY_KEY>", "<OPTIONAL_DOMAIN_IDX_KEY>"]
  REQUIRED_IDX: ["KEY", ...]
  REQUIRED_CHECKS: ["CHECK.*", ...]
  FORWARD_REPORTS:
    REG: "OK|UNKNOWN"
    XREF: "OK|UNKNOWN"
    KB: "OK|UNKNOWN"
  DISPATCH:
    TARGET_LAYER: "PIPE"
    NEXT_MODULE_KEY: "COR.STEP_RUN_CONTROLLER"
    NEXT_PROMPT: "го"

On GAP:
STATUS: GAP
GAP_CODE: GAP.PIPE_KEY_NOT_REACHABLE
REQUIRED_FIX: "Open required IDX so PIPE_KEY becomes reachable via NAV, then re-run selection/dispatch."
DISPATCH_CONTEXT:
  PIPE_KEY: ""
  PIPE_KIND: ""
  PIPE_ENTRY_KEY: ""
  OPEN_PLAN_KEYS: []
  REQUIRED_IDX: ["KEY", ...]
  REQUIRED_CHECKS: ["CHECK.*", ...]
  FORWARD_REPORTS:
    REG: "UNKNOWN"
    XREF: "UNKNOWN"
    KB: "UNKNOWN"
  DISPATCH:
    TARGET_LAYER: "PIPE"
    NEXT_MODULE_KEY: "COR.STEP_RUN_CONTROLLER"
    NEXT_PROMPT: "го"

On FAIL:
STATUS: FAIL
FAIL_CODE: FAIL.PIPE_REPORT_INVALID
REQUIRED_FIX: "Provide valid PIPE_SELECTION_REPORT with single PIPE_OPEN_PLAN_KEYS matching PIPE_KEY."
NEXT_PROMPT: "го"

---

## [M] GATES
PASS if:
- Keys-only (no RAW, no PATH)
- PIPE_KEY validated + reachable via NAV proofs
- OPEN_PLAN_KEYS <= 3 and starts with PIPE_KEY
- NEXT_MODULE_KEY == COR.STEP_RUN_CONTROLLER
- NEXT_PROMPT == "го"
