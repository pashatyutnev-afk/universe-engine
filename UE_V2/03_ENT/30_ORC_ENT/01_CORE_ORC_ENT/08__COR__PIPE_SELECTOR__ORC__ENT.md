FILE: UE_V2/03_ENT/30_ORC_ENT/01_CORE_ORC_ENT/08__COR__PIPE_SELECTOR__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 01_CORE_ORC_ENT
DOC_TYPE: ORC_ENTITY_MODULE
DOMAIN: COR_ORC_ENT
KEY: COR.PIPE_SELECTOR
UID: UE.V2.ENT.ORC.COR.PIPE_SELECTOR.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: RAW-only enforcement (KEY->IDX->RAW)

---

## [M] ROLE
Pipeline selector module.
Chooses the best-fit pipeline for the current run using ROUTE_TOKEN + NAV proofs + checks.
Produces `PIPE_SELECTION_REPORT` (keys-only) and dispatches next step to COR.PIPE_DISPATCHER.

## [M] PURPOSE
- Deterministically pick pipeline (PIPE_KEY) without обходы.
- Enforce minimal-load / anti-noise when selecting.
- Prefer domain pipeline if declared; otherwise fallback to default.
- Provide a strict explanation trail (selection reasons) without exposing RAW/PATH.

---

## [M] HARD_RULES
- Keys-only. No RAW output. No PATH traversal.
- Do not open pipeline trees. Only decide by keys + declared availability signals.
- No invention: pipeline candidates must be declared in ROUTE_TOKEN or reachable via REQUIRED_IDX.
- Deterministic: same inputs => same selection.
- Anti-noise: selection must not request more than 1 pipe key in the plan.

---

## [M] INPUTS
- ROUTE_TOKEN (required)
  - DOMAIN
  - ARTIFACT_TYPE
  - MODE_HINT: FAST|RELEASE_READY|MASTERPIECE (optional)
  - PIPE_SELECTED (optional hint from router)
  - REQUIRED_IDX: ["KEY"...]
  - REQUIRED_CHECKS: ["CHECK.*"...]
  - EXEC_MODE
  - NOISE_BUDGET
  - TRACE_FLAGS
  - OPTIONAL: PIPE_CANDIDATES (caller-declared)
      PRIMARY: ["PIPE.KEY"...]     # ordered preference list
      FALLBACK: ["PIPE.KEY"...]    # ordered fallback list
      DEFAULT: "PIPE.KEY"          # stable default
- NAV_ACCESS_PROOF (required)
  - REALM_ACCESS_OK: true|false
  - REACHABLE_KEYS: ["KEY"...]     # keys proven reachable via index navigation
- OPTIONAL: KB_ACCESS_REPORT (from COR.KB_SENTINEL)
- OPTIONAL: XREF_ACCESS_REPORT (from COR.XREF_SENTINEL)
- OPTIONAL: REG_ACCESS_REPORT (from COR.REG_SENTINEL)

---

## [M] OUTPUTS
- PIPE_SELECTION_REPORT (keys only)
  - PIPE_KEY: "<PIPE.KEY>"
  - PIPE_KIND: "DEFAULT|DOMAIN|SPECIAL"
  - SELECTION_REASONS: ["...", ...]
  - REQUIRED_CHECKS: ["CHECK.*"...]        # carried forward for dispatcher
  - REQUIRED_IDX: ["KEY"...]              # carried forward for dispatcher
  - PIPE_OPEN_PLAN_KEYS: ["<PIPE.KEY>"]   # always single item
  - DISPATCH:
      NEXT_MODULE_KEY: "COR.PIPE_DISPATCHER"
      NEXT_PROMPT: "го"
- STATUS: PASS | FAIL | GAP
- FAIL_CODE or GAP_CODE
- NEXT_MODULE_KEY: COR.PIPE_DISPATCHER (on PASS)
- NEXT_PROMPT: "го"

---

## [M] PIPE_SELECTION_REPORT SCHEMA (v1)
PIPE_SELECTION_REPORT:
  PIPE_KEY: "PIPE.DEFAULT"
  PIPE_KIND: "DEFAULT"
  SELECTION_REASONS:
    - "fallback: no domain pipe declared"
    - "deterministic: default selected"
  REQUIRED_CHECKS: ["CHECK.*", ...]
  REQUIRED_IDX: ["IDX.*", ...]
  PIPE_OPEN_PLAN_KEYS: ["PIPE.DEFAULT"]
  DISPATCH:
    NEXT_MODULE_KEY: "COR.PIPE_DISPATCHER"
    NEXT_PROMPT: "го"

---

## [M] DETERMINISTIC LOGIC

### P0) Preconditions
FAIL if:
- ROUTE_TOKEN missing
- NAV_ACCESS_PROOF missing
- NAV_ACCESS_PROOF.REALM_ACCESS_OK != true

### P1) Build candidate list (keys-only, no invention)
Candidate sources in priority order:

1) ROUTE_TOKEN.PIPE_SELECTED (if present)
   - treat as highest-priority single candidate

2) ROUTE_TOKEN.PIPE_CANDIDATES.PRIMARY (if present)
3) ROUTE_TOKEN.PIPE_CANDIDATES.FALLBACK (if present)
4) ROUTE_TOKEN.PIPE_CANDIDATES.DEFAULT (if present)
5) Minimal implicit fallback:
   - if a key equal to "PIPE.DEFAULT" exists in either:
     - NAV_ACCESS_PROOF.REACHABLE_KEYS
     - ROUTE_TOKEN.REQUIRED_IDX
   then include "PIPE.DEFAULT" as last resort candidate

If no candidates after this:
- GAP_CODE: GAP.PIPE_CANDIDATES_EMPTY
- REQUIRED_FIX: "Declare PIPE_SELECTED or PIPE_CANDIDATES and ensure reachability via IDX."

### P2) Validate reachability of candidates (must be index-proven)
A candidate is VALID if:
- candidate in NAV_ACCESS_PROOF.REACHABLE_KEYS
  OR candidate in ROUTE_TOKEN.REQUIRED_IDX (only if REQUIRED_IDX is guaranteed index-resolved by router)

If candidate list contains items but none are VALID:
- GAP when DOMAIN == "UNKNOWN"
  GAP_CODE: GAP.PIPE_NOT_REACHABLE_YET
  REQUIRED_FIX: "Complete routing + open required IDX so pipe keys become reachable."
- else FAIL:
  FAIL_CODE: FAIL.PIPE_NOT_REACHABLE
  REQUIRED_FIX: "Add required IDX/pipe keys so they are reachable via NAV."

### P3) Choose pipeline (stable selection order)
Selection order:
1) First VALID candidate from this ordered list:
   - PIPE_SELECTED
   - PRIMARY (in given order)
   - FALLBACK (in given order)
   - DEFAULT
   - PIPE.DEFAULT (implicit last resort)

PIPE_KIND mapping:
- If selected key equals "PIPE.DEFAULT" or ends with ".DEFAULT" -> PIPE_KIND = DEFAULT
- Else if selected key contains DOMAIN token (exact match rule below) -> PIPE_KIND = DOMAIN
- Else -> PIPE_KIND = SPECIAL

DOMAIN token match rule (deterministic):
- DOMAIN_STR = ROUTE_TOKEN.DOMAIN (upper snake or dot form accepted)
- candidate contains DOMAIN_STR as a whole segment split by ["_", ".", "-"]
Examples:
- DOMAIN="MUSIC" matches "PIPE.MUSIC.MAIN"
- DOMAIN="MUSIC_PROD" matches "PIPE.MUSIC_PROD.DEFAULT"

### P4) Build selection reasons (keys-only, no narrative)
SELECTION_REASONS must include 2–5 short strings:
- one for source ("pipe_selected"/"primary"/"fallback"/"default")
- one for reachability ("reachable via NAV")
- optional for mode hint ("mode=FAST => simpler pipe" etc.)
- optional for constraints ("artifact_type requires domain pipe" if check present)

### P5) Anti-noise clamp
PIPE_OPEN_PLAN_KEYS must be exactly:
- ["<selected PIPE_KEY>"]

No additional pipe keys may be requested here.

### P6) Carry-forward checks
Carry forward:
- REQUIRED_CHECKS = ROUTE_TOKEN.REQUIRED_CHECKS (as-is)
- REQUIRED_IDX = ROUTE_TOKEN.REQUIRED_IDX (as-is)

### P7) Dispatch
On PASS:
- NEXT_MODULE_KEY: COR.PIPE_DISPATCHER
- NEXT_PROMPT: "го"

---

## [M] FAIL CONDITIONS
FAIL.PIPE_INPUT_MISSING:
- ROUTE_TOKEN or NAV_ACCESS_PROOF missing

FAIL.PIPE_NAV_ACCESS_DENIED:
- NAV_ACCESS_PROOF.REALM_ACCESS_OK != true

FAIL.PIPE_NOT_REACHABLE:
- candidates exist but none reachable for known domain

---

## [M] GAP CONDITIONS
GAP.PIPE_CANDIDATES_EMPTY:
- no candidates declared and no PIPE.DEFAULT found

GAP.PIPE_NOT_REACHABLE_YET:
- DOMAIN == "UNKNOWN" and pipe reachability not proven yet

REQUIRED_FIX (GAP):
- Ensure router provides PIPE_SELECTED or PIPE_CANDIDATES
- Ensure required IDX is opened so pipe key is in REACHABLE_KEYS

---

## [M] OUTPUT TEMPLATE

On PASS:
STATUS: PASS
PIPE_SELECTION_REPORT:
  PIPE_KEY: "<PIPE.KEY>"
  PIPE_KIND: "DEFAULT|DOMAIN|SPECIAL"
  SELECTION_REASONS:
    - "<source reason>"
    - "reachable via NAV"
  REQUIRED_CHECKS: ["CHECK.*", ...]
  REQUIRED_IDX: ["KEY", ...]
  PIPE_OPEN_PLAN_KEYS: ["<PIPE.KEY>"]
  DISPATCH:
    NEXT_MODULE_KEY: "COR.PIPE_DISPATCHER"
    NEXT_PROMPT: "го"

On GAP:
STATUS: GAP
GAP_CODE: GAP.PIPE_CANDIDATES_EMPTY
REQUIRED_FIX: "Declare PIPE_SELECTED or PIPE_CANDIDATES and ensure reachability via IDX."
PIPE_SELECTION_REPORT:
  PIPE_KEY: ""
  PIPE_KIND: ""
  SELECTION_REASONS: []
  REQUIRED_CHECKS: ["CHECK.*", ...]
  REQUIRED_IDX: ["KEY", ...]
  PIPE_OPEN_PLAN_KEYS: []
  DISPATCH:
    NEXT_MODULE_KEY: "COR.PIPE_DISPATCHER"
    NEXT_PROMPT: "го"

On FAIL:
STATUS: FAIL
FAIL_CODE: FAIL.PIPE_NOT_REACHABLE
REQUIRED_FIX: "Add required IDX/pipe keys so they are reachable via NAV."
NEXT_PROMPT: "го"

---

## [M] GATES
PASS if:
- Keys-only (no RAW, no PATH)
- Candidate list built without invention
- Selected PIPE_KEY is reachable (index-proven)
- PIPE_OPEN_PLAN_KEYS has exactly 1 key (anti-noise)
- NEXT_MODULE_KEY == COR.PIPE_DISPATCHER
