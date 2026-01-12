# PD ONLY — VAL
FILE: 03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/04__PD_ONLY_VAL.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: VALIDATORS (VAL)
VAL_REALM: 10_MUSIC_VALIDATORS
DOC_TYPE: VALIDATOR
VAL_TYPE: PD_ONLY
LEVEL: L3
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.VAL.MUS.PD_ONLY.001
OWNER: SYSTEM
ROLE: Validates PD-only compliance for lyric sourcing workflow:
ensures PD policy mode is declared, eligibility evidence exists, required PD pipeline artifacts are present,
fragment limits are respected (no full poem dumps), and uncertain PD is handled per policy mode.

CHANGE_NOTE:
- DATE: 2026-01-12
- TYPE: MAJOR
- SUMMARY: "Created PD Only validator: checks PD artifacts, evidence, fragment limits, and uncertain handling aligned to Poet PD Policy."
- REASON: "PD mode must not rely on guessing; missing evidence is a hard safety risk."
- IMPACT: "Safer PD workflow and cleaner documentation."
- CHANGE_ID: UE.CHG.2026-01-12.VAL.PD_ONLY.001

---

## 0) PURPOSE (LAW)
Answer:
**“Is PD-only lyric usage compliant with PD policy and artifacts?”**

This validator checks that PD pipeline outputs exist and policy constraints are satisfied.
It does not decide legality; it enforces internal PD-policy rules.

---

## 1) INPUTS (CONSUMES)
Required when PD mode is used:
- TEXT_MODE: {PD_VERBATIM | PD_MOSAIC | ...}
- PD_POLICY_MODE: {STRICT | STANDARD | LENIENT}
- PD_PIPELINE_ARTIFACTS:
  - PD_ELIGIBILITY_REPORT_REF (PER)
  - FIT_RANKING_REF (FRANK)
  - JUICE_PACK_REF (JP)
  - MOSAIC_DRAFT_REF (MD)
  - EXCERPT_COLLISION_REPORT_REF (ECR)

- PD_ELIGIBILITY_STATUS: {PASS | FAIL | UNCERTAIN}
- EVIDENCE_CATEGORY: {E1..E5} (as defined by CTL)

Recommended:
- FRAGMENT_USAGE_STATS:
  - max_lines_per_fragment
  - max_chars_per_fragment
  - total_fragments_used
  - total_chars_used

If PD mode is NOT used:
- validator returns PASS (not applicable) unless invoked incorrectly.

---

## 2) OUTPUT (PRODUCES)
- DECISION: {PASS | WARN | FAIL}
- REASONS: (short bullets)
- REQUIRED_ACTION:
  - {NONE | PROVIDE_EVIDENCE | REMOVE_PD_MODE | REDUCE_FRAGMENT_SIZE | REPLACE_UNCERTAIN_SOURCE | RERUN_PD_PIPELINE}
- RETEST_NOTES: 1–2 knobs max

---

## 3) RULE SOURCE (CTL) — RAW
Poet PD Policy CTL:
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/05__POET_PD_POLICY_CTL.md

Credits & Metadata Policy CTL (TEXT_MODE declaration):
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/13__CREDITS_METADATA_POLICY_CTL.md

Quality gates policy:
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/09__QUALITY_GATES_CTL.md

---

## 4) CHECKS (DETERMINISTIC)

### CHECK A — PD mode declared correctly
If TEXT_MODE indicates PD usage:
- PD_POLICY_MODE must be present.
FAIL if missing.

---

### CHECK B — Required PD artifacts exist
All PD pipeline artifact refs must be present:
- PER, FRANK, JP, MD, ECR
FAIL if any missing.

---

### CHECK C — Eligibility status handling
Rules (aligned to CTL):
- If PD_ELIGIBILITY_STATUS=FAIL → FAIL
- If PD_ELIGIBILITY_STATUS=UNCERTAIN:
  - STRICT → FAIL
  - STANDARD → FAIL unless trusted pool membership is declared in evidence
  - LENIENT → WARN only if rationale recorded (rationale field may exist in PER)

---

### CHECK D — Fragment size limits (no dumps)
If fragment stats provided:
- must not exceed CTL caps:
  - MAX_LINES_PER_FRAGMENT
  - MAX_CHARS_PER_FRAGMENT
  - MAX_FRAGMENTS_PER_JUICE_PACK
  - MAX_TOTAL_FRAGMENT_TEXT_CHARS_PER_PACK
FAIL if clearly violated.
WARN if near limits and should be reduced.

If stats are missing:
- WARN (insufficient instrumentation) in PD runs.

---

### CHECK E — Excerpt collision check exists
ECR must exist and not be BLOCK:
- BLOCK → FAIL
- WARN → WARN (requires substitutions and rerun mosaic step)

---

## 5) DECISION LOGIC
PASS when:
- PD mode declared + artifacts exist
- eligibility PASS (or allowed per mode)
- fragment limits respected (or no evidence of violation)
- ECR PASS

WARN when:
- ECR WARN (needs substitution)
- fragment limits near caps
- missing fragment stats but artifacts exist

FAIL when:
- missing PD policy mode
- missing required artifacts
- eligibility FAIL
- eligibility UNCERTAIN in STRICT (or not allowed)
- fragment limits violated (dump risk)
- ECR BLOCK

---

## 6) REQUIRED ACTION KNOBS
Choose 1–2 max.

- PROVIDE_EVIDENCE:
  - add eligibility evidence category and source ref in PER
- REMOVE_PD_MODE:
  - switch TEXT_MODE to ORIGINAL/ADAPTATION/INSPIRED
- REDUCE_FRAGMENT_SIZE:
  - shorten fragments / reduce total chars
- REPLACE_UNCERTAIN_SOURCE:
  - pick a different PD candidate with PASS evidence
- RERUN_PD_PIPELINE:
  - rerun from PD Filter or from Mosaic step after substitutions

---

## 7) OUTPUT SCHEMA (MANDATORY)
PD_ONLY_VAL_RESULT:
- TRACK_UID:
- TEXT_MODE:
- PD_POLICY_MODE:
- PD_ELIGIBILITY_STATUS:
- EVIDENCE_CATEGORY:
- ARTIFACT_REFS_PRESENT: YES/NO
- FRAGMENT_USAGE_STATS: (optional)
- ECR_STATUS: {PASS | WARN | BLOCK}
- DECISION: {PASS | WARN | FAIL}
- REASONS: [...]
- REQUIRED_ACTION: ...
- RETEST_NOTES: [...]

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED

--- END.
