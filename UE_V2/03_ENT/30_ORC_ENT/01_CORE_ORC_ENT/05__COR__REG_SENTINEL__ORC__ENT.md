FILE: UE_V2/03_ENT/30_ORC_ENT/01_CORE_ORC_ENT/05__COR__REG_SENTINEL__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 01_CORE_ORC_ENT
DOC_TYPE: ORC_ENTITY_MODULE
DOMAIN: COR_ORC_ENT
KEY: COR.REG_SENTINEL
UID: UE.V2.ENT.ORC.COR.REG_SENTINEL.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: RAW-only enforcement (KEY->IDX->RAW)

---

## [M] ROLE
Registry sentinel module.
Confirms that the run can reach and use required registry anchors (REG) strictly via IDX/KEY resolution.
Prevents silent runs that skip registry hooks, run context registers, or required “write targets” needed later by LOG.

## [M] PURPOSE
- Confirm REG access path exists (KEY -> required IDX -> RAW resolution by nav layer).
- Confirm the minimum registry hooks required for a deterministic run are declared and reachable.
- Produce a `REG_ACCESS_REPORT` (keys-only) that becomes the contract for downstream modules.
- Block execution when registry anchors are missing (no “half-run” without registers).

## [M] HARD_RULES
- Do not traverse PATH, do not emit RAW here. Keys-only.
- Do not open files. This module only validates and plans.
- Do not invent registry structure. If REG keys are not declared in ROUTE_TOKEN, require them (FAIL) or mark as GAP only when domain specifics are not yet known.
- Always keep compatibility with STEP-RUN: output must be stable, minimal, and deterministic.
- Anti-noise: never add more than `NOISE_BUDGET.OPEN_FILES_MAX` keys to any plan emitted here.

---

## [M] INPUTS
- ROUTE_TOKEN (required)
  - DOMAIN
  - REQUIRED_IDX: [KEY...]
  - REQUIRED_CHECKS: [CHECK...]
  - NOISE_BUDGET:
      OPEN_FILES_MAX: <int>
      TARGET_FILES_MAX: <int>
  - TRACE_FLAGS
  - EXEC_MODE
- NAV_ACTION_PLAN (required)  (from COR.NAV_SENTINEL)
  - OPEN_NEXT_KEYS (ordered)
  - VERIFY_AFTER_OPEN (ordered)
  - REQUIRED_REALM_ACCESS (symbols)
- OPTIONAL: RUNTIME_STATE
  - resolved_keys: ["KEY"...]            # what nav already proved resolvable
  - realm_caps: ["REALM.REG"...]         # what nav already confirmed
  - run_seed: "<string|null>"            # deterministic seed if runtime uses it

---

## [M] OUTPUTS
- REG_ACCESS_REPORT (keys only)
  - REG_REQUIRED: true|false
  - REG_ANCHOR_KEYS: ["<key>", ...]
  - REG_CONTEXT_KEYS: ["<key>", ...]
  - REG_WRITE_TARGET_KEYS: ["<key>", ...]
  - REG_MIN_PLAN_KEYS: ["<key>", ...]    # what nav should ensure is open/resolved next
  - REG_CHECKLIST: ["<check>", ...]
- STATUS: PASS | FAIL | GAP
- FAIL_CODE or GAP_CODE
- NEXT_MODULE_KEY: COR.XREF_SENTINEL (on PASS)
- NEXT_PROMPT: "го"

---

## [M] REG_ACCESS_REPORT SCHEMA (v1)
REG_ACCESS_REPORT:
  REG_REQUIRED: true
  REG_ANCHOR_KEYS: ["REG.ROOT|REG.INDEX|..."]
  REG_CONTEXT_KEYS: ["REG.RUN_CONTEXT|..."]
  REG_WRITE_TARGET_KEYS: ["REG.WRITE.RUN_STATE|..."]
  REG_MIN_PLAN_KEYS: ["<key>", ...]
  REG_CHECKLIST:
    - "CHECK.REG.REACHABLE_VIA_INDEX"
    - "CHECK.REG.MIN_ANCHORS_DECLARED"
    - "CHECK.REG.WRITE_TARGETS_DECLARED"
    - "CHECK.REG.ANTI_NOISE"
  DISPATCH:
    NEXT_MODULE_KEY: "COR.XREF_SENTINEL"
    NEXT_PROMPT: "го"

Note:
- Keys above are symbolic placeholders. Real keys must come from ROUTE_TOKEN / domain IDX.
- This module fails if real REG keys are absent when REG is required.

---

## [M] DETERMINISTIC LOGIC

### R0) Preconditions
FAIL if:
- ROUTE_TOKEN missing
- NAV_ACTION_PLAN missing
- ROUTE_TOKEN.REQUIRED_IDX empty
- NAV_ACTION_PLAN.OPEN_NEXT_KEYS empty

### R1) Decide whether REG is required
REG_REQUIRED = true if ANY:
- "REALM.REG" in NAV_ACTION_PLAN.REQUIRED_REALM_ACCESS
- "CHECK.REG.*" exists in ROUTE_TOKEN.REQUIRED_CHECKS
- EXEC_MODE implies structured run (anything except explicitly "RAW_CHAT_ONLY")

If REG_REQUIRED is false:
- Output report with REG_REQUIRED: false
- STATUS: PASS
- NEXT_MODULE_KEY: COR.XREF_SENTINEL

### R2) Extract declared REG keys (no invention)
Build three lists ONLY from declared keys in inputs:
- REG_ANCHOR_KEYS:
  - keys in ROUTE_TOKEN.REQUIRED_IDX that match prefix "REG." OR are explicitly tagged by caller as REG anchors
- REG_CONTEXT_KEYS:
  - keys in ROUTE_TOKEN.TARGET_KEYS (if present) that match "REG.*CONTEXT*" OR caller-provided mapping
- REG_WRITE_TARGET_KEYS:
  - keys in ROUTE_TOKEN.REQUIRED_CHECKS-derived mapping if caller provided "REG.WRITE.*" keys
  - otherwise empty (and triggers FAIL if REG_REQUIRED)

If your runtime does not use prefixes:
- Caller must pass explicit lists in ROUTE_TOKEN via TARGET_KEYS.REG_* (recommended). If absent -> FAIL.

### R3) Validate minimum declared anchors
If REG_REQUIRED is true, then minimum must hold:
- len(REG_ANCHOR_KEYS) >= 1
- len(REG_CONTEXT_KEYS) >= 1
- len(REG_WRITE_TARGET_KEYS) >= 1

If any missing:
- GAP only if DOMAIN == "UNKNOWN" (routing not final yet)
  GAP_CODE: GAP.REG_KEYS_NOT_DECLARED_YET
  REQUIRED_FIX: Provide REG key set in ROUTE_TOKEN after domain detect/router.
- Otherwise FAIL:
  FAIL_CODE: FAIL.REG_KEYS_MISSING
  REQUIRED_FIX: Add required REG keys to ROUTE_TOKEN (anchors, context, write targets).

### R4) Build REG_MIN_PLAN_KEYS (keys-only, anti-noise)
Start with (ordered):
1) First anchor key from REG_ANCHOR_KEYS
2) First context key from REG_CONTEXT_KEYS
3) First write-target key from REG_WRITE_TARGET_KEYS

Then add (only if budget allows, and not duplicates):
4) Any additional REG_ANCHOR_KEYS (up to 2)
5) Any additional REG_CONTEXT_KEYS (up to 2)

Respect budget:
- Let B = ROUTE_TOKEN.NOISE_BUDGET.OPEN_FILES_MAX
- REG_MIN_PLAN_KEYS must not exceed max(1, min(5, B))  # hard clamp to keep it minimal

### R5) Build REG_CHECKLIST (ordered)
Always include:
- CHECK.REG.REACHABLE_VIA_INDEX
- CHECK.REG.MIN_ANCHORS_DECLARED
- CHECK.REG.WRITE_TARGETS_DECLARED
- CHECK.REG.ANTI_NOISE

Merge any checks from ROUTE_TOKEN.REQUIRED_CHECKS that start with "CHECK.REG."
Deduplicate, keep baseline ordering first, then the rest alpha.

### R6) Dispatch
On PASS (or GAP where nav can proceed):
- NEXT_MODULE_KEY: COR.XREF_SENTINEL
- NEXT_PROMPT: "го"

---

## [M] FAIL CONDITIONS
FAIL.REG_INPUT_MISSING:
- ROUTE_TOKEN or NAV_ACTION_PLAN missing

FAIL.REG_KEYS_MISSING:
- REG_REQUIRED true but any of (anchors/context/write targets) empty for known domain
REQUIRED_FIX:
- Put explicit REG keys into ROUTE_TOKEN (recommended field: TARGET_KEYS.REG_ANCHORS / REG_CONTEXT / REG_WRITE_TARGETS)

FAIL.REG_NOISE_BUDGET:
- Cannot produce minimal plan within noise budget (caller misconfigured OPEN_FILES_MAX too low)
REQUIRED_FIX:
- Increase OPEN_FILES_MAX or reduce ALWAYS_OPEN_KEYS elsewhere

FAIL.NON_DETERMINISTIC_REG_SET:
- Inputs provide unordered/unstable sets
REQUIRED_FIX:
- Normalize to stable arrays at intake

---

## [M] GAP CONDITIONS (minimal, only when routing not final)
GAP.REG_KEYS_NOT_DECLARED_YET:
- DOMAIN == "UNKNOWN" and REG keys are not declared yet
REQUIRED_FIX:
- Complete domain detect + route token build, then re-run sentinel.

---

## [M] OUTPUT TEMPLATE

On PASS:
STATUS: PASS
REG_ACCESS_REPORT:
  REG_REQUIRED: true
  REG_ANCHOR_KEYS: ["<key>", ...]
  REG_CONTEXT_KEYS: ["<key>", ...]
  REG_WRITE_TARGET_KEYS: ["<key>", ...]
  REG_MIN_PLAN_KEYS: ["<key>", ...]
  REG_CHECKLIST: ["CHECK.REG.REACHABLE_VIA_INDEX", "CHECK.REG.MIN_ANCHORS_DECLARED", "CHECK.REG.WRITE_TARGETS_DECLARED", "CHECK.REG.ANTI_NOISE"]
  DISPATCH:
    NEXT_MODULE_KEY: "COR.XREF_SENTINEL"
    NEXT_PROMPT: "го"

On GAP:
STATUS: GAP
GAP_CODE: GAP.REG_KEYS_NOT_DECLARED_YET
REQUIRED_FIX: "Provide explicit REG key set in ROUTE_TOKEN after routing."
REG_ACCESS_REPORT:
  REG_REQUIRED: true
  REG_ANCHOR_KEYS: []
  REG_CONTEXT_KEYS: []
  REG_WRITE_TARGET_KEYS: []
  REG_MIN_PLAN_KEYS: []
  REG_CHECKLIST: ["CHECK.REG.REACHABLE_VIA_INDEX","CHECK.REG.MIN_ANCHORS_DECLARED","CHECK.REG.WRITE_TARGETS_DECLARED","CHECK.REG.ANTI_NOISE"]
  DISPATCH:
    NEXT_MODULE_KEY: "COR.XREF_SENTINEL"
    NEXT_PROMPT: "го"

On FAIL:
STATUS: FAIL
FAIL_CODE: FAIL.REG_KEYS_MISSING
REQUIRED_FIX: "Add anchors/context/write-target REG keys to ROUTE_TOKEN."
NEXT_PROMPT: "го"

---

## [M] GATES
PASS if:
- Keys-only (no RAW, no PATH)
- REG_REQUIRED computed deterministically
- For known domain: anchors + context + write targets are declared (non-empty)
- REG_MIN_PLAN_KEYS respects noise budget and remains minimal
- NEXT_MODULE_KEY == COR.XREF_SENTINEL

GAP if:
- Domain not resolved yet and REG keys are not declared

FAIL if:
- Required inputs missing
- Known domain but REG key sets missing
- Noise budget impossible
