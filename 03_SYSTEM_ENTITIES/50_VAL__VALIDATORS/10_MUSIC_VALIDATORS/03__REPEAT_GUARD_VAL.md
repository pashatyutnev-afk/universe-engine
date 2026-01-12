# REPEAT GUARD — VAL
FILE: 03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/03__REPEAT_GUARD_VAL.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: VALIDATORS (VAL)
VAL_REALM: 10_MUSIC_VALIDATORS
DOC_TYPE: VALIDATOR
VAL_TYPE: REPEAT_GUARD
LEVEL: L3
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.VAL.MUS.REPEAT_GUARD.001
OWNER: SYSTEM
ROLE: Validates repeat-safe behavior in lyrics/hook structure:
blocks chant spam, identical phrase loops, copy-paste chorus repeats without variation, and over-repeated slogans.
Aligned with Negative Spec packs and Quality Gates policy.

CHANGE_NOTE:
- DATE: 2026-01-12
- TYPE: MAJOR
- SUMMARY: "Created Repeat Guard validator: deterministic repeat/spam checks and required variation fixes."
- REASON: "Top failure mode: same phrases repeated endlessly causing low quality and catalog sameness."
- IMPACT: "Cleaner hooks, better listening retention, higher credibility."
- CHANGE_ID: UE.CHG.2026-01-12.VAL.REPEAT_GUARD.001

---

## 0) PURPOSE (LAW)
Answer:
**“Is repetition purposeful and varied, not spam?”**

This validator checks structural/lyric repetition patterns and required variation rules.

---

## 1) INPUTS (CONSUMES)
Required:
- DURATION_MODE: {SHORT | FULL | ALT_INTRO}
- LYRICS_MODE: {LYRICAL | INSTRUMENTAL}
- STRUCTURE_NOTES:
  - chorus_repeat_count (0..N)
  - variation_present: YES/NO (or description)
- TEXT_SAMPLES (recommended):
  - chorus text (or hook line tokens)
  - repeated phrases list (if available)
- HOOK_STACK_NOTES (optional):
  - hook grammar type
  - repetition geometry token (A/A’/B/A)

If instrumental:
- provide motif repetition notes instead of lyrics text.

---

## 2) OUTPUT (PRODUCES)
- DECISION: {PASS | WARN | FAIL}
- REASONS: (short bullets)
- REQUIRED_ACTION:
  - {NONE | ADD_VARIATION | REDUCE_REPEATS | REWRITE_HOOK_LINE | CHANGE_HOOK_GRAMMAR}
- RETEST_NOTES: 1–2 knobs max

---

## 3) RULE SOURCES (CTL) — RAW
Negative Spec Library CTL (repeat spam pack):
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/12__NEGATIVE_SPEC_LIBRARY_CTL.md

Quality Gates CTL (decision semantics):
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/09__QUALITY_GATES_CTL.md

---

## 4) CHECKS (DETERMINISTIC)

### CHECK A — Identical chorus repeats without variation
If chorus_repeat_count ≥ 1:
- PASS if variation_present=YES (at least 1 line or phrase changes)
- WARN if variation unclear but likely fixable
- FAIL if variation_present=NO and repeats are direct copy-paste

---

### CHECK B — Chant spam / phrase loop dominance
PASS when:
- no single phrase is repeated excessively without change
WARN when:
- one phrase is repeated too much but can be reduced or varied
FAIL when:
- track is dominated by a single repeated phrase (loop spam)

(Operational sign: repeated phrase appears many times back-to-back or across most sections.)

---

### CHECK C — Hook grammar stuck in one pattern
PASS when:
- repetition geometry includes at least one evolution point (A/A’ rather than A/A/A/A)
WARN when:
- minimal evolution exists but weak
FAIL when:
- entire hook behavior is a flat loop with no variation knob

---

### CHECK D — Instrumental motif spam (instrumental mode)
PASS when:
- motif repeats with variation (change texture/rhythm/ending)
WARN when:
- variation weak
FAIL when:
- motif loops identically for most of track

---

## 5) DECISION LOGIC
PASS when:
- no copy-paste repeats
- no phrase spam dominance
- variation knob exists and is used

WARN when:
- repetition is borderline and fixable with 1 knob:
  - add one altered line
  - reduce repeats
  - add micro-variation

FAIL when:
- copy-paste chorus repeats dominate
- chant spam / phrase loop dominates
- no evolution/variation plan exists

---

## 6) REQUIRED ACTION KNOBS (STANDARD)
Choose only 1–2 knobs in WARN/FAIL.

- ADD_VARIATION:
  - change one line in repeat chorus
  - add a response line
  - alter cadence on repeat

- REDUCE_REPEATS:
  - reduce count or shorten the repeated section

- REWRITE_HOOK_LINE:
  - replace the repeated slogan with a stronger, shorter, less spammy line

- CHANGE_HOOK_GRAMMAR:
  - chant → motif or slogan → motif with variation

---

## 7) OUTPUT SCHEMA (MANDATORY)
REPEAT_GUARD_VAL_RESULT:
- TRACK_UID:
- VARIANT_LABEL:
- DURATION_MODE:
- LYRICS_MODE:
- chorus_repeat_count:
- variation_present:
- repeated_phrases: (optional)
- DECISION: {PASS | WARN | FAIL}
- REASONS: [...]
- REQUIRED_ACTION: ...
- RETEST_NOTES: [...]

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED

--- END.
