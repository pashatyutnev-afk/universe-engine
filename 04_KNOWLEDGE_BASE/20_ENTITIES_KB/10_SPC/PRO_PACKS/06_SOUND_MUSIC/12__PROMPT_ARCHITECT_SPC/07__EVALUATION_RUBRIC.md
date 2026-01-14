# SPC PRO PACK — EVALUATION RUBRIC (PROMPT_ARCHITECT) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/12__PROMPT_ARCHITECT_SPC/07__EVALUATION_RUBRIC.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC
PACK_CLASS: SPC_PRO_PACK
DOMAIN: SOUND_MUSIC
DOC_TYPE: RUBRIC
LEVEL: L3
STATUS: DRAFT
LOCK: FIXED
VERSION: 0.1.0
UID: UE.KB.SPC.PACK.PROMPT_ARCHITECT.RUBRIC.DRAFT.001
OWNER: SYSTEM
ROLE: Scoring rubric for PROMPT_ARCHITECT outputs (prompt contracts + iteration logs). Provides deterministic scoring axes, thresholds, hard-fails, and decision rule aligned to pack gates.

CHANGE_NOTE:
- DATE: 2026-01-14
- TYPE: MAJOR
- SUMMARY: "Created evaluation rubric for PROMPT_ARCHITECT: 5 scoring axes aligned to gates, thresholds, and report template."
- REASON: "Rubric converts gate outcomes into a consistent overall decision and enables calibration by cases."
- IMPACT: "Less subjective evaluation and faster improvement loops."
- CHANGE_ID: UE.CHG.2026-01-14.KB.SPC.PACK.PROMPT.RUBRIC.001

---

## 0) PURPOSE
This rubric scores:
- prompt contract quality (spec-level, not audio)
- iteration discipline (variants/patch logs)
- readiness for passing downstream QA/VAL

Rubric is aligned with gates (UID-only).

---

## 1) SCALE
SCALE: 0..3 per axis
- 0 = broken / missing
- 1 = weak / vague / risky
- 2 = solid / usable
- 3 = excellent / pro-level

Total score: 0..15

---

## 2) AXES (5)
### AX1 — Contract Clarity & Completeness (Gate 01)
Score:
- 0: missing core blocks OR severe contradictions
- 1: blocks exist but vague/contradictory/overloaded
- 2: complete, mostly consistent, minor cleanup
- 3: complete, concise, non-contradictory, controllable

### AX2 — Style Fingerprint Stability (Gate 04)
Score:
- 0: genre soup / no anchors / contradictions
- 1: identity unclear or too many anchors
- 2: clear primary identity + anchors; dominance mostly ok
- 3: 3–6 anchors, dominance explicit, minimal drift risk

### AX3 — Vocal Intent & Differentiation (Gate 02)
Score:
- 0: no vocal plan / contradictions
- 1: “make voices different” vibes-only
- 2: role ownership + ≥2 levers; adequate negatives
- 3: strong role map, compact levers, targeted negatives, clear contrast rule

### AX4 — Repetition Control Intent (Gate 03)
Score:
- 0: no repetition policy; contradictions
- 1: policy vague; no verse novelty
- 2: policy explicit + verse novelty + targeted negatives
- 3: policy explicit, balanced (hook allowed), novelty constraints clean, no over-banning

### AX5 — Iteration Discipline & Trace (Gate 05)
Score:
- 0: no baseline freeze; multi-axis chaos
- 1: partial logs; unclear axis changes
- 2: one-axis mostly respected; logs exist; decisions recorded
- 3: strict one-axis; minimal deltas; expected effect + decision; loop limits respected

---

## 3) HARD FAILS (INSTANT FAIL)
INSTANT_FAIL if any:
- Gate 01 = FAIL (contract broken)
- unsafe / disallowed prompting present
- “copy exactly X” instruction not rewritten into principles
- invented claims about KB/gates/UIDs (no-fantasy breach)
- silent multi-axis changes presented as minimal patch

---

## 4) DECISION RULE
Decision uses both gates and score.

Step A: Run gates (recommended):
- 01 clarity (required)
- 02 voice (if vocals relevant)
- 03 repetition (usually)
- 04 style (recommended)
- 05 discipline (if iteration exists)

Step B: Compute rubric score.

PASS:
- no instant fails
- AX1 ≥ 2
- total score ≥ 11
- and required gates PASS (or REWORK resolved)

REWORK:
- no instant fails
- total score 8–10 OR any axis = 1 that is fixable with one patch
- gate outcome includes REWORK

FAIL:
- any instant fail OR total score ≤ 7

---

## 5) REWORK PRIORITY (WHAT TO FIX FIRST)
Priority order:
1) AX1 Contract clarity (fix contradictions/missing blocks)
2) AX2 Style stability (prune anchors, dominance)
3) AX3 Vocal intent (role map + levers)
4) AX4 Repetition policy (novelty + negatives)
5) AX5 Discipline (freeze baseline, one-axis logs)

---

## 6) REPORT TEMPLATE (COPY)
RUBRIC_REPORT:
- DATE: YYYY-MM-DD
- TARGET_OUTPUT_ID:
- CONTEXT:
  - format:
  - language:
  - vocal mode:
- GATE_RESULTS (UID-ONLY):
  - <gate uid> -> PASS/REWORK/FAIL
- SCORES:
  - AX1: 0..3
  - AX2: 0..3
  - AX3: 0..3
  - AX4: 0..3
  - AX5: 0..3
- TOTAL: 0..15
- DECISION: PASS/REWORK/FAIL
- TOP_ISSUES:
  - <issue>
- FIX PLAN:
  - playbook uid/name + minimal patch idea
- TRACE:
  - MEMORY_REUSE: YES/NO
  - WEB_LOOKUP_USED: YES/NO
  - AXIS_CHANGED (if rework):
  - LOOP_COUNT:

---

## 7) CALIBRATION LINK (CASES)
Use case library for calibration:
- GOOD case should score ≥ 12
- BAD case should instant FAIL
- BORDERLINE should score 9–10 and REWORK on one gate
- EDGE cases adjust structure expectations (e.g., loop)

---

## 8) RELATED (UID-ONLY)
GATE UIDS:
- UE.KB.SPC.GATE.PROMPT_CONTRACT_CLARITY.001
- UE.KB.SPC.GATE.VOICE_DIVERSITY_INTENT.001
- UE.KB.SPC.GATE.REPETITION_CONTROL_INTENT.001
- UE.KB.SPC.GATE.STYLE_FINGERPRINT_STABILITY.001
- UE.KB.SPC.GATE.ONE_AXIS_DISCIPLINE.001

--- END.
