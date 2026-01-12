# COLLISION BLOCKER — VAL
FILE: 03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/05__COLLISION_BLOCKER_VAL.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: VALIDATORS (VAL)
VAL_REALM: 10_MUSIC_VALIDATORS
DOC_TYPE: VALIDATOR
VAL_TYPE: COLLISION_BLOCKER
LEVEL: L3
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.VAL.MUS.COLLISION_BLOCKER.001
OWNER: SYSTEM
ROLE: Validates catalog collision risk for a candidate track/variant using fingerprint similarity severity
(allow/penalize/warn/block) defined by Fingerprint Collision Thresholds CTL.
Enforces required novelty actions on WARN and blocks documentation/release on BLOCK.

CHANGE_NOTE:
- DATE: 2026-01-12
- TYPE: MAJOR
- SUMMARY: "Created Collision Blocker validator: severity-based decisions aligned to fingerprint collision thresholds and required novelty actions."
- REASON: "Main failure mode: near-duplicate tracks across catalog (same vocals/hooks/palette)."
- IMPACT: "Higher differentiation, safer scaling, cleaner catalog identity."
- CHANGE_ID: UE.CHG.2026-01-12.VAL.COLLISION_BLOCKER.001

---

## 0) PURPOSE (LAW)
Answer:
**“Is this output too similar to an existing catalog item in the selected scope?”**

This validator does not compute similarity by itself; it validates that:
- collision severity is within allowed range
- required actions are taken when severity is PENALIZE/WARN
- BLOCK stops the pipeline

---

## 1) INPUTS (CONSUMES)
Required:
- SCOPE_MODE: {GROUP | ALBUM | GLOBAL}
- SIMILARITY_SCORE_0_1
- SEVERITY: {ALLOW | PENALIZE | WARN | BLOCK}
- NEAREST_NEIGHBOR_REF:
  - id/token (not full content)
- NOVELTY_ACTIONS_TAKEN (optional):
  - list of knobs changed since last run
- ARTIFACT_CONTEXT:
  - TRACK_UID / VARIANT_LABEL

Where severity should come from:
- Catalog Collision ENG output or collision report notes.

---

## 2) OUTPUT (PRODUCES)
- DECISION: {PASS | WARN | FAIL}
- REASONS: (short bullets)
- REQUIRED_ACTION:
  - {NONE | APPLY_NOVELTY_KNOBS | REDESIGN_HOOK_OR_VOICE | CHANGE_PALETTE | CHANGE_GROOVE | CHANGE_HOOK_GRAMMAR}
- RETEST_NOTES: 1–2 knobs max

---

## 3) RULE SOURCE (CTL) — RAW
Fingerprint Collision Thresholds CTL:
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/06__FINGERPRINT_COLLISION_THRESHOLDS_CTL.md

Catalog Memory CTL (scope and tokens):
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/07__CATALOG_MEMORY_CTL.md

Quality gates policy:
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/09__QUALITY_GATES_CTL.md

---

## 4) CHECKS (DETERMINISTIC)

### CHECK A — Severity mapping valid
- SEVERITY must match the thresholds policy for the given scope.
If inconsistent:
- WARN if slightly inconsistent (instrumentation missing)
- FAIL if clearly inconsistent / missing core fields

(Validator assumes upstream computed severity correctly; it checks presence and coherence.)

---

### CHECK B — Enforce actions by severity
- ALLOW → PASS
- PENALIZE → WARN unless at least 1 novelty knob is recorded as applied (then PASS with note)
- WARN → WARN unless at least 2 novelty knobs are recorded, and one is from {vocal identity OR hook grammar} (then PASS)
- BLOCK → FAIL (hard stop)

---

### CHECK C — Nearest neighbor reference required
- NEAREST_NEIGHBOR_REF must exist for PENALIZE/WARN/BLOCK.
FAIL if missing (cannot justify the collision decision).

---

## 5) DECISION LOGIC
PASS when:
- SEVERITY=ALLOW
OR
- SEVERITY=PENALIZE and 1 novelty knob applied
OR
- SEVERITY=WARN and 2 knobs applied with required knob type present

WARN when:
- SEVERITY=PENALIZE and no knob applied yet
OR
- SEVERITY=WARN and knob set insufficient
OR
- missing some instrumentation fields but overall severity plausible

FAIL when:
- SEVERITY=BLOCK
OR
- no nearest neighbor reference for non-ALLOW severities
OR
- severity incoherent and cannot be trusted

---

## 6) REQUIRED ACTION KNOBS (STANDARD)
Choose minimal set.

For PENALIZE:
- change one of:
  - palette (C2)
  - groove/tempo band (C3)
  - hook grammar (C5)

For WARN:
- change at least two:
  - one must be hook grammar OR vocal identity
  - second can be palette or groove

For BLOCK:
- redesign:
  - new hook grammar AND new palette OR new vocal identity
  - rerun collision check after redesign

---

## 7) OUTPUT SCHEMA (MANDATORY)
COLLISION_BLOCKER_VAL_RESULT:
- TRACK_UID:
- VARIANT_LABEL:
- SCOPE_MODE:
- SIMILARITY_SCORE_0_1:
- SEVERITY:
- NEAREST_NEIGHBOR_REF:
- NOVELTY_ACTIONS_TAKEN:
- DECISION: {PASS | WARN | FAIL}
- REASONS: [...]
- REQUIRED_ACTION: ...
- RETEST_NOTES: [...]

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED

--- END.
