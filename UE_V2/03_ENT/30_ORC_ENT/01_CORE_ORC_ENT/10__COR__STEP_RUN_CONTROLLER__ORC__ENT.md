FILE: UE_V2/03_ENT/30_ORC_ENT/01_CORE_ORC_ENT/10__COR__STEP_RUN_CONTROLLER__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 01_CORE_ORC_ENT
DOC_TYPE: ORC_ENTITY_MODULE
DOMAIN: COR_ORC_ENT
KEY: COR.STEP_RUN_CONTROLLER
UID: UE.V2.ENT.ORC.COR.STEP_RUN_CONTROLLER.001
VERSION: 1.1.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-09
OWNER: ORC_ENT
NAV_RULE: RAW-only enforcement (KEY->IDX->RAW)

---

## [M] ROLE
Step-run controller.

Consumes `DISPATCH_CONTEXT.PHASE_PLAN` and advances **one phase per user "го"**.
This module is the cadence manager: it does not generate domain content, it opens the correct keys for the current phase and hands off to PIPE execution.

---

## [M] PURPOSE
- Turn a PHASE_PLAN into a sequence of atomic “phase steps”.
- Ensure explicit user consent for each phase (default command: "го").
- Keep determinism: same inputs => same phase progression.
- Prevent context pollution by enforcing **per-phase** open-key budgets.
- Standardize PASS/FAIL/GAP outputs and next prompt.

---

## [M] HARD_RULES
- Keys-only outputs (never RAW or PATH).
- Do not execute pipe logic; only prepare/open/gate/hand off.
- Use the PHASE as the atomic unit (not a random 1–3 key step).
- Per-phase budget enforcement:
  - `PHASE_NOISE_BUDGET = DISPATCH_CONTEXT.PHASE_NOISE_BUDGET || ROUTE_TOKEN.NOISE_BUDGET || 12`
  - If OPEN_PLAN_KEYS > budget → FAIL.NOISE_BUDGET_VIOLATION
- If required inputs missing → FAIL (no guessing).
- If needed key not reachable (NAV proof) → GAP.KEY_NOT_REACHABLE

---

## [M] INPUTS
- ROUTE_TOKEN (required)
  - DOMAIN
  - ARTIFACT_TYPE
  - EXEC_MODE
  - NOISE_BUDGET (optional)
  - TRACE_FLAGS (optional)

- DISPATCH_CONTEXT (required, from COR.PIPE_DISPATCHER)
  - PIPE_KEY
  - PIPE_KIND
  - PHASE_PLAN: [PHASE...]
  - REQUIRED_IDX: ["KEY"...]
  - REQUIRED_CHECKS: ["CHECK.*"...]
  - DISPATCH:
      TARGET_LAYER: "PIPE"
      NEXT_MODULE_KEY: "COR.STEP_RUN_CONTROLLER"
      NEXT_PROMPT: "го"

- RUN_STATE (optional)
  - PHASE_CURSOR (optional)     # index in PHASE_PLAN, default 0
  - PHASE_HISTORY (optional)
  - LAST_STATUS (optional)

- USER_COMMAND (optional)
  - TEXT ("го" | "повтори" | "стоп")

---

## [M] OUTPUTS
- STEP_RUN_PLAN (keys-only)
  - PHASE_ID: "S0|S1|..."
  - PHASE_NAME: "<NAME>"
  - OPEN_KEYS: ["KEY"...]                 # from PHASE.OPEN_PLAN_KEYS
  - VALIDATE_CHECKS: ["CHECK.*"...]       # merged checks (stable order)
  - EXPECTED_OUTPUT_KEYS: ["TOKEN"...]
  - STOP_RULE: "<TEXT>"
  - HANDOFF:
      NEXT_LAYER: "PIPE"
      NEXT_MODULE_KEY: "<PIPE_KEY>"
      NEXT_PROMPT: "го"
  - CONTEXT_BUDGET:
      PHASE_NOISE_BUDGET: 12
      OPEN_KEYS_COUNT: <n>

- STATUS: PASS | FAIL | GAP
- FAIL_CODE or GAP_CODE
- REQUIRED_FIX (on FAIL/GAP)
- NEXT_PROMPT (always, default "го")

---

## [M] PHASE (schema)
PHASE:
  PHASE_ID: "S0|S1|..."
  PHASE_NAME: "..."
  OPEN_PLAN_KEYS: ["KEY"...]
  EXPECTED_OUTPUT_KEYS: ["TOKEN"...]
  STOP_RULE: "..."
  NEXT_PROMPT: "го"

---

## [M] DETERMINISTIC LOGIC (v1.1)

### D0) Normalize user command
Default if missing: USER_COMMAND.TEXT = "го"

Recognized:
- "го" => advance
- "повтори" => re-emit current STEP_RUN_PLAN (no cursor change)
- "стоп" => FAIL.USER_STOP

Unrecognized => FAIL.UNKNOWN_COMMAND

### D1) Preconditions
FAIL if:
- ROUTE_TOKEN missing
- DISPATCH_CONTEXT missing
- PIPE_KEY missing
- PHASE_PLAN missing or empty

FAIL_CODE:
- FAIL.INPUT_MISSING
- FAIL.DISPATCH_CONTEXT_INVALID

### D2) Cursor
CURSOR = RUN_STATE.PHASE_CURSOR if present else 0

If CURSOR >= len(PHASE_PLAN):
- PASS with PRODUCE = ["OUT.RUN_COMPLETE"]
- NEXT_PROMPT = "го"
- HANDOFF.NEXT_LAYER = "CORE"
- HANDOFF.NEXT_MODULE_KEY = "COR.RELEASE_PACKAGER"

### D3) Build current phase step plan
PHASE = PHASE_PLAN[CURSOR]

Budget:
- PHASE_NOISE_BUDGET = DISPATCH_CONTEXT.PHASE_NOISE_BUDGET || ROUTE_TOKEN.NOISE_BUDGET || 12

Validate:
- len(PHASE.OPEN_PLAN_KEYS) <= PHASE_NOISE_BUDGET
- PHASE.OPEN_PLAN_KEYS not empty
- PIPE_KEY present in DISPATCH_CONTEXT

If budget violated:
- FAIL.NOISE_BUDGET_VIOLATION
- REQUIRED_FIX: "Split phase into sub-phase(s) or reduce OPEN_PLAN_KEYS."

Checks:
- VALIDATE_CHECKS = dedup( DISPATCH_CONTEXT.REQUIRED_CHECKS + ROUTE_TOKEN.REQUIRED_CHECKS + ["CHECK.NAV.KEYS_REACHABLE"] )

Emit STEP_RUN_PLAN:
- OPEN_KEYS = PHASE.OPEN_PLAN_KEYS
- EXPECTED_OUTPUT_KEYS = PHASE.EXPECTED_OUTPUT_KEYS
- STOP_RULE = PHASE.STOP_RULE
- HANDOFF.NEXT_LAYER = "PIPE"
- HANDOFF.NEXT_MODULE_KEY = DISPATCH_CONTEXT.PIPE_KEY
- NEXT_PROMPT = "го"

### D4) Advance rules
If USER_COMMAND.TEXT == "го":
- return STEP_RUN_PLAN for PHASE[CURSOR] and instruct next cursor = CURSOR+1
If USER_COMMAND.TEXT == "повтори":
- re-emit same plan, cursor unchanged

---

## [M] FAIL CODES
- FAIL.INPUT_MISSING
- FAIL.DISPATCH_CONTEXT_INVALID
- FAIL.UNKNOWN_COMMAND
- FAIL.NOISE_BUDGET_VIOLATION
- FAIL.USER_STOP

---

## [M] GAP CODES
- GAP.KEY_NOT_REACHABLE
- GAP.NAV_PROOF_MISSING

REQUIRED_FIX must specify which key(s) are unreachable and which NAV/IDX needs repair.

---

## [M] OUTPUT TEMPLATE (canonical)
STATUS: PASS
STEP_RUN_PLAN:
  PHASE_ID: "S0"
  PHASE_NAME: "INTAKE + CONSTRAINTS"
  OPEN_KEYS: ["CTL.MUS.DURATION_POLICY", "..."]
  VALIDATE_CHECKS: ["CHECK.*", "..."]
  EXPECTED_OUTPUT_KEYS: ["CONSTRAINT_FRAME", "..."]
  STOP_RULE: "constraints locked (duration/structure/language/bpm)"
  HANDOFF:
    NEXT_LAYER: "PIPE"
    NEXT_MODULE_KEY: "MUS.TRACK"
    NEXT_PROMPT: "го"
NEXT_PROMPT: "го"
