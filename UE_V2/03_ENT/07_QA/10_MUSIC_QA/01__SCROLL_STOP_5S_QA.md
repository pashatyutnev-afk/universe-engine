# SCROLL STOP 5s — QA
FILE: 03_SYSTEM_ENTITIES/60_QA__QUALITY/10_MUSIC_QA/01__SCROLL_STOP_5S_QA.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: QUALITY (QA)
QA_REALM: 10_MUSIC_QA
DOC_TYPE: QA_CHECK
QA_TYPE: SCROLL_STOP_5S
LEVEL: L3
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.QA.MUS.SCROLL_STOP_5S.001
OWNER: SYSTEM
ROLE: A fast heuristic listening test:
in the first 5 seconds, does the track create a “stop scrolling” impulse?
Evaluates immediate identity stamp, energy clarity, and attention hook without needing a full listen.

CHANGE_NOTE:
- DATE: 2026-01-12
- TYPE: MAJOR
- SUMMARY: "Created Scroll Stop 5s QA: test procedure, scoring, PASS/WARN/FAIL, and fix suggestions."
- REASON: "Short-form success requires instant attention; dead intros kill performance."
- IMPACT: "Faster selection of winners and fewer wasted takes."
- CHANGE_ID: UE.CHG.2026-01-12.QA.SCROLL_STOP.001

---

## 0) PURPOSE (LAW)
Answer:
**“Would a viewer stop scrolling within the first 5 seconds?”**

This is a human/heuristic gate, not a deterministic validator.

---

## 1) INPUTS
- audio take (candidate)
- optional: DURATION_MODE (SHORT/FULL), UGC_INTENT (YES/NO)
- optional: identity anchors (Style Fingerprint summary)

---

## 2) PROCEDURE (HOW TO RUN)
1) Start playback from 0:00.
2) Listen only 0:00–0:05.
3) Judge the immediate “stop impulse” using the criteria below.
4) Output RESULT + NOTES + FIX_SUGGESTION.

---

## 3) EVALUATION CRITERIA (HEURISTIC)
### C1 — Identity stamp present?
- signature tag / motif / obvious genre anchor is heard immediately

### C2 — Energy clarity
- groove or tone is clear (not foggy)
- no dead air / no weak intro

### C3 — Attention hook
At least one:
- vocal entry with strong clarity
- catchy motif
- striking timbre or drum pattern
- immediate hook-adjacent phrase

### C4 — No anti-scroll artifacts
Avoid:
- ambient build
- slow fade-in
- muddy start
- unclear vocal

---

## 4) RESULT (PASS/WARN/FAIL)
PASS when:
- clear identity stamp or hook impulse exists within 5s
- intro is not dead

WARN when:
- potential exists but start is slightly weak (fixable by one knob)

FAIL when:
- first 5 seconds are dead / generic / unclear
- nothing makes you stop

---

## 5) FIX SUGGESTION KNOBS (1–2 MAX)
Choose minimal actions.

- COLD_OPEN:
  - start on groove immediately
- EARLY_STAMP:
  - add signature tag or motif at 0–3s
- CLARITY_FIX:
  - make intro less muddy; bring lead element forward
- HOOK_ADJACENT_START:
  - start near pre-hook/hook

---

## 6) OUTPUT TEMPLATE (MANDATORY)
SCROLL_STOP_5S_QA_RESULT:
- TRACK_UID:
- TAKE_ID:
- RESULT: {PASS | WARN | FAIL}
- NOTES:
  - 3–7 bullets
- FIX_SUGGESTION:
  - 1–2 knobs max

---

## 7) REFERENCES (RAW)
Related policies:
- Duration Policy CTL  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/03__DURATION_POLICY_CTL.md
- UGC Viral Ruleset CTL  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/40_CTL__CONTROLLERS/10_MUSIC_CONTROLLERS/02__UGC_VIRAL_RULESET_CTL.md

Used in gate ORC:
- Track TEST → DOC Gate ORC  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/20_ORC__ORCHESTRATORS/10_MUSIC_ORCHESTRATORS/03__TRACK_TEST_DOC_GATE_ORC.md

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED

--- END.
