FILE: UE_V2/03_ENT/30_ORC_ENT/01_CORE_ORC_ENT/11__COR__FOCUS_LOOP_CONTROLLER__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 01_CORE_ORC_ENT
DOC_TYPE: ORC_ENTITY_MODULE
DOMAIN: COR_ORC_ENT
KEY: COR.FOCUS_LOOP_CONTROLLER
UID: UE.V2.ENT.ORC.COR.FOCUS_LOOP_CONTROLLER.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: RAW-only enforcement (KEY->IDX->RAW)

---

## [M] ROLE
Focus loop controller module.
Maintains strict focus on ROUTE_TOKEN scope, prevents drift, and enforces “one focus target at a time” behavior across steps.
It does not generate domain content; it controls attention, scope, and minimal-open policy while the run progresses.

## [M] PURPOSE
- Keep the run inside ROUTE_TOKEN scope (DOMAIN / ARTIFACT_TYPE / PIPE_SELECTED).
- Prevent “context trash”: limit openings, block tree-load behavior, block side quests.
- Provide a deterministic focus plan for the next step (what is in-scope vs out-of-scope).
- Ensure repetition control: avoid re-opening the same targets unless needed by checks.
- Provide a stable “FocusState” (keys-only) used by STEP_RUN and PIPE modules.

---

## [M] HARD_RULES
- Keys-only. Never output RAW or PATH.
- FocusState is authoritative for “what we are doing now”.
- One focus target at a time (FOCUS_KEY) + optional 1–2 supporting keys (SUPPORT_KEYS).
- Anti-noise always on: default NOISE_BUDGET = 3.
- No re-routing here. If routing must change -> FAIL.ROUTE_DRIFT (request new route token via router module).
- No domain logic here. Only scope control + gating + minimal plan.

---

## [M] INPUTS
- ROUTE_TOKEN (required)
  - DOMAIN
  - ARTIFACT_TYPE
  - MODE_HINT (optional)
  - PIPE_SELECTED (optional)
  - REQUIRED_IDX: ["KEY"...]
  - REQUIRED_CHECKS: ["CHECK.*"...]
  - EXEC_MODE
  - NOISE_BUDGET (optional, default 3)
  - TRACE_FLAGS (optional)
- STEP_RUN_PLAN (optional, from COR.STEP_RUN_CONTROLLER)
  - STEP_ID
  - OPEN_KEYS
  - VALIDATE_CHECKS
  - HANDOFF
- PIPE_INTENT (optional, from COR.PIPE_SELECTOR / PIPE layer)
  - PIPE_KEY
  - PIPE_STAGE (optional)
  - PIPE_GOAL (one-line)
- RUN_STATE (optional)
  - FOCUS_STATE (optional)
  - STEP_HISTORY (optional)
  - LAST_OPEN_KEYS (optional)
  - LAST_STATUS (optional)
- USER_COMMAND (optional)
  - TEXT: "го" | "сверни" | "расфокус" | "стоп" | "повтори"
  - NOTE (optional)

---

## [M] OUTPUTS
- FOCUS_STATE (keys-only)
  - FOCUS_ID: "F.001" ...
  - FOCUS_KEY: "<KEY>"                 # the single primary target key
  - SUPPORT_KEYS: ["KEY"...]           # up to 2 additional keys
  - IN_SCOPE:
      DOMAIN: "<DOMAIN>"
      ARTIFACT_TYPE: "<TYPE>"
      PIPE_KEY: "<KEY_OR_EMPTY>"
      ALLOWED_KEYS_PREFIX: ["COR.", "PIPE.", "LOG.", "NAV.", "GVN."]   # policy, not strict matching
  - EXPLICIT_BLOCKS:
      - "NO_TREE_LOAD"
      - "NO_PATH_NAV"
      - "NO_EXTRA_DOMAINS"
  - CONTEXT_BUDGET:
      NOISE_BUDGET: 3
      MAX_OPEN_KEYS: 3
  - NEXT_ACTION:
      OPEN_KEYS: ["KEY"...]            # clamped to budget
      VALIDATE_CHECKS: ["CHECK.*"...]
      NEXT_MODULE_KEY: "<KEY>"
      NEXT_PROMPT: "го"
- STATUS: PASS | FAIL
- FAIL_CODE (if FAIL)
- REQUIRED_FIX (if FAIL)
- NEXT_PROMPT (always, default "го")

Note:
- This module uses FAIL only (no “GAP taxonomy” here) because focus control must never invent missing dependencies.
  Missing required material should be escalated as FAIL.INPUT_MISSING or FAIL.SCOPE_UNRESOLVED.

---

## [M] FOCUS MODEL (v1)

### Focus layers
- Layer A: ROUTE scope (DOMAIN / ARTIFACT_TYPE / PIPE)
- Layer B: Focus target (FOCUS_KEY)
- Layer C: Supporting keys (SUPPORT_KEYS)
- Layer D: Budget (NOISE_BUDGET) + open plan (NEXT_ACTION.OPEN_KEYS)

### Default focus selection rule
Priority order:
1) STEP_RUN_PLAN.HANDOFF.NEXT_MODULE_KEY (if present)
2) PIPE_INTENT.PIPE_KEY (if present)
3) ROUTE_TOKEN.PIPE_SELECTED (if present)
4) Fallback: COR.STEP_RUN_CONTROLLER (cadence controller)

---

## [M] DETERMINISTIC LOGIC

### D0) Normalize user command
If USER_COMMAND missing:
- USER_COMMAND.TEXT = "го"

Recognized:
- "го" => proceed with next action
- "повтори" => re-emit last FOCUS_STATE (no change)
- "сверни" => tighten scope (drop SUPPORT_KEYS, keep only FOCUS_KEY)
- "расфокус" => FAIL.UNKNOWN_COMMAND (intentional: force explicit routing decision, no “free browsing”)
- "стоп" => FAIL.USER_STOP

If unrecognized:
- FAIL_CODE: FAIL.UNKNOWN_COMMAND
- REQUIRED_FIX: "Use: го | повтори | сверни | стоп"

### D1) Preconditions
FAIL if:
- ROUTE_TOKEN missing
- ROUTE_TOKEN.DOMAIN missing
- ROUTE_TOKEN.ARTIFACT_TYPE missing

FAIL_CODE:
- FAIL.INPUT_MISSING

### D2) Detect drift
Drift is any mismatch between current intent and ROUTE_TOKEN:
- STEP_RUN_PLAN / PIPE_INTENT proposes a different DOMAIN or ARTIFACT_TYPE
- PIPE_KEY not aligned with ROUTE_TOKEN.PIPE_SELECTED when PIPE_SELECTED is locked by router

If drift detected:
- FAIL_CODE: FAIL.ROUTE_DRIFT
- REQUIRED_FIX: "Request a new ROUTE_TOKEN via router; do not continue inside old scope."

### D3) Compute FOCUS_KEY
FOCUS_KEY selection:
- if STEP_RUN_PLAN.HANDOFF.NEXT_MODULE_KEY exists -> use it
- else if PIPE_INTENT.PIPE_KEY exists -> use it
- else if ROUTE_TOKEN.PIPE_SELECTED exists -> use it
- else -> use "COR.STEP_RUN_CONTROLLER"

### D4) Compute SUPPORT_KEYS
Start empty.
Add at most 2 keys, deterministic order:
1) If STEP_RUN_PLAN.OPEN_KEYS exists -> take first key that is not FOCUS_KEY
2) If PIPE_INTENT.PIPE_KEY exists and not equal to FOCUS_KEY -> add it
3) If ROUTE_TOKEN.REQUIRED_IDX exists -> add the first IDX key only if needed by checks (keys-only policy)

Clamp:
- SUPPORT_KEYS length <= 2
- Total (FOCUS_KEY + SUPPORT_KEYS) <= NOISE_BUDGET (default 3)

If budget violated:
- Drop SUPPORT_KEYS from the end until within budget.

### D5) Build NEXT_ACTION
NEXT_ACTION.OPEN_KEYS:
- Start with [FOCUS_KEY]
- Append SUPPORT_KEYS
- If STEP_RUN_PLAN.OPEN_KEYS exists, merge but clamp to budget (stable order, dedup)

NEXT_ACTION.VALIDATE_CHECKS:
- merge ROUTE_TOKEN.REQUIRED_CHECKS + STEP_RUN_PLAN.VALIDATE_CHECKS
- dedup, stable order

NEXT_ACTION.NEXT_MODULE_KEY:
- If STEP_RUN_PLAN.HANDOFF.NEXT_MODULE_KEY exists -> use it
- Else -> use FOCUS_KEY

NEXT_PROMPT:
- always "го"

### D6) Apply "сверни"
If USER_COMMAND.TEXT == "сверни":
- SUPPORT_KEYS = []
- NEXT_ACTION.OPEN_KEYS = [FOCUS_KEY]
- STATUS remains PASS

---

## [M] ANTI-NOISE / MIN-OPEN POLICY
Defaults:
- NOISE_BUDGET = 3
- MAX_OPEN_KEYS = 3
- FOCUS_KEY always included
- SUPPORT_KEYS optional, max 2

Forbidden:
- opening >3 keys
- loading directory trees
- PATH-based navigation
- pulling unrelated domains/realms

Violations:
- FAIL.NOISE_BUDGET_VIOLATION (only if cannot be resolved by clamping, which should be rare)

---

## [M] FAIL CONDITIONS
- FAIL.INPUT_MISSING
- FAIL.UNKNOWN_COMMAND
- FAIL.ROUTE_DRIFT
- FAIL.NOISE_BUDGET_VIOLATION
- FAIL.USER_STOP

FAIL payload must include:
- FAIL_CODE
- REQUIRED_FIX
- NEXT_PROMPT: "го"

---

## [M] OUTPUT TEMPLATE (canonical)

On PASS:
STATUS: PASS
FOCUS_STATE:
  FOCUS_ID: "F.001"
  FOCUS_KEY: "<KEY>"
  SUPPORT_KEYS: ["<KEY>", "<KEY>"]
  IN_SCOPE:
    DOMAIN: "<DOMAIN>"
    ARTIFACT_TYPE: "<TYPE>"
    PIPE_KEY: "<KEY_OR_EMPTY>"
    ALLOWED_KEYS_PREFIX: ["COR.", "PIPE.", "LOG.", "NAV.", "GVN."]
  EXPLICIT_BLOCKS:
    - "NO_TREE_LOAD"
    - "NO_PATH_NAV"
    - "NO_EXTRA_DOMAINS"
  CONTEXT_BUDGET:
    NOISE_BUDGET: 3
    MAX_OPEN_KEYS: 3
  NEXT_ACTION:
    OPEN_KEYS: ["<KEY>", "..."]
    VALIDATE_CHECKS: ["CHECK.*", "..."]
    NEXT_MODULE_KEY: "<KEY>"
    NEXT_PROMPT: "го"
NEXT_PROMPT: "го"

On FAIL:
STATUS: FAIL
FAIL_CODE: FAIL.ROUTE_DRIFT
REQUIRED_FIX: "Request a new ROUTE_TOKEN via router; do not continue inside old scope."
NEXT_PROMPT: "го"

---

## [M] GATES
PASS if:
- Keys-only (no RAW, no PATH)
- One primary focus key is set
- Total open keys <= budget
- No drift outside ROUTE_TOKEN scope
- NEXT_PROMPT is "го"

FAIL if:
- ROUTE_TOKEN missing / invalid
- unknown command
- route drift detected
- noise budget cannot be enforced safely
