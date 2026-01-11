# Viral Hook Blueprint Engine — ENGINE
FILE: 03_SYSTEM_ENTITIES/10_ENG__ENGINES/12_TREND_GENRE_ENGINES/04__VIRAL_HOOK_BLUEPRINT_ENG.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: ENGINES (ENG)
ENGINE_FAMILY: 12_TREND_GENRE_ENGINES
DOC_TYPE: ENGINE
ENGINE_TYPE: TREND_GENRE
LEVEL: L3
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.ENG.TG.VIRAL_HOOK_BLUEPRINT.001
OWNER: SYSTEM
ROLE: Defines the viral-ready structural blueprint of a track (hook timing, repetition geometry, drops, pauses, energy curve, clip windows), based on style fingerprint + audience + duration policy. Produces an executable hook plan for Prompt Compiler and QA/Validators.

CHANGE_NOTE:
- DATE: 2026-01-11
- TYPE: MAJOR
- SUMMARY: "Created Viral Hook Blueprint: structural grammar, early-recognition targets, anti-repeat rules, and UGC-aligned moment placement."
- REASON: "Virality is not luck; it’s engineered timing + recognition + loopability."
- IMPACT: "Higher scroll-stop, better loop metrics, stronger creator adoption."
- CHANGE_ID: UE.CHG.2026-01-11.ENG.TG.VIRAL.BLUEPRINT.001

---

## 0) PURPOSE (LAW)
This engine outputs a **Viral Hook Blueprint (VHB)** — a concise structural plan that:
- guarantees early recognition (10–15s target for short variants)
- places hook and microhooks with repeat-safe variation
- includes at least one pause/snap and one drop/switch
- aligns with UGC moment needs
- stays within style fingerprint and duration policy

---

## 1) INPUTS (CONSUMES)
- Earworm Hook Stack (H1/H2/microhooks/S-tag/Q-line)
- Style Fingerprint (identity anchors)
- Audience Segment Target
- Duration Policy (short/full/alt intro)
- UGC Viral Ruleset (platform behavior constraints)
- Negative Spec Library (anti-artifacts)
- Catalog Memory (collision avoidance intent)

---

## 2) OUTPUTS (PRODUCES)
- Viral Hook Blueprint (VHB):
  - blueprint type (A/B/C templates)
  - timing targets (relative windows)
  - repetition geometry (A/A’/B/A etc.)
  - energy curve plan
  - required moments: pause/snap, drop/switch, loop outro
  - hook clarity rules (mix/arrangement intent)
- Variant Blueprints:
  - SHORT (UGC)
  - FULL (album)
  - ALT INTRO (optional)
- Validator Notes (what must be checked)

---

## 3) MINI-CONTRACT (MANDATORY)
CONSUMES: [
  "Earworm Hook Stack",
  "Style Fingerprint",
  "Audience Segment Target",
  "Duration Policy",
  "UGC Viral Ruleset",
  "Negative Spec Library",
  "Catalog Memory (optional)"
]
PRODUCES: [
  "Viral Hook Blueprint (VHB)",
  "Variant Blueprints (short/full/alt intro)",
  "Validator Notes"
]
DEPENDS_ON: [
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/12_TREND_GENRE_ENGINES/06__EARWORM_HOOK_STACK_ENG.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/12_TREND_GENRE_ENGINES/03__STYLE_FINGERPRINT_ENG.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/03__DURATION_POLICY_CTL.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/02__UGC_VIRAL_RULESET_CTL.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/01__HOOK_TIMING_VAL.md",
  "https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/60_QA__QUALITY/10_MUSIC_QA/01__SCROLL_STOP_5S_QA.md"
]
OUTPUT_TARGET: "05_PROJECTS/<MUSIC_PROJECTS>/BLUEPRINTS/VIRAL/"

---

## 4) BLUEPRINT TEMPLATES (STANDARD SET)
The engine must choose ONE primary template per variant.

### TEMPLATE A — FAST HOOK (short-form oriented)
- intro grab immediately
- hook appears early
- short verse, fast chorus
- loopable outro

### TEMPLATE B — MICROHOOK → HOOK (priming)
- microhook first (0–10s)
- hook hits soon after
- drop/switch after first hook

### TEMPLATE C — CALL/RESPONSE VIRAL
- hook is built as call-response (duet friendly)
- pause/snap before response
- designed for creators to lip-sync

---

## 5) TIMING TARGETS (RELATIVE WINDOWS)
Timing targets are expressed as windows (platform-safe):

Mandatory fields:
- INTRO_GRAB: [t..t]
- MICROHOOK_1: [t..t] (optional, recommended)
- HOOK_1: [t..t]
- PAUSE_SNAP: [t..t]
- DROP_SWITCH: [t..t]
- HOOK_2: [t..t] (repeat with variation)
- CLIP_WINDOW_PRIMARY: [t..t]
- OUTRO_LOOP: [t..t]

Default heuristic (overridden by Duration Policy):
- intro grab: 0–7s
- hook_1: by 10–20s (short), by 15–30s (full)
- pause/snap: before hook_1 or before hook_2
- drop/switch: after hook_1
- outro loop: last 6–12s

---

## 6) REPETITION GEOMETRY (REPEAT-SAFE)
Allowed patterns:
- A / A’ / B / A
- A / B / A / C / A
- A (short) / A (full) / A’’ (final)

Where:
- A = Hook core (H1)
- A’ = Hook with 1 knob changed (timbre/rhythm/lyric setup)
- B = Contrast section (H2 or verse)
- C = Drop/switch section

Hard rules:
- no exact copy-paste hook more than 2 times
- each hook return must apply at least 1 variation knob
- at least one “attention reset” event (pause or drop)

---

## 7) ENERGY CURVE (EXECUTABLE PLAN)
Engine outputs an energy curve in 4 phases:
1) Grab (0–10s): immediate identity
2) Lock (10–30s): hook + recognition
3) Flip (30–60s): drop/switch + renewed hook
4) Loop (last 10–15s): loopable ending imprint

If short variant:
- compress phases 2–3
- maximize phase 1 + loop

---

## 8) HOOK CLARITY RULES (MIX/ARRANGEMENT INTENT)
To make hook obvious:
- reduce competing layers under hook
- keep hook element 1 step louder/clearer (intent, not exact dB)
- vocals: prioritize intelligibility (RU)
- avoid long reverb tails masking hook
- ensure beat grid is clean at clip windows

---

## 9) UGC ALIGNMENT RULES
Blueprint must guarantee:
- at least 2 strong clip windows (10–15s each)
- at least 1 pause/snap (easy cut)
- at least 1 callout or quote line (if lyrical)
- at least 1 “drop” moment (edit-friendly)

---

## 10) FAILURE MODES & FIX
1) Hook too late
- Fix: switch to Template A or B; compress intro.

2) Hook not recognizable on first listen
- Fix: simplify hook contour; add S-tag earlier.

3) Too repetitive
- Fix: enforce A/A’ geometry and add contrast B.

4) Too busy, no clip windows
- Fix: add pause/snap and simplify arrangement during hook.

---

## 11) VALIDATOR NOTES (MANDATORY)
The blueprint must declare what validators should check:
- Hook timing pass/fail (window compliance)
- UGC-ready pass/fail (clip windows present)
- Repeat guard pass/fail (no spam repeats)
- Recognition 10s QA and Loop 15s QA

---

## 12) OUTPUT FORMAT (MANDATORY)
### VHB (for each variant)
- TEMPLATE: <A|B|C>
- TIMING_TARGETS:
  - intro_grab:
  - microhook_1:
  - hook_1:
  - pause_snap:
  - drop_switch:
  - hook_2:
  - clip_primary:
  - outro_loop:
- REPETITION_GEOMETRY:
- ENERGY_CURVE:
- HOOK_CLARITY_RULES:
- UGC_ALIGNMENT:
- VALIDATOR_NOTES:

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED

--- END.
