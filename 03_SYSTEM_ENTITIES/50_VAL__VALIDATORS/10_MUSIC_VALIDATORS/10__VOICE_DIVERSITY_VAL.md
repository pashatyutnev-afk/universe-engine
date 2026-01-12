# VOICE DIVERSITY — VAL
FILE: 03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/10__VOICE_DIVERSITY_VAL.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: VALIDATORS (VAL)
VAL_REALM: 10_MUSIC_VALIDATORS
DOC_TYPE: VALIDATOR
VAL_TYPE: VOICE_DIVERSITY
LEVEL: L3
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.VAL.MUS.VOICE_DIVERSITY.001
OWNER: SYSTEM
ROLE: Validates that planned or produced vocals do not collapse into a single generic voice across catalog scope.
Checks voice-role distribution, distinct vocal identity tokens, and adherence to cast/roster plans.
Outputs PASS/WARN/FAIL with corrective actions (cast split, role changes, instrumental variant, etc.).

CHANGE_NOTE:
- DATE: 2026-01-12
- TYPE: MAJOR
- SUMMARY: "Created Voice Diversity validator: role distribution checks and corrective actions to prevent same-voice collapse."
- REASON: "Known failure mode: many tracks sound like the same person singing."
- IMPACT: "More believable catalog, stronger group identity, better differentiation."
- CHANGE_ID: UE.CHG.2026-01-12.VAL.VOICE_DIVERSITY.001

---

## 0) PURPOSE (LAW)
Answer:
**“Are vocal identities sufficiently diverse as intended?”**

This validator can be used at:
- planning stage (cast roster spec)
- post-generation stage (voice tokens / perceived sameness)

---

## 1) INPUTS (CONSUMES)
Required:
- SCOPE_MODE: {GROUP | ALBUM | GLOBAL}
- VOCAL_MODE: {LYRICAL | INSTRUMENTAL | MIXED}
- VOICE_TOKENS_CURRENT:
  - lead_vocal_token
  - contrast_vocal_token (optional)
  - choir_stack_token (optional)
  - delivery_style_token (optional)
- CAST_PLAN (optional but recommended):
  - allowed vocalist roles list
  - lead/contrast distribution intent

Recommended:
- RECENT_VOICE_TOKENS_HISTORY (from catalog memory scope)
- NEAREST_NEIGHBOR_VOICE_ALERTS (if any)

---

## 2) OUTPUT (PRODUCES)
- DECISION: {PASS | WARN | FAIL}
- REASONS: (short bullets)
- REQUIRED_ACTION:
  - {NONE | ADD_CONTRAST_VOCAL | CHANGE_LEAD_ROLE | SPLIT_DUET | SWITCH_TO_INSTRUMENTAL | RECAST}
- RETEST_NOTES: 1–2 knobs max

---

## 3) RULE SOURCES (CTL) — RAW
Catalog Memory CTL (voice tokens and history):
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/07__CATALOG_MEMORY_CTL.md

Fingerprint Collision Thresholds CTL (similarity severity):
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/06__FINGERPRINT_COLLISION_THRESHOLDS_CTL.md

Quality gates policy:
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/09__QUALITY_GATES_CTL.md

---

## 4) CHECKS (DETERMINISTIC)

### CHECK A — Presence of vocal identity tokens (if lyrical)
If VOCAL_MODE includes lyrical vocals:
- lead_vocal_token must be present
WARN if missing (instrumentation issue)
FAIL if consistently missing while claiming lyrical mode

---

### CHECK B — Same-voice collapse risk vs history
If history exists:
- compare lead_vocal_token to recent tokens in scope
WARN if:
- token matches many recent items (sameness risk)
FAIL if:
- token matches almost everything recently AND scope requires diversity (album-level or explicit policy)

(Exact thresholds can be refined later; this validator enforces the presence of the check and action.)

---

### CHECK C — Role distribution intent (planning)
If CAST_PLAN provided:
- confirm current plan includes at least:
  - one contrast option OR a reason for single-voice identity
WARN if:
- plan seems too narrow
FAIL if:
- plan conflicts with group identity objective requiring diversity

---

### CHECK D — Instrumental exceptions
If track is instrumental:
- PASS (voice diversity not applicable)
unless policy says the group must be vocal; then WARN only.

---

## 5) DECISION LOGIC
PASS when:
- voice tokens exist (if lyrical)
- diversity risk is low or intentional (single-voice identity documented)
- cast plan (if provided) supports required variety

WARN when:
- sameness risk detected but fixable with 1 knob:
  - add contrast vocal
  - duet split
  - change lead role
- missing instrumentation data (tokens) but can be added

FAIL when:
- strong sameness across scope and no plan to fix
- cast plan violates required diversity objective

---

## 6) REQUIRED ACTION KNOBS (STANDARD)
Choose 1–2 knobs.

- ADD_CONTRAST_VOCAL:
  - add second voice for pre-hook/chorus responses
- CHANGE_LEAD_ROLE:
  - switch vocalist role token
- SPLIT_DUET:
  - call/response or alternating lines
- SWITCH_TO_INSTRUMENTAL:
  - if vocals are causing sameness and track works instrumental
- RECAST:
  - regenerate with different vocal identity constraints

---

## 7) OUTPUT SCHEMA (MANDATORY)
VOICE_DIVERSITY_VAL_RESULT:
- TARGET_UID:
- SCOPE_MODE:
- VOCAL_MODE:
- lead_vocal_token:
- recent_match_count: (optional)
- DECISION: {PASS | WARN | FAIL}
- REASONS: [...]
- REQUIRED_ACTION: ...
- RETEST_NOTES: [...]

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED

--- END.
