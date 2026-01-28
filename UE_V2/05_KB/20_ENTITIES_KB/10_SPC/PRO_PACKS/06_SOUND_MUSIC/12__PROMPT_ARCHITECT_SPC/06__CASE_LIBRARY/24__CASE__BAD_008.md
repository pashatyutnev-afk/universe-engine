# CASE — BAD (UGC/SHORT: HOOK TIMING MISSING / NO EARLY RECOGNITION) (PROMPT_ARCHITECT) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/12__PROMPT_ARCHITECT_SPC/06__CASE_LIBRARY/24__CASE__BAD_008.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC
PACK_CLASS: SPC_PRO_PACK
DOMAIN: SOUND_MUSIC
DOC_TYPE: CASE
LEVEL: L3
STATUS: DRAFT
LOCK: FIXED
VERSION: 0.1.0
UID: UE.KB.SPC.CASE.PROMPT_ARCHITECT.BAD.008
OWNER: SYSTEM
ROLE: BAD case calibrating UGC/SHORT failure: loop/short prompt lacks explicit “hook immediately” timing and does not define recognition/edit points. Should trigger REWORK on contract clarity for short mode and fail UGC-readiness intent (policy miss).

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Added BAD case #8: UGC/short without hook timing/recognition window → REWORK/FAIL patterns."
- REASON: "Short/UGC outputs need immediate recognition and cut-friendly structure; missing timing causes weak clips."
- IMPACT: "Improves short-mode prompting discipline and avoids unusable UGC clips."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.CASE.BAD.008

---

## 0) CASE RECORD
CASE_RECORD:
- CASE_ID: CASE-BAD-008
- TYPE: BAD
- CONTEXT:
  - FORMAT: UGC SHORT / LOOP (15–30s)
  - LANGUAGE: any (optional hook)
  - VOCAL_MODE: optional
  - STYLE: any (not focus)
- INPUT_INTENT (short):
  - Make a short clip for UGC, but prompt forgets to demand immediate hook/recognition and edit points.

---

## 1) PROMPT CONTRACT (BAD EXAMPLE)
STYLE_BLOCK:
- "energetic electronic rock, punchy drums" (ok)

STRUCTURE_BLOCK (LOOP MODE BUT WEAK):
- "build up for a while then drop"
- "make it cinematic intro then later hook"
- (no explicit “hook appears immediately”)
- (no clear loop segment components A/B/C)
- (no edit points / cut-friendly phrasing)

VOCAL_INTENT_BLOCK:
- optional / not specified

NEGATIVE_SPEC_BLOCK:
- avoid mud
- avoid boring parts (vague)

CONSTRAINTS_BLOCK:
- duration: 15–30 seconds
- (missing: early recognition window / hook timing)
- (missing: repetition policy suitable for loop)

---

## 2) EXPECTED GATE RESULTS (UID-ONLY)
EXPECTED_GATE_RESULTS:
- UE.KB.SPC.GATE.PROMPT_CONTRACT_CLARITY.001 -> REWORK/FAIL
  WHY: short/loop mode requires explicit hook timing + loop segment definition; “build up then drop” wastes short duration

- UE.KB.SPC.GATE.REPETITION_CONTROL_INTENT.001 -> REWORK
  WHY: loop repetition policy not stated (where repetition is allowed, how hook repeats)

- UE.KB.SPC.GATE.STYLE_FINGERPRINT_STABILITY.001 -> PASS/REWORK
  NOTE: style may be ok, but structure makes the clip unusable

Other gates:
- voice: N/A
- one-axis: N/A

POLICY MISS (UID-ONLY, NOT A PACK GATE):
- UE.CTL.MUS.DURATION_POLICY.001 -> NOT SATISFIED (intent missing)
- UE.CTL.MUS.UGC_VIRAL_RULESET.001 -> NOT SATISFIED (edit points / early recognition missing)

---

## 3) WHY THIS IS BAD (CALIBRATION NOTES)
WHY_BAD:
- In 15–30s, “build up then later hook” often produces:
  - no recognition in first seconds
  - weak UGC performance and low retention
- Without edit points and loop components:
  - clip is hard to cut and loop cleanly
- Missing repetition policy:
  - hook may not repeat or may repeat randomly.

---

## 4) FIX PATH (WHAT TO DO)
Fix steps:
1) Rewrite STRUCTURE_BLOCK for LOOP:
  - define loop segment components:
    - A) riff/groove foundation
    - B) hook phrase/motif (immediate)
    - C) 1–2 accents (optional)
2) Add timing constraint:
  - "hook must be clear immediately (first seconds)"
3) Add UGC cut/cycle constraints:
  - "clear edit points / cut-friendly phrasing"
4) Add repetition policy suitable for loop:
  - "repetition allowed; keep hook short and clean"
5) Use PB-04 PATCH MIN (axis: short/UGC structure) if baseline exists; otherwise PB-01 CORE WORKFLOW (loop profile).

Expected after fix:
- Gate 01 -> PASS (short-mode contract becomes explicit)
- Gate 03 -> PASS (loop repetition policy explicit)

---

## 5) TRACE
TRACE:
- MEMORY_REUSE: NO
- WEB_LOOKUP_USED: NO

--- END.
