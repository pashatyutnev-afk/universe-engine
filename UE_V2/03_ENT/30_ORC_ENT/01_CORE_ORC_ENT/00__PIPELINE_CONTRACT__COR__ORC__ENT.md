FILE: UE_V2/03_ENT/30_ORC_ENT/01_CORE_ORC_ENT/00__PIPELINE_CONTRACT__COR__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 01_CORE_ORC_ENT
DOC_TYPE: PIPELINE_CONTRACT
DOMAIN: COR_ORC_ENT
UID: UE.V2.ENT.PIPE.COR_ORC_ENT.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: RAW via INDEX_MANIFEST keys only

---

## [M] PURPOSE
PIPELINE_CONTRACT defines deterministic navigation + execution rules for realm 01_CORE_ORC_ENT.
It is the only allowed way to resolve and run CORE orchestrator modules using KEYS from INDEX_MANIFEST.

## [M] HARD_RULES
- INPUT to contract is KEY-based only (no PATH routing).
- Resolution is strictly: KEY -> (INDEX_MANIFEST lookup) -> RAW (authoritative).
- If RAW exists for KEY, PATH must never be used for opening/running.
- Minimal-open policy: open only INDEX_MANIFEST + 1 target module per step.
- No bulk loading, no tree scans, no обход IDX.
- Contract never edits repository content (MODE: USAGE-ONLY).

## [M] CONTRACT_SCOPE
- REALM_ID: UE_V2/03_ENT/30_ORC_ENT/01_CORE_ORC_ENT
- INDEX_KEYSPACE: COR.*
- REQUIRED_KEYS:
  - INDEX_MANIFEST
  - PIPELINE_CONTRACT
- OPTIONAL_KEYS:
  - COR.* modules
  - LEGACY.* modules

## [M] INPUTS
- TASK_TEXT: string (required)
- MODE_HINT: FAST | RELEASE_READY | MASTERPIECE (optional)
- CONSTRAINTS: object (optional)
  - platform, duration, style, references, limits
- ROUTE_TOKEN: object (optional; if absent, builder must create)
- REQUEST: object (internal envelope)
  - ACTION: one of ACTIONS (see below)
  - KEY: target KEY (for actions needing a module)
  - PAYLOAD: action payload

## [M] OUTPUTS
- RESULT: object
  - STATUS: PASS | FAIL
  - ACTION_TAKEN: string
  - OPENED_KEYS: [KEY...]
  - ROUTE_TOKEN: object (when applicable)
  - NEXT_PROMPT: "го" | "go" (deterministic next step)
  - FAIL_CODE: string (when FAIL)
  - REQUIRED_FIX: one-line instruction (when FAIL)

## [M] ACTIONS
ACTIONS are deterministic and side-effect free (except opening referenced RAW content for read).
- RESOLVE_KEY
- OPEN_BY_KEY
- RUN_MODULE
- LIST_KEYS
- BUILD_ROUTE_TOKEN
- SELECT_PIPE
- DISPATCH_PIPE
- STEP_RUN_TICK
- FOCUS_LOOP_TICK
- FINALIZE_RUN

## [M] RESOLUTION RULES (KEY -> RAW)
R0) Always open INDEX_MANIFEST first.
R1) Find exact KEY match (case-sensitive).
R2) If entry.RAW is non-empty -> authoritative.
R3) If entry.RAW is empty -> FAIL (RAW_REQUIRED) unless action is LIST_KEYS.
R4) Never resolve through PATH when RAW exists.
R5) If KEY not found -> FAIL (KEY_NOT_FOUND).

## [M] STEP-RUN INTEGRATION (minimal cadence)
This realm is executed by step ticks. One user “го” == one tick.
Tick order (default):
T1) STEP_RUN_TICK
T2) RUN_MODULE (exactly one module) OR DISPATCH_PIPE
T3) FOCUS_LOOP_TICK
T4) FINALIZE_RUN (when gates satisfied)
Each tick must emit NEXT_PROMPT = "го" unless FINALIZE_RUN closes the run.

## [M] MODULE INVOCATION (RUN_MODULE)
RUN_MODULE requires:
- KEY: one of COR.* or LEGACY.* (existing in INDEX_MANIFEST)
- PAYLOAD: { TASK_TEXT, MODE_HINT?, CONSTRAINTS?, ROUTE_TOKEN? }

RUN_MODULE semantics:
- Open target by KEY (OPEN_BY_KEY)
- Apply module logic (conceptually)
- Return normalized RESULT with either:
  - PASS + updated ROUTE_TOKEN
  - FAIL + FAIL_CODE + REQUIRED_FIX

## [M] ROUTE_TOKEN HANDOFF (CORE contract expectations)
ROUTE_TOKEN is the single carrier of routing state across steps.
Minimum fields expected (contract-level):
- DOMAIN
- ARTIFACT_TYPE
- MODE
- PIPE_SELECTED
- DEFAULT_ORC
- REQUIRED_IDX
- REQUIRED_CHECKS
- EXEC_MODE
Contract rule:
- If ROUTE_TOKEN absent, BUILD_ROUTE_TOKEN must be executed using COR.ROUTE_TOKEN_BUILDER.
- If PIPE_SELECTED set, SELECT_PIPE + DISPATCH_PIPE are allowed (via CORE modules).

## [M] KEY ORDER (recommended deterministic path)
This is the canonical recommended order for CORE realm operations:
1) COR.TASK_INTAKE
2) COR.DOMAIN_DETECTOR
3) COR.ROUTE_TOKEN_BUILDER
4) COR.NAV_SENTINEL
5) COR.REG_SENTINEL
6) COR.XREF_SENTINEL
7) COR.KB_SENTINEL
8) COR.PIPE_SELECTOR
9) COR.PIPE_DISPATCHER
10) COR.STEP_RUN_CONTROLLER
11) COR.FOCUS_LOOP_CONTROLLER
12) COR.GATEKEEPER
13) COR.LOGGER
14) COR.FAIL_HANDLER
15) COR.RELEASE_PACKAGER
(LEGACY.* is only used when ROUTE_TOKEN explicitly requests legacy compatibility.)

## [M] LOGGING HOOKS (contract-level)
Contract does not write logs directly, but MUST request logging via COR.LOGGER when:
- ROUTE_TOKEN is created or changed
- PIPE selection changes
- Any FAIL occurs
Contract must include in RESULT:
- OPENED_KEYS
- ACTION_TAKEN
so logger can record deterministically.

## [M] FAIL CODES (realm-local)
- FAIL.INPUT_MISSING: TASK_TEXT missing or empty.
- FAIL.KEY_NOT_FOUND: KEY not present in INDEX_MANIFEST.
- FAIL.RAW_REQUIRED: KEY exists but RAW empty where required.
- FAIL.RAW_ONLY_VIOLATION: attempt to navigate via PATH when RAW exists.
- FAIL.MULTI_MODULE_TICK: attempt to run more than one module in a single tick.
- FAIL.NON_DETERMINISTIC: ambiguous action without explicit ACTION/KEY.

## [M] GATES
PASS if:
- INDEX_MANIFEST is resolvable and opened first
- KEY resolution uses RAW when present
- Exactly one module executed per step tick
- RESULT includes NEXT_PROMPT (default "го") or run is finalized

FAIL if:
- TASK_TEXT missing (FAIL.INPUT_MISSING)
- KEY not found (FAIL.KEY_NOT_FOUND)
- RAW required but missing (FAIL.RAW_REQUIRED)
- Any PATH bypass attempted (FAIL.RAW_ONLY_VIOLATION)
- More than one module executed in a tick (FAIL.MULTI_MODULE_TICK)
