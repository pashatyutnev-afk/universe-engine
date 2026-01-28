# UGC READY — VAL
FILE: 03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/02__UGC_READY_VAL.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: VALIDATORS (VAL)
VAL_REALM: 10_MUSIC_VALIDATORS
DOC_TYPE: VALIDATOR
VAL_TYPE: UGC_READY
LEVEL: L3
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.VAL.MUS.UGC_READY.001
OWNER: SYSTEM
ROLE: Validates UGC readiness compliance against UGC Viral Ruleset CTL:
presence of clip windows, edit points, quote/tag placement, early recognition support, and loop imprint.
Outputs PASS/WARN/FAIL with required corrective knobs.

CHANGE_NOTE:
- DATE: 2026-01-12
- TYPE: MAJOR
- SUMMARY: "Created UGC Ready validator: deterministic checks for clip windows/edit points/quote-tag/loop imprint aligned to UGC ruleset."
- REASON: "Tracks fail virality when they have no usable clip windows or edit points."
- IMPACT: "Higher creator adoption and stronger UGC performance."
- CHANGE_ID: UE.CHG.2026-01-12.VAL.UGC_READY.001

---

## 0) PURPOSE (LAW)
Answer:
**“Does this track variant satisfy UGC viral constraints?”**

This validator checks against UGC Viral Ruleset CTL.

---

## 1) INPUTS (CONSUMES)
Required:
- UGC_INTENT: {YES | NO} (or objective: UGC-first / not)
- UGC_MOMENT_SPEC:
  - primary_clip_window: [start_sec, end_sec]
  - secondary_clip_windows: (optional list)
  - edit_points: (pause/snap/drop/switch; list or note)
  - quote_hook: (optional, lyrical)
  - sound_tag: (optional, instrumental)
  - loop_imprint_note: (how ending loops)
- TIMING_MARKERS (recommended):
  - t_identity_stamp_sec
  - t_hook1_sec

If UGC_INTENT=NO, validator may return PASS by default unless gross violations exist.
If UGC_INTENT=YES, full checks apply.

---

## 2) OUTPUT (PRODUCES)
- DECISION: {PASS | WARN | FAIL}
- REASONS: (short bullets)
- REQUIRED_ACTION:
  - {NONE | ADD_CLIP_WINDOW | ADD_EDIT_POINT | IMPROVE_QUOTE_OR_TAG | MOVE_IDENTITY_EARLIER | IMPROVE_LOOP_IMPRINT}
- RETEST_NOTES: 1–2 knobs max

---

## 3) RULE SOURCE (CTL) — RAW
UGC Viral Ruleset CTL:
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/02__UGC_VIRAL_RULESET_CTL.md

Duration Policy CTL (timing alignment):
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/03__DURATION_POLICY_CTL.md

Quality gates policy:
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/09__QUALITY_GATES_CTL.md

---

## 4) CHECKS (DETERMINISTIC)

### CHECK A — Primary clip window exists
PASS condition:
- primary_clip_window exists
- length ~8–15s recommended
WARN if:
- window exists but is awkward length (too short/too long)
FAIL if:
- UGC_INTENT=YES and no primary window exists

---

### CHECK B — At least one edit point exists
PASS condition:
- edit_points list not empty (pause/snap OR drop/switch)
WARN if:
- edit point exists but weak/unclear (single vague note)
FAIL if:
- UGC_INTENT=YES and no edit point exists

---

### CHECK C — Quote hook OR sound tag present
PASS condition:
- if lyrical: quote_hook exists OR explicit hook caption note exists
- if instrumental: sound_tag exists
WARN if:
- present but unclear (“maybe here” without specifics)
FAIL if:
- UGC_INTENT=YES and neither quote_hook nor sound_tag exists

---

### CHECK D — Early recognition support
PASS condition:
- identity stamp and hook timing are not obviously late for the chosen mode
WARN if:
- borderline late but fixable by ALT_INTRO / early stamp
FAIL if:
- identity stamp obviously late and UGC_INTENT=YES

(If timing markers missing: WARN unless UGC_INTENT=NO.)

---

### CHECK E — Loop imprint note exists
PASS condition:
- loop_imprint_note exists (simple statement is enough)
WARN if:
- loop imprint exists but weak/unclear
FAIL if:
- UGC_INTENT=YES and no loop plan exists

---

## 5) DECISION LOGIC
PASS when:
- A + B + C pass (for UGC_INTENT=YES)
- D not FAIL
- E at least WARN (prefer PASS)

WARN when:
- one component is weak but fixable with 1 knob
- missing timing markers but other UGC spec exists

FAIL when:
- UGC_INTENT=YES and any of A/B/C is missing
- or D is clearly violated for UGC-first mode

---

## 6) REQUIRED ACTION KNOBS (STANDARD)
Choose only 1–2 knobs.

- ADD_CLIP_WINDOW:
  - define a 10–15s hook-centric window
- ADD_EDIT_POINT:
  - add pause/snap near hook
  - or engineer a drop/switch peak
- IMPROVE_QUOTE_OR_TAG:
  - choose stronger Q-line / place it near window
  - define clear S-tag
- MOVE_IDENTITY_EARLIER:
  - cold open / signature tag intro
- IMPROVE_LOOP_IMPRINT:
  - loopable outro / end-stamp

---

## 7) OUTPUT SCHEMA (MANDATORY)
UGC_READY_VAL_RESULT:
- TRACK_UID:
- VARIANT_LABEL:
- UGC_INTENT:
- primary_clip_window:
- edit_points:
- quote_hook:
- sound_tag:
- loop_imprint_note:
- t_identity_stamp_sec: (optional)
- t_hook1_sec: (optional)
- DECISION: {PASS | WARN | FAIL}
- REASONS: [...]
- REQUIRED_ACTION: ...
- RETEST_NOTES: [...]

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED

--- END.
