# REGRESSION GUARD — QA
FILE: 03_SYSTEM_ENTITIES/60_QA__QUALITY/10_MUSIC_QA/09__REGRESSION_GUARD_QA.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: QUALITY (QA)
QA_REALM: 10_MUSIC_QA
DOC_TYPE: QA_CHECK
QA_TYPE: REGRESSION_GUARD
LEVEL: L3
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.QA.MUS.REGRESSION_GUARD.001
OWNER: SYSTEM
ROLE: A regression safety check across iterations:
ensures that “new version” changes do not degrade key qualities (scroll-stop, recognition, loopability, mix translation),
and that fixes do not introduce new failures. Used when reworking a take or producing ALT_INTRO/repair variants.

CHANGE_NOTE:
- DATE: 2026-01-12
- TYPE: MAJOR
- SUMMARY: "Created Regression Guard QA: A/B compare protocol and PASS/WARN/FAIL for regression prevention."
- REASON: "Fixing one problem often breaks another; this guard prevents quality regression."
- IMPACT: "More stable improvement loops and fewer wasted iterations."
- CHANGE_ID: UE.CHG.2026-01-12.QA.REGRESSION.001

---

## 0) PURPOSE (LAW)
Answer:
**“Did the new iteration improve without breaking key qualities?”**

This QA is used for:
- ALT_INTRO versions
- retests after WARN
- revised prompt packs
- mix fixes

---

## 1) INPUTS
Required:
- BASE_VERSION (audio take)
- NEW_VERSION (audio take)
Optional:
- what was changed (1–2 knobs)
- which gate was failing before (e.g., Hook Timing, UGC edit point)

---

## 2) PROCEDURE (HOW TO RUN)
1) Run fast A/B comparisons on short windows:
   - 0:00–0:05 (scroll stop)
   - 0:00–0:10 (recognition)
   - best 10–15s clip window (loop test)
   - 15–30s mid section (mix translation feel)
2) Decide:
   - did the intended fix work?
   - did anything get worse?

---

## 3) REGRESSION RUBRIC (HEURISTIC)
### R1 — Fix success
- the targeted issue is improved (e.g., hook earlier, clearer cut point)

### R2 — No new major problems
- new version did not become:
  - more annoying
  - less clear
  - less loopable
  - worse translated (mud/harshness)

### R3 — Identity preserved
- the track still feels like the same intended identity (no drift)

---

## 4) RESULT (PASS/WARN/FAIL)
PASS when:
- fix succeeded
- no regression in key qualities
- identity preserved

WARN when:
- fix succeeded but one new weakness appeared (minor)

FAIL when:
- fix did not succeed
OR
- fix introduced a major regression (worse scroll-stop/recognition/loop)

---

## 5) FIX SUGGESTION KNOBS (1–2 MAX)
- KEEP_FIX_TUNE_SECONDARY:
  - keep the main fix, adjust secondary parameter
- REVERT_AND_TRY_OTHER:
  - revert and attempt a different knob
- IDENTITY_RELOCK:
  - restore anchors if drift happened

---

## 6) OUTPUT TEMPLATE (MANDATORY)
REGRESSION_GUARD_QA_RESULT:
- TRACK_UID:
- BASE_TAKE_ID:
- NEW_TAKE_ID:
- TARGETED_FIX: (short)
- RESULT: {PASS | WARN | FAIL}
- IMPROVED:
  - bullets
- REGRESSED:
  - bullets
- NOTES:
  - 3–12 bullets
- FIX_SUGGESTION:
  - 1–2 knobs max

---

## 7) REFERENCES (RAW)
This QA ties to:
- Quality Gates CTL  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/09__QUALITY_GATES_CTL.md

Related QAs:
- Scroll Stop 5s QA  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/60_QA__QUALITY/10_MUSIC_QA/01__SCROLL_STOP_5S_QA.md
- Recognition 10s QA  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/60_QA__QUALITY/10_MUSIC_QA/03__RECOGNITION_10S_QA.md
- Loop 15s QA  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/60_QA__QUALITY/10_MUSIC_QA/02__LOOP_15S_QA.md
- Mix Translation QA  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/60_QA__QUALITY/10_MUSIC_QA/05__MIX_TRANSLATION_QA.md

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED

--- END.
