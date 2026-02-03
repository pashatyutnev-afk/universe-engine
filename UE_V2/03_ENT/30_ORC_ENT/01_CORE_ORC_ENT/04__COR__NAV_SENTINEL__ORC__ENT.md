FILE: UE_V2/03_ENT/30_ORC_ENT/01_CORE_ORC_ENT/04__COR__NAV_SENTINEL__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 01_CORE_ORC_ENT
DOC_TYPE: ORC_ENTITY_MODULE
DOMAIN: COR_ORC_ENT
KEY: COR.NAV_SENTINEL
UID: UE.V2.ENT.ORC.COR.NAV_SENTINEL.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: RAW-only enforcement (KEY->IDX->RAW)

---

## [M] ROLE
Navigation sentinel module.
Guards the run against PATH обходы and non-deterministic loads.
Converts `ROUTE_TOKEN` + `MIN_LOAD_PLAN` into a strict `NAV_ACTION_PLAN` (KEY-only), to be executed by the runtime/nav layer.

## [M] PURPOSE
- Enforce RAW-only navigation policy at execution time.
- Prevent bypassing IDX and prevent mass loading (ANTI_NOISE).
- Ensure the run can reach required realms (REG/XREF/KB/PIPE/LOG) through required indexes.
- Produce a deterministic list of what to open next (KEYS only), and what to verify.

## [M] HARD_RULES
- Never traverse PATH. PATH is informational only and must not be used for execution.
- Do not emit RAW URLs here. This module outputs KEYS only.
- Do not open files. Only produce an action plan for the runtime/nav layer.
- Never request or load “entire trees”. Respect NOISE_BUDGET.
- Any resolution of KEY->RAW happens only through INDEX_MANIFEST (nav layer responsibility).
- If required nav anchors are missing -> FAIL (or GAP if domain index/pipe missing by token).

---

## [M] INPUTS
- ROUTE_TOKEN (required)
  - REQUIRED_IDX (keys)
  - REQUIRED_CHECKS
  - NOISE_BUDGET
  - TARGET_KEYS
  - TRACE_FLAGS
- MIN_LOAD_PLAN (required)
  - ALWAYS_OPEN_KEYS
  - THEN_OPEN_KEYS
  - TARGET_KEYS_MAX
  - TARGET_FILE_KEYS_HINT
- OPTIONAL: RUNTIME_STATE
  - already_opened_keys: [KEY...]
  - last_step: "S0|S1|S2|S3|..."

---

## [M] OUTPUTS
- NAV_ACTION_PLAN (keys only)
  - OPEN_NEXT_KEYS (ordered)
  - VERIFY_AFTER_OPEN (ordered checks)
  - REQUIRED_REALM_ACCESS (REG/XREF/KB/PIPE/LOG as symbols)
  - NAV_GUARDS (RAW-only + anti-noise)
- STATUS: PASS | FAIL | GAP
- FAIL_CODE or GAP_CODE
- NEXT_MODULE_KEY: COR.REG_SENTINEL (on PASS)
- NEXT_PROMPT: "го"

---

## [M] NAV_ACTION_PLAN SCHEMA (v1)
NAV_ACTION_PLAN:
  OPEN_NEXT_KEYS: ["<key>", ...]
  VERIFY_AFTER_OPEN: ["<check>", ...]
  REQUIRED_REALM_ACCESS: ["REALM.REG", "REALM.XREF", "REALM.KB", "REALM.PIPE", "REALM.LOG"]
  NAV_GUARDS:
    RAW_ONLY: true
    IDX_REQUIRED: true
    ANTI_NOISE:
      OPEN_FILES_MAX: <int>
      TARGET_FILES_MAX: <int>
  TARGET_RESOLUTION_HINT:
    IDX_DOMAIN_ROOT: "<key|null>"
    TARGET_FILE_KEYS_HINT: ["<key>", ...]
  DISPATCH:
    NEXT_MODULE_KEY: "COR.REG_SENTINEL"
    NEXT_PROMPT: "го"

---

## [M] DETERMINISTIC LOGIC

### N0) Preconditions
FAIL if:
- ROUTE_TOKEN missing
- MIN_LOAD_PLAN missing
- ROUTE_TOKEN.REQUIRED_IDX empty
- MIN_LOAD_PLAN.ALWAYS_OPEN_KEYS missing or empty

### N1) Compute OPEN_NEXT_KEYS (strict order)
Start with:
1) MIN_LOAD_PLAN.ALWAYS_OPEN_KEYS (keep given order)
2) MIN_LOAD_PLAN.THEN_OPEN_KEYS (keep given order)

Then add (if fits noise budget and not already listed):
3) ROUTE_TOKEN.TARGET_KEYS.IDX_DOMAIN_ROOT (if not null)
4) One (1) key from ROUTE_TOKEN.TARGET_KEYS.TARGET_FILES (first only)

Deduplicate while preserving first occurrence order.

### N2) Enforce ANTI_NOISE
Let B = ROUTE_TOKEN.NOISE_BUDGET.OPEN_FILES_MAX
- If len(OPEN_NEXT_KEYS) > B -> trim tail (never trim ALWAYS_OPEN_KEYS)
- If STILL > B after attempting to trim optional keys -> FAIL.NOISE_BUDGET_EXCEEDED

Target keys max:
- Keep ROUTE_TOKEN.NOISE_BUDGET.TARGET_FILES_MAX for later steps (do not load targets here beyond one hint).

### N3) Build VERIFY_AFTER_OPEN (ordered)
Baseline (always):
- "CHECK.NAV.RAW_ONLY"
- "CHECK.KEYS.RESOLVE_VIA_INDEX"
- "CHECK.MARKERS.MUST_LOAD"
- "CHECK.ANTI_NOISE.MIN_LOAD"

Merge ROUTE_TOKEN.REQUIRED_CHECKS.
Deduplicate.
Ordering rule:
1) CHECK.NAV.RAW_ONLY
2) CHECK.KEYS.RESOLVE_VIA_INDEX
3) CHECK.MARKERS.MUST_LOAD
4) CHECK.ANTI_NOISE.MIN_LOAD
5) everything else alpha

### N4) Required realm access declaration (symbolic)
Always require:
- REALM.REG
- REALM.XREF
- REALM.KB
- REALM.PIPE
- REALM.LOG
(Actual confirmation happens when IDX is opened; this module only declares requirement.)

### N5) GAP vs FAIL
- GAP if ROUTE_TOKEN.TARGET_KEYS.IDX_DOMAIN_ROOT is null AND ROUTE_TOKEN.DOMAIN not "UNKNOWN"
  GAP_CODE: GAP.DOMAIN_INDEX_NOT_PROVIDED
  REQUIRED_FIX: Provide/derive domain IDX key via domain detector/router.
- GAP if ROUTE_TOKEN.PIPE_SELECTED is null AND ROUTE_TOKEN.DOMAIN not "UNKNOWN"
  GAP_CODE: GAP.PIPE_NOT_SELECTED_YET
  REQUIRED_FIX: Let COR.PIPE_SELECTOR select a pipe after nav anchors confirm.

(These GAPs do not block NAV anchors; they signal missing domain specifics.)

---

## [M] FAIL CONDITIONS
FAIL.NAV_INPUT_MISSING:
- ROUTE_TOKEN or MIN_LOAD_PLAN missing

FAIL.REQUIRED_IDX_EMPTY:
- ROUTE_TOKEN.REQUIRED_IDX empty

FAIL.NOISE_BUDGET_EXCEEDED:
- OPEN_NEXT_KEYS cannot be reduced to fit OPEN_FILES_MAX without breaking ALWAYS_OPEN_KEYS

FAIL.NON_DETERMINISTIC_ORDER:
- inputs contain unordered sets without stable ordering (caller bug)
REQUIRED_FIX: Normalize inputs to stable arrays.

---

## [M] GAP CONDITIONS
GAP.DOMAIN_INDEX_NOT_PROVIDED:
- domain appears known but IDX_DOMAIN_ROOT is null

GAP.PIPE_NOT_SELECTED_YET:
- PIPE_SELECTED is null for known domain (expected before selector)

---

## [M] OUTPUT TEMPLATE

On PASS:
STATUS: PASS
NAV_ACTION_PLAN:
  OPEN_NEXT_KEYS: ["<...>"]
  VERIFY_AFTER_OPEN: ["<...>"]
  REQUIRED_REALM_ACCESS: ["REALM.REG","REALM.XREF","REALM.KB","REALM.PIPE","REALM.LOG"]
  NAV_GUARDS:
    RAW_ONLY: true
    IDX_REQUIRED: true
    ANTI_NOISE:
      OPEN_FILES_MAX: <int>
      TARGET_FILES_MAX: <int>
  TARGET_RESOLUTION_HINT:
    IDX_DOMAIN_ROOT: "<...|null>"
    TARGET_FILE_KEYS_HINT: ["<...>"]
  DISPATCH:
    NEXT_MODULE_KEY: "COR.REG_SENTINEL"
    NEXT_PROMPT: "го"

On GAP:
STATUS: GAP
GAP_CODE: GAP.<...>
REQUIRED_FIX: "<one line>"
NAV_ACTION_PLAN: <still emitted if possible>
DISPATCH:
  NEXT_MODULE_KEY: "COR.REG_SENTINEL"
  NEXT_PROMPT: "го"

On FAIL:
STATUS: FAIL
FAIL_CODE: FAIL.<...>
REQUIRED_FIX: "<one line>"
NEXT_PROMPT: "го"

---

## [M] GATES
PASS if:
- OPEN_NEXT_KEYS starts with MIN_LOAD_PLAN.ALWAYS_OPEN_KEYS in the same order
- VERIFY_AFTER_OPEN includes RAW-only + resolve-via-index + must-load marker checks
- No PATH usage, no RAW emission, keys-only plan
- Noise budget respected
- NEXT_MODULE_KEY == COR.REG_SENTINEL

GAP if:
- domain-specific IDX/pipe unresolved but nav anchors can still proceed

FAIL if:
- required inputs missing
- required idx missing
- noise budget cannot be satisfied
