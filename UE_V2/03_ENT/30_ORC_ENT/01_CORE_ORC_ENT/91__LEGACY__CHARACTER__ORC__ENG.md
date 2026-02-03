FILE: UE_V2/03_ENT/30_ORC_ENT/01_CORE_ORC_ENT/91__LEGACY__CHARACTER__ORC__ENG.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 01_CORE_ORC_ENT
DOC_TYPE: ORC_ENTITY_MODULE (LEGACY_ADAPTER)
DOMAIN: COR_ORC_ENT
KEY: LEGACY.CHARACTER_ORC_ENG
UID: UE.V2.ENT.ORC.LEGACY.CHARACTER_ORC_ENG.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: RAW-only enforcement (KEY->IDX->RAW)

---

## [M] ROLE
Legacy adapter orchestrator for character-design tasks (ENG flavor).
Provides backward compatibility for legacy “character pipeline” behaviors while enforcing UE_V2 rules: RAW-only nav, minimal load, step-run cadence, deterministic outputs.

---

## [M] PURPOSE
- Run legacy character workflows inside UE_V2 without violating governance.
- Translate UE_V2 ROUTE_TOKEN + TASK_TEXT into a legacy-compatible character plan.
- Prevent identity leakage, over-specificity, and uncontrolled expansion (“noise”) typical in legacy flows.
- Output UE_V2-ready character artifacts (structured, packageable), not legacy freeform dumps.

---

## [M] WHEN TO USE
Use this module only when:
- ROUTE_TOKEN indicates legacy execution OR PIPE_SELECTED selects legacy character adapter, OR
- CORE routes to legacy due to missing domain pipe and fallback is explicitly allowed by REQUIRED_CHECKS.

Do NOT use when:
- A UE_V2 domain pipe for characters/entities exists and is selected.
- The run involves registry/entity mutations (creation/edit) that must be handled by governance/entity pipes.

---

## [M] HARD_RULES
- Adapter only:
  - Never overrides COR routing; runs only after selection by CORE pipeline dispatcher.
- RAW-only:
  - Any legacy references must resolve via UE_V2 IDX->RAW. No PATH обходы.
- Keys-only contract:
  - Inputs/outputs reference KEYS and check-ids, not URLs.
- Minimal load:
  - Open only REQUIRED_IDX + 1–3 target files max.
- Step-run:
  - Produce only step-appropriate increments per “го”.
- No direct entity writes:
  - This module may propose character specs but must not mutate registries or entity passports.
- No personal data:
  - Do not generate real-person likenesses or doxxing-like specificity; keep fictional abstraction unless explicitly allowed by domain rules.

---

## [M] INPUTS
- ROUTE_TOKEN (required)
  - DOMAIN, ARTIFACT_TYPE, MODE, PIPE_SELECTED, REQUIRED_IDX, REQUIRED_CHECKS, EXEC_MODE
- TASK_TEXT (required)
- CONSTRAINTS (optional)
  - platform, duration, style, references, target medium
- RUN_STATE (required)
  - STEP, STATUS, OPENED_KEYS (optional)
- LEGACY_HINT (optional)
  - legacy_profile: CHARACTER_DEFAULT|CHARACTER_VOICE|CHARACTER_CAST
  - detail_budget: LOW|MED|HIGH (bounded by anti-noise)

---

## [M] OUTPUTS
- LEGACY_EXEC_PLAN (internal)
  - mapping of UE_V2 steps to legacy character actions
- DELIVERABLES_RAW (for packager)
  - list of deliverable items {TITLE, BODY, META(optional)}
- CHECK_REPORT updates (optional)
  - WARN/FAILED notes when boundaries are hit

User-facing output is emitted via COR.RELEASE_PACKAGER.

---

## [M] COMPATIBILITY BOUNDARIES
Supported legacy flavors:
- Single character spec (core identity, goals, conflict)
- Voice and dialogue constraints (style guardrails)
- Small cast layout (2–6 roles) at high-level
- Scene-function mapping (how character behaves per scene role)

Not supported (must route to domain pipes):
- Registry operations (create/edit canonical entities)
- Long-form biographies with excessive detail
- Cross-realm canonical linkage requiring XREF/REG updates
- Bulk cast generation beyond bounds

---

## [M] LEGACY PROFILE MAP
### CHARACTER_DEFAULT
- Output: compact character passport draft (non-canonical)
- Noise: low
- Use: quick iteration, early ideation

### CHARACTER_VOICE
- Output: voice constraints + dialogue patterns + taboo list
- Noise: low-medium
- Use: consistent speech for songs/scripts

### CHARACTER_CAST
- Output: 2–6 roles with distinct functions and contrast matrix
- Noise: medium (bounded)
- Use: group/cast planning without canon writes

If MODE_HINT is present:
- FAST -> CHARACTER_DEFAULT
- RELEASE_READY -> CHARACTER_VOICE
- MASTERPIECE -> CHARACTER_CAST (still bounded)

---

## [M] STEP-RUN BEHAVIOR (adapter rules)
This module aligns to UE_V2 steps and never bypasses COR.STEP_RUN_CONTROLLER.

S0) Intake mirror (read-only)
- Reuse normalized inputs from COR.TASK_INTAKE where available.
- If TASK_TEXT missing -> STOP via FAIL_HANDLER semantics.

S1) Route confirmation
- Verify ROUTE_TOKEN permits legacy character adapter.
- If not permitted -> GAP ("legacy not permitted") and stop.

S2) Plan build
- Select legacy_profile (LEGACY_HINT or derived from MODE_HINT).
- Set detail budget cap:
  - LOW: 6–9 bullets per deliverable
  - MED: 10–14 bullets
  - HIGH: 15–18 bullets (max, only if gates allow)

S3) Produce deliverables for current step
- Produce structured character spec increments only.
- Avoid repeating phrases and templates that become recognizable.
- No canon claims; mark as “draft for packaging”.

---

## [M] DELIVERABLE SHAPES (canonical titles)
Allowed DELIVERABLES_RAW titles:

- "CHARACTER_CORE"
  - identity anchors: desire, fear, contradiction, wound, mask, truth

- "CHARACTER_VOICE_CONSTRAINTS"
  - diction, rhythm, metaphor palette, forbidden tropes, repetition guard

- "CHARACTER_CONTRAST_MATRIX"
  - if CAST: table-like bullets contrasting roles on 6–8 axes

- "SCENE_FUNCTION_NOTES"
  - how the character behaves as a function of scene purpose (not plot dump)

- "NEXT_STEP_QUEST"
  - one deterministic next prompt for the user (packager will set final NEXT_PROMPT)

If WARN/GAP/STOP:
- Only "NEXT_ACTION" with minimal instruction.

---

## [M] NOISE CONTROLS
- Anti-repetition:
  - Rotate sentence openers; vary syntax while keeping deterministic ordering.
- Avoid over-specific descriptors:
  - No exact addresses, legal names, real-world identifiers, biometric-level detail.
- Avoid “signature” patterns:
  - Do not reuse identical constraint lists across characters; use a constraint pool with variation.
- Keep outputs compact per step:
  - No “full biography” walls of text.

---

## [M] SAFETY / RISK NOTES
- If the task tries to emulate a real person or identifiable celebrity:
  - WARN and abstract into generic traits; if required specificity is demanded -> STOP (safety boundary).
- If the task asks for manipulative/doxxing content:
  - STOP.

(Actual messaging normalized by COR.FAIL_HANDLER.)

---

## [M] ERROR HANDLING (adapter-level)
- Unsupported mandatory request -> GAP (missing pipe) or STOP (blocked), depending on REQUIRED_CHECKS.
- Missing REQUIRED_IDX access -> GAP (dependency missing).
- Safety boundary triggered -> STOP.

Module emits structured signals; COR.FAIL_HANDLER produces the user-facing explanation.

---

## [M] GATES
PASS if:
- RAW-only, minimal load, step-run satisfied
- DELIVERABLES_RAW created using canonical titles
- No forbidden ops attempted

WARN if:
- Legacy fallback used while domain pipe exists but not selected (must be logged)
- User request trends toward over-specificity (abstracted)

GAP if:
- Required legacy keys/idx missing
- Legacy adapter not permitted by route token

STOP if:
- TASK_TEXT missing
- Safety boundary blocks execution
- Forbidden operation requested as mandatory
