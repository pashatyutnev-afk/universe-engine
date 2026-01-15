# SPC PRO PACK — GATE (G8) — TAKE PACK REPEATABILITY + QC (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/05__KB_GATES/08__GATE__TAKE_PACK_REPEATABILITY.md

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
UID: UE.KB.SPC.GATE.VOCAL_DIRECTOR.TAKE_PACK.001
OWNER: SYSTEM
ROLE: Gate G8 validates that a Take Direction Pack exists and is repeatable: section goals, risk lines, repeatability rules, QC hard/soft fails, and comp notes are defined. Prevents session drift and unusable takes.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created Gate G8: Take Pack Repeatability + QC for VOCAL_DIRECTOR Pro Pack."
- REASON: "Without explicit take goals and QC hard fails, direction becomes subjective and comping becomes inconsistent."
- IMPACT: "Faster sessions, consistent vocal character, fewer unusable takes."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.GATE.VD.TAKEPACK.001

---

## 0) PURPOSE
This gate answers:
- Is the take direction pack complete enough to produce repeatable takes and comp-safe results?

Validates:
- TAKE_GOALS_BY_SECTION
- REPEATABILITY_RULES
- QC_HARD_FAILS / QC_SOFT_FAILS
- COMP_NOTES

---

## 1) REQUIRED INPUTS
Prerequisites:
- G1 PASS (inputs exist)
- Recommended: G2/G3 PASS so QC can tie to P0 targets

Inputs to validate:
- TAKE_GOALS_BY_SECTION
- REPEATABILITY_RULES
- QC_HARD_FAILS
- QC_SOFT_FAILS (optional but recommended)
- COMP_NOTES

---

## 2) PASS / REWORK / FAIL CONDITIONS
### PASS
PASS if ALL are true:
- TAKE_GOALS_BY_SECTION exists and covers at least Verse + Chorus
- each section has 2–4 goals (executable)
- REPEATABILITY_RULES exist (short, strict; at least 3 rules)
- QC_HARD_FAILS exist and include must-hear protection:
  - P0 not understood → hard fail (if must-hear targets exist)
  - breath split inside P0 → hard fail (if breath gate applies)
- COMP_NOTES exist and prohibit comping across different pronunciations/characters

### REWORK
REWORK if:
- take goals exist but are too many/vague
- repeatability rules missing or too weak
- QC exists but lacks hard fails
- comp notes missing
Fix route:
- PB-06 TAKE DIRECTION PACK to rebuild goals + QC + repeatability + comp notes

### FAIL
FAIL if:
- take pack missing entirely
- QC_HARD_FAILS missing (no rejection criteria)
- repeatability rules absent (drift guaranteed)
- take pack includes out-of-scope mixing chain prescriptions
FAIL implies:
- NOT READY; must create/rebuild via PB-06.

---

## 3) REQUIRED EVIDENCE (WHAT MUST BE SHOWN)
EVIDENCE_BLOCK must exist in output pack:
- TAKE_GOALS_BY_SECTION:
- REPEATABILITY_RULES:
- QC_HARD_FAILS:
- QC_SOFT_FAILS (if present):
- COMP_NOTES:
- NOTES:
  - how QC ties to must-hear targets (short)

---

## 4) FIX ROUTE (PLAYBOOK MAPPING)
If REWORK/FAIL:
- Apply PB-06 TAKE DIRECTION PACK
- Rerun G8, then proceed to G9 only if PASS.

---

## 5) COMMON FAIL MODES
- Goals are “be better” vibes, not executable.
- No hard fails; everything becomes subjective.
- Drift between takes; comp is impossible.
- Comping across different pronunciations creates artifacts.
- “Fix” attempted via mixing advice (out of scope).

---

## 6) OUTPUT FORMAT (MANDATORY)
G8_RESULT:
- VERDICT: PASS | REWORK | FAIL
- EVIDENCE_BLOCK:
  - TAKE_GOALS_BY_SECTION:
  - REPEATABILITY_RULES:
  - QC_HARD_FAILS:
  - COMP_NOTES:
- NEXT_STEP:
  - if PASS: "Proceed to G9 SCOPE COMPLIANCE"
  - if REWORK/FAIL: "Apply PB-06 and rerun G8"

--- END.
