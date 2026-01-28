# SPC PRO PACK — GATE (G7) — STACKING SAFE (P0 PROTECTED) (VOCAL_DIRECTOR) (DRAFT)
FILE: 04_KNOWLEDGE_BASE/20_ENTITIES_KB/10_SPC/PRO_PACKS/06_SOUND_MUSIC/07__VOCAL_DIRECTOR_SPC/09__GATES/07__GATE__STACKING_SAFE.md

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
UID: UE.KB.SPC.GATE.VOCAL_DIRECTOR.STACKING_SAFE.001
OWNER: SYSTEM
ROLE: Gate G7 verifies clarity-safe stacking decisions: stacking must be explicitly YES/NO, and if YES it must include minimal-first placement, explicit P0 protected zones, and QC rules with fail triggers preventing intelligibility loss.

CHANGE_NOTE:
- DATE: 2026-01-15
- TYPE: MAJOR
- SUMMARY: "Created Gate G7 STACKING SAFE for VOCAL_DIRECTOR."
- REASON: "Uncontrolled stacking commonly masks consonant attacks and destroys must-hear recognition."
- IMPACT: "Allows hook lift without sacrificing clarity."
- CHANGE_ID: UE.CHG.2026-01-15.KB.SPC.GATE.VD.G7.001

---

## 0) PURPOSE
Ensure stacking does not reduce intelligibility:
- explicit decision (YES/NO)
- protected zones for P0
- QC fail triggers
- minimal-first constraint

PASS of G7 is recommended before take pack (G8).

---

## 1) REQUIRED ARTIFACTS (STABLE NAMES)
G7 requires:
- STACKING_DECISION (or explicit stacking_used field)
- STACKING_MAP_BY_SECTION (if stacking_used=YES)
- PROTECTED_ZONES (if stacking_used=YES)
- QC_RULES (if stacking_used=YES)
Optional:
- N_A_DECISION (if stacking_used=NO)

Origin tool:
- T11 STACKING_SAFE_PLANNER

Playbook:
- PB-07 STACKING SAFE FIX

---

## 2) THRESHOLDS (STRICT)
### Explicit decision
- stacking_used must be explicitly YES or NO

### If stacking_used = YES
Required:
- stacking map exists and is minimal-first
- protected zones explicitly list:
  - P0 phrases (copy-exact)
  - P0 word attack list
- QC rules include:
  - P0 first listen remains YES
  - fail trigger: if P0 becomes less clear → remove/move stacking
Forbidden:
- continuous stacking across full chorus lines
- stacking over P0 attacks by default

### If stacking_used = NO
Required:
- explicit N/A decision with reason + alternative lift lever

---

## 3) PASS / REWORK / FAIL
### PASS if:
- stacking_used explicit AND
  - if YES: map + protected zones + QC rules present
  - if NO: explicit N/A decision present

### REWORK if:
- decision exists but:
  - protected zones are vague (“important words”) OR
  - QC rules missing fail triggers OR
  - map exists but placement is under-specified
(Fixable by strengthening protection/QC.)

### FAIL if:
- no explicit decision (YES/NO)
- stacking is “everywhere” or continuous across chorus (violates minimal-first)
- protected zones missing entirely when stacking_used=YES
- QC rules missing entirely when stacking_used=YES
- stacking is designed to sit on P0 attacks (intelligibility loss by design)

Stop rule:
- If FAIL → do not proceed to G8 until fixed.

---

## 4) OUTPUT (G7 VERDICT BLOCK)
G7_VERDICT:
- STATUS: PASS | REWORK | FAIL
- reasons:
  - 1)
  - 2) (optional)
- stop_run: YES/NO
- next_action:
  - if PASS: "Proceed to G8 TAKE PACK"
  - if REWORK: "Strengthen protected zones/QC via T11; rerun G7"
  - if FAIL: "Apply PB-07; rerun G7, then verify G3"

---

## 5) FIX ROUTE
Tool:
- T11 STACKING_SAFE_PLANNER

Playbook:
- PB-07 STACKING SAFE FIX (A5)

Verification:
- After stacking changes, verify G3 (intelligibility).

---

## 6) ANTI-SCOPE VIOLATIONS
Forbidden:
- mix/master chain prescriptions
Allowed:
- placement/protection rules and QC checks

---

## 7) TRACE
TRACE:
- GATE: G7
- UID: UE.KB.SPC.GATE.VOCAL_DIRECTOR.STACKING_SAFE.001
- TOOL: T11
- PLAYBOOK: PB-07

--- END.
