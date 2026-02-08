FILE: UE_V2/03_ENT/30_ORC_ENT/01_CORE_ORC_ENT/13__COR__LOGGER__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 01_CORE_ORC_ENT
DOC_TYPE: ORC_ENTITY_MODULE
DOMAIN: COR_ORC_ENT
KEY: COR.LOGGER
UID: UE.V2.ENT.ORC.COR.LOGGER.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: RAW-only enforcement (KEY->IDX->RAW)

---

## [M] ROLE
Run logger for UE_V2 step-runs.
Emits run logs, decision entries, token archive hooks, and audit linkage signals using keys-only references.
Does not invent facts, does not expand scope, does not write raw URLs in outputs.

## [M] PURPOSE
- Provide deterministic, minimal-noise logging for every run.
- Capture ROUTE_TOKEN snapshots, step transitions, and decision points.
- Support audit and trace without polluting user-facing outputs.
- Produce structured LOG_EVENTS for downstream LOG realm modules (bridges/writers).

---

## [M] HARD_RULES
- Keys-only output. Never output RAW or PATH.
- No mass dumping of context. Only structured, minimal LOG_EVENTS.
- Do not mutate ROUTE_TOKEN, RUN_STATE, PIPE_STATE. Logging is side-effect free at orchestrator level.
- Every log emission is append-only semantics (no edits, no rewrites).
- Deterministic ordering of events (stable sort by EVENT_SEQ).
- If LOG endpoints are not available (keys missing), do not stop the run. Emit WARN.LOG_SINK_MISSING and continue unless explicitly required by REQUIRED_CHECKS.

---

## [M] INPUTS
- ROUTE_TOKEN (required)
  - DOMAIN
  - ARTIFACT_TYPE
  - MODE_HINT (optional)
  - PIPE_SELECTED (optional)
  - REQUIRED_IDX (optional)
  - REQUIRED_CHECKS (optional)
  - EXEC_MODE
  - TRACE_FLAGS (optional)
- RUN_STATE (required)
  - RUN_ID (optional, stable token if exists)
  - STEP (optional)
  - STEP_HISTORY (optional)
  - OPENED_KEYS (optional)
  - LAST_DECISION (optional)
- PIPE_STATE (optional)
  - PIPE_KEY (optional)
  - PIPE_STAGE (optional)
  - PIPE_OUTPUT_KEYS (optional)
- CHECK_REPORT (optional)
  - PASSED (optional)
  - FAILED (optional)
  - WARN (optional)
- GATE_REPORT (optional)
  - DECISION (optional)
  - REASON_CODE (optional)
- USER_COMMAND (optional)
  - TEXT (optional)
  - NOTE (optional)

---

## [M] OUTPUTS
- LOG_PACKET (keys-only)
  - RUN_ID: "<ID_OR_EMPTY>"
  - EVENT_SEQ_START: <int>
  - EVENT_SEQ_END: <int>
  - LOG_EVENTS: [<LOG_EVENT>...]
  - WARNINGS: ["WARN.*"...]
  - NEXT_PROMPT: "го"

Where LOG_EVENT:
- EVENT_SEQ: <int>
- EVENT_TYPE: RUN_START|STEP|ROUTE|NAV|PIPE|CHECK|DECISION|RUN_END|WARN|ERROR
- LEVEL: INFO|WARN|ERROR
- TS_HINT: "0000-00-00T00:00:00Z"    # optional placeholder, real TS handled by LOG sink
- MESSAGE: "<ONE_LINE>"
- KEYS: ["KEY"...]                   # referenced keys only
- TAGS: ["TAG"...]                   # optional tags: [CORE, TRACE, ROUTE, PIPE, GATE]
- DATA:
  - ROUTE_TOKEN_HASH (optional)
  - STEP (optional)
  - PIPE_KEY (optional)
  - FAIL_CODE (optional)
  - REASON_CODE (optional)

---

## [M] LOG SINK CONTRACT (keys-only)
COR.LOGGER does not write to files directly.
It emits LOG_PACKET intended for LOG realm endpoints (resolved elsewhere), typically:
- UE_V2/14_LOG/01__RUN_LOG.md (sink key: LOG.RUN_LOG)
- UE_V2/14_LOG/03__TOKEN_ARCHIVE.md (sink key: LOG.TOKEN_ARCHIVE)
- UE_V2/14_LOG/04__DECISION_LOG.md (sink key: LOG.DECISION_LOG)

This module references sinks by keys only:
- LOG.RUN_LOG
- LOG.TOKEN_ARCHIVE
- LOG.DECISION_LOG

If sink keys are not present in the active run’s available keyset, emit WARN.LOG_SINK_MISSING.

---

## [M] DETERMINISTIC LOGIC

### L0) Initialize sequence counters
- EVENT_SEQ_START = 1
- EVENT_SEQ increments by 1 per appended event
- EVENT_SEQ_END = last EVENT_SEQ

If RUN_STATE has prior logging offset:
- EVENT_SEQ_START = RUN_STATE.LOG_SEQ_NEXT (if provided)
Else:
- start at 1

### L1) Determine run id
- RUN_ID = RUN_STATE.RUN_ID if present
- else RUN_ID = "" (allowed)

### L2) Normalize command
If USER_COMMAND missing:
- USER_COMMAND.TEXT = "го"

### L3) Build event set (minimal)
Always attempt to emit in this order (skip if inputs missing):
1) RUN_START (if STEP_HISTORY empty or STEP indicates start)
2) ROUTE (always if ROUTE_TOKEN present)
3) STEP (if RUN_STATE.STEP present)
4) NAV (if RUN_STATE.OPENED_KEYS present and non-empty)
5) PIPE (if PIPE_STATE.PIPE_KEY present)
6) CHECK (if CHECK_REPORT present)
7) DECISION (if GATE_REPORT present OR RUN_STATE.LAST_DECISION present)
8) RUN_END (only if decision is PASS/FAIL finalized and caller indicates end-of-run)

No invention:
- If a field is absent, do not fabricate it. Emit fewer events.

### L4) ROUTE_TOKEN hash (deterministic, no crypto requirement)
To support drift detection without exposing content:
- ROUTE_TOKEN_HASH is computed by caller if available.
- If not provided, omit ROUTE_TOKEN_HASH entirely.

### L5) Warnings
Emit warnings (LEVEL: WARN) when:
- WARN.LOG_SINK_MISSING: known sink keys are not available in run context
- WARN.NO_CHECK_REPORT: REQUIRED_CHECKS exist but CHECK_REPORT absent
- WARN.NO_PIPE_STATE: PIPE_SELECTED exists but PIPE_STATE absent

Warnings never stop execution.

### L6) Errors
Emit ERROR events only when:
- ROUTE_TOKEN is missing required fields (DOMAIN, ARTIFACT_TYPE, EXEC_MODE)
- Caller provides FAIL_CODE
This module itself does not decide FAIL; it records.

---

## [M] EVENT DEFINITIONS (templates)

### RUN_START
EVENT_TYPE: RUN_START
LEVEL: INFO
MESSAGE: "Run started"
KEYS: ["COR.LOGGER"]
TAGS: ["CORE"]

### ROUTE
EVENT_TYPE: ROUTE
LEVEL: INFO
MESSAGE: "Route token attached"
KEYS: ["COR.ROUTE_TOKEN_BUILDER"]
TAGS: ["CORE", "ROUTE"]
DATA:
  ROUTE_TOKEN_HASH: "<optional>"

### STEP
EVENT_TYPE: STEP
LEVEL: INFO
MESSAGE: "Step progressed"
KEYS: ["COR.STEP_RUN_CONTROLLER"]
TAGS: ["CORE", "TRACE"]
DATA:
  STEP: "<S*>"

### NAV
EVENT_TYPE: NAV
LEVEL: INFO
MESSAGE: "Opened keys updated"
KEYS: ["COR.NAV_SENTINEL"]
TAGS: ["CORE", "NAV"]
DATA:
  # none required

### PIPE
EVENT_TYPE: PIPE
LEVEL: INFO
MESSAGE: "Pipe state observed"
KEYS: ["COR.PIPE_DISPATCHER"]
TAGS: ["CORE", "PIPE"]
DATA:
  PIPE_KEY: "<KEY>"

### CHECK
EVENT_TYPE: CHECK
LEVEL: INFO|WARN
MESSAGE: "Check report attached"
KEYS: ["COR.GATEKEEPER"]
TAGS: ["CORE", "GATE"]

### DECISION
EVENT_TYPE: DECISION
LEVEL: INFO|WARN|ERROR
MESSAGE: "Decision recorded"
KEYS: ["COR.GATEKEEPER"]
TAGS: ["CORE", "GATE"]
DATA:
  REASON_CODE: "<CODE>"
  FAIL_CODE: "<optional>"

### RUN_END
EVENT_TYPE: RUN_END
LEVEL: INFO
MESSAGE: "Run ended"
KEYS: ["COR.LOGGER"]
TAGS: ["CORE"]

---

## [M] OUTPUT TEMPLATE (canonical)

LOG_PACKET:
  RUN_ID: ""
  EVENT_SEQ_START: 1
  EVENT_SEQ_END: 6
  LOG_EVENTS:
    - EVENT_SEQ: 1
      EVENT_TYPE: RUN_START
      LEVEL: INFO
      TS_HINT: "0000-00-00T00:00:00Z"
      MESSAGE: "Run started"
      KEYS: ["COR.LOGGER"]
      TAGS: ["CORE"]
      DATA: {}

    - EVENT_SEQ: 2
      EVENT_TYPE: ROUTE
      LEVEL: INFO
      TS_HINT: "0000-00-00T00:00:00Z"
      MESSAGE: "Route token attached"
      KEYS: ["COR.ROUTE_TOKEN_BUILDER"]
      TAGS: ["CORE", "ROUTE"]
      DATA: {}

    - EVENT_SEQ: 3
      EVENT_TYPE: STEP
      LEVEL: INFO
      TS_HINT: "0000-00-00T00:00:00Z"
      MESSAGE: "Step progressed"
      KEYS: ["COR.STEP_RUN_CONTROLLER"]
      TAGS: ["CORE", "TRACE"]
      DATA:
        STEP: "S*"

    - EVENT_SEQ: 4
      EVENT_TYPE: PIPE
      LEVEL: INFO
      TS_HINT: "0000-00-00T00:00:00Z"
      MESSAGE: "Pipe state observed"
      KEYS: ["COR.PIPE_DISPATCHER"]
      TAGS: ["CORE", "PIPE"]
      DATA:
        PIPE_KEY: "PIPE.*"

    - EVENT_SEQ: 5
      EVENT_TYPE: DECISION
      LEVEL: INFO
      TS_HINT: "0000-00-00T00:00:00Z"
      MESSAGE: "Decision recorded"
      KEYS: ["COR.GATEKEEPER"]
      TAGS: ["CORE", "GATE"]
      DATA:
        REASON_CODE: "PASS.OK"

    - EVENT_SEQ: 6
      EVENT_TYPE: RUN_END
      LEVEL: INFO
      TS_HINT: "0000-00-00T00:00:00Z"
      MESSAGE: "Run ended"
      KEYS: ["COR.LOGGER"]
      TAGS: ["CORE"]
      DATA: {}
  WARNINGS: []
  NEXT_PROMPT: "го"

---

## [M] FAIL CONDITIONS (record-only)
COR.LOGGER does not decide FAIL, but if caller passes FAIL_CODE it must be recorded:
- FAIL_CODE: "<CODE>"
- Emit an ERROR event with EVENT_TYPE: ERROR and DATA.FAIL_CODE

---

## [M] GATES
PASS if:
- Output is keys-only (no RAW, no PATH)
- Event ordering is deterministic and EVENT_SEQ contiguous
- Minimal-noise policy preserved (no large dumps)
- NEXT_PROMPT is "го"

FAIL if:
- The module outputs RAW/PATH
- Non-deterministic ordering or missing EVENT_SEQ continuity
