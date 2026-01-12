# CREDITS & RIGHTS — VAL
FILE: 03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/09__CREDITS_RIGHTS_VAL.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: VALIDATORS (VAL)
VAL_REALM: 10_MUSIC_VALIDATORS
DOC_TYPE: VALIDATOR
VAL_TYPE: CREDITS_RIGHTS
LEVEL: L3
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.VAL.MUS.CREDITS_RIGHTS.001
OWNER: SYSTEM
ROLE: Validates presence and coherence of required credits/metadata fields and text-mode attribution:
ensures TEXT_MODE is declared, PD fields are present when PD used, and release docs do not contain prohibited full-text dumps.
Aligned to Credits & Metadata Policy CTL and Poet PD Policy.

CHANGE_NOTE:
- DATE: 2026-01-12
- TYPE: MAJOR
- SUMMARY: "Created Credits & Rights validator: required fields checks, PD attribution checks, and no-dump enforcement."
- REASON: "Release packaging fails when metadata/credits are missing or PD mode lacks attribution and evidence."
- IMPACT: "Consistent catalog docs and safer attribution handling."
- CHANGE_ID: UE.CHG.2026-01-12.VAL.CREDITS.RIGHTS.001

---

## 0) PURPOSE (LAW)
Answer:
**“Are credits/metadata and text-mode attribution complete and coherent?”**

This validator enforces internal policy requirements for documentation and release packaging.
It does not provide legal conclusions.

---

## 1) INPUTS (CONSUMES)
Required:
- METADATA_FIELDS (core set):
  - GROUP_NAME, TRACK_TITLE, TRACK_UID
  - LANGUAGE_PRIMARY
  - GENRE_STACK, MOOD_STACK
  - DURATION_MODE, UGC_MODE
  - WINNER_TAKE_ID
  - PROMPT_PACK_FROZEN_REF
- CREDITS_FIELDS (core set):
  - MUSIC_CREDIT / SYSTEM marker
  - MIX_CREDIT / MASTER_CREDIT (role/system)
  - VOCAL credits if lyrical
- TEXT_MODE: {ORIGINAL | PD_VERBATIM | PD_MOSAIC | ADAPTATION | INSPIRED}
Optional:
- PD_FIELDS (required if TEXT_MODE indicates PD use):
  - PD_POLICY_MODE
  - PD_ELIGIBILITY_REPORT_REF
  - EXCERPT_COLLISION_REPORT_REF
  - AUTHOR/WORK/SOURCE_REF/ATTRIBUTION_LINE (if tracked)

Recommended:
- CONTENT_SAFETY_NOTE: "no full poem dump" compliance statement (optional)

---

## 2) OUTPUT (PRODUCES)
- DECISION: {PASS | WARN | FAIL}
- REASONS: (short bullets)
- REQUIRED_ACTION:
  - {NONE | ADD_METADATA_FIELDS | ADD_CREDITS_FIELDS | FIX_TEXT_MODE | ADD_PD_ATTRIBUTION | REMOVE_DUMPED_TEXT}
- RETEST_NOTES: 1–2 actions max

---

## 3) RULE SOURCES (CTL) — RAW
Credits & Metadata Policy CTL:
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/13__CREDITS_METADATA_POLICY_CTL.md

Poet PD Policy CTL:
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/05__POET_PD_POLICY_CTL.md

Quality gates policy:
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/09__QUALITY_GATES_CTL.md

---

## 4) CHECKS (DETERMINISTIC)

### CHECK A — Core metadata present
FAIL if any of these are missing:
- GROUP_NAME
- TRACK_TITLE
- TRACK_UID
- LANGUAGE_PRIMARY
- GENRE_STACK
- MOOD_STACK
- WINNER_TAKE_ID
- PROMPT_PACK_FROZEN_REF

WARN if optional but useful fields missing (dates, platform targets).

---

### CHECK B — Core credits present
FAIL if:
- no music/system credit marker exists
- mix/master credit markers missing (role or system)
WARN if:
- secondary roles missing (producer/prompt architect etc.)

---

### CHECK C — TEXT_MODE declared
FAIL if TEXT_MODE missing.

---

### CHECK D — PD attribution completeness (conditional)
If TEXT_MODE in {PD_VERBATIM, PD_MOSAIC}:
FAIL if any missing:
- PD_POLICY_MODE
- PD_ELIGIBILITY_REPORT_REF
- EXCERPT_COLLISION_REPORT_REF
WARN if missing:
- AUTHOR/WORK/ATTRIBUTION_LINE (depending on whether project tracks them)

If TEXT_MODE is ORIGINAL:
- PD fields should not be required.

---

### CHECK E — No full-text dumps (hard)
FAIL if documentation contains:
- full poem dumps or long contiguous source text (policy violation)
WARN if:
- text length seems excessive and should be reduced to fragments/structured lyrics.

(Detection method is operational; this validator enforces the rule conceptually.)

---

## 5) DECISION LOGIC
PASS when:
- core metadata and credits present
- TEXT_MODE present and coherent
- if PD mode used: required PD refs present
- no dump violations

WARN when:
- minor optional fields missing
- PD attribution partially missing but fixable

FAIL when:
- any core metadata missing
- TEXT_MODE missing
- PD required fields missing in PD mode
- full-text dump detected

---

## 6) REQUIRED ACTIONS
- ADD_METADATA_FIELDS: populate missing required metadata fields
- ADD_CREDITS_FIELDS: add required credit markers/roles
- FIX_TEXT_MODE: set correct mode and align fields
- ADD_PD_ATTRIBUTION: attach PD refs and attribution line
- REMOVE_DUMPED_TEXT: reduce to fragments/structured lyrics and re-run PD checks

---

## 7) OUTPUT SCHEMA (MANDATORY)
CREDITS_RIGHTS_VAL_RESULT:
- TRACK_UID:
- TEXT_MODE:
- MISSING_METADATA_FIELDS: [...]
- MISSING_CREDITS_FIELDS: [...]
- PD_FIELDS_STATUS: {NA | OK | MISSING}
- DUMP_VIOLATION: {NO | SUSPECTED | YES}
- DECISION: {PASS | WARN | FAIL}
- REASONS: [...]
- REQUIRED_ACTION: ...
- RETEST_NOTES: [...]

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED

--- END.
