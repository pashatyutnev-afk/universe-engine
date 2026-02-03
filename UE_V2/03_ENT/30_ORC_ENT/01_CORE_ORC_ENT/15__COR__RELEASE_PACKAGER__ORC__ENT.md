FILE: UE_V2/03_ENT/30_ORC_ENT/01_CORE_ORC_ENT/15__COR__RELEASE_PACKAGER__ORC__ENT.md
SCOPE: UE_V2 / 03_ENT / 30_ORC_ENT / 01_CORE_ORC_ENT
DOC_TYPE: ORC_ENTITY_MODULE
DOMAIN: COR_ORC_ENT
KEY: COR.RELEASE_PACKAGER
UID: UE.V2.ENT.ORC.COR.RELEASE_PACKAGER.001
VERSION: 1.0.0
STATUS: ACTIVE
MODE: REPO (USAGE-ONLY, NO-EDIT)
CREATED: 2026-02-02
UPDATED: 2026-02-02
OWNER: ORC_ENT
NAV_RULE: RAW-only enforcement (KEY->IDX->RAW)

---

## [M] ROLE
Release/output packager for UE_V2 step-runs.
Converts internal run results into a deterministic OUTPUT_PACK with strict structure, minimal noise, and stable formatting across modes.

---

## [M] PURPOSE
- Produce a single, copy-ready deliverable bundle (OUTPUT_PACK) per step-run.
- Enforce stable formatting so downstream can diff, archive, and re-run deterministically.
- Keep user-facing output focused on content/results, not system internals.
- Support modes: FAST | RELEASE_READY | MASTERPIECE (format stays stable, only depth changes).

---

## [M] HARD_RULES
- OUTPUT-FIRST: user sees deliverables, not internal mechanics.
- Keys-only in user-facing content:
  - Never print RAW URLs or PATH values inside OUTPUT_PACK.
  - Allowed: KEY names, UID, VERSION, STATUS, simple labels.
- Deterministic ordering:
  1) MODE
  2) RESOURCES USED
  3) DELIVERABLES
  4) GATES
  5) NEXT PROMPT
- No mass lists:
  - RESOURCES USED max 8 lines unless explicitly required by REQUIRED_CHECKS.
- No duplication:
  - Do not repeat the same statement in multiple sections.
- No speculation:
  - If an output is missing, mark it as missing and route via FAIL_HANDLER semantics (do not invent).
- Do not alter ROUTE_TOKEN:
  - Include it as-is (or reference it by stable fields), do not “improve” it.
- Do not embed long templates:
  - OUTPUT_PACK is not a doc dump; it is a packaging layer.

---

## [M] INPUTS
- ROUTE_TOKEN (required)
  - DOMAIN
  - ARTIFACT_TYPE
  - MODE
  - PIPE_SELECTED
  - DEFAULT_ORC
  - REQUIRED_IDX
  - REQUIRED_CHECKS
  - EXEC_MODE
- RUN_STATE (required)
  - STEP
  - STATUS: PASS|WARN|GAP|STOP
  - OPENED_KEYS (optional)
  - DECISIONS (optional)
- DELIVERABLES_RAW (optional)
  - DELIVERABLE_ITEMS: list of {TITLE, BODY, META(optional)}
- CHECK_REPORT (optional)
  - PASSED: [<CHECK_ID>...]
  - FAILED: [<CHECK_ID>...]
  - WARN:   [<CHECK_ID>...]
- FAIL_RESPONSE (optional)
  - From COR.FAIL_HANDLER if run is STOP/GAP or warnings need normalization.

---

## [M] OUTPUTS
OUTPUT_PACK (canonical format):
- MODE
- RESOURCES USED
- DELIVERABLES
- GATES
- NEXT_PROMPT

All outputs are plain text blocks with stable headings.

---

## [M] OUTPUT_PACK CANON (strict)

### 1) MODE
Must be exactly:
MODE: REPO (USAGE-ONLY, NO-EDIT)

Optional line (only if MODE_HINT present in ROUTE_TOKEN.MODE):
MODE_HINT: FAST|RELEASE_READY|MASTERPIECE

### 2) RESOURCES USED
List minimal opened keys and confirmed markers, keys-only:
RESOURCES USED:
- USING RAW: [KEY...]                 # keys only (no urls)
- MARKERS CONFIRMED: [MUST_LOAD...]   # marker names only
- IDX USED: [<REQUIRED_IDX_KEY>]      # key only
- PIPE: [<PIPE_SELECTED_KEY>]         # key only

Rules:
- If OPENED_KEYS exist, prefer them for USING RAW list.
- If none exist, include only REQUIRED_IDX and PIPE key if present.
- Max 8 entries in USING RAW.

### 3) DELIVERABLES
DELIVERABLES:
- <DELIVERABLE_TITLE_1>
  <BODY>
- <DELIVERABLE_TITLE_2>
  <BODY>

Rules:
- Titles must be short and scannable.
- BODY must be the actual useful output (content).
- If STATUS is STOP or GAP:
  - DELIVERABLES must include only FAIL_RESPONSE.user_message content (one item)
  - Do not include partial content blocks.

### 4) GATES
GATES:
- STATUS: PASS|WARN|GAP|STOP
- PASSED: [..]     # optional
- WARN:   [..]     # optional
- FAILED: [..]     # optional
- NOTES: "<one line>"  # optional

Rules:
- If FAIL_RESPONSE exists, STATUS must equal FAIL_RESPONSE.STATUS.
- Keep lists short; if more than 8 checks, show first 8 + “...”.

### 5) NEXT_PROMPT
Must always be:
NEXT_PROMPT: го

---

## [M] MODE DEPTH RULES (content shaping)
- FAST:
  - Deliverables are minimal and actionable.
  - No “context paragraphs”.
- RELEASE_READY:
  - Deliverables include final wording, structure, and ready-to-copy blocks.
  - Minimal rationale allowed only if it changes user actions.
- MASTERPIECE:
  - Deliverables can include variants (max 3) IF requested by task or required by checks.
  - Still avoid noise; never dump system docs.

---

## [M] PACKAGING ALGORITHM (deterministic)
P0) Resolve effective status:
- If FAIL_RESPONSE exists -> STATUS = FAIL_RESPONSE.STATUS
- Else STATUS = RUN_STATE.STATUS

P1) Build RESOURCES USED:
- USING RAW:
  - stable order: MUST_LOAD keys (if present) -> REQUIRED_IDX -> PIPE -> OPENED_KEYS extras
- MARKERS CONFIRMED:
  - from RUN_STATE or CHECK_REPORT (if provided)
- IDX USED:
  - ROUTE_TOKEN.REQUIRED_IDX if present
- PIPE:
  - ROUTE_TOKEN.PIPE_SELECTED if present

P2) Build DELIVERABLES:
- If STATUS in [STOP, GAP]:
  - Single item: "NEXT ACTION" with FAIL_RESPONSE.NEXT_ACTION.USER_MESSAGE
- Else:
  - Use DELIVERABLES_RAW.DELIVERABLE_ITEMS in order provided
  - If none provided, add single item:
    - "NO_DELIVERABLES" with "Нет готовых deliverables для упаковки. Жми го для следующего шага."

P3) Build GATES:
- STATUS set
- PASSED/WARN/FAILED from CHECK_REPORT if present
- NOTES:
  - PASS: "ok"
  - WARN: "non-blocking"
  - GAP: "dependency missing"
  - STOP: "blocked"

P4) Emit OUTPUT_PACK in canonical order.

---

## [M] NOISE CONTROLS
- Never include:
  - raw links
  - path lists
  - internal heuristics
  - long explanations
- Never exceed:
  - 1 screen of RESOURCES USED
  - 1–3 screens of DELIVERABLES (unless MASTERPIECE requires variants)

---

## [M] GATES
PASS if:
- OUTPUT_PACK emitted with canonical section order
- Keys-only compliance satisfied (no RAW/PATH)
- NEXT_PROMPT equals "го"
- STATUS consistent with FAIL_RESPONSE when present

FAIL if:
- RAW/PATH leaks into user-facing output
- Non-deterministic ordering
- Missing NEXT_PROMPT
- Packs partial deliverables during STOP/GAP
