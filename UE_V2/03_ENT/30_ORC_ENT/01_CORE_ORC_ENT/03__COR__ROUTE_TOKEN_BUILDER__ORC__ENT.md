FILE: UE_V2/03_ENT/30_ORC_ENT/01_CORE_ORC_ENT/03__COR__ROUTE_TOKEN_BUILDER__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 01_CORE_ORC_ENT
DOC_TYPE: ORC_ENTITY_MODULE
DOMAIN: COR_ORC_ENT
KEY: COR.ROUTE_TOKEN_BUILDER
UID: UE.V2.ENT.ORC.COR.ROUTE_TOKEN_BUILDER.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: Resolve via INDEX_MANIFEST (KEY->RAW)

---

## [M] ROLE
Route token builder module.
Assembles a deterministic `ROUTE_TOKEN` from normalized REQUEST and ROUTING_HINTS, defining minimal load plan, required indexes/checks, and step-run execution envelope.

## [M] PURPOSE
- Convert user intent into a compact, deterministic `ROUTE_TOKEN`.
- Enforce ANTI_NOISE: minimum required fields only, no mass loading.
- Prepare the run for `COR.NAV_SENTINEL` + `COR.PIPE_SELECTOR`.
- Ensure the token is stable: same inputs -> same token.

## [M] HARD_RULES
- No external loading, no RAW output, no PATH traversal.
- Do not invent requirements; only derive from REQUEST + ROUTING_HINTS.
- Always output canonical START fields:
  DOMAIN, ARTIFACT_TYPE, MODE, PIPE_SELECTED, DEFAULT_ORC, REQUIRED_IDX, REQUIRED_CHECKS, EXEC_MODE.
- Deterministic ordering for arrays (alphabetical or fixed priority tables).
- Minimal-open policy: one domain IDX + 1–3 target files (keys only at this stage).
- MODE is USAGE-ONLY: no repo edits.

---

## [M] INPUTS
- REQUEST envelope from `COR.TASK_INTAKE` (required)
  - TASK_TEXT
  - MODE_HINT (FAST|RELEASE_READY|MASTERPIECE|empty)
  - CONSTRAINTS (platform, duration, style, references)
  - INTENT_SIGNALS (parsed flags)
- ROUTING_HINTS from `COR.DOMAIN_DETECTOR` (required)
  - DOMAIN_PRIMARY
  - ARTIFACT_TYPE
  - PIPE_SUGGESTION
  - REQUIRED_IDX_SUGGESTION
  - REQUIRED_CHECKS_SUGGESTION
- OPTIONAL: ROUTER_CONTEXT (if caller provides)
  - PRIOR_ROUTE_TOKEN (for continuation)
  - STEP_STATE (S0..Sn)

---

## [M] OUTPUTS
- ROUTE_TOKEN (canonical, minimal)
- MIN_LOAD_PLAN (keys only; resolution later via NAV/IDX)
- RUN_SEED update
  - NEXT_MODULE_KEY: COR.NAV_SENTINEL
  - NEXT_PROMPT: "го"
- STATUS: PASS | FAIL
- FAIL_CODE + REQUIRED_FIX (when FAIL)

---

## [M] ROUTE_TOKEN SCHEMA (v1)

### [M] Canon fields (required by START)
ROUTE_TOKEN:
  DOMAIN: "<domain>"
  ARTIFACT_TYPE: "<type>"
  MODE: "<FAST|RELEASE_READY|MASTERPIECE>"
  EXEC_MODE: "STEP_RUN"
  PIPE_SELECTED: "<string|null>"
  DEFAULT_ORC: "<string>"
  REQUIRED_IDX: ["<key>", ...]
  REQUIRED_CHECKS: ["<check>", ...]
  TRACE_FLAGS: ["TRACE.ON", "TRACE.MIN", ...]
  NOISE_BUDGET:
    OPEN_FILES_MAX: 4
    TARGET_FILES_MAX: 3
  TARGET_KEYS:
    IDX_DOMAIN_ROOT: "<key|null>"
    TARGET_FILES: ["<key>", ...]
  TOKEN_META:
    TOKEN_ID: "<deterministic-id>"
    TOKEN_VERSION: "1.0"
    CREATED_AT: "2026-02-02"
    UPDATED_AT: "2026-02-02"

### [M] Notes
- REQUIRED_IDX contains KEYS, not RAW/paths.
- PIPE_SELECTED may remain null until `COR.PIPE_SELECTOR`.
- DEFAULT_ORC is a symbolic owner string for routing context, not a repo pointer.

---

## [M] DETERMINISTIC BUILD LOGIC

### T0) Preconditions
- If REQUEST.TASK_TEXT missing or empty -> FAIL.INPUT_MISSING
- If ROUTING_HINTS missing OR ROUTING_HINTS.ARTIFACT_TYPE missing -> FAIL.MISSING_HINTS

### T1) Normalize MODE
MODE priority:
1) REQUEST.MODE_HINT if in {FAST, RELEASE_READY, MASTERPIECE}
2) else default "RELEASE_READY"

### T2) Set DOMAIN + ARTIFACT_TYPE
- DOMAIN = ROUTING_HINTS.DOMAIN_PRIMARY (or "UNKNOWN" if provided)
- ARTIFACT_TYPE = ROUTING_HINTS.ARTIFACT_TYPE

### T3) EXEC_MODE
- Always "STEP_RUN" for UE_V2 runtime cadence.

### T4) TRACE_FLAGS (minimal)
- Always include:
  - "TRACE.ON"
  - "TRACE.MIN"
If MODE == MASTERPIECE:
  - add "TRACE.DECISIONS"
If MODE == FAST:
  - add "TRACE.SUMMARY_ONLY"
Deterministic ordering: TRACE.ON, TRACE.MIN, TRACE.SUMMARY_ONLY, TRACE.DECISIONS

### T5) REQUIRED_CHECKS
Start with baseline (always):
- "CHECK.NAV.RAW_ONLY"
- "CHECK.ANTI_NOISE.MIN_LOAD"
- "CHECK.LOG.HOOKS_PRESENT"

Merge in ROUTING_HINTS.REQUIRED_CHECKS_SUGGESTION (if any).
Deduplicate + sort deterministically (fixed priority list below, then alpha for unknown):

Priority list (first):
1) CHECK.NAV.RAW_ONLY
2) CHECK.ANTI_NOISE.MIN_LOAD
3) CHECK.LOG.HOOKS_PRESENT
4) CHECK.MARKERS.MUST_LOAD
5) CHECK.KEYS.RESOLVE_VIA_INDEX
6) CHECK.IP.SAFETY_NO_DERIVATIVE_TEXT
7) CHECK.DUPLICATES.AVOID_REPEATS
8) CHECK.DURATION.FRAMES
9) CHECK.STYLE.COHERENCE

### T6) REQUIRED_IDX (keys only)
- Always include core root index key:
  - "IDX.UE_V2.ROOT" (symbolic; resolved by NAV layer)
- Add domain index suggestion if present:
  - ROUTING_HINTS.REQUIRED_IDX_SUGGESTION (single key)
Deduplicate, keep order:
- IDX.UE_V2.ROOT first, then domain suggestion.

### T7) DEFAULT_ORC (symbolic)
Mapping:
- DOMAIN == MUSIC -> "ORC.MUSIC.DEFAULT"
- DOMAIN == VIDEO -> "ORC.VIDEO.DEFAULT"
- DOMAIN startswith REPO_ -> "ORC.REPO.DEFAULT"
- else -> "ORC.CORE.DEFAULT"

### T8) PIPE_SELECTED (preselection hint)
- PIPE_SELECTED = ROUTING_HINTS.PIPE_SUGGESTION (may be null)
This is a hint, final selection belongs to `COR.PIPE_SELECTOR`.

### T9) TARGET_KEYS (keys only, no lookups)
- IDX_DOMAIN_ROOT = ROUTING_HINTS.REQUIRED_IDX_SUGGESTION or null
- TARGET_FILES determined by ARTIFACT_TYPE:
  - If ARTIFACT_TYPE == DOC -> ["KEY.DOC.TARGET"]
  - If ARTIFACT_TYPE == BRAND_DNA -> ["KEY.MUSIC.BRAND_DNA"]
  - If ARTIFACT_TYPE == ALBUM_PLAN -> ["KEY.MUSIC.ALBUM_PLAN"]
  - If ARTIFACT_TYPE == PROMPT_PACK -> ["KEY.PROMPT_PACK.TARGET"]
  - If ARTIFACT_TYPE == LYRICS_PACK -> ["KEY.LYRICS_PACK.TARGET"]
  - Else -> ["KEY.TARGET.GENERIC"]
Keep max 1 here; real target file keys are resolved later after NAV/IDX open.

### T10) NOISE_BUDGET
- OPEN_FILES_MAX = 4
- TARGET_FILES_MAX = 3
If MODE == FAST:
- OPEN_FILES_MAX = 3
- TARGET_FILES_MAX = 2
If MODE == MASTERPIECE:
- OPEN_FILES_MAX = 5
- TARGET_FILES_MAX = 3
(Still respects system anti-noise; never exceeds 5 opens.)

### T11) TOKEN_ID (deterministic)
Construct TOKEN_ID from stable fields:
TOKEN_ID = "RT." + DOMAIN + "." + ARTIFACT_TYPE + "." + MODE
No hashes, no random.
Example: RT.MUSIC.ALBUM_PLAN.RELEASE_READY

### T12) MIN_LOAD_PLAN (keys only)
MIN_LOAD_PLAN:
  ALWAYS_OPEN_KEYS:
    - "KEY.START"
    - "KEY.RUNTIME_MANIFEST"
    - "KEY.TASK_ROUTER"
    - "KEY.NAV_ROOT"
  THEN_OPEN_KEYS:
    - "IDX.UE_V2.ROOT"
    - "<IDX_DOMAIN_ROOT if not null>"
  TARGET_KEYS_MAX: <from NOISE_BUDGET.TARGET_FILES_MAX>
  TARGET_FILE_KEYS_HINT: <from ROUTE_TOKEN.TARGET_KEYS.TARGET_FILES>
This plan lists KEYS only. Resolution is enforced by NAV/IDX layer.

---

## [M] FAIL CONDITIONS
FAIL.INPUT_MISSING:
- REQUEST missing or TASK_TEXT empty
REQUIRED_FIX: Provide TASK_TEXT (what to do).

FAIL.MISSING_HINTS:
- ROUTING_HINTS absent or missing ARTIFACT_TYPE/DOMAIN_PRIMARY
REQUIRED_FIX: Re-run COR.DOMAIN_DETECTOR with normalized REQUEST.

FAIL.MODE_INVALID:
- MODE_HINT provided but not in allowed set
REQUIRED_FIX: Use MODE_HINT FAST|RELEASE_READY|MASTERPIECE or omit.

---

## [M] OUTPUT TEMPLATE (CANON)

On PASS:
STATUS: PASS
ROUTE_TOKEN:
  DOMAIN: "<...>"
  ARTIFACT_TYPE: "<...>"
  MODE: "<...>"
  EXEC_MODE: "STEP_RUN"
  PIPE_SELECTED: "<...|null>"
  DEFAULT_ORC: "<...>"
  REQUIRED_IDX: ["<...>"]
  REQUIRED_CHECKS: ["<...>"]
  TRACE_FLAGS: ["<...>"]
  NOISE_BUDGET:
    OPEN_FILES_MAX: <int>
    TARGET_FILES_MAX: <int>
  TARGET_KEYS:
    IDX_DOMAIN_ROOT: "<...|null>"
    TARGET_FILES: ["<...>"]
  TOKEN_META:
    TOKEN_ID: "<...>"
    TOKEN_VERSION: "1.0"
    CREATED_AT: "2026-02-02"
    UPDATED_AT: "2026-02-02"
MIN_LOAD_PLAN:
  ALWAYS_OPEN_KEYS: ["KEY.START", "KEY.RUNTIME_MANIFEST", "KEY.TASK_ROUTER", "KEY.NAV_ROOT"]
  THEN_OPEN_KEYS: ["IDX.UE_V2.ROOT", "<...optional...>"]
  TARGET_KEYS_MAX: <int>
  TARGET_FILE_KEYS_HINT: ["<...>"]
RUN_SEED:
  NEXT_MODULE_KEY: COR.NAV_SENTINEL
  NEXT_PROMPT: "го"

On FAIL:
STATUS: FAIL
FAIL_CODE: FAIL.<...>
REQUIRED_FIX: "<one line>"
NEXT_PROMPT: "го"

---

## [M] GATES
PASS if:
- ROUTE_TOKEN includes all canon fields from START
- REQUIRED_IDX not empty and begins with IDX.UE_V2.ROOT
- EXEC_MODE == STEP_RUN
- NEXT_MODULE_KEY == COR.NAV_SENTINEL
- Output respects ANTI_NOISE

FAIL if:
- INPUT_MISSING or MISSING_HINTS or MODE_INVALID
