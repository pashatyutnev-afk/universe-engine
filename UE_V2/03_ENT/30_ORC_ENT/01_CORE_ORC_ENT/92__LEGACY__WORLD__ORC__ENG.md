FILE: UE_V2/03_ENT/30_ORC_ENT/01_CORE_ORC_ENT/92__LEGACY__WORLD__ORC__ENG.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 01_CORE_ORC_ENT
DOC_TYPE: ORC_ENTITY_MODULE (LEGACY_ADAPTER)
DOMAIN: COR_ORC_ENT
KEY: LEGACY.WORLD_ORC_ENG
UID: UE.V2.ENT.ORC.LEGACY.WORLD_ORC_ENG.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: RAW-only enforcement (KEY->IDX->RAW)

---

## [M] ROLE
Legacy adapter orchestrator for worldbuilding tasks (ENG flavor).
Brings legacy “world pipeline” behavior into UE_V2 while enforcing RAW-only nav, minimal load, step-run cadence, deterministic formatting, and governance boundaries.

---

## [M] PURPOSE
- Execute legacy worldbuilding flows inside UE_V2 without breaking NAV/REG/XREF/KB/LOG laws.
- Translate UE_V2 ROUTE_TOKEN + TASK_TEXT into a controlled worldbuilding plan.
- Produce UE_V2-ready world artifacts (packageable blocks) instead of uncontrolled lore dumps.
- Maintain novelty and avoid recognizable repeated phrasing across outputs.

---

## [M] WHEN TO USE
Use this module only when:
- ROUTE_TOKEN.PIPE_SELECTED explicitly targets legacy world adapter, OR
- CORE uses legacy fallback due to missing domain pipe and fallback is permitted by REQUIRED_CHECKS.

Do NOT use when:
- There is an active UE_V2 domain pipe for worlds/lore and it is selected.
- The run requires registry/entity mutations (canonical creation/edit) that must go through governance/entity pipes.
- The task requires bulk generation beyond anti-noise bounds.

---

## [M] HARD_RULES
- Adapter only:
  - Never changes routing decisions. Runs only after COR pipeline dispatcher selects it.
- RAW-only:
  - Any reference must resolve via IDX->RAW. No PATH обходы.
- Keys-only contract:
  - Inputs/outputs reference KEYS and check-ids, not raw URLs in narrative.
- Minimal load:
  - Open only REQUIRED_IDX + 1–3 target files max.
- Step-run:
  - Output only the increment required for the current "го" step.
- No direct entity writes:
  - May propose drafts/specs but must not mutate canonical registries, passports, or indexes.
- Canon-control:
  - Outputs are drafts unless explicitly routed to canonical entity pipe.
- Safety:
  - No real-world sensitive targeting. No instructions enabling harm.

---

## [M] INPUTS
- ROUTE_TOKEN (required)
  - DOMAIN, ARTIFACT_TYPE, MODE, PIPE_SELECTED, REQUIRED_IDX, REQUIRED_CHECKS, EXEC_MODE
- TASK_TEXT (required)
- CONSTRAINTS (optional)
  - platform, duration, style, references, medium, tone
- RUN_STATE (required)
  - STEP, STATUS, OPENED_KEYS (optional)
- LEGACY_HINT (optional)
  - legacy_profile: WORLD_DEFAULT|WORLD_RULES|WORLD_ATLAS
  - detail_budget: LOW|MED|HIGH (bounded by anti-noise)

---

## [M] OUTPUTS
- LEGACY_EXEC_PLAN (internal)
  - mapping UE_V2 steps to legacy world actions
- DELIVERABLES_RAW (for packager)
  - list of deliverable items {TITLE, BODY, META(optional)}
- CHECK_REPORT updates (optional)
  - WARN/FAILED notes when boundaries are hit

User-facing output is emitted via COR.RELEASE_PACKAGER.

---

## [M] COMPATIBILITY BOUNDARIES
Supported legacy flavors:
- World pillars and constraints (tone, laws, themes)
- High-level geography and region roles (no exhaustive atlases)
- Factions overview (2–6 factions, functional contrast)
- Technology/magic palette rules (principles and constraints, not encyclopedias)
- Scene-function notes for “how world behaves in content”

Not supported (must route to domain pipes):
- Canonical registry/entity creation or edits
- Long-form encyclopedic lore, exhaustive timelines, massive genealogies
- Cross-realm canonical linkage requiring XREF/REG updates
- Detailed real-world political targeting or instructions enabling harm

---

## [M] LEGACY PROFILE MAP
### WORLD_DEFAULT
- Output: world pillars + core constraints + short region roles
- Noise: low
- Use: quick foundation for series/albums/themes

### WORLD_RULES
- Output: world laws/constraints + taboo list + consistency guardrails
- Noise: low-medium
- Use: keeping outputs consistent across many albums/releases

### WORLD_ATLAS
- Output: compact “atlas sketch” (regions + factions + signature motifs)
- Noise: medium (bounded)
- Use: variety generation without canon writes

If MODE_HINT is present:
- FAST -> WORLD_DEFAULT
- RELEASE_READY -> WORLD_RULES
- MASTERPIECE -> WORLD_ATLAS (still bounded)

---

## [M] STEP-RUN BEHAVIOR (adapter rules)
Aligns to UE_V2 step cadence and never bypasses COR.STEP_RUN_CONTROLLER.

S0) Intake mirror (read-only)
- Reuse normalized inputs from COR.TASK_INTAKE where available.
- If TASK_TEXT missing -> STOP (fail-handler semantics).

S1) Route confirmation
- Verify ROUTE_TOKEN permits legacy world adapter.
- If not permitted -> GAP ("legacy not permitted") and stop.

S2) Plan build
- Select legacy_profile (LEGACY_HINT or derived from MODE_HINT).
- Apply detail budget caps:
  - LOW: 6–9 bullets per deliverable
  - MED: 10–14 bullets
  - HIGH: 15–18 bullets (max, only if gates allow)

S3) Produce deliverables for current step
- Output structured worldbuilding increments only.
- No lore floods. No canon claims. No uncontrolled expansions.

---

## [M] DELIVERABLE SHAPES (canonical titles)
Allowed DELIVERABLES_RAW titles:

- "WORLD_PILLARS"
  - 5–7 pillars: tone, promise, fear, contrast, sensory signature, rhythm

- "WORLD_CONSTRAINTS"
  - hard constraints, taboo list, consistency guardrails, drift-prevention notes

- "REGION_ROLE_MAP"
  - 3–6 regions with functional roles (not exhaustive geography)

- "FACTIONS_OVERVIEW"
  - 2–6 factions, each: goal, method, aesthetic, pressure they apply

- "TECH_MAGIC_PALETTE"
  - principles and limits, acceptable motifs, forbidden shortcuts

- "SCENE_FUNCTION_NOTES"
  - how world reacts to actions, how stakes manifest, what never happens

- "NEXT_STEP_QUEST"
  - one deterministic next prompt for the user

If WARN/GAP/STOP:
- Only "NEXT_ACTION" with minimal instruction.

---

## [M] NOISE CONTROLS
- Anti-repetition:
  - Rotate phrasing, avoid signature templates, vary sentence shapes while keeping deterministic ordering.
- Variation pool:
  - Use motif pools (sound, texture, light, weather, materials) to differentiate worlds.
- Bound complexity:
  - Prefer constraint-first, then selective detail. Avoid encyclopedic breadth.
- Avoid namedropping:
  - No direct borrowing of recognizable IP. Keep original abstractions.

---

## [M] SAFETY / RISK NOTES
- If the task requests realistic instructions enabling harm:
  - STOP.
- If the task requests targeted political manipulation or harassment:
  - STOP.
- If the task attempts to replicate a protected fictional universe 1:1:
  - WARN and abstract; if replication is mandatory -> STOP.

(User-facing phrasing handled by COR.FAIL_HANDLER.)

---

## [M] ERROR HANDLING (adapter-level)
- Unsupported mandatory request -> GAP (missing pipe) or STOP (blocked), depending on REQUIRED_CHECKS.
- Missing REQUIRED_IDX access -> GAP (dependency missing).
- Safety boundary triggered -> STOP.
- Over-budget request -> WARN and downshift detail_budget.

Module emits structured signals; COR.FAIL_HANDLER produces the user-facing explanation.

---

## [M] GATES
PASS if:
- RAW-only, minimal load, step-run satisfied
- DELIVERABLES_RAW created using canonical titles
- No forbidden ops attempted

WARN if:
- Legacy fallback used while a domain pipe exists but not selected (must be logged)
- User request trends toward replication or harm (abstracted/blocked)

GAP if:
- Required legacy keys/idx missing
- Legacy adapter not permitted by route token

STOP if:
- TASK_TEXT missing
- Safety boundary blocks execution
- Forbidden operation requested as mandatory
