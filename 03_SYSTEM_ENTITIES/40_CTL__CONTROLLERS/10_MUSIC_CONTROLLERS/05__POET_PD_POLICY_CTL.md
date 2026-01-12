# POET PD POLICY — CTL
FILE: 03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/05__POET_PD_POLICY_CTL.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: CONTROLLERS (CTL)
CTL_REALM: 10_MUSIC_CONTROLLERS
DOC_TYPE: CONTROLLER
CTL_TYPE: POET_PD_POLICY
LEVEL: L3
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.CTL.MUS.POET_PD_POLICY.001
OWNER: SYSTEM
ROLE: Defines PD-only policy constraints for lyric sourcing and usage:
eligibility evidence categories, strictness modes, fragment-size limits, “no full poem dump” rule,
translation constraints, and required output artifacts for the PD pipeline.

CHANGE_NOTE:
- DATE: 2026-01-12
- TYPE: MAJOR
- SUMMARY: "Created Poet PD Policy CTL: strictness modes, eligibility evidence, fragment limits, and prohibitions for PD-only lyrics."
- REASON: "PD pipeline must be deterministic and safe; eligibility must not be guessed."
- IMPACT: "Safer PD workflow + cleaner mosaics + reduced overuse."
- CHANGE_ID: UE.CHG.2026-01-12.CTL.POET.PD_POLICY.001

---

## 0) PURPOSE (LAW)
This controller defines the **PD-only law** for lyrics:
- what counts as PD-eligible (evidence)
- what to do when evidence is missing (UNCERTAIN handling)
- how much text may be used as fragments
- what is prohibited (full poem dumps, risky translations)
- what artifacts must be produced by the PD pipeline

CTL is the law source; engines/orchestrators must implement it.

---

## 1) POLICY MODES (STRICTNESS)
One of the following modes must be selected for a run:

- MODE.STRICT (default)
- MODE.STANDARD
- MODE.LENIENT (only if explicitly allowed by governance)

### MODE.STRICT (default)
- UNCERTAIN = FAIL (do not use)
- requires strong evidence category (see Section 2)

### MODE.STANDARD
- UNCERTAIN may be allowed only if a trusted PD pool is used (pre-approved corpus)
- still forbids copyrighted text

### MODE.LENIENT
- allows broader inference, but must be explicitly approved
- still must not request copyrighted text in prompts

---

## 2) ELIGIBILITY EVIDENCE CATEGORIES
PD Filter engine must classify evidence:

E1 — EXPLICIT PD STATEMENT (strong)
- explicit “public domain” statement from an accepted source

E2 — AUTHOR DEATH YEAR RULE (strong, if known)
- author death year provided and meets threshold

E3 — PUBLICATION YEAR RULE (fallback)
- publication year provided and meets threshold

E4 — TRUSTED PD POOL MEMBERSHIP (strong if pool is approved)
- candidate belongs to a pre-approved PD corpus set

E5 — UNKNOWN / INSUFFICIENT
- missing key fields; evidence not acceptable

---

## 3) THRESHOLDS (PARAMETERS)
This CTL defines policy parameters used by PD Filter.

### Default thresholds (placeholders; adjustable by governance)
- DEATH_YEAR_THRESHOLD_YEARS: 70
- PUBLICATION_YEAR_THRESHOLD_YEARS: 95

Notes:
- These thresholds are applied as policy parameters, not legal advice.
- If governance later defines different thresholds, update this CTL version.

---

## 4) UNCERTAIN HANDLING (MANDATORY)
If PD Filter output is UNCERTAIN:
- MODE.STRICT: treat as FAIL, stop candidate
- MODE.STANDARD: allow only if E4 trusted pool membership exists
- MODE.LENIENT: allow only with recorded rationale and increased collision/rights checks

---

## 5) FRAGMENT SIZE LIMITS (NO DUMPS)
This policy enforces fragments-only usage.

### Fragment length caps (default)
- MAX_LINES_PER_FRAGMENT: 2
- MAX_CHARS_PER_FRAGMENT: 200

### Pack caps
- MAX_FRAGMENTS_PER_JUICE_PACK: 20
- MAX_TOTAL_FRAGMENT_TEXT_CHARS_PER_PACK: 2000

Hard rule:
- No full poem output.
- No contiguous long stanza copying.

---

## 6) TRANSLATION & MODERN ADAPTATION RULES (RISK)
- Avoid “modern translations” unless explicitly PD and allowed by evidence.
- If translation status is unknown: treat as risk → FAIL in STRICT mode.
- Prefer original-language PD texts when possible, then minimal adaptation in mosaic.

---

## 7) REQUIRED PD PIPELINE ARTIFACTS
If PD mode is used, the pipeline MUST produce:
- PD_ELIGIBILITY_REPORT (PASS/FAIL/UNCERTAIN + evidence)
- FIT_RANKING (top candidates + rationale)
- JUICE_PACK (ranked fragments + tags + cadence)
- MOSAIC_DRAFT (section-labeled, paste-ready)
- EXCERPT_COLLISION_REPORT (PASS/WARN/BLOCK + blocklist/penalties)

---

## 8) PROHIBITED REQUESTS (HARD BLOCKERS)
PD mode must NOT:
- request or include copyrighted poems/lyrics
- paste full poems as output
- rely on “guessing” PD status without evidence
- reuse the same famous lines repeatedly (collision guard must run)

---

## 9) DEPENDENCY REFERENCES (RAW)
Implemented by:
- PD Filter ENG  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/13_POET_PD_CORPUS_ENGINES/01__PD_FILTER_ENG.md
- Poem Fit Scoring ENG  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/13_POET_PD_CORPUS_ENGINES/02__POEM_FIT_SCORING_ENG.md
- Juice Extractor ENG  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/13_POET_PD_CORPUS_ENGINES/03__JUICE_EXTRACTOR_ENG.md
- Mosaic Composer ENG  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/13_POET_PD_CORPUS_ENGINES/04__MOSAIC_COMPOSER_ENG.md
- Excerpt Collision Guard ENG  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/13_POET_PD_CORPUS_ENGINES/05__EXCERPT_COLLISION_ENG.md

Orchestrated by:
- Poet Pack ORC  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/06__POET_PACK_ORC.md

Validator alignment:
- PD Only VAL  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/04__PD_ONLY_VAL.md
- Credits/Rights VAL  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/09__CREDITS_RIGHTS_VAL.md

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED

--- END.
