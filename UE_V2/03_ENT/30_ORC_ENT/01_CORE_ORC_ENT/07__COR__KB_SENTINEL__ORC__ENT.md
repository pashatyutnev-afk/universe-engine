FILE: UE_V2/03_ENT/30_ORC_ENT/01_CORE_ORC_ENT/07__COR__KB_SENTINEL__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 01_CORE_ORC_ENT
DOC_TYPE: ORC_ENTITY_MODULE
DOMAIN: COR_ORC_ENT
KEY: COR.KB_SENTINEL
UID: UE.V2.ENT.ORC.COR.KB_SENTINEL.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: RAW-only enforcement (KEY->IDX->RAW)

---

## [M] ROLE
Knowledge Base sentinel module.
Enforces KB boundaries, required KB declarations, and minimal KB load plan.
Prevents unscoped knowledge usage and blocks "knowledge drift" outside declared scope.

## [M] PURPOSE
- Decide if KB is required for the run (deterministically).
- Validate that KB scope is declared (inputs, outputs, boundaries) when KB is required.
- Validate that KB sources are declared as KEYS (no raw emission here).
- Produce `KB_ACCESS_REPORT` (keys-only) for downstream routing/pipes.
- Keep anti-noise: never mass-load KB trees.

---

## [M] HARD_RULES
- Keys-only. No RAW output. No PATH traversal.
- Do not open KB content files here. Only validate declarations and build minimal key plan.
- No invention: if KB keys/scope are missing, emit FAIL (known domain) or GAP (unknown domain).
- Deterministic: stable ordering rules, no random sampling.
- Anti-noise: KB plan must respect NOISE_BUDGET and be minimal.

---

## [M] INPUTS
- ROUTE_TOKEN (required)
  - DOMAIN
  - ARTIFACT_TYPE
  - MODE_HINT: FAST|RELEASE_READY|MASTERPIECE (optional)
  - REQUIRED_IDX: ["KEY"...]
  - REQUIRED_CHECKS: ["CHECK.*"...]
  - NOISE_BUDGET:
      OPEN_FILES_MAX: <int>
      TARGET_FILES_MAX: <int>
  - TRACE_FLAGS
  - EXEC_MODE
  - OPTIONAL: KB_DECL (caller-declared)
      KB_REQUIRED: true|false (optional hint, sentinel may escalate)
      KB_SCOPE:
        INPUTS: ["<what KB may use>", ...]
        OUTPUTS: ["<what KB may produce>", ...]
        BOUNDARIES: ["<what KB must not cross>", ...]
      KB_KEYS:
        KB_ROOTS: ["KEY"...]        # anchors, indexes, root kb nodes
        KB_SOURCES: ["KEY"...]      # source pointers (keys only)
        KB_GUARDS: ["KEY"...]       # optional scope guards / gate docs
- NAV_ACTION_PLAN (required) (from COR.NAV_SENTINEL)
  - REQUIRED_REALM_ACCESS: ["REALM.KB", ...]
  - OPEN_NEXT_KEYS: ["KEY"...]
  - VERIFY_AFTER_OPEN: ["CHECK"...]
- OPTIONAL: XREF_ACCESS_REPORT (from COR.XREF_SENTINEL)
  - XREF_TARGET_REALMS: ["REALM.*"...]
  - XREF_CHECKLIST: ["CHECK.*"...]
- OPTIONAL: RUNTIME_STATE
  - resolved_keys: ["KEY"...]
  - realm_caps: ["REALM.KB"...]
  - run_seed: "<string|null>"

---

## [M] OUTPUTS
- KB_ACCESS_REPORT (keys only)
  - KB_REQUIRED: true|false
  - KB_SCOPE_OK: true|false
  - KB_SCOPE:
      INPUTS: ["...", ...]
      OUTPUTS: ["...", ...]
      BOUNDARIES: ["...", ...]
  - KB_ROOT_KEYS: ["<key>", ...]
  - KB_SOURCE_KEYS: ["<key>", ...]
  - KB_GUARD_KEYS: ["<key>", ...]
  - KB_MIN_PLAN_KEYS: ["<key>", ...]
  - KB_CHECKLIST: ["<check>", ...]
- STATUS: PASS | FAIL | GAP
- FAIL_CODE or GAP_CODE
- NEXT_MODULE_KEY: COR.PIPE_SELECTOR (on PASS)
- NEXT_PROMPT: "го"

---

## [M] KB_ACCESS_REPORT SCHEMA (v1)
KB_ACCESS_REPORT:
  KB_REQUIRED: true
  KB_SCOPE_OK: true
  KB_SCOPE:
    INPUTS: ["..."]
    OUTPUTS: ["..."]
    BOUNDARIES: ["..."]
  KB_ROOT_KEYS: ["KB.ROOT|KB.INDEX|..."]
  KB_SOURCE_KEYS: ["KB.SRC.*|..."]
  KB_GUARD_KEYS: ["KB.GUARD.*|..."]
  KB_MIN_PLAN_KEYS: ["<key>", ...]
  KB_CHECKLIST:
    - "CHECK.KB.REACHABLE_VIA_INDEX"
    - "CHECK.KB.SCOPE_DECLARED"
    - "CHECK.KB.SOURCES_DECLARED"
    - "CHECK.KB.BOUNDARIES_DECLARED"
    - "CHECK.KB.ANTI_NOISE"
  DISPATCH:
    NEXT_MODULE_KEY: "COR.PIPE_SELECTOR"
    NEXT_PROMPT: "го"

Note:
- Keys are symbolic examples only. Real keys must come from ROUTE_TOKEN / domain IDX.
- If your system does not use KB.* prefixes, the caller must pass explicit KB_KEYS lists.

---

## [M] DETERMINISTIC LOGIC

### K0) Preconditions
FAIL if:
- ROUTE_TOKEN missing
- NAV_ACTION_PLAN missing
- ROUTE_TOKEN.REQUIRED_IDX empty

### K1) Decide whether KB is required
Base rule:
KB_REQUIRED = true if ANY:
- "REALM.KB" in NAV_ACTION_PLAN.REQUIRED_REALM_ACCESS
- any check in ROUTE_TOKEN.REQUIRED_CHECKS starts with "CHECK.KB."
- MODE_HINT in {RELEASE_READY, MASTERPIECE} (quality modes require scoped knowledge)
- ARTIFACT_TYPE implies knowledge-intensive output (caller may tag with CHECK.KB.*)

Respect caller hint:
- If ROUTE_TOKEN.KB_DECL.KB_REQUIRED is explicitly true -> KB_REQUIRED true.
- If explicitly false -> may remain false only if no hard triggers above.

If KB_REQUIRED is false:
- Output minimal report with KB_REQUIRED: false, KB_SCOPE_OK: true
- STATUS: PASS
- NEXT_MODULE_KEY: COR.PIPE_SELECTOR

### K2) Validate that KB scope is declared when required
If KB_REQUIRED is true:
- Require ROUTE_TOKEN.KB_DECL.KB_SCOPE with:
  - INPUTS non-empty
  - OUTPUTS non-empty
  - BOUNDARIES non-empty
If missing:
- GAP only if DOMAIN == "UNKNOWN"
  GAP_CODE: GAP.KB_SCOPE_NOT_DECLARED_YET
  REQUIRED_FIX: Declare KB_SCOPE (inputs, outputs, boundaries) in ROUTE_TOKEN.KB_DECL.
- Otherwise FAIL:
  FAIL_CODE: FAIL.KB_SCOPE_MISSING
  REQUIRED_FIX: Add KB_SCOPE (inputs, outputs, boundaries) to ROUTE_TOKEN.KB_DECL.

### K3) Extract declared KB keys (no invention)
Primary source:
- ROUTE_TOKEN.KB_DECL.KB_KEYS.KB_ROOTS / KB_SOURCES / KB_GUARDS

Fallback (prefix-based only if your system uses it):
- KB_ROOT_KEYS:
  - keys in ROUTE_TOKEN.REQUIRED_IDX where key starts with "KB."
  - plus any where key contains "KB.ROOT" or "KB.INDEX" (if used)
- KB_SOURCE_KEYS:
  - keys in ROUTE_TOKEN.REQUIRED_IDX where key contains "KB.SRC" or starts with "KB.SRC."
- KB_GUARD_KEYS:
  - keys in ROUTE_TOKEN.REQUIRED_IDX where key contains "KB.GUARD" or starts with "KB.GUARD."

If KB_REQUIRED is true and no reliable extraction is possible:
- GAP when DOMAIN == "UNKNOWN"
- else FAIL.KB_KEYS_MISSING

### K4) Validate minimum keys when required
If KB_REQUIRED is true, minimum must hold for known domain:
- len(KB_ROOT_KEYS) >= 1
- len(KB_SOURCE_KEYS) >= 1     (at least one declared KB source pointer key)
- guards optional

If missing:
- GAP only if DOMAIN == "UNKNOWN"
  GAP_CODE: GAP.KB_KEYS_NOT_DECLARED_YET
  REQUIRED_FIX: Declare KB_ROOTS and KB_SOURCES keys.
- Otherwise FAIL:
  FAIL_CODE: FAIL.KB_KEYS_MISSING
  REQUIRED_FIX: Add KB_ROOTS and KB_SOURCES keys to ROUTE_TOKEN.KB_DECL.

### K5) Build KB_MIN_PLAN_KEYS (keys-only, anti-noise)
Ordered selection:
1) First KB root key
2) First KB source key
3) First KB guard key (if any)

Then add (only if budget allows, not duplicates):
4) Additional KB source key (up to 1)
5) Additional KB root key (up to 1)

Budget clamp:
- Let B = ROUTE_TOKEN.NOISE_BUDGET.OPEN_FILES_MAX
- KB_MIN_PLAN_KEYS must not exceed max(1, min(5, B))

### K6) Build KB_CHECKLIST (ordered)
Always include baseline:
- CHECK.KB.REACHABLE_VIA_INDEX
- CHECK.KB.SCOPE_DECLARED
- CHECK.KB.SOURCES_DECLARED
- CHECK.KB.BOUNDARIES_DECLARED
- CHECK.KB.ANTI_NOISE

Merge any checks from ROUTE_TOKEN.REQUIRED_CHECKS that start with "CHECK.KB."
Deduplicate, keep baseline ordering first, then remaining alpha.

### K7) Dispatch
On PASS (or GAP where nav can proceed):
- NEXT_MODULE_KEY: COR.PIPE_SELECTOR
- NEXT_PROMPT: "го"

---

## [M] FAIL CONDITIONS
FAIL.KB_INPUT_MISSING:
- ROUTE_TOKEN or NAV_ACTION_PLAN missing

FAIL.KB_SCOPE_MISSING:
- KB_REQUIRED true but KB_SCOPE not declared

FAIL.KB_KEYS_MISSING:
- KB_REQUIRED true but KB_ROOTS or KB_SOURCES missing for known domain

FAIL.KB_NOISE_BUDGET:
- Cannot produce minimal plan within OPEN_FILES_MAX

---

## [M] GAP CONDITIONS (minimal, only when routing not final)
GAP.KB_SCOPE_NOT_DECLARED_YET:
- DOMAIN == "UNKNOWN" and KB_SCOPE not declared

GAP.KB_KEYS_NOT_DECLARED_YET:
- DOMAIN == "UNKNOWN" and KB key sets not declared

REQUIRED_FIX:
- Complete domain detect + route token build, then declare KB_DECL and re-run sentinel.

---

## [M] OUTPUT TEMPLATE

On PASS (KB required):
STATUS: PASS
KB_ACCESS_REPORT:
  KB_REQUIRED: true
  KB_SCOPE_OK: true
  KB_SCOPE:
    INPUTS: ["..."]
    OUTPUTS: ["..."]
    BOUNDARIES: ["..."]
  KB_ROOT_KEYS: ["<key>", ...]
  KB_SOURCE_KEYS: ["<key>", ...]
  KB_GUARD_KEYS: ["<key>", ...]
  KB_MIN_PLAN_KEYS: ["<key>", ...]
  KB_CHECKLIST:
    - "CHECK.KB.REACHABLE_VIA_INDEX"
    - "CHECK.KB.SCOPE_DECLARED"
    - "CHECK.KB.SOURCES_DECLARED"
    - "CHECK.KB.BOUNDARIES_DECLARED"
    - "CHECK.KB.ANTI_NOISE"
  DISPATCH:
    NEXT_MODULE_KEY: "COR.PIPE_SELECTOR"
    NEXT_PROMPT: "го"

On PASS (KB not required):
STATUS: PASS
KB_ACCESS_REPORT:
  KB_REQUIRED: false
  KB_SCOPE_OK: true
  KB_SCOPE:
    INPUTS: []
    OUTPUTS: []
    BOUNDARIES: []
  KB_ROOT_KEYS: []
  KB_SOURCE_KEYS: []
  KB_GUARD_KEYS: []
  KB_MIN_PLAN_KEYS: []
  KB_CHECKLIST:
    - "CHECK.KB.ANTI_NOISE"
  DISPATCH:
    NEXT_MODULE_KEY: "COR.PIPE_SELECTOR"
    NEXT_PROMPT: "го"

On GAP:
STATUS: GAP
GAP_CODE: GAP.KB_SCOPE_NOT_DECLARED_YET
REQUIRED_FIX: "Declare KB_SCOPE (inputs, outputs, boundaries) and KB keys in ROUTE_TOKEN.KB_DECL."
KB_ACCESS_REPORT:
  KB_REQUIRED: true
  KB_SCOPE_OK: false
  KB_SCOPE:
    INPUTS: []
    OUTPUTS: []
    BOUNDARIES: []
  KB_ROOT_KEYS: []
  KB_SOURCE_KEYS: []
  KB_GUARD_KEYS: []
  KB_MIN_PLAN_KEYS: []
  KB_CHECKLIST:
    - "CHECK.KB.REACHABLE_VIA_INDEX"
    - "CHECK.KB.SCOPE_DECLARED"
    - "CHECK.KB.SOURCES_DECLARED"
    - "CHECK.KB.BOUNDARIES_DECLARED"
    - "CHECK.KB.ANTI_NOISE"
  DISPATCH:
    NEXT_MODULE_KEY: "COR.PIPE_SELECTOR"
    NEXT_PROMPT: "го"

On FAIL:
STATUS: FAIL
FAIL_CODE: FAIL.KB_SCOPE_MISSING
REQUIRED_FIX: "Add KB_SCOPE (inputs, outputs, boundaries) and KB_ROOTS/KB_SOURCES keys to ROUTE_TOKEN.KB_DECL."
NEXT_PROMPT: "го"

---

## [M] GATES
PASS if:
- Keys-only (no RAW, no PATH)
- KB_REQUIRED computed deterministically
- If KB_REQUIRED true and known domain: KB_SCOPE declared (inputs, outputs, boundaries)
- If KB_REQUIRED true and known domain: KB_ROOTS and KB_SOURCES declared
- KB_MIN_PLAN_KEYS respects noise budget and is minimal
- NEXT_MODULE_KEY == COR.PIPE_SELECTOR

GAP if:
- Domain not resolved yet and KB scope/keys are not declared

FAIL if:
- Required inputs missing
- Known domain but required KB scope/keys missing
- Noise budget impossible
