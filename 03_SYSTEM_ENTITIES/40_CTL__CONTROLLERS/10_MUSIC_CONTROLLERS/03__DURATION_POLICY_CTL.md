# DURATION POLICY — CTL
FILE: 03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/03__DURATION_POLICY_CTL.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: CONTROLLERS (CTL)
CTL_REALM: 10_MUSIC_CONTROLLERS
DOC_TYPE: CONTROLLER
CTL_TYPE: DURATION_POLICY
LEVEL: L3
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.CTL.MUS.DURATION_POLICY.001
OWNER: SYSTEM
ROLE: Defines duration targets and structure budgets for variants (SHORT/FULL/ALT_INTRO),
including hook timing windows, section density rules, and prohibitions that prevent dead intros and overly long builds.
Used by Duration Strategy ENG, Hook/UGC engines, Prompt Compiler, and QA/VAL gates.

CHANGE_NOTE:
- DATE: 2026-01-12
- TYPE: MAJOR
- SUMMARY: "Created Duration Policy CTL: duration modes, hook timing windows, section budgets, and variant rules."
- REASON: "Without duration law, outputs drift in length, intros become long, and UGC variants fail."
- IMPACT: "Consistent runtimes, earlier hooks, better loop behavior."
- CHANGE_ID: UE.CHG.2026-01-12.CTL.DURATION.POLICY.001

---

## 0) PURPOSE (LAW)
This controller defines **duration rules** and **structure budgets**.
It does not decide creative content; it sets constraints for engines and gates.

---

## 1) DURATION MODES (STANDARD)
A production run must select one of:

- MODE.SHORT (UGC-first)
- MODE.FULL (song-first)
- MODE.ALT_INTRO (repair variant, optional)

---

## 2) TARGET DURATIONS (DEFAULT BANDS)
These are target bands; engines may output within band unless higher-level plan overrides.

- SHORT: ~0:45 to ~1:30
- FULL: ~2:00 to ~3:30
- ALT_INTRO: same as SHORT or FULL (depends on base), but changes intro behavior

If platform requires specific max/min, it must be encoded elsewhere; this CTL defines defaults.

---

## 3) HOOK TIMING WINDOWS (MANDATORY)
Hook timing expectations by mode:

### SHORT
- identity stamp: 0–7s
- Hook_1 must appear by: 10–20s
- Clip window should be available by: 10–30s

### FULL
- identity stamp: 0–10s
- Hook_1 must appear by: 15–30s
- Clip window should be available by: 15–45s

ALT_INTRO:
- forces “direct entry” or “microhook priming”
- goal: move hook earlier or make recognition faster

---

## 4) SECTION BUDGETS (STRUCTURE LIMITS)
These are budgets for lyrics/sections, not strict templates.

### SHORT (UGC-first)
- Intro: 0–2 lines (or none)
- Chorus (hook): 4–6 lines max
- Verse: 2–6 lines max
- Chorus repeat: allowed, must vary at least 1 line
- Bridge: optional, 0–2 lines max
- Outro: 0–2 lines (loop-friendly)

### FULL (song-first)
- Verse 1: 4–10 lines
- Chorus: 6–8 lines
- Verse 2: 4–10 lines (variation)
- Chorus repeat: allowed, must vary at least 1 small knob (line/phrase)
- Bridge: optional 2–6 lines
- Final chorus: allowed

---

## 5) INTRO POLICY (ANTI-DEAD INTRO)
Hard rule:
- No long ambient intro before identity stamp.

Allowed intro styles:
- direct entry (hook-adjacent)
- microhook priming
- signature tag intro (S-tag) + immediate groove

Prohibited:
- intros that delay recognition beyond hook timing windows
- long spoken/ambient build for UGC variants

---

## 6) VARIANT RULES (MANDATORY)
If variants are produced:
- SHORT and FULL must preserve identity anchors.
- ALT_INTRO exists only to repair:
  - late hook
  - weak recognition
  - dead intro

ALT_INTRO may change:
- intro method
- early hook positioning
but must not change:
- style fingerprint anchors
- primary genre identity

---

## 7) PASS/FAIL CRITERIA (FOR GATES)
PASS when:
- track stays within target band (or close)
- hook appears within timing window for selected mode
- identity stamp occurs early
- structure budgets respected (no bloated chorus)
- intro policy satisfied

WARN when:
- minor timing drift (hook slightly late) but fixable with ALT_INTRO
- short variant too long but can be trimmed

FAIL when:
- hook far outside window
- long dead intro persists
- structure is bloated and not UGC-usable (in SHORT mode)

---

## 8) REFERENCES (RAW)
Used by:
- Duration Strategy ENG  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/11_MUSIC_FACTORY_ENGINES/05__DURATION_STRATEGY_ENG.md
- Viral Hook Blueprint ENG  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/12_TREND_GENRE_ENGINES/04__VIRAL_HOOK_BLUEPRINT_ENG.md
- UGC Moment Map ENG  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/12_TREND_GENRE_ENGINES/05__UGC_MOMENT_MAP_ENG.md

Validator alignment:
- Hook Timing VAL  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/01__HOOK_TIMING_VAL.md

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED

--- END.
