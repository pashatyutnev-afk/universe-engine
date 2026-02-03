FILE: UE_V2/03_ENT/30_ORC_ENT/01_CORE_ORC_ENT/06__COR__XREF_SENTINEL__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 01_CORE_ORC_ENT
DOC_TYPE: ORC_ENTITY_MODULE
DOMAIN: COR_ORC_ENT
KEY: COR.XREF_SENTINEL
UID: UE.V2.ENT.ORC.COR.XREF_SENTINEL.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: RAW-only enforcement (KEY->IDX->RAW)

---

## [M] ROLE
Cross-reference sentinel module.
Ensures the run respects cross-realm boundaries and uses declared XREF/REG/IDX bridges instead of implicit jumping.
Prevents "silent teleport" between realms/domains without traceability.

## [M] PURPOSE
- Confirm that cross-realm references are explicitly declared and routable via XREF keys.
- Confirm that the ROUTE_TOKEN contains required XREF checks and that NAV can reach relevant XREF anchors.
- Produce a minimal `XREF_ACCESS_REPORT` (keys-only) to be used by router/pipe modules.
- Block (FAIL) when the run attempts to cross boundaries without declared xref contracts.

---

## [M] HARD_RULES
- Keys-only. No RAW emission. No PATH traversal.
- Do not open target files. Only validate declarations + build minimal plan.
- No invention: if XREF keys are not declared, require caller to declare them (FAIL) or allow GAP only if DOMAIN is unknown.
- Anti-noise: emit minimal key plan within NOISE_BUDGET.
- Deterministic order: stable sorting and fixed priority rules.

---

## [M] INPUTS
- ROUTE_TOKEN (required)
  - DOMAIN
  - ARTIFACT_TYPE
  - REQUIRED_IDX: ["KEY"...]
  - REQUIRED_CHECKS: ["CHECK.*"...]
  - NOISE_BUDGET:
      OPEN_FILES_MAX: <int>
      TARGET_FILES_MAX: <int>
  - TRACE_FLAGS
  - EXEC_MODE
  - OPTIONAL: TARGET_REALMS: ["REALM.*"...]     # caller-declared target realms for this run
  - OPTIONAL: TARGET_KEYS:
      XREF_ANCHORS: ["KEY"...]                  # explicit xref anchor keys
      XREF_BRIDGES: ["KEY"...]                  # explicit bridge keys for cross-realm resolution
      XREF_GUARDS: ["KEY"...]                   # optional guard docs/keys
- NAV_ACTION_PLAN (required)  (from COR.NAV_SENTINEL)
  - REQUIRED_REALM_ACCESS: ["REALM.XREF", ...]
  - OPEN_NEXT_KEYS: ["KEY"...]                  # ordered
  - VERIFY_AFTER_OPEN: ["CHECK"...]             # ordered
- OPTIONAL: REG_ACCESS_REPORT (from COR.REG_SENTINEL)
  - REG_REQUIRED
  - REG_MIN_PLAN_KEYS
- OPTIONAL: RUNTIME_STATE
  - resolved_keys: ["KEY"...]
  - realm_caps: ["REALM.XREF"...]
  - run_seed: "<string|null>"

---

## [M] OUTPUTS
- XREF_ACCESS_REPORT (keys only)
  - XREF_REQUIRED: true|false
  - XREF_ANCHOR_KEYS: ["<key>", ...]
  - XREF_BRIDGE_KEYS: ["<key>", ...]
  - XREF_GUARD_KEYS: ["<key>", ...]
  - XREF_TARGET_REALMS: ["REALM.*", ...]
  - XREF_MIN_PLAN_KEYS: ["<key>", ...]
  - XREF_CHECKLIST: ["<check>", ...]
- STATUS: PASS | FAIL | GAP
- FAIL_CODE or GAP_CODE
- NEXT_MODULE_KEY: COR.KB_SENTINEL (on PASS)
- NEXT_PROMPT: "го"

---

## [M] XREF_ACCESS_REPORT SCHEMA (v1)
XREF_ACCESS_REPORT:
  XREF_REQUIRED: true
  XREF_ANCHOR_KEYS: ["XREF.ROOT|XREF.INDEX|..."]
  XREF_BRIDGE_KEYS: ["XREF.BRIDGE.<realmA>.<realmB>|..."]
  XREF_GUARD_KEYS: ["XREF.GUARD.*|..."]
  XREF_TARGET_REALMS: ["REALM.<domain>", ...]
  XREF_MIN_PLAN_KEYS: ["<key>", ...]
  XREF_CHECKLIST:
    - "CHECK.XREF.REACHABLE_VIA_INDEX"
    - "CHECK.XREF.BOUNDARIES_DECLARED"
    - "CHECK.XREF.BRIDGES_DECLARED"
    - "CHECK.XREF.ANTI_NOISE"
  DISPATCH:
    NEXT_MODULE_KEY: "COR.KB_SENTINEL"
    NEXT_PROMPT: "го"

Note:
- Keys are symbolic examples only. Real keys must come from ROUTE_TOKEN / domain IDX.
- If your system does not use prefixes, the caller must pass explicit XREF lists.

---

## [M] DETERMINISTIC LOGIC

### X0) Preconditions
FAIL if:
- ROUTE_TOKEN missing
- NAV_ACTION_PLAN missing
- ROUTE_TOKEN.REQUIRED_IDX empty

### X1) Decide whether XREF is required
XREF_REQUIRED = true if ANY:
- "REALM.XREF" in NAV_ACTION_PLAN.REQUIRED_REALM_ACCESS
- any check in ROUTE_TOKEN.REQUIRED_CHECKS starts with "CHECK.XREF."
- ROUTE_TOKEN declares TARGET_REALMS count > 1  (cross-realm intent)
- ROUTE_TOKEN.DOMAIN implies external dependency (caller tag "CROSS_REALM" if used)

If XREF_REQUIRED is false:
- Output report with XREF_REQUIRED: false
- STATUS: PASS
- NEXT_MODULE_KEY: COR.KB_SENTINEL

### X2) Extract declared XREF keys (no invention)
Primary source (recommended):
- ROUTE_TOKEN.TARGET_KEYS.XREF_ANCHORS / XREF_BRIDGES / XREF_GUARDS

Fallback (prefix-based only if your system uses it):
- XREF_ANCHOR_KEYS:
  - keys in ROUTE_TOKEN.REQUIRED_IDX where key starts with "XREF."
- XREF_BRIDGE_KEYS:
  - keys in ROUTE_TOKEN.REQUIRED_IDX where key contains "BRIDGE" or starts with "XREF.BRIDGE."
- XREF_GUARD_KEYS:
  - keys in ROUTE_TOKEN.REQUIRED_IDX where key contains "GUARD" or starts with "XREF.GUARD."

If neither explicit lists nor reliable prefix conventions exist:
- For XREF_REQUIRED true -> FAIL (known domain) or GAP (unknown domain).

### X3) Determine target realms (keys-only)
XREF_TARGET_REALMS derived deterministically:
1) If ROUTE_TOKEN.TARGET_REALMS present -> use as-is (stable order expected).
2) Else if caller provides DOMAIN + ARTIFACT_TYPE mapping -> add only that realm ("REALM.<DOMAIN>") and "REALM.CORE".
3) Else -> ["REALM.CORE"] only.

Normalize:
- Deduplicate while preserving order.
- If order is unstable (set-like input) -> FAIL.NON_DETERMINISTIC_XREF_REALMS.

### X4) Validate minimum declared anchors/bridges when required
If XREF_REQUIRED is true, minimum must hold for known domain:
- len(XREF_ANCHOR_KEYS) >= 1
- len(XREF_BRIDGE_KEYS) >= 1   (if XREF_TARGET_REALMS size > 1)
- len(XREF_GUARD_KEYS) >= 0 (optional)

If missing:
- GAP only if DOMAIN == "UNKNOWN"
  GAP_CODE: GAP.XREF_KEYS_NOT_DECLARED_YET
  REQUIRED_FIX: Provide explicit XREF key set after routing.
- Otherwise FAIL:
  FAIL_CODE: FAIL.XREF_KEYS_MISSING
  REQUIRED_FIX: Add XREF anchors and required bridges (per target realms) to ROUTE_TOKEN.

### X5) Build XREF_MIN_PLAN_KEYS (keys-only, anti-noise)
Ordered selection:
1) First anchor key from XREF_ANCHOR_KEYS
2) First bridge key from XREF_BRIDGE_KEYS (if any)
3) First guard key from XREF_GUARD_KEYS (if any)

Then add (only if budget allows, and not duplicates):
4) Additional anchor keys (up to 1)
5) Additional bridge keys (up to 1)

Budget clamp:
- Let B = ROUTE_TOKEN.NOISE_BUDGET.OPEN_FILES_MAX
- XREF_MIN_PLAN_KEYS must not exceed max(1, min(5, B))

### X6) Build XREF_CHECKLIST (ordered)
Always include baseline:
- CHECK.XREF.REACHABLE_VIA_INDEX
- CHECK.XREF.BOUNDARIES_DECLARED
- CHECK.XREF.BRIDGES_DECLARED
- CHECK.XREF.ANTI_NOISE

Merge any checks from ROUTE_TOKEN.REQUIRED_CHECKS that start with "CHECK.XREF."
Deduplicate, keep baseline ordering first, then remaining alpha.

### X7) Dispatch
On PASS (or GAP where nav can proceed):
- NEXT_MODULE_KEY: COR.KB_SENTINEL
- NEXT_PROMPT: "го"

---

## [M] FAIL CONDITIONS
FAIL.XREF_INPUT_MISSING:
- ROUTE_TOKEN or NAV_ACTION_PLAN missing

FAIL.XREF_KEYS_MISSING:
- XREF_REQUIRED true but anchors missing
- or bridges missing when multiple target realms implied and domain is known

FAIL.NON_DETERMINISTIC_XREF_REALMS:
- TARGET_REALMS provided as an unstable set-like structure or inconsistent ordering

FAIL.XREF_NOISE_BUDGET:
- Cannot produce minimal plan within OPEN_FILES_MAX

---

## [M] GAP CONDITIONS (minimal, only when routing not final)
GAP.XREF_KEYS_NOT_DECLARED_YET:
- DOMAIN == "UNKNOWN" and XREF key sets not declared yet
REQUIRED_FIX:
- Complete domain detect + route token build, then re-run sentinel.

---

## [M] OUTPUT TEMPLATE

On PASS:
STATUS: PASS
XREF_ACCESS_REPORT:
  XREF_REQUIRED: true
  XREF_ANCHOR_KEYS: ["<key>", ...]
  XREF_BRIDGE_KEYS: ["<key>", ...]
  XREF_GUARD_KEYS: ["<key>", ...]
  XREF_TARGET_REALMS: ["REALM.*", ...]
  XREF_MIN_PLAN_KEYS: ["<key>", ...]
  XREF_CHECKLIST: ["CHECK.XREF.REACHABLE_VIA_INDEX","CHECK.XREF.BOUNDARIES_DECLARED","CHECK.XREF.BRIDGES_DECLARED","CHECK.XREF.ANTI_NOISE"]
  DISPATCH:
    NEXT_MODULE_KEY: "COR.KB_SENTINEL"
    NEXT_PROMPT: "го"

On GAP:
STATUS: GAP
GAP_CODE: GAP.XREF_KEYS_NOT_DECLARED_YET
REQUIRED_FIX: "Provide explicit XREF key set in ROUTE_TOKEN after routing."
XREF_ACCESS_REPORT:
  XREF_REQUIRED: true
  XREF_ANCHOR_KEYS: []
  XREF_BRIDGE_KEYS: []
  XREF_GUARD_KEYS: []
  XREF_TARGET_REALMS: ["REALM.CORE"]
  XREF_MIN_PLAN_KEYS: []
  XREF_CHECKLIST: ["CHECK.XREF.REACHABLE_VIA_INDEX","CHECK.XREF.BOUNDARIES_DECLARED","CHECK.XREF.BRIDGES_DECLARED","CHECK.XREF.ANTI_NOISE"]
  DISPATCH:
    NEXT_MODULE_KEY: "COR.KB_SENTINEL"
    NEXT_PROMPT: "го"

On FAIL:
STATUS: FAIL
FAIL_CODE: FAIL.XREF_KEYS_MISSING
REQUIRED_FIX: "Add XREF anchors and required bridges to ROUTE_TOKEN."
NEXT_PROMPT: "го"

---

## [M] GATES
PASS if:
- Keys-only (no RAW, no PATH)
- XREF_REQUIRED computed deterministically
- For known domain: anchors declared; bridges declared when cross-realm intent exists
- XREF_MIN_PLAN_KEYS respects noise budget and is minimal
- NEXT_MODULE_KEY == COR.KB_SENTINEL

GAP if:
- Domain not resolved yet and XREF keys are not declared

FAIL if:
- Required inputs missing
- Known domain but required XREF key sets missing
- Non-deterministic realm list
- Noise budget impossible
