# RELEASE PACK READY — VAL
FILE: 03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/06__RELEASE_PACK_READY_VAL.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: VALIDATORS (VAL)
VAL_REALM: 10_MUSIC_VALIDATORS
DOC_TYPE: VALIDATOR
VAL_TYPE: RELEASE_PACK_READY
LEVEL: L3
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.VAL.MUS.RELEASE_PACK_READY.001
OWNER: SYSTEM
ROLE: Validates Release Pack completeness and policy compliance:
required variants present, platform titles present, metadata/credits present, filename-safe strings present,
and QA/VAL snapshots attached. Blocks shipping if mandatory components missing.

CHANGE_NOTE:
- DATE: 2026-01-12
- TYPE: MAJOR
- SUMMARY: "Created Release Pack Ready validator: deterministic checklist aligned to Release Variants and Credits/Metadata policies."
- REASON: "Releases fail when packs are incomplete or inconsistent; this validator prevents broken uploads."
- IMPACT: "Cleaner publishing and consistent catalog artifacts."
- CHANGE_ID: UE.CHG.2026-01-12.VAL.RELEASE_PACK_READY.001

---

## 0) PURPOSE (LAW)
Answer:
**“Is the Release Pack complete and compliant with policies?”**

This validator checks Release Pack structure against CTL:
- Release Variants
- Credits & Metadata Policy
- Naming/platform title availability (when required)

---

## 1) INPUTS (CONSUMES)
Required:
- RELEASE_PACK_REF (or embedded pack fields)
- VARIANT_MANIFEST:
  - list of variants included (labels)
  - for each: winner take id + prompt snapshot ref
- PLATFORM_TITLES_PACK_REF (or titles embedded)
- METADATA_SHEET_REF (or embedded)
- CREDITS_RIGHTS_NOTE_REF (or embedded)
- QA_VAL_SNAPSHOT_REF
- FILENAME_SAFE_STRINGS_PRESENT: YES/NO

Optional:
- PD_MODE_USED: YES/NO
- PD_ARTIFACT_REFS (if PD_MODE_USED)

---

## 2) OUTPUT (PRODUCES)
- DECISION: {PASS | WARN | FAIL}
- REASONS: short bullets
- REQUIRED_ACTION:
  - {NONE | ADD_MISSING_VARIANTS | ADD_PLATFORM_TITLES | ADD_METADATA | ADD_CREDITS | ADD_FILENAME_SAFE | FIX_PD_FIELDS}
- RETEST_NOTES: 1–2 actions max

---

## 3) RULE SOURCES (CTL) — RAW
Release Variants CTL:
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/04__RELEASE_VARIANTS_CTL.md

Credits & Metadata Policy CTL:
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/13__CREDITS_METADATA_POLICY_CTL.md

Quality gates policy:
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/09__QUALITY_GATES_CTL.md

---

## 4) CHECKLIST (DETERMINISTIC)

### CHECK A — Required variants present
- MAIN must exist always.
- If objective requires UGC-first: SHORT_CUT must exist.
- Variant labels must be from allowed set (no invented labels).

FAIL if MAIN missing.
FAIL if UGC-first required but SHORT_CUT missing.
WARN if optional variants present but incomplete.

---

### CHECK B — Each variant has required contents
For each included variant:
- winner take id present
- frozen prompt pack ref present
- duration mode label present
- QA/VAL snapshot ref (or global ref) present

FAIL if any included variant lacks winner take id or prompt ref.
WARN if minor fields missing but fixable.

---

### CHECK C — Platform titles pack present
- PLATFORM_TITLES_PACK must exist (at least streaming + YouTube titles).
FAIL if missing.

---

### CHECK D — Metadata and credits present
- Metadata sheet must include required core fields (group/track/title/uid/dates/genre/mood/language).
- Credits/rights note must exist.

FAIL if metadata missing.
FAIL if credits/rights missing.

---

### CHECK E — Filename-safe strings present
- GROUP_NAME_SAFE, TRACK_TITLE_SAFE, VARIANT_LABEL_SAFE should exist.
FAIL if missing.

---

### CHECK F — PD fields (conditional)
If PD_MODE_USED=YES:
- PD policy mode declared
- PD eligibility report ref exists
- excerpt collision report ref exists
FAIL if missing key PD refs.

---

## 5) DECISION LOGIC
PASS when:
- all required checks pass

WARN when:
- pack is complete enough but has fixable minor omissions
  (e.g., filename-safe missing for one platform title)

FAIL when:
- any mandatory component missing (variants/titles/metadata/credits)
- PD required fields missing in PD mode

---

## 6) REQUIRED ACTIONS
- ADD_MISSING_VARIANTS:
  - generate required variant via Release Pack ORC and include refs
- ADD_PLATFORM_TITLES:
  - run naming pipeline and platform titles engine
- ADD_METADATA / ADD_CREDITS:
  - populate required fields and attach refs
- ADD_FILENAME_SAFE:
  - produce sanitized strings
- FIX_PD_FIELDS:
  - attach missing PD refs or switch text mode away from PD

---

## 7) OUTPUT SCHEMA (MANDATORY)
RELEASE_PACK_READY_VAL_RESULT:
- RELEASE_UID:
- DECISION: {PASS | WARN | FAIL}
- MISSING:
  - variants:
  - titles:
  - metadata:
  - credits:
  - filename_safe:
  - pd_fields:
- REASONS: [...]
- REQUIRED_ACTION: ...
- RETEST_NOTES: [...]

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED

--- END.
