FILE: UE_V2/03_ENT/30_ORC_ENT/01_CORE_ORC_ENT/90__LEGACY__NARRATIVE__ORC__ENG.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 01_CORE_ORC_ENT
DOC_TYPE: ORC_ENTITY_MODULE (LEGACY_ADAPTER)
DOMAIN: COR_ORC_ENT
KEY: LEGACY.NARRATIVE_ORC_ENG
UID: UE.V2.ENT.ORC.LEGACY.NARRATIVE_ORC_ENG.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: RAW-only enforcement (KEY->IDX->RAW)

---

## [M] ROLE
Legacy adapter orchestrator for narrative-style tasks (ENG flavor).
Provides backward compatibility with UE legacy narrative workflows while enforcing UE_V2 rules: RAW-only nav, minimal load, step-run, and keys-only contracts.

---

## [M] PURPOSE
- Allow old/legacy narrative pipelines to run inside UE_V2 without breaking governance rules.
- Translate UE_V2 ROUTE_TOKEN + TASK_TEXT into a legacy-compatible execution plan.
- Constrain legacy behavior to UE_V2 anti-noise and safety boundaries.
- Produce deliverables through UE_V2 packaging and gating (not legacy formatting).

---

## [M] WHEN TO USE
Use this module only when:
- ROUTE_TOKEN indicates LEGACY mode or legacy pipeline selection, OR
- PIPE_DEFAULT cannot resolve a domain-specific UE_V2 pipe but legacy narrative path exists and is allowed by checks.

Do NOT use when:
- A domain UE_V2 pipe exists and passes routing checks.
- The task demands strict domain artifacts not supported by legacy narrative flow.

---

## [M] HARD_RULES
- Adapter, not owner:
  - This module does not replace CORE routing; it executes only after CORE selects it.
- RAW-only:
  - Any legacy references must be resolved through UE_V2 IDX->RAW. No PATH обходы.
- Keys-only contract:
  - Inputs/outputs reference KEYS and check-ids, not URLs.
- Minimal load:
  - Never mass-load legacy trees. Open only REQUIRED_IDX + 1–3 target files max.
- Step-run only:
  - Must comply with UE_V2 step cadence; do not run “full story” in one go unless MODE_HINT explicitly demands and gates allow.
- No legacy formatting leaks:
  - Final user-facing output is packaged by COR.RELEASE_PACKAGER canonical OUTPUT_PACK.

---

## [M] INPUTS
- ROUTE_TOKEN (required)
  - DOMAIN, ARTIFACT_TYPE, MODE, PIPE_SELECTED, REQUIRED_IDX, REQUIRED_CHECKS, EXEC_MODE
- TASK_TEXT (required)
- CONSTRAINTS (optional)
  - platform, duration, style, references
- RUN_STATE (required)
  - STEP, STATUS, OPENED_KEYS (optional)
- LEGACY_HINT (optional)
  - legacy_profile: NARRATIVE_DEFAULT|NARRATIVE_DENSE|NARRATIVE_SCENE
  - legacy_steps: integer (cap to UE_V2 step-run)

---

## [M] OUTPUTS
- LEGACY_EXEC_PLAN (internal)
  - A small deterministic plan describing how legacy actions map to UE_V2 steps.
- DELIVERABLES_RAW (for packager)
  - list of deliverable items {TITLE, BODY, META(optional)}
- CHECK_REPORT updates (optional)
  - WARN/FAILED notes if legacy flow hits boundary conditions

User-facing output is emitted via COR.RELEASE_PACKAGER.

---

## [M] COMPATIBILITY BOUNDARIES
This adapter supports only these legacy task flavors:
- Narrative outline / arc
- Scene beats and sequencing
- Character voice constraints (high-level)
- Style constraints and tone shaping (high-level)

Not supported (must route to domain pipes):
- Canon registry mutations
- Entity creation/edit operations
- Bulk KB operations
- Cross-realm refactoring
- Compliance index rewrites

If requested, raise WARN or route to FAIL_HANDLER with GAP/STOP depending on checks.

---

## [M] LEGACY PROFILE MAP
Profiles are deterministic presets for how much structure vs prose is allowed.

### NARRATIVE_DEFAULT
- Output: structured outline + 1 sample scene beat
- Noise: low
- Typical use: brainstorming, first-pass outline

### NARRATIVE_DENSE
- Output: deeper outline + multiple beats + style constraints
- Noise: medium (still bounded)
- Typical use: release-ready narrative spec

### NARRATIVE_SCENE
- Output: scene-by-scene beat sheet (not full prose)
- Noise: medium-high but still step-run bounded
- Typical use: scene planning

---

## [M] STEP-RUN BEHAVIOR (adapter rules)
This module must align to UE_V2 steps. It never overrides the global step-run controller; it only produces deliverables appropriate for the current step.

S0) Intake mirror (read-only)
- Reuse normalized inputs from COR.TASK_INTAKE (do not re-parse if already available)
- If TASK_TEXT missing -> emit STOP via FAIL_HANDLER pattern

S1) Route confirmation
- Verify ROUTE_TOKEN allows legacy execution:
  - PIPE_SELECTED indicates legacy OR EXEC_MODE indicates fallback allowed
- If not allowed -> emit GAP ("legacy not permitted") and stop

S2) Legacy execution plan build
- Select legacy_profile:
  - Use LEGACY_HINT.legacy_profile if provided
  - Else derive from MODE_HINT:
    - FAST -> NARRATIVE_DEFAULT
    - RELEASE_READY -> NARRATIVE_DENSE
    - MASTERPIECE -> NARRATIVE_SCENE (bounded)
- Compute legacy_steps cap:
  - Default: 1 step worth of work per "го"
  - Never exceed 2 steps worth of deliverables in a single run

S3) Produce deliverables for current step
- Generate deliverables strictly as:
  - Outline / beats / constraints
  - No long prose dumps
- Include constraints and uniqueness guards if relevant
- Hand off to packager

---

## [M] DELIVERABLE SHAPES (canonical titles)
When producing DELIVERABLES_RAW, titles must be chosen from this set:

- "NARRATIVE_SKELETON"
  - 8–14 bullet arc outline, deterministic ordering

- "SCENE_BEAT_SHEET"
  - numbered beats (1..N), 10–18 items max per step

- "VOICE_AND_STYLE_CONSTRAINTS"
  - 6–12 constraints, avoid repeating phrases, avoid drift

- "NEXT_STEP_QUEST"
  - a single actionable next prompt for the user (still packager sets final NEXT_PROMPT)

If STATUS is WARN/GAP/STOP, only produce a single item:
- "NEXT_ACTION" with the minimal instruction.

---

## [M] NOISE CONTROLS
- Avoid repeated phrasing:
  - Do not reuse the same line starters across beats.
  - Prefer variable syntax patterns (but keep ordering deterministic).
- Avoid author-identifiable fingerprints:
  - Never quote known texts; only create generalized constraints and beats.
- Keep outputs compact:
  - One screen per deliverable item when possible.

---

## [M] ERROR HANDLING (adapter-level)
- If legacy flow requests unsupported operation:
  - If it is optional: WARN + suggest routing to proper pipe next step
  - If it is required: GAP with missing pipe/idx requirement
- If required IDX not accessible:
  - GAP (dependency missing)
- If safety boundary triggered by REQUIRED_CHECKS:
  - STOP (blocked) via FAIL_HANDLER semantics

This module emits only structured signals; COR.FAIL_HANDLER normalizes user messaging.

---

## [M] GATES
PASS if:
- Legacy execution stays within UE_V2 constraints (RAW-only, minimal load, step-run)
- DELIVERABLES_RAW created with canonical titles
- No forbidden operations attempted

WARN if:
- Legacy fallback used while domain pipe exists but is not selected (must be logged)
- Output requires further routing confirmation next step️

GAP if:
- Required legacy compatibility keys/idx are missing
- Legacy not permitted by route token

STOP if:
- TASK_TEXT missing
- Safety boundary blocks execution
- Forbidden operation requested as mandatory
