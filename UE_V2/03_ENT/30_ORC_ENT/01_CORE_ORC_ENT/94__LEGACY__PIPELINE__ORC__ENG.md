FILE: UE_V2/03_ENT/30_ORC_ENT/01_CORE_ORC_ENT/94__LEGACY__PIPELINE__ORC__ENG.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 01_CORE_ORC_ENT
DOC_TYPE: ORC_ENTITY_MODULE (LEGACY_ADAPTER)
DOMAIN: COR_ORC_ENT
KEY: LEGACY.PIPELINE_ORC_ENG
UID: UE.V2.ENT.ORC.LEGACY.PIPELINE_ORC_ENG.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: RAW-only enforcement (KEY->IDX->RAW)

---

## [M] ROLE
Legacy adapter orchestrator for pipeline routing (ENG flavor).
Provides back-compat “pipeline selection + dispatch” behavior while honoring UE_V2 laws: RAW-only navigation, minimal-load, step-run cadence, deterministic routing via ROUTE_TOKEN, and mandatory logging hooks.

---

## [M] PURPOSE
- Serve as a compatibility bridge when legacy pipeline logic is required by ROUTE_TOKEN or when the core router selects legacy fallback.
- Translate legacy “choose pipeline by intent” patterns into UE_V2 ROUTE_TOKEN primitives without bypassing COR.ROUTE_TOKEN_BUILDER / COR.PIPE_SELECTOR / COR.PIPE_DISPATCHER.
- Provide deterministic resolution rules so the same TASK_TEXT yields the same PIPE_SELECTED under the same constraints.
- Prevent “pipeline drift” (jumping pipes mid-run without explicit decision log).

---

## [M] WHEN TO USE
Use only when:
- ROUTE_TOKEN.PIPE_SELECTED targets legacy pipeline adapter explicitly, OR
- CORE routing allows legacy fallback and selected it due to missing domain pipe.

Do NOT use when:
- UE_V2 domain pipe exists and is selected by COR.PIPE_SELECTOR.
- User requests mass navigation or opening many files (anti-noise violation).
- The run is in a governance-sensitive context requiring GVN.CHANGE_CONTROL decisions (this module is not governance).

---

## [M] HARD_RULES
- Adapter-only:
  - This module never invents new domains or entities. It only maps existing UE_V2 routing signals.
- No bypass:
  - Must not replace CORE router; can only operate inside its selected path.
- RAW-only:
  - Any references resolve via REQUIRED_IDX (KEY->RAW). No PATH usage when RAW exists.
- Determinism:
  - Routing decisions must be reproducible. No random choice.
- Minimal load:
  - Open only REQUIRED_IDX + NAV_ROOT (+ optional PIPE_DEFAULT) if not already in core open-set.
- Step-run:
  - Performs at most one routing decision per "го".
- Logging hooks:
  - Every non-trivial routing decision must emit a DECISION_LOG entry (through COR.LOGGER, not directly).
- No content generation:
  - This module is routing/control only. It does not produce lyrics/prompts beyond a minimal NEXT_ACTION.

---

## [M] INPUTS
- ROUTE_TOKEN (required)
  - DOMAIN, ARTIFACT_TYPE, MODE, REQUIRED_IDX, REQUIRED_CHECKS, EXEC_MODE
  - PIPE_SELECTED may be empty at entry (legacy helps choose) or already set (legacy verifies)
- TASK_TEXT (required)
- MODE_HINT (optional)
- CONSTRAINTS (optional)
  - platform, duration, style, references, output_format
- RUN_STATE (required)
  - STEP, OPENED_KEYS(optional), CURRENT_PIPE(optional)
- LEGACY_HINT (optional)
  - legacy_pipe_family: NARRATIVE|CHARACTER|WORLD|PRODUCTION|PIPELINE
  - fallback_policy: STRICT|ALLOW_FALLBACK (bounded)

---

## [M] OUTPUTS
- ROUTE_TOKEN_PATCH (optional)
  - PIPE_SELECTED set/validated
  - DEFAULT_ORC maybe set (legacy module name) only if needed for compatibility
  - REQUIRED_IDX may be augmented only with explicit rule and only if missing
- NEXT_ACTION
  - one deterministic next user prompt "го" plus what will happen next
- WARN/FAIL signals (structured)
  - for COR.FAIL_HANDLER / COR.GATEKEEPER

---

## [M] COMPATIBILITY MAP (legacy families -> UE_V2 pipes)
This module does not hardcode raw urls; it only returns PIPE_SELECTED as a KEY.
Actual KEY->RAW resolution happens via REQUIRED_IDX.

Legacy family mapping (conceptual):
- NARRATIVE -> PIPE.NARRATIVE (or domain narrative pipe)
- CHARACTER -> PIPE.CHARACTER
- WORLD -> PIPE.WORLD
- PRODUCTION -> PIPE.PRODUCTION
- PIPELINE -> PIPE.DEFAULT (meta-router) or PIPE.ROUTER_HELPER

If the mapped pipe KEY does not exist in REQUIRED_IDX:
- GAP if REQUIRED_CHECKS demand it,
- otherwise fallback to PIPE_DEFAULT if allowed.

---

## [M] ROUTING HEURISTICS (deterministic)
### [M] H0) Pre-checks
- If TASK_TEXT missing -> STOP
- If ROUTE_TOKEN.DOMAIN missing -> rely on COR.DOMAIN_DETECTOR output; if absent -> GAP (missing domain detection)

### [M] H1) If PIPE_SELECTED already set
- Validate it is permitted by REQUIRED_CHECKS and exists in REQUIRED_IDX
- If mismatch with CURRENT_PIPE:
  - require DECISION_LOG escalation (signal WARN: PIPE_SWITCH_REQUESTED)
  - do not switch silently

### [M] H2) If PIPE_SELECTED empty
Choose pipe using ordered rules:
1) If CONSTRAINTS.platform implies a dedicated pipe family (example: "suno" -> production/music pipe)
2) If ARTIFACT_TYPE implies pipeline (lyrics/prompts -> production; entity passport -> governance/entity pipe)
3) If legacy_pipe_family provided -> map using COMPATIBILITY MAP
4) Else use PIPE_DEFAULT

Tie-breakers (stable):
- MODE_HINT: FAST prefers PIPE_DEFAULT; RELEASE_READY prefers specialized pipe if available; MASTERPIECE prefers specialized pipe + stricter checks
- If multiple candidate pipes, pick lexicographically smallest KEY (deterministic) among allowed candidates

---

## [M] PIPE SWITCH POLICY (anti-drift)
- Default: no switching mid-run.
- Switch is allowed only if:
  - RUN_STATE.STEP boundary reached AND
  - ROUTE_TOKEN_PATCH explicitly requests switch AND
  - DECISION_LOG entry is required and emitted by core logger

If user tries to force switching without step boundary:
- WARN and defer to next step.

---

## [M] STEP-RUN BEHAVIOR
Aligned with UE_V2 cadence. This module can be called during core S3/S5 phases, but only emits minimal routing artifacts.

S0) Intake mirror
- Read inputs (no parsing beyond presence checks)

S1) Validate context
- Confirm RAW-only nav and required index access (via required keys, not by opening trees)

S2) Decide / validate pipe
- Apply routing heuristics H1/H2
- Output ROUTE_TOKEN_PATCH (if any)

S3) Hand back control
- Provide NEXT_ACTION: "го"
- Indicate which core component should run next:
  - COR.PIPE_SELECTOR (if pipe not locked)
  - COR.PIPE_DISPATCHER (if pipe locked and valid)

---

## [M] DELIVERABLE SHAPE (canonical)
This module must output only these titles:

- "ROUTE_TOKEN_PATCH"
  - fields: PIPE_SELECTED, DEFAULT_ORC(optional), REQUIRED_IDX(optional_additions), REQUIRED_CHECKS(optional_notes)

- "NEXT_ACTION"
  - one line instruction with "го" and what happens next

- "WARN_SIGNAL" (optional)
  - PIPE_SWITCH_REQUESTED | FALLBACK_USED | PIPE_KEY_MISSING

- "STOP_SIGNAL" (optional)
  - MISSING_TASK_TEXT | BLOCKED_BY_CHECKS

No other deliverables permitted.

---

## [M] SAFETY / COMPLIANCE
- If routing implies a disallowed task (e.g., explicit request for illegal instructions):
  - emit STOP_SIGNAL and let COR.FAIL_HANDLER respond.
- Do not route to pipes that would encourage policy violations (identity cloning, copyright copying).
- This module does not generate the prohibited content; it only blocks unsafe routing.

---

## [M] ERROR HANDLING
- GAP: PIPE_KEY_MISSING
  - Candidate pipe KEY not present in REQUIRED_IDX or cannot resolve RAW
- STOP: MISSING_TASK_TEXT
- WARN: FALLBACK_USED
  - When PIPE_DEFAULT used due to missing specialized pipe
- WARN: PIPE_SWITCH_REQUESTED
  - Attempt to change pipe mid-run without decision log

All user-facing phrasing is delegated to COR.FAIL_HANDLER.

---

## [M] GATES
PASS if:
- Deterministic pipe decision/validation produced
- ROUTE_TOKEN_PATCH is minimal and legal
- No bypass of core router occurred

WARN if:
- Fallback to PIPE_DEFAULT occurred
- Pipe switch requested and deferred

GAP if:
- Required pipe key missing from idx and checks require it

STOP if:
- TASK_TEXT missing
- Routing blocked by required checks / safety boundary
