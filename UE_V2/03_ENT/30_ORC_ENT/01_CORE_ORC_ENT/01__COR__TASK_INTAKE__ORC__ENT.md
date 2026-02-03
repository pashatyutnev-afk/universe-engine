FILE: UE_V2/03_ENT/30_ORC_ENT/01_CORE_ORC_ENT/01__COR__TASK_INTAKE__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 01_CORE_ORC_ENT
DOC_TYPE: ORC_ENTITY_MODULE
DOMAIN: COR_ORC_ENT
KEY: COR.TASK_INTAKE
UID: UE.V2.ENT.ORC.COR.TASK_INTAKE.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: Resolve via INDEX_MANIFEST (KEY->RAW)

---

## [M] ROLE
Task intake and normalization module.
Transforms raw user request into a normalized REQUEST envelope + initial run intent fields for ROUTE_TOKEN creation.

## [M] PURPOSE
- Extract TASK_TEXT, MODE_HINT, CONSTRAINTS, and intent signals from the user message.
- Normalize to canonical fields (minimal, deterministic).
- Emit safe defaults when optional inputs are missing.
- Produce a compact output that does not pollute context (ANTI_NOISE).

## [M] HARD_RULES
- Must not invent external facts or hidden requirements.
- Must not load other realms/files (except what caller already opened by contract).
- Must be deterministic: same input -> same normalized output.
- Must not expand long explanations; output is structured and short.
- Must never output RAW links (navigation belongs to contract/index).
- MODE is USAGE-ONLY: no repo edits.

## [M] INPUTS
- USER_MESSAGE: string (required)
- MODE_HINT: FAST | RELEASE_READY | MASTERPIECE (optional; may be embedded in message)
- CONSTRAINTS: object (optional; may be embedded in message)
- CONTEXT_HINTS: object (optional; e.g., platform, duration, style, refs)

## [M] OUTPUTS
- REQUEST (normalized envelope)
  - TASK_TEXT: string
  - MODE_HINT: FAST | RELEASE_READY | MASTERPIECE | null
  - CONSTRAINTS: object (may be empty)
  - INTENT_SIGNALS: object (small)
  - SAFETY_NOTES: object (small, only if needed)
- RUN_SEED (minimal seed for next modules)
  - EXEC_MODE: STEP_RUN
  - NEXT_MODULE_KEY: COR.DOMAIN_DETECTOR
  - NEXT_PROMPT: "го"
- STATUS: PASS | FAIL
- FAIL_CODE + REQUIRED_FIX (when FAIL)

## [M] NORMALIZATION (CANON)
N0) Trim whitespace; collapse repeated spaces.
N1) TASK_TEXT extraction:
  - If message contains an explicit task request, set TASK_TEXT = message (sanitized).
  - If message is "го" / "go" only -> FAIL (no task text).
N2) MODE_HINT extraction:
  - If MODE_HINT provided separately -> accept.
  - Else detect tokens (case-insensitive):
    - "fast" -> FAST
    - "release" / "готово" / "ready" -> RELEASE_READY
    - "masterpiece" / "идеал" -> MASTERPIECE
  - If none -> null (caller may default later).
N3) CONSTRAINTS extraction (minimal, no guessing):
  - If message contains explicit constraints, capture only these keys when present:
    - platform, duration, style, references, language, format, limits
  - Unknown keys are allowed but must be shallow (no nested heavy objects).
N4) INTENT_SIGNALS (tiny flags, not verbose):
  - has_duration: true/false
  - has_platform: true/false
  - has_style: true/false
  - has_refs: true/false
  - ambiguity_risk: low/med/high (deterministic heuristic)
N5) SAFETY_NOTES:
  - Only include if user request implies unsafe/forbidden action.
  - Otherwise omit or keep empty object.

## [M] ANTI_NOISE POLICY (MODULE)
- Output only REQUEST + RUN_SEED + STATUS (and FAIL details if needed).
- No commentary, no long guidance, no multi-paragraph explanations.
- Keep TASK_TEXT unchanged in meaning; sanitize only formatting.

## [M] FAIL CONDITIONS
FAIL.INPUT_MISSING:
- USER_MESSAGE empty OR only "го"/"go"/similar confirmation without task.
REQUIRED_FIX: Provide TASK_TEXT describing what to do.

FAIL.TASK_TOO_VAGUE:
- TASK_TEXT exists but contains no actionable verb/object (heuristic).
REQUIRED_FIX: Add target artifact/type + constraints.

FAIL.UNSUPPORTED_REQUEST:
- Request clearly violates safety constraints (module-level gate only).
REQUIRED_FIX: Reframe request into allowed scope.

## [M] DETERMINISTIC HEURISTICS (v1)
Ambiguity scoring:
- high if TASK_TEXT length < 12 chars OR lacks any of: noun/object, action verb
- med if has action but lacks artifact type or constraints
- low if has action + artifact type + at least one constraint

## [M] STEP-RUN BEHAVIOR
This module is always the first functional module after contract start.
It MUST:
- return NEXT_MODULE_KEY = COR.DOMAIN_DETECTOR on PASS
- return NEXT_PROMPT = "го" on PASS

## [M] OUTPUT TEMPLATE (CANON)
On PASS:
STATUS: PASS
REQUEST:
  TASK_TEXT: "<...>"
  MODE_HINT: <FAST|RELEASE_READY|MASTERPIECE|null>
  CONSTRAINTS: { ... }
  INTENT_SIGNALS: { has_duration: <bool>, has_platform: <bool>, has_style: <bool>, has_refs: <bool>, ambiguity_risk: <low|med|high> }
RUN_SEED:
  EXEC_MODE: STEP_RUN
  NEXT_MODULE_KEY: COR.DOMAIN_DETECTOR
  NEXT_PROMPT: "го"

On FAIL:
STATUS: FAIL
FAIL_CODE: FAIL.<...>
REQUIRED_FIX: "<one line>"
NEXT_PROMPT: "го"

## [M] GATES
PASS if:
- TASK_TEXT present and non-empty
- REQUEST envelope produced
- NEXT_MODULE_KEY set to COR.DOMAIN_DETECTOR
- Output respects ANTI_NOISE

FAIL if:
- INPUT_MISSING or TASK_TOO_VAGUE or UNSUPPORTED_REQUEST
