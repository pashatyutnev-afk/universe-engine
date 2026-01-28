# SPC PRO PACK — GATE (G6) — BREATH / SINGABILITY (PROTECT P0) (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/05__KB_GATES/06__GATE__BREATH_SINGABILITY.md

SCOPE: Universe Engine
LAYER: 04_KNOWLEDGE_BASE
REALM: 20_ENTITIES_KB / 10_SPC
PACK_CLASS: SPC_PRO_PACK
DOMAIN: SOUND_MUSIC
DOC_TYPE: GATE
LEVEL: L3
STATUS: DRAFT
LOCK: FIXED
VERSION: 0.1.0
UID: UE.KB.SPC.GATE.VOCAL_DIRECTOR.BREATH_SINGABILITY.001
OWNER: SYSTEM
ROLE: Gate G6 validates that breath policy and singability handling exist: P0 must-hear phrases are protected from breath splits, density risks are flagged, and escalation notes are produced when text is unsingable at tempo. Prevents “impossible takes.”

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created Gate G6: Breath / Singability (protect P0) for VOCAL_DIRECTOR Pro Pack."
- REASON: "Many clarity failures are breath/density failures; without explicit policy, hooks break and intelligibility collapses."
- IMPACT: "Cleaner hook delivery, repeatable phrasing, correct escalation when text must change."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.GATE.VD.BREATH.001

---

## 0) PURPOSE
This gate answers:
- Does the pack protect must-hear phrases from breath breaks and handle singability risks deterministically?

Validates:
- BREATH_POLICY
- MUST_HEAR_PROTECTION_RULES
- DENSITY_SCAN (or equivalent risk line list)
- ESCALATION_NOTES when required

---

## 1) REQUIRED INPUTS
Prerequisites:
- G1 PASS (inputs exist)
- G2 PASS (must-hear targets exist)

Inputs to validate:
- MUST_HEAR_PHRASES (P0/P1) and/or P0 words list
- BREATH_POLICY artifact
- any risk-line notes (if present)

---

## 2) PASS / REWORK / FAIL CONDITIONS
### PASS
PASS if ALL are true:
- BREATH_POLICY exists and defines:
  - allowed breath points
  - forbidden breath points (especially inside P0)
- MUST_HEAR_PROTECTION_RULES exist and explicitly state:
  - “never split P0 phrases”
- A singability risk artifact exists:
  - DENSITY_SCAN OR RISK_LINES list
- If unsingable-risk is detected:
  - ESCALATION_NOTES exist (to Lyricist/Songwriter) without rewriting text

### REWORK
REWORK if:
- breath policy exists but is incomplete (no forbidden points / no P0 protection)
- no density scan/risk list exists, but density issues are implied
- escalation rules are not explicit
Fix route:
- PB-04 to build density scan + breath policy + escalation formatting

### FAIL
FAIL if:
- breath policy missing entirely
- pack permits breath breaks inside P0 phrases
- unsingable lines are “handled” by rewriting lyrics inside the pack (scope violation)
- no escalation notes despite clearly unsingable constraints
FAIL implies:
- NOT READY; must rebuild breath/singability layer with PB-04.

---

## 3) REQUIRED EVIDENCE (WHAT MUST BE SHOWN)
EVIDENCE_BLOCK must exist in output pack:
- BREATH_POLICY:
  - allowed:
  - forbidden:
- MUST_HEAR_PROTECTION_RULES:
  - rule list
- SINGABILITY_RISK:
  - DENSITY_SCAN or RISK_LINES:
- ESCALATION_NOTES:
  - present: YES/NO
  - owner: Lyricist/Songwriter (if YES)
  - must_keep: P0 list (if YES)

---

## 4) FIX ROUTE (PLAYBOOK MAPPING)
If REWORK/FAIL:
- Apply PB-04 BREATH & DENSITY FIX + ESCALATION
- Rerun G6, then proceed to G7 only if PASS.

---

## 5) COMMON FAIL MODES
- Breath breaks inside hook phrase.
- “Fix” by speeding/forcing diction without breath plan.
- Density risks ignored until late.
- Escalation missing; silent lyric rewrite attempted.

---

## 6) OUTPUT FORMAT (MANDATORY)
G6_RESULT:
- VERDICT: PASS | REWORK | FAIL
- EVIDENCE_BLOCK:
  - BREATH_POLICY:
  - MUST_HEAR_PROTECTION_RULES:
  - SINGABILITY_RISK:
  - ESCALATION_NOTES:
- NEXT_STEP:
  - if PASS: "Proceed to G7 STACKING CLARITY-SAFE"
  - if REWORK/FAIL: "Apply PB-04 and rerun G6"

--- END.
