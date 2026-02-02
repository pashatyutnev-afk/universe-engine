# QUALITY GATES — CTL
FILE: 03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/09__QUALITY_GATES_CTL.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: CONTROLLERS (CTL)
CTL_REALM: 10_MUSIC_CONTROLLERS
DOC_TYPE: CONTROLLER
CTL_TYPE: QUALITY_GATES
LEVEL: L3
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.CTL.MUS.QUALITY_GATES.001
OWNER: SYSTEM
ROLE: Defines the factory-wide quality gate policy (PASS/WARN/FAIL logic) across Validators (VAL) and QA checks.
Specifies which checks are critical, which are optional, and what actions are required on WARN/FAIL.
Used by TEST→DOC gate ORC and Release readiness.

CHANGE_NOTE:
- DATE: 2026-01-12
- TYPE: MAJOR
- SUMMARY: "Created Quality Gates CTL: critical checks list, decision policy, and required actions on WARN/FAIL."
- REASON: "Without a single gate policy, decisions become inconsistent and docs/releases bloat."
- IMPACT: "Deterministic PASS/WARN/FAIL decisions + cleaner pipeline."
- CHANGE_ID: UE.CHG.2026-01-12.CTL.QUALITY.GATES.001

---

## 0) PURPOSE (LAW)
This controller defines:
- which checks are **critical** (must pass)
- which checks are **recommended** (may warn)
- how to decide PASS/WARN/FAIL consistently
- what actions are mandatory on WARN/FAIL

This is the policy used by the TEST→DOC gate.

---

## 1) GATE LEVELS (STANDARD)
- CRITICAL: fail → decision FAIL
- IMPORTANT: fail → decision WARN (or FAIL if combined)
- OPTIONAL: fail → note only (unless repeated)

---

## 2) CRITICAL CHECKS (MUST PASS)
Critical validators:
- Hook Timing VAL  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/01__HOOK_TIMING_VAL.md
- Repeat Guard VAL  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/03__REPEAT_GUARD_VAL.md
- Prompt Fidelity VAL  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/08__PROMPT_FIDELITY_VAL.md
- Collision Blocker VAL  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/05__COLLISION_BLOCKER_VAL.md

Conditional critical:
- PD Only VAL (if PD lyrics used)  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/04__PD_ONLY_VAL.md

---

## 3) IMPORTANT CHECKS (FAIL → WARN)
Validators:
- UGC Ready VAL  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/02__UGC_READY_VAL.md
- Hook Timing VAL edge-case warnings (still critical if hard fail)

QA:
- Scroll Stop 5s QA  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/60_QA__QUALITY/10_MUSIC_QA/01__SCROLL_STOP_5S_QA.md
- Recognition 10s QA  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/60_QA__QUALITY/10_MUSIC_QA/03__RECOGNITION_10S_QA.md
- Loop 15s QA  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/60_QA__QUALITY/10_MUSIC_QA/02__LOOP_15S_QA.md

---

## 4) OPTIONAL CHECKS (NOTE ONLY)
QA:
- Mix Translation QA  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/60_QA__QUALITY/10_MUSIC_QA/05__MIX_TRANSLATION_QA.md
- Creator Panel QA  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/60_QA__QUALITY/10_MUSIC_QA/04__CREATOR_PANEL_QA.md
- Hook Panel QA  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/60_QA__QUALITY/10_MUSIC_QA/06__HOOK_PANEL_QA.md

---

## 5) DECISION POLICY (PASS/WARN/FAIL)
### PASS
- all CRITICAL pass
- IMPORTANT checks are pass or minor notes

### WARN
- CRITICAL all pass
- 1 IMPORTANT fails OR multiple OPTIONAL fail patterns
- fixable with 1 knob (e.g., ALT_INTRO, stronger cut point, clearer Q-line)

### FAIL
- any CRITICAL fails
OR
- multiple IMPORTANT fail together
OR
- repeated WARN cycles without improvement

---

## 6) REQUIRED ACTIONS
### On WARN
- produce a RETEST_BRIEF:
  - change only 1–2 knobs
  - keep anchors fixed
- rerun only necessary steps (hook/prompt/intro) then recheck gates

### On FAIL
- stop documentation and release packaging
- redesign:
  - new hook grammar OR new palette/vocal role
- rerun Track Factory with updated plan

---

## 7) OUTPUT EXPECTATIONS (WHAT GATE MUST RECORD)
A decision record must include:
- decision (PASS/WARN/FAIL)
- list of checks run
- failures and notes
- selected fix knobs (if any)
- next action

---

## 8) REFERENCES (RAW)
Used by:
- Track TEST → DOC Gate ORC  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/03__TRACK_TEST_DOC_GATE_ORC.md
- Release Pack Ready VAL  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/06__RELEASE_PACK_READY_VAL.md

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED

--- END.
