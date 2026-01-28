# PD Filter Engine — ENGINE
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/13_POET_PD_CORPUS_ENGINES/01__PD_FILTER_ENG.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
ENGINE_FAMILY: 13_POET_PD_CORPUS_ENGINES
DOC_TYPE: ENGINE
ENGINE_TYPE: POET_PD_CORPUS
LEVEL: L3
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.ENG.PD.PD_FILTER.001
OWNER: SYSTEM
ROLE: Determines whether a poem/text source is eligible for use under PD-only policy.
Outputs a PD Eligibility Report + an allowed corpus subset for downstream engines.

CHANGE_NOTE:
- DATE: 2026-01-12
- TYPE: MAJOR
- SUMMARY: "Created PD Filter engine: eligibility rules, deterministic checks, output schema, and handoffs to fit scoring."
- REASON: "PD-only lyric pipeline requires a hard gate; without it the system cannot safely use texts."
- IMPACT: "Deterministic PD eligibility + safer lyric generation."
- CHANGE_ID: UE.CHG.2026-01-12.ENG.PD.PD_FILTER.001

---

## 0) PURPOSE (LAW)
This engine answers:
**“Can we use this text source under PD-only rules?”**

It must:
- accept only sources that pass policy
- output a clear PASS/FAIL decision with reasons
- produce an “Allowed Corpus Subset” for scoring and extraction

---

## 1) INPUTS (CONSUMES)
- Candidate poem/text metadata (as provided by the pipeline):
  - author name (if known)
  - work title (if known)
  - language
  - source reference (where it comes from)
  - publication year (if known)
  - death year (if known)
  - license note (if provided)

- PD Policy Controller:
  - defines strictness, allowed jurisdictions/assumptions, and what counts as “acceptable evidence”

---

## 2) OUTPUTS (PRODUCES)
Primary:
- PD_ELIGIBILITY_REPORT (PER): PASS / FAIL / UNCERTAIN

Secondary:
- ALLOWED_CORPUS_SUBSET (ACS):
  - list of eligible works (IDs/refs)
  - notes on constraints (e.g., “only fragments”, “no full poem dumps”)

---

## 3) MINI-CONTRACT (MANDATORY)
CONSUMES: [
  "Candidate text metadata",
  "Poet PD Policy CTL"
]
PRODUCES: [
  "PD Eligibility Report (PER)",
  "Allowed Corpus Subset (ACS)"
]
DEPENDS_ON: [
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/05__POET_PD_POLICY_CTL.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/04__PD_ONLY_VAL.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/09__CREDITS_RIGHTS_VAL.md"
]
OUTPUT_TARGET: "05_PROJECTS//PD_CORPUS/ELIGIBILITY/"

---

## 4) PD SAFETY BOUNDARIES (ABSOLUTE)
- This family is PD-first.
- This engine must never “assume PD” without meeting policy rules.
- If evidence is insufficient → result is UNCERTAIN (treated as FAIL by strict policy unless CTL allows fallback).

---

## 5) ELIGIBILITY RULES (DETERMINISTIC)
Rules are applied in order.

### R1 — Explicit license statement (strongest)
If metadata includes explicit “public domain” / “PD” statement and policy accepts the source:
- PASS (note evidence)

### R2 — Author death year rule (if provided)
If author death year is known and PD policy defines a threshold:
- if (current_year - death_year) >= threshold → PASS
- else → FAIL
(Threshold and jurisdiction assumptions are defined by PD Policy CTL.)

### R3 — Publication year rule (fallback)
If publication year is known and PD policy allows:
- if (current_year - publication_year) >= threshold → PASS
- else → FAIL

### R4 — Known disallowed markers
If candidate contains markers that policy treats as risky:
- “modern translation”, “copyrighted translation”, “publisher exclusive”, “license unknown”
→ FAIL or UNCERTAIN based on policy strictness.

### R5 — Missing key fields
If neither (license) nor (death year) nor (publication year) is available:
- UNCERTAIN

---

## 6) PROCEDURE (OPERATIONAL STEPS)
1) Load PD Policy CTL (strictness + thresholds + accepted evidence sources).
2) Normalize candidate metadata fields (author/work/year/license note).
3) Run eligibility rules R1..R5.
4) Generate PD_ELIGIBILITY_REPORT (PER):
   - decision
   - evidence used
   - missing fields
   - recommended next action
5) If PASS:
   - add candidate to ALLOWED_CORPUS_SUBSET (ACS)
6) If FAIL/UNCERTAIN:
   - do NOT pass to scoring engines
   - output “how to make it PASS” (what metadata is needed)

---

## 7) OUTPUT SCHEMA (MANDATORY)

### PD_ELIGIBILITY_REPORT (PER)
- DECISION: {PASS | FAIL | UNCERTAIN}
- CANDIDATE_ID:
- AUTHOR:
- WORK_TITLE:
- LANGUAGE:
- EVIDENCE:
  - license_statement:
  - death_year:
  - publication_year:
  - source_note:
- POLICY_APPLIED:
  - threshold_type:
  - threshold_value:
  - strict_mode: YES/NO
- REASONS:
  - bullets
- MISSING_FIELDS:
  - list
- NEXT_ACTION:
  - {ALLOW_TO_SCORING | REJECT | REQUEST_METADATA}

### ALLOWED_CORPUS_SUBSET (ACS)
- LIST:
  - item: CANDIDATE_ID + short reference + constraints
- CONSTRAINTS:
  - “fragments only” / “no full poem dump” / “use mosaic” etc. (policy-driven)

---

## 8) FAILURE MODES & FIXES
1) Too many UNCERTAIN results
- Fix: enrich candidate metadata; tighten accepted sources list; add death/publication fields.

2) False positives (risky sources pass)
- Fix: increase strict_mode in PD Policy CTL; require stronger evidence category.

3) Pipeline slows down because PD checks are heavy
- Fix: cache PASS decisions per author/work; only recheck when policy changes.

---

## 9) HANDOFFS (XREF)
If PASS:
- `13_POET_PD_CORPUS_ENGINES/02__POEM_FIT_SCORING_ENG.md`

If FAIL/UNCERTAIN:
- stop lyric pipeline for this candidate
- Track Factory must switch to:
  - different PD candidate
  - or instrumental mode (if allowed by higher-level plan)

Validators:
- `50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/04__PD_ONLY_VAL.md`
- `50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/09__CREDITS_RIGHTS_VAL.md`

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED

--- END.
