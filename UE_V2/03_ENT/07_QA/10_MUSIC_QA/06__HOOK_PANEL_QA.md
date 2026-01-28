# HOOK PANEL — QA
FILE: 03_SYSTEM_ENTITIES/60_QA__QUALITY/10_MUSIC_QA/06__HOOK_PANEL_QA.md

SCOPE: Universe Engine
LAYER: 03_SYSTEM_ENTITIES
ENTITY_GROUP: QUALITY (QA)
QA_REALM: 10_MUSIC_QA
DOC_TYPE: QA_CHECK
QA_TYPE: HOOK_PANEL
LEVEL: L3
STATUS: ACTIVE
LOCK: FIXED
VERSION: 1.0.0
UID: UE.QA.MUS.HOOK_PANEL.001
OWNER: SYSTEM
ROLE: A hook quality panel check:
evaluates whether the hook stack is memorable, repeat-safe, and clip-friendly.
Focuses on H1/H2/microhooks/Q-line/S-tag perception rather than technical compliance.

CHANGE_NOTE:
- DATE: 2026-01-12
- TYPE: MAJOR
- SUMMARY: "Created Hook Panel QA: rubric for hook memorability, quoteability, and repeat-safe variation."
- REASON: "Hooks can be compliant but still weak; QA panel checks the human effect."
- IMPACT: "Higher earworm rate and better selection of winners."
- CHANGE_ID: UE.CHG.2026-01-12.QA.HOOK_PANEL.001

---

## 0) PURPOSE (LAW)
Answer:
**“Is the hook actually strong for humans?”**

This is a heuristic panel test (not deterministic).

---

## 1) INPUTS
- audio take (candidate)
- optional: hook timestamps (hook1 time)
- optional: lyrics / Q-line candidate
- optional: UGC clip window

---

## 2) PROCEDURE (HOW TO RUN)
1) Find the primary hook moment (or first chorus / hook section).
2) Listen to hook section twice.
3) After second listen, ask:
   - can I hum it?
   - do I remember a line or motif?
   - would I replay the clip?
4) Output RESULT + notes.

---

## 3) HOOK RUBRIC (HEURISTIC)
### C1 — Memorability (H1)
- after 2 listens, hook sticks

### C2 — Distinctiveness
- not generic; has a unique contour, timbre, or slogan

### C3 — Quoteability (Q-line) / Tagability (S-tag)
- lyrical: one line is caption-ready
- instrumental: signature tag/motif is identifiable

### C4 — Repeat-safe feel
- repetition feels addictive, not irritating
- has small evolution on repeats (if repeats exist)

### C5 — Clip friendliness
- hook works as 10–15s standalone clip

---

## 4) RESULT (PASS/WARN/FAIL)
PASS when:
- memorability and clip friendliness are strong
- at least 3 of C1..C5 are clearly positive

WARN when:
- hook has potential but is slightly generic or not clear (fixable)

FAIL when:
- hook is forgettable or annoying
- no quote/tag moment exists

---

## 5) FIX SUGGESTION KNOBS (1–2 MAX)
- SHARPEN_H1:
  - simplify and emphasize the main motif/line
- ADD_Q_LINE_OR_TAG:
  - create a clearer quote line or signature tag
- VARIATION_TWEAK:
  - add a subtle evolution on hook repeat
- CLIP_OPTIMIZE:
  - reframe hook section to work better as 10–15s clip

---

## 6) OUTPUT TEMPLATE (MANDATORY)
HOOK_PANEL_QA_RESULT:
- TRACK_UID:
- TAKE_ID:
- HOOK_WINDOW: [start_sec..end_sec] (optional)
- RESULT: {PASS | WARN | FAIL}
- NOTES:
  - 3–10 bullets
- FIX_SUGGESTION:
  - 1–2 knobs max

---

## 7) REFERENCES (RAW)
Hook system context:
- Earworm Hook Stack ENG  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/10_ENG__ENGINES/12_TREND_GENRE_ENGINES/06__EARWORM_HOOK_STACK_ENG.md

Validator alignment:
- Repeat Guard VAL  
  RAW: https://raw.githubusercontent.com/pashatyutnev-afk/universe-engine/refs/heads/main/03_SYSTEM_ENTITIES/50_VAL__VALIDATORS/10_MUSIC_VALIDATORS/03__REPEAT_GUARD_VAL.md

---

## FINAL RULE (LOCK)
OWNER: SYSTEM
LOCK: FIXED

--- END.
