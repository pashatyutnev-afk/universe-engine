# NAMING COLLISION — VAL
FILE: 03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/07__NAMING_COLLISION_VAL.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: VALIDATORS (VAL)
VAL_REALM: 10_MUSIC_VALIDATORS
DOC_TYPE: VALIDATOR
VAL_TYPE: NAMING_COLLISION
LEVEL: L3
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.VAL.MUS.NAMING_COLLISION.001
OWNER: SYSTEM
ROLE: Validates Naming Collision Report outputs:
ensures collision checks were performed, scope mode is declared, decisions are justified,
and approved shortlist + safe fallbacks exist before platform titles and release packaging.

CHANGE_NOTE:
- DATE: 2026-01-12
- TYPE: MAJOR
- SUMMARY: "Created Naming Collision validator: checks completeness and coherence of Naming Collision Report and required outputs."
- REASON: "Naming collisions break catalog clarity and can cause platform confusion."
- IMPACT: "Cleaner titles, safer platform packaging, consistent naming pipeline."
- CHANGE_ID: UE.CHG.2026-01-12.VAL.NAMING_COLLISION.001

---

## 0) PURPOSE (LAW)
Answer:
**“Is the naming collision check complete and safe to proceed?”**

This validator checks the presence and completeness of the Naming Collision Report (NCR).

---

## 1) INPUTS (CONSUMES)
Required:
- NAMING_COLLISION_REPORT (NCR):
  - SCOPE_MODE
  - TOTAL_CANDIDATES
  - APPROVED_COUNT
  - WARN_COUNT
  - BLOCKED_COUNT
  - DECISION: {PASS | WARN | BLOCK}
  - APPROVED_SHORTLIST
  - BLOCKED_LIST (with reasons)
  - SAFE_FALLBACKS
  - NEXT_ACTION

Optional:
- references to catalog memory snapshot used

---

## 2) OUTPUT (PRODUCES)
- DECISION: {PASS | WARN | FAIL}
- REASONS: (short bullets)
- REQUIRED_ACTION:
  - {NONE | RECHECK_SCOPE | ADD_FALLBACKS | REGENERATE_NAMES | APPLY_FIXES}
- RETEST_NOTES: 1–2 actions max

---

## 3) RULE SOURCES (RAW)
Naming Collision ENG (what NCR should contain):
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/14_NAMING_IDENTITY_ENGINES/03__NAMING_COLLISION_ENG.md

Catalog Memory CTL (scope usage):
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/07__CATALOG_MEMORY_CTL.md

Quality gates policy:
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/09__QUALITY_GATES_CTL.md

---

## 4) CHECKS (DETERMINISTIC)

### CHECK A — NCR presence and required fields
FAIL if NCR missing OR required fields missing:
- scope mode
- decision
- approved shortlist
- safe fallbacks

---

### CHECK B — Approved shortlist must be non-empty for PASS
- If NCR decision is PASS:
  - APPROVED_SHORTLIST must exist and have at least 1 item.
FAIL if empty.

---

### CHECK C — Safe fallbacks must exist
- SAFE_FALLBACKS must include 1–5 items.
WARN if empty but shortlist exists (fixable).
FAIL if both shortlist and fallbacks empty.

---

### CHECK D — Blocked list reasons
- BLOCKED_LIST entries must include at least one reason:
  - exact match / normalized match / near duplicate / series conflict
WARN if reasons missing (fixable).
FAIL if BLOCKED_LIST present but completely unreasoned.

---

### CHECK E — Decision coherence
- counts should add up: APPROVED + WARN + BLOCKED ≈ TOTAL
WARN if mismatch small (instrumentation issue).
FAIL if mismatch large / nonsensical.

---

## 5) DECISION LOGIC
PASS when:
- NCR complete
- approved shortlist exists
- safe fallbacks exist
- decision is PASS or WARN (WARN allowed by ORC depending on stage)

WARN when:
- NCR mostly complete but missing minor components (fallbacks or reason details)

FAIL when:
- NCR missing critical fields
- no approved shortlist for PASS
- no fallbacks and no shortlist
- decision incoherent

---

## 6) REQUIRED ACTIONS
- RECHECK_SCOPE:
  - rerun collision check with correct scope (group/global)
- ADD_FALLBACKS:
  - create 1–5 safe fallback titles
- REGENERATE_NAMES:
  - rerun Naming Generation and collision check
- APPLY_FIXES:
  - fix borderline names and rerun collision check

---

## 7) OUTPUT SCHEMA (MANDATORY)
NAMING_COLLISION_VAL_RESULT:
- TARGET_UID:
- SCOPE_MODE:
- NCR_DECISION: {PASS | WARN | BLOCK}
- DECISION: {PASS | WARN | FAIL}
- MISSING_FIELDS: (list)
- REASONS: [...]
- REQUIRED_ACTION: ...
- RETEST_NOTES: [...]

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED

--- END.
