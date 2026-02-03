FILE: UE_V2/03_ENT/30_ORC_ENT/01_CORE_ORC_ENT/10__COR__STEP_RUN_CONTROLLER__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 01_CORE_ORC_ENT
DOC_TYPE: ORC_ENTITY_MODULE
DOMAIN: COR_ORC_ENT
KEY: COR.STEP_RUN_CONTROLLER
UID: UE.V2.ENT.ORC.COR.STEP_RUN_CONTROLLER.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: RAW-only enforcement (KEY->IDX->RAW)

---

## [M] ROLE
Step-run controller module.
Controls the run cadence as a deterministic, user-driven “step loop” using the command "го".
Enforces minimal-open / anti-noise policy and produces the next step plan without executing content generation itself.

## [M] PURPOSE
- Convert current run state into a single next-step plan (one atomic action).
- Enforce step-by-step interaction: every advancement requires explicit user "го".
- Prevent context pollution: open only minimal required targets (1–3 keys).
- Keep route deterministic: no drift outside ROUTE_TOKEN scope.
- Standardize gates (PASS/FAIL/GAP) + next prompt.

---

## [M] HARD_RULES
- Keys-only. Never output RAW or PATH.
- One step = one atomic action (open/validate/produce a single output bundle).
- "го" is the only default step-advance command.
- No massive loads: strictly follow NOISE_BUDGET and anti-noise policy.
- Do not re-route here. ROUTE_TOKEN is authority; only validate and advance within it.
- Any missing mandatory input => FAIL, not “guessing”.
- Any missing required dependency key/index/pipe => GAP (needs nav resolution), not “workaround”.

---

## [M] INPUTS
- ROUTE_TOKEN (required)
  - DOMAIN
  - ARTIFACT_TYPE
  - MODE_HINT (optional)
  - PIPE_SELECTED (optional)
  - DEFAULT_ORC (optional)
  - REQUIRED_IDX: ["KEY"...]
  - REQUIRED_CHECKS: ["CHECK.*"...]
  - EXEC_MODE
  - NOISE_BUDGET (optional, default 3)
  - TRACE_FLAGS (optional)
- DISPATCH_CONTEXT (required, from COR.PIPE_DISPATCHER)
  - PIPE_KEY
  - PIPE_KIND
  - PIPE_ENTRY_KEY (optional)
  - OPEN_PLAN_KEYS
  - REQUIRED_IDX
  - REQUIRED_CHECKS
  - FORWARD_REPORTS (status-only)
  - DISPATCH:
      TARGET_LAYER
      NEXT_MODULE_KEY
      NEXT_PROMPT
- RUN_STATE (optional)
  - STEP_ID (optional)
  - STEP_HISTORY (optional)
  - LAST_STATUS (optional)
  - LAST_FAIL_CODE / LAST_GAP_CODE (optional)
- USER_COMMAND (optional)
  - TEXT (e.g., "го", "стоп", "повтори", "сверни")
  - NOTE (optional)

---

## [M] OUTPUTS
- STEP_RUN_PLAN (keys-only)
  - STEP_ID: "SR.001" ...
  - STEP_NAME: "<ONE_LINE>"
  - OPEN_KEYS: ["KEY"...]                  # keys to open now (1–3)
  - VALIDATE_CHECKS: ["CHECK.*"...]        # checks to run now
  - PRODUCE: ["OUT.*"...]                  # what artifact(s) this step yields
  - HANDOFF:
      NEXT_LAYER: "PIPE|CORE|GVN|LOG"
      NEXT_MODULE_KEY: "<KEY>"
      NEXT_PROMPT: "го"
  - CONTEXT_BUDGET:
      NOISE_BUDGET: 3
      OPEN_KEYS_COUNT: 1
- STATUS: PASS | FAIL | GAP
- FAIL_CODE or GAP_CODE
- REQUIRED_FIX (on FAIL/GAP)
- NEXT_PROMPT (always, default "го")

---

## [M] STEP MODEL (v1)
Step-run is expressed as a small finite-step cadence.
This controller is cadence-only; domain logic stays inside PIPE layer.

### Steps (default)
- SR.001 DISPATCH_VALIDATE
- SR.002 PIPE_HANDOFF_PREP
- SR.003 PIPE_STEP_EXEC_GATE
- SR.004 OUTPUT_PACKAGE_GATE

Notes:
- SR.* steps do not “generate content”; they prepare and gate execution.
- If PIPE layer has its own step-run, this controller only hands off once and then follows PIPE’s cadence.

---

## [M] DETERMINISTIC LOGIC

### D0) Normalize user command
Default command if missing:
- USER_COMMAND.TEXT = "го"

Recognized commands (minimal set):
- "го" => advance one step
- "повтори" => re-emit last STEP_RUN_PLAN (no state change)
- "стоп" => stop safely (returns FAIL with FAIL.USER_STOP)

If unrecognized:
- FAIL_CODE: FAIL.UNKNOWN_COMMAND
- REQUIRED_FIX: "Use: го | повтори | стоп"

### D1) Preconditions
FAIL if:
- ROUTE_TOKEN missing
- DISPATCH_CONTEXT missing
- DISPATCH_CONTEXT.PIPE_KEY empty
- DISPATCH_CONTEXT.OPEN_PLAN_KEYS empty

FAIL_CODE options:
- FAIL.INPUT_MISSING
- FAIL.DISPATCH_CONTEXT_INVALID

### D2) Determine current STEP_ID
If RUN_STATE.STEP_ID exists:
- use it
Else:
- start at SR.001

### D3) SR.001 DISPATCH_VALIDATE
Goal:
- validate that the controller can proceed without breaking anti-noise policy

Checks:
- OPEN_PLAN_KEYS length <= NOISE_BUDGET (default 3)
- OPEN_PLAN_KEYS[0] == PIPE_KEY
- ROUTE_TOKEN.REQUIRED_CHECKS union DISPATCH_CONTEXT.REQUIRED_CHECKS -> VALIDATE_CHECKS (dedup, stable order)

On PASS:
- produce STEP_RUN_PLAN with:
  - OPEN_KEYS = DISPATCH_CONTEXT.OPEN_PLAN_KEYS (clamped)
  - VALIDATE_CHECKS = merged checks (dedup)
  - PRODUCE = ["OUT.DISPATCH_OK"]
  - HANDOFF.NEXT_MODULE_KEY = COR.FOCUS_LOOP_CONTROLLER
  - NEXT_PROMPT = "го"

On FAIL:
- FAIL_CODE: FAIL.NOISE_BUDGET_VIOLATION | FAIL.DISPATCH_CONTEXT_INVALID
- REQUIRED_FIX: "Reduce OPEN_PLAN_KEYS to <=3 and ensure first key equals PIPE_KEY."

### D4) SR.002 PIPE_HANDOFF_PREP (after SR.001)
Goal:
- prepare handoff instruction into PIPE layer while preserving focus scope

Inputs required:
- ROUTE_TOKEN
- DISPATCH_CONTEXT
- (optional) RUN_STATE, for history only

Plan:
- OPEN_KEYS = [DISPATCH_CONTEXT.PIPE_KEY] plus optional PIPE_ENTRY_KEY (if present) (<=3)
- VALIDATE_CHECKS = ["CHECK.NAV.PIPE_REACHABLE"] plus existing REQUIRED_CHECKS (keys-only)
- PRODUCE = ["OUT.PIPE_HANDOFF_READY"]
- HANDOFF.NEXT_LAYER = "PIPE"
- HANDOFF.NEXT_MODULE_KEY = "PIPE.DEFAULT" (or DISPATCH_CONTEXT.PIPE_KEY if already a pipe module key)
- NEXT_PROMPT = "го"

If PIPE_KEY is not a PIPE module key (shape unknown):
- GAP_CODE: GAP.PIPE_KEY_SHAPE_UNKNOWN
- REQUIRED_FIX: "Ensure PIPE_KEY resolves to a pipe module key through NAV/IDX."

### D5) SR.003 PIPE_STEP_EXEC_GATE (after SR.002)
Goal:
- gate execution: confirm the user explicitly advances and scope is intact

Rules:
- If USER_COMMAND.TEXT != "го" => FAIL.UNKNOWN_COMMAND (handled by D0)
- If ROUTE_TOKEN scope changed (detected by mismatch of DOMAIN/ARTIFACT_TYPE) => FAIL.ROUTE_DRIFT

Output:
- STEP_RUN_PLAN produces ["OUT.PIPE_EXEC_AUTHORIZED"]
- HANDOFF stays in PIPE, NEXT_MODULE_KEY = DISPATCH_CONTEXT.PIPE_KEY
- NEXT_PROMPT = "го"

### D6) SR.004 OUTPUT_PACKAGE_GATE (after PIPE returns a result)
Goal:
- package outputs deterministically and close run

Required (from PIPE layer):
- PIPE_RESULT (keys-only reference summary)
  - OUT_PACK_KEYS (optional)
  - STATUS
  - NEXT (optional)

If PIPE_RESULT missing:
- GAP_CODE: GAP.PIPE_RESULT_MISSING
- REQUIRED_FIX: "Return PIPE_RESULT (keys-only) from PIPE layer to finalize."

On PASS:
- HANDOFF.NEXT_MODULE_KEY = COR.RELEASE_PACKAGER
- PRODUCE = ["OUT.READY_FOR_RELEASE_PACK"]
- NEXT_PROMPT = "го"

---

## [M] ANTI-NOISE / MIN-OPEN POLICY
Default NOISE_BUDGET = 3 keys.
OPEN_KEYS must be:
- 1 key minimum
- 3 keys maximum
- Always start with PIPE_KEY when operating in pipe-cadence steps

Violations:
- FAIL.NOISE_BUDGET_VIOLATION

---

## [M] FAIL CONDITIONS
- FAIL.INPUT_MISSING
- FAIL.DISPATCH_CONTEXT_INVALID
- FAIL.UNKNOWN_COMMAND
- FAIL.NOISE_BUDGET_VIOLATION
- FAIL.ROUTE_DRIFT
- FAIL.USER_STOP

FAIL payload must include:
- FAIL_CODE
- REQUIRED_FIX
- NEXT_PROMPT: "го"

---

## [M] GAP CONDITIONS
- GAP.PIPE_KEY_SHAPE_UNKNOWN
- GAP.PIPE_RESULT_MISSING

GAP payload must include:
- GAP_CODE
- REQUIRED_FIX
- NEXT_PROMPT: "го"

---

## [M] OUTPUT TEMPLATE (canonical)

On PASS:
STATUS: PASS
STEP_RUN_PLAN:
  STEP_ID: "SR.001"
  STEP_NAME: "DISPATCH_VALIDATE"
  OPEN_KEYS: ["<KEY>", "..."]
  VALIDATE_CHECKS: ["CHECK.*", "..."]
  PRODUCE: ["OUT.*"]
  HANDOFF:
    NEXT_LAYER: "CORE|PIPE|LOG|GVN"
    NEXT_MODULE_KEY: "<KEY>"
    NEXT_PROMPT: "го"
  CONTEXT_BUDGET:
    NOISE_BUDGET: 3
    OPEN_KEYS_COUNT: 1
NEXT_PROMPT: "го"

On GAP:
STATUS: GAP
GAP_CODE: GAP.PIPE_RESULT_MISSING
REQUIRED_FIX: "Return PIPE_RESULT (keys-only) from PIPE layer to finalize."
NEXT_PROMPT: "го"

On FAIL:
STATUS: FAIL
FAIL_CODE: FAIL.UNKNOWN_COMMAND
REQUIRED_FIX: "Use: го | повтори | стоп"
NEXT_PROMPT: "го"

---

## [M] GATES
PASS if:
- Keys-only (no RAW, no PATH)
- STEP_RUN_PLAN includes OPEN_KEYS (1–3) and NEXT_PROMPT "го"
- No re-routing outside ROUTE_TOKEN scope
- Anti-noise policy satisfied

FAIL if:
- required inputs missing/invalid
- unknown command
- route drift detected
- noise budget violated

GAP if:
- required PIPE key shape/result cannot be validated with provided proofs
