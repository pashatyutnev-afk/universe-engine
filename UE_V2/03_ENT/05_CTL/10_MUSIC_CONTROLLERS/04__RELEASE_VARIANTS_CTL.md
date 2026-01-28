# RELEASE VARIANTS — CTL
FILE: 03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/04__RELEASE_VARIANTS_CTL.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: CONTROLLERS (CTL)
CTL_REALM: 10_MUSIC_CONTROLLERS
DOC_TYPE: CONTROLLER
CTL_TYPE: RELEASE_VARIANTS
LEVEL: L3
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.CTL.MUS.RELEASE_VARIANTS.001
OWNER: SYSTEM
ROLE: Defines which release variants are allowed/required per track type and objective (UGC-first vs album-first),
including minimum required pack contents, naming of variants, and prohibitions against variant bloat.
Used by Release Pack ORC/ENG and QA/VAL readiness.

CHANGE_NOTE:
- DATE: 2026-01-12
- TYPE: MAJOR
- SUMMARY: "Created Release Variants CTL: required/optional variants, pack contents, and anti-bloat rules."
- REASON: "Without variant policy, packaging becomes inconsistent and wastes production time."
- IMPACT: "Consistent releases + faster publishing + better UGC coverage."
- CHANGE_ID: UE.CHG.2026-01-12.CTL.RELEASE.VARIANTS.001

---

## 0) PURPOSE (LAW)
This controller defines:
- which variants a release pack must include
- when variants are required
- how variants are named
- limits to prevent variant bloat

---

## 1) VARIANT TYPES (STANDARD)
- MAIN: default canonical version
- SHORT_CUT: UGC-first condensed version (or “short edit”)
- ALT_INTRO: repair variant to fix late hook / weak recognition
- INSTRUMENTAL: optional, if vocals are not essential or for creator use
- EXTENDED: optional, if full-form benefits the track (album-first)

---

## 2) REQUIRED VARIANTS (MINIMUM PACK)
A Release Pack must include at least:

### Rule V1 — MAIN is mandatory
- Always include MAIN.

### Rule V2 — SHORT_CUT is mandatory when objective is UGC-first
- If track objective is UGC-first or platform requires short-form:
  - include SHORT_CUT.

### Rule V3 — ALT_INTRO is optional (repair only)
- Include only if MAIN or SHORT_CUT failed:
  - Hook Timing
  - Recognition QA
  - Scroll Stop QA

---

## 3) OPTIONAL VARIANTS (CONTROLLED)
Optional variants must have a reason.

### INSTRUMENTAL
Allowed if:
- track is intended for creators or overlays
- vocals are not the core identity anchor

### EXTENDED
Allowed if:
- album-first objective
- extended arrangement adds value (not just longer)

Hard rule:
- Optional variants must not exceed 2 additional variants unless approved by showrunner.

---

## 4) PACK CONTENTS (MANDATORY PER VARIANT)
For each included variant, Release Pack must include:
- audio/take pointer (winner id)
- prompt pack snapshot (what produced it)
- duration mode label (SHORT/FULL/ALT_INTRO)
- UGC notes (if SHORT_CUT)
- QA/VAL snapshot reference (pass record)

---

## 5) NAMING RULES (VARIANT LABELS)
Variant labels must be consistent:
- MAIN
- SHORT_CUT
- ALT_INTRO
- INSTRUMENTAL
- EXTENDED

Do not invent new labels unless a new CTL version explicitly adds them.

---

## 6) ANTI-BLOAT PROHIBITIONS (HARD)
A Release Pack must NOT:
- include many micro-variants with minimal difference
- include variants without a documented reason
- include >3 total variants by default (MAIN + SHORT_CUT + 1 optional)

---

## 7) PASS/FAIL EXPECTATIONS (FOR READINESS)
PASS when:
- required variants present (MAIN always; SHORT_CUT when UGC-first)
- each variant has complete contents
- variant count within policy

WARN when:
- one optional variant missing required contents (fixable)
- variant count at upper limit but justified

FAIL when:
- MAIN missing
- UGC-first but SHORT_CUT missing
- variant bloat (too many unreasoned variants)

---

## 8) REFERENCES (RAW)
Used by:
- Release Pack ORC  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/04__RELEASE_PACK_ORC.md
- Release Pack ENG  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/11_MUSIC_FACTORY_ENGINES/06__RELEASE_PACK_ENG.md

Validator alignment:
- Release Pack Ready VAL  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/06__RELEASE_PACK_READY_VAL.md

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED

--- END.
