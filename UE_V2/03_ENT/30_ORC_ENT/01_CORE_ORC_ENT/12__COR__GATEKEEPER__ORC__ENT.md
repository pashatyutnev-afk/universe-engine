FILE: UE_V2/03_ENT/30_ORC_ENT/01_CORE_ORC_ENT/12__COR__GATEKEEPER__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 01_CORE_ORC_ENT
DOC_TYPE: ORC_ENTITY_MODULE
DOMAIN: COR_ORC_ENT
KEY: COR.GATEKEEPER
UID: UE.V2.ENT.ORC.COR.GATEKEEPER.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: RAW-only enforcement (KEY->IDX->RAW)

---

## [M] ROLE
Gatekeeper for run completion.
Applies final gates, validates that mandatory outputs exist, selects PASS/FAIL deterministically, and emits the next prompt (default “го”).
This module does not generate domain content; it validates completeness and readiness of the run outcome.

## [M] PURPOSE
- Enforce completion criteria before output is considered valid.
- Prevent “half-done” runs from being packaged as RELEASE_READY / MASTERPIECE.
- Normalize end-state: PASS or FAIL with actionable required fixes.
- Ensure deterministic next prompt for step-run interaction.
- Provide a compact GATE_REPORT (keys-only) for LOG and RELEASE packager.

---

## [M] HARD_RULES
- Keys-only. Never output RAW or PATH.
- Deterministic decisions only: no “maybe”, no “I think”.
- Gatekeeper must not change ROUTE_TOKEN. If mismatch detected -> FAIL.ROUTE_DRIFT.
- If required deliverable is missing -> FAIL.DELIVERABLE_MISSING.
- If required check not satisfied -> FAIL.CHECK_FAILED.
- Always emit NEXT_PROMPT (default: "го").
- If MODE_HINT is RELEASE_READY or MASTERPIECE, gates are stricter (see Gate Profiles).

---

## [M] INPUTS
- ROUTE_TOKEN (required)
  - DOMAIN
  - ARTIFACT_TYPE
  - MODE_HINT (optional: FAST|RELEASE_READY|MASTERPIECE)
  - PIPE_SELECTED (optional)
  - REQUIRED_IDX: ["KEY"...]
  - REQUIRED_CHECKS: ["CHECK.*"...]
  - EXEC_MODE
  - TRACE_FLAGS (optional)
- RUN_STATE (required)
  - STATUS (optional, last known)
  - STEP_HISTORY (optional)
  - DECISION_TRAIL (optional)
  - OPENED_KEYS (optional)
- PIPE_STATE (optional, from PIPE layer)
  - PIPE_KEY
  - PIPE_STAGE (optional)
  - PIPE_OUTPUT_KEYS: ["KEY"...]          # what pipe produced (keys-only)
  - PIPE_CHECKS_PASSED: ["CHECK.*"...]    # checks satisfied
  - PIPE_CHECKS_FAILED: ["CHECK.*"...]    # checks failed
- OUTPUT_PACK (optional, from COR.RELEASE_PACKAGER candidate)
  - DELIVERABLE_KEYS: ["KEY"...]
  - SUMMARY_KEY (optional)
- CHECK_REPORT (optional)
  - PASSED: ["CHECK.*"...]
  - FAILED: ["CHECK.*"...]
  - WARN: ["CHECK.*"...]
- USER_COMMAND (optional)
  - TEXT: "го" | "повтори" | "стоп"
  - NOTE (optional)

---

## [M] OUTPUTS
- STATUS: PASS | FAIL
- GATE_REPORT (keys-only)
  - GATE_PROFILE: FAST | RELEASE_READY | MASTERPIECE
  - REQUIRED_DELIVERABLE_KEYS: ["KEY"...]
  - PRESENT_DELIVERABLE_KEYS: ["KEY"...]
  - REQUIRED_CHECKS: ["CHECK.*"...]
  - PASSED_CHECKS: ["CHECK.*"...]
  - FAILED_CHECKS: ["CHECK.*"...]
  - WARNINGS: ["WARN.*"...]               # optional internal warnings
  - DECISION: PASS | FAIL
  - REASON_CODE: "<CODE>"
  - REQUIRED_FIX: "<ONE_LINE_ACTION>"
- NEXT_MODULE_KEY
  - on PASS: "COR.RELEASE_PACKAGER" (default) OR caller-provided
  - on FAIL: "COR.FAIL_HANDLER" (default)
- NEXT_PROMPT: "го"
- FAIL_CODE (if FAIL)

---

## [M] GATE PROFILES (v1)
Gate profiles are selected by ROUTE_TOKEN.MODE_HINT:
- FAST:
  - Minimal: must have ROUTE_TOKEN, must have at least 1 deliverable key if artifact requires it.
  - Checks are advisory unless explicitly required by REQUIRED_CHECKS.
- RELEASE_READY:
  - Must have all required deliverables + all required checks passed.
  - No failed checks allowed.
- MASTERPIECE:
  - Same as RELEASE_READY + requires presence of QUALITY/CONSISTENCY checks if they exist in REQUIRED_CHECKS.
  - Requires at least one “review-ready summary” deliverable if available in OUTPUT_PACK (SUMMARY_KEY or equivalent key in deliverables).

Default if MODE_HINT missing:
- RELEASE_READY

---

## [M] DETERMINISTIC LOGIC

### D0) Normalize command
If USER_COMMAND missing -> USER_COMMAND.TEXT = "го"

Recognized:
- "го" => evaluate gates now
- "повтори" => re-emit last known GATE_REPORT if RUN_STATE has it; else evaluate normally
- "стоп" => FAIL.USER_STOP

If unrecognized:
- FAIL_CODE: FAIL.UNKNOWN_COMMAND
- REQUIRED_FIX: "Use: го | повтори | стоп"

### D1) Preconditions
FAIL if:
- ROUTE_TOKEN missing OR ROUTE_TOKEN.DOMAIN missing OR ROUTE_TOKEN.ARTIFACT_TYPE missing

FAIL_CODE:
- FAIL.INPUT_MISSING
REQUIRED_FIX:
- "Provide ROUTE_TOKEN with DOMAIN and ARTIFACT_TYPE."

### D2) Select gate profile
If ROUTE_TOKEN.MODE_HINT in [FAST, RELEASE_READY, MASTERPIECE] use it.
Else: RELEASE_READY.

### D3) Compute required deliverables (keys-only)
The required deliverables are derived deterministically:

Base set:
- REQUIRED_DELIVERABLE_KEYS = []

Rules:
1) If OUTPUT_PACK.DELIVERABLE_KEYS exists:
   - REQUIRED_DELIVERABLE_KEYS := OUTPUT_PACK.DELIVERABLE_KEYS (treat as required in RELEASE_READY/MASTERPIECE)
2) Else if PIPE_STATE.PIPE_OUTPUT_KEYS exists:
   - REQUIRED_DELIVERABLE_KEYS := PIPE_STATE.PIPE_OUTPUT_KEYS (treat as required in RELEASE_READY/MASTERPIECE)
3) Else:
   - REQUIRED_DELIVERABLE_KEYS := [] (allowed only in FAST)

Then apply profile tightening:
- FAST:
  - REQUIRED_DELIVERABLE_KEYS may be empty
- RELEASE_READY / MASTERPIECE:
  - REQUIRED_DELIVERABLE_KEYS must be non-empty
  - If empty -> FAIL.DELIVERABLE_MISSING

Masterpiece extra:
- If OUTPUT_PACK.SUMMARY_KEY exists:
  - require SUMMARY_KEY to be present in PRESENT_DELIVERABLE_KEYS
- Else:
  - no forced invention; do not fail for missing summary if it never existed

### D4) Compute present deliverables
PRESENT_DELIVERABLE_KEYS is union (stable order, dedup):
- OUTPUT_PACK.DELIVERABLE_KEYS (if any)
- PIPE_STATE.PIPE_OUTPUT_KEYS (if any)

### D5) Resolve required checks
REQUIRED_CHECKS (stable order, dedup):
- ROUTE_TOKEN.REQUIRED_CHECKS (if any)
- CHECK_REPORT.FAILED/PASSED/WARN (if present, include only those that also appear in REQUIRED_CHECKS list; do not expand scope)

Determine PASSED_CHECKS and FAILED_CHECKS:
Priority source:
1) CHECK_REPORT if present
2) Else PIPE_STATE.PIPE_CHECKS_PASSED / PIPE_CHECKS_FAILED
3) Else empty

Profile tightening:
- FAST:
  - If REQUIRED_CHECKS provided: any FAILED_CHECKS among them => FAIL.CHECK_FAILED
  - Else ignore checks
- RELEASE_READY / MASTERPIECE:
  - Any FAILED_CHECKS among REQUIRED_CHECKS => FAIL.CHECK_FAILED
  - Missing checks are treated as failed if REQUIRED_CHECKS is non-empty but no evidence of pass exists:
    - FAIL.CHECK_EVIDENCE_MISSING

### D6) Final decision
Fail reasons (priority order):
1) USER_COMMAND == "стоп" -> FAIL.USER_STOP
2) Preconditions fail -> FAIL.INPUT_MISSING
3) Drift hint (if PIPE_STATE.PIPE_KEY contradicts ROUTE_TOKEN.PIPE_SELECTED AND PIPE_SELECTED is set) -> FAIL.ROUTE_DRIFT
4) Required deliverables missing -> FAIL.DELIVERABLE_MISSING
5) Required checks failed -> FAIL.CHECK_FAILED
6) Required checks evidence missing (RELEASE_READY/MASTERPIECE) -> FAIL.CHECK_EVIDENCE_MISSING
Else PASS.

### D7) Next module selection
On PASS:
- NEXT_MODULE_KEY = "COR.RELEASE_PACKAGER"
On FAIL:
- NEXT_MODULE_KEY = "COR.FAIL_HANDLER"

NEXT_PROMPT:
- always "го"

---

## [M] FAIL CONDITIONS
- FAIL.INPUT_MISSING
- FAIL.UNKNOWN_COMMAND
- FAIL.USER_STOP
- FAIL.ROUTE_DRIFT
- FAIL.DELIVERABLE_MISSING
- FAIL.CHECK_FAILED
- FAIL.CHECK_EVIDENCE_MISSING

Each FAIL must include:
- FAIL_CODE
- REQUIRED_FIX (one-line)
- NEXT_MODULE_KEY = "COR.FAIL_HANDLER"
- NEXT_PROMPT = "го"

---

## [M] OUTPUT TEMPLATE (canonical)

On PASS:
STATUS: PASS
GATE_REPORT:
  GATE_PROFILE: "RELEASE_READY"
  REQUIRED_DELIVERABLE_KEYS: ["<KEY>", "..."]
  PRESENT_DELIVERABLE_KEYS: ["<KEY>", "..."]
  REQUIRED_CHECKS: ["CHECK.*", "..."]
  PASSED_CHECKS: ["CHECK.*", "..."]
  FAILED_CHECKS: []
  WARNINGS: []
  DECISION: PASS
  REASON_CODE: PASS.OK
  REQUIRED_FIX: ""
NEXT_MODULE_KEY: "COR.RELEASE_PACKAGER"
NEXT_PROMPT: "го"

On FAIL:
STATUS: FAIL
FAIL_CODE: FAIL.DELIVERABLE_MISSING
GATE_REPORT:
  GATE_PROFILE: "RELEASE_READY"
  REQUIRED_DELIVERABLE_KEYS: ["<KEY>", "..."]
  PRESENT_DELIVERABLE_KEYS: ["<KEY>", "..."]
  REQUIRED_CHECKS: ["CHECK.*", "..."]
  PASSED_CHECKS: ["CHECK.*", "..."]
  FAILED_CHECKS: ["CHECK.*", "..."]
  WARNINGS: []
  DECISION: FAIL
  REASON_CODE: FAIL.DELIVERABLE_MISSING
  REQUIRED_FIX: "Produce required deliverables in PIPE stage, then run gatekeeper again."
NEXT_MODULE_KEY: "COR.FAIL_HANDLER"
NEXT_PROMPT: "го"

---

## [M] GATES
PASS if:
- Keys-only output (no RAW, no PATH)
- Gate profile chosen deterministically
- REQUIRED_DELIVERABLE_KEYS satisfied for RELEASE_READY/MASTERPIECE
- REQUIRED_CHECKS are passed (or not required in FAST)
- NEXT_PROMPT is "го"

FAIL if:
- Missing/invalid ROUTE_TOKEN
- Route drift detected
- Required deliverables missing (profile-dependent)
- Required checks failed or evidence missing (profile-dependent)
- Unknown command or user stop
