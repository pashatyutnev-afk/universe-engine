FILE: UE_V2/03_ENT/30_ORC_ENT/01_CORE_ORC_ENT/09__COR__PIPE_DISPATCHER__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 01_CORE_ORC_ENT
DOC_TYPE: ORC_ENTITY_MODULE
DOMAIN: COR_ORC_ENT
KEY: COR.PIPE_DISPATCHER
UID: UE.V2.ENT.ORC.COR.PIPE_DISPATCHER.001
VERSION: 1.1.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-09
OWNER: ORC_ENT
NAV_RULE: RAW-only enforcement (KEY->IDX->RAW)

---

## [M] ROLE
Pipeline dispatcher module.

Builds deterministic dispatch context for a selected PIPE.
Dispatcher does NOT execute the pipe; it produces a **phased** open-plan (keys-only) so the system can:
- explode a task into sub-tasks,
- distribute work to domain entities,
- avoid “one-shot minimalism”.

---

## [M] PURPOSE
- Convert `PIPE_SELECTION_REPORT` into `DISPATCH_CONTEXT` (keys-only).
- Provide **PHASE_PLAN** (multiple small open-plans) so entities do not idle.
- Enforce “anti-noise” via per-phase budgets (not a single tiny budget for the whole run).
- Ensure PIPE is reachable via NAV proofs before any further action.
- Produce the next stable user action: "го".

---

## [M] HARD_RULES
- Keys-only in outputs. Never output RAW or PATH in DISPATCH_CONTEXT.
- No pipe execution here. Only dispatch preparation.
- No invention: PIPE_KEY and required checks must come from inputs OR from **CANON PLAYBOOKS** below (predefined, repo-stored).
- Deterministic: same inputs => same DISPATCH_CONTEXT.
- Anti-noise is **per phase**:
  - default `PHASE_NOISE_BUDGET = 12` keys (unless ROUTE_TOKEN overrides).
  - if a phase needs more than budget → split into sub-phase (A/B).
- Must preserve ROUTE_TOKEN scope; no route drift.

---

## [M] INPUTS
- ROUTE_TOKEN (required)
  - DOMAIN
  - ARTIFACT_TYPE
  - MODE_HINT (optional)
  - REQUIRED_IDX: ["KEY"...]
  - REQUIRED_CHECKS: ["CHECK.*"...]
  - EXEC_MODE
  - NOISE_BUDGET (optional, overrides defaults)
  - TRACE_FLAGS
- PIPE_SELECTION_REPORT (required, from COR.PIPE_SELECTOR)
  - PIPE_KEY
  - PIPE_KIND
  - SELECTION_REASONS
  - REQUIRED_CHECKS
  - REQUIRED_IDX
- NAV_ACCESS_PROOF (required)
  - REALM_ACCESS_OK: true|false
  - REACHABLE_KEYS: ["KEY"...]
- OPTIONAL: REG_ACCESS_REPORT / XREF_ACCESS_REPORT / KB_ACCESS_REPORT (forward-only)

---

## [M] OUTPUTS
- DISPATCH_CONTEXT (keys-only)
  - PIPE_KEY: "<PIPE.KEY>"
  - PIPE_KIND: "DEFAULT|DOMAIN|SPECIAL"
  - PHASE_PLAN: [PHASE ...]   # ordered phases (each phase has small OPEN_PLAN_KEYS)
  - REQUIRED_IDX: ["KEY"...]
  - REQUIRED_CHECKS: ["CHECK.*"...]
  - FORWARD_REPORTS: REG/XREF/KB
  - DISPATCH:
      TARGET_LAYER: "PIPE"
      NEXT_MODULE_KEY: "COR.STEP_RUN_CONTROLLER"
      NEXT_PROMPT: "го"
- STATUS: PASS | FAIL | GAP
- FAIL_CODE or GAP_CODE
- REQUIRED_FIX (on GAP/FAIL)
- NEXT_MODULE_KEY (on PASS): COR.STEP_RUN_CONTROLLER
- NEXT_PROMPT: "го"

PHASE (schema):
  PHASE_ID: "S0|S1|..."
  PHASE_NAME: "..."
  OPEN_PLAN_KEYS: ["KEY"...]          # <= PHASE_NOISE_BUDGET
  EXPECTED_OUTPUT_KEYS: ["TOKEN"...]  # high-level expected outputs
  STOP_RULE: "..."                   # when phase is considered complete
  NEXT_PROMPT: "го"

---

## [M] CANON PLAYBOOKS (DOMAIN PRELOAD)
These playbooks define which entities MUST participate, by domain.
They are **keys-only** and are allowed as “non-invention” because they are repo-stored in this module.

### PLAYBOOK: MUSIC / TRACK (PIPE_ID: MUS.TRACK)
PHASE_NOISE_BUDGET_DEFAULT: 12

S0 / INTAKE + CONSTRAINTS
OPEN_PLAN_KEYS:
- CTL.MUS.DURATION_POLICY
- CTL.MUS.PROMPT_CONTRACT
- CTL.MUS.QUALITY_GATES
EXPECTED_OUTPUT_KEYS:
- CONSTRAINT_FRAME
- QUALITY_GATE_FRAME
STOP_RULE:
- constraints locked (duration/structure/language/bpm)

S1 / STYLE ROUTING (genre fusion + energy arc)
OPEN_PLAN_KEYS:
- MUS.GENRE_STYLE_ROUTER
- MUS.ARRANGEMENT_ROUTER
- CTL.MUS.NEGATIVE_SPEC_LIBRARY
EXPECTED_OUTPUT_KEYS:
- STYLE_PROFILE
- ARR_PROFILE
- NEGATIVE_DRAFT
STOP_RULE:
- STYLE_PROFILE and ARR_PROFILE exist

S2 / HOOK EXPLOSION (pool + quick panel)
OPEN_PLAN_KEYS:
- MUS.HOOK_FORGE
- QA.MUS.HOOK_PANEL
- VAL.MUS.HOOK_TIMING
EXPECTED_OUTPUT_KEYS:
- HOOK_POOL (ranked)
- HOOK_TOP3
STOP_RULE:
- HOOK_TOP3 chosen (at least 3)

S3 / LYRICS FACTORY (variants + controls)
OPEN_PLAN_KEYS:
- MUS.LYRIC_BRIEF_FACTORY
- MUS.LYRICS_ROOM
- MUS.LYRIC_DRAFTER
- MUS.LYRIC_EDITOR
- CTL.MUS.POET_PD_POLICY
- CTL.MUS.SUNO_PHRASEBOOK
- CTL.MUS.CTL.TONE_AND_ETHOS
- CTL.MUS.CTL.FLOW_AND_PRONUNCIATION
- MUS.QA_CHECKS
EXPECTED_OUTPUT_KEYS:
- LYRICS_VARIANTS (3–6)
- LYRICS_TOP1
STOP_RULE:
- LYRICS_TOP1 passes QA (no hard fails)

S4 / PROMPT PACK (2–4 variants)
OPEN_PLAN_KEYS:
- MUS.PROMPT_PACKAGER
- MUS.PROMPT_PACKAGER_PLUS
- VAL.MUS.PROMPT_FIDELITY
- CTL.MUS.VARIANT_POLICY
EXPECTED_OUTPUT_KEYS:
- SUNO_PACK_VARIANTS (2–4)
STOP_RULE:
- at least 2 valid packs exist

S5 / QA + RELEASE PACK
OPEN_PLAN_KEYS:
- QA.MUS.MIX_TRANSLATION
- QA.MUS.TRACK_QA_PANEL
- VAL.MUS.RELEASE_PACK_READY
- MUS.METADATA_FACTORY
- MUS.IDENTITY_BUILD
- VAL.MUS.NAMING_COLLISION
EXPECTED_OUTPUT_KEYS:
- FINAL_SUNO_PACK
- RELEASE_PACK
STOP_RULE:
- FINAL_SUNO_PACK ready + release checks pass

S6 / FOCUS LOOPS (optional, only on FAIL)
OPEN_PLAN_KEYS:
- MUS.HOOK_FOCUS_LOOP
- MUS.MIX_FOCUS_LOOP
- MUS.LYRICS_FOCUS_LOOP
- CTL.MUS.FOCUS_LOOP_STOP_RULES
EXPECTED_OUTPUT_KEYS:
- IMPROVED_PACK
STOP_RULE:
- stop rules trigger OR all gates pass

---

## [M] DISPATCH LOGIC (DETERMINISTIC)
1) Validate NAV_ACCESS_PROOF.REALM_ACCESS_OK == true
   - else FAIL: NAV_ACCESS_DENIED
2) Take PIPE_KEY from PIPE_SELECTION_REPORT
3) Select PLAYBOOK by ROUTE_TOKEN.DOMAIN + PIPE_KEY (or PIPE_ID class)
   - if no playbook → GAP: PLAYBOOK_MISSING
4) Build DISPATCH_CONTEXT:
   - REQUIRED_CHECKS = PIPE_SELECTION_REPORT.REQUIRED_CHECKS (+ ROUTE_TOKEN.REQUIRED_CHECKS)
   - REQUIRED_IDX = PIPE_SELECTION_REPORT.REQUIRED_IDX (+ ROUTE_TOKEN.REQUIRED_IDX)
   - PHASE_PLAN = playbook phases (ordered)
5) Output NEXT_MODULE_KEY = COR.STEP_RUN_CONTROLLER and NEXT_PROMPT = "го"

---

## [M] FAIL / GAP CODES
FAIL:
- NAV_ACCESS_DENIED
- INPUT_MISSING (ROUTE_TOKEN or PIPE_SELECTION_REPORT)

GAP:
- PLAYBOOK_MISSING
- KEY_NOT_REACHABLE (when NAV_ACCESS_PROOF lacks key needed by playbook)

REQUIRED_FIX format:
- what is missing
- which key/module should be added or indexed

---

## [M] NOTES
- This dispatcher is the answer to “кто решает кто участвует”.
  Decision ownership here is **playbook-driven** (domain policy), not ad-hoc minimal loading.
- Step-run controller consumes PHASE_PLAN and advances only after STOP_RULE triggers.
