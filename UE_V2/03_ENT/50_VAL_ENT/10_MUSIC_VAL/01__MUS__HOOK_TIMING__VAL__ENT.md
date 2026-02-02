# HOOK TIMING — VAL
FILE: 03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/01__HOOK_TIMING_VAL.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: VALIDATORS (VAL)
VAL_REALM: 10_MUSIC_VALIDATORS
DOC_TYPE: VALIDATOR
VAL_TYPE: HOOK_TIMING
LEVEL: L3
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.VAL.MUS.HOOK_TIMING.001
OWNER: SYSTEM
ROLE: Validates hook timing compliance against Duration Policy:
identity stamp timing, Hook_1 arrival window, and clip-window readiness.
Outputs PASS/WARN/FAIL with required corrective action knobs.

CHANGE_NOTE:
- DATE: 2026-01-12
- TYPE: MAJOR
- SUMMARY: "Created Hook Timing validator: required timing markers, deterministic checks per duration mode, and fix actions."
- REASON: "Late hooks and dead intros are top failure modes for UGC and recognition."
- IMPACT: "Earlier recognition + higher UGC readiness + consistent factory gating."
- CHANGE_ID: UE.CHG.2026-01-12.VAL.HOOK_TIMING.001

---

## 0) PURPOSE (LAW)
Answer:
**“Hook and identity arrive early enough for the selected duration mode?”**

This validator checks timing markers against Duration Policy CTL.

---

## 1) INPUTS (CONSUMES)
Required:
- DURATION_MODE: {SHORT | FULL | ALT_INTRO}
- TIMING_MARKERS:
  - t_identity_stamp_sec
  - t_hook1_sec
  - t_primary_clip_window_start_sec (optional but recommended)
  - t_primary_clip_window_end_sec (optional but recommended)

Optional:
- notes: where S-tag appears
- track variant label: {MAIN | SHORT_CUT | ALT_INTRO | ...}

Where markers come from:
- manual annotation OR
- take metadata OR
- structured listening notes (must include seconds)

---

## 2) OUTPUT (PRODUCES)
- DECISION: {PASS | WARN | FAIL}
- REASONS: (short bullets)
- REQUIRED_ACTION:
  - {NONE | ALT_INTRO | SHORTEN_INTRO | MOVE_HOOK_EARLIER | INCREASE_EARLY_STAMP | RESTRUCTURE_SECTIONS}
- RETEST_NOTES (if WARN/FAIL): 1–2 knobs max

---

## 3) RULE SOURCE (CTL) — RAW
Duration Policy CTL (source of timing windows):
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/03__DURATION_POLICY_CTL.md

Quality gates policy (how WARN/FAIL is handled in ORC):
RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/09__QUALITY_GATES_CTL.md

---

## 4) CHECKS (DETERMINISTIC)

### CHECK A — Identity stamp timing
- Validate t_identity_stamp_sec is within the window for selected mode.

Expected (policy-aligned):
- SHORT: 0–7s
- FULL: 0–10s
- ALT_INTRO: must improve identity timing vs base

Decision:
- FAIL if identity stamp is clearly late for mode.
- WARN if slightly late but fixable by ALT_INTRO / intro trim.

---

### CHECK B — Hook_1 arrival timing
- Validate t_hook1_sec within the window for selected mode.

Expected (policy-aligned):
- SHORT: Hook_1 by 10–20s
- FULL: Hook_1 by 15–30s
- ALT_INTRO: hook must move earlier or recognition must become stronger earlier

Decision:
- FAIL if hook is far outside window.
- WARN if borderline and fixable by one knob.

---

### CHECK C — Primary clip window readiness (recommended)
If t_primary_clip_window_* markers exist:
- Confirm at least one clean clip window exists early enough.

Expected (policy-aligned):
- SHORT: clip window should be available by 10–30s
- FULL: clip window by 15–45s

Decision:
- WARN if missing/late (unless the run is explicitly non-UGC).
- FAIL only if UGC-first objective is declared AND no clip window exists.

---

## 5) DECISION LOGIC (PASS/WARN/FAIL)
PASS when:
- Identity stamp within window
- Hook_1 within window
- Clip window exists within window (or not required for non-UGC run)

WARN when:
- One check is slightly late but fixable with 1 knob:
  - trim intro
  - ALT_INTRO
  - earlier motif stamp
  - chorus density shift (bring hook earlier)

FAIL when:
- Identity stamp clearly late for mode
OR
- Hook_1 clearly late for mode
OR
- UGC-first declared and no early clip window exists

---

## 6) REQUIRED ACTION KNOBS (STANDARD)
Choose only 1–2 knobs in WARN/FAIL retest.

- ALT_INTRO:
  - cold open
  - signature tag first
  - microhook priming

- SHORTEN_INTRO:
  - remove long ambient build
  - start on groove immediately

- MOVE_HOOK_EARLIER:
  - pre-hook into chorus faster
  - compress verse lines (SHORT mode)

- INCREASE_EARLY_STAMP:
  - stronger S-tag / motif in first 10s

- RESTRUCTURE_SECTIONS:
  - rebuild section order to satisfy windows

---

## 7) OUTPUT SCHEMA (MANDATORY)
HOOK_TIMING_VAL_RESULT:
- TRACK_UID:
- VARIANT_LABEL:
- DURATION_MODE:
- t_identity_stamp_sec:
- t_hook1_sec:
- t_primary_clip_window_start_sec: (optional)
- t_primary_clip_window_end_sec: (optional)
- DECISION: {PASS | WARN | FAIL}
- REASONS: [...]
- REQUIRED_ACTION: ...
- RETEST_NOTES: [...]

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED

--- END.
